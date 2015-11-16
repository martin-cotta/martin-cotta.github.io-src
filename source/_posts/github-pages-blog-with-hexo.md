title: Github Pages blog with Hexo
date: 2015-11-13 17:30:00
categories:
- Setup
tags:
- Blogging
- Hexo
- Nodejs
---

[Hexo](https://hexo.io/) is a simple, lightweight blogging framework suitable for developers. It supports [Github flavored markdown](https://help.github.com/articles/github-flavored-markdown/) and it's powered by [Node.js](https://github.com/hexojs/hexo).

The following are the steps to setup Hexo under OSX and generate your [Github Pages](https://pages.github.com/) Site `http://username.github.io`

### Prerequisites (Git, Nodejs & Xcode command line tools)
We're using [Homebrew](http://brew.sh/) to get latest release of Git & Nodejs

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

```yaml
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

You can now create Posts/Pages and see your local site at: `http://0.0.0.0:4000/`

```sh
# to create a post:
hexo new "My New Post"
# to create a page:
hexo new page "Some Page"
```

then just edit the `.md` files created under `username.github.io/source` directory and see your changes in the browser

> You need to update the [Front-matter](https://hexo.io/docs/front-matter.html) on every .md file to set categories, tags and other settings   


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

Create another repository in GitHub, something like `username.github.io-src` (or whatever you want, the name is not important)

```sh
git init
# add the core fies
git add _config.yml package.json .gitignore scaffolds/*.md themes
git commit -m "Adding Hexo Site"
# add any .md you just created 
git add source
git commit -m "Add first post"
# push to github
git remote add origin https://github.com/username/username.github.io-src.git
git push -u origin master
```