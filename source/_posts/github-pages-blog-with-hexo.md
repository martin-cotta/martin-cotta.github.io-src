title: GitHub Pages blog with Hexo
date: 2015-11-16 16:28:52
categories:
- Tools
- Setup
tags:
- blogging
- hexo
- nodejs
- github
---

[Hexo](https://hexo.io/) is a simple, lightweight blogging framework suitable for developers. It supports [Github flavored markdown](https://help.github.com/articles/github-flavored-markdown/) and it's powered by [Node.js](https://github.com/hexojs/hexo)

Here is a quick setup to get Hexo up and running under OS X and to generate your [Github Pages](https://pages.github.com/) Site `http://username.github.io`

### Prerequisites (Git, Nodejs & Xcode command line tools)
Here we're using [Homebrew](http://brew.sh/) to get the latest release of Git & Nodejs, but we could've used any other package manager or the official installers

```sh
brew update
brew install git
brew install node
xcode-select --install # Xcode Command Line Tools
```

### Install Hexo

```sh
npm install hexo-cli -g # install package globally
npm install hexo-server --save
npm install hexo-deployer-git --save
hexo -v # to verify the installed version
```

To update or uninstall Hexo:

```sh
npm update hexo
npm uninstall hexo
```

### Setup Hexo

Initialize the site directory, install all dependencies and fire up the site

```sh
hexo init username.github.io && cd username.github.io
npm install
hexo server # to see your local site in the browser
```

### Configure
Modify site settings in `_config.yml`

``` yml
# Site
## https://hexo.io/docs/configuration.html
title: My blog title
subtitle: my subtitle
description: some description
author: Your name
language: en
# Writing
filename_case: 1 # lowercase
```

### Add content

You can now create Posts and/or Pages and preview your local changes: `http://0.0.0.0:4000/`

```sh
# to create a post:
hexo new "My New Post"
# to create a page:
hexo new page "Some Page"
```

then just edit the `.md` files created under `username.github.io/source` directory and see your changes in the browser

You need to update the [Front-matter](https://hexo.io/docs/front-matter.html) on every .md file to set categories, tags and other settings   


### Deploy to GitHub

Head over to GitHub and create a new repository named `username.github.io`, where `username` is your username (or organization name) on GitHub.

Update deployment setting in `_config.yml`

```sh
# Deployment
## Docs: http://hexo.io/docs/deployment.html
deploy:
  type: git
  repository: https://github.com/username/username.github.io.git
  branch: master
```

Generate and upload the site to GitHub

```sh
hexo clean
hexo deploy
```

Now the blog is live at `http://username.github.io`  

### Versioning your Hexo site

Create another repository in GitHub, something like `username.github.io-src` (or whatever you want, the name is not important here)

```sh
git init
# add the core files
git add _config.yml package.json .gitignore scaffolds/*.md themes
git commit -m "Adding Hexo Site"
# add any .md you just created
git add source
git commit -m "Add first post"
# push to github
git remote add origin https://github.com/username/username.github.io-src.git
git push -u origin master
```

Add a few themes

You can find more themes at `https://hexo.io/themes/`

```sh
git submodule add https://github.com/ppoffice/hexo-theme-hueman.git themes/hueman
git submodule add https://github.com/pinggod/hexo-theme-jekyll themes/jekyll
git submodule add https://github.com/tommy351/hexo-theme-light.git themes/light
# more themes at `https://hexo.io/themes/`
```

check out the official documentation: https://hexo.io/docs/
