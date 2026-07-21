# Claim Register: Abstract, Introduction, and Method

## Claim policy

`Allowed` means the current evidence supports the stated wording. `Bounded`
means the claim is usable only with the listed qualifier. `Deferred` means it
belongs to the later Experiments/Validation phase. `Prohibited` marks wording
that conflicts with the evidence or the user's framing instructions.

| Claim ID | Planned claim | Status | Evidence / citation anchor | Permitted wording and placement | Required qualifier or test |
|---|---|---|---|---|---|
| C01 | The studied robot log provides one unary-labeled trajectory per context rather than a same-context preference pair. | Allowed | E001 | Abstract, Introduction P1, Method 3.1. | Say `in our setting` or `we study`; do not universalize to all real-world logs. |
| C02 | The optimization stage collects no new environment interaction. | Allowed | E002 | Abstract, Introduction, Method assumptions. | Explicitly distinguish current-policy model sampling at logged contexts from a robot rollout. |
| C03 | Canonical DPO, PPO, and GRPO do not consume the same feedback object. | Allowed | E018; C009, C059, C060, C066 | Introduction assumption comparison. | DPO: pairs; PPO: rewarded trajectories and advantages; GRPO: rewarded groups. Never collapse these into `paired data`. |
| C04 | Flow/DiT terminal action likelihood is not directly exposed to standard likelihood-ratio objectives. | Allowed | E004; C003 | Introduction and Method transition. | Say `not directly available` or `costly/intractable to evaluate`, not `all policy gradients fail`. |
| C05 | Flow-KTO defines `Delta_theta=L_ref-L_theta` as a reference-relative CFM improvement score. | Allowed | E003 | Method 3.2 and Introduction preview. | Use `CFM/ELBO-related surrogate`; do not use `exact reward` or `exact log ratio`. |
| C06 | Under a suitable weighted denoising objective, a CFM-loss difference is related to an ELBO difference. | Bounded | E004; C003 | Method derivation. | State schedule/weighting assumptions and retain the ELBO-gap term; no near-lossless claim. |
| C07 | The dynamic reference is estimated using current-policy actions sampled at logged contexts and scored under current/reference policies. | Allowed | E005 | Abstract, Introduction, Method 3.3. | Call it a `policy-centered dynamic surrogate reference point`; stop gradient through the estimate. |
| C08 | Dataset-action, current-policy, and mismatched rolled-action scores are different estimands. | Allowed | E006-E008 | Introduction motivation and Method 3.3 distinction. | Numerical comparisons are deferred to Results. Dataset-action scoring remains a diagnostic. |
| C09 | The unary objective is exact KTO, `lambda_y[1-sigma(beta m_y)]`. | Allowed as intended method | E009; C001/REF013 | Abstract (`bounded unary utility`) and Method 3.4 with full equation. | Final empirical paper needs a code/checkpoint audit showing the reported runs use this equation. |
| C10 | Flow-KTO uses no pairwise comparison, rewarded group, learned reward model, or value critic in its core update. | Allowed | E001-E002, E018 | Abstract and contribution bullets. | Do not imply that critic-based alternatives are impossible when richer transition/reward information exists. |
| C11 | Holding KTO weights fixed while using `beta` at the `1e2` order makes the sigmoid margin-sensitive at the observed CFM-score scale. | Bounded design claim | E010-E011 | Introduction contribution and Method 3.5. | Present `beta` as inverse margin temperature. Mention the peak-gradient consequence; do not claim causal deployment improvement yet. |
| C12 | Exact KTO provides bounded, two-sided margin-dependent gradient attenuation. | Allowed mathematical claim | E009-E011; REF013 | Method 3.5. | Give the derivative. Do not use softplus's one-sided gradient formula. |
| C13 | Flow-KTO is not defined as FPO plus KTO, or as KTO applied to a flow policy. | Mandatory framing | User instruction; `confirmed_motivation.md`; `style_profile.md` | Controls title, Abstract, Introduction, contribution bullets. | Prior lineage must still be cited honestly in the closest-work paragraph. |
| C14 | KTO, Diffusion-KTO, RKO, FPO, and CrossVLA already cover adjacent components or settings. | Allowed | E016-E018; C001-C008 | Introduction closest-work paragraph. | Explain the exact assumption delta; do not hide prior overlap or use it to define the paper as a combination. |
| C15 | Initial real-robot deployments showed a clear change for the better in whole-robot action behavior. | Deferred under the current writing scope | E013 | Excluded from the current Abstract and Introduction. | Reintroduce only when the controlled evaluation and exact checkpoint mapping support a result sentence. |
| C16 | Flow-KTO improves throughput by `221/h` on two robots. | Deferred | E014 | Excluded from Abstract/Introduction/Method. | Requires raw counts, matched duration/load, definitions, uncertainty, and checkpoint mapping. |
| C17 | Flow-KTO improves double-grab rate and return rate. | Prohibited with current records | E014 | Do not write. | Double-grab worsened numerically in both supplied comparisons; return rate improved numerically. Both are lower-is-better and conditions are unmatched. |
| C18 | Policy-centered estimation causes better robot performance than fixed/data/mismatched references. | Deferred | E006-E008 | Do not write as a result. Method may state the semantic reason for choosing it. | Requires same-data, same-backbone controlled estimator ablation. |
| C19 | Scaling `beta` from `1e-2` to `1e2` causes stable or superior optimization. | Deferred | E010-E011, E015 | Do not write as an empirical conclusion. | Requires exact-KTO factorial comparison; historical beta/LR evidence used softplus and has confounds. |
| C20 | Flow-KTO is the first unary alignment method for robot diffusion/flow policies. | Prohibited | E016-E017; RKO | Do not write. | RKO directly blocks this priority claim. |
| C21 | `Delta_theta` is an exact likelihood ratio or `b_theta` is an exact KL divergence. | Prohibited | E003-E005 | Do not write. | A tractable likelihood-calibration study would be required even for a stronger approximation claim. |
| C22 | All policy-gradient methods fail for flow or DiT policies. | Prohibited | E004, E018; FPO and denoising-MDP work | Do not write. | State only the missing information and likelihood interface for the studied objective/data regime. |
| C23 | Historical softplus runs empirically validate exact KTO. | Prohibited | E009-E011, E015 | Do not write. | Exact equation and checkpoint provenance must be audited separately. |
| C24 | Optional behavior-cloning/CFM anchoring preserves pretrained competence. | Deferred / implementation-only | E012 | Method may define the regularizer and its purpose without claiming an effect. | Preservation requires held-out and closed-loop evidence; exact batch composition must be audited. |
| C25 | Naive end-to-end backpropagation through the multi-step flow generation process can yield unstable gradients in the studied post-training setting. | Bounded | E019; explicit user instruction | Abstract problem sentence and Introduction flow-policy motivation. | Say `can yield unstable gradients` and keep the setting qualifier. Do not generalize this to every flow/diffusion optimizer or use it to imply C22. |
| C26 | RECAP and QAM are the two highest-priority adjacent flow-policy extraction routes for the current Introduction. | Allowed as a scoped comparison | E020; C037; C068 | Introduction and Related Work may compare RECAP's value/advantage-conditioned extraction with QAM's critic-gradient adjoint matching. | State their assumptions exactly. RECAP uses richer demonstrations, autonomous rollouts, interventions, a value function, and binarized advantages. QAM uses transition rewards, TD critic learning, and critic action gradients. Do not claim either route is inapplicable merely because the present objective avoids a critic. |

## Manuscript-level claim contract

The current draft may promise a method and a future controlled test, but it may
not use preliminary deployment observations to certify the estimator or scale
mechanism. The strongest present scientific claim in the Method is structural:
Flow-KTO turns a fixed unary-labeled trajectory into a signed, policy-centered
CFM margin and optimizes the exact bounded KTO utility without a learned critic
or new environment interaction.
