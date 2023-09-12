---
title: static site generator wiki
---


## ssg

### Docsify

- Docsify generates your documentation website **on the fly**. Unlike GitBook, it does not generate static html files. Instead, it smartly loads and parses your Markdown files and displays them as a website. 

Docsify makes it easy to create a documentation website, but is not a static-site generator and is not SEO friendly.

### Docusaurus

- Docusaurus is a static-site generator. It builds a **single-page application** with fast client-side navigation, leveraging the full power of React to make your site interactive. It provides out-of-the-box **documentation features** but can be used to create any kind of site (personal website, product, blog, marketing landing pages, etc).

The docs feature provides users with a way to organize Markdown files in a hierarchical format.

Extend and customize with React

MDX:Write interactive components via JSX and React embedded in Markdown.

MDX allows you to use JSX in your markdown content. You can import components, such as interactive charts or alerts, and embed them within your content. This makes writing long-form content with components a blast.

MDX has no runtime, all compilation occurs during the build stage

### jekyll

ruby

Static
Markdown, Liquid, HTML & CSS go in. Static sites come out ready for deployment.

Blog-aware
Permalinks, categories, pages, posts, and custom layouts are all first-class citizens here.

Simple
No more databases, comment moderation, or pesky updates to install—just your content.

moderation

适度；适中；合理
the quality of being reasonable and not being extreme
评审

pesky
causing trouble; annoying.

### hexo

Hexo provides the Nunjucks template engine by default

---

Valine was born in August 7, 2017. It’s a fast, simple & efficient Leancloud based no back end comment system.

Theoretically, but not limited to static blog. Hexo, Jekyll, Typecho, Hugo, Ghost, Docsify and other blog or document programs are currently using Valine.

valine 需要 leancloud

leancloud开发版：开发版让用户可以在开发阶段和个人项目中免费使用 LeanCloud 的大部分功能。大部分商业应用在发布给外部用户后会超过开发版的用量限制，将会需要升级到商用版。

---

Jinja is a fast, expressive, extensible templating engine. Special placeholders in the template allow writing code similar to Python syntax. Then the template is passed data to render the final document.

Nunjucks is essentially a port of jinja2


A notable feature of Hexo is tag plugins. Tag plugins are snippets of code you can add to your Markdown files without having to write complex or messy HTML to render specific content.

Octopress plugins.

Tag Plugins
Tag plugins are different from post tags. They are ported from Octopress and provide a useful way for you to quickly add specific content to your posts.



theme layout
Layout folder. This folder contains the theme’s template files, which define the appearance of your website. Hexo provides the Nunjucks template engine by default, but you can easily install additional plugins to support alternative engines such as EJS or Pug. Hexo chooses the template engine based on the file extension of the template (just like the posts). For example:

layout.ejs   - uses EJS
layout.njk   - uses Nunjucks


- hexojs/warehouse

A JSON database with Models, Schemas, and a flexible querying interface. It powers the wildly successful static site generator Hexo.


### Hugo

- The Single Binary Approach
Some static site generators install a single binary and don't require complex dependency management. The single binary approach gets things set up quickly and easily.

One of the advantages of using Hugo is that it doesn't depend on client-side JS.

Hugo supports unlimited content types, taxonomies, menus, dynamic API-driven content, and more, all without plugins.

Hugo ships with pre-made templates to make quick work of SEO, commenting, analytics and other functions. One line of code, and you're done.


Hugo's Go-based templating