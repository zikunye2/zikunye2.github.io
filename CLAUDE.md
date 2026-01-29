# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal academic website for Zikun Ye (zikunye.com), built with the **al-folio** Jekyll theme. Deployed via GitHub Actions to GitHub Pages (gh-pages branch).

## Default Workflow

When the user opens this project, ask: **"What would you like to update on your website or CV?"**

After they describe changes:
1. Update the relevant website files
2. If the change affects CV content (publications, teaching, services, etc.), also update the CV LaTeX source at `/Users/yezikun/Documents/Personal Website/CV_zikunye/main.tex` and recompile:
   ```bash
   cd "/Users/yezikun/Documents/Personal Website/CV_zikunye" && pdflatex main.tex && cp main.pdf "/Users/yezikun/Documents/Personal Website/zikunye2.github.io/assets/pdf/CV_zikunye.pdf"
   ```
3. If the change is purely about website styling, skip the CV update
4. Start the local preview server (if not already running) and ask the user to check the site:
   ```bash
   cd "/Users/yezikun/Documents/Personal Website/zikunye2.github.io"
   bundle exec jekyll serve --port 4000
   ```
   Run this in the background. Site at http://localhost:4000.
5. Ask: **"Take a look at http://localhost:4000 — are you satisfied, or do you want more changes?"**
6. If not satisfied, make further changes. Jekyll auto-rebuilds on file changes, so just ask the user to refresh the page. If `_config.yml` was changed, restart the server.
7. Once satisfied, push to GitHub and stop the local server:
   ```bash
   cd "/Users/yezikun/Documents/Personal Website/zikunye2.github.io"
   git add -A && git commit -m "description" && git push origin master
   ```
   Then kill the Jekyll serve process.

## Build & Preview

```bash
bundle exec jekyll serve --port 4000
```
Requires Ruby 3.3, bundler. Site served at http://localhost:4000.

## Key Content Files

| File | Purpose |
|------|---------|
| `_pages/about.md` | Homepage with bio, profile image, contact info |
| `_pages/research.md` | Publications, working papers, conference papers, academic services (raw HTML) |
| `_pages/teaching.md` | Course listings |
| `_pages/students.md` | Current students |
| `_pages/cv.md` | CV download link |
| `_data/socials.yml` | Email, Google Scholar ID, LinkedIn |
| `_config.yml` | Site-wide configuration |
| `assets/img/zye.png` | Profile photo |
| `assets/pdf/CV_zikunye.pdf` | Compiled CV PDF |

## CV LaTeX Source

Located outside this repo at `/Users/yezikun/Documents/Personal Website/CV_zikunye/main.tex`. Uses `resume.cls`. Compile with `pdflatex main.tex`.

## Styling

- Theme color: blue (set in `_sass/_themes.scss` using `$blue-color`)
- Max content width: 800px (`_sass/_variables.scss`)
- Profile image size: 21% width (`_sass/_components.scss`)
- Social icons: 2rem font-size (`_sass/_components.scss`)
- Page titles hidden via `display_title: false` front matter (logic in `_layouts/page.liquid`)
- Journal names styled with inline `color: var(--global-theme-color); font-weight: 700` (blue bold)
- No italics used anywhere in research page

## Research Page Conventions

- Author-first format, **Zikun Ye** in bold
- Paper titles are direct hyperlinks to the paper
- `[Code]` link appears right after title
- `†` (&#8224;) = authors listed alphabetically
- `*` (&#42;) = student advised
- Journal names as bullet points in blue bold (not italic)
- Sections: Journal Publications, Working Papers, Conference Papers, Academic Services

## Deployment

Push to `master` triggers `.github/workflows/deploy.yml` which builds with Jekyll and deploys to `gh-pages` branch. GitHub Pages source must be set to "Deploy from a branch" → `gh-pages`.
