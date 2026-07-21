# SOTA Gap Map: Offline Binary-Label Post-Training for Flow Robot Policies

> Research-stage artifact (Agent C, SOTA Mapper)  
> Tier: `pro`  
> Literature cutoff represented by the supplied local corpus: 2026-07-14  
> Controlling motivation: real-robot logs commonly provide one offline policy trajectory per observation/context, with one per-trajectory quality label; training must not require new environment rollouts.

## Gap Summary

The defensible gap is narrower than "flow policies cannot be optimized with RL" and narrower than a combination of two existing algorithms. The allowed local technical corpus and the narrow public novelty check already cover all of the following separately:

- unpaired desirable/undesirable alignment (KTO; Diffusion-KTO), including a real-robot visuomotor diffusion-policy study (RKO, `WEB001`);
- CFM-loss differences as an ELBO-related policy-ratio surrogate (FPO), including paired DPO on a flow VLA (CrossVLA, `WEB005`);
- online flow/diffusion policy gradients (FPO, LaST-R1);
- trajectory-level mode-label editing of Diffusion Policy and pi0.5 (MoRE, `WEB004`);
- offline or offline-to-online improvement of flow-based robot policies using critics, value functions, advantage conditioning, or adjoint matching (`pi0.6*`/RECAP, QAM, LWD);
- offline robot policy refinement using denser progress/advantage annotations (ARM).

The unresolved conjunction in the reviewed corpus is:

> **Directly post-train a pretrained multi-step flow-matching robot policy from a fixed dataset of unpaired, per-trajectory binary quality labels, without learning a reward/value critic and without collecting new environment interactions, while estimating a current-policy-centered reference point from model-internal samples and controlling the scale and saturation of the CFM surrogate.**

This is a data-regime and estimator gap, not proof of a universally superior RL objective. The user reports a clear, practically salient action-quality improvement in the complete real-robot closed loop and supplied two operational comparisons with higher throughput; these observations support the premise but do not yet close the controlled empirical gap because raw tables, metric definitions, matched conditions, uncertainty, and broader replication are missing.

## Task Boundary and Algorithm Distinctions

Let `x` denote the logged observation/context, `y` the single logged action chunk or trajectory, and `b in {desirable, undesirable}` its quality label. Sampling `y' ~ pi_theta(.|x)` inside the policy at a logged `x` is model computation; it is **not** a new environment rollout because no transition or reward is queried from the robot.

| Method family | Signal and sampling actually required | Relevance to this setting |
|---|---|---|
| DPO | Canonically consumes an offline pair `(x, y_w, y_l)` and optimizes the preferred-vs-dispreferred log-ratio difference. It does not require on-policy rollouts, but it does require paired alternatives (or a separately justified unpaired variant) and a tractable/approximated policy ratio. | One labeled `y` per `x` does not supply the canonical DPO pair. This is a data mismatch, not a statement that all DPO-like methods are impossible. |
| PPO | Collects trajectories from the current/behavior policy, obtains rewards, and estimates per-step advantages, commonly with a learned value function and GAE. It does not require several candidates for the same `x`. | Standard on-policy PPO is unavailable without fresh rewarded trajectories, but offline actor-critic or advantage-learning alternatives may still be viable if transition/reward coverage is adequate. |
| GRPO | Canonically samples a group of candidates for the same prompt/context, evaluates their rewards, and forms group-relative normalized advantages without a PPO-style learned critic. | The logged dataset has neither rewarded current-policy groups nor reward access for newly sampled action candidates. Internal samples can estimate a reference point, but cannot produce GRPO advantages without rewards. |
| KTO | Consumes unpaired binary feedback. Its theoretical reference point is current-policy-centered `D_KL(pi_theta; pi_ref)`; the paper's practical implementation uses a biased mismatched-output microbatch estimate. | The feedback format fits, but the original likelihood ratio is unavailable and its practical reference estimator is especially questionable for continuous robot actions. |
| Offline Q/value methods | Learn returns or action values from transition structure, outcome rewards, and sufficient behavioral coverage; examples in the allowed local corpus include RECAP and LWD. | These methods are not categorically ruled out. They are competing approaches when complete transitions and reliable terminal outcomes support value learning, but impose a critic/value-model and coverage assumption absent from a direct binary-utility objective. |

Accordingly, the paper must not say that "all policy-gradient methods fail for DiT/flow policies." FPO and denoising-MDP methods demonstrate otherwise. The precise limitation is that the user's fixed feedback corpus lacks the on-policy rewards, group samples, or paired alternatives required by particular estimators, while exact terminal action likelihood remains intractable.

## Deep-Read Literature Scope

The following PDFs were converted with `pdftotext` and inspected at the abstract, formulation, objective/algorithm, experiments, ablations, discussion/limitations, and relevant appendices. This exceeds the requested six-paper minimum.

