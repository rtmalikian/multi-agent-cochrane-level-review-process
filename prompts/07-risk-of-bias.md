> Source: Raphael Malikian, Multi-Agent Cochrane-Level Review Process (Robust Standard v2) — https://github.com/rtmalikian/multi-agent-cochrane-level-review-process — Licence: Attribution — Non-Commercial (LICENSE.md). Free for non-profit use with acknowledgement; commercial use by licence (rtmalikian@gmail.com).
>
> Use with `EXAMPLE_MULTI_STEP_PROMPT.md`. Send one step at a time. You (the human) are the accountable author.

# STEP 7 — Risk of bias, in duplicate, adjudicated by reading

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
