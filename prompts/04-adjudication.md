> Source: Raphael Malikian, Multi-Agent Cochrane-Level Review Process (Robust Standard v2) — https://github.com/rtmalikian/multi-agent-cochrane-level-review-process — Licence: Attribution — Non-Commercial (LICENSE.md). Free for non-profit use with acknowledgement; commercial use by licence (rtmalikian@gmail.com).
>
> Use with `EXAMPLE_MULTI_STEP_PROMPT.md`. Send one step at a time. You (the human) are the accountable author.

# STEP 4 — Adjudication by reading (never by rule)

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