| Source | Paper | Directly relevant finding |
|---|---|---|
| REF013 | **KTO: Model Alignment as Prospect Theoretic Optimization** (ICML 2024; arXiv:2402.01306v4) | Establishes unpaired binary alignment and a current-policy KL reference point. In practice it avoids slow policy sampling by scoring mismatched outputs shifted within a microbatch, clamps the estimate at zero, and stops gradient through it. Its KTO utility is sigmoid-based, not negative-log-sigmoid. |
| REF014 | **Aligning Diffusion Models by Optimizing Human Utility** / Diffusion-KTO (NeurIPS 2024) | Extends KTO to per-image binary feedback by using a tractable local reverse-diffusion transition ratio at a sampled denoising step. It retains the unrelated-pair reference estimate. Its ablation explicitly treats `U(x)=sigma(x)` (KTO) and `U(x)=log sigma(x)` (loss-averse) as different objectives. |
| REF015 | **Flow Matching Policy Gradients** / FPO (arXiv:2507.21053v2) | Uses `exp(L_CFM,old-L_CFM,theta)` in a PPO-style on-policy objective. The derivation is through weighted denoising loss and an ELBO, not an equality between raw CFM MSE and exact log likelihood. It requires rewarded rollouts and advantages. |
| REF008 | **ARM: Advantage Reward Modeling for Long-Horizon Manipulation** (arXiv:2604.03037v2) | Performs offline robot refinement using tri-state segment labels, a learned reward/progress model, reconstruction, and advantage-weighted BC. It demonstrates that offline robot improvement is possible, but with denser annotation and an auxiliary reward model. |
| REF009 | **LaST-R1: Reinforcing Robotic Manipulation via Adaptive Physical Latent Reasoning** (arXiv:2604.28192v3) | Its LAPO/PPO training is online: the appendix reports 512 sampled trajectories per RL iteration, sparse terminal rewards, a value head, and GAE. It is not evidence that a single offline label suffices for PPO. |
| REF010 | **Learning while Deploying: Fleet-Scale Reinforcement Learning for Generalist Robot Policies** (arXiv:2605.00416v2) | Improves a flow VLA with distributional value learning and Q-learning via adjoint matching. Its offline stage uses demonstrations, historical success/failure rollouts, play data, sparse rewards, and a critic; its main result additionally uses a 16-robot online fleet. |
| REF011 | **`pi0.6*`: a VLA That Learns From Experience** | RECAP pretrains and iteratively improves a flow VLA through a learned value function and binarized advantage conditioning using demonstrations, autonomous rollouts, and interventions. It is a high-priority domain competitor, including an offline policy-improvement stage. |
| REF018 | **Q-learning with Adjoint Matching** (ICLR 2026; arXiv:2601.14234v4) | Uses TD critic learning and adjoint matching to transform critic action gradients into step-wise supervision for a multi-step flow policy. It avoids direct backpropagation through the optimized denoising chain while retaining full policy expressivity, but requires transition rewards, a learned critic, and critic action gradients. |
| REF012 | **EXPO-FT: Sample-Efficient Reinforcement Learning Finetuning for Vision-Language-Action Models** (arXiv:2605.25477v1) | Uses online, off-policy Q-learning, edited action candidates, reward detectors, and human interventions. It shows that flow-VLA likelihood intractability does not eliminate all RL routes, but violates the no-new-rollout constraint. |

All files under `/home/robotera/文档/ICLR_template/` and `/home/robotera/文档/RSS/` are excluded from this SOTA map as technical evidence. They may teach venue structure, but the user explicitly separated target-scene examples from domain/core evidence. A later systematic novelty audit may retrieve an underlying work independently from an official/public source and then add it to the source index.

## Supplementary Public Novelty Check

The following directly overlapping works were retrieved from public arXiv records because they were missing from the allowed local technical corpus. They are used only where the inspected full text supports the comparison. They must be added to the formal source index and citation bank before manuscript drafting.

| ID | Public source | Verified overlap and boundary |
|---|---|---|
| WEB001 | Moletta, Welle, and Kragic, **Preference Aligned Visuomotor Diffusion Policies for Deformable Object Manipulation**, arXiv:2602.09583 / RA-L 2026 record, https://arxiv.org/abs/2602.09583 | Applies Diffusion-KTO per-sample binary labels to real-world visuomotor DDPM policies and proposes RKO. It uses curated preferred/dispreferred strategy demonstrations (60 winning and 60 losing demonstrations per preference setting), not the proposed current-policy CFM MC reference point or the same fixed operational-rollout setting. |
| WEB002 | Kim et al., **Preference Alignment with Flow Matching**, NeurIPS 2024, arXiv:2405.19806, https://arxiv.org/abs/2405.19806 | Learns a separate preference flow from paired less-/more-preferred outputs and uses it at inference; it does not directly post-train the base robot policy from unary labels. |
| WEB003 | Chen et al., **DeformPAM**, arXiv:2410.11584, https://arxiv.org/abs/2410.11584 | Uses multiple sampled actions, human pairwise ranking, Diffusion-DPO, and implicit-reward action reranking for real-world deformable manipulation. It requires paired comparisons and inference-time candidate selection. |
| WEB004 | Wang et al., **Behavior Uncloning: Distilling Mode Redirection into Policy Weights without Inference-Time Steering**, arXiv:2606.29201, https://arxiv.org/abs/2606.29201 | Uses trajectory-level mode labels to edit Diffusion Policy and pi0.5, including real-robot tests. It trains a temporary mode classifier and uses retain/redirect losses rather than a reference-centered unary utility. |
| WEB005 | Liu, **CrossVLA: Cross-Paradigm Post-Training and Inference Optimization for Vision-Language-Action Models**, arXiv:2605.21854, https://arxiv.org/abs/2605.21854 | Uses negative CFM MSE as a surrogate log-probability for paired DPO on pi0.5. It directly precludes claiming that the CFM-MSE surrogate or flow-VLA DPO is new, but it does not solve the unary current-policy-centering problem. |

