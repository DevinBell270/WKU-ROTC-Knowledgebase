# Wiki log

Append-only. `grep "^## \[" wiki/log.md | tail -5` for recent activity.

## [2026-09-08] schema | Initial LLM Wiki

Instantiated Karpathy three-layer wiki: `raw/` immutable captures, `wiki/` compiled pages, `AGENTS.md` schema. Cursor rule `.cursor/rules/llm-wiki.mdc` always applies.

## [2026-09-08] ingest | Catalog 2026–2027 + department site + PMS correction

Ingested undergraduate catalog department / BS 733 / minor 420 / MIL courses; department homepage, scholarships, courses, major, minor, contact, benefits, nurse corps, history, veteran, rotc_program; WKU News 2026-05-07 commencement; Herald 2025-11-11 Veterans Day; human correction that LTC David Schnaak is PMS/chair.

Created overview, index, source-conflicts, entities, programs, concepts, mil-catalog, history, and source summaries.

Standing override: catalog listing of LTC Anthony Struzik is stale.

## [2026-09-17] ingest | Housing LLC pages (ROTC + campus-wide)

Captured WKU Housing & Residence Life LLC overview, FAQ, apply excerpt, ROTC LLC page, Zacharias Hall, halls index, and Fall 2025 assignment locations. Compiled [[living-learning-communities]], expanded [[living-learning-community]], added [[zacharias-hall]], [[housing-llc]], and filed query [[rotc-llc]].

Current ROTC LLC building on Housing: Zacharias Hall (subject to change). Fall 2025 page had ROTC in Meredith. Housing “gen ed” heading on MIL 101/102 is unverified vs catalog Colonnade. February 2026 LLC dates on the capture are elapsed.

## [2026-09-17] ingest | Social Scout FB keepers (9/11 stair climb + IMT lab)

Filed Facebook captures `raw/social/2026-09-12-911-stair-climb.md` and `raw/social/2026-09-11-imt-lab.md`. Compiled [[wku-rotc-facebook-social-2026-09]]. Linked Ranger Team 9/11 stadium stair climb and IMT lab on [[hilltopper-battalion]]. No named cadets in these posts. Captions verbatim; Instagram in that window was behind a login wall.

## [2026-09-21] ingest | Social Scout pack (Yates Memorial Run + training)

Filed seven keepers under `raw/social/` (Yates IG carousel, IG wrap, Chaney's IG, FB wrap page-URL-only, CDT Harlow learning the ropes, Almost FTX, Getting the basics down). Compiled [[wku-rotc-social-2026-09-21]] and [[eric-d-yates]] (caption facts only: 1LT Eric D. Yates; KIA September 17, 2010; 16th annual memorial run September 19, 2026). Updated [[hilltopper-battalion]] and [[index]]. Harlow is name-only (`CDT Harlow`); class/major/hometown not in source. Wilkinson and full Harlow cadet-card bios were not ingested.

## [2026-09-24] ingest | WKU News Military Friendly® Top Ten (Mar 2026)

Captured `raw/news/2026-03-27-military-friendly-top-ten.md` (WKU News 2026-03-27, article 12981). Topic is Military Student Services / military-connected students; no ROTC, Military Science, or cadet mention. Compiled [[wku-news-military-friendly-2026]], [[kent-johnson]] (Director of Military Student Services), and a MSS section on [[veterans-and-prior-service]] (Top Ten rankings, named programs, $250/credit-hour wording, Military Connected Students of WKU, wku.edu/veterans). Pointers on [[scholarships]] and [[contact-and-location]] so the $250 rate is not treated as ROTC money. Distinct from ROTC scholarships/stipends. No new [[source-conflicts]] row (Herald Military Times “Best for Vets” is a different ranking).

Judgment call left for the human: **Military Connected Students of WKU** is named on multiple pages but has no standalone page; the article only names it and the advocacy one-liner.

## [2026-09-24] meeting | ROTC staff: highlight Military Friendly® on ROTC site

ROTC program staff, in a meeting on 2026-09-24, asked that the WKU News Military Friendly® rankings be highlighted on the ROTC website as a point of pride: proof that WKU supports military students and families, and that the campus atmosphere for military-connected students compares well with other universities.

Recorded as usage guidance on [[veterans-and-prior-service]] (Recruiting / web copy use) and pointed from [[overview]] and [[brandon-smith]]. No `raw/corrections/` file: AGENTS.md reserves that layer for operational-fact overrides (PMS, office practice, local policy), not meeting requests about web copy. Copy may use only the article’s published ranking and $250-per-credit-hour wording, with the 2026–2027 designation year. Comparative slogans (“best for military students,” “better than other universities”) are not in the source; the “compares well” line is staff intent, not a sourced claim.

## [2026-09-24] ingest | Staff correction: Basic Course is four MIL classes

Filed `raw/corrections/2026-09-24-basic-course-four-classes.md` (same 2026-09-24 meeting, relayed by Devin Bell). No-obligation window is the full two-year [[basic-course]]: MIL 101, MIL 102, MIL 201, MIL 202 (freshman and sophomore years). Recruiting copy that says students get only two classes before they have to commit is wrong. Catalog 2026–2027 already matches (four-semester basic course; no obligation by participating). Obligation still begins with the written [[advanced-course]] contract, or with a [[scholarships|scholarship]] that requires agreeing to commission (a scholarship student may contract earlier). Compiled [[human-correction-basic-course]], [[basic-course]], [[army-rotc]], [[overview]], [[scholarships]], [[brandon-smith]]. No [[source-conflicts]] row: no ingested page said “two classes.”

## [2026-09-24] ingest | Staff correction: JROTC not required to join

Filed `raw/corrections/2026-09-24-jrotc-not-required.md` (same 2026-09-24 meeting, relayed by Devin Bell). Junior ROTC in high school is not required to join Army ROTC at WKU. Compiled [[human-correction-jrotc]], [[basic-course]], [[army-rotc]]. No source says JROTC earns placement credit; published placement remains prior service, Guard, or Reserve only. No [[source-conflicts]] row.

## [2026-09-24] ingest | Staff correction: Brandon Smith Army cell is 270-745-1765

Filed `raw/corrections/2026-09-24-brandon-smith-army-cell.md` (Brandon Smith, verbal, via Devin Bell, 2026-09-24). Government Army cell is **270-745-1765** (text or call). It is not 270-745-6054. **270-745-6054** is the office phone (calls). Compiled [[human-correction-brandon-army-cell]], [[brandon-smith]], [[contact-and-location]], [[simultaneous-membership-program]]. Department SMS-only line 270-721-8539 is unchanged and is not this cell. Other published numbers were not changed.

Open PR #2’s Prezi lists “Text or Call: 270-745-1765” without saying whose line it is. This correction identifies that number as Brandon’s Army cell; the PR #2 phone conflict is resolved once both PRs merge. Other Prezi content was not imported. No [[source-conflicts]] row on this branch (the Prezi conflict is not recorded here).
