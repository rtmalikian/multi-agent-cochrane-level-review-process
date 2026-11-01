> Source: Raphael Malikian, Multi-Agent Cochrane-Level Review Process (Robust Standard v2) — https://github.com/rtmalikian/multi-agent-cochrane-level-review-process — Licence: Attribution — Non-Commercial (LICENSE.md). Free for non-profit use with acknowledgement; commercial use by licence (rtmalikian@gmail.com).
>
> Use with `EXAMPLE_MULTI_STEP_PROMPT.md`. Send one step at a time. You (the human) are the accountable author.

# STEP 2 — Search (full retrieval, nothing partial counted as searched)

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
