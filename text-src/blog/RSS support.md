RSS is now supported in my static site generator! 
When in "--blog" mode, pagebuild looks for a "rss.cfg" config file in the path/text-src/blog/ folder, and generates a simple RSS feed in the path/blog/ folder if it finds one.
The config format is simple: Lines begin with a "key: " and contain only one value per line in quotes, all other entries are ignored.
These are all the valid config options:

The feed title:<br>
title: "PipInSpace's Blog"<br>
The blog link:<br>
link: "https://pipinspace.github.io/blog/blog"<br>
The blog description:<br>
description: "My Blog. Sometimes I post here."<br>
The location of post files:<br>
post-link: "https://pipinspace.github.io/blog/"

All other relevant information is extracted from the posts.
You can find my feed [here](https://pipinspace.github.io/blog/rss).<br>
Thanks for reading! - PipInSpace