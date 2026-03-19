# K!MOBit Blog Module

This folder contains the standalone blog experience for the portfolio.

## Scope

This README is for the blog only.

- Entry page: `blog/index.html`
- Styles: `blog/css/`
- Data source: `blog/data/posts.en.json`
- Client logic: `blog/js/`
- Post content: `blog/posts/en/`

## Architecture

The blog is a vanilla JavaScript hash-routed SPA.

- Routes are handled in `blog/js/router.js`.
- Main page rendering and route handlers are in `blog/js/blog.js`.
- Post HTML is lazy-loaded by `blog/js/post-loader.js`.
- Filters and cards are handled by `blog/js/filters.js`.
- Terminal commands are handled by `blog/js/terminal.js`.

## Run Locally

Use any static server from the repository root.

```bash
npx vite --port=4000
```

Then open:

- `http://localhost:4000/blog/`

## Add a New Blog Post

1. Create the post HTML file:

```text
blog/posts/en/<category>/<slug>.html
```

2. Add metadata in:

```text
blog/data/posts.en.json
```

3. Required metadata fields per post object:

- `id` (unique slug)
- `title`
- `excerpt`
- `date` (`YYYY-MM-DD`)
- `category` (must match configured category names)
- `tags` (array)
- `difficulty`
- `readTime`
- `icon`
- `file` (relative path to post HTML)

4. Optional fields:

- `pinned`
- `cost`
- `materials`
- `hardware`

5. Verify in browser:

- Home cards
- Browse filters
- Category pages
- Terminal `ls`, `search`, and `cat`

## Add a New Category

1. Add the category to `CATEGORIES` in `blog/js/blog.js`.
2. Use the exact same category name in post metadata.
3. Add posts using that category.

## Notes

- The blog expects JSON metadata and HTML post files to stay in sync.
- If a post fails to open, check the `file` path in `posts.en.json`.
- Keep post IDs unique; routing depends on `id` values.
