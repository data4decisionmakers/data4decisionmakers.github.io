# Workflow: new course page

Scaffold a new course page for the D4DM website. Per `AGENTS.md`, each course lives in its own sub-directory under `courses/`.

## Inputs

- **Title** (required): the course title. If not provided, ask for one.

## Steps

1. **Build the slug** from the title: lowercase, spaces → hyphens, drop characters that aren't `a-z`, `0-9`, or `-`, collapse repeated hyphens. E.g. "Introduction to survey analysis" → `introduction-to-survey-analysis`.

2. **Directory** = `courses/<slug>/`. If it already exists, stop and report it rather than overwriting.

3. **Create `courses/<slug>/index.qmd`** with this front matter (fill `title`; leave the rest as placeholders to edit):

   ```yaml
   ---
   title: "<TITLE>"
   subtitle: "Course sub-title"
   description: "Course description"
   author: "Ernest Guevarra"
   date-modified: last-modified
   image: "images/preview.png"
   draft: true
   categories:
     - course
   ---

   ## Overview

   Describe the course here.

   ## Schedule

   ## Registration
   ```

   Set `draft: true` so unpublished courses don't appear on the site. The `image:` path is relative to the course directory.

4. **Report** the created file path. Remind the user to link it from the Courses overview page (`courses/index.qmd`) if that listing exists, to add `images/preview.png`, and that the course stays hidden until `draft: false`.

Do not run `quarto render` or commit — leave that to the user.
