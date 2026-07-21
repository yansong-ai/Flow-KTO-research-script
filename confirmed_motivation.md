# Confirmed Motivation

## User Confirmation

- Confirmation date: 2026-07-15 (Asia/Shanghai).
- Fixed title: **Flow-KTO: Learning Flow-Based Robot Policies from Unary Feedback**.
- Controlling option: **Option A, Policy-Centered Unary Flow Optimization**.
- Supporting role of Option B: real-robot operational value and later closed-loop validation.
- Supporting role of Option C: estimator semantics, margin dynamics, and optimization diagnostics.
- Objective choice: **exact KTO**, using the original `1 - sigma` utility form rather than a negative-log-sigmoid or softplus surrogate.
- Metric direction confirmed by the user: lower double-grab rate is better; lower reflow rate is better.
- Writing order confirmed by the user: Introduction, Related Work,
  Preliminaries, Method, Experiments, and only then Abstract and Conclusion.
- Introduction narrative contract confirmed by the user: state the problem;
  review existing methods and explain their mismatch; state the proposed
  response; conclude with itemized core contributions. Variable names,
  notation, and formal definitions belong in Preliminaries rather than the
  Introduction.
- Current drafting scope: Introduction only. Related Work follows after the
  Introduction is accepted; Method, Experiments, Abstract, and Conclusion remain
  deferred. Any earlier abstract prose is provisional and must not be treated as
  accepted manuscript text.

## Controlling Motivation

Real-world robot deployment produces feedback on trajectories that the policy actually executes. For each encountered context, this feedback may provide one executed trajectory and one unary quality judgment, but no reproducible same-context alternative, rewarded candidate group, or new on-policy interaction for the subsequent optimization stage. At the same time, the terminal action density of a multi-step flow-based robot policy is not directly exposed to the likelihood-ratio objectives used by many policy-optimization methods. The paper is therefore motivated by one question: **can a pretrained flow robot policy be directly post-trained from unary feedback collected during real-world deployment, without collecting additional robot interactions for optimization or learning a reward/value critic?**

## Governing Principle

The method should express policy improvement in the policy's native flow-matching training space and center that improvement against actions sampled internally from the current policy. Unary desirable or undesirable labels then determine which side of the policy-centered reference point should receive utility. The utility retains exact KTO's bounded sigmoid form, while the CFM score and its policy-sampled reference provide the tractable quantities required by a multi-step flow policy.

## Narrative Hierarchy

1. **Primary problem:** direct post-training under fixed, one-trajectory-per-context unary feedback.
2. **Primary method response:** a reference-relative CFM improvement score and a current-policy-sampled dynamic surrogate reference point.
3. **Objective:** exact KTO utility, `lambda_y - lambda_y sigma(beta m_y)`, with the label determining the signed centered margin.
4. **Supporting mechanism:** score-scale handling, estimator variance control, and margin-aware optimization diagnostics.
5. **Validation role:** later demonstrate closed-loop robot improvement and preserve held-out imitation quality under a controlled protocol.

## Framing Constraints

- Do not define Flow-KTO as `FPO + KTO`, `based on FPO and KTO`, or a flow extension of KTO.
- Present the problem, derive the required score and policy-centered reference, then state the exact relationship to KTO, FPO, Diffusion-KTO, RKO, and CrossVLA in Related Work or a method-relation paragraph.
- Do not claim that PPO, GRPO, and DPO all require paired preferences. Their data and estimator requirements must remain distinct.
- Do not claim that all policy-gradient methods fail for DiT, diffusion, or flow policies.
- Call the CFM quantity a reference-relative CFM or ELBO-related improvement score unless an exact likelihood-calibration result is available.
- Call the policy-sampled quantity a dynamic surrogate reference point, not an exact KL divergence.
- Do not claim statistical significance, general real-world superiority, or a lower double-grab/reflow rate until the corresponding controlled evidence is presented.

## Current Evidence Boundary

The project already contains estimator comparisons, strict held-out diagnostics, beta/margin analyses, a direct user observation of clear whole-robot action improvement, and BOT154/BOT159 operational comparisons. These materials justify the problem, method design, and a bounded empirical motivation. They do not yet justify an abstract-level claim of statistically controlled superiority. During the current three-section drafting phase, evidence may be previewed only at the strength already recorded in `user_supplied_real_robot_evidence.md` and `sota_gap_map.md`; the Experiments and Validation prose remains unwritten.
