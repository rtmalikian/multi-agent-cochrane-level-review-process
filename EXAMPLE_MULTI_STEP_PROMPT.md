# Example Multi-Step Prompt — Run a Cochrane-Level Systematic Review With a Multi-Agent LLM Team

**Author:** Raphael Malikian — https://github.com/rtmalikian
**Licence:** Malikian Attribution — Non-Commercial Licence v1.0 (see LICENSE.md). Free for non-profit use **with acknowledgement**. Commercial use: email rtmalikian@gmail.com for licensing.
**What this is:** The exact working pattern behind three published Cochrane-level reviews (see `examples/WORKED_EXAMPLES.md`). It is written so you can paste it, step by step, into an AI agent system that can spawn sub-agents / parallel workers (for example Muse, ChatGPT with agents, Gemini, an open-source agent framework, or a team of separate chat sessions you coordinate by hand).

> **How to use it (read this first)**
>
> 1. Fill in every `[BRACKETED PLACEHOLDER]` in Step 0. Do not skip the denominator definition — most failed reviews fail there.
> 2. Send **one step at a time**. Do not paste all 12 steps at once and ask for a finished review. Each step produces files; check them before you authorise the next step.
> 3. Keep the **independence rules**: screeners, extractors and risk-of-bias assessors must work in **separate sessions / agents that cannot see each other's work** until the merge step. If your tool cannot spawn isolated agents, open separate chats and paste each role its own prompt from the `prompts/` folder.
> 4. **You are the accountable author.** The agents are the team, not the author. You set the question, settle the items they flag for you, and sign off every number. Never publish a number you have not traced to its source file.
> 5. At every step, the agent must **stop and report** rather than invent, guess or silently work around a block. A blocked source is logged as blocked. A missing full text is logged as not retrieved. That honesty is what makes the output credible.

---

## STEP 0 — The master instruction (paste this first, with your topic filled in)

```text
You are coordinating a Cochrane-level systematic review and meta-analysis for me.
I am the accountable human author. You will organise a team of LLM agents in place
of a human research team. Follow the Robust Standard v2 in this repository exactly.

MY TOPIC
- Review question: [STATE THE QUESTION IN ONE SENTENCE]
- Population / setting: [WHO / WHERE]
- Intervention / exposure: [WHAT WAS DONE / APPLIED]
- Comparator: [WHAT IT IS COMPARED WITH, OR "none — single-arm proportions"]
- Primary outcome: [NAME IT, with its DENOMINATOR, e.g. "proportion of summaries
  with at least 1 clinically significant error, denominator = summaries assessed"]
- Secondary outcomes: [LIST, EACH WITH ITS DENOMINATOR]
- Eligible study designs: [LIST]
- Date range / languages: [e.g. 2022-2026, no language limit at search]
- Summary types / subtypes for pre-specified subgroups: [LIST, OR "none"]
- Databases I can actually access: [LIST ONLY SOURCES YOU CAN REALLY RUN.
  List licensed databases without access separately as "not run".]

NON-NEGOTIABLE RULES — repeat these to every agent you spawn
1. Protocol first. No screening before I approve a dated written protocol.
2. No invented number, count, date or citation. Ever.
3. A source not run is NEVER reported as searched. Blocked sources are retried
   on two separate occasions, by a second route where one exists, then logged
   as blocked with the error.
4. Dual independent work: two screeners, two extractors, two risk-of-bias
   assessors, each working apart, none seeing the other's calls until merge.
5. Real adjudication by reading. A coded rule may triage but may NEVER finally
   exclude a record a screener included, and may NEVER settle a disagreement.
6. Statistics checked two ways: name the model in the protocol, report tau-squared,
   I-squared and prediction intervals, and hand-check at least one pool in full.
7. GRADE every critical outcome, with downgrade reasons named per outcome.
8. Figures are inspected, not assumed: every forest plot carries a summary
   diamond, and every figure/table page is rendered and visually inspected
   before shipping. A build that fails inspection does not ship.
9. Log everything: search counts, agreement and kappa, disagreement counts and
   types, adjudication outcomes, extraction discrepancy rate per field,
   risk-of-bias disagreements, and every correction after first build.
10. This is a Cochrane-LEVEL review. It is NOT a Cochrane review and must never
    be described as one. No PROSPERO number may be claimed unless one was
    actually issued before analysis.
11. No clinical or medication recommendation. Evidence synthesis only.
12. Stop and report at the end of each step. Do not start the next step until
    I say "proceed".

Begin with Step 1 only: the protocol.
```

