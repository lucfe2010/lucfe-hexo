---
layout: post
title:  "Jekyll wiki"
categories: jekyll update
author: lucfe
---

## Creating a GitHub Pages site with Jekyll

0. Creating a repository for your site

![Alt text](/assets/images/2023-09-05-jekyll-wiki/image-1.png)

每个用户唯一的一个PAGE REPOSITORY
USERNAME.github.io
网站地址默认为<https://USERNAME.github.io>

![Alt text](/assets/images/2023-09-05-jekyll-wiki/image-2.png)

1. Open Git Bash.

navigate to the location where you want to store your site's source files, replacing PARENT-FOLDER with the folder you want to contain the folder for your repository.

2. cd PARENT-FOLDER
![Alt text](/assets/images/2023-09-05-jekyll-wiki/image-3.png)

1. initialize a local Git repository, replacing REPOSITORY-NAME with the name of your repository.

$ git init REPOSITORY-NAME

4. Change directories to the repository.

```bash
$ cd REPOSITORY-NAME
# Changes the working directory
```

5.

- 5.1. chose to publish your site from the docs folder on the default branch, create and change directories to the docs folder.

```bash
$ mkdir docs
# Creates a new folder called docs
$ cd docs
```

- 5.2. chose to publish your site from the gh-pages branch, create and checkout the gh-pages branch.

```bash
$ git checkout --orphan gh-pages
# Creates a new branch, with no history or contents, called gh-pages, and switches to the gh-pages branch
$ git rm -rf .
# Removes the contents from your default branch from the working directory
```

6. To create a new Jekyll site, use the jekyll new command:

$ jekyll new --skip-bundle .

Creates a Jekyll site in the current directory

7. Open the Gemfile that Jekyll created.

Add "#" to the beginning of the line that starts with gem "jekyll" to comment out this line.

Add the github-pages gem by editing the line starting with # gem "github-pages". Change this line to:

gem "github-pages", "~> GITHUB-PAGES-VERSION", group: :jekyll_plugins
Replace GITHUB-PAGES-VERSION with the latest supported version of the github-pages gem. You can find this version here: "Dependency versions."

The correct version Jekyll will be installed as a dependency of the github-pages gem.

gem "github-pages", "~> 228", group: :jekyll_plugins

Save and close the Gemfile.

8. intall some dependecies

Bundler
Conveniently, bundler has a feature to alias a Gem-server to another one. This way, you can leave your Gemfile source '<https://rubygems.org>' at the top of each Gemfile.
Run this command:
bundle config mirror.<https://rubygems.org> <https://gems.ruby-china.com>
To remove the aliasing, just delete the appropriate line in ~/.bundle/config.

bundle config mirror.<https://rubygems.org> <https://gems.ruby-china.com>

bundle config mirror.<https://rubygems.org> <https://rubygems.org>

From the command line, run `bundle install`.

9. make any necessary edits to the _config.yml file. This is required for relative paths when the repository is hosted in a subdirectory.

```yaml
baseurl: "/lucfe/" # the subpath of your site, e.g. /blog
url: "https://lucfe2010.github.io" # the base hostname & protocol for your site, e.g. http://example.com
```

10.Run your Jekyll site locally.
$ bundle add webrick
$ bundle exec jekyll serve

10. Add and commit your work.

git add .
git commit -m 'Initial GitHub pages site with Jekyll'

11.Add your repository on GitHub.com as a remote, replacing USER with the account that owns the repository and REPOSITORY with the name of the repository.

$ git remote add origin <https://github.com/USER/REPOSITORY.git>

---

如果你clone下来一个别人的仓库，在此基础上完成你的代码，推送到自己的仓库可能遇到如下问题： error: remote origin already exists.表示远程仓库已存在。 因此你要进行以下操作： 1、先输入git remote rm origin 删除关联的origin的远程库

---

12.Push the repository to GitHub, replacing BRANCH with the name of the branch you're working on.

git branch -M main
git push -u origin main

git push -u origin BRANCH

13. Configure your publishing source

![Alt text](/assets/images/2023-09-05-jekyll-wiki/image-4.png)

main branch,doc/ folder
![Alt text](/assets/images/2023-09-05-jekyll-wiki/image-5.png)

gh-pages, / folder
![Alt text](/assets/images/2023-09-05-jekyll-wiki/image-6.png)

