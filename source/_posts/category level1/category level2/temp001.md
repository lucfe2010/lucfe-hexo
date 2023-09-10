wireframe

html

A markup language is a text-encoding system consisting of a set of symbols inserted in a text document to control its structure, formatting, or the relationship between its parts.[1] Markup is often used to control the display of the document or to enrich its content to facilitate automated processing.

A markup language is a set of rules governing what markup information may be included in a document and how it is combined with the content of the document in a way to facilitate use by humans and computer programs.


most modern markup languages, such as XML, identify document components (for example headings, paragraphs, and tables), with the expectation that technology, such as stylesheets, will be used to apply formatting or other processing.


markup meta-languages

XML allow designers to specify particular schemas, which determine which elements, attributes, and other features are permitted, and where.

The schemas are a set of 'types', each associated with a set of properties. The types are arranged in a hierarchy.

---

What is Schema Markup?
Firstly, what is Schema?

In essence, this is part of adding extra information to online content to allow search engines to have a better picture of what a website is about.

This extra information isn't viewed by users on-screen but inserted as part of HTML code. It is a form of microdata, which is read by the search engine spiders when crawling your website. It helps the search engine understand what your page is actually about.

This should be an addition to keywords in your content, which are chosen as means of good SEO practice.

"Schema Markup" is the action of adding this data into your site's coding based on vocabulary from the community at Schema.org. Schema is so relevant because the community is sponsored by Google, Microsoft, Yahoo and Yandex.

Knowing which words to use in relation to your content are pre-determined. There is a hierarchical family tree, if you will, to follow.

These are words which would benefit users if the sites had mark ups installed on them.

[Getting started with schema.org using Microdata](https://schema.org/docs/gs.html)

---

Some markup languages, such as the widely used HTML, have pre-defined presentation semantics, meaning that their specifications prescribe some aspects of how to present the structured data on particular media.

css

js

yarn

yo

npm

npx

yaml



git

bash
shell

node  js

bulma

https://bulma.io/

Bulma: the modern
CSS framework that
just works.
Bulma is a free, open source framework that provides ready-to-use frontend components that you can easily combine to build responsive web interfaces.

inferno


## Markdown engines, CSS frameworks, CSS methodology

NPM packages (Babel, PostCSS, Less/Sass, etc)

### templates
Templates define the presentation of your website by describing what each page should look like. 

It might be necessary to goto the blog root and install a specific renderer for the template language you have chosen.

- templates
npm install hexo-renderer-ejs
npm install hexo-renderer-njks
npm install hexo-render-pug

- styles
npm install hexo-renderer-stylus
npm install hexo-renderer-less
npm install hexo-renderer-sass

liquid
react
vue

template engines (**EJS**, Pug, Nunjucks,

ejs


Pug is a high-performance template engine heavily influenced by Haml and implemented with JavaScript for Node.js and browsers.

[pugjs.org](https://pugjs.org/)


Haml (HTML abstraction markup language) is based on one primary principle: markup should be beautiful. It’s not just beauty for beauty’s sake either; Haml accelerates and simplifies template creation down to veritable haiku.

veritable十足的
a word used to emphasize that sb/sth can be compared to sb/sth else that is more exciting, more impressive, etc.

haiku俳句(日本传统诗体，三行为一首，通常有17个音节)

Embedded Ruby (ERB)
ERB is a templating language based on Ruby.

### Style choices:预处理

**stylus**
sass
scss
less
css


### others

image/svg+xml

## ssg

- Docsify generates your documentation website **on the fly**. Unlike GitBook, it does not generate static html files. Instead, it smartly loads and parses your Markdown files and displays them as a website. 

Docsify makes it easy to create a documentation website, but is not a static-site generator and is not SEO friendly.


- Docusaurus is a static-site generator. It builds a **single-page application** with fast client-side navigation, leveraging the full power of React to make your site interactive. It provides out-of-the-box **documentation features** but can be used to create any kind of site (personal website, product, blog, marketing landing pages, etc).

The docs feature provides users with a way to organize Markdown files in a hierarchical format.

Extend and customize with React

MDX:Write interactive components via JSX and React embedded in Markdown.

MDX allows you to use JSX in your markdown content. You can import components, such as interactive charts or alerts, and embed them within your content. This makes writing long-form content with components a blast.

MDX has no runtime, all compilation occurs during the build stage

- jekyll

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

- hexo

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

Usage: hexo <command>

Commands:
  clean     Remove generated files and cache.   
  config    Get or set configurations.
  deploy    Deploy your website.
  generate  Generate static files.
  help      Get help on a command.
  init      Create a new Hexo folder.
  list      List the information of the site    
  migrate   Migrate your site from other system to Hexo.
  new       Create a new post.
  publish   Moves a draft post from _drafts to _posts folder.
  **render**    Render files with renderer plugins.    
  server    Start the server.
  version   Display version information.

Global Options:
  --config  Specify config file instead of using _config.yml
  --cwd     Specify the CWD(change working diretory)
  --debug   Display all verbose messages in the terminal
  --draft   Display draft posts
  --safe    Disable all plugins and scripts        
  --silent  Hide output on console

- hexojs/warehouse

A JSON database with Models, Schemas, and a flexible querying interface. It powers the wildly successful static site generator Hexo.




- The Single Binary Approach
Some static site generators install a single binary and don't require complex dependency management. The single binary approach gets things set up quickly and easily.

One of the advantages of using Hugo is that it doesn't depend on client-side JS.

Hugo supports unlimited content types, taxonomies, menus, dynamic API-driven content, and more, all without plugins.

Hugo ships with pre-made templates to make quick work of SEO, commenting, analytics and other functions. One line of code, and you're done.


Hugo's Go-based templating