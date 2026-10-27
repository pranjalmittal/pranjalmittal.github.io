# Spec: convert static HTML portfolio to Jekyll site using jekyllBear theme

## Goal
Convert `/data/home/workspace/pranjalmittal.github.io` from a single static `index.html` to a Jekyll site using the [jekyllBear](https://github.com/knhash/jekyllBear) theme, preserving all existing content (about, experience, skills, contact) plus theme features (blog, tags, life timeline, light/dark mode).

## Why
The user wants the jekyllBear theme. GitHub Pages natively builds Jekyll sites, so this is the natural fit rather than fighting static HTML against a Jekyll theme config.

## Scope (in)
- `_config.yml`: `theme: jekyll-bear-theme`, personal title/description/url, navbar links, tags collection, permalink, timezone
- `Gemfile`: `gem "jekyll-bear-theme"`
- `index.md`: home page (about + experience + skills + contact), `layout: default`
- `blog.md`: blog listing, `layout: blog`
- `life.md`: life-in-weeks timeline (optional, theme feature)
- `404.html`: 404 page
- `_data/life-in-weeks.yml`: life events data (optional)
- `_posts/`: migrated experience highlights as dated posts (optional seed content)
- `_my_tags/`: tag pages (design, fiction, general, poem)
- Remove `index.html` (replaced by `index.md`)

## Scope (out)
- No Tailwind (reverted — previous experiment discarded via backup)
- No build tooling beyond Jekyll/GitHub Pages
- No CI, no linting

## Acceptance criteria
- `_config.yml` is valid YAML with `theme: jekyll-bear-theme`
- `Gemfile` declares `gem "jekyll-bear-theme"`
- All pages have valid Jekyll front matter (`---` block with `layout` and `title`)
- Existing content (about, experience, skills, contact, GitHub/LinkedIn links) preserved in Markdown
- Site builds as a standard GitHub Pages Jekyll site (no custom plugins beyond theme)
- No `index.html` remains at root

## Rejected alternatives
| Alternative | Reason rejected |
|---|---|
| Keep static HTML + remote_theme | Jekyll themes require Jekyll processing; static HTML ignores theme layouts |
| `remote_theme: knhash/jekyllBear` | Theme README documents gem-based `theme: jekyll-bear-theme`; follow documented install |
| Full blog migration (all experience as posts) | Over-scoped; seed minimal posts, keep experience on home page |
