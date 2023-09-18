---
title: html learning
categories: [0004 Formal science, 计算机科学技术 Computer science]
tags: [html, web development]
---
## 转义字符

HTML中<，>，&等有特殊含义（<，>，用于链接签，&用于转义），不能直接使用。这些符号是不显示在我们最终看到的网页里的，那如果我们希望在网页中显示这些符号，就要用到HTML转义字符串（Escape Sequence）

显示 说明 实体名称 实体编号
 空格 &nbsp; &#160;
< 小于 &lt; &#60;
> 大于 &gt; &#62;
& &符号 &amp; &#38;
" 双引号 &quot; &#34;
© 版权 &copy; &#169;
® 已注册商标 &reg; &#174;
™ 商标（美国） ™ &#8482;
× 乘号 &times; &#215;
÷ 除号 &divide; &#247;

## overview of HTML

HyperText Markup Language, or HTML, is the standard markup language for describing the structure of documents displayed on the web.

HTML documents are basically a tree of nodes, including HTML elements and text nodes.

HTML elements provide the semantics and formatting for documents, including creating paragraphs, lists and tables, and embedding images and form controls.

### Elements

HTML consists of a series of elements, which you use to enclose, or wrap, different parts of the content to make it appear or act in a certain way.

example:

![Alt text](/assets/images/html/image.png)

Elements and tags aren't the exact same thing, though many people use the terms interchangeably.
The tag name is the content in the brackets. The tag includes the brackets. In this case, `<h1>`. An "element" is the opening and closing tags, and all the content between those tags, including nested elements.

When nesting elements, it's important that they are ***properly nested***. HTML tags should be closed in the reverse order of which they were opened. In the above example, notice how the `<em>` is both opened and closed within the opening and closing `<strong>` tags, and the `<strong>` is both open and closed within the `<p>` tags.

```html
<p>This paragraph has some
  <strong><em>strongly emphasized</em></strong>
  content</p>
```

while it is valid to omit tags, don't.

#### Non-replaced elements

Non-replaced elements have opening and (sometimes optional) closing tags that surround them and may include text and other tags as sub-elements.

#### Replaced and void elements

Replaced elements are replaced by objects, be it a graphical user interface (UI) widget in the case of most form controls, or a raster or scalable image file in the case of most images.

example: the two replaced elements `<img>` and `<input>` are replaced by non-text content: an image and a graphical user interface object, respectively.

```html
<input type="range">
<img src="switch.svg" alt="light switch">
```

---

Void elements are all self-closing elements and are represented by one tag. This means there is no such thing as a closing tag for a void element. Optionally, you can include a slash at the end of the tag, which many people find makes markup easier to read.

example, we self close the tag with a slash:

```html
<input type="range"/>
<img src="switch.svg" alt="light switch"/>
```

---

Replaced elements and void elements are often confused.

Most replaced elements are void elements, but not all. The video, picture, object, and iframe elements are replaced, but aren't void. They can all contain other elements or text, so they all have a closing tag.

Most void elements are replaced; but again, not all, as we saw with base, link, param, and meta.

### Attributes

These extra bits of space-separated name/value pairs (though sometimes including a value is optional) are called attributes.

Attributes provide information about the element. The attribute, like the rest of the opening tag, won't appear in the content, but they do help define how the content will appear to both your sighted and non-sighted (assistive technologies and search engines) users.

The opening tag always starts with the element type. The type can be followed by zero or more attributes, separated by one or more spaces. Most attribute names are followed by an equal sign equating it with the attribute value, wrapped with opening and closing quotation marks.

![Alt text](/assets/images/html/image-1.png)

some attributes are global—meaning they can appear within any element's opening tag. Some apply only to several elements but not all, and others are element-specific, relevant only to a single element.

---

Most attributes are name/value pairs. Boolean attributes, whose value is true, false, or the same as the name of the attribute, can be included as just the attribute: the value is not necessary.

`<img src="switch.svg" alt="light switch" ismap />`

---

If the value includes a space or special characters, quotes are needed. For this reason, quoting is always recommended.
for legibility, quotes and spaces are recommended, and appreciated.

---

