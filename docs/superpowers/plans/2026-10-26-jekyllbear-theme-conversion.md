# Plan: jekyllBear theme conversion

## Tasks (TDD order)
1. `test_config_has_theme` — verify `_config.yml` contains `theme: jekyll-bear-theme` and is valid YAML.
2. `test_gemfile_has_gem` — verify `Gemfile` contains `gem "jekyll-bear-theme"`.
3. `test_index_md_has_front_matter` — verify `index.md` has `---` front matter with `layout` and `title`.
4. `test_no_index_html` — verify `index.html` removed from root.
5. `test_content_preserved` — verify about/experience/skills/contact text and GitHub/LinkedIn URLs present in Markdown files.
6. Create `_config.yml`, `Gemfile`, `index.md`, `blog.md`, `life.md`, `404.html`, `_data/life-in-weeks.yml`, `_posts/` seed posts, `_my_tags/` tag pages.
7. Remove `index.html`.
8. Validate all YAML/front matter with Python (no Ruby available locally).
9. (No commit — per user request.)

## Ponytail notes
- YAGNI: no life-in-weeks events unless user provides them; no blog posts unless user provides them; seed structure only.
- Reuse: existing content copy moved verbatim into Markdown.
- Minimum diff: convert one file (index.html → index.md) + supporting Jekyll files.
- `# ponytail:` cannot test `jekyll build` locally (no Ruby/Jekyll installed); validation limited to YAML/front-matter syntax.
