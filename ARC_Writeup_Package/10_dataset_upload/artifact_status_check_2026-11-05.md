# Artifact status check — November 5, 2026 (owner-side) — REVISED same evening

Method: Kaggle SDK `GetKernel`/`GetDataset` with the defiaudit account credentials,
plus anonymous HTTP fetches (public pages render their own `<title>`; private or
missing pages return the generic Kaggle title). Control test: a known PRIVATE
kernel (`defiaudit/private-arc2-v12-a2-div-20261025-r2`) returns HTTP 200 for its
owner.

**Revision (evening, Nov 5 — read-only browser check with the owner session):**
the two notebook rows below were first read as "REMOVED" because the API returned
404 on their slugs. That inference was wrong: a 404 on a slug does not distinguish
deletion from a rename + privatization. Opening both links in a logged-in browser
shows the history alive. Paper v11 uses the corrected reading.

| Artifact | Type | Status on 2026-11-05 |
|---|---|---|
| `defiaudit/arc-agi2-lb33-89-minimal-perfpatch` | notebook (draw kernel) | Old slug no longer resolves publicly (API 404). **Owner browser check: the link opens a private kernel (shown as "v32-VERIF", consistent with `defiaudit/arc-agi2-v32-verif-executive-verifier-bench`) carrying a 32-version server-side history that includes saved v12 and the verbatim v26; best shown graded result 31.39 at v9.** So: renamed + private, NOT removed. |
| `defiaudit/arc-agi2-selection-bakeoff-v2-decoder-battery` | notebook (bake-off) | Separate kernel gone; its link opens the same private kernel — history merged (as first noted). |
| `defiaudit/arc-agi2-v32-verif-executive-verifier-bench` | notebook | Private; the owner-side target of the two links above. |
| `defiaudit/agi2-dsl-v214r-solver` | notebook | Public (anonymous title test passes). |
| `defiaudit/agi2-dsl-v214r-chain` | dataset | Public (anonymous title test passes). |
| `defiaudit/arc-paper-track-2026` | dataset | Public (`isPrivate: false`, anonymous API check Nov 6); v9 confirmed live at version 4 (byte-identical to the archive copy), v11 at version 5 (Nov 5); version 6 ships the v14 PDF (the abstract compares the fit with two related descriptive summaries --- matching the writeup body; the rerun-variance finding is scoped to our fork-cluster entry; the cover anchor is limited to scores). |
| `mikelou1/arc-agi2-lb33-89-minimal-perfpatch` | notebook (the fork source) | **Public, 235 votes.** Slug and title self-label "LB33.89" — a fork-time score we have found no independent record of; the page's current public score shows 32.22. |
| Competition submissions (45 rows) | competition record | Intact — verbatim export ships in this folder (`kaggle_submissions_export_2026-11-05.csv/.json`). |
| Leaderboard | competition record | Intact — full API pull of Nov 5 (`kaggle_lb_full_2026-11-05.json`, 3,627 teams): mikelou1 **#33 @ 69.72** (current final standing; confirmed on the live page), DefiAudit #715 @ 31.39. `kaggle_lb_settled_2026-10-29.csv` is a **dated pre-close snapshot** (mikelou1 #17 on Oct 29 — not the final standing). `kaggle_lb_snapshot_2026-09-06.csv` puts the Sep 6 top-1% cutoff at 33.06 (rank 19 of 1,852). Bronze line 32.22. |

Why this revision matters: the v9/v10 text withdrew version-history claims on the
assumption the draw kernel had been deleted. The history is in fact alive
privately — version-level comparison (v12 vs v26, the 31.39 draw at v9) is
owner-side possible again, though not public. The public record remains the
fire-time descriptions plus the SHA-256 byte snapshots under `code_chapters/`.
The 33.89 fork-time score of the source notebook stays a self-label: only its
name carries it, and paper v11 marks it as such everywhere.
