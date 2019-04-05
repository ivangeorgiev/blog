---
title: "Jekyll: Convert README.md to index.html"
date: 2019-04-05
links:
  - title: 
    url: "https://stackoverflow.com/questions/43889579/tell-jekyll-on-github-pages-to-convert-readme-md-to-readme-html-not-index-htm"
---

Add `permalink` to the page metadata.

```yml
---
permalink: index.html
---
Here is my README content...

```

This is also useful if you want to override the default page name being used by Jekyll. For example, if you have a page named `blog-list.md` you might instruct Jekyll to convert it to `blog.html` instead of `blog-list.html` (the default behavior).



