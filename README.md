# Multi-Agent Cochrane-Level Review Process — Robust Standard v2

### One accountable human author. A team of AI agents. Cochrane-level rigour, built in the open.

[![Licence: Attribution — Non-Commercial](https://img.shields.io/badge/Licence-Attribution--NonCommercial-orange)](LICENSE.md)
[![Reviews built with this process: 3](https://img.shields.io/badge/Reviews%20built-3-brightgreen)](#worked-examples--three-published-reviews)
[![Hub: Systematic Reviews](https://img.shields.io/badge/Hub-Systematic%20Reviews-blue)](https://rtmalikian.github.io/systematic-reviews/)

**By Raphael Malikian** — independent researcher, healthcare founder and operator who bootstrapped and ran a direct primary care clinic as CEO, now building clinical AI. ORCID [0009-0008-4326-4205](https://orcid.org/0009-0008-4326-4205) · rtmalikian@gmail.com · GitHub [@rtmalikian](https://github.com/rtmalikian) · X [@rtmalikian](https://x.com/rtmalikian)

---

## What this is

A complete, reusable process for producing a **Cochrane-level systematic review and meta-analysis using a multi-agent LLM team in place of a human research team** — with one named human author accountable for every judgement and every number.

It is the process that produced three published reviews in October 2026 (ambient AI scribes; LLM citation fabrication; errors in LLM clinical summaries — links below). This repository open-sources the process itself: the standard, the team structure, the independence rules, the templates, and a **copy-paste multi-step prompt** you can give your own AI agents.

> These are Cochrane-**level** reviews. They are **not** Cochrane reviews and are not submitted to Cochrane (Cochrane requires at least two authors). This process never lets you claim otherwise.

## Start here — the prompt

**👉 [`EXAMPLE_MULTI_STEP_PROMPT.md`](EXAMPLE_MULTI_STEP_PROMPT.md)** — the full 12-step prompt (Step 0 master instruction + one prompt per stage, plus a one-paragraph short version).

Copy Step 0, fill in your topic, question and — most importantly — your **primary outcome with its denominator**, then work through the steps **one at a time**, checking the files each step produces before authorising the next.

Individual stage prompts also live in [`prompts/`](prompts/) if you coordinate separate chat sessions by hand. Blank forms live in [`templates/`](templates/).

## The team

| Role | Does | Independence rule |
|---|---|---|
| Information specialist | Strings, full retrieval, search log | Logs searched / partial / blocked / not run honestly |
| Screener A & Screener B | Title/abstract screening | Separate sessions, different decision procedures, no sight of each other |
| Screening adjudicator | Settles every disagreement | By re-reading — never by a coded rule |
| Extractor A & Extractor B | Full extraction from full texts | Separate sessions; sheets merged field by field by code |
| Settlement reader | Settles extraction discrepancies | By a third reading of the source, per field |
| Risk-of-bias pair + adjudicator | RoB 2 / ROBINS-I / QUADAS-2 or a pre-specified adapted tool | Disagreements settled by reading, never "take the more cautious" |
| Statistician | Random-effects synthesis | Hand-checks one pool in full + crude totals of every pool, by a second route |
| GRADE assessor | Certainty per critical outcome | Downgrade reasons named per outcome |
| Methods editor | Protocol-vs-review differences, reporting checks | PRISMA 2020 + PRISMA-S |
| Visual QA pass | Renders and inspects every figure/table page | A failed build does not ship |
| **Human author** | **Question, flagged items, final sign-off** | **Accountable for every number** |

## The Robust Standard v2 — 12 non-negotiables

1. **Protocol first** — dated, outcomes and denominators fixed in advance, PROSPERO-ready form prepared before screening. No registration number is ever backdated or implied.
2. **Search, full retrieval** — a test page or capped sample never counts as searched. Blocked sources retried twice, by a second route where one exists. Licensed databases with no access are listed as not run, with ready strings.
3. **Dual independent screening** — two passes apart, agreement and Cohen's kappa computed by code and explained.
4. **Real adjudication, never a coded rule as the final word** — a rule may triage; it may not exclude or settle.
5. **Two fully independent extractions** — field-by-field merge, discrepancy rate per field reported, every discrepancy settled by re-reading.
6. **Risk of bias in duplicate, adjudicated by reading** — never by a mechanical rule.
7. **Statistics checked two ways** — model named in advance; tau-squared, I-squared and prediction intervals reported; poolability judged per outcome; unpoolable outcomes reported as findings, not rescued by redefinition.
8. **GRADE per critical outcome** — Summary of Findings table before the Background, downgrade reasons stated.
9. **Manuscript in Cochrane order** — PRISMA 2020 / PRISMA-S, plain-language summary, claims in the same paragraph as their numbers, no clinical recommendation, factual AI-assistance note.
10. **Figures built and inspected** — summary diamonds on every forest plot, page-fit checked, every figure/table page visually inspected and logged before shipping.
11. **Disclosure of the team itself** — roles, prompts version, kappa, disagreement counts, discrepancy rates and every post-build correction reported as results (RAISE 2025 style).
12. **Honesty rules** — no invented number, count, date or citation; a source not run is never reported as searched; paywalled texts logged as not retrieved, no workarounds; incidents kept visible.

The full standard is in [`ROBUST_STANDARD_V2.md`](ROBUST_STANDARD_V2.md).

## Worked examples — three published reviews

| # | Review | Headline finding | Links |
|---|---|---|---|
| 1 | Ambient AI scribes for clinical documentation (74 studies) | Documentation time −18.9%, and 59.8% of audited notes had ≥1 error | [Zenodo 10.5281/zenodo.23565499](https://doi.org/10.5281/zenodo.23565499) · [GitHub](https://github.com/rtmalikian/ambient-ai-scribes-meta-analysis-clinical-documentation-burnout-note-errors) |
| 2 | Fabricated citations in LLM-generated biomedical references (63 studies, 22,461 references) | 19.4% completely fabricated, 37.0% fully accurate; retrieval on 5.8% vs off 31.0% | [Zenodo 10.5281/zenodo.23585717](https://doi.org/10.5281/zenodo.23585717) · [GitHub](https://github.com/rtmalikian/llm-citation-fabrication-meta-analysis-biomedical-references-hallucinated-citations) |
| 3 | Clinically significant errors in LLM clinical summaries (11 studies) | 60.6% of summaries had ≥1 error of any type; only 1/11 studies reported clinically significant errors per summary (21.0%) | [Zenodo 10.5281/zenodo.23847500](https://doi.org/10.5281/zenodo.23847500) · [GitHub](https://github.com/rtmalikian/llm-clinical-summarization-errors-meta-analysis) · [Reading page](https://rtmalikian.github.io/llm-clinical-summarization-errors-meta-analysis/) |

**Hub for all three:** https://rtmalikian.github.io/systematic-reviews/

Full details in [`examples/WORKED_EXAMPLES.md`](examples/WORKED_EXAMPLES.md).

## Repository map

```
EXAMPLE_MULTI_STEP_PROMPT.md   The copy-paste 12-step prompt — start here
ROBUST_STANDARD_V2.md          The full standard (v2, 22 Oct 2026)
prompts/                       One file per stage, for hand-coordinated sessions
templates/                     Protocol, extraction, RoB, team-log, checklist forms
examples/WORKED_EXAMPLES.md    What the three published reviews teach about the process
docs/                          GitHub Pages landing page for this process
CITATION.cff                   Cite this process
LICENSE.md                     Attribution — Non-Commercial licence (read it)
```

## Licence — acknowledgement required, non-profit free, commercial by licence

This process is **free for non-profit, academic, personal and other non-commercial use — with acknowledgement**:

> Malikian R. Multi-Agent Cochrane-Level Review Process (Robust Standard v2). 2026. https://github.com/rtmalikian/multi-agent-cochrane-level-review-process

**Commercial use requires a licence.** If you want to use this process inside a company, in a paid product or service, in paid training, or in consultancy deliverables, email **rtmalikian@gmail.com** first.

Full terms: [`LICENSE.md`](LICENSE.md). Note: the three reviews themselves are CC BY 4.0 — this licence covers the *process*, prompts and templates in this repository.

## How to cite

Malikian R. Multi-Agent Cochrane-Level Review Process (Robust Standard v2): a multi-agent LLM-team method for Cochrane-level systematic reviews and meta-analyses, with an example multi-step prompt. 2026. GitHub: https://github.com/rtmalikian/multi-agent-cochrane-level-review-process

## Corrections and questions

Open an issue. Corrections to the process are versioned and logged, never silently overwritten — that is Rule 12 applied to this repository itself.
