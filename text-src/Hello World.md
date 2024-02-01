Hi, this is the first real post on this blog!

This blog is generated with my own static site generator [pagebuild](https://github.com/PipInSpace/pagebuild). 
It generates blog post html files and a blog index from html templates and markdown files. The output of the parser
is minimal and practically all styling can be done over the template files and CSS. Template files are largely regular
html, sections to be replaced are marked with {{tags}}. 

The blog_index template supports the tags {{current_post}} (The most recent blog post, formatted with title, content and date)
and {{​all_posts}}, a table/list of links to all posts with their creation date. The template blog_post supports the three
tags {{date}} (The post's creation date), {{title}} (The post's human-readable title, the filename of it's  Markdown file)
and {{content}}, the post's parsed content.

Additionally, you can define "components" with the {{tag}}-syntax through a components.html file. These are tiny snippets that let
you reuse markdown and html easily and can be inserted in both the template files and the markdown source files. They even work
recursively, but I wouldn't recommend putting a component within itself (The system can handle this somewhat and won't crash, but
it's still not pretty). For examples, visit the example file on [GitHub](https://github.com/PipInSpace/pipinspace.github.io/blob/main/text-src/components.html).

[pagebuild](https://github.com/PipInSpace/pagebuild) is still very much a WIP. In the future I might add support for {{​all_posts}}
lists on post pages and a more extensible syntax. The components system I have thrown together is relatively robust, but including
the all_posts tag here in the Markdown without a zero-width space to throw off the replace function would get "messy" in the current
approach. I might have to rework that :). Maybe add conditions to the components system? We'll see.

Thanks for Reading! - PipInSpace