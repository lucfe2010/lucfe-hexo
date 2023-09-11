---
title: helowo

---



## nodejs 重新安装问题

![Alt text](/assets/images/hexo-wiki-new/image-6.png)

在windows下删除C:\Users\Sam\AppData\Roaming\npm 以及C:\Users\Sam\AppData\Roaming\npm-cache.

2.刷新环境变量 关于刷新环境，二选一就可以 方法一：重启电脑（耗时


```bash
PS C:\Users\lcf\Documents\lucfe_website> hexo init lucfe-hexo
hexo : 无法加载文件 C:\Users\lcf\AppData\Roaming\npm\hexo.ps1，因为在此系统上禁止运行脚本。有关详细信息，请参阅 https:/go.microsoft.com/fwlink/?
LinkID=135170 中的 about_Execution_Policies。
所在位置 行:1 字符: 1
+ hexo init lucfe-hexo
+ ~~~~
    + CategoryInfo          : SecurityError: (:) []，PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess

```

powershell执行命令时出错，提示权限问题，请更换为git bash

### Git中只克隆一个特定分支

git clone -b 分支名 --single-branch <repository url>

要在Git中只克隆一个特定分支，可以使用以下命令： 其中，“-b”选项指定要克隆的分支名称，“--single-branch”选项告诉Git只克隆指定的分支，而不是整个代码库。请将“<repository URL>”替换为要克隆的Git存储库的URL。

clone 
https
https://github.com/lucfe2010/lucfe-hexo-private.git

like:
git clone -b gh-pages --single-branch https://github.com/lucfe2010/lucfe-hexo-private.git


### git fetch

在远程分支上窥视，无需在本地存储库中配置远程
$ git fetch git://git.kernel.org/pub/scm/git/git.git maint

Shell
第一个命令从 git://git.kernel.org/pub/scm/git/git.git 从存储库中获取maint分支

如
git fetch https://github.com/lucfe2010/lucfe-hexo-private.git gh-pages

### git push

最后

添加远程仓库
先在github上创建一个仓库，复制仓库的HTTP地址，然后回到本地

origin_learn_git是给这个远程仓库取的别名，随便取

git remote add origin_learn_git https://github.com/DejaVuyan/learn_git.git



push到远程仓库
git push -u origin_learn_git main 将当前所在的分支推送到远端的main分支，

git push -u https://github.com/lucfe2010/lucfe-hexo.git gh-pages

## 使用 git subtree 如何将现有 git 仓库中的子目录分离为独立仓库并保留其提交历史

看来上述需求还是比较普遍的，自从 1.8 版本之后 git 就添加了 subtree 子命令，使用这个新命令我们可以很简单高效地解决这个问题。

首先，进入 big-repo 所在的目录，运行：

git subtree split -P <name-of-folder> -b <name-of-new-branch>

1.在主原仓库下执行 ---@!!!注意，要在主原仓库commit变动后才有变化update(主仓库有变动时 要刷新才能COMMIT)
git subtree split -P public -b hexo-public-folder

运行后，git 会遍历原仓库中所有的历史提交，挑选出与指定路径相关的 commit 并存入名为 name-of-new-branch 的临时分支中。另外需要注意的是，如果你在使用 Windows，且该文件夹深度 > 1，你必须使用斜杠 / 作为目录分隔符而不是默认的反斜杠 \。

然后，我们创建一个新的 git 仓库：

mkdir <new-repo>
git init


接着把原仓库中的临时分支拉到新仓库中：

git pull </path/to/big-repo> <name-of-new-branch>

2. 在lucfe-hexo-public/lucfe-hexo新仓库目录下
git pull ../ hexo-public-folder

好了，完成。现在看看你的新仓库，是不是已经包含了原子文件夹中的所有文件和你之前在原仓库中的所有提交历史呢？

3. 手动添加.nojekyll文件



### .gitignore不生效问题解决方法

第一种方法 .gitignore中已经标明忽略的文件目录下的文件，git push的时候还会出现在push的目录中，或者用git status查看状态，想要忽略的文件还是显示被追踪状态。 