## Candidate Contribution Map

| Candidate Contribution | What SOTA Already Does | User Evidence | Real Gap | Claim Strength | Risk |
|---|---|---|---|---|---|
| Reference-relative CFM improvement score for labeled robot trajectories: `Delta_CFM=L_ref-L_theta` | FPO already uses a CFM-loss difference as an ELBO-related current-vs-old ratio surrogate. Diffusion-KTO already applies binary utility to a diffusion model. CrossVLA (`WEB005`) already uses negative CFM MSE as a paired-DPO surrogate on pi0.5. | The project computes reference/current teacher-forced losses and obtains label-direction margins across several real-robot checkpoints. Healthy checkpoints preserve strict held-out CFM/BC ratios while moving negative margins. | Apply a **direct reference-centered binary utility objective** to a pretrained flow robot policy under the fixed, unpaired trajectory-label regime, without a critic or environment interaction. The novelty lies in the full data/estimator setting, not in `L_ref-L_theta` alone. | **Medium-low** as a method contribution; **none** for claiming the raw score itself is new. | **High.** A reviewer can characterize it as an obvious transfer of existing score and utility components unless the estimator, calibration, and robot evidence are substantial. |
| Current-policy-sampled, teacher-forced dynamic reference point | KTO's ideal `z0` is already policy-centered, but KTO and Diffusion-KTO practically use shifted/unrelated dataset outputs. The inspected RKO description (`WEB001`) retains a `Q_ref`-style center but does not establish the proposed current-policy CFM MC estimator. FPO does not provide a KTO reference point. | In a matched 1008-sample study, policy-sampled and dataset-action means diverge increasingly by epoch (`+1.05e-5`, `+6.03e-5`, `+7.69e-5`); the gap is concentrated in negative states. On a healthy run at epoch 15, policy-sampled `z0=+6.16e-4` while rolled-action eval gives `-5.05e-4`. Across 64 trials, 112-sample estimates track 4096-sample means but retain material variance. | A practical flow-policy estimator of KTO's intended current-policy reference: sample actions internally from `pi_theta` at logged observations, then score those same actions under theta/reference with paired CFM randomness and stop-gradient. This is distinct from dataset-action and mismatched rolled-action estimators. | **Medium**, and currently the strongest estimator-level contribution. | **Medium-high.** Because `Delta_CFM` is not exact log ratio, this is a policy-centered **surrogate reference point**, not a measured KL. It also adds model sampling cost and requires variance control. |
| CFM score-scale calibration across timesteps, action horizons, dimensions, and model families | FPO derives specific time-weighted denoising losses from expected ELBOs, notes upward scale bias for low-MC exponential ratios, and uses MC count plus clipping. Diffusion-KTO's very different beta scale also illustrates objective-scale dependence. | Existing logs show margins on the order of `1e-3` to `1e-2` and beta values 200/400, but no supplied ablation establishes a calibration map, likelihood correspondence, or invariance across action dimensions/tasks. | A calibrated surrogate whose numerical scale is comparable across flow timesteps and action chunks, and whose calibration is used consistently by the sample score and dynamic reference point. | **Hypothesis only** until validated. Potentially **medium** as a supporting technical contribution. | **High.** Setting the unknown proportionality constant to one and letting beta absorb it is not a calibration result. FPO already supplies much of the theoretical starting point. |
| Coupled beta/learning-rate control with margin-dependent attenuation | KTO already states that beta controls utility saturation and that learning rate is its most sensitive hyperparameter. Sigmoid KTO and the project's softplus loss both have margin-dependent gradients. Diffusion-KTO ablates beta; FPO uses PPO clipping rather than this rule. | The logs derive the softplus negative coefficient `w*beta/(1+exp(beta*d))`. The `beta=400, lr=5e-7` runs show slower early drift than the prior `beta=200, lr=1e-6` run; n20 epoch4 and n16 epoch5/6 preserve strict held-out ratios around `0.976-0.980` with controlled margins. However, the old/new recipes are not a clean beta/LR-only comparison. | A stability protocol that keeps the boundary-scale update `lr*beta` approximately fixed while making already-correct margins attenuate earlier, coupled to raw-margin and held-out guards. This can be a derived design rule, not a claim to invent saturation. | **Medium** analytically for the stated softplus implementation; **weak** empirically. | **High.** Data, labels, quota, and checkpoint timing confound the present comparison. Changing beta also changes every beta-scaled saturation threshold and changing LR weakens the BC anchor. |
| No-new-environment-rollout learning from one unpaired quality label per logged trajectory | KTO and Diffusion-KTO match the feedback format outside robotics; RKO (`WEB001`) already applies unary Diffusion-KTO to real-robot visuomotor policies. RECAP and LWD improve flow robot policies offline but rely on transition rewards plus learned Q/value functions and broader data mixtures. ARM uses denser tri-state labels and a reward model. MoRE (`WEB004`) uses trajectory mode labels but requires an auxiliary classifier and a different editing objective. | The user reports that action quality improved clearly in the complete real-robot closed loop. Separately, BOT154/BOT159 operational records each show `+221/h` throughput over their release baselines, with return-rate changes of `-0.5/-1.4 pp`; these records are not yet independently verified or controlled. Existing logs document fixed-data training and model-internal scoring. | Demonstrate that direct binary utility post-training is useful when paired comparisons, rewarded groups, a reliable critic, and new environment interaction are unavailable. The distinctive claim must be narrower than unary robot-policy alignment alone. | **Medium** as a problem-setting contribution. **Qualitative field evidence is meaningful but non-statistical; quantitative performance evidence remains preliminary.** | **High.** RKO is a direct novelty threat. If complete outcome-labeled trajectories suffice to train RECAP/LWD-style critics, reviewers may reject the claim that alternatives are inapplicable. Raw operational data and a matched deployment protocol are still required. |
| Margin/held-out guard suite and early stopping for negative over-optimization | KTO's utility saturates; FPO uses clipping; standard RL monitors KL/trust regions. None of these makes the project's exact diagnostic suite a conceptual novelty. | Model C has healthy common held-out ratios (`0.96145` SFSZ, `0.97086` GZYZ) but a much larger negative margin (`0.017725`), Action/Ref (`1.501x`), and beta-scaled saturation fraction (`20.49%`) than A/B. Beta400 checkpoints show strict held-out ratios can stay green while negative tail saturation rises. | A robot-policy-specific safety/selection protocol combining strict held-out CFM, raw label margins, tail saturation, Action/Ref, and positive diagnostics, rather than treating mean BC loss or negative strength as sufficient. | **Medium** as an empirical diagnostic or engineering contribution; **low** as the paper's main novelty. | **Medium.** Teacher-forced diagnostics may correlate poorly with closed-loop behavior; thresholds are beta-, dataset-, and model-dependent. |
| The currently written `-log sigma` / softplus objective as "KTO" | Original KTO minimizes `lambda-v` with `v=lambda*sigma(...)`. Diffusion-KTO explicitly reports `sigma`, `log sigma`, and `-log sigma(-x)` as different utility choices. | The proposal writes `-log sigma`; the July attribution log derives and implements the corresponding softplus gradient. | There may be a useful KTO-inspired one-sided classification objective, but it must be named and justified as a variant, with an exact-KTO control. | **Not claimable yet.** | **Critical.** Calling it original KTO would import theory and prior evidence that do not apply to the implemented loss. |

