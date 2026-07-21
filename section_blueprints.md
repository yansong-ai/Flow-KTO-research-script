# Section Blueprints: Introduction-First Drafting Sequence

## Scope

- Fixed title: **Flow-KTO: Learning Flow-Based Robot Policies from Unary Feedback**.
- Confirmed writing order: Introduction, Related Work, Preliminaries, Method,
  Experiments, then Abstract and Conclusion.
- Current deliverable: English Introduction only. Related Work is the next
  writing unit after the Introduction is accepted.
- Venue-neutral source: suitable for later adaptation to ICLR 2027 or RSS 2027.
- Controlling contribution: direct post-training of a pretrained flow robot
  policy from a fixed one-trajectory-per-context unary-feedback corpus, using a
  reference-relative CFM score, a current-policy-sampled dynamic surrogate
  reference, and exact bounded KTO at the numerical scale of CFM margins.
- Deferred: Related Work prose, Preliminaries, Method revision, Experiments,
  Validation, deployment protocol, operational tables, Abstract, Conclusion,
  limitations, and venue template integration.

## Whole-work throughline

The reader should encounter one causal sequence:

1. Flow-based policies provide an expressive model of multimodal,
   high-dimensional robot actions.
2. Direct post-training faces two coupled obstacles in the studied setting:
   naive backpropagation through multi-step generation can yield unstable
   gradients, and a deployed observation has one executed trajectory rather
   than same-context alternatives.
3. A valid update must therefore compare current and reference policies in the
   native CFM training space and center that comparison on actions that the
   current policy itself would produce.
4. Flow-KTO realizes this principle with a signed centered CFM margin and exact
   bounded KTO utility. The KTO amplitude is kept fixed; beta is calibrated as
   an inverse margin temperature at the CFM-score scale.
5. The result sentence remains empty until controlled evaluation supports a
   quantitative claim.

The manuscript must remain intelligible if the names KTO and FPO are removed
from its defining sentence. Those names enter through attribution and precise
comparison, not through an `A+B` identity.

## Deferred abstract blueprint

The abstract is written only after the method, experiments, and conclusion have
stabilized. The moves below remain planning notes; they are not an accepted
abstract draft.

**Target length:** 95-120 words before the result sentence, one paragraph, no
citations. The abstract summarizes the paper rather than reproducing its Method
section.

| Move | Planned content | Evidence / boundary | Target check |
|---|---|---|---|
| A1: field background | Locate the paper in flow-based robot policy learning and state what these policies model: multimodal, high-dimensional manipulation actions. | Domain background; E004 | Use one compact sentence, with no generic claim about the importance or future of robotics. |
| A2: coupled problem | State the two obstacles together: naive backpropagation through multi-step generation can yield unstable gradients, and the studied deployment log contains one rollout per physical observation rather than same-context alternatives. | E001, E019; C01, C25 | Qualify the gradient statement and the deployment setting; do not claim that all flow-policy optimization or policy-gradient methods fail. |
| A3: method at paper resolution | Name Flow-KTO and summarize only its governing operation: a bounded, reference-relative update in CFM space, centered on current-policy actions, from unary trajectory labels. State the no-critic/no-new-interaction scope in one short follow-up sentence. | E002-E005, E009; C02, C05, C07, C09-C10 | Omit estimator implementation, stop-gradient, Monte Carlo, beta values, anchoring, and prior-method names. |
| A4: result | End with one quantitative controlled result that identifies the evaluation scope, strongest matched baseline, primary effect, and one competence/safety qualifier. | E013-E015; deferred claims C15-C19 | Keep this slot invisible until the controlled evaluation and checkpoint audit support it; never substitute unmatched deployment observations. |

## Introduction blueprint

**Target length:** 800-1,000 words before final venue compression.

### Move 1. State the problem completely

- Paragraph 1 defines the physical feedback object in ordinary language: one
  executed trajectory and one desirable/undesirable judgment for each logged
  context, with no reproducible same-context alternative.
- Paragraph 2 adds the independent policy-interface constraint: a flow policy
  generates an action through multiple vector-field evaluations and does not
  expose terminal action likelihood as a direct network output. End with the
  paper's single research question.
- Do not introduce variable names, mathematical symbols, equations, or formal
  loss definitions. Those belong in Preliminaries.