## STEP 1 — Protocol

```text
STEP 1 — PROTOCOL. Draft a dated protocol following the Cochrane Handbook (v6.5)
structure: background, objectives, eligibility criteria (designs, population,
exposure, comparators, outcomes with definitions AND denominators fixed in
advance), search methods, selection methods, extraction plan, risk-of-bias tool
(name it; if you must adapt a tool, say "adapted" and specify the adaptation
BEFORE extraction), synthesis plan (model, transformation, estimator,
Hartung-Knapp handling, subgroup and sensitivity analyses — all pre-specified,
with interaction tests for subgroup claims), and GRADE plan with expected
downgrade pressure points named before results are known.
Also prepare: (a) a PROSPERO-ready form, field by field; (b) a section titled
"LLM team in place of a human research team" listing every role, its independence
rules, and how disagreements will be logged (RAISE 2025 style disclosure);
(c) a competitor check — search PROSPERO and the Cochrane Library for an existing
or registered review on this exact question, and state in writing how this
review differs in scope, or stop and tell me if it does not differ.
Save: protocol.md, prospero-form.md, llm-team-log.md (started).
Then STOP and show me the protocol for approval.
```

## STEP 2 — Search (full retrieval, nothing partial counted as searched)

```text
STEP 2 — SEARCH. Act as the information specialist. For every accessible source:
write the exact string, run it in FULL, and log string-as-run, date, hit count
and retrieved count in search-log.md and search-results.csv.
Rules: a test page, a capped retrieval or a first-N relevance sample NEVER counts
as a searched source — log it as partial and tell me. Retry blocked sources on
two separate occasions / by a second route before logging them blocked.
List licensed databases with no access as "not run, string ready" — never imply
they were searched. Deduplicate by DOI, then normalised title, then a near-duplicate
pass, and report each count. Then do systematic citation chasing on all included
studies and competing reviews found later (its yield counts in the PRISMA flow).
Save: search-log.md, search-results.csv, retrieval-log.csv.
Then STOP and report counts per source, blocked sources, and partial sources.
```

## STEP 3 — Dual independent screening

```text
STEP 3 — SCREENING. Spawn Screener A and Screener B as ISOLATED agents.
Give each the eligibility rules from the approved protocol and a DIFFERENT written
decision procedure. Neither may see the other's calls, reasons or files.
Each screener returns, for every deduplicated record: include / exclude / maybe,
plus a one-line reason, in screening-A.csv and screening-B.csv.
A third agent (who did no screening) then merges the two files BY CODE, computes
the agreement rate and Cohen's kappa (3-category and binary), and lists every
disagreement. Report the kappa WITH an explanation of what drove it.
Save: screening-A.csv, screening-B.csv, screening-merged.csv.
Then STOP and report: records screened, agreement, kappa, disagreement count by type.
```

## STEP 4 — Adjudication by reading (never by rule)

```text
STEP 4 — ADJUDICATION. Spawn an Adjudicator agent who did no screening.
For EVERY disagreement, and every include/maybe record any triage would drop, the
adjudicator re-reads the full title and abstract, both screeners' reasons, and the
eligibility rules, then records its own call WITH a reason in adjudication.csv.
A coded rule may sort or prioritise the list. It may not settle anything.
Records the adjudicator cannot settle are listed by ID in flagged-for-author.md
for MY decision — do not decide them for me.
Then run a strict full-abstract pass over everything that survived, applying the
eligibility rules exactly as written, and list full texts to retrieve.
Save: adjudication.csv, flagged-for-author.md, full-text-list.md, prisma-flow.md (updated).
Then STOP and list what you flagged for me.
```

## STEP 5 — Full-text retrieval and full-text screening

```text
STEP 5 — FULL TEXTS. Retrieve each report through lawful open routes only
(PubMed Central, Europe PMC, publisher open access, Unpaywall, preprint servers).
No paywall workarounds. Log every report as retrieved or not retrieved, with the
route tried, in retrieval-log.csv. Screen retrieved full texts against the
eligibility rules in duplicate; give ONE exclusion reason per excluded report,
in the protocol's order of reasons. Update the PRISMA flow so the arithmetic
reconciles exactly at every stage — if it does not reconcile, stop and find out why.
Save: fulltext-screening.csv, retrieval-log.csv, prisma-flow.md.
Then STOP and report: sought, retrieved, not retrieved, assessed, excluded (by reason), included.
```

## STEP 6 — Two fully independent extractions

