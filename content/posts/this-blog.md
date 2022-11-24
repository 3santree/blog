---
title: "This blog"
date: 2022-11-23T17:56:07-05:00
draft: false
tags: ["blog"]
description: "how to create a blog like this"
---
# Welcome
> I will show you how I started this blog

## Install Hugo (on Mac)
```bash
brew install hugo
```
## Create empty hugo site
```bash
# This will create a basic hugo project called my-hugo-site
hugo new site my-hugo-site
# It creates the file structure for you.
tree my-hugo-site
.
├── archetypes
│   └── default.md
├── config.toml         // empty config file
├── content             // your blog content
├── data
├── layouts             
├── public
├── resources
│   └── _gen
│       ├── assets
│       └── images
├── static
└── themes              // put theme inside here
```

## Install [zozo theme](https://github.com/varkai/hugo-theme-zozo)
> Shortout to the author of this theme, thanks for creating such a nice theme. 
My requirement for building a blog is simple: Simple to look, Simple to use, Simple to change. Let me show you
```
# Download the theme from github and put it into themes folder
git clone https://github.com/varkai/hugo-theme-zozo themes/zozo
# Replace our empty config file
cp themes/zozo/exampleSite/content/config.toml .
# Create a post, this will create a folder posts in the content folder
# which will be the location for putting your later blog post
hugo new posts/hello-world.md
# Edit "hello-world" post file we just created

--- // This is the header of this post
title: "Hello World"    // Anything you like
date: [Automatic created for you]
draft: false            // Change it to false
---
# Hello World

# Start the server at localhost:3000
hugo server --port=3000 -D
```
Now you're able to see your blog at `localhost:3000` in your browser. However, the default page you get may be different from me because I changed a few things, but don't worry, remember it's simple to use?
## config.toml
Open config.toml, you will see well-commented settings which don't need much of explanation.
### Changing the default title and subtitle:
```
# By saving the config file, hugo will refresh the page for you automatically.
title = "3Santree"                        # site title                   
subTitle = "a security researcher"        # site's subTitle           
```
### Delete about page

Delete the section of about

### Delete the social icons under your subtitle
Delete the social media icon you want by deleting the respondding line. If you want to link your social media, simply copy the link here.
```
[social]
  github = "https://github.com/3santree"
```

### Delete rss icon
```
# Delete line 18 of themes/zozo/layouts/partials/header.html
<a href="{{ .Site.RSSLink }}" type="application/rss+xml" title="rss" target="_blank"><i
                        class="ri-rss-fill"></i></a>
# Delete line 32-34 of themes/zozo/layouts/partials/head.html
{{ with .OutputFormats.Get "rss" }}
{{ printf `<link rel="%s" type="%s" href="%s" title="%s" />` .Rel .MediaType.Type .Permalink $.Site.Title | safeHTML }}
{{ end }}
```
## You want to explore it further?
- Comparing the [live demo](https://zozo.varkai.com/) with the source code (themes/zozo/exampleSite)
- Check out hugo offical documentation

# Enjoy

