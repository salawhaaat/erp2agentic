# CLAUDE.md — working notes for this vault

This is an Obsidian vault, not a codebase: a NYU Tandon course (**IE-GY 9113B — Systems Integration: From ERP to Agentic AI**), converted from Brightspace PDFs into Markdown so it's git-trackable and shareable on GitHub. Start at [[index]] for navigation.

## Structure

- `index.md` — vault home / map of content (Obsidian-facing navigation).
- `README.md` — short GitHub-facing landing page; points to `index.md`.
- `announcements.md` — running log of professor's Brightspace announcements, newest first.
- `Syllabus and Rubrics/` — syllabus and assessment rubrics (course-wide references, not weekly).
- `Final Project Info/` — capstone kit orientation, storyboard, and the Board Memo/Presentation `.docx`/`.pptx` templates (left as binary, not converted).
- `w0/`, `w1/`, `w2/`, `w3/` — one folder per course week, holding that week's study note(s)/slides only. **Capstone deliverables do not live here** — see `project/`.
- `project/` — the team's Sweetgreen capstone work: the backbone-context note, the context-and-diagnosis brief, the Lab 1 pre-work brief, and raw in-class breakout scratch notes. Kept separate from `w1`/`w2`/`w3` so the capstone reads as one unit instead of being scattered across weeks.

## Capstone context

- **Company:** Sweetgreen (fast-casual restaurant chain). Confirmed in Week 2; an earlier Week 1 practice exercise used AWS as a throwaway drill, not the real company — see the note at the top of `project/Agentic AI Project.md`.
- **Process:** Order-to-Cash (customer order → payment → kitchen → prep → verify/pack → pickup/delivery → transaction complete).
- **Core thesis so far:** the backbone's weakest point is the handoff between digital ordering channels and kitchen execution (traditional line vs. Infinite Kitchen) — order accuracy and availability information don't reliably survive that handoff. This is the throughline across all three deliverables in `project/`.
- Deliverables build on each other in order: backbone-context note → context-and-diagnosis brief → Lab 1 pre-work → feeds Board Memo §2/§3 and storyboard slides S1/S3/S4/S5. Don't re-derive the diagnosis from scratch each time — extend/refine the existing chain, and update all three together if the underlying diagnosis changes.

## Formatting conventions (apply these to any note you add or edit)

- **Frontmatter:** every note gets YAML frontmatter with at least `title` and `tags`.
- **Headings:** one `#` document title, `##` for major sections, `###` for subsections. No orphaned page-number/footer artifacts (these came from PDF conversion — strip them, don't preserve them).
- **Tables:** always clean GFM tables (`| col |` with a `|---|` separator row). If source text is too mangled to confidently reconstruct as a table, use a bullet/definition list instead rather than leaving broken pipe fragments.
- **Foldable callouts:** wrap dense reference material, worked examples, long case narratives, or anything a reader would consult rather than read straight through, in a collapsed Obsidian callout:
  ```
  > [!example]- Section Title
  > content, one "> " per line including blank lines
  ```
  Use `[!example]-`, `[!info]-`, `[!note]-`, or `[!quote]-` as fits. The trailing `-` collapses it by default (`+` would default-expand). Never fold core teaching content, due dates, or homework instructions — only supplementary material.
- **Wikilinks:** use bare `[[Note Name]]` or `[[Note Name|display text]]` — Obsidian resolves by filename across the whole vault regardless of folder, so links don't need full paths and survive files being moved between folders.
- **Diagrams:** Mermaid renders natively in Obsidian (and on GitHub). Use `flowchart` diagrams for process maps; mark control points and decision points explicitly when diagramming a business process (this course's own vocabulary — see [[w0/W0_ERPFloor_Course Primer]] and [[w1/W01_IntegrationBackbone_StudyNote_PB14]]).
- **No PDFs in this vault** — every source PDF was converted to Markdown and the original PDF deleted. If a new PDF shows up (e.g. a new week's study note from Brightspace), convert it (`markitdown`) and delete the PDF rather than keeping both.

## Open items

See the checklist in [[index]] for what's drafted vs. still a real-world action (emailing the professor, setting up tool accounts, etc.) — those can't be done from inside the vault.
