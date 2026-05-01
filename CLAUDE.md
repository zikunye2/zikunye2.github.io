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

## Commit messages

Follow `<type>: <description>` (types: `feat`, `fix`, `refactor`, `docs`,
`test`, `chore`, `perf`, `ci`). Match the surrounding history when in doubt.