## Closest-Work Delta

| Closest work | Exact overlap | Decisive delta for the proposed study | Novelty threat |
|---|---|---|---|
| RKO / Preference Aligned Visuomotor Diffusion Policies (`WEB001`) | Per-sample binary Diffusion-KTO objective, reference policy, and real-world visuomotor diffusion-policy evaluation | Uses a DDPM/U-Net policy and curated winning/losing strategy demonstrations. The inspected formulation does not establish the proposed current-policy-sampled CFM reference point or the same one-fixed-operational-rollout-per-observation regime. | **Critical.** It precludes any "first unary-feedback robot diffusion policy" claim. The paper needs a faithful same-backbone/data comparator and must show that current-policy centering and calibration matter. |
| Diffusion-KTO | Per-sample binary feedback, reference policy, utility-centered generative-model alignment, no reward model | Uses tractable local reverse-DDPM transition log ratios and an unrelated-pair baseline for text-to-image data. The proposed study uses a multi-step flow robot policy, a CFM/ELBO surrogate, and current-policy-sampled teacher-forced reference estimation under a fixed robot dataset. | **Very high.** This work precludes claiming the first binary-feedback alignment of an implicit generative model. |
| FPO | Flow-policy optimization without exact terminal likelihood; CFM loss differences stand in for a policy ratio | FPO is on-policy PPO: it collects current-policy environment trajectories and computes advantages. It neither addresses isolated binary offline labels nor a KTO-style policy-centered reference point. | **Very high.** This work precludes claiming the CFM-difference policy score as new. |
| CrossVLA (`WEB005`) | Negative CFM MSE as a surrogate log-probability for DPO on pi0.5 | Uses canonical paired DPO data and has no unary current-policy utility reference point; reported on LIBERO rather than the target operational setting. | **Very high for the score; moderate for the full method.** It precludes claiming CFM-surrogate DPO on a flow VLA as new. |
| KTO | Unpaired binary desirable/undesirable data and a current-policy reference point | KTO assumes tractable autoregressive likelihoods. Its policy sampling is considered too slow, so its implementation uses a biased mismatched-output estimate. The proposed estimator pays model-sampling cost to recover policy centering for continuous flow actions. | **High** for the utility; **moderate** for the estimator implementation. |
| MoRE / Behavior Uncloning (`WEB004`) | Trajectory-level behavior labels, policy-weight editing, Diffusion Policy and pi0.5, real-robot evaluation | Trains a temporary behavior-mode classifier and uses retain/redirect losses. It targets mode suppression rather than reference-centered unary utility and does not establish the same data uniqueness assumption. | **High adjacent threat.** It narrows the claim from binary trajectory-label robot-policy editing to the proposed estimator/objective. |
| Preference Flow Matching (`WEB002`) / DeformPAM (`WEB003`) | Preference learning with flow matching; real-robot diffusion preference learning and action selection | Both require paired preferences. PFM trains a separate preference-flow module used at inference; DeformPAM ranks multiple candidate actions and uses an implicit reward for inference-time reranking. | **Moderate.** They preclude broad first-preference-flow/robot-diffusion claims but do not solve unary direct post-training. |
| `pi0.6*` / RECAP | End-to-end flow-VLA improvement, offline RL pretraining, episode outcome labels, no need for an action likelihood in advantage-conditioned extraction | Learns a value function from large heterogeneous demonstrations, rollouts, and interventions, then conditions the policy on binarized advantages. Its best results use iterative on-robot collection. The proposed objective avoids a value model and targets data where only isolated trajectory quality is dependable. | **Very high domain threat.** A reviewer may ask why RECAP-style value learning is not the correct solution. |
| QAM (`REF018`) | Preserves multi-step flow-policy expressivity while avoiding unstable backpropagation through the full denoising chain | Learns a TD critic from transitions and rewards, then uses the critic's action gradient through adjoint matching. It solves the gradient-transport problem under a critic-based RL formulation, not direct learning from isolated unary trajectory judgments. | **Very high optimization-side threat.** It invalidates any claim that instability forces a CFM utility route and requires a matched critic/adjoint-matching baseline where the data support one. |
| LWD | Offline stage updates an end-to-end flow VLA from terminal success/failure data; QAM handles flow policy extraction | Requires distributional value/critic learning, demonstration/rollout/play mixtures, and ultimately fleet-scale online data. It optimizes action gradients through adjoint matching rather than label-signed reference-relative CFM utility. | **High domain threat.** It narrows the claim to no-critic, restricted-feedback learning. |
| ARM | Offline real-robot refinement and relative advantage supervision | Uses tri-state temporal labels, a reward/progress model, reconstructed dense gains, and weighted BC; it does not directly alter likelihood via a current/reference flow score. | **Moderate.** It is a strong annotation-efficiency and offline baseline if its labels can be produced. |
| LaST-R1 / EXPO-FT | Improve real robot/VLA policies and show viable non-BC optimization routes | They require online interaction, reward detectors, advantages, or value/Q learning. | **Boundary works**, not direct novelty blockers, but they invalidate blanket claims about RL impossibility. |

