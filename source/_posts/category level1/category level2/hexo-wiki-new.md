---
title: hexo wiki
toc: true
categories: [category1 level1, category1 level2]
---
## hexo install and setup

### Install Hexo

Once all the requirements are installed, you can install Hexo with npm:

`$ npm install -g hexo-cli`

### setup

Once Hexo is installed, run the following commands to initialize Hexo in the target `<folder>`.

```bash
hexo init <folder>
cd <folder>
npm install
```

eg:

```bash
hexo init .
npm install
```

## icarus install and setup

### INSTALL from source

Download the source code tarball from the GitHub and extract it to your Hexo site’s theme directory. Alternatively, you can use Git to clone the Icarus repository to the themes directory:

Git Bash/Shell

`git clone https://github.com/ppoffice/hexo-theme-icarus.git themes/icarus -b <version number> --depth 1`

You can omit `-b <version number>` to get the latest development version of Icarus. Leave --depth 1 out if you want to download full Git commit history of Icarus as well.

eg:

`git clone https://github.com/ppoffice/hexo-theme-icarus.git themes/icarus --depth 1`

### icarus setup

1. 要将themes/icarus文件夹中的 package.json 中的 dependencies 内容拷贝并添加到主目录的package.json 中

2. Next, activate Icarus in your site’s _config.yml file:

   _config.yml

   ```yml
   theme: icarus
   ```

   or use the hexo command to change the theme to Icarus:
   Shell command:
   `hexo config theme icarus`

3. 然后

   `npm install`

4. 再

   use the hexo command to change the theme to Icarus:

   Shell
   `hexo config theme icarus`

5. 这时根据提示

   ```bsh
   ERROR Package hexo-renderer-stylus's version (3.0.0) does not satisfy the required version (^2.0.0).
   ERROR Please install the missing dependencies your Hexo site root directory:
   ERROR npm install --save hexo-renderer-stylus@^2.0.0
   ```

## git setup

create a new repository on the command line

eg:

```bash
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/lucfe2010/lucfe-hexo-private-1.git
git push -u origin main
```

注意提示

```bash
hint: You've added another git repository inside your current repository.
hint: Clones of the outer repository will not contain the contents of
hint: the embedded repository and will not know how to obtain it.
```

### 清除icarus主题文件夹的 GIT 和 GITHUB

使用 windows file explore删除 icarus主题文件夹 中的`.git`文件夹

然后

git rm -r --cached .
git add .

#### git 用法

git init
git add .
git commit -m "first commit"
git branch -M main
git push -u origin main

##### git remote

git remote -v：列出当前仓库中已配置的远程仓库，并显示它们的 URL。

- git remote add
`git remote add <remote_name> <remote_url>`
添加一个新的远程仓库。指定一个远程仓库的名称和 URL，将其添加到当前仓库中。如
`git remote add lucfe-clone https://github.com/lucfe2010/lucfe-hexo-61.git`
`git remote add origin https://github.com/lucfe2010/lucfe-private-91.git`

- git remote remove
`git remote remove <remote_name>`
`git remote remove origin`

## hexo config

### basic config

#### language

`language: cn`

#### site url

change the `url` to the website url of your own
`url: http://lucfe2010.github.io/lucfe-hexo`

### permalink

Permalinks
You can specify the permalinks for your site in _config.yml or in the front-matter for each post.

Variables
Besides the following variables, you can use any attributes in the permalink.

:category -> Categories. If the post is uncategorized, it will use the default_category value.

eg

Change
`permalink: ':year/:month/:day/:title/'`
to
`permalink: ':title/'`

### Global Asset Folder

Global Asset Folder
Assets are non-post files in the source folder, such as images, CSS or JavaScript files. For instance, If you are only going to have a few images in the Hexo project, then the easiest way is to keep them in a source/images directory. Then, you can access them using something like `![](/images/image.jpg)`.

#### For vscode copy images

Use vscode open the `source` folder as project folder to create and edit the posts

change the the image relative path link
`assets/images/<post title>/*.jpg`
or
`../../assets/images/<post title>/*.jpg`
to the project directory absolute path link
`/assets/images/<post title>/*.jpg`

#### dont use Post Asset Folder

or any kind of post asset image link plugin, there are lots of bugs!

## hexo server

With the release of Hexo 3, the server has been separated from the main module. To start using the server, you will first have to install hexo-server.

`$ npm install hexo-server --save`

