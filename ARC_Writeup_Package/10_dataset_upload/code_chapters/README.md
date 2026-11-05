# Chapter code snapshots (byte archive)

After the campaign the draw notebook (`defiaudit/arc-agi2-lb33-89-minimal-perfpatch`,
kernel id 133380733) stopped resolving publicly (API 404); an owner-side browser
check on Nov 5 found it alive but **renamed and private, with its 32-version
server-side history intact** — shown as "v32-VERIF", saved v12 and the verbatim
v26 included, best shown graded result 31.39 at v9 (see
`07_raw_draws/evidence/artifact_status_check_2026-11-05.md`). These four files
remain the public byte record of the builds that were **pushed to or pulled from
that exact kernel** during the campaign and kept locally; SHA-256 checksums are in
`SHA256SUMS.txt`.

## Naming — two numbering systems, stated side by side

The notebooks' internal headers carry their own build numbers (v38, v39-BAKEOFF,
v41-V2SEL, v42-HARD). The paper, the ledger (`arc2_draws_raw_45.csv`) and the
fire-time descriptions in Kaggle's export use the kernel-version labels (v1–v15
chapters, v26 verbatim, v29, v31-HARD). The two prefixes do **not** coincide — the
v38–v42 headers cannot be this kernel's version numbers, since its history holds
32 versions; they are the campaign's separate internal build counter. The
private server-side history corroborates the kernel-version labels (v12 and v26
are visible in it; its best shown result, 31.39, sits at v9). The authoritative
draw→code mapping is the fire-time descriptions in
`07_raw_draws/evidence/kaggle_submissions_export_2026-11-05.csv`.

| File | Internal header (verbatim) | Chapter / use (paper + fire-log labels) |
|---|---|---|
| `01_forkline_snapshot_pulled_2026-09-12.ipynb` | `# v38 — 基于原始 33.89 baseline 的最小性能补丁` ("minimal perf patch on the original 33.89 baseline") | Fork-line build, pulled from Kaggle Sep 12, 2026 immediately before the draw-6 push (v4/v5 era; the v1–v15 chapter family behind graded draws 1–38). |
| `02_bakeoff_build.ipynb` | `# v39-BAKEOFF — (selection-only experiment; NOT a submission notebook)` | The 10-selector bake-off build (paper Section 6; baked off 37 eval tasks on Oct 26). |
| `03_v29_rerank_build.ipynb` | `# v41-V2SEL — selection default = soft_agreement (bake-off winner 9.17 vs 7.50)` | The re-rank/selection build — fire description of graded draw 40 (ref 57682428): "draw40 v29-V2SEL first soft_agreement draw; bake-off winner deployed as module default". |
| `04_v31_hard_build.ipynb` | `# v42-HARD — per-task try/except (draw39 rerun-crash lesson) + soft_agreement default` | The crash-hardened build — fire descriptions of graded draws 41–44 (refs 57717109 / 57752643 / 57786357 / 57855664): "v31-HARD daily variance draw; soft_agreement selection + per-task crash hardening". |

Caveats: these are the local push/pull copies, not Kaggle's server archive; the
mapping above follows the campaign's fire logs, and the submission-level record
(which kernel version produced which graded draw) survives independently in
Kaggle's own submissions export with fire-time descriptions. The snapshots are
**code-only**: execution outputs were not preserved (verified — 0 of 8 code cells
carry outputs in each file), so nothing here is a saved-run proof; the graded
results these builds fed live in the export and the ledger.
