---
layout: default
title: Enhancing My GitHub Pages Blog
date: 2025-08-18
thumbnail: /assets/images/blog_enhancing.png
description: Creating under constraints to enhance my blog with pagination, tag-based filtering, and real-time search
tags: [GitHub, coding, web-development, JavaScript, creativity, CSS]
---

# 🚀 From basic blog to smart content hub

My GitHub Pages blog [started simple](https://nathanwatkinsdc.github.io/2025/07/23/How-I-Built-This-Site-with-GitHub-Pages.html) with a clean layout, four pages, and a growing collection of posts, but as I added content, the blog page began to become unwieldy. Posts piled up in a long list with no way to filter or navigate efficiently.

I would have benefited from a [content management system](https://en.wikipedia.org/wiki/Content_management_system#:~:text=A%20content%20management%20system%20(CMS,typically%20includes%20a%20WCM%20function.) like WordPress, but I wanted to stick to GitHub Pages despite its constraints like no databases or server-side processing. These constraints didn't get me down, though, as I tend to believe that the best creative outcomes come from experimentation under constraints (so long as the cost of experimenting isn't too high, which it wasn't in this case).

# 📝 The problem: when success creates problems

Here are the problems I began to see or foresee on my blog page:
- **Long scroll of doom**: All posts displayed at once
- **No organization**: No way to filter by programming vs. data science vs. creative writing
- **Poor discoverability**: Readers couldn't easily find posts on specific topics
- **Mobile unfriendly**: Too much scrolling on smaller screens

Still committed to GitHub Pages because of its simplicity and free hosting, the challenge became building advanced features within [Jekyll](https://en.wikipedia.org/wiki/Jekyll_(software))'s constraints.
# 🎯 The vision: smart filtering without complexity

I decided I wanted three key enhancements:
1. **Pagination**: show 5 posts at a time with "Load More" functionality
2. **Tag-based filtering**: click hashtags to filter posts by topic
3. **Real-time search**: find posts by title, description, or tags

The catch was, everything had to work with GitHub Pages' limited plugin support and static generation. 

# 🔧 The Solution: JavaScript to the rescue

## The pagination challenge

I built JavaScript-based pagination after my first attempt with Jekyll's pagination plugin succumbed to GitHub Pages' plugin pickiness:

```javascript
// Show only the first 5 posts, hide the rest
function updateDisplay() {
    blogCards.forEach(card => card.style.display = 'none');
    filteredCards.slice(0, currentlyVisible).forEach(card => {
        card.style.display = 'flex';
    });
}
```

With this approach, I can control which posts display and when.
## The hashtag system

For hashtags, I implemented a two-part system whereby (1) Jekyll process frontmatter tags and generates the data and (2) JavaScript creates the interactive filters dynamically. Now, each post includes tags in its frontmatter:

```yaml
tags: [web-development, jekyll, github-pages, javascript]
```

JavaScript scans all posts, counts tag occurrences, and builds a filterable grid:

```javascript
// Count tag occurrences across all posts
const tagCounts = {};
blogCards.forEach(card => {
    const tags = card.dataset.tags.trim();
    if (tags) {
        tags.split(' ').forEach(tag => {
            tagCounts[tag] = (tagCounts[tag] || 0) + 1;
        });
    }
});
```

## The search implementation

Under GitHub Pages' constraints, the search feature needed to be fast and work without a backend, so I implemented a client-side filtering that searches across titles, descriptions, and tags:

```javascript
filteredCards = baseCards.filter(card => {
    const title = card.dataset.title || '';
    const description = card.dataset.description || '';
    const tags = card.dataset.tags || '';
    
    return title.includes(searchTerm) || 
           description.includes(searchTerm) || 
           tags.includes(searchTerm);
});
```

# 🎨 The design evolution: from sidebar to grid

I tried to put the tag filter menu in a sidebar on the left, but it consumed too much horizontal space. After some user feedback (I was the user), I redesigned it as a compact grid. It transformed from a vertical sidebar taking 25% of screen width to a collapsible (space-saving) horizontal grid in 4 columns.

The CSS Grid implementation creates responsive columns that degrade to fewer columns on mobile:

```css
.tag-filter-container {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 8px;
}
```

# 🎭 The polish: square thumbnails and smooth interactions

With the key enhancements in place, I turned to the details like changing the blog post cards' thumbnail images from rectangles to squares using CSS:

```css
.blog-thumbnail-container {
    flex: 0 0 200px;
    width: 200px;
    height: 200px;
    overflow: hidden;
}

.blog-thumbnail {
    width: 100%;
    height: 100%;
    object-fit: cover;
}
```

I also added a collapse/expand button for the tag filters, giving users control over their screen real estate.

# 🧠 Technical Lessons Learned

Honestly, I thought this exercise of adding 3 enhancements would be easier than it was, but I'm grateful for the obstacles I encountered along the way because I learned a few lessons:
## Lesson 1: working with Jekyll's limitations
Jekyll's limitations weren't severe enough for me to jump ship. They just made me get creative. I used client-side JavaScript instead of server-side pagination, and I embedded data in HTML attributes for JavaScript to process instead of relying on complex Jekyll queries.
## Lesson 2: performance considerations
I noted some performance considerations for future reference. With all posts loaded in the [DOM](https://en.wikipedia.org/wiki/Document_Object_Model), performance could become an issue with hundreds of posts. My current implementation is fine for typical blog sizes, but a future optimization might [lazy-load](https://en.wikipedia.org/wiki/Lazy_loading) post content.
## Lesson 3: mobile-first responsive design
The grid layout may have been the hardest part. My layout needed to work on everything from phones to ultrawide monitors. CSS Grid's `repeat(auto-fit, minmax())` function handles this well, but I found fixed column counts (`repeat(4, 1fr)`) gave more predictable results.

# 📈 The results: a more engaging blog experience

Again taking user feedback from a sample of one user (myself), I've identified several improvements of the enhanced blog:
- Organized content discovery through tag filtering
- Faster navigation with pagination and search
- Better mobile experience with responsive design
- Professional polish that signals my technical skills

Most importantly, I believe the enhanced page showcases problem-solving abilities that translate directly to the kind of work I want to do.
# 🔗 Implementation Details

For fellow developers/enthusiasts interested in the technical implementation:

**File Structure:**
- `_layouts/blog.html` - The main layout with JavaScript
- `assets/style.css` - CSS Grid and responsive styles  
- `blog.md` - Simple page that uses the blog layout

**Key Technologies:**
- Jekyll or static site generation
- CSS Grid for responsive tag layout
- Vanilla JavaScript for all interactivity
- Local storage could be added for user preferences

**GitHub Pages Compatibility:**
Everything runs client-side, working perfectly with GitHub Pages' static hosting and Jekyll processing.
# 🎯 Next steps: always iterating

What I love about my approach is that each enhancement can be added incrementally without breaking existing functionality. With three more enhancements behind me, I have others in mind for the future:
- **tag popularity visualization** with dynamic sizing
- **reading time estimates** for each post
- **related posts suggestions** based on shared tags
- **export functionality** for filtered post lists

# 💡 A note for job seekers

Though I love my current job, I'm actively in search of new opportunities, and developing this page is part of my job search. I believe my new enhancements bolster multiple purposes of the site in my job search:
1. **Portfolio demonstration**: shows JavaScript, CSS, and problem-solving skills
2. **Content organization**: makes it easier for potential employers to find relevant posts
3. **Professional presentation**: a polished blog reflects attention to detail
4. **Learning documentation**: each post becomes a case study

## 🤔 Afterthoughts

Sometimes the best way to learn new skills is to solve real problems. These blog enhancements checked both boxes - improving my site while deepening my front-end development experience.

For the complete code, jump to my [GitHub](https://github.com/nathanwatkinsdc) and try adding similar features to your page.
