# Flow-KTO Motivation and Contribution Options After Research

## Research Consensus

The reviewed literature does **not** support the broad claim that flow/DiT policies cannot be optimized with reinforcement learning. It also does not support saying that DPO, PPO, and GRPO all require paired data. Their actual mismatches with this project are different:

- DPO canonically requires a preferred/dispreferred pair for the same context.
- PPO requires rewarded trajectories and an advantage estimator, typically from new policy interaction or a sufficiently supported offline alternative.
- GRPO requires rewarded groups of candidates for the same context.
- Critic/value approaches can be viable offline, but require transitions, rewards/outcomes, coverage, and an auxiliary value-learning assumption.

The defensible project setting is narrower: a fixed collection of real-robot trajectories, one unary quality label per logged trajectory/context, no new environment rollout for training, and an implicit multi-step flow policy whose exact terminal action likelihood is not directly available.

The closest novelty threats are KTO, Diffusion-KTO, RKO, FPO, CrossVLA, MoRE, ARM, RECAP/`pi0.6*`, and Learning while Deploying. In particular, RKO already applies unary Diffusion-KTO to a real-world visuomotor diffusion policy, so Flow-KTO cannot claim to be the first unary-feedback robot diffusion/flow method.

## Evidence Already Available

- The project distinguishes policy-sampled, dataset-action, and mismatched rolled-action CFM reference estimates and shows that they target different quantities; policy-sampled and rolled estimates can even have opposite signs.
- Policy-sampled estimates have been compared with 4096-sample references; 112-sample estimates are approximately centered but retain meaningful variance.
- Strict multisite held-out probes show that mean imitation/CFM quality can remain healthy while label-specific negative margins and saturation become excessive.
- The softplus objective admits a clear beta/LR gradient analysis, and recent beta/LR runs provide suggestive but confounded stability evidence.
- The user directly observed a clear improvement in complete real-robot action behavior.
- BOT154 and BOT159 records each report `+221/h` throughput over their stated release baselines; reflow is numerically lower in both records. These comparisons currently have unmatched durations and incomplete protocol metadata.

## Mandatory Technical Decision

The original KTO loss minimizes `lambda - lambda*sigma(margin)`. The documented Flow-KTO implementation/proposal uses `-log sigma(margin)`, equivalently a softplus loss. These objectives have different gradients and saturation behavior.

Before confirming the contribution, choose one scientifically explicit route:

1. **Exact-KTO route:** implement/evaluate original sigmoid KTO as the primary objective and treat softplus as an ablation or variant.
2. **KTO-inspired route:** retain softplus, define its utility and gradient on its own terms, and compare it directly with exact KTO. The title may remain `Flow-KTO`, but the paper must not claim that the implemented objective is unchanged KTO.

No motivation option below removes this requirement.

---

## Option A — Policy-Centered Unary Flow Optimization (Recommended)

### Controlling motivation

Real-robot improvement data often provide only one logged trajectory and one quality judgment for a context. Existing paired, grouped, on-policy, or critic-based routes impose additional feedback or modeling assumptions, while a flow policy does not expose the terminal action likelihood needed by standard ratio objectives. The central question is whether such a policy can be improved directly from unary offline feedback by defining and centering policy improvement in its native flow-training space.

### Candidate core contribution

> Flow-KTO formulates direct post-training of a pretrained flow robot policy from fixed unary trajectory labels, using a reference-relative CFM improvement score and a current-policy-sampled dynamic surrogate reference point, without collecting new environment interactions or learning a reward/value critic.

### Contribution hierarchy

1. **Primary:** restricted-feedback direct post-training for a pretrained flow robot policy.
2. **Technical:** a policy-sampled, teacher-forced dynamic reference estimator that is explicitly different from dataset-action and mismatched estimators.
3. **Supporting:** score calibration and a validated margin-aware stability protocol.
4. **Empirical:** controlled real-robot improvement while preserving held-out imitation quality.

### Why this is not an A+B story

The narrative begins from a missing information structure and derives what must be estimated. KTO, FPO, and related methods are prior solutions to neighboring subproblems; they do not define the paper's object. The paper is judged on whether the policy-centered estimator and restricted-feedback formulation are necessary and effective.

### Evidence still required

- Exact-KTO vs softplus objective control.
- Policy-sampled vs dataset-action vs rolled vs fixed/zero reference training ablation.
- CFM-score calibration or a narrower surrogate claim.
- Same-data/backbone comparison with a faithful unary baseline such as RKO/Diffusion-KTO where feasible.
- Raw, matched, repeated BOT154/BOT159 or equivalent real-robot evaluation.

### Venue fit

- **ICLR:** strongest if estimator semantics, calibration, exact-objective comparison, and cross-setting evidence are completed.
- **RSS:** strong if the same method is paired with complete hardware protocol, matched deployments, and failure analysis.

