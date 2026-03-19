# 🖊️ K!MOBit — Blog Module

[![Live Blog](https://img.shields.io/badge/🌐%20Live%20Blog-ka.budgo.net-4a90e2?style=for-the-badge)](https://ka.budgo.net/blog/index.html)
[![Blog Status](https://img.shields.io/website?url=https%3A%2F%2Fka.budgo.net%2Fblog%2Findex.html&style=for-the-badge&label=Blog%20Status&up_color=brightgreen&down_color=red)](https://ka.budgo.net/blog/index.html)
[![Grubhub Status](https://img.shields.io/website?url=https%3A%2F%2Fka.budgo.net%2F&style=for-the-badge&label=Grubhub%20Status&up_color=FF8000&down_color=red&logo=grubhub&logoColor=white)](https://ka.budgo.net/)
[![Vanilla JS](https://img.shields.io/badge/Vanilla%20JS-SPA-yellow?style=for-the-badge&logo=javascript)](https://ka.budgo.net/blog/index.html)

> A standalone blog experience for the portfolio — powered by vanilla JavaScript with hash-based routing, a built-in terminal, and lazy-loaded posts.

---

## 📸 Preview

[![Blog Screenshot](https://image.thum.io/get/width/1200/crop/800/https://ka.budgo.net/blog/index.html)](https://ka.budgo.net/blog/index.html)

---

## 📋 Table of Contents

- [Scope](#-scope)
- [Architecture](#-architecture)
- [Run Locally](#-run-locally)
- [Add a New Blog Post](#-add-a-new-blog-post)
- [Add a New Category](#-add-a-new-category)
- [Notes](#-notes)

---

## 🗂️ Scope

This README covers the standalone blog module only.

| File / Folder | Purpose |
|---|---|
| `blog/index.html` | Entry page |
| `blog/css/` | Styles |
| `blog/data/posts.en.json` | Post metadata |
| `blog/js/` | Client-side logic |
| `blog/posts/en/` | Post HTML content |

---

## 🏗️ Architecture

The blog is a **vanilla JavaScript hash-routed SPA** — no build step required.

| Module | Responsibility |
|---|---|
| `blog/js/router.js` | Hash-based routing |
| `blog/js/blog.js` | Main rendering & route handlers |
| `blog/js/post-loader.js` | Lazy-loads post HTML |
| `blog/js/filters.js` | Filters & card rendering |
| `blog/js/terminal.js` | Terminal command interface |

---

## 🚀 Run Locally

Use any static server from the repository root:

```bash
npx vite --port=4000
```

Then open:

```
http://localhost:4000/blog/
```

---

## ✍️ Add a New Blog Post

**1.** Create the post HTML file:

```text
blog/posts/en/<category>/<slug>.html
```

**2.** Add metadata in:

```text
blog/data/posts.en.json
```

**3.** Required metadata fields:

| Field | Description |
|---|---|
| `id` | Unique slug (used for routing) |
| `title` | Post title |
| `excerpt` | Short description |
| `date` | `YYYY-MM-DD` format |
| `category` | Must match a configured category |
| `tags` | Array of tag strings |
| `difficulty` | Skill level indicator |
| `readTime` | Estimated read time |
| `icon` | Emoji or icon string |
| `file` | Relative path to post HTML |

**4.** Optional fields: `pinned`, `cost`, `materials`, `hardware`

**5.** Verify in browser:

- ✅ Home cards
- ✅ Browse filters
- ✅ Category pages
- ✅ Terminal `ls`, `search`, and `cat`

---

## 🗃️ Add a New Category

1. Add the category to `CATEGORIES` in `blog/js/blog.js`.
2. Use the **exact same** category name in post metadata.
3. Add posts using that category.

---

## 📝 Notes

> ⚠️ The blog expects JSON metadata and HTML post files to stay in sync.

- If a post fails to open, verify the `file` path in `posts.en.json`.
- Keep post `id` values unique — routing depends on them.
