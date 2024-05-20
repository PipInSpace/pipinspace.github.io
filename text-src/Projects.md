{{component: link-banner}}
<div class="main_body">

# My Projects

Here you can find a list of my favourite projects:

- <span class="span-highlight"><a style="color: var(--accent-colour-secondary); font-weight: 400;" href="#ionsolver">IonSolver </a></span> -- a simulation software
- <span class="span-highlight"><a style="color: var(--accent-colour-secondary); font-weight: 400;" href="#pagebuild">pagebuild </a></span> -- a minimalistic static site generator written in Rust
- <span class="span-highlight"><a style="color: var(--accent-colour-secondary); font-weight: 400;" href="#website">  My Website</a></span> -- an attempt at basic webdev
- <span class="span-highlight"><a style="color: var(--accent-colour-secondary); font-weight: 400;" href="#reminder"> reminder  </a></span> -- it reminds you to do stuff
- <span class="span-highlight"><a style="color: var(--accent-colour-secondary); font-weight: 400;" href="#rdex-ui">   rdex-ui   </a></span> -- a fancy sci-fi terminal emulator

<h2 id="ionsolver">IonSolver</h2>
<p align="center" style="margin-bottom: 0">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://github.com/PipInSpace/PipInSpace/assets/79136709/9d6f3849-6caa-4419-b5c9-dc44affa8178">
    <img style="width: 100%;" alt="IonSolver logo" src="https://github.com/PipInSpace/PipInSpace/assets/79136709/228f0279-a389-42de-a62d-15177ee31db7">
  </picture>
</p>

[IonSolver](https://github.com/PipInSpace/IonSolver) is a magnetohydrodynamic Lattice-Boltzmann simulation software. In English, this means that IonSolver can simulate how charged fluids like plasma interact with themselves and with outside magnetic and electric fields. IonSolver is currently my main project and I work on it with a friend. We started developing it to study ion thrusters without actually having to build and test them, but have since focused more on getting the physics of the software as accurate as possible. This project combines two of my biggest interests, physics and high performance computing with concurrent programming. IonSolver is open-source and available on GitHub.
<br> <span class="span-highlight">GitHub repository</span> -- [github.com/PipInSpace/IonSolver](https://github.com/PipInSpace/IonSolver)
<br> <span class="span-highlight">YouTube playlist</span> -- [youtube.com/playlist?list=PLKV8...](https://youtube.com/playlist?list=PLKV8dpY2AdM_QT6Yrf0DTfBjzDtKi5w70)

<h2 id="pagebuild">pagebuild</h2>

[pagebuild](https://github.com/PipInSpace/pagebuild) is a very simple and fast static site generator written in Rust. It turns markdown files into html through html templates and "components" that can be defined by the user to reuse markdown or html content. pagebuild also supports simple blogs generated from markdown with a blog index page, pages for every blog post and an RSS feed. This website is created with pagebuild and assembled only from markdown, templates and components!
<br> <span class="span-highlight">GitHub repository</span> -- [github.com/PipInSpace/pagebuild](https://github.com/PipInSpace/pagebuild)

<h2 id="website">My Website</h2>
<!--<iframe src="https://pipinspace.github.io" title="my website" style="width: calc(100% - 20px); height: 400px; margin: 0 10px; box-sizing: border-box;"></iframe>--> 

A small personal website and blog. It is created using pagebuild: the raw text source, components and html templates are accessible on [GitHub](https://github.com/PipInSpace/pipinspace.github.io). This website is a small playground for webdev experiments, my personal writing and a short portfolio. It is hosted both on GitHub pages and on my own server.
<br> <span class="span-highlight">GitHub repository</span> -- [github.com/PipInSpace/pipinspace.github.io](https://github.com/PipInSpace/pipinspace.github.io)

<h2 id="reminder">reminder</h2>

<a href="https://github.com/PipInSpace/reminder">reminder</a> reminds you to do things! It's a small app that, when configured to run on startup, reads a small and simple config file containing tasks you want to be reminded of. When the right conditions are met, a small semi-transparent alert windows opens containing a specified text. It takes focus but is otherwise unobtrusive and closes on a click. reminder is WIP but functional. Editing the config is still manual but very simple, a GUI might follow for that.
<br> <span class="span-highlight">GitHub repository</span> -- [github.com/PipInSpace/reminder](https://github.com/PipInSpace/reminder)

<h2 id="rdex-ui">rdex-ui</h2>

A fancy sci-fi UI/terminal emulator. [rdex-ui](https://github.com/PipInSpace/rdex-ui) uses the tauri library to create a user interface looking like a science fiction computer while providing a working terminal. It is inspired by the eDEX-UI and DEX-UI projects and has the goal of being both good-looking and performant. You can find a short demo [on YouTube](https://www.youtube.com/watch?v=r9r9SWMaATw). 
<br> <span class="span-highlight">GitHub repository</span> -- [github.com/PipInSpace/reminder](https://github.com/PipInSpace/reminder)
<br> <span class="span-highlight">YouTube Demo</span> -- [youtube.com/watch?v=r9r9SWMaATw](https://www.youtube.com/watch?v=r9r9SWMaATw)

{{component: impressum}}
</div>