Once the server has been installed, run the following command to start the server. Your website will run at `http://localhost:4000` by default. When the server is running, Hexo will watch for file changes and update automatically so it’s not necessary to manually restart the server.

`$ hexo server`

### Static Mode

In static mode, only files in the public folder will be served and file watching is disabled. You have to run hexo generate before starting the server. Usually used in production.

`$ hexo server -s`

## Git deploy

1. Install hexo-deployer-git.
   `$ npm install hexo-deployer-git --save`

2. Edit _config.yml (with example values shown below as comments):

   ```yml
   deploy:
     type: git
     repo: <repository url> # https://bitbucket.org/JohnSmith/johnsmith.bitbucket.io
     branch: [branch]
     message: [message]
   ```

   | Option  | Description                                                                                               | Default                                          |
   | ------- | --------------------------------------------------------------------------------------------------------- | ------------------------------------------------ |
   | repo    | URL of the target repository                                                                              |                                                  |
   | branch  | Branch name.                                                                                              | gh-pages (GitHub)                                |
   | message | Customize commit message.                                                                                 | Site updated: `{{ now('YYYY-MM-DD HH:mm:ss') }}` |
   | token   | Optional token value to authenticate with the repo. Prefix with $ to read token from environment variable |                                                  |

   eg

   ```yml
   deploy:
     type: git
     repo: https://github.com/lucfe2010/lucfe-hexo.git
     branch: master
     message: 
   ```

3. Deploy your site `hexo clean && hexo deploy`.

   - You will be prompted with username and password of the target repository, unless you authenticate with a token or ssh key.
   - `hexo-deployer-git` does not store your username and password. Use `git-credential-cache` to store them temporarily.

4. Navigate to your repository settings and change the “Pages” branch to gh-pages (or the branch specified in your config). The deployed site should be live on the link shown on the “Pages” setting.

## icarus config

### Logo

设置你站点的logo。 此logo会显示在导航栏和页脚。 logo配置的值既可以是你的logo图片的路径或URL地址：

_config.icarus.yml
`logo: /img/logo.svg`
也可以像下面这样设置成文字：

```yml
logo:
    text: My Beautiful Site
```

本站设为

```yml
logo:
    text: Lucfe Knowledges
```

### Favicon

你可以在head配置中指定你的网站favicon的路径或URL地址。

```yml
head:
    favicon: /img/favicon.svg
```

### RSS

你可以通过head部分的rss设置来添加RSS链接信息。

```yml
head:
    rss: /path/to/atom.xml
```

本站设为

```yml
head:
    rss: /atom.xml
```

### 导航栏

navbar部分定义了导航栏中的菜单与链接。 你可以通过向menu设置项中添加`<链接名>: <链接URL>`的方式添加任意导航栏菜单链接。 如要向导航栏右侧添加链接，请向links设置项中添加`<链接名>: <链接URL>`。

```yml
navbar:
    # 导航栏菜单项
    menu:
        Home: /
        Archives: /archives
        Categories: /categories
        Tags: /tags
        About: /about
    # 导航栏右侧的链接
    links:
        GitHub: 'https://github.com'
        Download on GitHub:
            icon: fab fa-github
            # url: 'https://github.com/ppoffice/hexo-theme-icarus'
            url: 'https://github.com/lucfe2010/lucfe-hexo'
```

你也可以使用FontAwesome图标来作为纯文字链接的替换，格式如下：

链接格式

```yml
<链接名>:
    icon: <FontAwesome图标的class名>
    url: <链接URL>
```

#### 页脚

footer部分定义了页脚右侧的链接。 链接的配置格式与navbar中links的配置格式完全一致。

你也可以在页脚展示自定义版权文字：\

```yml
footer:
    copyright: 用💖发电
```

### 文章

#### 封面 & 缩略图

若要为文章添加封面图，请在文章的front-matter中添加cover选项：

post.md

```md
title: Icarus快速上手
cover: /gallery/covers/cover.jpg
---
Post content...
```

类似地，你也可以在文章的front-matter中为文章设置缩略图：

post.md

```md
title: Icarus快速上手
thumbnail: /gallery/thumbnails/thumbnail.jpg

---
Post content...
```

文章的缩略图会显示在归档页面和最新文章挂件中。

如果你在front-matter中使用的是图片的路径，你需要确保它是绝对或者相对于你的source目录的路径。 例如，为使用`<your blog>/source/gallery/image.jpg`作为缩略图，你需要在front-matter中使用`/gallery/image.jpg`作为图片路径。

#### 文章许可协议

