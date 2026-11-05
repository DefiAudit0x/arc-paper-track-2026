## 1. What we submitted

Our ARC-AGI-2 entry is a two-candidate hybrid. Candidate 1 is a fork of a public notebook in our reachable band (`mikelou1/arc-agi2-lb33-89-minimal-perfpatch` — public; its title and slug self-label "33.89" (slug: "lb33-89"), which we cannot independently verify; its public page showed 32.22 at the Nov 5 check). Candidate 2 is a self-built DSL exact-fit solver (`defiaudit/agi2-dsl-v214r-solver`, public, CPU-only, no internet, no LLM), the surviving artifact of a 217-round hypothesis-lab cycle. Our best final score is 31.39 — 0.55 below the 31.94 bronze cutoff at the Nov 2 close (rank 669 of 3,571 then; settled once late grading drained: 715 of 3,627, cutoff 32.22).

We treated the submission pipeline as a measurable system, not a one-shot lottery ticket. The headline result is not a leaderboard record; it is an audit: **44 graded hidden-set draws across the campaign — 43 on our fork line, one pooled draw on a second fork (NVARC+) — produced scores from 26.39 to 31.39, a 5.00-point spread.** For a benchmark graded to two decimals, the largest source of variance in a typical fork-cluster entry is not the model — it is the rerun.

## 2. The draws table

All scores are official; every run used the same 4×L4 environment and hidden test set. The export's fire-time descriptions supply code labels for 39 of 44 graded draws; the other five rely on ledger notes and byte snapshots.

| # | Code version | Seed state | Public score |
|---|--------------|-------|--------------|
| 1 | perfpatch v1 | unfixed | 28.89 |
| 2 | v1 rerun | unfixed | **30.97** |
| 3 | perfpatch v4 | ledger-note seed patch | 30.14 |
| 4 | NVARC+ v3 (2nd fork) | seeded pass (fire desc.) | 30.14 |
| 5 | v1 rerun | unfixed | 29.72 |
| … | 39 more reruns across chapters | unfixed | 26.39–31.39 |
| 44 | v31-HARD rerun (final, fired Nov 1) | unfixed | 28.47 |

The Nov 5 Kaggle export reconciles 45 submissions: 44 with scores and one no-score row carrying an unhandled-error message. We interpret it as a whole-run failure and exclude it from statistics. The ledger assigns 43 graded draws to one fork-development line: draws 1–3 and 5–38 (kernels v1–v15), the v26 control (39), v29 re-rank (40), and v31-HARD (41–44). Draw 4 alone is the pooled run from the second fork, NVARC+. These are successive code chapters, not identical code. The v26 fire description claims byte identity with saved v12 ("=v12 bytes"); a second v26 run had no grade. The sample σ was 1.14 for n=38 and 1.09 for n=44; this descriptive similarity does not establish exchangeability between later and earlier draws. Summary statistics: **μ = 29.16, sample σ = 1.09, median 29.31, min 26.39, max 31.39** (population σ: 1.08; best Sep 18). Two findings. First, the three early unfixed draws landed on three distinct values straddling a 2.08-point spread that contains most of the published fork-cluster band (similar forks cluster near 28.06 on the public LB; the source notebook self-labels 33.89 in slug and title — unverified; its public page showed 32.22 at the Nov 5 check — and its author finished the season at 69.72). A fork team's "score" is a *random variable*, and most leaderboard comparisons inside the fork band are noise. Second, the two draws the record marks as seed-controlled — ref 56125103 (our ledger's seed-patched-v4 note; the export carries no fire description for it) and ref 56148554 (fire description: "passA LB-proven + seedB") — landed on exactly 30.14, while three unpatched v1 runs scattered 28.89–30.97; two draws cannot establish causation (§11), and the seed labels are bookkeeping entries, not platform-verified states.

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

The normal fit (μ = 29.16, σ = 1.09) is compared with the observed maximum and bronze-threshold crossing count. These are related descriptive summaries of the same draws, compatible with the fit; they are not independent validation or evidence of exchangeability. The model predicts an expected maximum of ≈31.55 over 44 draws; the observed maximum was 31.39 (gap 0.16). Its fitted tail predicts 0.89 draws at or above 31.39; one was observed. The final draw (28.47, 26th percentile) landed with the queue 24–31 hours deep. Modeled P(≥ 31.94) ≈ 0.53% per draw; over 44 draws, the estimated chance of at least one bronze-grade draw is ≈21%. We did not cash it: the best draw stayed 0.55 below the 31.94 line at the close (settled: 32.22). That is the point: the protocol converts luck into a measured, bounded quantity and prices reruns in points.

## 6. Bench the selector: a causal layer and a refutation

We then tested whether smarter selection could beat resampling. A 10-selector bake-off on 37 held-out evaluation tasks found a winner worth +1.67 points over the production default. A calibrated simulation projected a further +2.27 from an executive verifier. A zero-quota real-pool benchmark on 40 evaluation tasks refuted the projection (+0.00): forcing attempt-2 diversity is harmful (−2.00). The diagnosis relocates the binding constraint: the candidate pool, not the selector. Decoding solved 118 of 741 pool attempts (15.9%); selection can only rank what the pool contains. Simulated verifier gains are hypotheses until they survive the real pool.

## 7. Where else this applies

Nothing here is ARC-specific. Any evaluation that (i) reruns stochastic code on a hidden set and (ii) selects a team's maximum is an order-statistics marketplace: LLM benchmark submissions with sampling temperature, ARC-AGI-3 agent reruns, nondeterministic training pipelines. The same audit — log every draw, fit the spread, weigh points-per-draw against points-per-engineering-day — applies unchanged; publishing draws tables is the cheapest known fix for leaderboard noise.

## 8. The second candidate, and a negative result

Our DSL solver keeps the submission honest. It is a pure-Python exact-fit chain (v208–v214 lineage) with no learned component; its public notebook self-scores on the open evaluation split and writes the hidden-set submission JSON; its 30-file dependency closure ships as a public dataset (`defiaudit/agi2-dsl-v214r-chain`). It scored 0 on the hidden set; it bounds what a CPU-only, no-LLM exact-fit program covers on ARC-AGI-2 and motivated every rejection in our v215–v217 lab cycle.

## 9. The ARC-AGI-3 replication: pin the dependencies

We replicated the audit on the ARC-AGI-3 track (best agent score 1.82). Mid-competition, the third-party model our bundle imported (`keithtyser/qwen3-8-flash-next-nvfp4`) was privatized by its author (API 403, web 404); the bundle's strict identity check refused substitutes and closed the track. The one-line summary: **measure the rerun, bench the selector, pin the dependencies.** Reproducibility is not only statistics; it is supply-chain hygiene.

## 10. Reproducibility

Graded scores map to submission IDs in the public ledger. The linked dataset contains the 45-row ledger, verbatim Nov 5 export, and this v12 PDF. An owner-side check on Nov 5 found the draw history in a renamed private kernel: 32 versions, including v12 and verbatim v26; the best shown result was 31.39 at v9. This history is not publicly inspectable; public code evidence comprises the fire-time descriptions and SHA-256-checked chapter snapshots.

## 11. Limitations

Forty-four draws cannot prove independence. The normal fit is descriptive, not derived; the maximum and bronze-crossing count are related, not independent checks. Seed "fixing" rests on ledger notes, not platform-verified states; hidden-set hardware variation remains possible. Our absolute score is mid-pack, and nothing here claims a modeling breakthrough. The contribution is the measurement instrument: draws tables make fork quality — and leaderboard stability — falsifiable, at zero cost, before the next engineering sprint.
