---
title  : Creating website online in less than 10 minutes with Jekyll and Github
date  : 2019-04-01
---

When I was planning on starting a blog (know why I did it [here](https://hemanth346.github.io/tweet-that-made-me-to-start-a-blog,-know-why/) ), I was initially thinking of a word press blog, but later after having seen most the [OpenAI scholars' blogs](https://openai.com/blog/openai-scholars-class-of-19/), I loved Github pages, I can create post in Markdown format and push with git which is a bonus. There are many guides that can help you setup the pages using Jekyll builder offline and then pushing to Github. I however was not able to setup Jekyll on my PC and had to do the entire thing online, which took some digging but was very easy. Here is my step by step guide to be able to do it

## 1. Fork any theme from existing repositories

You can find the demo and source code of the themes at below sites, there could be more but this is what I used

https://jekyllthemes.io/ (some of them are paid)

http://jekyllthemes.org/

I've used *Minimal Mistakes Jekyll theme* for this blog

> ***Fork the repository of the theme you like, create a branch named gh_pages, and personalize it***

## 2. Personalize the blog

You can personalize the site by making changes to ***_config.yml*** file in your repository directory. The file will be self explanatory or can be a quick google search away.

For detailed instructions you can to go through quick start guide or documentation of the theme if available.


## 3. Write posts, add pages
Create a folder ***_posts*** in home directory if already not existing, proceed to write your posts - each in a new file, commit the changes. For adding pages - we create ***_pages*** folder and add files in required format, update ***_data/navigation.yml*** file


Viola.!! Your blog is up and running.


### Don't make it harder than it is. Remember below tips, they'll come handy until you get hold of things..!

1. Always commit each and every file after editing it, commit one file at a time.
2. Keep commits log open in separate tab, refresh it after every commit to check if the site is successfully built.

> ***I can safely say that by following above tips it'll be much better and faster than checking after an hour of work to find all the previous commits are not built and that you are not sure why it is happening, sure we can do debugging but error message are not that helpful.***
