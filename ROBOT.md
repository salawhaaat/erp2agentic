# Working notes for this vault

This is an Obsidian vault, not a codebase. It's a NYU Tandon course, IE-GY 9113B: Systems Integration, From ERP to Agentic AI, converted from Brightspace PDFs into Markdown so it's easy to track in git and browse on GitHub. Start at [[index]] for navigation.

## Structure

- `index.md`: vault home and map of content, the main navigation page in Obsidian.
- `announcements.md`: running log of the professor's Brightspace announcements, newest first.
- `Syllabus and Rubrics/`: syllabus and assessment rubrics. Course-wide references, not tied to a specific week.
- `Final Project Info/`: capstone kit orientation, storyboard, and the Board Memo/Presentation `.docx`/`.pptx` templates. These stay as binary files, not converted to Markdown.
- `w0/`, `w1/`, `w2/`, `w3/`: one folder per course week, holding that week's study notes and slides only. Capstone deliverables don't live here, see `project/`.
- `project/`: the team's Sweetgreen capstone work. Backbone-context note, context-and-diagnosis brief, Lab 1 pre-work brief, the Lab 1 process map, a research log under `project/research/`, standalone diagram source files under `project/diagrams/` (embedded into the write-up notes with `![[...]]` rather than pasted inline, so a diagram can be edited in one place), and raw in-class breakout scratch notes. Kept separate from `w1`/`w2`/`w3` so the capstone reads as one unit instead of being scattered across weeks.

## Capstone context

- **Company:** Sweetgreen, a fast-casual restaurant chain. Confirmed in Week 2. An earlier Week 1 practice exercise used AWS as a throwaway drill, not the real company. See the note at the top of `project/Agentic AI Project.md`.
- **Process:** Order-to-Cash, meaning customer order, payment, kitchen, prep, verify and pack, pickup or delivery, then transaction complete.
- **Core thesis so far:** the backbone's weakest point is the handoff between digital ordering channels and kitchen execution (traditional line vs. Infinite Kitchen). Order accuracy and availability information don't reliably survive that handoff. This idea runs through everything in `project/`.
- Deliverables build on each other in order: backbone-context note, then context-and-diagnosis brief, then Lab 1 pre-work and process map. These feed Board Memo §2/§3 and storyboard slides S1/S3/S4/S5. Don't re-derive the diagnosis from scratch each time. Extend or refine the existing chain, and update everything together if the underlying diagnosis changes.

## Formatting conventions

Apply these to any note you add or edit.

- **Frontmatter:** every note gets YAML frontmatter with at least `title` and `tags`.
- **Headings:** one `#` document title, `##` for major sections, `###` for subsections. Strip any orphaned page-number or footer artifacts left over from PDF conversion; don't preserve them.
- **Tables:** always clean GFM tables (`| col |` with a `|---|` separator row). If the source text is too mangled to confidently reconstruct as a table, use a bullet or definition list instead, rather than leaving broken pipe fragments.
- **Foldable callouts:** wrap dense reference material, worked examples, long case narratives, or anything a reader would consult rather than read straight through, in a collapsed Obsidian callout:
  ```
  > [!example]- Section Title
  > content, one "> " per line including blank lines
  ```
  Use `[!example]-`, `[!info]-`, `[!note]-`, or `[!quote]-` as fits. The trailing `-` collapses it by default (`+` would default-expand). Never fold core teaching content, due dates, or homework instructions, only supplementary material.
- **Wikilinks:** use bare `[[Note Name]]` or `[[Note Name|display text]]`. Obsidian resolves by filename across the whole vault regardless of folder, so links don't need full paths and survive files being moved between folders.
- **Diagrams:** Mermaid renders natively in Obsidian and on GitHub. Use `flowchart` diagrams for process maps, and mark control points and decision points explicitly when diagramming a business process. That's this course's own vocabulary; see [[w0/W0_ERPFloor_Course Primer]] and [[w1/W01_IntegrationBackbone_StudyNote_PB14]].
- **No PDFs in this vault.** Every source PDF gets converted to Markdown and the original deleted. If a new PDF shows up, say a new week's study note from Brightspace, convert it (`markitdown`) and delete the PDF rather than keeping both.

## Writing style

Write plainly. Avoid em dashes; use commas, periods, or parentheses instead. Avoid stacking clauses into one long sentence when two short ones read better. Skip AI-tell phrasing like "it's not just X, it's Y" or "this isn't merely A, it's B." Say the thing directly.

## Open items

See the checklist in [[index]] for what's drafted vs. still a real-world action (emailing the professor, setting up tool accounts, etc.). Those can't be done from inside the vault.