```text
STEP 6 — EXTRACTION, TWICE. First pilot the extraction form on 2 studies and show
me the piloted form. Then spawn Extractor A and Extractor B as ISOLATED agents.
Each extracts EVERY included study in full, from its full text, onto the piloted
form — every field, including denominators, numerators, model/version, and the
exact wording behind any graded outcome (e.g. "clinically significant").
Neither sees the other's sheet. Outputs: extraction-A.csv, extraction-B.csv.
A merge agent then compares the two sheets FIELD BY FIELD BY CODE and reports the
discrepancy count and rate per field. EVERY discrepancy is settled by a third
reading of the source for that field — never by picking a pass. Settlements are
logged with reasons. Then run a verification pass on top: hand-check totals and
check named arms against the papers.
Save: extraction-form.md, extraction-A.csv, extraction-B.csv, extraction-settled.csv,
extraction-discrepancies.md (with the discrepancy rate per field).
Then STOP and report the discrepancy rate and every substantive discrepancy.
```

## STEP 7 — Risk of bias, in duplicate, adjudicated by reading

```text
STEP 7 — RISK OF BIAS. Spawn two assessor agents, isolated from each other.
Each assesses every included study (per outcome where the data allow) with the
tool named in the protocol — RoB 2 / ROBINS-I / QUADAS-2 where they fit, or the
pre-specified adapted tool, named as adapted at every mention.
Each judgement needs a supporting quote or fact from the paper, not just a label.
An adjudicator agent then settles EVERY disagreement by re-reading the paper and
both rationales. Never settle by a mechanical rule such as "take the more
cautious judgement".
Save: rob-A.csv, rob-B.csv, rob-settled.csv, rob-summary.md (disagreement counts included).
Then STOP and report disagreements by domain and how each type was settled.
```

## STEP 8 — Statistics, checked two ways

```text
STEP 8 — ANALYSIS. Act as the statistician, following the synthesis plan in the
approved protocol exactly. Judge poolability per outcome against the FIXED outcome
definitions: studies that do not map onto a definition are narrative, never forced
into a pool. For each pool report: model, transformation, estimator, tau-squared,
I-squared, 95% CI and prediction interval. Use Hartung-Knapp where pre-specified,
or justify its omission in the methods. Subgroup claims rest on interaction tests.
HAND-CHECK at least one pool in full by a second route (different code path or
manual calculation) and hand-check the crude totals of every pool against the
settled extraction sheet. If the primary outcome cannot be pooled because too few
studies report it on the pre-specified denominator, SAY SO as a finding — do not
quietly change the outcome, the denominator or the inclusion criteria to rescue a
pool. Any post-hoc pool must be created by a dated, logged amendment and labelled
post hoc everywhere it appears.
Publish the analysis code and the dataset so a reader can rebuild every figure.
Save: analysis code, results-summary.csv, forest plots (Step 9), analysis-results.md.
Then STOP and show me every pooled result next to the studies and counts behind it.
```

## STEP 9 — Figures and visual QA (a shipping gate)

```text
STEP 9 — FIGURES + VISUAL QA. Build every forest plot with the pooled estimate drawn
as a SUMMARY DIAMOND (centre = pooled value, tips = 95% CI) and the prediction
interval shown where computed. Size every figure to fit the printed page BEFORE
building the PDF: no figure taller than the usable page height; split arm-level
plots into panels. After building the PDF, RENDER AND VISUALLY INSPECT every
figure and table page: diamond visible, axis labels present, nothing clipped,
no heading orphaned on a blank page, every planned figure actually present.
Log the inspection page by page in visual-qa-log.md. If any page fails, fix it
and inspect again. A build that fails inspection does not ship.
Save: figures, visual-qa-log.md. Then STOP and report the inspection result.
```

## STEP 10 — GRADE and Summary of Findings

```text
STEP 10 — GRADE. Act as the GRADE assessor. Rate certainty per critical outcome,
starting from the level the protocol specifies for this evidence type, and name
every downgrade reason per outcome (risk of bias, inconsistency, indirectness,
imprecision, publication bias) — or state explicitly why there was no downgrade.
Build the Summary of Findings table and place it BEFORE the Background in the
manuscript, as Cochrane manuscripts do. Expected pressure points named in the
protocol must each be addressed: confirmed, or explained.
Save: summary-of-findings.md, grade-assessment.md. Then STOP.
```

## STEP 11 — Manuscript, claims traceability and the de-AI pass

