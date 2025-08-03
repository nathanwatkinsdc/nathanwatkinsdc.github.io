---
layout: default
title: "GHOST SCRAMBLE: Building My First React App"
date: 2025-08-01
thumbnail: /assets/images/ghostscramble_thumbnail.png
description: A brief summary of how I built my first React app using my GHOST SCRAMBLE creative device
---

## 👷 Building my first React app

I've been wanting to build a React web app for a while, and it struck me the other day that my [GHOST SCRAMBLE](https://nathanwatkinsdc.github.io/2025/07/28/GHOST-SCRAMBLE-Creative-Device.html) creative device was a perfect place to start. 

If you didn't have a chance to read the post linked above, GHOST SCRAMBLE is an acronym that I use to get my brain juices flowing when doing some creative writing. Basically, I go through the phrase letter by letter and think of an idea for the concept represented by each. Once I'm done, I'm always ready to write, but I never know where my brain will take me - that's the fun part. 

**So where does an app come into play?** What I had in mind was a simple journaling app where the user clicks through 13 (one per letter in GHOST SCRAMBLE) text fields to fill out before reaching a final field for the journal entry. When the user is done, they can save and export their work. 

### 💻 What I built
Here are the features of my interactive journaling app:

- All 12 GHOST SCRAMBLE prompts show up with tooltips (in German and English) (*I was an exchange student in Germany once upon a time, hence the German words*)
- Users write freely for each prompt, then synthesize their thoughts in a Reflection field
- Session management is supported, whereby users can create, save, reload, and delete entries
- Users can export entries as text files for later use
- Sessions are stored in localStorage for persistence between visits

And here's a super satisfying screenshot of my work:

<img src="/assets/images/ghostscramble_screenshot.png" alt="My photo description" style="width:50%; max-width:400px;">

### 🛠️ Tools and skills used
I worked through a few versions of the app, trying to stretch my tech and design skills. Eventually I landed at a version exhibiting:

- **React** for building a dynamic, component-based front-end
- **Lucide-react icons** for a clean, professional look
- **Custom CSS** for responsive, modern styling (no pre-made templates!)
- **LocalStorage API** for lightweight data persistence
- **File handling** to generate downloadable `.txt` exports
- GitHub for **version control and public sharing**

For anyone like me who's interested in this type of thing, here's my folder structure:

```
ghost-scramble-journal/
├── public/
├── src/
│   ├── App.js
│   ├── index.css
│   ├── GhostScramble.css
│   └── index.js
├── package.json
└── README.md
```

You can also check out my folder structure by going to the [GitHub repo](https://nathanwatkinsdc.github.io) where I saved this project, which you can also take for a spin and tweak to your own liking 😁

### 🌟 Personal takeaways/reflections
I'm really pleased with the fruits of my labor on this project, which I feel showcases my ability to (1) **learn new frameworks quickly** (this was my first React project), (2) build a **usable, visually appealing web tool** from scratch, and (3) combine **creativity and technical skill** in a way that's unique to me. It's also gratifying to continue iterating on a project that's been with me for so many years, as I've been using the device in my journaling practice in some form since undergrad.

