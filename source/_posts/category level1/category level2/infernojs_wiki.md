---
title: inferno js wiki
toc: true
categories: [category1 level1, category1 level2]
---

{% raw %}

## Component

```jsx
Class component:

import { Component } from 'inferno';

class MyComponent extends Component {
  render() {
    ...
  }
}
```

## class declare

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

### props

#### site

```js
site: {
    posts: _Query { data: [Array], length: 5 },
    pages: _Query { data: [Array], length: 1 },
    categories: _Query { data: [Array], length: 5 },
    tags: _Query { data: [], length: 0 },
    data: {}
}
```

#### config

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



##### language

`<html lang={language ? language.substr(0, 2) : ''}>`

##### 
url,

##### 
head = {},

const {
    meta = [],
    manifest = {},
    open_graph = {},
    structured_data = {},
    canonical_url = page.permalink,
    rss,
    favicon
} = head;


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


{rss ? <link rel="alternate" href={url_for(rss)} title={config.title} type="application/atom+xml" /> : null}

head:
    # URL or path to the website's icon
    favicon: /assets/images/favicon_l.png

{favicon ? <link rel="icon" href={url_for(favicon)} /> : null}

##### 
article,

article:
    # Code highlight settings
    highlight:
        # Code highlight themes
        # https://github.com/highlightjs/highlight.js/tree/master/src/styles
        theme: atom-one-light



##### highlight theme
highlight,

variant = 'default'
the theme variant 'default' or 'cyberpunk'
see [cnd](#cdn-fontcdn-and-iconcdn)

let hlTheme, images;
        if (highlight && highlight.enable === false) {
            hlTheme = null;
        } else if (article && article.highlight && article.highlight.theme) {
            hlTheme = article.highlight.theme;
        } else {
            hlTheme = 'atom-one-light';
        }


##### 
config.title 
site title

#### page

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

page.content


##### canonical_url = page.permalink

{canonical_url ? <link rel="canonical" href={canonical_url} /> : null}

##### page.month page.year

##### 

#### body

the rendered html from another layout files.
也就是layout文件夹第一层的中去除`layout.jsx`的其他`*.jsx`文件

#### helper

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
##### helper._p('common.archive', Infinity);

if (helper.is_tag()) {
        title = helper._p('common.tag', 1) + ': ' + page.tag;
    }

if (helper.is_categories()) {
        title = helper._p('common.category', Infinity);}


##### url_for

##### cdn fontcdn and iconcdn

cdn()

{hlTheme ? <link rel="stylesheet" href={cdn('highlight.js', '11.7.0', 'styles/' + hlTheme + '.css')} /> : null}

[hlTheme](#highlight-theme)

fontcdn()
<link rel="stylesheet" href={fontCssUrl[variant]} />

const fontCssUrl = {
            default: fontcdn('Ubuntu:wght@400;600&family=Source+Code+Pro', 'css2'),
            cyberpunk: fontcdn('Oxanium:wght@300;400;600&family=Roboto+Mono', 'css2')
        };

iconcdn()
<link rel="stylesheet" href={iconcdn()} />



##### is_post

##### 

const noIndex = helper.is_archive() || helper.is_category() || helper.is_tag();

{noIndex ? <meta name="robots" content="noindex" /> : null}


##### helper.is_archive()

https://lucfe2010.github.io/lucfe-hexo/archives/

helper.is_month()

https://lucfe2010.github.io/lucfe-hexo/archives/2023/09/

helper.is_year()

https://lucfe2010.github.io/lucfe-hexo/archives/2023/


## imgPattern

let img;
const imgPattern = /<img [^>]*src=['"]([^'"]+)([^>]*>)/gi;
img = imgPattern.exec(page.content);


## page.photos
structured_data.image

images = [url_for('/img/og_image.png')];

## 

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

## 

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

## meta tags

<MetaTags meta={meta} />

<Meta meta={[
    'name="generator";content="Hexo 4.2.0"'
    'property="article:author";content="PPOffice"'
]} />

## <WebApp
    name="******"
    manifest="/path/to/manifest.json"
    tileIcon="/path/to/image"
    themeColor="#000000"
    icons={[
        { src: '/path/to/image', sizes: '128x128 256x256' },
        { src: '/path/to/image', sizes: '512x512' },
    ]} />




## followIt

{followItVerificationCode ? <meta name="follow.it-verification-code" content={followItVerificationCode} /> : null}

let followItVerificationCode = null;
        if (Array.isArray(config.widgets)) {
            const widget = config.widgets.find(widget => widget.type === 'followit');
            if (widget) {
                followItVerificationCode = widget.verification_code;
            }
        }



{% endraw %}