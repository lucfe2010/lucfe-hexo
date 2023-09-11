1. 查看当前地址
npm config get registry
复制

2. 设置当前地址（设置为淘宝镜像）
不要用这个npm config set registry http://registry.npm.taobao.org/
npm config set registry https://registry.npmmirror.com
复制
3. 设置当前地址（设置为默认地址）
npm config set registry https://registry.npmjs.org/


MAKE A PROJECT DIRECTORY 
Create a directory for your project using the mkdir command (short for make directory):

mkdir eleventy-sample
Now move into that directory with the cd command (short for change directory):

cd eleventy-sample


## INSTALL ELEVENTY 
### CREATE A package.json 
Installing Eleventy into a project requires a package.json file. The npm command (provided by Node.js) will create one for you with npm init -y. -y tells npm to use default values and skips the command line questionnaire.

npm init -y


### INSTALL ELEVENTY 
@11ty/eleventy is published on npm and we can install and save it into our project’s package.json by running:

npm install @11ty/eleventy --save-dev
You may also install Eleventy globally but the package.json installation method above is recommended.

## RUN ELEVENTY 
We can use the npx command (also provided by Node.js) to run our local project's version of Eleventy. Let’s make sure our installation went okay and try to run Eleventy:

npx @11ty/eleventy

## CREATE SOME TEMPLATES 
A template is a content file written in a format such as Markdown, HTML, Liquid, Nunjucks, and more, which Eleventy transforms into a page (or pages) when building our site.

Let’s run two commands to create two new template files.

echo '<!doctype html><title>Page title</title><p>Hi</p>' > index.html
echo '# Page header' > README.md
Alternatively, you can create these using any text editor—just make sure you save them into your project folder and they have the correct file extensions.

### After you’ve created an HTML template and a Markdown template, let’s run Eleventy again with the following command:

npx @11ty/eleventy
The output might look like this:

npx @11ty/eleventy
[11ty] Writing _site/README/index.html from ./README.md (liquid)
[11ty] Writing _site/index.html from ./index.html (liquid)
[11ty] Wrote 2 files in 0.04 seconds (v2.0.1)
We’ve compiled our two content templates in the current directory into the output folder (_site is the default).

## GAZE UPON YOUR TEMPLATES 
Use --serve to start up a hot-reloading local web server.

npx @11ty/eleventy --serve
Your command line might look something like:

npx @11ty/eleventy --serve
[11ty] Writing _site/index.html from ./index.html (liquid)
[11ty] Writing _site/README/index.html from ./README.md (liquid)
[11ty] Wrote 2 files in 0.04 seconds (v2.0.0)
[11ty] Watching…
[11ty] Server at http://localhost:8080/
Open http://localhost:8080/ or http://localhost:8080/README/ in your favorite web browser to see your Eleventy site live! When you save your template files—Eleventy will refresh the browser with your new changes automatically!


## USE A BUILD SCRIPT 
When deploying your Eleventy site, the goal is to provide your chosen host with your project’s build output (the _site folder by default). The command you run is usually configured via a build script in your package.json file. It might look like this:
## DEPOLY ON GITHUB PAGES.0B

FILENAME package.json
{
  "scripts": {
    "build": "npx @11ty/eleventy"
  }
}

### New files in your GitHub repo
.nojekyll file: Open a plain-text editor and save an empty file in the root of your repo (where you have the .eleventy.js) with the filename .nojekyll. This will stop GitHub from trying to build your site as a Jekyll site.

.github directory: Create a new directory in the root of your repo and name it .github (yes, starting with a period). Inside that directory, make a directory named workflows. Open a plain-text editor and save a file inside the workflows directory called build.yml. Copy the contents from my build.yml file here.
Note: my build.yml file was updated 6/14/23 with Node version improvements thanks to Simon Wiles


