# Mikheyev Labs website

This site uses the [Minimal Mistakes](http://mmistakes.github.io/minimal-mistakes) theme, which is based on a static web page generator called Jekyll. The site is hosted on Github using their Github pages feature. You can wither clone the repository to add posts on your local computer (recommended), or you can edit them directly on Github, which works pretty well, too. If confused, don't hesitate to look at the Minimal Mistakes website for documentation and examples.

To add a post, you simply add a file with the ingredients below to the `_posts` folder, and corresponding images, if any to `images` and Github will compile the site automatically. Alternatively, you can test out how your post looks on your computer using `jekyll build` and even `jekyll serve` on your computer when you have cloned the repository and [installed Jekyll](https://jekyllrb.com/docs/installation/).

## Elements of a post
The post is written in Markdown, which is a human-readable language that can be easily converted by computers to html. Github uses it extensively (e.g., in this README). 

### File name
The post file name has the format `YEAR-MONTH-DAY-title.markdown`. This is important, since that's how Jekyll determines the date of the post.
### Header
Inside the post is a header like this:
```
---
title: Ph.D. student position to work on Lord Howe stick insect
header:
  image: images/stick-insect-phd.jpg
author: alexander_mikheyev
categories: []
tags: ['news', 'Australia']
---
```
The tags and categories don't yet play a role on the site, but could be used to organize the posts later. Maybe use 'Australia' and 'Okinawa' to classify posts that belong in one or the other domain for now. The `author:` field overrides the default author, and you should have an entry made for yourself in `_data/authors.yml`. All of these fields are optional, so if you don't have a header image, you don't need to include this field.

### Including images
You will need to upload the image into the `images` folder on the site. Make sure it is not too lage, smaller than 600px wide is preferable. You can see some examples of how to format images in the code for [this post](https://raw.githubusercontent.com/MikheyevLab/EcoEvoUnit/master/_posts/2017-07-12-EcoEvo_quest.markdown) and numerous [samples posts in Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/year-archive/). You can match these posts with their markdown code on the theme's [Github repo](https://github.com/mmistakes/minimal-mistakes/tree/master/test/_posts)
