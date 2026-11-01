> Source: Raphael Malikian, Multi-Agent Cochrane-Level Review Process (Robust Standard v2) — https://github.com/rtmalikian/multi-agent-cochrane-level-review-process — Licence: Attribution — Non-Commercial (LICENSE.md). Free for non-profit use with acknowledgement; commercial use by licence (rtmalikian@gmail.com).
>
> Use with `EXAMPLE_MULTI_STEP_PROMPT.md`. Send one step at a time. You (the human) are the accountable author.

# STEP 6 — Two fully independent extractions

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
