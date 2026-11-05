## 1. What we submitted

Our ARC-AGI-2 entry is a two-candidate hybrid. Candidate 1 is a fork of a top public notebook in our reachable band (`mikelou1/arc-agi2-lb33-89-minimal-perfpatch` — public; its slug and title self-label "lb33-89", a fork-time score we cannot independently verify — the page shows 32.22). Candidate 2 is a self-built DSL exact-fit solver (`defiaudit/agi2-dsl-v214r-solver`, public, CPU-only, no internet, no LLM), the surviving artifact of a 217-round hypothesis-lab cycle. Our best final score is 31.39 — 0.55 below the 31.94 bronze cutoff at the Nov 2 close (rank 669 of 3,571 then; settled once late grading drained: 715 of 3,627, cutoff 32.22).

We treated the submission pipeline as a measurable system, not a one-shot lottery ticket. The headline result is not a leaderboard record; it is an audit: **44 graded hidden-set draws across the campaign — 43 on our fork line, one pooled draw on a second fork (NVARC+) — produced scores from 26.39 to 31.39, a 5.00-point spread.** For a benchmark graded to two decimals, the largest source of variance in a typical fork-cluster entry is not the model — it is the rerun.

## 2. The draws table

All scores are official; every run used the same 4×L4 environment and hidden test set; the export's fire-time descriptions carry code labels for 39 of the 44 graded draws; the other five on ledger notes and byte snapshots.

| # | Code version | Seed state | Public score |
|---|--------------|-------|--------------|
| 1 | perfpatch v1 | unfixed | 28.89 |
| 2 | v1 rerun | unfixed | **30.97** |
| 3 | perfpatch v4 | ledger-note seed patch | 30.14 |
| 4 | NVARC+ v3 (2nd fork) | seeded pass (fire desc.) | 30.14 |
| 5 | v1 rerun | unfixed | 29.72 |
| … | 39 more reruns across chapters | unfixed | 26.39–31.39 |
| 44 | v31-HARD rerun (final, fired Nov 1) | unfixed | 28.47 |

