# ARC Paper Track 2026 — fork variance audit (defiaudit)

Evidence bundle for the paper "Fork Variance Is a Free Sample: Auditing a Hybrid
ARC-AGI-2 Submission" (ARC Prize 2026 Paper Track, writeup submitted Sep 12, 2026).

## Contents (v16, November 6, 2026)
- `ARC_Paper_Track_defiaudit_v16.pdf` — the full paper, current version (10 pages incl. cover; Appendix A = the complete 45-submission ledger). Earlier versions (v9 at dataset version 4, v11 at version 5) stay in this dataset's version history. v16 regenerates the media-gallery cover with the scoped anchor claim (every graded score anchored to a Kaggle submission ID) and fixes the printed-margin clipping of the dataset URL; no wording changes.
- `arc2_draws_raw_45.csv` — raw ledger: `ledger_no` 1-45, `graded_no` 1-44, code chapters, statuses, scores, notes. Reconciles 45/45 with the submissions export.
- `kaggle_submissions_export_2026-11-05.csv/.json` — verbatim Kaggle API export: dates, fire-time descriptions (present for 39 of the 44 graded draws; 5 empty), statuses, scores, and the failed run's error string.
- `kaggle_lb_snapshot_2026-09-06.csv` — public leaderboard snapshot proving 33.06 was the top-1% cutoff at fork time (rank 19 of 1,852).
- `kaggle_lb_settled_2026-10-29.csv` — official leaderboard CSV export of Oct 29, 2026 (pre-close snapshot: mikelou1 #17 then; the final standing is #33 @ 69.72 per the Nov 5 full pull below). Bronze line 32.22.
- `kaggle_lb_full_2026-11-05.json` — full settled pull via API (3,627 teams; DefiAudit #715 @ 31.39; mikelou1 #33 @ 69.72).
- `artifact_status_check_2026-11-05.md` — which cited artifacts are public, private, or merged (owner-side checks; the draw notebook survives renamed and private with its 32-version history — see the file).
- `code_chapters/` — SHA-256-checked byte snapshots of the chapter builds (fork-line, bake-off, v29 re-rank, v31-HARD) pushed to/pulled from kernel id 133380733 during the campaign. Each notebook's verbatim internal header is quoted beside its chapter label in `code_chapters/README.md`.

All scores are official Kaggle competition results for account defiaudit.
