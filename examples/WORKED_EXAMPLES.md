# Worked Examples — Three Reviews Built With This Process

All three are Cochrane-level, single-author, LLM-team reviews by Raphael Malikian. Free preprints (CC BY 4.0), full data and code on GitHub. Hub: https://rtmalikian.github.io/systematic-reviews/

## Review 1 — Ambient AI scribes (22 Oct 2026)
Question: do ambient AI scribes cut documentation time and after-hours work, ease burnout — and what errors do they add?
Flow: 1,049 records → 567 screened → 157 sought → 74 studies included. Screening agreement 0.77, kappa 0.64.
Headlines: documentation time −18.9% (low certainty); work exhaustion SMD −0.44 in 2 RCTs (moderate); notes with ≥1 error 59.8% (very low).
Lesson baked into the standard: report benefit and error burden for the same tool, in the same paper, or the synthesis is half a result.
Zenodo: https://doi.org/10.5281/zenodo.23565499 · GitHub: https://github.com/rtmalikian/ambient-ai-scribes-meta-analysis-clinical-documentation-burnout-note-errors

## Review 2 — LLM citation fabrication (22 Oct 2026, robustness pass 23 Oct 2026)
Question: what proportion of LLM-generated biomedical references are fabricated, inaccurate, or fully accurate?
Flow: 16,474 screened (incl. 489 from citation chasing) → 63 experiments, 148 arms, 22,461 references.
Headlines (corrected, post-robustness-pass): fabricated 19.4% (14.9–24.8); fully accurate 37.0%; any major inaccuracy 16.5%; retrieval on 5.8% fabricated vs off 31.0%. GRADE very low throughout.
Lessons baked into v2: Review 2 v1 used a coded screening adjudication rule, one extraction + verification, and a mechanical RoB rule. The audit named all three as step-downs — so v2 bans all three, and the corrected version was re-issued on every platform with the amendment logged, never silently overwritten.
Zenodo: https://doi.org/10.5281/zenodo.23585717 · GitHub: https://github.com/rtmalikian/llm-citation-fabrication-meta-analysis-biomedical-references-hallucinated-citations

## Review 3 — Errors in LLM clinical summaries (31 Oct 2026)
Question: what proportion of LLM-generated clinical summaries contain ≥1 clinically significant error, per summary?
Flow: 991 records → 483 screened → 48 assessed → 11 studies, 22 arms. Kappa 0.62. Extraction: 374 field pairs, 161 raw discrepancies (43%, mostly format), 6 substantive, all settled by re-reading.
Headlines: primary outcome NOT pooled — only 1/11 studies reported it per summary (21.0%, 13/62). Supplementary any-error pool 60.6%; omissions 20.7%; fabrications 17.6%; inaccuracies 27.9%. GRADE very low throughout. RoB: high 9, some concerns 2, low 0.
Lessons baked into the prompt: an unpoolable primary outcome is a finding (here, a formal reporting-gap result), not a licence to redefine the outcome; and page-fit visual QA for every figure AND table page is a shipping gate (Round 1 failed, was fixed, Round 2 passed page by page).
Zenodo: https://doi.org/10.5281/zenodo.23847500 · GitHub: https://github.com/rtmalikian/llm-clinical-summarization-errors-meta-analysis · Reading page: https://rtmalikian.github.io/llm-clinical-summarization-errors-meta-analysis/