Values that are defined in the specification are case-insensitive. Strings that are not defined as keywords are generally case-sensitive, including id and class values.

> Note that if an attribute value is case-sensitive in HTML, it is case-sensitive when used as part of an attribute selector in CSS and in JavaScript.

it is recommended, but not required, to mark up your HTML using lowercase letters for all your element names and attribute names within your tags, and quote all attribute values.

### Appearance of elements

HTML should be used to structure content, not to define the content's appearance. Appearance is the realm of CSS.

While many elements that alter the appearance of content, such as `<h1>`, `<strong>`, and `<em>`, have a semantic meaning, the appearance can and generally will be changed with author styles.

```html
<h1>This header has both <strong>strong</strong> and <em>emphasized</em> content</h1>
```

### Element, attributes, and JavaScript

The Document Object Model (DOM) is the data representation of the structure and content of the HTML document. As the browser parses HTML, it creates a JavaScript object for every element and section of text encountered. These objects are called nodes—element nodes and text nodes, respectively.

HTML DOM API

HTMLElement

HTMLAnchorElement
HTMLImageElement

## Document structure

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>Machine Learning Workshop</title>
    <meta name="viewport" content="width=device-width" />
    <link rel="stylesheet" src="css/styles.css" />
    <link rel="icon" type="image/png" href="/images/favicon.png" />
    <link rel="alternate" href="https://www.machinelearningworkshop.com/fr/" hreflang="fr-FR" />
    <link rel="alternate" href="https://www.machinelearningworkshop.com/pt/" hreflang="pt-BR" />
    <link rel="canonical" href="https://www.machinelearning.com" />
  </head>
  <body>

    <!-- <script defer src="scripts/lightswitch.js"></script>-->
  </body>
</html>
```

HTML documents include a document type declaration and the `<html>` root element. Nested in the `<html>` element are the document head and document body.

While the head of the document isn't visible to the sighted visitor, it is vital to make your site function. It contains all the meta information, including information for search engines and social media results, icons for the browser tab and mobile home screen shortcut, and the behavior and presentation of your content.

### Add to every HTML document

#### `<!DOCTYPE html>`

The first thing in any HTML document is the preamble. For HTML, all you need is `<!DOCTYPE html>`. This may look like an HTML element, but it isn't. It's a special kind of node called "doctype". The doctype tells the browser to use standards mode. If omitted, browsers will use a different rendering mode known as quirks mode.

#### `<html>`

The `<html>` element is the root element for an HTML document. It is the parent of the `<head>` and `<body>`, containing everything in the HTML document other than the doctype. If omitted it will be implied, but it is important to include it, as this is the element on which the language of the content of the document is declared.

#### Content language

The lang language attribute added to the `<html>` tag defines the main language of the document. The value of the lang attribute is a two- or three-letter ISO language code followed by the region. The region is optional, but recommended, as a language can vary greatly between regions.

---

The lang attribute is not limited to the `<html>` tag. If there is text within the page that is in a language different from the main document language, the lang attribute should be used to identify exceptions to the main language within the document.

### Required components inside the `<head>`

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>Machine Learning Workshop</title>
    <meta name="viewport" content="width=device-width" />
  </head>
  <body>

  </body>
</html>
```

#### Character encoding

The very first element in the `<head>` should be the charset character encoding declaration. It comes before the title to ensure the browser can render the characters in that title and all the characters in the rest of the document.

---

The default encoding in most browsers is windows-1252, depending on the locale. However, you should use UTF-8, as it enables the one- to four-byte encoding of all characters, even ones you didn't even know existed. Also, it's the encoding type required by HTML5.

To set the character encoding to UTF-8, include:

`<meta charset="utf-8" />`

The character encoding is inherited into everything in the document, even `<style>` and `<script>`.

#### Document title

Your home page and all additional pages should each have a unique title. The contents for the document title, the text between the opening and closing `<title>` tags, are displayed in the browser tab, the list of open windows, the history, search results, and, unless redefined with `<meta>` tags, in social media cards.

`<title>Machine Learning Workshop</title>`

#### Viewport metadata

The other meta tag that should be considered essential is the viewport meta tag, which helps site responsiveness, enabling content to render well by default, no matter the viewport width.