## User-Provided Closed-Loop Evidence and Boundary

### Qualitative field observation

The user confirms that, in the complete real-robot closed loop, Flow-KTO produced a clear and practically salient improvement in action quality. This is authoritative first-hand project evidence and should be preserved as motivation for a controlled study. The word "clear" describes the user's observed field effect; it does **not** mean statistically significant, randomized, or causally isolated.

### Quantitative operational records

These numbers were supplied directly by the user and have not yet been checked against raw tables, event definitions, or a matched evaluation protocol.

| Robot / model | Evaluation duration | Efficiency | Double-grasp rate | Return rate | Immediate reading |
|---|---:|---:|---:|---:|---|
| Shenzhen SF BOT154 / `Flow-KTO_new_release_0624` | `60:00` vs MIST baseline `153:00` | `887/h` vs release-0622 baseline `666/h` (`+221/h`) | `4.2%` vs `1.8%` (`+2.4 pp`) | `9.4%` vs `9.9%` (`-0.5 pp`) | Throughput is higher and return rate is lower, but durations are unmatched. |
| Shenzhen SF BOT159 / `Flow-KTO` | `77:13` vs baseline `90:00` | `1116/h` vs `895/h` (`+221/h`) | `1.6%` vs `1.0%` (`+0.6 pp`) | `5.2%` vs `6.6%` (`-1.4 pp`) | Throughput is higher and return rate is lower, but durations are unmatched. |

Do not interpret the increased double-grasp rate as beneficial or harmful until the event definition and desired direction are confirmed. Only two robots are represented, and time window, workload, item mix, reset policy, traffic, software/hardware parity, and operator/site effects may be confounded. Paper-grade evidence requires raw counts/opportunities, metric definitions, matched or randomized interleaving, confidence intervals, and replication across robots/shifts/tasks.

### The delta that should lead the paper