```text
STEP 11 — MANUSCRIPT. Write the manuscript in Cochrane order, reported against
PRISMA 2020 and PRISMA-S: structured abstract (under 1,000 words), plain-language
summary, Summary of Findings, Background, Objectives, Methods (including the
LLM-team section and every difference between protocol and review, declared),
Results, Discussion, and Authors' Conclusions split into implications for practice
and for research. RULES: every discussion claim sits in the same paragraph as the
number it rests on; no clinical or medication recommendation; declarations state
funding, conflicts, and a factual AI-assistance note (RAISE 2025 wording);
registration is stated plainly — a number only if one was actually issued.
Then build a CLAIMS VERIFICATION LOG: trace every pooled number, count and
percentage in the manuscript back to its row in results-summary.csv and its source
in the settled extraction sheet. Any number that does not trace does not ship.
Then run a plain-writing pass: short sentences, no hype words, no inflated claims,
numbers stated the same way everywhere.
Save: manuscript.md, manuscript.pdf, claims-verification-log.md.
Then STOP and show me the abstract, the Summary of Findings, and the claims log.
```

## STEP 12 — Dissemination (free routes only, everything verified live)

```text
STEP 12 — DISSEMINATION, ONLY AFTER I APPROVE THE MANUSCRIPT.
Prepare: (a) a public GitHub repository containing the manuscript, protocol,
search log and strings, screening files, settled extraction data, risk-of-bias
judgements, analysis code, figures, team log and a README that starts with how
to read and download the paper; (b) a Zenodo deposit (preprint, CC BY 4.0) and,
once the DOI exists, wire the DOI back into the README, citation file and any
reading page — never type a DOI from memory, paste it from the record page;
(c) a plain-language reading page (GitHub Pages) with the headline findings and a
PDF download; (d) a journal package for ONE no-fee journal whose scope fits, using
that journal's own template and author instructions, checked field by field;
(e) author-contact drafts if the review identifies studies whose authors hold
data the review needs (e.g. per-denominator counts) — drafts only, I send them.
VERIFY EVERYTHING LIVE after creation: open the repo, the DOI and the reading
page and read them back before telling me they are live.
Save: github-package/, zenodo-package/, journal-package/, launch-drafts.md.
Then STOP and report, link by link, what you verified.
```

---

## The one-paragraph short version (for a single-agent tool with no sub-agents)

```text
Run a Cochrane-level systematic review on [QUESTION] with [PRIMARY OUTCOME +
DENOMINATOR] fixed in advance. Work in 12 logged steps: protocol (with PROSPERO-ready
form and competitor check) → full search with every source logged as searched /
partial / blocked / not run → dual independent screening in two separate sessions
with kappa reported → adjudication by re-reading, never by rule → lawful full-text
retrieval with exact PRISMA arithmetic → two fully independent extractions, merged
field by field, every discrepancy settled by a third reading → duplicate risk-of-bias
with adjudication by reading → random-effects analysis exactly as pre-specified,
hand-checked by a second route, with any unpoolable primary outcome reported as a
finding, not rescued → forest plots with summary diamonds, every page visually
inspected → GRADE per outcome with named downgrade reasons → Cochrane-order
manuscript with a claims-verification log tracing every number to the data →
free dissemination (GitHub + Zenodo) verified live. Never invent a number, count,
date or citation. Stop after each step and show me the files before proceeding.
I am the accountable author.
```

## What good looks like — red flags that mean STOP

| Signal | What it means | What to do |
|---|---|---|
| A pooled number with no row in `results-summary.csv` | Untraced claim | Remove it or trace it before shipping |
| Kappa reported with no explanation | Screening may be rule-based theatre | Require the disagreement breakdown by type |
| Extraction discrepancy rate of 0% | The two passes were not independent | Re-run one pass in a genuinely isolated session |
| A forest plot with no diamond | The build step was skipped | Rebuild and re-inspect the page |
| "Databases searched" listing a source that was blocked | Honesty breach | Correct the log and the manuscript, disclose the correction |
| Primary outcome quietly redefined to get a pool | Outcome switching | Restore the protocol definition; log any amendment as post hoc |
| A PROSPERO number with no issued record | False registration claim | Remove it; state plainly that none was issued |

## Attribution

If you use this prompt or the process behind it, you must acknowledge:
**Raphael Malikian — Multi-Agent Cochrane-Level Review Process (Robust Standard v2) — https://github.com/rtmalikian/multi-agent-cochrane-level-review-process**
Non-profit use with acknowledgement is free under LICENSE.md. Commercial use requires a licence: **rtmalikian@gmail.com**.
