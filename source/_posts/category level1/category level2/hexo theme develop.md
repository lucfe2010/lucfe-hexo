---
title: hexo theme develop
toc: true
categories: [category1 level1, category1 level2]
---




## hexo theme variables

### site

Site Variables
Variable	Description	Type
site.posts	All posts	array of post objects
site.pages	All pages	array of page objects
site.categories	All categories	array of categories objects
site.tags	All tags	array of tags objects

### config

```js
config: {
    title: 'Lucfe Knowledge Documentation',
    subtitle: '',
    description: '',
    author: 'lucfe',
    language: 'en',
    timezone: '',
    url: 'http://lucfe2010.github.io/lucfe-hexo',
    root: '/lucfe-hexo/',
    permalink: ':title/',
    permalink_defaults: null,

    ...

}
```



#### language

`<html lang={language ? language.substr(0, 2) : ''}>`



#### config.head

_config.yml
head:
    # URL or path to the website's icon
    favicon: /assets/images/favicon_l.png
    # Web application manifests configuration
    # https://developer.mozilla.org/en-US/docs/Web/Manifest
    manifest:
        # Name of the web application (default to the site title)
        name: 

        ...

    meta:
    rss


`{rss ? <link rel="alternate" href={url_for(rss)} title={config.title} type="application/atom+xml" /> : null}`


#### config.head.favicon

head:
    # URL or path to the website's icon
    favicon: /assets/images/favicon_l.png

`{favicon ? <link rel="icon" href={url_for(favicon)} /> : null}`

##### article

article:
    # Code highlight settings
    highlight:
        # Code highlight themes
        # https://github.com/highlightjs/highlight.js/tree/master/src/styles
        theme: atom-one-light



##### article highlight theme

highlight

variant = 'default'
`# the theme variant 'default' or 'cyberpunk'`

