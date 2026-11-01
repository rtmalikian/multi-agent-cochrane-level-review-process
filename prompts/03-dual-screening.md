> Source: Raphael Malikian, Multi-Agent Cochrane-Level Review Process (Robust Standard v2) — https://github.com/rtmalikian/multi-agent-cochrane-level-review-process — Licence: Attribution — Non-Commercial (LICENSE.md). Free for non-profit use with acknowledgement; commercial use by licence (rtmalikian@gmail.com).
>
> Use with `EXAMPLE_MULTI_STEP_PROMPT.md`. Send one step at a time. You (the human) are the accountable author.

# STEP 3 — Dual independent screening

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
