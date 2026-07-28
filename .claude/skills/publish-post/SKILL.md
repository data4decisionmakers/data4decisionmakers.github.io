---
name: publish-post
description: Publish a D4DM draft post or course by flipping draft:true to draft:false, verifying the render, then guiding the commit -> PR-to-main -> merge flow from the AGENTS.md Publishing steps. Invoke with /publish-post <path or slug>.
disable-model-invocation: true
---

Read `.agent/workflows/publish-post.md` and follow the procedure there. It is the single source of truth for this workflow (agent-agnostic).

`$ARGUMENTS` supplies the **target** — a directory, an `index.qmd` path, or a slug identifying the content to publish.
