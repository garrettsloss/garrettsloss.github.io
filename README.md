# garrettsloss.com

Personal website — blog, projects, and resume.

**Stack:** React 19 + Vite + Reactstrap (Bootstrap 5)

---

## Dev commands

```bash
npm run dev       # start local dev server (localhost:5173)
npm run build     # production build → /dist
npm run preview   # preview the production build locally
```

---

## Adding content

All content lives in the `content/` folder as Markdown files. Drop a file in, rebuild, done — no code edits needed.

### Add a project

1. Create `content/projects/your-slug.md` (the filename becomes the URL: `/projects/your-slug`)
2. Add the frontmatter + body:

```markdown
---
title: My Project Title
summary: One-line description shown on the projects listing page.
tags: [React, TypeScript, Whatever]
date: 2026-05-28
---

Write your project content here in **Markdown**.

![image description](/content/projects/your-slug/photo.jpg "optional caption text")
```

3. Put any images in `public/content/projects/your-slug/`
4. Run `npm run build`

### Add a blog post

1. Create `content/blog/your-slug.md` (URL: `/blog/your-slug`)
2. Same frontmatter format as projects:

```markdown
---
title: My Post Title
summary: Optional one-line summary.
date: 2026-05-28
---

Post content in **Markdown**.
```

3. Run `npm run build`

Posts are automatically sorted newest-first by the `date` field.

---

## Downloadable files

Drop any file into `public/content/downloads/` and it's immediately available — no rebuild needed.

```
public/
  content/
    downloads/
      my-resume.pdf
      project-report.md
```

Link to it in Markdown:
```markdown
[Download the report](/content/downloads/project-report.md)
```

Or in JSX (use the `download` attribute to force a download instead of opening in the browser):
```jsx
<a href="/content/downloads/my-resume.pdf" download>Download Resume (PDF)</a>
```

---

## Images

Images referenced from Markdown must live in `public/content/` so they're served at a static path:

```
public/
  content/
    projects/
      your-slug/
        photo.jpg     →  /content/projects/your-slug/photo.jpg
    blog/
      your-slug/
        photo.jpg     →  /content/blog/your-slug/photo.jpg
```

Reference them in Markdown as:
```markdown
![alt text](/content/projects/your-slug/photo.jpg "caption")
```

---

## Project structure

```
content/
  projects/       ← drop .md files here for projects
  blog/           ← drop .md files here for blog posts
public/
  content/        ← images referenced from markdown
src/
  components/     ← SiteNavbar, SiteFooter
  lib/
    content.js    ← glob loader + frontmatter parser (don't need to touch this)
  pages/          ← Home, Projects, ProjectDetail, Blog, BlogPost, Resume, Contact
  App.jsx         ← routes
```

---

## Adding a new page/route

1. Create `src/pages/MyPage.jsx`
2. Import and add a `<Route>` in `src/App.jsx`
3. Add a nav link in `src/components/SiteNavbar.jsx` if needed