你可以在你的文章/页面的底部展示你的作品的使用许可，许可链接可以是文字或者图标。 这里的配置与导航栏或者页脚的links配置一致：

```yml
article:
    # 文章许可协议
    licenses:
        Creative Commons:
            icon: fab fa-creative-commons
            url: 'https://creativecommons.org/'
        'CC BY-NC-SA 4.0': 'https://creativecommons.org/licenses/by-nc-sa/4.0/'
```

#### 一些元数据

- 文章阅读时间
你可以将article部分的readtime设置为true来显示文章字数统计以及预计阅读时间。

- 文章更新时间
若要显示文章的更新时间，请在文章的front_matter中设置updated时间：

post.md

```md
title: Icarus快速上手
updated: 2020-04-01 00:00:00

---
Post content...
```

然后，将主题配置文件的article部分的update_time设置为true：

你也可以将update_time设置为false来隐藏所有文章的更新时间，或设置为auto而在文章的更新时间 与发布时间相同时隐藏更新时间。

- 文章许可协议
你可以在你的文章/页面的底部展示你的作品的使用许可，许可链接可以是文字或者图标。 这里的配置与导航栏或者页脚的links配置一致：

### wiget挂件

页面挂件的安装配置。 若要同时展示多个挂件，只需在主题配置的widgets数组中添加多个挂件配置。 它们会按照定义的顺序出现。 每个挂件必须包含type(挂件类型)与position(挂件展示位置)设置项。 示例如下：

```yml
widgets:
    -
        type: ... # 挂件1
        position: left
        ...
    -
        type: ... # 挂件2
        position: right
        ...
```

#### 布局配置文件

布局配置文件遵循着与主题配置文件相同的格式和定义。 `_config.post.yml`中的配置对所有文章生效，而`_config.page.yml`中的配置对所有自定义页面生效。 这两个文件将覆盖主题配置文件中的配置。

例如，你可以在_config.post.yml中把所有文章变为两栏布局：

```yml
widgets:
    -
        type: recent_posts
        position: left
    -
        type: categories
        position: left
    -
        type: tags
        position: left
```

同时所有其他页面仍保持三栏布局：

```yml
widgets:
    -
        type: recent_posts
        position: left
    -
        type: categories
        position: right
    -
        type: tags
        position: right
```

#### 作者资料卡profile

- 你可以启用作者资料卡挂件来展示文章作者/网站站长的信息。 资料卡的配置如下所示：

如果你希望使用Gravatar而不是avatar配置项作为头像图片，请在gravatar项填入 你的Gravatar邮箱地址并在avatar一项中留空；

本站使用的如下

![Alt text](/assets/images/avatar_l.png)

- social_links可以采用如下两种格式：

图标形式：

```yml
<链接名称>:
    icon: <FontAwesome5_图标的_HTML_class名称>
    url: <链接的URL地址>

```

文字形式：

`<链接名称>: <链接的URL地址>`

#### 文章目录 toc

需要开启目录的文章头部加入toc: true：

```md
title: 一篇有目录的文章
toc: true
---
文章内容...
```

#### 其他

##### 最新文章 recent posts

##### 文章归档 archives

##### 文章分类 categories

##### 文章标签 tags

```yml
widgets:
    -
        position: right
        type: tags
        order_by: name      # 可选项。按名称(name)或长度(length)来排序。加上`-`前缀来倒序排列。
        amount: 20          # 可选项。最多显示的标签数量。留空以显示所有标签。
        show_count: true    # 可选项。是否显示标签名称右侧的文章数量。
```

##### 友站链接 links

```yml
widgets:
    -
        position: left
        type: links
        # 友站名称与链接
        links:
            Hexo: 'https://hexo.io'
            Bulma: 'https://bulma.io'
```

##### plugin widgets

###### Google Feedburner

Google即将关闭Feedburner的邮件订阅功能。 你可以切换到follow.it挂件或者其他邮件订阅服务。

###### Google AdSense

在Google AdSense上新建广告。 然后，复制广告HTML代码中的data-ad-client和data-ad-slot值分别填入到挂件配置的client_id和slot_id项中。 示例如下：

```yml
widgets:
    -
        position: left
        type: adsense
        client_id: ca-pub-xxxxxxxx
        slot_id: xxxxxxx
```

###### install and set hexo-generator-feed

install

`$ npm install hexo-generator-feed --save`

You can configure this plugin in _config.yml.

