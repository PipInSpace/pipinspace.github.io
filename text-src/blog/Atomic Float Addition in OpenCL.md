The following code snippet is a cross-platform implementation of atomic float addition in OpenCL.
The implementation uses hardware-supported functions whereever possible and implements a fallback algorithm that is faster than most commonly used approaches.
I am sharing it here for other developers to use as a single function to handle atomic addition on all platforms uniformly.

<link href="../styles/prism.css" rel="stylesheet" />
<script src="../files/prism.js"></script> <!--syntax highlighting-->
<pre class="lang-opencl"><code>inline void atomic_add_f(volatile __global float* addr, const float val) {
	#if defined(cl_nv_pragma_unroll) // use hardware-supported atomic addition on Nvidia GPUs with inline PTX assembly
		float ret; asm volatile("atom.global.add.f32 %0,[%1],%2;":"=f"(ret):"l"(addr),"f"(val):"memory");
	#elif defined(__opencl_c_ext_fp32_global_atomic_add) // use hardware-supported atomic addition on some Intel GPUs
		atomic_fetch_add_explicit((volatile global atomic_float*)addr, val, memory_order_relaxed);
	#elif __has_builtin(__builtin_amdgcn_global_atomic_fadd_f32) // use hardware-supported atomic addition on some AMD GPUs
		__builtin_amdgcn_global_atomic_fadd_f32(addr, val);
	#else // fallback emulation: https://forums.developer.nvidia.com/t/atomicadd-float-float-atomicmul-float-float/14639/5
		float old = val; while((old=atomic_xchg(addr, atomic_xchg(addr, 0.0f)+old))!=0.0f);
	#endif
}</code></pre>

But why does this need to exist?
Atomic addition of integers is a core part of the OpenCL specification and is included in virtually all implementations of the spec.
Atomic addition of floating point numbers however is not officially part of the specification, and only a handful of atomic operations defined in the core spec accept floats at all (one of them being `atomic_xchg()`, used in the above implementation).
Because atomic float addition is a very useful tool and many algorithms depend on it, numerous vendors have implemented their own hardware-supported versions, sometimes with accompanying OpenCL extensions.
These are not standardized however and code using a specific extension will never be universally cross-platform. The above snippet defines a singular inline function that uses macros to expand only the supported implementation on the platform the code is compiled on.
If no compatible implementation is detected, the function expands into a functionally identical (but slower than native) implementation that is up to an order of magnitude(!!!) faster than common workarounds<sup><a id="1t" href="#1b">[1]</a></sup>.
I hope this code saves some headaches when working with atomic float addition! If you have any improvements for or thoughts on the code above feel free to reach out to me, preferably over the [Fediverse](https://mastodon.social/@pipinspace). I want to thank [ProjectPhysX](https://github.com/ProjectPhysX) for compiling the implementations and especially for providing the PTX assembly for NVidia GPUs!

<a id="1b" href="#1t">[1]</a>: Yes, really! Many implementations loose an immense amount of speed when conflicts between threads occur. One of the more common implementations uses only one `atomic_cmpxchg()` call in a while loop that checks for successful addition. This can quickly lead to race conditions where threads have to "retry" the addition every time another thread writes a new value to memory in between, possibly for hundreds of times. This completely degrades performance and in my tests is about 8000 times slower than the  fallback algorithm in the snippet above.