原因是因为在git忽略目录中，新建的文件在git中会有缓存，如果某些文件已经被纳入了版本管理中，就算是在.gitignore中已经声明了忽略路径也是不起作用的，

 这时候我们就应该先把本地缓存删除，然后再进行git的提交，这样就不会出现忽略的文件了。 解决方法: git清除本地缓存（改变成未track状态），然后再提交: 

```bash
git rm -r --cached .
git add .
git commit -m 'update .gitignore'
git push -u origin master
```

需要特别注意的是：
 1）.gitignore只能忽略那些原来没有被track的文件，如果某些文件已经被纳入了版本管理中，则修改.gitignore是无效的。 
 2）想要.gitignore起作用，必须要在这些文件不在暂存区中才可以，.gitignore文件只是忽略没有被staged(cached)文件， 对于已经被staged文件，加入ignore文件时一定要先从staged移除，才可以忽略。





### folers
Once initialized, here’s what your project folder will look like:

```
.
├── _config.yml
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts
└── themes

```

scaffolds

脚手架;建筑架;鹰架
A scaffold is a temporary raised platform on which workers stand to paint, repair, or build high parts of a building.

Scaffold folder. When you create a new post, Hexo bases the new file on the scaffold.

source
Source folder. This is where you put your site’s content. Hexo ignores hidden files and files or folders whose names are prefixed with

_ (underscore)
`- except the _posts folder.`

Renderable files (e.g. Markdown, HTML) will be processed and put into the public folder, while other files will simply be copied.

themes
Theme folder. Hexo generates a static website by combining the site contents with the theme.

## writing

To create a new post or a new page, you can run the following command:

`$ hexo new [layout] <title>`
post is the default layout, but you can supply your own.

### Layout

There are three default layouts in Hexo: post, page and draft. Files created by each of them is saved to a different path. Newly created posts are saved to the source/_posts folder.

### Filename

By default, Hexo uses the post title as its filename. You can edit the new_post_name setting in _config.yml to change the default filename. 

### Drafts

Previously, we mentioned a special layout in Hexo: draft. Posts initialized with this layout are saved to the source/_drafts folder. 
Drafts are not displayed by default. You can add the --draft option when running Hexo or enable the render_drafts setting in _config.yml to render drafts.

You can use the publish command to move drafts to the source/_posts folder. publish works in a similar way to the new command.

`$ hexo publish [layout] <title>`

You can use the publish command to move drafts to the source/_posts folder. publish works in a similar way to the new command.

### Supported Formats

Hexo support posts written in any format, as long as the corresponding renderer plugin is installed.

For example, Hexo has hexo-renderer-marked and hexo-renderer-ejs installed by default, so you can write your posts in markdown or in ejs. 

`$ hexo publish [layout] <title>`

## front matter

Front-matter is a block of YAML or JSON at the beginning of the file that is used to configure settings for your writings. Front-matter is terminated by three dashes when written in YAML or three semicolons when written in JSON.

YAML
```yaml
---
title: Hello World
date: 2013/7/13 20:46:25
---

```
JSON

"title": "Hello World",
"date": "2013/7/13 20:46:25"
;;;

Setting	Description	Default
layout	Layout	config.default_layout
title	Title	Filename (posts only)
date	Published date	File created date
tags	Tags (Not available for pages)	
categories	Categories (Not available for pages)	
permalink	Overrides the default permalink of the post. Permalink should end with / or .html	null

Categories & Tags
Only posts support the use of categories and tags. Categories apply to posts in order, resulting in a hierarchy of classifications and sub-classifications. Tags are all defined on the same hierarchical level so the order in which they appear is not important.

Example

categories:
- Sports
- Baseball
tags:
- Injury
- Fight
- Shocking

If you want to apply multiple category hierarchies, use a list of names instead of a single name. If Hexo sees any categories defined this way on a post, it will treat each category for that post as its own independent hierarchy.

Example

