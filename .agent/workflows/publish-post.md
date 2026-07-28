# Workflow: publish a draft post or course

Take a drafted post/course from `draft: true` to live on <https://d4dm.org>, following the Publishing steps in `AGENTS.md`.

## Inputs

- **Target** (required): identifies the content — a directory, an `index.qmd` path, or a slug. If not provided, ask which post/course to publish.

## Steps

1. **Locate the file.** Resolve the target to a single `index.qmd`. If it's a directory, use its `index.qmd`. If it's a bare slug, search `posts/` and `courses/` for a matching directory. If zero or multiple matches, ask to disambiguate.

2. **Flip the draft flag.** Read the front matter. If `draft: true`, change it to `draft: false`. If already `false` or absent, say it's already publishable and confirm before proceeding. Leave `date-modified: last-modified` as-is.

3. **Verify the render.** Run `quarto render` and confirm it completes with no errors — per `AGENTS.md` a post must pass the render test to merge. If it fails, stop, report the errors, and let the user fix them.

4. **Branch & commit.** Do not commit directly to `main`. If on `main`, create a branch (e.g. `publish/<slug>`) first. Stage the source changes (the `.qmd` and any new images) — not generated output under `docs/`/`_site/` unless the repo tracks it. Commit with a clear message (e.g. `Publish post: <title>`).

5. **Open a PR to main.** Use `gh pr create` targeting `main` with a short title and body. Report the PR URL.

6. **Report next step.** Once the render test passes and the PR merges to `main`, the GitHub Actions workflow (`.github/workflows/publish.yml`) publishes the site via GitHub Pages.

Only push/commit/PR when the render is clean. Confirm before creating the PR if anything is ambiguous.
