---
layout: default
title: "How I Built This Site with GitHub Pages"
date: 2025-07-23
thumbnail: /assets/images/githubpages.png
description: A quick breakdown of how I built and deployed my personal website using Jekyll and GitHub Pages
tags: [web-development, github, jekyll, tutorial, coding]
---

# 🛠️ How I built this site with GitHub Pages
In this post, I walk you through how I made this site using GitHub Pages. But first, a little context.

# 🧑‍💻 Context: I like making websites
I made my first website when I ran for student government in seventh grade. Then I did the same thing during every campaign through high school and college. I’ve made plenty of pretty sites over the years at work, but for this page I wanted to do something really simple. So I did a little research and landed on GitHub Pages. 

## 🔧 Step 1: create a GitHub repository
The first step is to create a repo named: 

>> username.github.io

Then GitHub will serve files in this repo as a website at:

>> https://username.github.io

## 💎 Step 2: set up Jekyll
Jekyll is one of the few things you’ll need to install to get your page up and running. It’s a static site generator that works seamlessly with GitHub Pages. I used it to manage blog posts in markdown, create reusable layouts and styles, and preview everything locally (i.e., on a local server in my browser) with the terminal command `jekyll serve`. =
## 🎨 Step 3: customize layouts & styles
The next thing I did was add a few **Pages** in.md format: Home, Blog, Resume, Links. Then I added some custom **Layouts** like a custom navigation bar and responsive blog cards. Finally I added a **CSS** style sheet that styled everything in `assets/style.css`. 

## 🚀 Step 4: deploy with a push
Once I was happy with the changes made to my page on my local server, I ran it by pushing it to GitHub using my terminal:

```bash
git add .
git commit -m "Update blog"
git push origin main
```

Then GitHub Pages took care of the rest. That means absolutely no servers ❌ no FTP ❌ and no headache ❌. If you want to build your own site just like mine, check out [GitHub Pages](https://pages.github.com).
