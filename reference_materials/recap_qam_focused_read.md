# Focused Read: RECAP and QAM

## Scope and verification

This focused read was requested on 2026-07-16 to improve Flow-KTO's closest-work
positioning and Introduction structure. It covers each paper's Introduction and
the method/setup passages needed to verify the comparison. It is not represented
as a page-by-page audit of every experiment or appendix.

| ID | Source | Verified document facts | Read scope |
|---|---|---|---|
| REF011 | *pi0.6*: A VLA That Learns From Experience, Physical Intelligence, local 18-page PDF, arXiv:2511.14759 | The PDF describes RECAP and `pi0.6*`; its Figure 1 and method sections state autonomous rollouts, human corrections, value-function training, binarized advantage conditioning, and a CFG-related policy extraction construction. | Abstract, Introduction, Related Work positioning, Preliminaries, and policy-extraction passages. |
| REF018 | *Q-learning with Adjoint Matching*, Qiyang Li and Sergey Levine, ICLR 2026, local 32-page PDF, arXiv:2601.14234v4 | The PDF states that QAM combines TD critic learning with adjoint matching to use critic action gradients for step-wise flow-policy supervision without direct full-denoising backpropagation. | Abstract, Introduction, Related Work taxonomy, Preliminaries, and high-level formulation. |

## Technical comparison

| Dimension | RECAP / pi0.6* | QAM | Flow-KTO boundary |
|---|---|---|---|
| Primary setting | Generalist flow VLA improvement from demonstrations, autonomous deployment experience, and interventions. | Offline and offline-to-online continuous-control RL with expressive flow policies. | Fixed operational robot log with one independently labeled trajectory per context. |
| Feedback/data | Episode outcome labels determine rewards; demonstrations, older/new rollouts, and human corrections are mixed. | Transition tuples with rewards support TD learning; online interaction is also evaluated. | One desirable/undesirable trajectory judgment; no same-context pair or new environment interaction during optimization. |
| Learned intermediary | Multi-task distributional value function and action advantages. | Q-function and its action gradient. | No learned reward, value, or Q critic in the core update. |
| Policy extraction | Conditions the VLA on a binarized advantage indicator. The derivation is closely related to classifier-free guidance, while training uses supervised/flow-matching objectives on all data. | Adjoint matching transforms the critic action gradient into direct step-wise velocity-field supervision, avoiding backpropagation through the optimized denoising chain. | Uses a reference-relative CFM score, a current-policy-sampled dynamic reference point, and label-directed exact bounded KTO. |
| Why it matters as a baseline | Shows that sparse outcome feedback can improve a large flow VLA when richer trajectories, a value model, and iterative robot collection are available. | Shows that ODE/denoising backpropagation instability can be avoided without discarding critic gradients or collapsing the policy to one step. | Flow-KTO must justify the value of the more restricted no-critic/no-new-rollout route, not claim that the alternatives are impossible. |

## Introduction structure learned

### RECAP

1. Opens with the operational premise that mastery requires practice, then
   translates practice into autonomous robot experience.
2. Names the full system immediately and explains the complete data/value/policy
   loop rather than beginning with optimizer details.
3. Makes the payoff concrete through representative long-horizon tasks and
   deployment results.
4. Closes by locating novelty in the integrated recipe and its demonstrated
   system-level effect.

Transfer to Flow-KTO: begin from the feedback that deployment naturally leaves,
then describe the entire learning loop at low resolution. Do not copy RECAP's
practice metaphor, system results, or combination-based novelty claim.

### QAM

1. Opens with one explicit tension: expressive multi-step policies versus
   tractable critic-based optimization.
2. Categorizes existing responses by what they sacrifice, then asks one focused
   research question.
3. Examines a tempting CFG-style noisy-action guidance route and identifies its
   hidden out-of-distribution critic-gradient assumption.
4. Introduces adjoint matching only after the direct alternative has failed,
   then maps each method component to the stated tension.
5. Closes with the technical contribution and the evidence scope.

Transfer to Flow-KTO: organize closest alternatives around the intermediary used
for policy extraction. RECAP constructs value/advantage supervision; QAM retains
a critic and transports its action gradient; Flow-KTO constructs a direct unary
CFM comparison without a critic. This makes the proposed route follow from a
real decision rather than from a list of unrelated alignment papers.

## Claim and experiment consequences

- The Introduction may say that RECAP and QAM provide viable flow-policy
  improvement routes under richer feedback and critic assumptions.
- It may not say that unary outcome labels cannot train a value function: RECAP
  is direct counterevidence when trajectory structure and data coverage suffice.
- It may not say that multi-step flow optimization necessarily requires unstable
  end-to-end backpropagation: QAM is direct counterevidence.
- A matched paper should include, where the corpus permits, a RECAP-style
  advantage-conditioning baseline and a critic/QAM-style baseline. If a critic
  cannot be trained fairly from the available records, the missing transitions,
  rewards, coverage, or implementation dependency must be documented rather
  than asserted.