it enables controlling a viewport's size and scale, and prevents the site's content from being sized down to fit a 960px site onto a 320px screen, it is definitely recommended.

`<meta name="viewport" content="width=device-width" />`
The preceding code means "make the site responsive, starting by making the width of the content the width of the screen".

In addition to width, you can set zoom and scalability, but they both default to accessible values. If you want to be explicit, include:
`<meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=1" />`

### Other `<head>` content

#### CSS

There are three ways to include CSS: `<link>`, `<style>`, and the *style attribute*.

Styles, either via `<link>` or `<style>`, or both, should go in the head. They will work if included in the document's body, but you want your styles in the head for performance reasons. That may seem counterintuitive, as you may think you want your content to load first, but you actually want the browser to know how to render the content when it is loaded. Adding styles first prevents the unnecessary repainting that occurs if an element is styled after it is first rendered.

---

including an external resource using a `<link>` element with the rel attribute set to stylesheet

The `<link>` tag is the preferred method of including stylesheets. Linking a single or a few external style sheets is good for both developer experience and site performance: you get to maintain CSS in one spot instead of it being sprinkled everywhere, and browsers can cache the external file, meaning it doesn't have to be downloaded again with every page navigation.

The syntax is `<link rel="stylesheet" href="styles.css">`, where styles.css is the URL of your stylesheet. You'll often see type="text/css". Not necessary! If you are including styles written in something other than CSS, the type is needed, but since there isn't any other type, this attribute isn't needed. The rel attribute defines the relationship: in this case stylesheet. If you omit this, your CSS will not be linked.

---

including CSS directly in the head of your document within opening and closing `<style>` tags.

 custom properties declared in a head style block:

```html
<style>
  :root {
    --theme-color: #226DAA;
  }
</style>
```

---
If you want your external style sheet styles to be within a cascade layer but you don't have access to edit the CSS file to put the layer information in it, you'll want to include the CSS with @import inside a `<style>`:

```html
<style>
  @import "styles.css" layer(firstLayer);
</style>
```

When using @import to import style sheets into your document, optionally into cascade layers, the @import statements must be the first statements in your `<style>`

#### Other uses of the `<link>` element

The link element is used to create relationships between the HTML document and external resources. Some of these resources may be downloaded, others are informational.

It's preferable to include those related to meta information in the head and those related to performance in the `<body>`.

You'll include three other types in your header now: icon, alternate, and canonical

##### Favicon

Use the `<link>` tag, with the `rel="icon"` attribute/value pair to identify the favicon to be used for your document.

A favicon is a very small icon that appears on the browser tab, generally to the left of the document title. When you have an unwieldy number of tabs open, the tabs will shrink and the title may disappear altogether, but the icon always remains visible. Most favicons are company or application logos.

If you don't declare a favicon, the browser will look for a file named favicon.ico in the top-level directory (the website's root folder). With `<link>`, you can use a different file name and location:

`<link rel="icon" sizes="16x16 32x32 48x48" type="image/png" href="/images/mlwicon.png" />`

The sizes attribute accepts the value of any for scalable icons or a space-separated list of square widthXheight values; where the width and height values are 16, 32, 48, or greater in that **geometric sequence**, the pixel unit is omitted, and the X is case-insensitive.

> While you can use `<link>` to define a completely different image on each page or even each page load, don't. For consistency and a good user experience, use a single image!

##### Alternate versions of the site

We use the alternate value of the rel attribute to identify translations, or alternate representations, of the site.

Let's pretend we have versions of the site translated into French and Brazilian Portuguese:
When using alternate for a translation, the hreflang attribute must be set.

```html
<link rel="alternate" href="https://www.machinelearningworkshop.com/fr/" hreflang="fr-FR" />
<link rel="alternate" href="https://www.machinelearningworkshop.com/pt/" hreflang="pt-BR" />
```

---

The alternate value is for more than just translations.

For example, the type attribute can define the alternate URI for an RSS feed when the type attribute is set to application/rss+xml or application/atom+xml.

example,  link to a pretend PDF version of the site.

`<link rel="alternate" type="application/x-pdf" href="https://machinelearningworkshop.com/mlw.pdf" />`

