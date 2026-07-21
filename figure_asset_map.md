# Figure and Asset Map

## Current asset status

The indexed project directory contains Markdown research logs but no local
bitmap or vector assets suitable for direct manuscript inclusion. The current
writing phase therefore plans argument-bearing visuals without fabricating
robot photographs, plots, or result panels. No figure is required to understand
the present Abstract/Introduction/Method draft.

| Asset ID | Planned manuscript location | Argument carried | Source material | Current status | Claim boundary / next action |
|---|---|---|---|---|---|
| F1 | Introduction, first page | Contrast the available log `(x,y,c)` with signals absent from the dataset, then show that current-policy actions are sampled internally only to center the update. The diagram should visibly separate an environment rollout from model-internal sampling. | E001, E002, E005; `confirmed_motivation.md` | Planned conceptual figure; no source image required. | Draw only after notation is frozen. Do not imply that sampled actions receive rewards or interact with the environment. |
| F2 | Method overview | Two branches at the same logged context: the labeled action and the current-policy sampled action. Both are teacher-forced through current/reference CFM scorers; the second branch forms a stop-gradient reference, and the first enters the signed exact-KTO margin. | E003, E005, E009 | Planned method schematic. | Must label `Delta_CFM` as a surrogate score and `b_theta` as a dynamic surrogate reference, not likelihood ratio or KL. |
| F3 | Method, scale-matched utility subsection | Plot `1-sigma(beta m)` and its gradient magnitude for representative beta values after normalizing the horizontal axis in raw CFM-margin units. This visual explains fixed utility amplitude versus changing margin temperature. | E009-E011 | Derivable analytical plot; not generated in this phase. | Use the final audited beta values. Avoid importing empirical margin distributions into this analytical panel. |
| A1 | Method | Pseudocode for policy-centered reference estimation and a unary update. | E002-E005, E008-E012 | To be typeset directly from the final algorithm, not an external asset. | Include shared CFM randomness, stop-gradient, distributed averaging if used, and optional anchor loss only after implementation audit. |
| T1 | Method or appendix | Notation table for `x`, `y`, `c`, `pi_ref`, `pi_theta`, `Delta_theta`, `b_theta`, `m`, `lambda`, and `beta`. | Method blueprint | Planned LaTeX table if page budget permits. | Keep terms consistent between ICLR- and RSS-facing versions. |
| F4 | Deferred Results | Compare policy-sampled, dataset-action, and mismatched rolled-action estimands across checkpoints with uncertainty. | E006-E008; `016_*`; `022_*` | Source numbers exist; excluded from current prose and figures. | Recreate only from raw machine-readable artifacts and exact manifests, not by transcribing summary tables. |
| F5 | Deferred Results | Show raw margin, beta-scaled margin, exact-KTO effective gradient, held-out CFM quality, and checkpoint selection. | E011, E015; `023_*`-`026_*` | Historical diagnostic sources exist; exact-KTO panel not yet available. | Softplus-run diagnostics cannot be relabeled as exact-KTO evidence. |
| T2 | Deferred real-robot evaluation | Matched robot comparison with raw counts, durations, denominators, rates, uncertainty, and workload/checkpoint controls. | E013-E014 | Preliminary summary only; paper-grade table unavailable. | Double-grab and return rate are lower-is-better. Do not include until metric definitions and matched protocol are audited. |
| F6 | Deferred RSS-facing first page | Actual robot/task sequence or wide deployment image showing the physical setting. | User deployment archive, not yet supplied to PaperSpine | Missing. | Use an anonymized real asset only; do not generate a synthetic robot scene as evidence. |

## Current drafting decision

The partial manuscript will not reference a nonexistent figure. F1-F3 and A1
remain planned assets until the method notation and implementation details are
audited. This keeps the current text compilable and prevents a decorative
pipeline from substituting for evidence.
