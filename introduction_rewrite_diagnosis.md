# Introduction Rewrite Diagnosis

## Decision

The existing Introduction should be replaced rather than sentence-polished.
Its factual ingredients are mostly usable, but their ordering does not make the
method follow from the problem. The rewrite preserves only verified facts,
citations, terminology, and claim boundaries.

## Material logic failures

1. **The opening changes granularity without control.** It moves among an
   action chunk, a trajectory, and a demonstration before defining the actual
   training record. A reader cannot tell whether the unit of feedback is one
   action, one chunk, or a full episode. The rewrite defines the record first as
   `(context, policy-generated trajectory, unary judgment)` and uses that unit
   consistently.
2. **The algorithm comparison is a list rather than an inference.** The old
   paragraph names DPO, PPO, GRPO, and critic-based robot learning in quick
   succession, then treats their distinct missing inputs as one conclusion.
   The rewrite gives each family one symmetric comparison: available feedback,
   required estimator, and the exact missing field in the studied log.
3. **The policy-centered reference appears without its decisive premise.** The
   old text says that a reference point must be evaluated under the current
   policy, but it does not first explain why the logged trajectory score alone
   is insufficient. The rewrite states the missing distinction: a logged score
   measures change for that trajectory, whereas unary utility also needs to know
   where that change lies relative to the current policy's own score
   distribution.
4. **Method-level beta details interrupt the Introduction.** Numerical score
   orders, peak gradients, and two-sided saturation arrive before the reader has
   finished locating the contribution. The rewrite keeps only the design role
   of scale calibration in the Introduction and defers numerical and derivative
   details to Method.
5. **Closest-work positioning becomes a citation inventory.** Listing six
   methods obscures the comparison dimensions and makes Flow-KTO look like a
   component recipe. The rewrite compares adjacent work along three explicit
   dimensions: feedback structure, policy score, and interaction requirement.
6. **The ending speaks in review-process language.** Phrases such as "burden of
   proof" describe how the paper should be judged rather than what the paper
   contributes. The rewrite ends with orthogonal contributions and reserves a
   results paragraph until controlled experiments exist.

## Sentence-level contract for the replacement

- Each sentence performs one primary function: define, distinguish, derive,
  specify, attribute, or bound.
- A connective is used only when the preceding sentence supplies its premise.
- Comparisons name a shared dimension and compare like with like.
- Method names do not define Flow-KTO's identity.
- No empirical effect, exact likelihood, exact KL, priority, or generality claim
  exceeds the confirmed evidence boundary.

## User-confirmed macro revision

The Introduction is now treated as one complete low-resolution narration of the
paper. Its visible order is fixed:

1. state the full problem;
2. review existing methods and explain the exact mismatch;
3. state the proposed response in one concentrated place;
4. itemize the core contributions.

All equations, variable names, sign conventions, expectations, and reusable
formal definitions are removed from the Introduction. They are assigned to a
standalone Preliminaries section between Related Work and Method.

## Focused-comparator revision

The earlier closest-work paragraph remained too broad because it grouped KTO,
Diffusion-KTO, RKO, FPO, and CrossVLA by component overlap. The revised
Introduction instead uses two independent paragraphs organized around policy
extraction in the target subfield:

- RECAP is the feedback-side route: outcome to value to binarized advantage to
  advantage-conditioned flow VLA.
- QAM is the optimization-side route: transition reward to TD critic to action
  gradient to adjoint-matching supervision for the flow velocity field.

The following paragraph synthesizes these as two learned intermediaries and
positions Flow-KTO as a direct route that deliberately constructs neither. This
is a design boundary, not a claim that RECAP or QAM cannot be trained when
richer data are available.