The paper should be framed around a **restricted-feedback direct policy-improvement problem**: no rewarded current-policy rollouts, no same-context candidate groups, no paired preferences, and no trusted critic target. The method then uses model-internal policy samples only to estimate where the current policy sits relative to a fixed reference; it does not assign reward to those samples. This distinction is both technically real and easy for a reviewer to test.

The contribution should not be defined as "FPO + KTO." That description concedes that both key ideas are borrowed and hides the most defensible work: estimator semantics, CFM calibration, robot-data constraints, and stable optimization/validation.

The most dangerous novelty objection is now RKO (`WEB001`), not only Diffusion-KTO in text-to-image generation: unary Diffusion-KTO has already been evaluated on real-world visuomotor diffusion policies. Flow-KTO must therefore establish that the flow-native current-policy reference estimator, fixed operational-rollout regime, and scale/stability protocol are substantive rather than a backbone substitution.

## Candidate Mechanism Audit

### 1. CFM relative improvement score

The safe definition is

```text
Delta_CFM(x,y) = L_CFM,ref(y|x) - L_CFM,theta(y|x).
```

It measures reference-relative improvement under a shared teacher-forced forward-noising protocol. It is not automatically

```text
log pi_theta(y|x) - log pi_ref(y|x).
```

FPO justifies a stronger connection only through a correctly weighted denoising objective and an ELBO. For monotonic weighting schedules, including the optimal-transport schedule considered by FPO, the loss corresponds to a negative expected ELBO of noisy data plus a theta-independent constant. For uniform diffusion weighting, the result is stronger for the clean action. Even then, FPO's ratio includes the ELBO gap rather than equaling the exact likelihood ratio. Its low-MC exponential ratio is upward biased in scale, although the paper argues the gradient direction is unbiased under its assumptions.

Consequences for the proposed study:

- use the same flow schedule, loss weighting, action masking, normalization, sampled timesteps, and noise draws for theta and reference;
- call `Delta_CFM` a **relative CFM/ELBO improvement score** unless a calibration experiment supports a likelihood claim;
- do not repeat the proposal's "near-lossless replacement" language;
- distinguish a fixed pretraining reference from FPO's per-iteration rollout policy `theta_old`; a fixed reference does not inherit PPO trust-region semantics.

### 2. Policy-centered dynamic baseline

The candidate estimator is

```text
z_policy = E_{x in B, y' ~ pi_theta(.|x)}[Delta_CFM(x,y')],
```

estimated by sampling `y'` from the current policy and teacher-forced scoring that same sampled action under theta and reference. The scoring randomness should be paired, the estimate should be stop-gradient, and EMA or multiple microbatches should control variance.

It must be kept distinct from:

```text
z_data   = E_{(x,y)~D}[Delta_CFM(x,y)]
z_rolled = E_i[Delta_CFM(x_i,y_{i+1})]  # mismatched action/context
```

`z_data` measures relative fit on logged behavior actions. It can be a useful matched-action diagnostic, but it does not measure where the current policy puts mass. `z_rolled` measures sensitivity to context-action mismatch and can become out-of-distribution. The user logs show the latter can reverse sign relative to policy sampling even in a healthy run. These are different estimands, not interchangeable implementations.

Because `Delta_CFM` is a surrogate, `z_policy` must be called a **policy-centered dynamic reference/baseline**, not an exact KL. The strongest present support is estimator validity: 112-sample trials approximately recover the 4096-sample mean, and policy sampling exposes drift missed by dataset/rolled estimates. The missing support is causal: no controlled result yet shows that training with this baseline improves closed-loop performance over `z=0`, a fixed baseline, or a dataset baseline.

### 3. CFM scale calibration

An unknown score scale cannot simply disappear into beta. The effective logit is

```text
margin_logit = beta * (calibrated_Delta_CFM - calibrated_z_policy),
```

so action dimension, chunk length, masking, flow-time weighting, number of MC samples, and loss reduction all change the effective utility curve. Calibration and beta are therefore statistically coupled.

A credible calibration study should compare at least raw sum, per-valid-dimension mean, flow-time-stratified normalization, and reference-loss/variance normalization. It should test:

- agreement with exact or high-accuracy likelihood ratios on a tractable low-dimensional flow model;
- stability across action horizons/dimensions and noise-time strata;
- rank consistency of theta-vs-reference changes across checkpoints;
- variance and bias as the number of paired `(t, epsilon)` samples changes;
- whether the same beta range transfers after calibration.

Without these tests, calibration is future work, not a completed contribution.

### 4. Beta/LR coupling and margin-dependent attenuation

The July log derives the currently implemented undesirable-example loss as

```text
L_neg_softplus = w_neg * softplus(beta * (r_hat - z0)).
```

For a correctly rejected negative with `d = z0-r_hat > 0`, its update multiplier is proportional to

```text
lr * w_neg * beta / (1 + exp(beta*d)).
```

Holding `lr*beta` constant preserves the boundary-scale update at `d=0` for this objective, while larger beta makes the update decay earlier as a positive margin accumulates. This supports the proposed `beta up, lr down` control rule.