##### Canonical

If you create several translations or versions of Machine Learning Workshop, search engines may get confused as to which version is the authoritative source. For this, use rel="canonical" to identify the preferred URL for the site or application.

Include the canonical URL on all of your translated pages, and on the home page, indicating our preferred URL:

`<link rel="canonical" href="https://www.machinelearning.com" />`

> most often used for cross-posting with publications and blogging platforms to credit the original source; when a site syndicates content, it should include the canonical link to the original source.

#### Scripts

The `<script>` tag is used to include, well, scripts. The default type is JavaScript. If you include any other scripting language, include the type attribute with the mime type, or type="module" if it's a JavaScript module. Only JavaScript and JavaScript modules get parsed and executed.

JavaScript is not only render-blocking, but the browser stops downloading all assets when scripts are downloaded and doesn't resume downloading other assets until the JavaScript is executed.

reduce the blocking nature of JavaScript download and execution: defer and async. With defer, HTML rendering is not blocked during the download, and the JavaScript only executes after the document has otherwise finished rendering. With async, rendering isn't blocked during the download either, but once the script has finished downloading, the rendering is paused while the JavaScript is executed.

![Alt text](/assets/images/html/image-2.png)

example:

`<script src="js/switch.js" defer></script>`

Adding the defer attribute defers the execution of the script until after everything is rendered, preventing the script from harming performance. The async and defer attributes are **only valid on external scripts**.

#### Base

There is another element that is only found in the `<head>`. Not used very often, the `<base>` element allows setting a default link URL and target. The href attribute defines the base URL for all relative links.

The **target** attribute, valid on `<base>` as well as on links and forms, sets where those links should open.
The default of **_self** opens linked files in the same context as the current document.
Other options include **_blank**, which opens every link in a new window,
the **_parent** of the current content, which may be the same as self if the opener is not an iframe,
or **_top**, which is in the same browser tab, but popped out of any context to take up the entire tab.

example:
If our website found itself nested within an iframe on a site like Yummly, including the `<base>` element would mean when a user clicks on any links within our document, the link will load popped out of the iframe, taking up the whole browser window.

`<base target="_top" href="https://machinelearningworkshop.com" />`

> anchor links are resolved with `<base>`. The `<base>` effectively converts the link `<a href="#ref">` to `<a target="_top" href="https://machinelearningworkshop.com#ref">`, triggering an HTTP request to the base URL with the fragment attached.
>
> there can be only one `<base>` element in a document, and it should come before any relative URLs are used, including possible script or stylesheet references.

#### HTML comments

Anything between `<!-- and -->` will not be visible or parsed. HTML comments can be put anywhere on the page, including the head or body, with the exception of scripts or style blocks, where you should use JavaScript and CSS comments, respectively.

## Metadata

### Officially defined meta tags

There are two main types of meta tags: **pragma directives**, with the `http-equiv` attribute like the charset meta tag used to have, and **named meta types**, like the viewport meta tag with the `name` attribute that we discussed in the document structure section. Both the `name` and `http-equiv` meta types must include the content attribute, which defines the `content` for the type of metadata listed.

#### Pragma directives

The `http-equiv` attribute has as its value a pragma directive. These directives describe how the page should be parsed. Supported `http-equiv` values enable setting directives ***when you are unable to set HTTP headers directly***.

most of which have other methods of being set. For example, while you can include a language directive with `<meta http-equiv="content-language" content="en-us" />`,
`<meta charset=<charset>" />`

example 1 :
The most common pragma directive is the refresh directive.
While you can set a directive to refresh at an interval of the number of seconds set in the content attribute, and even redirect to a different URL, please don't.

`<meta http-equiv="refresh" content="60; https://machinelearningworkshop.com/regTimeout" />`

example 2 :
The most useful pragma directive is content-security-policy, which enables defining a content policy for the current document. Content policies mostly specify allowed server origins and script endpoints, which help guard against cross-site scripting attacks.

`<meta http-equiv="content-security-policy" content="default-src https:" />`

#### Named meta tags

The name attribute is the name of the metadata. In addition to `viewport`, you will probably want to include `description` and `theme-color`, but not `keywords`.

##### Keywords

