# Working notes for this vault

This is an Obsidian vault, not a codebase. It's a NYU Tandon course, IE-GY 9113B: Systems Integration, From ERP to Agentic AI, converted from Brightspace PDFs into Markdown so it's easy to track in git and browse on GitHub. Start at [[index]] for navigation.

## Structure

Three top-level layers — schema at root, immutable sources under `raw/`, LLM-maintained content under `wiki/`. See "The vault as an LLM wiki" below for the reasoning; this section is just the map.

**Schema (root):**
- `index.md`: vault home and map of content, the main navigation page in Obsidian.
- `ROBOT.md`: this file. Conventions and workflow.
- `log.md`: append-only chronological record of vault activity, newest entries at the bottom.

**`raw/` — read-only inputs. Never rewrite their substance, only fix a conversion artifact if you spot one.** Everything lives under the single child `raw/data/`, split by format first, then by topic, so it's obvious at a glance which format you're browsing and easy to find a file's counterpart in the other format (same topic folder, same basename):
- `raw/data/pdf/<topic>/`: original, non-Markdown files — PDFs, plus the two `.docx`/`.pptx` templates that have no Markdown counterpart by design (they're the professor's editable originals, nothing to convert them against).
- `raw/data/markdown/<topic>/`: the `markitdown` conversion of every PDF that has one, same basename as its PDF twin in the sibling tree.
- The topic folders mirror each other exactly across both trees: `syllabus-and-rubrics/`, `final-project-info/`, `course-weeks/w0/` … `w4/`, `sweetgreen-lab1-evidence/` (the team's graded final annotated map — PDF *and* a Markdown transcription, since it's a diagram-heavy document worth having in both forms). One exception: `final-project-info/` also holds `Final Project Teams.pdf` and the two Office templates, PDF-and-office side only — no Markdown pair, by design.
- `raw/data/transcripts/`: Markdown-only, no PDF source, genuinely verbatim — `announcements.md` (the professor's Brightspace announcements, newest first). Course-wide, not project-specific.
- `raw/data/datasets/`: externally generated binaries with no Markdown/PDF duality — the Gemini-generated Lab 1 sandbox (`.xlsx`). The data *is* the artifact; there's nothing to transcribe.

**To find a source's Markdown reading vs. its original:** same topic folder name, same basename, under `raw/data/markdown/` or `raw/data/pdf/` respectively. E.g. the Week 1 study note is `raw/data/markdown/course-weeks/w1/W01_IntegrationBackbone_StudyNote_PB14.md` and `raw/data/pdf/course-weeks/w1/W01_IntegrationBackbone_StudyNote_PB14.pdf`.

**`wiki/` — the layer you actively write, maintain, and cross-link. Should get richer with every week, not just longer.**
- `wiki/concepts/`: one page per recurring course term (control point, decision point, leverage gap, RPA candidate criteria, the three threads, the four archetypes, …). The single place a term is actually defined; everything else links to it instead of re-defining it inline.
- `wiki/entities/`: one page per company/organization that recurs across sources (Sweetgreen, and the case-study companies from the readings — Thermo Fisher Scientific, Bailey Hydraulics, …).
- `wiki/comparisons/`: side-by-side pages for recurring multi-way distinctions (e.g. RPA vs. traditional automation vs. AI).
- `wiki/project/`: the team's Sweetgreen capstone work, split by the week each deliverable belongs to — `week1/`, `week2/`, `week3/`, `week4/`, … — plus `wiki/project/shared/` for anything that isn't one week's work: the living board deck (`Board-Presentation-Sweetgreen.pptx`, filled in slide by slide as each week produces its evidence), the public research log (`shared/research/`), standalone diagram source files (`shared/diagrams/`, embedded into write-up notes with `![[...]]` rather than pasted inline so a diagram can be edited in one place), and cross-week provenance notes. A week folder holds that week's own write-up(s) plus its standalone share-out deck, if it has one (`.pptx` + `.pdf` export — see the PDF rule below). Wikilinks don't need the folder prefix (Obsidian resolves by filename vault-wide), so moving a deliverable between weeks later doesn't break anything that links to it.

## Capstone context

- **Company:** [[Sweetgreen]], a fast-casual restaurant chain. Confirmed in Week 2. An earlier Week 1 practice exercise used AWS as a throwaway drill, not the real company. See [[Sweetgreen-Breakout-Provenance]] for that history.
- **Process:** Order-to-Cash, meaning customer order, payment, kitchen, prep, verify and pack, pickup or delivery, then transaction complete.
- **Core thesis so far:** the backbone's weakest point is the handoff between digital ordering channels and kitchen execution (traditional line vs. Infinite Kitchen). Order accuracy and availability information don't reliably survive that handoff. This idea runs through everything in `wiki/project/`.
- Deliverables build on each other in order: backbone-context note, then context-and-diagnosis brief, then Lab 1 pre-work and process map. These feed Board Memo §2/§3 and storyboard slides S1/S3/S4/S5. Don't re-derive the diagnosis from scratch each time. Extend or refine the existing chain, and update everything together if the underlying diagnosis changes.

## Formatting conventions

Apply these to any note you add or edit.

- **Frontmatter:** every note gets YAML frontmatter with `title`, `tags`, and `type` (required for OKF conformance — see "Open Knowledge Format conformance" below). Recommended where it applies: `description` (one sentence) and `sources` (provenance back to `raw/`).
- **Headings:** one `#` document title, `##` for major sections, `###` for subsections. Strip any orphaned page-number or footer artifacts left over from PDF conversion; don't preserve them.
- **Tables:** always clean GFM tables (`| col |` with a `|---|` separator row). If the source text is too mangled to confidently reconstruct as a table, use a bullet or definition list instead, rather than leaving broken pipe fragments.
- **Foldable callouts:** wrap dense reference material, worked examples, long case narratives, or anything a reader would consult rather than read straight through, in a collapsed Obsidian callout:
  ```
  > [!example]- Section Title
  > content, one "> " per line including blank lines
  ```
  Use `[!example]-`, `[!info]-`, `[!note]-`, or `[!quote]-` as fits. The trailing `-` collapses it by default (`+` would default-expand). Never fold core teaching content, due dates, or homework instructions, only supplementary material.
- **Wikilinks:** use bare `[[Note Name]]` or `[[Note Name|display text]]`. Obsidian resolves by filename across the whole vault regardless of folder, so links don't need full paths and survive files being moved between folders.
- **Diagrams:** Mermaid renders natively in Obsidian and on GitHub, but its `subgraph` layout reorders unpredictably around back-edges (a rework loop, an escalation loop) and produces an unreadable tangle — verify any swimlane-style Mermaid diagram by rendering it directly (`npx @mermaid-js/mermaid-cli`) before trusting it, and prefer a flat flowchart with color-coded nodes over `subgraph` lanes when the process has cycles. For anything meant to be read at a glance — board decks, scan write-ups, a five-minute recap — lead with a hand-built swimlane image matching this course's own worked-example style (the Citi Bike "annotated process map" in the Week 3 lecture notes: ★ control point, ◆ decision point, red dashed rejection/rework path, ⚡ value-leak annotation), not a Mermaid diagram; keep the full step-by-step BPMN as a Mermaid fallback, collapsed underneath, not the lead visual. Mark control points and decision points explicitly; see [[Control Point]] and [[Decision Point]]. [[Order-and-Payment-Process-Map]] is the worked example (hand-built swimlane PNG leads, Mermaid BPMN folded below it).
- **Course study notes and lecture slides get converted to Markdown** (`markitdown`) *and* the original PDF is kept under `raw/data/pdf/course-weeks/`, same topic folder and basename as its Markdown twin in `raw/data/markdown/course-weeks/`. Reversed from an earlier rule that deleted the PDF after conversion: text conversion is lossy for anything visually laid out (a slide's diagram, a color-coded worked example, a callout box), and that's exactly the content most worth having later — the Week 3 lecture notes' "annotated process map" slide, the one [[Order-and-Payment-Swimlane]] is modeled on, is a case in point. The Markdown is what gets read and linked day to day; the PDF is the fallback when the Markdown alone doesn't answer the question, and it's what you read directly when a diagram or layout matters. This applies to any PDF: a received deliverable, a generated export, a graded artifact — keep it in `raw/`, fold its substance into a `wiki/` page too if it feeds a deliverable, but don't delete it. **Presentation decks the LLM authors are a different case from received PDFs, and get their own rule:** the `.pptx` is the editable source, kept always. A `.pdf` export is added alongside it only for decks meant to be sent to someone outside the vault as-is — a teammate, the professor — where a static, universally-openable file is the actual point (`Lab1-Presentation-Sweetgreen`, `Week4-Presentation-Sweetgreen`). Skip the `.pdf` for a deck that's purely a living internal artifact edited slide by slide and never sent out whole (`Board-Presentation-Sweetgreen` stays `.pptx`-only until it's finished and actually gets sent somewhere). This isn't the "keep the original, it's lossy to convert" logic above — a PDF export of an already-final deck loses nothing; it's a distribution-format call, made per deck.

## Writing style

Write plainly. Avoid em dashes; use commas, periods, or parentheses instead. Avoid stacking clauses into one long sentence when two short ones read better. Skip AI-tell phrasing like "it's not just X, it's Y" or "this isn't merely A, it's B." Say the thing directly.

## The vault as an LLM wiki

This vault is deliberately run as a compounding wiki, not a pile of retrieved documents, following the pattern popularized by Andrej Karpathy (https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f). Three layers, now physically separated on disk, not just conceptually:

- **Raw sources — `raw/`.** Immutable inputs: converted-but-unaltered course readings and professor reference documents, split into `raw/data/pdf/` (originals) and `raw/data/markdown/` (conversions), each mirrored by topic folder (`course-weeks/`, `syllabus-and-rubrics/`, `final-project-info/`, `sweetgreen-lab1-evidence/`), verbatim communications (`raw/data/transcripts/`) and externally generated binaries the LLM only reads (`raw/data/datasets/`). Never rewrite the substance of anything here — correct a conversion artifact if you spot one, that's it.
- **The wiki — `wiki/`.** Everything actively written, maintained, and cross-linked: `wiki/concepts/` (recurring terms), `wiki/entities/` (recurring companies/organizations), `wiki/comparisons/` (side-by-side distinctions), `wiki/project/` (the Sweetgreen capstone deliverables, diagrams, research). This layer should get richer and more cross-linked with every week, not just longer.
- **The schema — root.** This file (`ROBOT.md`), `index.md`, and `log.md`. The conventions doc, the catalog, and the history. Update `ROBOT.md` whenever a new convention gets established, not just when asked to.

**Ingest** (adding a new week's material or a new deliverable): drop/convert the raw material into the right `raw/` subfolder first if it's a new source. Then draft the wiki content: check whether any term in it is already a `wiki/concepts/` page, any company already a `wiki/entities/` page — link to it (`[[Control Point]]`) instead of re-explaining it inline. If a term or entity recurs across 2+ sources and has no page yet, create one. A good answer worth keeping (a comparison, a synthesis) becomes a `wiki/comparisons/` page, not just prose buried in one deliverable. Update `index.md`'s relevant table. Append one line to `log.md`.

**Query** (answering a question about the course or the capstone): read `index.md` first to find the relevant pages, then `wiki/concepts/` and `wiki/entities/` for any term or company involved, then drill into the specific `wiki/project/` or `raw/data/markdown/course-weeks/` notes. Don't re-derive a diagnosis or a definition that already exists somewhere in the vault — extend or cite it (this is already the rule for capstone deliverables under "Capstone context" above; it now applies vault-wide). If the answer is worth keeping, file it as a new page in the appropriate `wiki/` subfolder rather than leaving it only in chat.

**Lint** (periodically, or when asked to check the vault's health): look for orphan pages in `wiki/` (nothing links to them), terms or companies mentioned in 2+ places but still explained inline instead of linked to a page, and claims in an older `wiki/project/` note that a newer one has superseded without a cross-reference back. Fix what you find or flag it in `log.md` rather than silently leaving it.

**`log.md` format.** OKF-style: date-grouped, newest date first, `## YYYY-MM-DD` headings with `* **Category**: description` bullets underneath. See "Open Knowledge Format conformance" below.

**A separate, unrelated tool exists for this pattern too:** the `wiki@llm-wiki` Claude Code plugin (github.com/nvk/llm-wiki) implements a heavier version of the same idea with its own global store at `~/wiki/topics/<name>/`. It's installed (user scope) but not wired into this vault — this vault's `raw/`/`wiki/` split is maintained by hand, following the conventions on this page, not by that plugin's `/wiki` commands.

## Open Knowledge Format conformance

This vault follows Google's [Open Knowledge Format (OKF) v0.2](https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md), a plain-Markdown-plus-YAML-frontmatter standard for portable, agent-readable knowledge bundles. `index.md` declares `okf_version: "0.2"` in its frontmatter.

**What every `wiki/` and `raw/` Markdown file needs (the one required field):** `type` — a short string naming the kind of thing the file is. This vault's types so far: `concept`, `entity`, `comparison`, `deliverable`, `diagram`, `study-note`, `reference` (syllabus/rubrics/templates), `research-log`, `scratch-notes`, `announcement-log`. Add a new type rather than force-fitting an odd page into an existing one.

**Recommended, used where it earns its keep, not everywhere:**
- `description` — one sentence, for a future index/search pass.
- `sources` — provenance back to `raw/`, OKF's per-claim attribution pattern:
  ```yaml
  sources:
    - id: annotated-map-pdf
      resource: raw/data/pdf/sweetgreen-lab1-evidence/Sweetgreen-Lab1-Final-Annotated-Map.pdf
      title: Team's final annotated process map (graded, 24 Sep 2026)
  ```
  then cite it inline with a footnote keyed to the `id`: `The $44 figure comes from the graded map.[^annotated-map-pdf]`. Use this on `wiki/` pages that are substantively derived from one or two specific `raw/` files (a deliverable built from a PDF, a diagram modeled on a slide) — not required on every page.
- `generated` / `verified` — trust provenance (`generated: {by: claude-code/sonnet-5, at: <timestamp>}`, `verified: {by: human:<netid>, at: <timestamp>}`). Add `verified` once the professor or a teammate has actually reviewed a deliverable, not before.

**Not required, don't force it:** OKF's `Attested Computation` type (for verifiable executable computation) doesn't apply to this vault — nothing here runs live queries. Skip it.

**Conformance is additive, not a rewrite mandate.** OKF explicitly tolerates missing optional fields, unknown `type` values, and broken links — a bundle is conformant once every non-reserved `.md` file has a `type`. Add `type` to a file whenever you touch it; don't do a separate sweep just to backfill files you have no other reason to open.

## Open items

See the checklist in [[index]] for what's drafted vs. still a real-world action (emailing the professor, setting up tool accounts, etc.). Those can't be done from inside the vault.