However, original KTO uses a sigmoid utility. For an undesirable example its loss is proportional to

```text
L_neg_KTO = w_neg * (1 - sigma(beta*d)),
```

whose gradient magnitude is

```text
lr * w_neg * beta * sigma(beta*d) * (1-sigma(beta*d)).
```

These are not the same. The original KTO gradient attenuates at both extreme positive and extreme negative margins; softplus approaches a constant beta-scaled force on the badly wrong side. The objective must therefore be fixed or renamed before beta/LR theory is presented.

The present experiment is suggestive but not causal. `beta=400, lr=5e-7` slowed early negative drift and yielded useful early-stop checkpoints, yet the comparison with the prior model also changes data/label details, and the n20/n16 comparison changes quota rather than beta. A factorial control with fixed data, seed protocol, number of label passes, and checkpoint steps is required.

## Evidence Missing/Required

| Priority | Claim to support | Required evidence | Falsifying or claim-limiting outcome |
|---:|---|---|---|
| P0 | The optimized loss is KTO or a justified KTO-inspired variant | Audit the actual code equation; compare exact sigmoid KTO, softplus/log-sigmoid, positive-only BC, unlikelihood, and no-reference variants under identical data and steps. | If softplus is retained without outperforming/being more stable than exact KTO, the KTO theoretical framing should be removed and the method described as binary reference-centered classification. |
| P0 | `Delta_CFM` carries policy-ratio information | On a tractable flow model, compare calibrated CFM differences with exact/high-accuracy `log pi_theta-log pi_ref`; report correlation, ranking error, sign error, calibration curve, and MC uncertainty. | Weak or unstable agreement limits the method to a heuristic teacher-forced score objective; no likelihood/KL language is permissible. |
| P0 | Policy sampling is the right dynamic reference estimator | Controlled training ablation: policy-sampled vs dataset-action vs mismatched rolled-action vs `z=0` vs fixed/logit baseline, with equal compute where possible. Report estimator bias/variance and downstream stability. | If policy sampling does not improve stability or outcomes, it remains a diagnostic rather than a method contribution. |
| P0 | No-new-rollout training improves the robot policy | Freeze the dataset before optimization; audit the raw BOT154/BOT159 records and metric definitions; then evaluate untouched initial conditions/tasks with randomized/interleaved, duration- and load-matched closed-loop trials. Report event counts/opportunities, success, completion time/throughput, double-grasp semantics, return/safety failures, and confidence intervals for reference BC and all method variants. | Teacher-forced loss/margin gains or unmatched two-robot operational comparisons without controlled replication do not support a general policy-improvement claim. |
| P1 | CFM calibration is necessary and transferable | Cross-task/horizon/dimension comparison of raw and calibrated scores; pre-register one calibration rule and test it on held-out tasks/model scales. | A task-specific recalibration or beta sweep for every setting limits the contribution to tuning heuristics. |
| P1 | Coupled beta/LR causes margin self-regulation | Factorial study with beta-only, LR-only, coupled constant-`lr*beta`, and baseline settings; fixed dataset, quotas, label passes, seeds, and checkpoints. Track raw margins, effective gradient, Action/Ref, strict held-out tails, and closed-loop outcomes. | If coupled runs are no better than LR reduction or early stopping alone, the rule is not an independent contribution. |
| P1 | The restricted feedback regime rules out stronger offline alternatives in practice | Document label provenance and available transitions. Where feasible, compare against RECAP-style advantage conditioning, an offline critic/value baseline, LWD/QAM-style extraction, ARM/AW-BC-style weighting, and simple label-weighted BC. | If a critic/value method works with the same corpus, the motivation must shift from applicability to simplicity, compute, or robustness. |
| P1 | Negative-margin guards predict deployment quality | Correlate pre-deployment diagnostics with blinded closed-loop outcomes across enough independent checkpoints, tasks, and sites; avoid selecting thresholds on the test checkpoints. | If correlations are weak or sign-inconsistent, guards are safety diagnostics only and cannot justify model ranking. |
| P2 | Generality beyond one robot/data recipe | Multi-task, multi-site, multiple initialization/reference models, and at least several independent training seeds; report label balance and action-horizon details. | Single-task/single-run results support only a case study. |
| P2 | Novelty relative to the complete 2025-2026 flow-policy literature | Formally index and re-audit RKO, MoRE, CrossVLA, PFM, DeformPAM, and any original FlowGRPO/DPPO/`piRL`/QAM/DSRL sources retrieved independently from public records, not target-scene copies or secondary descriptions. | A closer method may force a narrower estimator or empirical claim. |

The current logs provide strong diagnostic evidence, and the user provides meaningful qualitative plus preliminary quantitative closed-loop evidence, but the package does not yet contain a controlled paper-grade performance result. In particular:

