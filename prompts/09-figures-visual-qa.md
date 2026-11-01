> Source: Raphael Malikian, Multi-Agent Cochrane-Level Review Process (Robust Standard v2) — https://github.com/rtmalikian/multi-agent-cochrane-level-review-process — Licence: Attribution — Non-Commercial (LICENSE.md). Free for non-profit use with acknowledgement; commercial use by licence (rtmalikian@gmail.com).
>
> Use with `EXAMPLE_MULTI_STEP_PROMPT.md`. Send one step at a time. You (the human) are the accountable author.

# STEP 9 — Figures and visual QA (a shipping gate)

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
