# MohsenRsh.github.io

Personal portfolio + "Miscellaneous" blog section. Plain HTML/CSS, no
framework, no build step. Hosted via GitHub Pages from this repo's root.

## Site structure
- `index.html` — homepage (photo, about, links, collapsible Miscellaneous
  section with post cards)
- `style.css` — all styles, including shared blog post styles
- `<slug>.html` — one file per blog post (e.g. `ruv-seq.html`,
  `anndata-to-seurat.html`)
- `sitemap.xml` — lists homepage + every post URL
- `profile-photo.png`, `*.png` — images used as default OG image / figures

Source markdown drafts for posts live outside this repo, in
`/home/mohsenrsh/Projects/mohsen_portofolio/<slug>-blog/`.

## Adding a new blog post
Each post is an isolated, additive change — don't touch unrelated parts of
`index.html` or `style.css`.

1. **Create `<slug>.html`** in the repo root, copying the structure of
   `anndata-to-seurat.html`:
   - `<title>` = "{Post Title} — Mohsen Rastgoo Shahrestani"
   - `<meta name="description">` = one-line summary
   - OG tags: `og:type=article`, `og:url`, `og:title`, `og:description`,
     `og:image` (default `profile-photo.png`, or a figure image if the post
     has one)
   - `<body class="post-page">` > `<div class="post-container">`
   - `<a href="index.html" class="back-link">← back</a>`
   - `<h1 class="post-title">`
   - Sections as `<h2 class="post-heading">` + `<p class="post-p">`
   - Optional `<div class="post-figure"><img ...></div>` placed where it's
     referenced in the text
   - Closing `<p class="post-footer">` with GitHub repo link (if any) and
     the standard line: "This is part of a series where I document
     challenges and resolutions from my ongoing bioinformatics work...
     Reach out via LinkedIn."

2. **Add one `.post-card` to `index.html`** inside `.post-cards`
   (in `#misc-body`):
   ```html
   <a href="<slug>.html" class="post-card">
       <p class="post-card-title">{Post Title}</p>
       <p class="post-card-summary">{One-line summary}</p>
       <div class="post-card-footer">
           <span class="post-card-date">{Month Year}</span>
           <span class="post-card-arrow">→</span>
       </div>
   </a>
   ```
   New cards go at the end of the list (most recent last, top of list = oldest).

3. **Add an entry to `sitemap.xml`**:
   ```xml
   <url>
       <loc>https://mohsenrsh.github.io/<slug>.html</loc>
       <priority>0.8</priority>
   </url>
   ```

4. **No CSS changes needed** — `style.css` already has generic
   `.post-*` and `.misc-*` styles shared by all posts.

5. Commit and push to publish (GitHub Pages serves directly from this repo).

## Design constraints (don't change without being asked)
- Dark theme: `--bg: #102030`, `--text: #f0f2f5`, `--accent: #c8d0dc`,
  `--text-muted: #8896a8`, `--border: #1e2e42`.
- Fonts: Merriweather (headings/titles), Inter (body).
- Don't modify anything above the contact icons in `index.html` (photo,
  name, subtitle, about text) unless explicitly asked.
- Miscellaneous section is collapsed by default; only the post cards
  collapse/expand, the title+description box stays visible.
