# Workflow: new blog post

Scaffold a new Quarto blog post for the D4DM website, following the post conventions in `AGENTS.md`.

## Inputs

- **Title** (required): the post title. If not provided, ask for one.
- **Date** (optional): a `YYYY-MM-DD` date. If not provided, use today's date (determine it, e.g. `date +%F` — do not guess).

## Steps

1. **Build the slug** from the title: lowercase, spaces → hyphens, drop characters that aren't `a-z`, `0-9`, or `-`, collapse repeated hyphens. E.g. "Getting started with survey data" → `getting-started-with-survey-data`.

2. **Directory** = `posts/<DATE>-<slug>/`. If it already exists, stop and report it rather than overwriting.

3. **Create `posts/<DATE>-<slug>/index.qmd`** with this front matter (fill `title` and `date`; leave the rest as placeholders to edit):

   ```yaml
   ---
   title: "<TITLE>"
   subtitle: "Post sub-title"
   description: "Post description"
   author: "Ernest Guevarra"
   date: "<DATE>"
   date-modified: last-modified
   image: "images/preview.png"
   draft: true
   categories:
     - tutorial
   ---

   Write your post here.
   ```

   Set `draft: true` so unfinished posts don't publish. The `image:` path is relative to the post directory — add `images/preview.png` (the listing thumbnail) or remove the line if unused.

4. **Report** the created file path. Preview with `quarto preview`; the post stays hidden until `draft: false`.

Do not run `quarto render` or commit — leave that to the user.