```YML
name: Build Eleventy
on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3

      - name: Use Node.js current
        uses: actions/setup-node@v3
        with:
          node-version: current

      - name: Install dependencies & build
        run: |
          npm ci
          npm run build

          
      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3.8.0
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          #publish_dir is the folder on the docker instance which eleventy builds the pages to.
          #it is not the docs folder in the repository
          publish_dir: _site
          #publish_branch is the branch in the repository.
          #this is where you need to point GitHub pages
          publish_branch: gh-pages
```

Depending on your Eleventy setup, you may need to change publish_dir in your build.yml file. My Eleventy site builds to a folder called dist. If yours builds to a folder with a different name, change it in this file.

### GitHub configuration
#### Creating a gh-pages branch
Using the GitHub interface, you'll need to create a new branch of your repo called gh-pages where the built version of your site will be hosted from. If you're looking at your repo on GitHub, you should see a little button that says main towards the upper left, under the <> Code tab. Click that button, then type gh-pages into the field that says Find or create a branch. This will create a new branch called gh-pages

***important!!!!
the gh-pages branch will be update by the github page action definded up right in the workflow. so dont use the gh-pages branch for editing content***

#### Actions configuration
Go into the settings for your repo, click on Actions in the set of tabs on the left, then General.
 Make sure that "Allow all actions and reusable workflows" is selected, 
 and at the bottom of that page, under Workflow permissions make sure that you have "Read and write permissions" selected.



#### GitHub Pages configuration
Go into the settings for your repo, and click on "Pages" in the set of tabs on the left. Use the dropdown under Source to choose the gh-pages branch.

### Building the sitePermalink
In theory, if you've set up all these things, anytime you push changes to GitHub, it will trigger an action that will build the site and move those files to the GitHub Pages hosting environment.

If everything isn't set up just right, you'll get an email that an action failed. Click the "View workflow run" link in the email, which will take you to a page with information on the failed workflow. Click on the text in the middle panel where you see a red circle with an x -- what the text says depends on where exactly it failed. Eventually you'll see text reflecting where exactly the process failed, and you can search parts of that error message to figure out what's going wrong.


## layout

Eleventy Layouts are special templates that can be used to wrap other content.

### first
To denote that a piece of content should be wrapped in a template, use the layout key in your front matter, like so:

content-using-layout.md

```markdown
---
layout: "layouts/mylayout.njk"
title: My Rad Markdown Blog Post
---
# {{ title }}
```

This will look for a mylayout.njk Nunjucks file in your includes folder at _includes/layouts/mylayout.njk.

### Next, we need to create a mylayout.njk file. It can contain any type of text, but here we’re using HTML:

FILENAME _includes/mylayout.njk

```

---
title: My Rad Blog
---

<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ title }}</title>
  </head>
  <body>{% raw %}
    {{ content | safe }}{% endraw %}
  </body>
</html>


```

If you are using a language that contains curly braces, you will likely need to place {% raw %} and {% endraw %} tags around your code. Since Jekyll 4.0 , you can add render_with_liquid: false in your front matter to disable Liquid entirely for a particular document.

Note that the layout template will populate the content data with the child template’s content.

 Also note that we don’t want to double-escape the output, so we’re using the provided Nunjucks safe filter here (see more language double-escaping syntax below).
### FRONT MATTER DATA IN LAYOUTS
Layouts can contain their own front matter data! It’ll be merged with the content’s data on render. Content data takes precedence(优先), if conflicting keys arise.

Front matter data set in a content template takes priority over layout front matter! Chained layouts have similar merge behavior. The closer to the content, the higher priority the data.

SOURCES OF DATA 
When the data is merged in the Eleventy Data Cascade, the order of priority for sources of data is (from highest priority to lowest):

1. Computed Data
1. Front Matter Data in a Template
1. Template Data Files
1. Directory Data Files (and ascending Parent Directories)
1. Front Matter Data in Layouts (this moved in 1.0) ⬅
1. Configuration API Global Data
1. Global Data Files