Search engine optimization snake-oil salespeople abused the keywords meta tag by stuffing them with comma-separated lists of spam words instead of lists of relevant key terms, so search engines do not consider this metadata to be useful anymore. ***No need*** to waste time, effort, or bytes adding it.

##### Description

The description value, however, is super important for SEO; in addition to helping sites rank based on the content, the description content value is often what search engines display under the page's title in search results.

Several browsers, like Firefox and Opera, use this as the default description of bookmarked pages.

The description should be a short and accurate summary of the page's content.

`<meta name="description"
  content="Register for a machine learning workshop at our school for machines who can't learn good and want to do other stuff good too" />`

##### Robots

If you don't want your site to be indexed by search engines, you can let them know. `<meta name="robots" content="noindex, nofollow" />` tells the bots to not index the site and not to follow any links.

You don't need to include `<meta name="robots" content="index, follow" />` to request indexing the site and following links, as that is the default, unless HTTP headers say otherwise.

`<meta name="robots" content="index, follow" />`

##### Theme color

The `theme-color` value lets you define a color to customize the browser interface. The color value on the content attribute will be used by supporting browsers and operating systems, letting you provide a suggested color for the user agents that support coloring the title bar, tab bar, or other chrome components.

The theme color meta tag can include a media attribute enabling the setting of different theme colors based on media queries. The media attribute can be included in this meta tag only and is ignored in all other meta tags.

`<meta name="theme-color" content="#226DAA" />`

### Open Graph

Open Graph and similar meta tag protocols can be used to control how social media sites, like Twitter, LinkedIn, and Facebook, display links to your content.

If not included, social media sites will correctly grab the title of your page and the description from the description meta tag, the same information as search engines will present

When you post a link to MachineLearningWorkshop.com or web.dev on Facebook or Twitter, a card with an image, site title, and site description appears. The entire card is a hyperlink to the URL you provided.

Open Graph meta tags have two attributes each: the `property` attribute instead of the name attribute, and the `content` or value for that property. The property attribute is not defined in official specifications but is widely supported by applications that support the Open Graph protocol.

```html
<meta property="og:title" content="Machine Learning Workshop" />
<meta property="og:description" content="School for Machines Who Can't Learn Good and Want to Do Other Stuff Good Too" />
<meta property="og:image" content="http://www.machinelearningworkshop.com/image/all.png" />
<meta property="og:image:alt" content="Black and white line drawing of refrigerator, french door refrigerator, range, washer, fan, microwave, vaccuum, space heater and air conditioner" />
```

```html
<meta name="twitter:title" content="Machine Learning Workshop" />
<meta name="twitter:description" content="School for machines who can't learn good and want to do other stuff good too" />
<meta name="twitter:url" content="https://www.machinelearningworkshop.com/?src=twitter" />
<meta name="twitter:image:src" content="http://www.machinelearningworkshop.com/image/all.png" />
<meta name="twitter:image:alt" content="27 different home appliances" />
<meta name="twitter:creator" content="@estellevw" />
<meta name="twitter:site" content="@perfmattersconf" />
```

![Alt text](/assets/images/html/image-3.png)

### Other useful meta information

The manifest file can prevent an unwieldy header full of `<link>` and `<meta>` tags. We can create a manifest file, generally called manifest.webmanifest or manifest.json. We then use the handy `<link>` tag with a rel attribute set to manifest and the href attribute set to the URL of the manifest file:

`<link rel="manifest" href="/mlw.webmanifest" />`

