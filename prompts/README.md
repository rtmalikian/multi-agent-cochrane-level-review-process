> Source: Raphael Malikian, Multi-Agent Cochrane-Level Review Process (Robust Standard v2) — https://github.com/rtmalikian/multi-agent-cochrane-level-review-process — Licence: Attribution — Non-Commercial (LICENSE.md). Free for non-profit use with acknowledgement; commercial use by licence (rtmalikian@gmail.com).
>
> Use with `EXAMPLE_MULTI_STEP_PROMPT.md`. Send one step at a time. You (the human) are the accountable author.

# Stage Prompts

One file per stage, extracted from `../EXAMPLE_MULTI_STEP_PROMPT.md`, for coordinating separate agent sessions by hand. Keep independence rules: screeners, extractors and RoB assessors work in isolated sessions and must not see each other's files until the merge step for their stage.

Files: 00 master instruction, 01 protocol, 02 search, 03 dual screening, 04 adjudication, 05 full-text retrieval, 06 dual extraction, 07 risk of bias, 08 statistics, 09 figures + visual QA, 10 GRADE, 11 manuscript, 12 dissemination.
