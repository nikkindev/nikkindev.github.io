## Personal Jekyll site

Theme: [Sidey](https://github.com/ronv/sidey)

### Configurations made

- **_config.yml**  
`remote_theme: ronv/sidey`  
`excerpt_separator: <!--more-->`  
`markdown: kramdown`  
(Others from theme config)

- **/pdfs** folder added to host docs

- **/_layouts/*.html**  
`<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>`  
Ref: [Ian Goodfellow's blog](http://www.iangoodfellow.com/blog/jekyll/markdown/tex/2016/11/07/latex-in-markdown.html)

- **/_data/navigation.yml**  
Custom links for navigation

- **index.html**  
Copied from theme

### Pages

```
---
title: <Title>
---

<Page content>
```

### Posts

```
---
title: <Title>
tags: [physics]
---

<Summary>

<!--more-->

<Post content>
```
- Name the *.md* file as **yyyy-mm-dd-<title>.md**
- TeX formatting within `$$...$$`
- Ignore TeX formatting in title
- To open links in new tab `[link](url){:target="_blank"}`