## html page now

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>Machine Learning Workshop</title>
    <meta name="viewport" content="width=device-width" />
    <meta name="description" content="Register for a machine learning workshop at our school for machines who can't learn good and want to do other stuff good too" />
    <meta property="og:title" content="Machine Learning Workshop" />
    <meta property="og:description" content="School for Machines Who Can't Learn Good and Want to Do Other Stuff Good Too" />
    <meta property="og:image" content="http://www.machinelearningworkshop.com/image/all.png" />
    <meta property="og:image:alt" content="Black and white line drawing of refrigerator, french door refrigerator, range, washer, fan, microwave, vaccuum, space heater and air conditioner" />
    <meta name="twitter:title" content="Machine Learning Workshop" />
    <meta name="twitter:description" content="School for machines who can't learn good and want to do other stuff good too" />
    <meta name="twitter:url" content="https://www.machinelearningworkshop.com/?src=twitter" />
    <meta name="twitter:image:src" content="http://www.machinelearningworkshop.com/image/all.png" />
    <meta name="twitter:image:alt" content="27 different home appliances" />
    <meta name="twitter:creator" content="@estellevw" />
    <meta name="twitter:site" content="@perfmattersconf" />
    <link rel="stylesheet" src="css/styles.css" />
    <link rel="icon" type="image/png" href="/images/favicon.png" />
    <link rel="alternate" href="https://www.machinelearningworkshop.com/fr/" hreflang="fr-FR" />
    <link rel="alternate" href="https://www.machinelearningworkshop.com/pt/" hreflang="pt-BR" />
    <link rel="canonical" href="https://www.machinelearning.com" />
    <link rel="manifest" href="/mlwmanifest.json" />
  </head>
  <body>

    <!-- <script defer src="scripts/lightswitch.js"></script>-->
  </body>
</html>
```

## Semantic HTML

Semantic means "relating to meaning". Writing semantic HTML means using HTML elements to structure your content based on each element's meaning, not its appearance.

The first code snippet uses <div> and <span>, two elements with no semantic value.

```html
<div>
  <span>Three words</span>
  <div>
    <a>one word</a>
    <a>one word</a>
    <a>one word</a>
    <a>one word</a>
  </div>
</div>
<div>
  <div>
    <div>five words</div>
  </div>
  <div>
    <div>three words</div>
    <div>forty-six words</div>
    <div>forty-four words</div>
  </div>
  <div>
    <div>seven words</h2>
    <div>sixty-eight words</div>
    <div>forty-four words</div>
  </div>
</div>
<div>
   <span>five words</span>
</div>
```

Let's rewrite this code with semantic elements:

```html
<header>
  <h1>Three words</h1>
  <nav>
    <a>one word</a>
    <a>one word</a>
    <a>one word</a>
    <a>one word</a>
  </nav>
</header>
<main>
  <header>
    <h1>five words</h1>
  </header>
  <section>
    <h2>three words</h2>
    <p>forty-six words</p>
    <p>forty-four words</p>
  </section>
  <section>
    <h2>seven words</h2>
    <p>sixty-eight words</p>
    <p>forty-four words</p>
  </section>
</main>
<footer>
  <p>five words</p>
</footer>
```

Semantic markup isn't just about making markup easier for developers to read; it's mostly about making markup easy for automated tools to decipher. 

### Accessibility object model (AOM)

As the browser parses the content received, it builds the document object model (DOM) and the CSS object model (CSSOM). It then also builds an accessibility tree. Assistive devices, such as screen readers, use the AOM to parse and interpret content. The DOM is a tree of all the nodes in the document. The AOM is like a semantic version of the DOM.

#### The role attribute
The role attribute describes the role an element has in the context of the document. The role attribute is a global attribute—meaning it is valid on all elements—defined by the ARIA specification rather than the WHATWG HTML specification, where almost everything else in this series is defined.

### Semantic elements

Asking yourself, "Which element best represents the function of this section of markup?" will generally result in you picking the best element for the job. The element you choose, and therefore the tags you use, should be appropriate for the content you are displaying, as tags have semantic meaning.

## Headings and sections

### Site `<header>`

```html
<!-- start header -->
<div id="pageHeader">
  <div id="title">Machine Learning Workshop</div>
  <!-- navigation -->
  <div id="navigation">
    <a href="#reg">Register</a>
    <a href="#about">About</a>
    <a href="#teachers">Instructors</a>
    <a href="#feedback">Testimonials</a>
  </div>
  <!-- end navigation bar -->
</div>
<!-- end of header -->
```

While the `id` and `class` attributes provide hooks for styling and JavaScript, they add no semantic value for the screen reader and (for the most part) the search engines.

---

```html
<!-- start header -->
<div role="banner">
  <div role="heading" aria-level="1">Machine Learning Workshop</div>
  <div role="navigation">
    <a href="#reg">Register</a>
    <a href="#about">About</a>
    <a href="#teachers">Instructors</a>
    <a href="#feedback">Testimonials</a>
  </div>
  <!-- end navigation bar -->
