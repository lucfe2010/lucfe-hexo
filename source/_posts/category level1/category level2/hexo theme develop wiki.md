---
title: hexo theme wiki
---

{% raw %}

languages 文件夹放有一个或多个语言文件。

layout 文件夹下面用于存放页面文件，通常第一层有 Index 首页 、 Archive 归档页 、 Tag 标签页 、 Category 分类页 、 Post 文章页 、 Page 页面详情页 、 layout 布局 ，一般还会创建一个公共页面的文件夹，该文件夹用于放置一个页面的部分内容，用于复用。

source 文件夹用于放一些资源文件，例如： 字体 、 CSS 、 JS 、 图片 等，也会根据他们的文件类型进行再次分类，图片放到图片的文件夹，JS 放到 JS 的文件夹。


先从 layout.ejs 文件开始，该文件是布局文件，其他页面都按照其来进行渲染，编写时遵循 HTML5 规范


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

---
title: 这是一篇文章
tip: hexo 开发
---
主内容...
文章页面最终渲染成：

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


### 下面做一个 关于 页面的例子：

首先在根目录资源文件夹创建一个名为 about 的文件夹，再到该文件夹下创建一个 index.md 文件，内容为：
---
title: 关于
type: 'about'
---
这是一个关于页面内容
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
	<%- partial('common/post-card') %>	// 这时引用一个文件
<% }); %>

post-card 文件内容为：
<div class="post-card">
    <%= post.title %>	// 这里是会报错的，无法通过
</div>

需要修改引用为：
<%- partial('common/post-card', {post: post}) %>	// 把 post 传过去才可使用

// 若没有传过去，只能使用 page.title，因为 Hexo 中没有预置 post 这个东东，具体可查看文档
// 一个页面显示所有文章
<% site.posts.each(function(post) { %>
	<h1><% post.title %></h1>
	<%- partial('common/post-card', {post: post}) %>
<% }); %>

### 主题中原有的 category.ejs 和 tag.ejs 文件都是属于单个对象的页面

category.ejs 页面只显示单个分类，当你点击分类 1 跳转过去的页面就是 category ，它不会显示出网站中所有的分类。

想要全部显示出来，需要自行创建一个页面categories 、 tags

{% endraw %}