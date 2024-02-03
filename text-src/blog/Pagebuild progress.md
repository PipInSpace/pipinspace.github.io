I have made some improvements to [pagebuild](https://github.com/PipInSpace/pagebuild), my static site generator. 
It actually also builds pages now and not just blog entries!

pagebuild has two "modes" now: when provided with just a directory, it builds static pages from the path/text-src/ folder containing markdown files and the "template.html" and "components.html" files. Additionally, when provided with the "--blog" flag, pagebuild can build a static blog from the path/text-src/blog/ folder. This blog will be saved to path/blog/ and contains a blog index html file (blog.html) and html files for each article. Articles as well as normal pages now have access to all the different tags:

- title - The page title (Markdown file name)
- content - The page content (Formatted html)
- date - The page creation date

And if blog mode is enabled:
- all_posts - A table of all posts sorted by their creation dates
- current_post - The most recent post, formatted with header, link and date

I am currently working on an rss feed generator.<br>
Thanks for reading! - PipInSpace