### Main risk

Without the estimator/objective ablations, reviewers can describe the work as a flow-backbone adaptation of unary generative alignment.

---

## Option B — Learning from Operational Unary Feedback in Real Robots

### Controlling motivation

Deployed robots continuously produce isolated successes and failures, but collecting same-state alternatives, reward-labeled candidate groups, or fresh exploration is expensive and operationally disruptive. The paper asks how to turn those naturally occurring unary labels into a practical policy-improvement loop for a real multi-step flow controller.

### Candidate core contribution

> Flow-KTO converts isolated operational trajectory judgments into direct updates of a flow-based manipulation policy and demonstrates measurable closed-loop improvement without additional environment data collection during optimization.

### Contribution hierarchy

1. **Primary:** an operational data-to-policy loop for fixed unary real-robot feedback.
2. **Method:** policy-centered reference-relative flow scoring.
3. **System evidence:** throughput, return/error behavior, action quality, and failure cases on matched robot deployments.
4. **Practical safeguards:** held-out quality, margin/saturation guards, and early stopping.

### Strength

This option best uses the user's clear whole-robot observation and the BOT154/BOT159 records. It creates a natural RSS story in which data collection constraints, embodiment, deployment, and failures are integral rather than appended.

### Evidence still required

- Metric definitions and desired directions, especially double-grab and reflow.
- Raw counts/denominators and exact checkpoint/config mapping.
- Matched or randomized/interleaved workload and duration protocol.
- Repeated windows, additional robots/tasks where possible, and uncertainty.
- Controls showing the change comes from the objective rather than data, checkpoint selection, speed, or other deployment settings.

### Venue fit

- **RSS:** strongest natural fit after protocol closure.
- **ICLR:** weaker unless the method yields a general estimator or learning insight beyond the deployment case.

### Main risk

RKO already provides unary real-robot diffusion-policy alignment, and critic/value methods address related operational settings. Without controlled method deltas, the paper may be judged as a narrow deployment study.

---

## Option C — Correct Reference Semantics and Margin Control for Flow-Policy Post-Training

### Controlling motivation

When likelihood ratios are replaced with flow-training scores, the reference point and numerical scale become part of the algorithm rather than harmless implementation details. Dataset-action or mismatched estimators can track a different quantity from the current policy, and aggressive negative updates can look healthy under mean held-out loss while harming closed-loop behavior.

### Candidate core contribution

> Flow-KTO identifies and corrects reference-estimation and scale-control failure modes in unary post-training of flow robot policies through current-policy sampling, explicit estimator separation, and margin-aware optimization diagnostics.

### Contribution hierarchy

1. **Primary:** empirical and analytical identification of estimator mismatch.
2. **Technical:** policy-centered reference estimation with variance controls.
3. **Optimization:** objective-specific beta/LR attenuation and guard design.
4. **Validation:** checkpoint-level diagnostics connected to controlled closed-loop outcomes.

### Strength

This is the strongest path under currently documented internal evidence. The sign reversal between estimators and the negative-saturation failure mode are concrete, falsifiable observations rather than broad novelty slogans.

### Evidence still required

- Controlled training with each estimator and exact objective variant.
- Correlation between diagnostics and blinded closed-loop results over enough independent checkpoints.
- Tractable-model check of CFM score/log-ratio agreement.
- Proof that beta/LR coupling adds value beyond lowering LR or early stopping.

### Venue fit

- **ICLR:** plausible as a methodological/analysis paper if the estimator and calibration study is rigorous and generalizes.
- **RSS:** plausible if diagnostics reliably predict or prevent real-robot failures.

### Main risk

The work may be viewed as a debugging/engineering report if it does not yield a reusable learning rule or controlled causal evidence.

---

## Recommended Choice

Choose **Option A** as the manuscript spine, use **Option B** as the real-world significance and validation layer, and use **Option C** as the mechanism/diagnostic support. This keeps one controlling contribution while preserving the strongest real-robot and estimator evidence.

This recommendation is **not a confirmation**. PaperSpine must wait for the user's explicit choice or revision before writing `confirmed_motivation.md` or `confirmed_contribution.md`.

## Items to Confirm with the Choice

1. Select Option A, B, C, or a specific combination with one dominant option.
2. Select the exact-KTO or KTO-inspired softplus route.
3. Confirm whether a higher double-grab rate is desirable or undesirable and define reflow/efficiency.
4. Confirm the baseline-row mapping and exact deployed checkpoint/config for BOT154 and BOT159.
5. Confirm which venue will be the primary manuscript branch once 2027 rules are published; substantially identical ICLR/RSS submissions cannot proceed in parallel.