categories:
- [Sports, Baseball]
- [MLB, American League, Boston Red Sox]
- [MLB, American League, New York Yankees]
- Rivalries

## Tag Plugins
Tag plugins are different from post tags. They are ported from Octopress and provide a useful way for you to quickly add specific content to your posts.

Although you can write your posts in any formats, but the tag plugins will always be available and syntax remains the same.






### Link
Inserts a link with target="_blank" attribute.

{% link text url [external] [title] %}

### Include Code
Inserts code snippets in source/downloads/code folder. The folder location can be specified through the code_dir option in the config.

{% raw %}
{% include_code [title] [lang:language] [from:line] [to:line] path/to/file %}
{% endraw %}

### Include Posts
Include links to other posts.

{% raw %}
{% post_path filename %}

{% endraw %}

#### jiesi
You can ignore permalink and folder information, like languages and dates, when using this tag.

For instance: .

This will work as long as the filename of the post is how-to-bake-a-cake.md, even if the post is located at source/posts/2015-02-my-family-holiday and has permalink 2018/en/how-to-bake-a-cake.

You can customize the text to display, instead of displaying the post’s title.

Post’s title and custom text are escaped by default. You can use the escape option to disable escaping.

#### For instance:

Display title of the post.

{% post_link hexo-3-8-released %}

Hexo 3.8.0 Released
Display custom text.

{% post_link hexo-3-8-released 'Link to a post' %}

Link to a post
Escape title.

{% post_link hexo-4-released 'How to use <b> tag in title' %}



### Raw
If certain content is causing processing issues in your posts, wrap it with the raw tag to avoid rendering errors.

{% raw %}
content
{% endraw %}

## Asset Folders

### Image
Inserts an image with specified size.

{% img [class names] /path/to/image [width] [height] '"title text" "alt text"' %}

#### Embedding an image using markdown
hexo-renderer-marked 3.1.0 introduced a new option that allows you to embed an image in markdown without using asset_img tag plugin.

To enable:

_config.yml
post_asset_folder: true
marked:
  prependRoot: true
  postAsset: true

/2020/01/02/foo/image.jpg
/2020/01/02/foo.md
Once enabled, an asset image will be automatically resolved to its corresponding post’s path. For example, “image.jpg” is located at “/2020/01/02/foo/image.jpg”, meaning it is an asset image of “/2020/01/02/foo/“ post, `![](image.jpg)` will be rendered as 

`<img src="/2020/01/02/foo/image.jpg">`.





#### embed image
“foo.jpg” is located at `http://example.com/2020/01/02/hello/foo.jpg`.

Default (no option)

{% asset_img foo.jpg %}

`<img src="/2020/01/02/hello/foo.jpg">`

### Global Asset Folder

Global Asset Folder
Assets are non-post files in the source folder, such as images, CSS or JavaScript files. For instance, If you are only going to have a few images in the Hexo project, then the easiest way is to keep them in a source/images directory. Then, you can access them using something like 

`![](/images/image.jpg)`.

for vscode edit the md file as open the source directory as project file

### dont use Post Asset Folder

For users who expect to regularly serve images and/or other assets, and for those who prefer to separate their assets on a post-per-post basis, Hexo also provides a more organized way to manage assets. This slightly more involved, but very convenient approach to asset management can be turned on by setting the post_asset_folder setting in _config.yml to true.

_config.yml
post_asset_folder: true

With asset folder management enabled, Hexo will create a folder every time you make a new post with the hexo new `[layout] <title>` command. This asset folder will have the same name as the markdown file associated with the post.

Place all assets related to your post into the associated folder, and you will be able to reference them using a relative path, making for an easier and more convenient workflow.

#### dont use this method
Relative Image Path
The build-in way to include images in your posts works fine, but it is a little aside the normal way to declare images in Markdown. The plugin [Hexo Asset Link] corrects that. After installing via npm install hexo-asset-link --save you can write this:

`![Test Image](hello-world/image-1.png)`
The best is, that VS Code’s Markdown can now show the image.

 hexo and vscode img path problem

`$ npm i -s hexo-asset-link`

