1.  optinal

permalink

_config.yml

`# Outputting`
permalink: none

PERMALINK STYLE   URL TEMPLATE
date  /:categories/:year/:month/:day/:title:output_ext
none  /:categories/:title:output_ext

Markdown › Copy Files: Destination
Defines where files copied created by drop or paste should be created. This is a map from globs that match on the Markdown document to destinations.
item value
{% raw %}`"*"  /assets/images/${documentBaseName}/`{% endraw %}

when copy image to vs code the `![]()`,is relative path like
../../../assets/images/2023-09-05-jekyll-wiki/image-6.png


## Directory Structure

_includes


These are the partials that can be mixed and matched by your layouts and posts to facilitate reuse. The liquid tag 



 can be used to include the partial in _includes/file.ext.


_layouts

These are the templates that wrap posts. Layouts are chosen on a post-by-post basis in the front matter, which is described in the next section. The liquid tag {% raw %} {{ content }} {% endraw %} is used to inject content into the web page.

_posts

Your dynamic content, so to speak. The naming convention of these files is important, and must follow the format: YEAR-MONTH-DAY-title.MARKUP. The permalinks can be customized for each post, but the date and markup language are determined solely by the file name.

_site

This is where the generated site will be placed (by default) once Jekyll is done transforming it. It’s probably a good idea to add this to your .gitignore file.

index.html or index.md and other HTML, Markdown files

Provided that the file has a front matter section, it will be transformed by Jekyll. The same will happen for any .html, .markdown, .md, or .textile file in your site’s root directory or directories not listed above.

The Gemfile and Gemfile.lock files are used by Bundler to keep track of the required gems and gem versions you need to build your Jekyll site.

Assets
Any file in /assets will be copied over to the user’s site upon build unless they have a file with the same relative path. You can ship any kind of asset here: SCSS, an image, a webfont, etc.

All files in /assets will be output into the compiled site in the /assets folder just as you’d expect from using Jekyll on your sites.

## theme

To locate a theme’s files on your computer:

Run bundle info --path followed by the name of the theme’s gem, e.g., bundle info --path minima for Jekyll’s default theme.

This returns the location of the gem-based theme files.

### Customization

To override the default structure and style of minima, simply create the concerned directory at the root of your site, copy the file you wish to customize to that directory, and then edit the file.
e.g., to override the [`_includes/head.html `](<../../category level1/category level2/_includes/head.html>) file to specify a custom style path, create an `_includes` directory, copy `_includes/head.html` from minima gem folder to `<yoursite>/_includes` and start editing that file.

To modify any stylesheet you must take the extra step of also copying the main sass file (_sass/minima.scss in the Minima theme) into the _sass directory in your site’s source.

An alternative, to continue getting theme updates on all stylesheets, is to use higher specificity CSS selectors in your own additional, originally named CSS files.

### Converting gem-based themes to regular themesPermalink
Suppose you want to get rid of the gem-based theme and convert it to a regular theme, where all files are present in your Jekyll site directory, with nothing stored in the theme gem.

To do this, copy the files from the theme gem’s directory into your Jekyll site directory. (For example, copy them to /myblog if you created your Jekyll site at /myblog. See the previous section for details.)

Then you must tell Jekyll about the plugins that were referenced by the theme. You can find these plugins in the theme’s gemspec file as runtime dependencies. If you were converting the Minima theme, for example, you might see:

spec.add_runtime_dependency "jekyll-feed", "~> 0.12"
spec.add_runtime_dependency "jekyll-seo-tag", "~> 2.6"

You should include these references in the Gemfile.

You could list them individually in both Gemfile and _config.yml.

```gemspec
# ./Gemfile

gem "jekyll-feed", "~> 0.12"
gem "jekyll-seo-tag", "~> 2.6"
```

```yaml
# ./_config.yml


plugins:
  - jekyll-feed
  - jekyll-seo-tag
```

If you’re publishing on GitHub Pages you should update only your _config.yml as GitHub Pages doesn’t load plugins via Bundler.

Either way, don’t forget to bundle update.

Finally, remove references to the theme gem in Gemfile and configuration. For example, to remove minima:

Open Gemfile and remove gem "minima", "~> 2.5".
Open _config.yml and remove theme: minima.
Now bundle update will no longer get updates for the theme gem.