- strict held-out CFM/BC ratios around `0.976-0.980` show no mean teacher-forced collapse; they do not prove better closed-loop control;
- Model C's high negative margin/saturation is a plausible failure signature, but the supplied materials do not provide a controlled quantitative success-rate curve tying that signature to causality;
- the user's first-hand observation of clearly improved closed-loop actions is valid field evidence but is not a randomized or statistical comparison;
- BOT154/BOT159 each report `+221/h` throughput and lower return rate, but both use unmatched durations, only two robots are represented, and raw counts/definitions/conditions are not yet available;
- the KTO-only and positive-self-anchor queue was still running in the latest supplied status, so no result from it may be claimed;
- historical probe overlap and `use_state` mismatches already invalidated some earlier comparisons, demonstrating why byte-identical manifests and native conditioning must remain hard requirements.

## Falsifiable Claim Boundary

### Claims that are supportable now

1. **Problem statement:** canonical paired DPO, on-policy PPO advantages, and group-relative GRPO require feedback structures not present in the stated fixed corpus. This does not rule out all offline RL or policy-gradient alternatives.
2. **Estimator observation:** in the supplied runs, policy-sampled, dataset-action, and mismatched rolled-action CFM reference estimates target different quantities and can materially disagree, including sign reversal.
3. **Failure observation:** mean held-out teacher-forced CFM can remain healthy while label-specific negative margins and tails become extreme; mean BC fit is therefore not a sufficient deployment diagnostic in these runs.
4. **Mechanism derivation:** for the logged softplus objective, keeping `lr*beta` fixed preserves the boundary-scale multiplier while increasing beta accelerates decay for already-correct positive margin.
5. **Field observation:** the user directly observed a clear action-quality improvement in the complete real-robot closed loop, and the supplied BOT154/BOT159 records each show `+221/h` throughput over their stated baselines. This supports operational promise, not statistical significance or causal attribution.

### Claims that require the P0/P1 evidence above

1. "The calibrated CFM score is a reliable surrogate for a policy log-ratio."
2. "A policy-sampled dynamic reference causes more stable or better robot learning than dataset/fixed baselines."
3. "The coupled beta/LR rule prevents reward hacking rather than merely slowing all updates."
4. "The method causally and generally improves real-robot success or throughput without additional environment rollouts."
5. "The method is broadly effective across flow-policy architectures, tasks, or sites."

### Claims that should not be made

1. "CFM loss difference is a near-lossless or exact replacement for log policy probability."
2. "All policy-gradient methods are impossible for DiT, diffusion, or flow policies."
3. "PPO, GRPO, and DPO all fail because they require paired preferences." Only DPO canonically requires pairs; PPO requires rewarded trajectories/advantages; GRPO requires rewarded groups.
4. "This is the first offline RL method for flow robot policies," "the first binary-feedback method for an implicit generative model," or "the first unary-feedback method for robot diffusion/flow policies." RKO (`WEB001`) directly invalidates the last claim.
5. "`z_policy` is the KL divergence." It is a current-policy expectation of a calibrated surrogate unless exact-ratio validity is established.
6. "Margin-dependent self-decay is novel." It is intrinsic to the chosen sigmoid/softplus utility; the potentially new element is a validated coupled control protocol for this robot-flow setting.
7. "The method is KTO" while optimizing `-log sigma` without qualification. The safe term is **KTO-inspired binary utility objective** until the implementation and exact-KTO ablation are resolved.
8. "The repeated `+221/h` proves general real-world improvement." It is a preliminary two-robot operational observation under unmatched durations and unverified conditions.

### Provisional paper-level statement

A falsifiable, appropriately bounded statement would be:

> We study direct post-training of a flow-matching robot policy from a fixed set of unpaired trajectory-level quality labels, without new environment interaction or a learned reward/value critic. We use a calibrated reference-relative CFM improvement score and estimate its reference point with actions sampled internally from the current policy and teacher-forced under current/reference models. We test whether this policy-centered estimator and a margin-aware optimization protocol improve closed-loop behavior while preserving held-out imitation quality.

This statement deliberately says "we test whether" until the user-provided robot observations are verified under a controlled protocol. If experiments validate it, the contribution hierarchy should be:

1. **Primary:** direct restricted-feedback post-training for pretrained flow robot policies, demonstrated without new environment rollouts;
2. **Technical:** a policy-sampled, teacher-forced dynamic surrogate reference estimator, explicitly separated from dataset and mismatched estimators;
3. **Supporting:** CFM scale calibration and a validated margin-aware beta/LR stability protocol;
4. **Diagnostic:** strict held-out and label-margin guards that predict, rather than merely accompany, closed-loop model quality.

That hierarchy foregrounds the real gap and does not define the work as an existing-method composition.

### Strongest and most dangerous statements

- **Strongest current statement:** policy-sampled, dataset-action, and mismatched rolled-action CFM baselines are different estimands, and the internal studies show that the offline proxies can materially disagree with current-policy sampling, including sign reversal. This directly supports the need to audit reference-point semantics.
- **Most dangerous statement:** Flow-KTO is substantively new relative to RKO/Diffusion-KTO rather than a flow-backbone adaptation. It becomes defensible only if current-policy centering and the scale/stability protocol produce controlled gains over a faithful same-data, same-backbone unary baseline.
