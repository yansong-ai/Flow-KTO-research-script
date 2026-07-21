# Flow-KTO Style Profile

## 1. Manuscript Identity

- Fixed title: **Flow-KTO: Learning Flow-Based Robot Policies from Unary Feedback**
- Target cycles: **ICLR 2027** and **RSS 2027**.
- Core audience: machine-learning researchers studying policy optimization and generative/flow policies; robotics researchers studying data-efficient real-world policy improvement.
- Source posture: problem and mechanism first; technical lineage is cited and compared in the appropriate sections but must not define the contribution as `FPO + KTO` or `A+B`.
- Evidence posture: distinguish direct observation, controlled comparison, diagnostic correlation, and mechanism hypothesis. Never promote one category into another through rhetoric.

## 2. Controlling Narrative Pattern

The manuscript should follow one causal spine:

1. **Structural data constraint:** each logged observation/context has one offline policy trajectory and one unary quality judgment; the dataset does not contain same-context pairs, rewarded groups, or fresh on-policy interaction.
2. **Optimization obstacle:** the terminal action density of the multi-step flow/DiT policy is not directly available to standard likelihood-ratio objectives.
3. **Principle:** direct policy improvement requires a reference-relative, differentiable score whose update direction is meaningful in the native flow-training space, plus a reference point representing where the current policy places mass.
4. **Method:** define a reference-relative CFM improvement score, estimate its policy-centered dynamic reference from model-internal current-policy samples, and control the score's effective margin scale during optimization.
5. **Validation:** test the objective and estimator against faithful alternatives, then test whether the resulting policy improves closed-loop robot behavior while preserving held-out imitation quality.
6. **Boundary:** no claim of exact likelihood, exact KL, universal RL impossibility, first unary robot-policy alignment, or broad real-world superiority without the required evidence.

The method should still have a coherent identity after deleting the names `KTO`, `FPO`, and `Diffusion-KTO` from the introduction. Those names belong in the prior-art comparison and exact-objective discussion, not in the paper's defining sentence.

## 3. Dual-Venue Profile

| Dimension | ICLR-facing version | RSS-facing version | Shared core |
|---|---|---|---|
| Primary value | General learning principle for unary feedback under an implicit flow policy | Useful and reproducible real-robot policy improvement under a concrete data bottleneck | Same method, derivation, data regime, and claim boundaries |
| Opening emphasis | Information/estimator mismatch and why existing objective assumptions fail | Operational cost of collecting alternatives/rewards and the consequence for deployed robots | One fixed trajectory plus one quality label per context |
| Method burden | Formal score semantics, estimator validity, calibration, exact-objective audit, cross-setting behavior | Algorithm clarity plus complete robot system/data/deployment protocol | Reference-relative CFM score and policy-centered baseline |
| Experiment burden | Matched algorithm baselines, estimator ablations, mechanism, breadth, compute | Hardware trials, matched conditions, denominators, uncertainty, failures, interventions, safety/return metrics | Same-backbone/data controls and real-robot evidence |
| Figure 1 | Unary-feedback mismatch and policy-centered score/reference mechanism, with a bounded robot result | Actual robot task/data loop and concrete before/after behavior, with method inset | Must communicate problem, mechanism, and evidence rather than show decorative modules |
| Main risk | Seen as a transfer of known KTO/CFM ingredients without a new general lesson | Seen as under-controlled deployment tuning or a narrow system case study | RKO/Diffusion-KTO novelty, surrogate validity, and objective mismatch |

Maintain a venue-neutral source until one venue is selected. Do not plan parallel submission of substantially the same paper. ICLR 2027 and RSS 2027 rules were not yet published on 2026-07-14; 2026 rules are planning precedents only.

## 4. Section Profiles

### Abstract

Use five moves in order:

1. Concrete data/optimization problem and stakes.
2. Exact gap in existing feedback or estimator assumptions.
3. Flow-KTO's independent principle and mechanism.
4. Strongest verified controlled and real-robot evidence.
5. Bounded field payoff.

Do not open with `We combine`, `Building on`, `Based on`, a list of prior method names, or generic claims that robot learning is difficult. Do not place the current `+221/h` observations in the abstract until metric definitions, checkpoint mapping, and protocol comparability are verified.

### Introduction

- Paragraph 1: make the real data constraint visible through one concrete collection situation, following RECAP's useful move from deployment experience to the exact learning record without copying its practice metaphor.
- Paragraph 2: frame one joint tension between restricted feedback and multi-step flow-policy optimization, following QAM's use of an explicit technical tension and focused question.
- Paragraph 3: summarize pairwise, on-policy, group-relative, and critic-based alternatives along their required training signals. Limit RECAP and QAM to one sentence each, state that both are viable under their own data interfaces, and leave their full technical chains to Related Work.
- Paragraph 4: derive the required direct comparisons from the fixed unary-feedback interface without making prior method names the subject of the paragraph.
- Paragraph 5: introduce Flow-KTO through its own score, current-policy reference estimator, interaction boundary, and scale mechanism.
- Contribution bullets: use at most three orthogonal units; do not inflate one derivation into multiple claims.

### Background and Related Work

- Define unary feedback, the fixed offline trajectory setting, flow-policy action generation, and reference-relative scoring.
- Treat KTO, Diffusion-KTO, FPO, RKO, Preference Alignment with Flow Matching, DeformPAM, MoRE, CrossVLA, ARM, RECAP/`pi0.6*`, QAM, Learning while Deploying, LaST-R1, and EXPO-FT by their exact assumptions.
- Explain RECAP's outcome-to-value-to-binarized-advantage-conditioning chain and QAM's reward-transition-to-TD-critic-to-adjoint-supervision chain here rather than in the Introduction.
- State relationships explicitly without allowing them to become the narrative subject.
- Include an exact-objective comparison: original KTO uses sigmoid utility, and
  the confirmed manuscript objective is exact bounded KTO. Historical softplus
  runs remain development evidence and cannot validate the exact objective
  until checkpoint/code provenance is audited.

