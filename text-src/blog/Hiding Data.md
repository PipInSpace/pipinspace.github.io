A while back I began experimenting with hiding data in innocuous images or text, also known as stenography. The idea is that messages or files are not encrypted but instead hidden in a way that makes detection difficult. When communicating in a public network, users sharing large amounts of encrypted files may arouse suspicion but "sharing a few memes" with your friends looks far less interesting. I've looked into two stenography methods in particular: subtle pixel manipulation in images (image-code) and the generation of nonsense texts with a reversible algorithm (Scipher). Both are implemented in public repositories on my [GitHub profile](https://github.com/VioletSpace).

## Image-Code
My goal with [image-code](https://github.com/VioletSpace/image-code) was to write a programm that is able to include any data (not just other images) within a PNG image without disrupting it too much. The program takes in an image (most file formats are supported) and a file to be encoded (a simple message may be saved as a .txt file). The program outputs a new PNG image that can be decoded by a similarly configured program to return the initial file content.<br>
The output image stores endoded data in a linked sequence of pixels. A pixel's R-channel pixels contains encoded data, the G- and B-channels point to the next pixel in the data sequence. image-code encodes these values as a difference from the average of the 4 surrounding pixels, so pixels usually remain close to their original colour in photos (but disturbance may be visible in very flat or artificial images).

The following images are 1. a base image for encoding and 2. that same base image with [another image](../img/blog/IonSolverCard.png) encoded into it. 

<div class="text-padding" style="display: flex; justify-content:center; gap: 10px">
    <a href="../img/blog/ion.png">    <img src="../img/blog/ion.png" alt="Photo of the NSTAR ion thruster. Base image for encoding in this example." width="100%"></a>
    <a href="../img/blog/ion_enc.png"><img src="../img/blog/ion_enc.png" alt="Photo of the NSTAR ion thruster. Another image is encoded into it, there is no visible difference." width="100%"></a>
</div>

There is no visible difference between the two images. When directly comparing the two, one can only see a little variation in the noise patter. This "data noise" is extracted and highlighted in the following image:

<div class="text-padding" style="display: flex; justify-content:center; gap: 10px">
    <a href="../img/blog/ion_data_noise_amplified.png"><img src="../img/blog/ion_data_noise_amplified.png" alt="Brightened data noise in the encoded image." width="100%"></a>
</div>

This image shows that encoded data isn't clumped together on a small spot with visible disturbance but spread out randomly over the entire image to minimize the visual impact. The data sequence flows in streaks of pixels, but their location is randomized enough to not be visible in the final output.<br>
If you want to use the program to send secret messages to your friends, the source code is available on my GitHub profile under [https://github.com/VioletSpace/image-code](https://github.com/VioletSpace/image-code) along with instructions. I want to highlight again that [image-code](https://github.com/VioletSpace/image-code) does not perform any encryption. The algorithm is easily reverse-engineered and the program should not be used to transfer sensitive data without prior encryption. Output images are also very sensitive to compression. Changing the file format or resolution is generally not possible without loosing the encoded data.

## Scipher
Scipher was not written by me. The version of Scipher [on my GitHub](https://github.com/VioletSpace/scipher) has been forked from [the original](https://github.com/strib/scipher) and adds Python 3.x support + an important bug fix for Windows.<br>
Scipher uses a clever algorithm to generate text from a specified [context-free grammar](https://en.wikipedia.org/wiki/Context-free_grammar) (CFG). During this process, choosing specific words and phrases can be used to encode arbitrary data. Scipher too is not limited to only text but can theoretically encode files of any size and type (although the produced text will be very long for larger files). It is configurable over the CFG used in generation, different grammars can result in very different text. The repository thankfully includes a grammar to generate nonsense "scientific conference invitations", hence the name.<br>
Context-free grammars provide sentence structures and words that can be assembled into a text by a program. The key insight here is that the program has many choices for both text structure and specific words. If these choices are made algorithmically and not randomly like usual, they can actually be used to encode data. Decoding is possible by reversing the decisions made at encoding, provided both sender and receiver have the exact same CFG.<br>
Because of the need for an exact copy of the grammar at decoding, Scipher-generated texts are a bit more secure (the CFG acts similar to a preshared key), but Scipher once again does not encrypt anything, it merely encodes data into an unusal format (i.e. conference invitations). The modified source code is also available on my GitHub profile under [https://github.com/VioletSpace/scipher](https://github.com/VioletSpace/scipher) along with usage instructions.

This is a sample output text from scipher that can be decoded using the default CFG:
<div class="text-padding" style="font-size: 0.7rem; pre code {text-wrap: wrap;}">
<style>
    code {
        text-wrap: wrap;
    }
</style>

    The 10th International ESSUF Special Issue on game-theoretic sharing economy / Birmingham, United Kingdom

    Call for papers -

    The goal of this symposium is to offer a forum for interchanging interpretations, opinions and visionary opinions among the statisticians and cryptographers of game-theoretic computational biology. This symposium ESSUF is a perfect excuse for experts from exhaustive communications and analysts from mutually exhaustive hardware and architecture to come together to display their short and new articles. The motif of ESSUF is ' kernels and voice-over-IP in the significant era of self-learning operating systems: ubiquitous middleware, semantic algorithms and you ', interchanging the mixture of encrypted theory, voice-over-IP, and real-time configurations in arguing optimal algorithms of independent computational biology. There is no limit on the number of footnotes for revisions.

    Topics of interest include, but are not limited to:
    Separated internet of things
    Computationally discrete communications

    Keynote talks:
    * Dr. Maksym Chandrasekar - Lille 2 University of Health and Law
    SMPs now considered harmful
    * Dr. Akshara Salinas - Eindhoven University of Technology
    Decoupling write-ahead logging from A* search with Markov models in the Ethernet with semaphores
    * Flora Browning - Rush University
    Contrasting the lookaside buffer with von Neumann machines and telephony

    Steering Committee:
    Beverly Polanco - University of Bergen

    Past ESSUF locations:
    Kunming, China

    Program Committee:
    Wayne Andrade, Tamkang University
    Assistant Professor Leonie Key, Medical College of Wisconsin
    Francesco Newman, Shaanxi Normal University
    Feng Coleman, University of Alcala

    General Co-Chairs:
    Vaughn Shao (Hunan University)
    Earl Rasmussen (University of Aberdeen)

    Important dates:
    - manuscripts due: June 17, 2024
    - notification of acceptance: July 5, 2024
    - final manuscripts due: August 29, 2024
    - special session date: October 16, 2024

    This symposium welcomes revisions on any subject related to the motifs and the topics discussed above. Submitted abstracts should not be longer than 25 pages, including footnotes. Please look at the terms and conditions and other minutiae on the symposium website.
</div>

Thanks for reading 💜!