- Anchors: E001-E004, E019; claims C01-C04 and C25.

### Move 2. Explain why existing methods do not solve this problem

- Use one compact paragraph to compare DPO, PPO/GRPO, RECAP, and QAM along a
  single dimension: the comparison, interaction, or critic-derived signal each
  update consumes. Give RECAP and QAM one sentence each, sufficient to name the
  intermediary and its data requirement but not to reproduce either method.
- End with the exact boundary: these are viable routes under richer interfaces,
  whereas the paper studies a fixed set of individually judged real-world
  trajectories and constructs none of those intermediaries.
- Reserve RECAP's outcome-to-value-to-advantage-conditioning chain and QAM's
  reward-to-TD-critic-to-adjoint-supervision chain for Related Work.
- Move KTO, Diffusion-KTO, RKO, FPO, and CrossVLA to the standalone Related Work
  section except where exact objective attribution is needed later.
- Anchors: E018-E020; C037, C068; claims C03-C04, C10, C22, C25-C26.

### Move 3. State what this paper proposes

- Paragraph 4 derives the solution principle from the restricted information
  interface, not from the names of prior methods: compare the labeled
  trajectory with a frozen reference in CFM training space, then interpret that
  comparison relative to trajectories generated by the current policy at
  stored contexts.
- Paragraph 5 names Flow-KTO and summarizes the final method in one concentrated
  place: reference-relative CFM scoring, a detached current-policy-sampled
  reference point, label-directed exact bounded KTO utility, and scale matching.
- Use no variable names or formulas. Explain component roles; leave formal
  definitions, signs, expectations, and derivatives to Preliminaries and Method.
- Anchors: E002-E012; claims C05-C13.

### Move 4. Itemize the core contributions

- End with at most three orthogonal contribution bullets:
  1. the restricted-feedback flow-policy problem and direct unary update;
  2. the current-policy-centered CFM reference estimator, distinguished from
     behavior-data and context-mismatched alternatives;
  3. exact bounded KTO calibrated to the CFM-margin scale with separate utility
     and mixing weights.
- Keep contributions conceptual and mathematical, not empirical, until the
  Experiments section supports a result summary.
- Leave a source-only placeholder for the future controlled-results paragraph.

## Preliminaries blueprint

Preliminaries will be written after Related Work and before Method. It owns the
paper's notation and reusable definitions so the Introduction remains a complete
symbol-free narrative.

- Define the fixed unary trajectory dataset and label convention in one notation
  table.
- Define the frozen reference policy, trainable current policy, and context
  distribution.
- Define flow interpolation, the CFM training loss, and the boundary between a
  CFM/ELBO-related score and exact terminal likelihood.
- State the canonical exact KTO utility and its reference semantics before the
  paper introduces the Flow-KTO-specific estimator.
- Do not claim proposed components as background; method-specific choices remain
  in Method even when their symbols are listed here for consistency.

## Method blueprint

**Target length:** 1,900-2,500 words plus equations and one algorithm. The Method
may rely on notation defined in Preliminaries and must not repeat those
definitions. Existing subsection numbers are provisional until Related Work and
Preliminaries are assembled.

### 3.1 Problem formulation: fixed unary robot logs

- Define the labeled set `D_u={(x_i,y_i,c_i)}` with `c_i in {+1,-1}` and at
  most one logged trajectory for each context.
- Define a frozen pretrained reference policy `pi_ref` and trainable policy
  `pi_theta`, initialized from the reference.
- State unavailable information: no same-context alternative, reward for
  internally sampled actions, environment transition during post-training, or
  learned reward/value critic.
- Define optional CFM anchor data separately from the unary corpus; it preserves
  the training interface but is not part of the unary signal.

### 3.2 Flow-native reference-relative improvement score

- Define a general conditional interpolation `y_t=alpha_t y+sigma_t eps` and
  target velocity `u_t=dot(alpha_t)y+dot(sigma_t)eps`.
- Define the masked/normalized CFM loss as an expectation over time and noise.
- State that current and reference models receive identical time/noise draws,
  preprocessing, masks, and reduction.
- Define `Delta_theta=L_CFM_ref-L_CFM_theta`; positive means improved relative
  fit to the scored trajectory.