### Method

Recommended order:

1. Problem formulation and available information.
2. Reference-relative CFM improvement score and approximation boundary.
3. Policy-sampled dynamic surrogate reference point; distinguish it from dataset-action and mismatched rolled-action estimates.
4. Unary positive/negative objective, with the exact implemented equation.
5. Score normalization/calibration and beta/LR behavior.
6. Algorithm, sampling/stop-gradient/EMA/distributed details, and compute.
7. What the method does not assume or claim.

Every component must answer a named requirement. Avoid chronological development history in the main method narrative.

### Experiments

Use question-led subsections:

1. Does fixed unary feedback improve the same pretrained flow robot policy?
2. Is policy-centered sampling a better training reference than `z=0`, fixed, dataset-action, or mismatched estimates?
3. Which objective and scale-control choices are necessary?
4. Does the method preserve held-out imitation behavior while changing labeled directions?
5. Does improvement persist in matched real-robot trials, and where does it fail?
6. What compute, sampling, and tuning cost is added?

Report matching dimensions before results: backbone, initialization, reference, data, labels, number of passes, optimizer steps, sampling budget, tuning budget, checkpoint rule, task load, robot, duration, and metric denominators.

### Discussion and Limitations

- Explain the observed mechanism only to the strength supported by estimator and objective ablations.
- Separate score semantics, optimization dynamics, offline diagnostics, and closed-loop behavior.
- Name RKO as the closest unary real-robot diffusion-policy threat and explain the tested delta rather than relying on architecture labels.
- State limits in task/site/robot count, binary-label quality, model family, calibration transfer, and deployment protocol.
- Do not dissolve the central claim with generic future work; state exactly what the current evidence establishes.

## 5. Language Profile

### Preferred language

- Concrete nouns: `real-world robot deployment feedback`, `recorded deployment trajectory`, `stored deployment context`, `unary feedback`, `current-policy sample`, `reference policy`, `CFM improvement score`, `dynamic reference point`, `closed-loop deployment`.
- Active technical verbs: `formulate`, `derive`, `estimate`, `center`, `calibrate`, `compare`, `isolate`, `validate`, `bound`.
- Causal links: `because`, `therefore`, `under this constraint`, `to preserve`, `which requires`.
- Evidence verbs: `observe` for a direct measurement, `show` for a controlled result, `support` for a bounded interpretation, and `suggest` for preliminary evidence.

### Phrases to avoid

- `the studied log`, `this record`, or `the log` when the intended object is
  feedback collected during real-world robot deployment
- `based on KTO and FPO`
- `combining KTO with flow matching`
- `a straightforward extension/application of KTO`
- `all policy-gradient methods fail`
- `PPO, GRPO, and DPO all require paired data`
- `near-lossless replacement of log likelihood`
- `the policy-sampled baseline is the KL divergence`
- `first`, `general`, `unified`, `principled`, or `safe` without an immediately testable definition
- `significant improvement` unless a statistical test and protocol justify that word

### Claim-strength ladder

| Evidence level | Permitted wording |
|---|---|
| User's direct field observation | `we observed a clear improvement in whole-robot action behavior in these deployments` |
| Unmatched operational comparison | `the two recorded deployments show higher hourly throughput under the reported conditions` |
| Matched repeated comparison with uncertainty | `Flow-KTO improves ... by ... under the evaluated protocol` |
| Cross-task/site/model replication | `the effect persists across ...` |
| Formal theorem or validated approximation | `under assumptions ..., the score ...` |

## 6. Figures and Tables

- Figure 1: problem-to-mechanism-to-evidence argument; show the actual robot/task signal when anonymity permits.
- Method figure: distinguish logged labeled action, internally sampled current-policy action, current/reference teacher-forced scoring, and the centered update.
- Estimator figure: policy-sampled vs dataset-action vs rolled-action trajectories across checkpoints, with uncertainty and exact estimand labels.
- Optimization figure: raw margin, beta-scaled margin, effective gradient, Action/Reference loss, and held-out quality; avoid beta-dependent thresholds without raw values.
- Main real-robot table: raw event counts, durations, denominators, rates, confidence intervals, and all matched settings.
- Failure table: sensing/data, feedback, optimization, policy execution, task/environment, and unsupported cases.

## 7. Citation and Attribution Style

- Cite prior work at the precise claim it supports; do not use citation clusters as substitutes for comparison.
- Separate source-derived facts from this paper's results.
- Attribute KTO's theoretical reference semantics, FPO's ELBO-related CFM surrogate, and Diffusion-KTO/RKO's unary generative-policy alignment accurately.
- Acknowledge overlap explicitly in Related Work and the method relation paragraph; novelty comes from the demonstrated problem/estimator/validation delta, not from suppressing ancestry.
- Recheck the official 2027 template and citation convention before final assembly. The target-year venue template overrides planning observations from 2026.

## 8. Final Style Gate

Before any section is accepted, verify:

- The paragraph advances, validates, or bounds the confirmed contribution.
- Its technical subject remains Flow-KTO's problem or mechanism, not a recipe of source methods.
- Every result has an internal evidence anchor and every literature claim has a verified source.
- Offline diagnostics are not used as closed-loop evidence.
- Real-robot statements include the protocol qualifiers required by their strength.
- Exact KTO and the implemented softplus variant are not conflated.
- ICLR-facing generality or RSS-facing physical relevance is earned by evidence, not asserted by style.
