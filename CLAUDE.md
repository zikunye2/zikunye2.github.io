# CLAUDE.md

Rules for any AI agent (Claude Code, Copilot, etc.) working in this repo.

Personal academic website for Zikun Ye ([zikunye.com](https://zikunye.com)),
built with the **al-folio** Jekyll theme. The CV LaTeX source lives here too,
in `_cv/`.

This file is the single source of truth for both of Zikun's Macs, and the
`CLAUDE.md` in the parent folder is a symlink to it — an agent started in this
repo or one level up reads the same rules. So keep every path here
**repo-relative**: the two machines have different home directories
(`/Users/zikunye` and `/Users/yezikun`), and absolute paths break on one of
them.

## Multi-machine workflow: always pull first, always push after

The maintainer (Zikun) edits this site from multiple computers. To prevent
divergent history and merge conflicts:

1. **Before any edit**, run `git pull --ff-only origin master`.
2. **Immediately after each commit**, run `git push origin master`. Never
   leave a local commit unpushed at the end of a turn.
3. If the fast-forward pull fails (local branch has diverged from origin),
   **stop and ask the maintainer** how to proceed. Do not force, rebase,
   merge, or reset without explicit instruction.

## Default workflow for a content request

When Zikun opens this project, ask: **"What would you like to update on your
website or CV?"** Then:

1. Pull first (above). Update the relevant site files.
2. If the change touches CV content (publications, teaching, services), also
   update `_cv/main.tex` and recompile — see `_cv/` below.
3. If it touches bio, research, publications, teaching, services, or contact,
   update `llms.txt` too. A bio-only change needs `llms.txt` but not the CV.
4. A purely stylistic change (CSS, layout, theme) needs neither the CV nor
   `llms.txt`.
5. Start the preview server, ask Zikun to look at http://localhost:4000, and
   ask whether to make further changes.
6. Once satisfied, commit, push (deploy is automatic), and stop the server.

## Build & preview

```sh
bundle exec jekyll serve --port 4000
```

Requires Ruby 3.3 and bundler. Run it in the background; site at
http://localhost:4000.

**The watcher is unreliable.** It reports "Auto-regeneration: enabled" but
often does not rebuild `_site/` after edits to `_pages/*.md` or `llms.txt`,
and touching the files does not help. Do not trust the page to refresh
itself: restart the server after edits (a fresh build takes ~30 s), or check
the mtime of `_site/<page>/index.html` before concluding an edit did not
apply. A `_config.yml` change always requires a restart.

## Deploy is automatic

Pushing to `master` triggers `.github/workflows/deploy.yml`, which runs
Jekyll build and publishes to the `gh-pages` branch. The live site updates in
~1 minute. There is no separate deploy step. GitHub Pages must stay set to
"Deploy from a branch" → `gh-pages`. Check status with:

```sh
gh run list --workflow=deploy.yml --limit 3
```

## CV source lives in `_cv/`

The CV LaTeX source is `_cv/main.tex` (class `_cv/resume.cls`;
`_cv/CV_template.tex` is the upstream sample for that class, kept for
reference and not part of the build). Jekyll does not publish `_cv/` — it is
neither in `include:` nor a declared collection — and because it is in this
repo, the pull-first/push-after rule above covers it. Never edit a CV copy
outside this repo. Compile and update both published copies, then commit
`_cv/main.tex` together with the two PDFs (build artifacts are git-ignored):

```sh
cd _cv && pdflatex main.tex && cp main.pdf ../assets/pdf/CV_zikunye.pdf && cp main.pdf ../files/CV_zikunye.pdf
```

Until 2026-10-06 the source lived outside the repo in `../CV_zikunye/`, so
each Mac had its own unsynced copy and they diverged. Both Macs are now
migrated and `../CV_zikunye` is a symlink to this folder, so older
instructions naming that path still resolve. If you ever find it as a real
folder again, it is obsolete: diff its `main.tex` against `_cv/main.tex`,
merge anything newer, then replace it with
`ln -s zikunye2.github.io/_cv ../CV_zikunye`.

BasicTeX lacks `wrapfig`, `enumitem`, `kantlipsum` and `textpos`. If
`pdflatex` reports one missing, download those archives from
`https://mirror.ctan.org/systems/texlive/tlnet/archive/<name>.tar.xz` and
copy their `tex/` folder into `~/Library/texmf/`. The four total about 50 KB,
and this needs no sudo. (A machine with full TeX Live needs none of this.)

## Keep llms.txt in sync

`llms.txt` at the repo root is an AI-readable summary of the site, covering
bio, research threads, publications, teaching, services, and contact. When
making content changes that affect any of these (adding a paper, updating a
course, changing the bio, changing services), update `llms.txt` to keep it
in sync. Pure styling changes (CSS, layout, theme) do not require llms.txt
updates.

## Key content files

| File | Purpose |
|------|---------|
| `_pages/about.md` | Homepage with bio, profile image, contact info |
| `_pages/research.md` | Publications, working papers, academic services (raw HTML) |
| `_pages/teaching.md` | Course listings |
| `_pages/students.md` | Current students |
| `_pages/cv.md` | CV download link + embedded PDF preview |
| `llms.txt` | AI-readable site summary at repo root |
| `_cv/main.tex` | CV LaTeX source |
| `_config.yml` | Site-wide configuration |
| `_data/socials.yml` | (currently empty; email comes from `_config.yml`) |
| `assets/img/zye.png` | Profile photo |
| `assets/pdf/CV_zikunye.pdf` | Compiled CV PDF (website embed) |
| `files/CV_zikunye.pdf` | Compiled CV PDF (school official link: zikunye.com/files/CV_zikunye.pdf) |

## Styling

- Theme color: blue (set in `_sass/_themes.scss` using `$blue-color`)
- Max content width: 800px (`_sass/_variables.scss`)
- Profile image size: 21% width (`_sass/_components.scss`)
- Social icons: 2rem font-size (`_sass/_components.scss`)
- Page titles hidden via `display_title: false` front matter (logic in `_layouts/page.liquid`)
- Journal names styled with inline `color: var(--global-theme-color); font-weight: 700` (blue bold)
- No italics used anywhere in the research page

## Research page conventions

- Author-first format, **Zikun Ye** in bold
- Paper titles are direct hyperlinks to the paper
- `[Code]` link appears right after the title
- `†` (`&#8224;`) = authors listed alphabetically
- `*` (`&#42;`) = student advised
- Journal names as bullet points in blue bold (not italic)
- Sections: Journal Publications, Working Papers, Academic Services
- **Journal Publications order: newest first.** The most recent (or
  forthcoming) paper goes at the top. Applies to the website and the CV.
- **Working Papers order is by status**, more advanced first: Minor/Major
  Revision → Under Review → In Preparation. Applies to the website and
  `_cv/main.tex`; the two must stay in sync.
- **CV-only rule:** in the `Working Papers` section of `_cv/main.tex`, journal
  names must NOT be bolded — no `\textbf{}` around them, keep them plain
  inside the italic status phrase. Journal Publications in the CV still use
  `\textbf{}` for journal names.

## Commit messages

Follow `<type>: <description>` (types: `feat`, `fix`, `refactor`, `docs`,
`test`, `chore`, `perf`, `ci`). Match the surrounding history when in doubt.