- Derive the ELBO-related interpretation under a suitable weighted denoising
  objective and retain the model-dependent ELBO-gap term. Never write an exact
  likelihood equality.

### 3.3 Policy-centered dynamic surrogate reference

- Define the target estimand over logged contexts and current-policy actions:
  `b_theta=E_{x~q_D, y_tilde~pi_theta(.|x)} Delta_theta(x,y_tilde)`.
- Give the Monte Carlo estimator using `K` model samples per context and `M`
  paired CFM time/noise samples.
- Apply stop-gradient to the entire reference estimate; the baseline controls
  utility saturation rather than creating a gradient through policy sampling.
- Explain the semantics of `b_data` and `b_mismatch` in one compact contrast.
- State variance-control options only at the level supported by E008; final
  sample count, EMA, clamp, and distributed averaging require implementation
  audit.

### 3.4 Exact unary KTO objective

- Let `s_i=+1` for desirable and `-1` for undesirable, and define
  `m_i=s_i(Delta_i-stopgrad(b_theta))`.
- Define `v_i=lambda_{s_i} sigma(beta m_i)` and
  `ell_i=lambda_{s_i}-v_i=lambda_{s_i}[1-sigma(beta m_i)]`.
- Expand desirable and undesirable forms once to remove sign ambiguity.
- Explain gradient direction: desirable examples reduce current CFM loss;
  undesirable examples increase it relative to the fixed reference.
- Explicitly state that there is no logarithm around the sigmoid.

### 3.5 Matching exact KTO to CFM score scale

- Separate three controls: class utility amplitudes `lambda_D,lambda_U`, an
  outer KTO-to-anchor coefficient `eta_KTO`, and inverse margin temperature
  `beta`.
- Explain the scale problem: beta values around `1e-2` leave `beta m` nearly
  zero for CFM margins around `1e-3`, making utility almost insensitive to the
  learned margin.
- State the design: hold the KTO/class weights fixed and use beta on the `1e2`
  order, selected against the measured score scale.
- Derive `|d ell/dm|=lambda beta sigma(beta m)(1-sigma(beta m))`, its active
  band and peak. This is the exact-KTO dynamic regulator.
- Note that optimizer learning rate and score normalization remain separate
  controls; do not import the historical softplus beta/LR derivation.

### 3.6 Training objective and algorithm

- Define the core unary expectation and, when used, an optional CFM retention
  term on anchor trajectories with a separate coefficient.
- Give an algorithm in this order: draw logged batch; sample current-policy
  actions without environment interaction; score policy samples under current
  and reference with paired CFM randomness; stop-gradient and aggregate the
  center; score unary actions; form signed exact-KTO loss; add optional anchor;
  update theta only.
- State added computation in symbolic terms: policy sampling plus reference
  teacher-forced forwards. Do not assert a measured runtime before evidence is
  available.
- Close with assumptions and non-claims: fixed reference, binary trajectory
  labels, a score whose scale is controlled, no exact likelihood/KL claim, and
  no claim that other RL routes are impossible.

## Citation allocation for the partial draft

| Manuscript claim | Primary citation-bank anchors | Planned BibTeX role |
|---|---|---|
| Paired DPO | C009 | Canonical DPO definition |
| PPO and advantage estimation | C059, C060 | Canonical PPO/GAE assumptions |
| Group-relative optimization | C066 | GRPO group-reward assumption |
| Unary KTO and exact sigmoid utility | C001 | Exact objective and theoretical reference point |
| Unary diffusion alignment | C002, C005 | Diffusion-KTO and closest robot precedent |
| CFM policy-ratio surrogate | C003 | ELBO-related score boundary |
| Paired CFM post-training | C008 | CrossVLA boundary |
| Critic/value robot alternatives | C037, C038, C040, C042, C043 | Assumption comparison, not dismissal |
| Flow-policy background | C021-C026 | Flow matching and robot-policy context |

## Deferred evidence slots

The abstract's preliminary evidence sentence and Introduction I7 are explicitly
provisional. Once the controlled evaluation is available, replace them with a
claim whose denominator, uncertainty, hardware scope, and causal comparison
are supported in the Evidence Bank. Do not fill those slots from exemplar
papers or historical softplus diagnostics.