Final accounting (reconciled row-by-row against Kaggle's Nov 5 export, shipped with the CSV): 45 submissions, 44 graded draws, one end-to-end error excluded from all statistics. The chapters are logged: 43 of the 44 draws sit on the fork's development line (draws 1–3, 5–38, kernels v1–v15); draw 4 is the campaign's one pooled draw from a second fork (NVARC+); then a verbatim control whose fire description claims byte-identity with saved v12 (39; "=v12 bytes"; a second v26 run crashed and is excluded), the re-ranked selection layer (40), and the crash-hardened build v31-HARD (41–44). Engineering barely moved the distribution: σ drifted from 1.14 (n=38) to 1.09 (n=44), so later draws are approximately exchangeable with the earlier ones. Summary statistics: **μ = 29.16, sample σ = 1.09, median 29.31, min 26.39, max 31.39** (population σ: 1.08; best Sep 18). Two findings. First, the three early unfixed draws landed on three distinct values straddling a 2.08-point spread that contains most of the published fork-cluster band (similar forks cluster near 28.06 on the public LB; the source notebook self-labels 33.89 in slug and title — unverified; page shows 32.22 — and its author finished the season at 69.72). A fork team's "score" is a *random variable*, and most leaderboard comparisons inside the fork band are noise. Second, the two draws the record marks as seed-controlled — ref 56125103 (our ledger's seed-patched-v4 note; the export carries no fire description for it) and ref 56148554 (fire description: "passA LB-proven + seedB") — landed on exactly 30.14, while three unpatched v1 runs scattered 28.89–30.97; two draws cannot establish causation (§11), and the seed labels are bookkeeping entries, not platform-verified states.

## 3. Why: leaderboard entries are order statistics

The perfpatch family chains an LLM proposal step with a deterministic search/verify layer. The search layer is reproducible; the proposal layer is not unless every sampling seed is pinned. With seeds free, each rerun resamples the proposal distribution, and the graded score is one draw from that distribution. This mechanism explains three community observations: (a) forks of the same notebook scatter across a multi-point band while the author sits on top of it; (b) scores drift after semantically neutral edits that perturb RNG consumption order; (c) "the fork didn't reproduce the author" is usually not skill drift — it is one sample competing against the maximum of many undocumented samples. A leaderboard of point estimates systematically overstates the reproducibility of everyone on it. Without a draws table, an author score may be skill or luck; with one, fork quality becomes measurable.

## 4. The free-draw audit protocol

Resubmitting an already-published notebook version is a free rerun: it consumes the daily slot: no code work, quota, or review. The protocol for any rerun-scored competition:

1. Fork the strongest reachable public notebook; submit once to establish your band.
2. Log every draw with its submission ID.
3. Pin seeds only when a stable comparison number is needed (accepting a fixed score that may sit below your best draw).
4. Spend every remaining daily slot resampling the *unfixed* version.
5. Let leaderboard auto-select keep the maximum; report the full table, not just the max.

## 5. What forty-four draws bought

Fitting a normal to the 44 draws gives μ = 29.16, σ = 1.09, validated against two independent observables. The order-statistics model predicts an expected maximum of ≈31.55 for 44 draws; the observed maximum is 31.39 — a 0.16 gap. The fitted tail predicts 0.89 draws at or above 31.39 in 44 tries; we observed exactly one. The final draw (28.47, 26th percentile) landed with the queue 24–31 hours deep. Pricing the lottery: each draw carried P(≥ 31.94) ≈ 0.53%, so 44 draws priced the chance of at least one bronze-grade draw at ≈21%. We did not cash it: the best draw stayed 0.55 below the 31.94 line at the close (settled: 32.22). That is the point: the protocol converts luck into a measured, bounded quantity and prices reruns in points.

## 6. Bench the selector: a causal layer and a refutation

We then tested whether smarter selection could beat resampling. A 10-selector bake-off on 37 held-out evaluation tasks found a winner worth +1.67 points over the production default. A calibrated simulation projected a further +2.27 from an executive verifier. A zero-quota real-pool benchmark on 40 evaluation tasks refuted the projection (+0.00): forcing attempt-2 diversity is harmful (−2.00). The diagnosis relocates the binding constraint: the candidate pool, not the selector. Decoding solved 118 of 741 pool attempts (15.9%); selection can only rank what the pool contains. Simulated verifier gains are hypotheses until they survive the real pool.

## 7. Where else this applies

Nothing here is ARC-specific. Any evaluation that (i) reruns stochastic code on a hidden set and (ii) selects a team's maximum is an order-statistics marketplace: LLM benchmark submissions with sampling temperature, ARC-AGI-3 agent reruns, nondeterministic training pipelines. The same audit — log every draw, fit the spread, weigh points-per-draw against points-per-engineering-day — applies unchanged; publishing draws tables is the cheapest known fix for leaderboard noise.

## 8. The second candidate, and a negative result

Our DSL solver keeps the submission honest. It is a pure-Python exact-fit chain (v208–v214 lineage) with no learned component; its public notebook self-scores on the open evaluation split and writes the hidden-set submission JSON; its 30-file dependency closure ships as a public dataset (`defiaudit/agi2-dsl-v214r-chain`). It scored 0 on the hidden set; it bounds what a CPU-only, no-LLM exact-fit program covers on ARC-AGI-2 and motivated every rejection in our v215–v217 lab cycle.

## 9. The ARC-AGI-3 replication: pin the dependencies

We replicated the audit on the ARC-AGI-3 track (best agent score 1.82). Mid-competition, the third-party model our bundle imported (`keithtyser/qwen3-8-flash-next-nvfp4`) was privatized by its author (API 403, web 404); the bundle's strict identity check refused substitutes and closed the track. The one-line summary: **measure the rerun, bench the selector, pin the dependencies.** Reproducibility is not only statistics; it is supply-chain hygiene.

## 10. Reproducibility

Every number is anchored to a public artifact: the submission IDs in the ledger, the DSL notebook and dataset, and the full-paper PDF in Project Links, whose Appendix A carries the full 45-submission ledger, mirrored as a public CSV beside a verbatim Kaggle submissions export (Nov 5). The draw notebook's slug stopped resolving after the campaign; it survives renamed and private, its 32-version history intact (owner check, Nov 5) — v12 and the verbatim v26 included — and its chapter-level code ships as SHA-256-checked byte snapshots in the same dataset. Any team can replicate the audit with one fork and a week of resubmits.

## 11. Limitations

Forty-four draws cannot prove draws are independent, and the normal fit is convenient rather than sacred — it is validated against two observables, not derived. Seed "fixing" rests on ledger notes, not platform-verified states; hidden-set hardware variation remains possible. Our absolute score is mid-pack, and nothing here claims a modeling breakthrough. The contribution is the measurement instrument: draws tables make fork quality — and leaderboard stability — falsifiable, at zero cost, before the next engineering sprint.
