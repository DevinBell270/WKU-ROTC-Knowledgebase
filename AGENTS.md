# WKU ROTC Knowledgebase — Agent Schema

This repository is an [LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) for the Western Kentucky University Department of Military Science and Leadership (Hilltopper Army ROTC). It is the **compiled** single source of truth for AI agents. Humans curate sources and ask questions. Agents write and maintain the wiki.

Read this file at the start of every session. Then read `wiki/index.md` before answering questions or ingesting sources.

## Architecture

Three layers. Do not mix them.

| Layer | Path | Who writes | Rule |
| --- | --- | --- | --- |
| Raw sources | `raw/` | humans (agents may *add* new captures, never rewrite existing ones) | Immutable snapshots. Read-only after ingest. |
| Wiki | `wiki/` | agents | Compiled, interlinked markdown. Agents own this layer. |
| Schema | `AGENTS.md` | humans + agents, co-evolved | Structure, authority, workflows. |

Obsidian-style `[[wikilinks]]` use the **filename stem** (unique across `wiki/`). Example: `[[ltc-david-schnaak]]`.

## Authority ranking

When sources disagree, do not blend them into one unattributed fact. Record both claims on the relevant pages and on `[[source-conflicts]]`. Apply this order:

1. **Human corrections in `raw/corrections/`** — program-staff overrides. Highest authority for *current operational facts* (who the PMS is, office practices, local policy).
2. **Dated official WKU communications** — WKU News, College of Education and Behavioral Sciences announcements, commencement programs. High authority for people, events, and recent facts.
3. **Undergraduate Catalog (current year in `raw/catalog-*/`)** — canonical for *degree requirements, course numbers, official catalog titles and hours, admission language as published*. Academic advising answers should lead with the catalog, then note department-site differences.
4. **Department website (`raw/wku-rotc/`)** — canonical for recruiting copy, contact routing, scholarships as marketed, Living Learning Community, nursing pathway, history narrative. Not canonical when it conflicts with the catalog on course titles, hours, or program requirements.
5. **Cadet handbook and other department PDFs** — useful for battalion practice; treat as potentially stale until a human confirms.
6. **Third-party news** — corroboration only (e.g. *College Heights Herald*).

Never silently prefer a stale catalog person/title over a human correction.

### Current standing overrides

- **PMS / department chair:** Lieutenant Colonel David Schnaak. The 2026–2027 catalog still lists LTC Anthony Struzik. Treat Struzik as superseded. See `[[ltc-david-schnaak]]` and `[[source-conflicts]]`.

## Query workflow

1. Read `wiki/index.md`.
2. Open the 2–8 most relevant pages. Follow `[[wikilinks]]`.
3. If a page is marked `contested: true` or `confidence: low`, say so in the answer.
4. Cite wiki pages and, for contested or high-stakes claims (commissioning eligibility, scholarships, contracts), also cite the raw source.
5. Do not answer from training data when the wiki covers the topic.
6. Valuable answers (comparisons, decision trees, advising checklists) get filed back under `wiki/queries/` and linked from `wiki/index.md`.

If the wiki does not contain the answer, say so, then optionally search official WKU/catalog pages, capture them into `raw/`, and ingest.

## Ingest workflow

When a new source is added (or you are told to ingest):

1. Capture an immutable snapshot under `raw/` with URL, capture date, and title. Do not edit a file that already exists in `raw/` except to add a *new* sibling file.
2. Write or update a source summary in `wiki/sources/`.
3. Update every affected entity, concept, program, and course page. One source often touches many pages.
4. If the source contradicts existing wiki claims, update `[[source-conflicts]]` and set `contested: true` on the affected pages. Do not delete the old claim; mark it superseded and date it.
5. Update `wiki/index.md` (one-line summary per page).
6. Append `wiki/log.md` using the log format below.
7. Bump `updated:` in YAML frontmatter on every page you touch.

Prefer ingesting one source (or one tightly related bundle) per pass so conflicts stay visible.

## Lint workflow

When asked to lint, check:

- Contradictions across pages vs `[[source-conflicts]]`
- Stale catalog people/titles vs `raw/corrections/`
- Orphan pages (no inbound `[[wikilinks]]`)
- Concepts mentioned in two or more pages that lack their own page
- Missing sources for claims that affect commissioning, money, or contracts
- Frontmatter completeness
- `wiki/index.md` coverage

File findings as a new `wiki/log.md` entry. Fix mechanical issues in the same pass. Leave judgment calls (which source wins) listed for the human.

## Page conventions

### Filenames

Lowercase kebab-case. Unique across `wiki/`. No spaces.

### Frontmatter

```yaml
---
title: Human-readable title
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: overview | entity | concept | program | course | source-summary | analysis | query | history
tags: []
sources: []
confidence: high | medium | low
contested: false
canonical_for: ""
---
```

- `sources` lists paths under `raw/`.
- `canonical_for` states what this page is allowed to be treated as truth *for* (e.g. "current PMS identity", "BS 733 catalog requirements").
- `contested: true` if live sources disagree.
- Keep pages short. One entity, concept, or program per page. Split rather than grow past ~200 lines.

### Body

Lead with the current accepted fact. Then supporting detail. Then "Source notes" for conflicts, gaps, and superseded claims. Use `[[wikilinks]]` on first mention of another wiki page.

Do not copy marketing filler. Do not invent course titles, hours, phone numbers, or eligibility rules.

## Directory map

```
raw/                      immutable captures
  corrections/            human overrides (highest operational authority)
  catalog-YYYY-YYYY/      undergraduate catalog snapshots
  wku-rotc/               department website snapshots
  news/                   WKU News and other dated official/third-party
wiki/
  index.md                catalog of every wiki page
  log.md                  append-only activity log
  overview.md             synthesis of the program
  sources/                one summary per ingested source
  entities/               people, orgs, places
  programs/               degree programs
  concepts/               ROTC constructs (courses-as-system, scholarships, SMP, …)
  courses/                MIL catalog
  analyses/               conflicts, comparisons
  history/                program history
  queries/                filed answers worth keeping
```

## Log format

Append-only. Each entry starts with:

```
## [YYYY-MM-DD] ingest | Short title
## [YYYY-MM-DD] query | Short title
## [YYYY-MM-DD] lint | Short title
## [YYYY-MM-DD] schema | Short title
```

## Out of scope until sourced

Do not fabricate: current cadet chain of command, full cadre roster, current scholarship deadlines, contract language, medical standards details, or branch assignment results. Capture a source first.

## Tools

At this scale, `wiki/index.md` plus grep is enough. Do not add vector RAG unless the wiki is hundreds of pages and index lookup is failing.
