---
author: "Saad Aouad"
date: 2017-10-02
linktitle: Go HUGO - Fast and flexible static site generator build with GoLang
menu:
  main:
    parent: tutorials
next: /tutorials/github-pages-blog
prev: /tutorials/automated-deployments
title: Go HUGO - Fast and flexible static site generator build with GoLang
description: The world’s fastest framework for building websites
weight: 10
---


> Hugo is one of the most popular open-source static site generators. With its amazing speed and flexibility, Hugo makes building websites fun again.

### **Quick Start**

#### **Step 1: Install Hugo**
> Homebrew, a package manager for macOS, can be installed from brew.sh. See [install](http://gohugo.io/getting-started/installing) if you are running Windows etc.

```
brew install hugo
```
Verify installation:
```
hugo version
```

#### **Step 2: Create a New Site**

Create a new Hugo site in a folder named GoHugo
```
hugo new site go-hugo
```

#### **Step 3: Add a Theme**

Check [themes.gohugo.io](https://themes.gohugo.io/) this is a list of themes to consider.
This quickstart uses the beautiful [Tranquilpeak theme](https://themes.gohugo.io/hugo-tranquilpeak-theme/).

```
cd go-hugo;\
git init;\
git submodule add https://github.com/kakawait/hugo-tranquilpeak-theme.git themes/hugo-tranquilpeak-theme;\

# Edit your config.toml configuration file
# and add the Tranquilpeak theme.
echo 'theme = "hugo-tranquilpeak-theme"' >> config.toml
```

#### **Step 4: Add Content**
```
hugo new posts/my-first-post.md
```

#### **Step 5: Run Hugo server**
```
hugo server -D
# Or 
hugo server

## Example
➜  go-hugo git:(master) hugo server        
Started building sites ...
Built site for language en:
0 draft content
0 future content
0 expired content
1 regular pages created
10 other pages created
0 non-page files copied
1 paginator pages created
0 tags created
0 categories created
total in 8 ms
Watching for changes in /Users/saadaouad/go-hugo/{data,content,layouts,static,themes}
Serving pages from memory
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

#### **Step 6: Customize your site**
Open up `config.toml` in any any text editor, and try to customize your web site like this:
```
baseURL = "https://saadaouad.io/"
languageCode = "en-us"
title = "My New Web Site Build With Hugo"
theme = "hugo-tranquilpeak-theme"
```
If you already have a domain ready, please set it to the `baseURL`, add your personal `title`, and you can also set the name of the `theme`.


##### **Happy hacking!**
