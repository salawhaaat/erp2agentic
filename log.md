---
title: Vault Activity Log
type: log
tags: [log]
---

# Vault Activity Log

OKF-style: date-grouped, newest date first. Backfilled from git history and session context on 2026-09-25 when this log was introduced and later reformatted to match [Open Knowledge Format v0.2](https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md); entries before 2026-09-25 are reconstructed from commit messages, not written live.

## 2026-09-25

* **Ingest**: Converted Week 4 study note (RPA) from PDF to Markdown, added to `raw/papers/course-weeks/w4/`.
* **Deliverable**: Sharpened the Lab 1 process map post-checkpoint; initially added a speculative quality control point (CP7) based on a misread of guest-lecturer feedback — corrected later the same day.
* **Deliverable**: Drafted the Week 4 RPA-candidate scan for Sweetgreen (Board Memo §4): ran the three-test filter across the Lab 1 map, confirmed D2 as the RPA candidate, D3 as the AI-agent target, rejected D1/the quality gate/the stock-accuracy root cause with reasons.
* **Ingest**: Backfilled two missing professor announcements (Sep 17 Final Project Kit, Sep 18 Strong first build) into the announcements log.
* **Lint**: Adopted the LLM-wiki pattern for this vault: added this log, a `concepts/` layer, and an ingest/query/lint workflow documented in `ROBOT.md`.
* **Ingest**: Received the actual final, checkpoint-graded Lab 1 artifacts (the team's annotated map PDF, dated 24 Sep 2026, and a regenerated Gemini sandbox `.xlsx`). Reconciled: the real checkpoint feedback was "make control points more specific" (CP1–CP6 now carry trigger/owner/fields/downstream use), not "add a quality control point" — the guest lecturer's suggestion was considered and explicitly not taken. Reverted the CP7 addition across the diagram, the Lab 1 note, the RPA scan, and the concept pages.
* **Update**: Rebuilt the order-and-payment process diagram as a six-stage production-workflow view leading, full BPMN detail folded underneath — superseded later the same day by the swimlane image.
* **Lint**: Installed the `wiki@llm-wiki` Claude Code plugin (github.com/nvk/llm-wiki, user scope) at the user's request. Not wired into this vault — it maintains its own separate store at `~/wiki/topics/<name>/`; this vault's raw/wiki split is maintained by hand.
* **Lint**: Restructured the entire vault into the two-layer LLM-wiki pattern on disk, not just documented conceptually. Moved the syllabus/rubrics/final-project-info materials, `w0`–`w4`, `announcements.md`, the breakout scratch notes, and the Lab 1 data sandbox under `raw/` (`raw/papers/{syllabus-and-rubrics,final-project-info,course-weeks}/`, `raw/data/transcripts/`, `raw/data/`). Moved `concepts/` and all capstone deliverables/diagrams/research under `wiki/`. Added two new wiki sublayers: `wiki/entities/` (Sweetgreen, Thermo Fisher Scientific, Bailey Hydraulics) and `wiki/comparisons/` (RPA vs. Traditional Automation vs. AI).
* **Update**: Rebuilt the primary diagram as a Mermaid swimlane flowchart (`subgraph` per actor). Rendered and inspected it directly (`mermaid-cli`) after a readability complaint — confirmed Mermaid reorders subgraphs unpredictably around this process's back-edges (the recovery loop, the escalation loop), producing an unreadable tangle. Discovered the *original* full-detail BPMN diagram had the same latent problem.
* **Update**: Replaced both diagrams (swimlane and full-detail) with flat, left-to-right Mermaid flowcharts, actor conveyed by node color instead of physical `subgraph` lanes. Verified clean layout via direct render before reintroducing.
* **Update**: User pointed to the Week 3 lecture notes' "annotated process map" slide (a Citi Bike worked example) as the target visual style. Hand-built an SVG matching that grammar (★ control point, ◆ decision point, red dashed rejection/rework path, ⚡ value-leak annotations, muted swimlane bands) for the Sweetgreen order-and-payment flow, rendered to PNG via `rsvg-convert`, iterated twice to fix node overlaps and arrow routing, and made it the primary embedded diagram (`wiki/project/diagrams/assets/Order-and-Payment-Swimlane.png` + `.svg` source).
* **Lint**: Reversed the PDF-deletion policy. Restored all original course PDFs from Downloads into `raw/`, paired by matching basename next to their existing Markdown conversions (deduped identical-content re-downloads by hash first); added `Final Project Teams.pdf` as a new raw reference, kept as-is and not excerpted since it names other students. Reasoning: text conversion is lossy for anything visually laid out, and that's exactly the content worth having later (the Citi Bike diagram slide above is the proof case).
* **Lint**: Adopted Google's [Open Knowledge Format (OKF) v0.2](https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md). Added `okf_version: "0.2"` to `index.md`; added the required `type` frontmatter field across `wiki/` and `raw/data/transcripts/`; documented conformance rules (required `type`, recommended `description`/`sources`/`generated`/`verified`) in `ROBOT.md`; reformatted this log to OKF's date-grouped style.
* **Lint**: Split `raw/papers/` by format, not just by topic, so the pairing between a PDF and its Markdown conversion is unambiguous from the folder alone: originals vs. conversions, mirrored topic folder for topic folder, same basename. Added a Markdown transcription of the final annotated map so that PDF isn't the odd one out without a Markdown twin. Added a `sources` provenance block (OKF pattern) to `wiki/project/Lab1-Process-Map-Sweetgreen.md` pointing at the two `raw/` files it's substantively derived from, as the first worked example of that field.
* **Lint**: Consolidated `raw/` to a single child, `raw/data/`, after feedback that four top-level folders directly under `raw/` (the format split plus `transcripts/` and `datasets/`) was one layer of clutter too many. Final shape: `raw/data/pdf/<topic>/`, `raw/data/markdown/<topic>/` (same topic folders, same basenames, mirrored), `raw/data/datasets/` (the sandbox `.xlsx`), `raw/data/transcripts/` (announcements). Fixed every literal path reference in `ROBOT.md`, `index.md`, and the Lab 1 note's `sources` block to match. Audited for redundant/leftover files while at it (a stray macOS `.DS_Store`, already gitignored; no actual duplicate content found).
* **Lint**: Checked every Markdown file in the vault for a leading blank line before frontmatter (user report) — none found; the visual gap they saw is almost certainly Obsidian's Properties panel rendering, not a file defect.
* **Lint**: Moved `Sweetgreen-Breakout-Scratch-Notes.md` out of `raw/data/transcripts/` into its own `raw/data/scratch-notes/` — it isn't a transcript of anyone else's words (it's the team's own in-class working notes, already typed `scratch-notes`), so it didn't belong grouped with `announcements.md`. `transcripts/` is now genuinely verbatim-only.
* **Lint**: Removed the two pre-curveball diagram PNGs (`Order-and-Payment-Process-Map-Annotated.png`, `-Diagram-Only.png`, generated 18 Sep 2026) — superseded by the swimlane image and carrying stale control-point/decision labels. Noted that the board deck's own slide S5 still has the old image baked in as binary (deleting the standalone PNG doesn't touch an already-embedded copy) and flagged it for re-export next time that deck is touched.

## 2026-09-18

* **Update**: Added the Lab 1 process map, resolved the curveball (Wonder/Infinite Kitchen boundary, then revised to the nightly-batch/stale-cache curveball), and added the Sweetgreen research log.
* **Deliverable**: Completed Lab 1: data sandbox, filled board deck, standalone Lab 1 presentation deck (`.pptx`/`.pdf`).
* **Ingest**: Added the humanize skill for repo-wide use; dropped the no-PDFs rule (presentation PDFs allowed) — later superseded by the fuller PDF-retention policy above.

## 2026-09-17

* **Deliverable**: Updated Sweetgreen deliverables with sourced FY2025/2026 filings and vendor data.

## 2026-09-15

* **Ingest**: Converted all course PDFs (`w0`–`w3`) to Markdown, restructured the vault for Obsidian, added `index.md` and `ROBOT.md`.
* **Creation**: Drafted initial Sweetgreen capstone deliverables (backbone-context note, context-and-diagnosis brief), consolidated under `project/`, added Mermaid diagrams.
