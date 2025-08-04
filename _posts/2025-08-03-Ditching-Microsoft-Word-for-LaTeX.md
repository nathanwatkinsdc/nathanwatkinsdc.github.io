---
layout: default
title: Ditching Microsoft Word for LaTeX
date: 2025-08-03
thumbnail: /assets/images/resume_latex.png
description: Why I decided to take the leap and build a resume template that actually works
---

# Why I‘m ditching Microsoft Word for LaTeX and built a resume template that actually works

*Or: how a data scientist’s formatting obsession and slightly unhealthy relationship with mathematical markup languages solved his job application woes*

It’s a familiar scene. It’s 2am, and you’re tailoring your resume for the fifteenth job application this week, and Microsoft Word decides that adding one more bullet point means your entire formatting scheme should spontaneously combust. The margins shift, and the spacing goes haywire. Your carefully crafted two-page masterpiece becomes a three-page disaster with a single orphaned line mocking you from page three in the print preview window.

Sound familiar?

As someone who’s spent years wrangling data into submission, I figured there had to be a better way. Turns out, the answer was hiding all along in my college math homework. 

## ♾️ The origin story
Back in college, when professors demanded typed solutions for complex mathematical proofs, I discovered [LaTeX](https://www.latex-project.org/)—a markup language that makes beautiful equations and doesn’t throw tantrums when you ask it to format things consistently. While my classmates were fighting with Word’s equation editor (🪦), I was cranking out elegant problem sets that looked like they belonged in actual textbooks.

Fast forward to 2025: I’m knee-deep in job applications, customizing resumes, and Word is testing my nerves. That’s when it hit me—why am I using a tool designed for casual document writing when I need something that treats formatting seriously and systematically?

## 🚚 The Great Resume Migration
So I did what any reasonable data scientist would do: I over-engineered a solution. But here’s the thing—it actually worked. Really well!

I built a modular LaTeX resume template that treats each section like a separate data file. Want to update your experience? *Update one file.* Want to update your experience? *Edit one file.* Need to tweak your summary for a specific role? *Another file.* Want to track changes with git because you’re paranoid about losing your work? *You get the idea.*

## 🤔 Why this matters
If you work with data, you already understand the value of:

- **Reproducible workflows** (compile once, looks perfect every time)
- **Version control** (git plays nicely with plain text files)
- **Modular architecture** (each section is independent and reusable)
- **Programmatic customization** (change colors/spacing with a few variables)

My resume template brings these same principles to job applications by applying software engineering best practices to career documents—which, let’s be honest, is exactly the kind of thing that makes hiring managers in tech think “this person gets it” 😉

## 🖥️ The technical bits (for the curious)
The template breaks everything into logical components: 

```
main.tex                 # The orchestrator
resume_class.tex         # All the styling magic
sections/
  ├── summary.tex        # Your elevator pitch
  ├── experience.tex     # Where you brag professionally  
  └── education.tex      # Academic credentials
```

And there are custom commands for consistent formatting:

- `\experienceentry{title}{company}{location}{dates}`
- `\educationentry{degree}{school}{year}`

No more fighting with indentation or bullet point spacing. Just clean, semantic markup that does what you tell it to do.

## 😻 The Unexpected Benefits
I expected the delight of formatting consistency, but there were more things that surprised me and gave me that umami taste:

**1. Speed:** Once set up, updating takes seconds. Adding a new job? Drop it into the experience file, recompile, done.

**2. Professional credibility:** applying for analytical roles? Show up with a perfectly formatted, clearly structured resume, signaling that you care about details and understand good system design. 

**3. Focus on content:** instead of wrestling with margins, spend more time crafting compelling bullet points because the formatting is handled programmatically.

**4. Customization without chaos:** want different colors for different industries? Change two hex values. Need to adjust spacing? One variable. 

## ✅ The Reality Check
Look, I’m not canceling my OneDrive subscription anytime soon and am not telling you to do that either. LaTeX has a learning curve, and if you’re applying to roles where technical prowess isn’t valued, the effort might not be worth it.

But if you’re in data science, engineering, finance, or any field where attention to detail and systematic thinking matter, this approach sends a signal about how you work. It says you care enough about quality to invest in proper tooling.

Plus, there’s something deeply satisfying about having a resume that compiles cleanly every single time. I’ve debugged enough Python scripts and SQL queries in my day to know that reproducibility is everything, and so applying that same mindset to career documents just makes sense.

As someone who’s debugged enough Python scripts and SQL queries to know that reproducibility is everything, applying that same mindset to career documents just makes sense.

## 🎯 The Bottom Line
LaTeX offers the mental clarity that comes from having one less frustrating tool in my workflow. If sounds good to you, I’ve [open-sourced the whole thing](https://github.com/nathanwatkinsdc/resume-latex). MIT license—use it however you want. If it helps you land a job, great. If it just saves you from one more Word-induced meltdown, that’s a win too. 

And if you’re the kind of person who reads a blog post about LaTeX resume templates and thinks “this sounds useful,” you’re probably exactly the kind of professional I’d want to work with, so please via [LinkedIn](https://www.linkedin.com/in/nathanlwatkins) or the contact info on my [Resume](https://nathanwatkinsdc.github.io/resume/).