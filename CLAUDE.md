# CLAUDE.md

Rules for any AI agent (Claude Code, Copilot, etc.) working in this repo.

## Multi-machine workflow: always pull first, always push after

The maintainer (Zikun) edits this site from multiple computers. To prevent
divergent history and merge conflicts:

1. **Before any edit**, run `git pull --ff-only origin master`.
2. **Immediately after each commit**, run `git push origin master`. Never
   leave a local commit unpushed at the end of a turn.
3. If the fast-forward pull fails (local branch has diverged from origin),
   **stop and ask the maintainer** how to proceed. Do not force, rebase,
   merge, or reset without explicit instruction.

## Deploy is automatic

Pushing to `master` triggers `.github/workflows/deploy.yml`, which runs
Jekyll build and publishes to the `gh-pages` branch. The live site at
[zikunye.com](https://zikunye.com) updates in ~1 minute. There is no
separate deploy step. Check status with:

```sh
gh run list --workflow=deploy.yml --limit 3
```

## CV source lives in `_cv/`

The CV LaTeX source is `_cv/main.tex` (class `_cv/resume.cls`). Jekyll does
not publish `_cv/`, and because it is in this repo, the pull-first/push-after
rule above covers it. Never edit a CV copy outside this repo. Compile and
update both published copies, then commit `_cv/main.tex` together with the
two PDFs (build artifacts are git-ignored):

```sh
cd _cv && pdflatex main.tex && cp main.pdf ../assets/pdf/CV_zikunye.pdf && cp main.pdf ../files/CV_zikunye.pdf
```

Until 2026-10-06 the source lived outside the repo in `../CV_zikunye/`, so
each Mac had its own unsynced copy and they diverged. If `../CV_zikunye` on
this machine is still a real folder (not a symlink to `zikunye2.github.io/_cv`),
it is obsolete: diff its `main.tex` against `_cv/main.tex` and merge anything
newer into `_cv/`, then `mv ../CV_zikunye ../CV_zikunye_old` and
`ln -s zikunye2.github.io/_cv ../CV_zikunye` so older instructions still
resolve.

BasicTeX lacks `wrapfig`, `enumitem`, `kantlipsum` and `textpos`. If
`pdflatex` reports one missing, download those archives from
`https://mirror.ctan.org/systems/texlive/tlnet/archive/<name>.tar.xz` and
copy their `tex/` folder into `~/Library/texmf/`. The four total about 50 KB,
and this needs no sudo.

## Keep llms.txt in sync

`llms.txt` at the repo root is an AI-readable summary of the site, covering
bio, research threads, publications, teaching, services, and contact. When
making content changes that affect any of these (adding a paper, updating a
course, changing the bio, changing services), update `llms.txt` to keep it
in sync. Pure styling changes (CSS, layout, theme) do not require llms.txt
updates.

## Commit messages

Follow `<type>: <description>` (types: `feat`, `fix`, `refactor`, `docs`,
`test`, `chore`, `perf`, `ci`). Match the surrounding history when in doubt.