<div>
<!-- end of header -->
```

This at least provides semantics and enables using attribute selectors in the CSS, but it still adds comments to identify which `<div>` each `</div>` ***closes***.

---

```html
<header>
  <h1>Machine Learning Workshop</h1>
  <nav>
    <a href="#reg">Register</a>
    <a href="#about">About</a>
    <a href="#teachers">Instructors</a>
    <a href="#feedback">Testimonials</a>
  </nav>
</header>
```


This code uses two semantic landmarks: `<header>` and `<nav>`.

The `<header>` element isn't always a landmark. It has different semantics depending on where it is nested. When the `<header>` is top level, it is the site banner, a landmark role, which you may have noted in the role code block. When a `<header>` is nested in `<main>`, `<article>`, or `<section>`, it just identifies it as the header for that section and isn't a landmark.

The `<nav>` element identifies content as navigation. As this `<nav>` is nested in the site heading, it is the main navigation for the site. If it was nested in an `<article>` or `<section>`, it would be internal navigation for that section only.

Using `</nav>` and `</header>` closing tags removes the need for comments to identify which element each end tag closed. In addition, using different tags for different elements removes the need for id and class hooks. The CSS selectors can have low specificity; you can probably target the links with header nav a without worrying about conflict.

### Site `<footer>`

```html
<footer>
  <p>&copy;2022 Machine Learning Workshop, LLC. All rights reserved.</p>
</footer>
```

Similar to `<header>`, whether the footer is a landmark depends on where the footer is nested. 


When it is the site footer, it is a landmark, and should contain the site footer information you want on every page, such as a copyright statement, contact information, and links to your privacy and cookie policies. The implicit role for the site footer is `contentinfo`. 


Otherwise, the footer has no implicit role and is not a landmark, When a `<footer>` is a descendant of an `<article>, <aside>, <main>`, `<nav>`, or `<section>`, it's not a landmark.

### Document structure

A layout with a header, two sidebars, and a footer, is known as the holy grail layout.

![Alt text](/assets/images/html/image-4.png)

```html
<body>
  <header>Header</header>
  <nav>Nav</nav>
  <main>Content</main>
  <aside>Aside</aside>
  <footer>Footer</footer>
</body>
```

a blog, you might have a series of articles in <main>:

```html
<body>
  <header>Header</header>
  <nav>Nav</nav>
  <main>
    <article>First post</article>
    <article>Second post</article>
  </main>
  <aside>Aside</aside>
  <footer>Footer</footer>
</body>
```

#### `<main>`

There's a single `<main>` landmark element. The `<main>` element identifies the main content of the document. There should be only one `<main>` per page.

#### `<aside>`

The `<aside>` is for content that is indirectly or tangentially related to the document's main content.
like most, the `<aside>` would likely be presented in a sidebar or a call-out box. The `<aside>` is also a landmark, with the implicit role of `complementary`.

#### `<article>`

An `<article>` represents a complete, or self-contained, section of content that is, in principle, independently reusable. 

Think of an article as you would an article in a newspaper.

#### `<section>`

The `<section>` element is used to encompass generic standalone sections of a document when there is no more specific semantic element to use. Sections should have a heading, with very few exceptions.

A `<section>` isn't a landmark unless it has an accessible name; if it has an accessible name, the implicit role is `region`.

Landmark roles should be used sparingly, to identify larger overall sections of the document. Using too many landmark roles can create "noise" in screen readers, making it difficult to understand the overall layout of the page.

### Headings: `<h1>-<h6>`

When a heading is nested in a document banner `<header>`, it is the heading for the application or site. When nested in `<main>`, whether or not it is nested within a `<header>` in `<main>`, it is the header for that page, not the whole site. When nested in an `<article>` or `<section>`, it is the header for that subsection of the page.

It is recommended to use heading levels similarly to heading levels in a text editor: starting with a `<h1>` as the main heading, with `<h2>` as headings for sub-sections, and `<h3>` if those sub-sections have sections; avoid skipping heading levels.