see [cnd](#cdn-fontcdn-and-iconcdn)

let hlTheme, images;
        if (highlight && highlight.enable === false) {
            hlTheme = null;
        } else if (article && article.highlight && article.highlight.theme) {
            hlTheme = article.highlight.theme;
        } else {
            hlTheme = 'atom-one-light';
        }


##### title

config.title 
site title

### page

```js
page: {
    base: '',
    total: 1,
    current: 1,
    current_url: '',
    posts: _Query { data: [Array], length: 5 },
    prev: 0,
    prev_link: '',
    next: 0,
    next_link: '',
    __index: true,
    path: 'index.html',
    lang: 'en',
    canonical_path: 'index.html'
  }
```

#### article (page)


Variable	Description	Type
page.title	Article title	string
page.date	Article created date	Moment.js object
page.updated	Article last updated date	Moment.js object
page.comments	Comment enabled or not	boolean
page.layout	Layout name	string
page.content	The full processed content of the article	string
page.excerpt	Article excerpt	string
page.more	Contents except article excerpt	string
page.source	The path of the source file	string
page.full_source	Full path of the source file	string
page.path	The URL of the article without root URL. We usually use url_for(page.path) in theme.	string
page.permalink	Full (encoded) URL of the article	string
page.prev	The previous post, null if the post is the first post	???
page.next	The next post, null if the post is the last post	???
page.raw	The raw data of the article	???
page.photos	The photos of the article (Used in gallery posts)	array of ???
page.link	The external link of the article (Used in link posts)	string

#### Post (post): 

Same as page layout but add the following variables.

Variable	Description	Type
page.published	True if the post is not a draft	boolean
page.categories	All categories of the post	array of ???
page.tags	All tags of the post	array of ???

#### Home (index)

Variable	Description	Type
page.per_page	Posts displayed per page	number
page.total	Total number of pages	number
page.current	Current page number	number
page.current_url	The URL of current page	string
page.posts	Posts in this page (Data Model)	object
page.prev	Previous page number. 0 if the current page is the first.	number
page.prev_link	The URL of previous page. '' if the current page is the first.	string
page.next	Next page number. 0 if the current page is the last.	number
page.next_link	The URL of next page. '' if the current page is the last.	string
page.path	The URL of current page without root URL. We usually use url_for(page.path) in theme.	string

#### Archive (archive): 
Same as index layout but add the following variables.

Variable	Description	Type
page.archive	Equals true	boolean
page.year	Archive year (4-digit)	number
page.month	Archive month (2-digit without leading zeros)	number

##### page.month page.year


#### Category (category):
Same as index layout but add the following variables.

Variable	Description	Type
page.category	Category name	string

#### Tag (tag): 
Same as index layout but add the following variables.

Variable	Description	Type
page.tag	Tag name	string

##### page.permalink

Full (encoded) URL of the article	string

canonical_url = page.permalink

`{canonical_url ? <link rel="canonical" href={canonical_url} /> : null}`




## hexo theme helpers

```js
helper: {
    date: [Function: bound dateHelper],
    date_xml: [Function: bound toISOString],
    time: [Function: bound timeHelper],
    full_date: [Function: bound fullDateHelper],
    relative_date: [Function: bound relativeDateHelper],
    time_tag: [Function: bound timeTagHelper],
    moment: [Function: bound hooks],
    search_form: [Function: bound moized(searchFormHelper)],
    strip_html: [Function: bound striptags],
    trim: [Function: bound ],
    titlecase: [Function: bound toTitleCase],
    word_wrap: [Function: bound wordWrap],
    truncate: [Function: bound truncate],
    escape_html: [Function: bound escapeHTML],
    fragment_cache: [Function: bound fragmentCache],
    gravatar: [Function: bound gravatarHelper],
    is_current: [Function: bound isCurrentHelper],
    is_home: [Function: bound isHomeHelper],
    is_home_first_page: [Function: bound isHomeFirstPageHelper],
    is_post: [Function: bound isPostHelper],
    is_page: [Function: bound isPageHelper],
    is_archive: [Function: bound isArchiveHelper],
    is_year: [Function: bound isYearHelper],
    is_month: [Function: bound isMonthHelper],
    is_category: [Function: bound isCategoryHelper],
    is_tag: [Function: bound isTagHelper],
    list_archives: [Function: bound listArchivesHelper],
    list_categories: [Function: bound listCategoriesHelper],
    list_tags: [Function: bound listTagsHelperFactory],
    list_posts: [Function: bound listPostsHelper],
    meta_generator: [Function: bound metaGeneratorHelper],
    open_graph: [Function: bound openGraphHelper],
    number_format: [Function: bound numberFormatHelper],
    paginator: [Function: bound paginatorHelper],
    partial: [Function: bound partial],
    markdown: [Function: bound markdownHelper],
    render: [Function: bound render],
    css: [Function: bound moized(cssHelper)],
    js: [Function: bound moized(jsHelper)],
    link_to: [Function: bound linkToHelper],
    mail_to: [Function: bound moized(mailToHelper)],
    image_tag: [Function: bound imageTagHelper],
    favicon_tag: [Function: bound faviconTagHelper],
    feed_tag: [Function: bound feedTagHelper],
    tagcloud: [Function: bound tagcloudHelperFactory],
    tag_cloud: [Function: bound tagcloudHelperFactory],
    toc: [Function: bound tocHelper],
    relative_url: [Function: bound ],
    url_for: [Function: bound ],
    full_url_for: [Function: bound ],
    inspect: [Function: bound inspectObject],
    log: [Function: bound log],
    cdn: [Function: bound ],
    fontcdn: [Function: bound ],
    iconcdn: [Function: bound ],
    is_categories: [Function: bound ],
    is_tags: [Function: bound ],
    __: [Function (anonymous)],
    _p: [Function (anonymous)]
  }
```




#### Templates
partial
Loads other template files. You can define local variables in locals.

<%- partial(layout, [locals], [options]) %>
Option	Description	Default
cache	Cache contents (Use fragment cache)	false
only	Strict local variables. Only use variables set in locals in templates.	false
fragment_cache
Caches the contents in a fragment. It saves the contents within a fragment and serves the cache when the next request comes in.

<%- fragment_cache(id, fn);
Examples:

<%- fragment_cache('header', function(){
  return '<header></header>';
}) %>

#### Conditional Tags
is_current
Check whether path matches the URL of the current page. Use strict options to enable strict matching.

<%- is_current(path, [strict]) %>
is_home
Check whether the current page is home page.

<%- is_home() %>
is_post
Check whether the current page is a post.

<%- is_post() %>
is_archive
Check whether the current page is an archive page.

<%- is_archive() %>
is_year
Check whether the current page is a yearly archive page.

<%- is_year() %>
is_month
Check whether the current page is a monthly archive page.

<%- is_month() %>
is_category
Check whether the current page is a category page.
If a string is given as parameter, check whether the current page match the given category.

<%- is_category() %>
<%- is_category('hobby') %>

is_tag
Check whether the current page is a tag page.
If a string is given as parameter, check whether the current page match the given tag.

<%- is_tag() %>
<%- is_tag('hobby') %>

##### helper.is_post()

helper.is_archive()

https://lucfe2010.github.io/lucfe-hexo/archives/

helper.is_month()

https://lucfe2010.github.io/lucfe-hexo/archives/2023/09/

helper.is_year()

https://lucfe2010.github.io/lucfe-hexo/archives/2023/


##### helper._p()

Templates
Use __ or _p helpers in templates to get the translated strings. The former is for normal usage and the latter is for plural strings. For example:

en.yml
index:
  title: Home
  add: Add
  video:
    zero: No videos
    one: One video
    other: %d videos
<%= __('index.title') %>
// Home

<%= _p('index.video', 3) %>
// 3 videos

---

helper._p('common.archive', Infinity);

if (helper.is_tag()) {
        title = helper._p('common.tag', 1) + ': ' + page.tag;
    }

if (helper.is_categories()) {
        title = helper._p('common.category', Infinity);}




#### URL
url_for
Returns a url with the root path prefixed. You should use this helper instead of config.root + path since Hexo 2.7.

<%- url_for(path) %>

gravatar
Inserts a Gravatar image.

<%- gravatar('a@abc.com' {s: 40, d: 'http://example.com/image.png'}) %>
// http://www.gravatar.com/avatar/b9b00e66c6b8a70f88c73cb6bdb06787?s=40&d=http%3A%2F%2Fexample.com%2Fimage.png


##### url_for

##### cdn fontcdn and iconcdn

cdn()

`{hlTheme ? <link rel="stylesheet" href={cdn('highlight.js', '11.7.0', 'styles/' + hlTheme + '.css')} /> : null}`

[hlTheme](#highlight-theme)

fontcdn()

```jsx
<link rel="stylesheet" href={fontCssUrl[variant]} />

const fontCssUrl = {
            default: fontcdn('Ubuntu:wght@400;600&family=Source+Code+Pro', 'css2'),
            cyberpunk: fontcdn('Oxanium:wght@300;400;600&family=Roboto+Mono', 'css2')
        };
```

iconcdn()

`<link rel="stylesheet" href={iconcdn()} />`


#### HTML Tags

css

<%- css('style.css') %>
// <link rel="stylesheet" href="/style.css" type="text/css">


js

<%- js('script.js') %>
// <script type="text/javascript" src="/script.js"></script>

link_to

<%- link_to('http://www.google.com', 'Google', {external: true}) %>
// <a href="http://www.google.com" title="Google" target="_blank" rel="external">Google</a>


image_tag
favicon_tag
feed_tag

#### List

##### list_categories
Inserts a list of all categories.

<%- list_categories([options]) %>
Option	Description	Default
orderby	Order of categories	name
order	Sort of order. 1, asc for ascending; -1, desc for descending	1
show_count	Display the number of posts for each category	true
style	Style to display the category list. list displays categories in an unordered list.	list
separator	Separator between categories. (Only works if style is not list)	,
depth	Levels of categories to be displayed. 0 displays all categories and child categories; -1 is similar to 0 but displayed in flat; 1 displays only top level categories.	0
class	Class name of category list.	category
transform	The function that changes the display of category name.	
suffix	Add a suffix to link.	None


##### list_tags
Inserts a list of all tags.

<%- list_tags([options]) %>
Option	Description	Default
orderby	Order of categories	name
order	Sort of order. 1, asc for ascending; -1, desc for descending	1
show_count	Display the number of posts for each tag	true
style	Style to display the tag list. list displays tags in an unordered list.	list
separator	Separator between categories. (Only works if style is not list)	,
class	Class name of tag list.	tag
transform	The function that changes the display of tag name.	
amount	The number of tags to display (0 = unlimited)	0
suffix	Add a suffix to link.	None

##### list_archives
Inserts a list of archives.

<%- list_archives([options]) %>
Option	Description	Default
type	Type. This value can be yearly or monthly.	monthly
order	Sort of order. 1, asc for ascending; -1, desc for descending	1
show_count	Display the number of posts for each archive	true
format	Date format	MMMM YYYY
style	Style to display the archive list. list displays archives in an unordered list.	list
separator	Separator between archives. (Only works if style is not list)	,
class	Class name of archive list.	archive
transform	The function that changes the display of archive name.	


##### list_posts
Inserts a list of posts.

<%- list_posts([options]) %>
Option	Description	Default
orderby	Order of posts	date
order	Sort of order. 1, asc for ascending; -1, desc for descending	1
style	Style to display the post list. list displays posts in an unordered list.	list
separator	Separator between posts. (Only works if style is not list)	,
class	Class name of post list.	post
amount	The number of posts to display (0 = unlimited)	6
transform	The function that changes the display of post name.	


##### tagcloud
Inserts a tag cloud.

<%- tagcloud([tags], [options]) %>
Option	Description	Default
min_font	Minimal font size	10
max_font	Maximum font size	20
unit	Unit of font size	px
amount	Total amount of tags	40
orderby	Order of tags	name
order	Sort order. 1, sac as ascending; -1, desc as descending	1
color	Colorizes the tag cloud	false
start_color	Start color. You can use hex (#b700ff), rgba (rgba(183, 0, 255, 1)), hsla (hsla(283, 100%, 50%, 1)) or color keywords. This option only works when color is true.	
end_color	End color. You can use hex (#b700ff), rgba (rgba(183, 0, 255, 1)), hsla (hsla(283, 100%, 50%, 1)) or color keywords. This option only works when color is true.

#### Miscellaneous
paginator
Inserts a paginator.

<%- paginator(options) %>
Option	Description	Default
base	Base URL	/
format	URL format	page/%d/
total	The number of pages	1
current	Current page number	0
prev_text	The link text of previous page. Works only if prev_next is set to true.	Prev
next_text	The link text of next page. Works only if prev_next is set to true.	Next
space	The space text	&hellp;
prev_next	Display previous and next links	true
end_size	The number of pages displayed on the start and the end side	1
mid_size	The number of pages displayed between current page, but not including current page	2
show_all	Display all pages. If this is set true, end_size and mid_size will not works.	false


toc
Parses all heading tags (h1~h6) in the content and inserts a table of contents.

#### Date & Time
date
Inserts formatted date. date can be unix time, ISO string, date object, or Moment.js object. format is date_format setting by default.

<%- date(date, [format]) %>
Examples:

<%- date(Date.now()) %>
// 2013-01-01

<%- date(Date.now(), 'YYYY/M/D') %>
// Jan 1 2013
date_xml
Inserts date in XML format. date can be unix time, ISO string, date object, or Moment.js object.

<%- date_xml(date) %>
Examples:

<%- date_xml(Date.now()) %>
// 2013-01-01T00:00:00.000Z
time
Inserts formatted time. date can be unix time, ISO string, date object, or Moment.js object. format is time_format setting by default.

<%- time(date, [format]) %>
Examples:

<%- time(Date.now()) %>
// 13:05:12

<%- time(Date.now(), 'h:mm:ss a') %>
// 1:05:12 pm
full_date
Inserts formatted date and time. date can be unix time, ISO string, date object, or Moment.js object. format is date_format + time_format setting by default.

<%- full_date(date, [format]) %>
Examples:

<%- full_date(new Date()) %>
// Jan 1, 2013 0:00:00

<%- full_date(new Date(), 'dddd, MMMM Do YYYY, h:mm:ss a') %>
// Tuesday, January 1st 2013, 12:00:00 am

<%- toc(str, [options]) %>
Option	Description	Default
class	Class name	toc
list_number	Displays list number	true
max_depth	Maximum heading depth of generated toc	6
Examples:

<%- toc(page.content) %>


## inferno 

### Component

```jsx
Class component:

import { Component } from 'inferno';

class MyComponent extends Component {
  render() {
    ...
  }
}
```

### class declare

```js
export declare class Component<P = {}, S = {}> implements IComponent<P, S> {
    state: S | null;
    props: {
        children?: InfernoNode;
    } & P;
    context: any;
    displayName?: string;
    refs?: any;

    ...

    constructor(props?: P, context?: any);

    ...

    render(_nextProps: P, _nextState: S, _nextContext: any): InfernoNode | undefined;
}
```

This is the base class for Inferno Components when they're defined using ES6 classes.

## icarus theme COMPONENTS



### js regex Pattern

```jsx
let img;
const imgPattern = /<img [^>]*src=['"]([^'"]+)([^>]*>)/gi;
img = imgPattern.exec(page.content);
```




### body

the rendered html from another layout files.
也就是layout文件夹第一层的中去除`layout.jsx`的其他`*.jsx`文件





### OpenGraph and Structured Data

```jsx
<OpenGraph
    type="blog"
    title="Page title"
    language="Page language"
    description="Page description"
    date="Page publish date"
    updated="Page update date"
    author="Page author"
    keywords="keyword1,keyword2,..."
    images={[ '/path/to/image.png' ]}
    url="/path/to/page"
    siteName="Site name"
    twitterId="Twitter ID"
    twitterCard="summary"
    twitterSite="Twitter Site"
    googlePlus="/path/to/google/plus"
    facebookAdmins="Facebook admin ID"
    facebookAppId="Facebook APP ID" />



<StructuredData
    title="Page title"
    url="/page/url"
    author="Page author name"
    publisher="Page publisher name"
    publisherLogo="/path/to/logo"
    description="Page description"
    images={[ '/path/to/image' ]}
    date="Page publish date"
    updated="Page update date" />
```

### meta tags

```jsx
<MetaTags meta={meta} />

<Meta meta={[
    'name="generator";content="Hexo 4.2.0"'
    'property="article:author";content="PPOffice"'
]} />
```


### WebApp

```jsx
<WebApp
    name="******"
    manifest="/path/to/manifest.json"
    tileIcon="/path/to/image"
    themeColor="#000000"
    icons={[
        { src: '/path/to/image', sizes: '128x128 256x256' },
        { src: '/path/to/image', sizes: '512x512' },
    ]} />
```

### followIt

`{followItVerificationCode ? <meta name="follow.it-verification-code" content={followItVerificationCode} /> : null}`

let followItVerificationCode = null;
        if (Array.isArray(config.widgets)) {
            const widget = config.widgets.find(widget => widget.type === 'followit');
            if (widget) {
                followItVerificationCode = widget.verification_code;
            }
        }


## hexo theme develop example

languages 文件夹放有一个或多个语言文件。

layout 文件夹下面用于存放页面文件，通常第一层有 Index 首页 、 Archive 归档页 、 Tag 标签页 、 Category 分类页 、 Post 文章页 、 Page 页面详情页 、 layout 布局 ，一般还会创建一个公共页面的文件夹，该文件夹用于放置一个页面的部分内容，用于复用。

source 文件夹用于放一些资源文件，例如： 字体 、 CSS 、 JS 、 图片 等，也会根据他们的文件类型进行再次分类，图片放到图片的文件夹，JS 放到 JS 的文件夹。


先从 layout.ejs 文件开始，该文件是布局文件，其他页面都按照其来进行渲染，编写时遵循 HTML5 规范

```ejs
<!DOCTYPE html>
<html lang="<%= config.language %>">
<head>
    <%- partial('common/head') %>
</head>
<body>
    <%- partial('common/header') %>
    <div class="wrapper">
        <%- body %>
    </div>
    <%- partial('common/footer') %>
</body>
</html>
```

config.language 表示使用根目录配置文件中 language 属性，假设配置文件中该属性填的是 zh-CN ，则最终渲染成 <html lang="zh-CN"> 。

partial() 用于引入公共布局，当引用后，每个页面都会存在你引用的这个布局，上面一共引用了三个文件 head 、 header 、 footer ，三个文件都在 common 文件夹下，这时候应该建立该文件夹，并在下面创建对应的三个 ejs 文件。假设 head.ejs 中的内容为 this is head ，最终渲染成如下：（每个页面都会存在此内容）
<head>
    this is head
</head>
<%- body %> 表示其他页面内容，例如： index.ejs 、 archive.ejs 等，假设 index.ejs 内容为 this is index ，则最终渲染成如下：（因为是写在首页文件中，所以只有首页会存在该内容）
<div class="wrapper">
    this is index
</div>


### Hexo 预置数据 即变量
post.ejs 文件内容如下：

<div class="post">
    <h1><%= page.title %></h1>
    <p><%= page.tip %></p>
    <div class="post-content">
        <%- page.content %>
    </div>
</div>
一篇 md 文章内容如下：

```md
---
title: 这是一篇文章
tip: hexo 开发

---

主内容...
文章页面最终渲染成：
```


```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    head
</head>
<body>
    header
    <div class="wrapper">
        <div class="post">
            <h1>这是一篇文章</h1>
            <p>hexo 开发</p>
            <div class="post-content">
                主内容...
            </div>
        </div>
    </div>
    footer
</body>
</html>
```


### 下面做一个 关于 页面的例子：

首先在根目录资源文件夹创建一个名为 about 的文件夹，再到该文件夹下创建一个 index.md 文件，内容为：

```md
---
title: 关于
type: 'about'
---
这是一个关于页面内容
```

到主题文件夹中布局文件夹中创建一个 about.ejs 页面，内容为：

<div class="about-page">
    <h1><%= page.title %></h1>
    <p><%- page.content %></p>
</div>
在 page.ejs 中引入 about.ejs
<% if (is_page() && page.type === 'about') { %>	// 该文件是其他页面的集合，所以得判断啥情况引入啥文件
	<%- partial('about') %>
<% } %>

// 假设引入友情链接文件
<% if (is_page() && page.type === 'links') { %>	// is_page() 是啥请看官方文档 - 辅助函数
	<%- partial('links') %>
<% } %>
最终渲染结果
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    head
</head>
<body>
    header
    <div class="wrapper">
        <div class="about-page">
            <h1>关于</h1>
            <p>这是一个关于页面内容</p>
        </div>
    </div>
    footer
</body>
</html>


### 列表

官方文档中有 list_categories 、 list_posts 等函数，都有具体的使用方法，在这里对于列表我写出我常用的方法。

文章列表：

对于文章通常有两种，一种是每页只显示 config.per_page 数量的文章，带有分页，另外一种是一个页面显示所有文章。

// 带分页，使用 Hexo 预置变量 page.posts
<% page.posts.each(function(post) { %>	// 因为这里有个对象 post
	<h1><% post.title %></h1>	// 所以这里才可以用 post.title
	<%- partial('common/post-card', {post: post}) %>	// 这时引用一个文件
<% }); %>

post-card 文件内容为：
<div class="post-card">
    <%= post.title %>	// 这里是会报错的，无法通过
</div>



// 一个页面显示所有文章
<% site.posts.each(function(post) { %>
	<h1><% post.title %></h1>
	<%- partial('common/post-card', {post: post}) %>
<% }); %>

### 主题中原有的 category.ejs 和 tag.ejs 文件都是属于单个对象的页面

category.ejs 页面只显示单个分类，当你点击分类 1 跳转过去的页面就是 category ，它不会显示出网站中所有的分类。

想要全部显示出来，需要自行创建一个页面categories 、 tags




