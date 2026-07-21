# Source Map

## Scope

This map separates user evidence, method-design records, external literature,
and target-venue exemplars for the paper tentatively titled **Flow-KTO:
Learning Flow-Based Robot Policies from Unary Feedback**. External papers may
support positioning or teach presentation patterns; they are not evidence for
this paper's empirical claims.

## Authority And Precedence

When sources disagree, use the following order:

1. Explicit user-confirmed title, contribution framing, and claim boundaries in
   `paper_spine_config.json`.
2. The newest consolidated project status and dated attribution/probe reports.
3. Current research syntheses and validated diagnostic protocols.
4. The original proposal for intended mechanisms and derivations, but not as
   proof that those mechanisms or empirical effects are correct.
5. Earlier experiment logs, retained for development history and failure-mode
   analysis when later documents have not invalidated them.
6. External literature for prior-art comparison, definitions, and citations.
7. ICLR exemplars for structure and rhetoric only.

## Internal Project Sources

| Source ID | Source | Category | Authority / Allowed Use | Important Boundary |
|---|---|---|---|---|
| INT-001 | `/home/robotera/workspace/skillized-agentic-workflow/manipulation_rl/Flow-KTO/001_KTO_proposal.md` | Human-authored proposal | Intended problem, initial derivation, and candidate objective | Statements such as a near-lossless CFM replacement are hypotheses unless supported by a theorem or dedicated approximation study. |
| INT-001A | `paper_rewriting_output/user_supplied_real_robot_evidence.md` | User-reported deployment evidence | Direct qualitative observation of clear whole-robot action improvement and BOT154/BOT159 rate comparisons | Manuscript strength remains conditional on metric definitions, raw denominators, checkpoint mapping, and deployment comparability. |
| INT-002 | `README.md` and `STATUS.md` in the project-material directory | Current project index and status | Entry point for the latest valid experimental interpretation and source precedence | Status text summarizes remote artifacts; it is not a substitute for raw logs when exact reproduction is required. |
| INT-003 | `015_z0_estimator_failure_modes_20260618.md`, `016_healthy_run_z0_mc_vs_rolled_20260619.md`, `022_policy_vs_dataset_action_z0_20260630.md` | Estimator studies | Evidence distinguishing policy-sampled, dataset-action, and rolled-action estimators | Rolled-action estimates are failure-mode/OOD diagnostics, not the proposal-level KTO baseline. Dataset-action scores are matched-action diagnostics, not a replacement for the policy expectation. |
| INT-004 | `023_three_deployed_models_attribution_20260713.md` | Current attribution analysis | Evidence for negative-margin saturation, beta-dependent gradients, and the beta/LR coupling hypothesis | Cross-run causal claims remain bounded because base model, data mixture, preprocessing, labels, and state conditioning were not all controlled simultaneously. |
| INT-005 | `024_beta400_n20_epoch1_4_probe_20260714.md`, `025_beta400_n16_epoch5_probe_20260714.md`, `026_n16_strict_multisite_heldout_epoch4_6_20260714.md` | Latest checkpoint/probe reports | Current evidence for beta-400 candidates, early stopping, strict held-out BC, and margin/saturation diagnostics | The original SFSZ panel overlapped training data and is only a regression panel. Strict multisite results carry the held-out claim. Small dagger strata must not support broad category claims. |
| INT-006 | `010_candidate_decision_and_positive_kto.md` through `021_explore_matrix_0624_insights_20260625.md` | Historical experiments and syntheses | Design history, ablation hypotheses, and documented failure modes | Several runs used rolled-action or KTO-only baseline pools and are explicitly superseded. Use only with the validity label in the later README/STATUS. |
| INT-007 | `auto-research/*.md` | Detailed development logs | Provenance, run history, and pointers to remote raw artifacts | These records contain intermediate decisions and must not be promoted to final claims without checking later corrections. |
| INT-008 | `probe/*.md` | Evaluation protocols | Metadata alignment, manifest discipline, fixed-BC diagnostics, and report semantics | A protocol documents intended procedure; only a completed report documents an observed result. |

## External Literature Sources

| Source Group | Path | Role | Prohibited Use |
|---|---|---|---|
| ICLR normal exemplars | `/home/robotera/文档/ICLR_template/Normal/` | Representative conference structure, novelty framing, evidence ordering, and page-budget patterns | Do not transfer claims, results, or citation statements into Flow-KTO. |
| ICLR award exemplars | `/home/robotera/文档/ICLR_template/PaperWithAwards/` | High-end contribution and narrative patterns | Do not treat award papers as the median ICLR norm. |
| Robot manipulation/RL literature | `/home/robotera/文档/manipulation_rl/` | Closest application and learning-setting comparison | Does not validate Flow-KTO's method or results. |
| Core preference/flow literature | `/home/robotera/文档/Flow-KTO/` | KTO, Diffusion-KTO, and FPO definitions and closest-work analysis | Must be cited and compared accurately, but must not define the paper as an `A+B` combination. |
| Additional robotics literature | `/home/robotera/文档/RSS/` | Recent robot-policy learning, offline improvement, and flow-policy context | Venue and task differences must be stated before transferring conclusions. |

The item-level external index is
`paper_rewriting_output/reference_materials/source_index.md`.

## Known Invalidated Or Restricted Evidence

- Same-batch rolled-action `z_0` is not a reliable estimator of
  `E_{a ~ pi_theta}[L_ref - L_theta]`; retain it only as an action-sensitivity
  diagnostic.
- The 2026-06-21 policy-z0 pilot/epoch-15 runs used a KTO-only baseline pool and
  are invalid for candidate selection or final efficacy claims.
- Historical cross-run probes that inherited the wrong `MIST.use_state` value
  cannot support model comparisons.
- The earlier SFSZ panel described as held out overlapped active KTO training
  data. It is a regression panel; only the later strict multisite panel supports
  held-out language.
- Recorded speed-ratio fields did not activate the intended transform in the
  compared deployed models and cannot explain their performance differences.
- A larger negative margin is not monotonically better. The project records
  show a reward-hacking/saturation regime, so raw margin, beta-scaled margin,
  effective gradient, Action/Reference loss, and held-out BC must be interpreted
  together.

## Local Verification Boundary

The supplied project-material directory contains Markdown proposals, summaries,
diagnostic reports, and protocols. It does **not** currently contain the source
code, training configs, raw JSON/JSONL logs, manifests, checkpoints, figures, or
robot-evaluation videos referenced under paths such as `poc/rmp/RobotModelPlatform`
or `/era-ai/private/...`. Numerical statements in the Markdown reports are user
evidence, but raw-artifact reproduction is not possible from the supplied local
bundle alone. Final headline metrics must therefore retain their run/checkpoint,
sample/seed, manifest, and validity qualifiers, and any claim needing raw
verification remains conditional until those artifacts are available.

## Research-Time Open Items

- The target cycles are ICLR 2027 and RSS 2027; their venue rules must be
  rechecked when official 2027 calls and author guides are published.
- A user-supplied real-robot comparison is now frozen in
  `user_supplied_real_robot_evidence.md`. It supports the existence of clear
  deployment improvement, but metric definitions, raw denominators, checkpoint
  mapping, and protocol comparability remain open before abstract-level claims.
- The paper must distinguish a gradient-aligned CFM surrogate from exact or
  lossless log-likelihood equivalence unless stronger theoretical or empirical
  evidence is supplied.
