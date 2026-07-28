---
name: new-post
description: Scaffold a new D4DM blog post directory under posts/<YYYY-MM-DD-slug>/index.qmd with the standard Quarto front matter. Invoke with /new-post <post title> (optionally add a date, e.g. /new-post "My title" 2026-08-01).
disable-model-invocation: true
---

Read `.agent/workflows/new-post.md` and follow the procedure there. It is the single source of truth for this workflow (agent-agnostic).

`$ARGUMENTS` supplies the inputs: the post **title**, optionally followed by a `YYYY-MM-DD` **date**. Strip surrounding quotes from the title.