```yml
feed:
  enable: true
  type: atom
  path: atom.xml
  limit: 20
  hub:
  content:
  content_limit: 140
  content_limit_delim: ' '
  order_by: -date
  icon: /assets/images/rss_icon_l.png
  autodiscovery: true
  template:
```

![Alt text](/assets/images/rss_icon_l.png)

###### follow.it

1. 使用诸如hexo-generator-feed此类的Hexo插件生成 你的Hexo网站的RSS源。

   `https://lucfe2010.github.io/lucfe-hexo/atom.xml`

2. 在FOLLOW.IT 网站一步步
   “定义关注表单设计”(Define the follow form’s design)页面上`already have a form`

   复制action=后双引号中的链接。 把你复制的action链接粘贴到挂件配置中的action_url设置项。

3. 在”连接你的源到follow.it账户“(Connect your feed to a follow.it account)页面上，在输入框中填入你将要用来注册follow.it账户 和管理订阅者的邮箱地址。

4. 你会收到一封来自follow.it的邮件。 在那封邮件中搜索`<meta name="follow_it-verification-code" content="******"/>`并复制content=后双引号中的content的值。 将你复制的值粘贴到挂件设置中的verification_code设置项。

   ![Alt text](/assets/images/hexo-wiki-new/image-3.png)

5. 回到你收到的第一封邮件并点击”点击这里来认领“(Click here to claim it)链接来认领你的订阅源。

![Alt text](/assets/images/hexo-wiki-new/image-4.png)

### icarus plugin seting

#### Google Analytics

在`追踪代码(Tracking Code)`界面上找到`Tracking ID`的值，例如”UA-12345678-0”. 将其填写到主题配置的`plugins > google_analytics > tracking_id`即可开启Google Analytics插件。

#### 用户评论

##### disqus

在评论服务首页的右上角点击“编辑配置”(Edit Settings)按钮。

![Alt text](/assets/images/hexo-wiki-new/image.png)

在“为你的站点配置Disqus”(Configure Disqus for Your Site)页面上找到“Shortname”的值， 复制到主题配置的评论配置项中。 例如，下面截图中的“Shortname”为my-hexo-blog-1：

![Alt text](/assets/images/hexo-wiki-new/image-1.png)

##### 畅言

![Alt text](/assets/images/hexo-wiki-new/image-5.png)

复制appid与conf的值到主题配置的对应配置项中。 例如，如下的HTML代码：

```html
<!--PC版-->
<div id="SOHUCS" sid="..."></div>
<script charset="utf-8" type="text/javascript" src="https://cy-cdn.kuaizhan.com/upload/changyan.js" ></script>
<script type="text/javascript">
window.changyan.api.config({
    appid: '????appid????',
    conf: 'prod_xxxxxxxxxxxxxxxxxxxxxxx'
});
</script>
```

对应到主题配置为：

```yml
comment:
    type: changyan
    app_id: appid
    conf: prod_xxxxxxxxxxxxxxxxxxxxxxx
```

#### 分享按钮

##### share this

copy the src URL from the HTML code fragment to the share button configuration.

![Alt text](/assets/images/hexo-wiki-new/image-2.png)

For example, the following ShareThis code:

`<script type="text/javascript" src="https://platform-api.sharethis.com/js/sharethis.js#property=xxxxxxxxxxxxx&product=inline-share-buttons" async="async"></script>`

maps to the following theme configuration:

```yml
share:
    type: sharethis
    install_url: https://platform-api.sharethis.com/js/sharethis.js#property=xxxxxxxxxxxxx&product=inline-share-buttons
```

## for china web connecting

### disable these plugins

business or payment
feedburn
google ad sense
google analytics
sharethis
changyan comments
disqus commnets
cookie consent
follow.it

### disable these links and font icons

article licsence links
footer links
navbar links

### CDN提供商 change cdn provider

内置CDN提供商
目前，Icarus提供如下的内置CDN服务提供商：

JavaScript库CDN
cdnjs.com (cdnjs)
jsDelivr (jsdelivr)
UNPKG (unpkg)
loli.net (loli)
Web字体CDN
Google Fonts (google)
loli.net (loli)
font.im (fontim)
中国科学技术大学 (ustc)
FontAwesome图标CDN
FontAwesome 5 (fontawesome)
loli.net (loli)

默认的CDN服务提供商配置为：

```yml
providers:
    cdn: jsdelivr
    fontcdn: google
    iconcdn: fontawesome
```

修改为：

```yml
providers:
    cdn: cdnjs
    fontcdn: loli
    iconcdn: loli
```
