# ICLR and RSS Exemplar Learning Dossier

## Scope, Verification, and Evidence Boundary

- Target scene: an ICLR conference paper whose robot-learning evidence should also satisfy RSS-facing expectations; target manuscript: **Flow-KTO: Learning Flow-Based Robot Policies from Unary Feedback**.
- Tier: `pro`. The inventory contains eight fully read exemplars: five local PDFs under `/home/robotera/文档/ICLR_template`, the two user-specified local RSS-facing PDFs `/home/robotera/文档/RSS/Generalizing from References using a Multi-Task.pdf` and `/home/robotera/文档/RSS/DexImit.pdf`, and one additional paper verified against the official ICLR/OpenReview record.
- The local sets are learned separately: `Normal` contains three ICLR 2026 poster papers; `PaperWithAwards` contains two ICLR 2016 papers retrospectively selected by the ICLR 2026 Program Chairs for the **Test of Time Award**. They were not the two ICLR 2016 Best Paper recipients. This distinction matters: the award set reveals durable problem framing, not a different contemporary submission format.
- Two additional neighboring papers requested by the user on 2026-07-16 are focused Introduction reads rather than additions to the fully read exemplar count: REF011/RECAP and REF018/QAM. Their technical assumptions and rhetoric are recorded in `reference_materials/recap_qam_focused_read.md`.
- The two files under `/home/robotera/文档/RSS` are treated as **RSS-facing local exemplars because the user selected them for that purpose**. Their PDF title pages do not state a publication year, venue, or acceptance status. Directory placement, PDF modification times, bibliography years, and two-column formatting are not used as metadata evidence.
- External papers are exemplars of structure, rhetoric, and evidence organization only. Their tasks, results, numbers, conclusions, and claims are **not evidence for Flow-KTO**. Every eventual Flow-KTO empirical statement must trace to user-provided experiments or a verified citation.

## Exemplar Inventory

| ID | Set / status | Verified title | Venue and verification | Contribution narrative learned | Experimental organization learned |
|---|---|---|---|---|---|
| REF001 | **Normal, local** | *Compositional Diffusion with Guided Search for Long-Horizon Planning* | ICLR 2026 Poster. Local PDF: `/home/robotera/文档/ICLR_template/Normal/2601.00126v2.pdf` (38 pages). [Official ICLR page](https://iclr.cc/virtual/2026/poster/10008638); [OpenReview](https://openreview.net/forum?id=b8avf4F2hn). | **Problem:** composing multimodal local distributions averages incompatible modes. **Principle:** long-horizon generation must search for locally compatible modes while propagating global constraints. **Method:** population search, likelihood pruning, and iterative resampling inside denoising. **Evidence:** robot planning first, scaling/ablation next, then panorama and video transfer. | The main claim is tested in increasingly demanding layers: play/stitching benchmarks; hybrid task-and-motion planning; compute scaling; cross-domain stress tests. Each subsection starts with a claim-like sentence rather than a metric name. |
| REF002 | **Normal, local** | *DiffusionNFT: Online Diffusion Reinforcement with Forward Process* | ICLR 2026 Poster. Local PDF: `/home/robotera/文档/ICLR_template/Normal/DIFFUSIONNFT: ONLINE DIFFUSION REINFORCEMENT WITH FORWARD PROCESS.pdf` (22 pages). [Official ICLR page](https://iclr.cc/virtual/2026/poster/10009149); [OpenReview](https://openreview.net/forum?id=VJZ477R89F). | **Problem:** reverse-process policy-gradient formulations inherit likelihood, solver, consistency, and CFG complications. **Principle:** policy improvement can be expressed on the unique forward process by contrasting reward-defined positive and negative generations. **Method:** a forward flow-matching objective with implicit positive/negative policies. **Evidence:** multi-reward training, controlled head-to-head comparison, then design ablations. | Experiments announce three questions up front, then answer them in the same order: broad effectiveness, fair efficiency comparison, and mechanism/design validation. Wall-clock evidence and endpoint quality are reported separately. |
| REF003 | **Normal, local** | *TROLL: Trust Regions Improve Reinforcement Learning for Large Language Models* | ICLR 2026 Poster. Local PDF: `/home/robotera/文档/ICLR_template/Normal/TROLL: TRUST REGIONS IMPROVE REINFORCEMENT.pdf` (40 pages). [Official ICLR page](https://iclr.cc/virtual/2026/poster/10008998); [OpenReview](https://openreview.net/forum?id=X9D5MVpPJ9). | **Problem:** PPO clipping is only a crude proxy for a trust region and can destabilize updates. **Principle:** constrain the object that actually matters, token-level distributional change. **Method:** differentiable KL projection plus a sparse representation that makes the principle computationally viable. **Evidence:** models, sizes, datasets, and advantage estimators, followed by sparsity, entropy, batch-size, and overhead analyses. | Separates setup, aggregate results, and analysis/ablations. Breadth establishes invariance to incidental choices; mechanism probes then rule out simpler explanations such as merely constraining more tokens. |
| REF004 | **Award, local** | *Unsupervised Representation Learning with Deep Convolutional Generative Adversarial Networks* | Published at ICLR 2016; selected for the **ICLR 2026 Test of Time Award**. Local PDF: `/home/robotera/文档/ICLR_template/PaperWithAwards/UNSUPERVISED REPRESENTATION LEARNING.pdf` (16 pages). [Official ICLR award announcement](https://blog.iclr.cc/2026/04/22/announcing-the-test-of-time-awards-from-iclr-2016/). | **Problem:** GANs are unstable and it is unclear whether their internals learn reusable representations. **Principle:** architectural constraints should induce stable training and a semantically organized representation. **Method:** a compact family of architecture rules. **Evidence:** transfer classification, anti-memorization checks, feature visualization, intervention, latent traversal, and vector arithmetic. | Uses multiple evidence types for one enduring claim: quantitative transfer, qualitative generation, internal probes, and controlled intervention. The breadth is not a collection of unrelated applications; each view tests representation quality. |
| REF005 | **Award, local** | *Continuous Control with Deep Reinforcement Learning* | Published at ICLR 2016; selected for the **ICLR 2026 Test of Time Award**. Local PDF: `/home/robotera/文档/ICLR_template/PaperWithAwards/CONTINUOUS CONTROL WITH DEEP REINFORCEMENT LEARNING.pdf` (14 pages). [Official ICLR award announcement](https://blog.iclr.cc/2026/04/22/announcing-the-test-of-time-awards-from-iclr-2016/). | **Problem:** action discretization explodes with control dimension, while naive nonlinear actor-critic learning is unstable. **Principle:** continuous control needs direct action optimization plus slowly changing learning targets and decorrelated experience. **Method:** DDPG with an explicit algorithm and a small set of stabilization choices. **Evidence:** more than twenty control tasks, state and pixel observations, planning comparison, and component removal. | Holds architecture and hyperparameters largely fixed across tasks, so breadth itself becomes robustness evidence. Component removal directly connects claimed stabilization mechanisms to observed learning behavior. |
| REF006 | **RSS-facing, local; venue/year unverified** | *Generalizing from References using a Multi-Task Reference and Goal-Driven RL Framework* | Local PDF: `/home/robotera/文档/RSS/Generalizing from References using a Multi-Task.pdf` (11 pages). The title and authors are visible in the PDF; no publication year, venue, or acceptance line is present, so none is asserted. | **Problem:** reference tracking produces natural motion but is brittle beyond demonstrations, while task-only RL adapts but can lose motion quality and require heavy shaping. **Principle:** treat reference motion as a behavioral-shaping prior rather than a deployment-time constraint. **Method:** one goal-conditioned policy shares observation/action spaces across reference-guided and goal-driven tasks, with a coupled curriculum that shifts training toward generalization as assistance is removed. **Evidence:** nominal and beyond-nominal tests, alternative training paradigms, simulation and hardware, long-horizon skill composition, component ablations, and extensions. | The evaluation announces five questions and answers them in order. It compares the two ends of the motivating trade-off, separates task success from motion quality, distinguishes nominal from out-of-distribution initializations, and uses hardware/composition tests to validate reuse rather than trajectory replay. |
| REF007 | **RSS-facing, local; venue/year unverified** | *DexImit: Learning Bimanual Dexterous Manipulation from Monocular Human Videos* | Local PDF: `/home/robotera/文档/RSS/DexImit.pdf` (12 pages). The title and authors are visible in the PDF; no publication year, venue, or acceptance line is present, so none is asserted. | **Problem:** bimanual dexterous data are scarce, while direct use of abundant monocular human video is blocked by embodiment gaps, reconstruction error, and long-horizon physical interaction. **Principle:** convert video into physically plausible robot data through explicit geometric and action constraints rather than treating the human hand as the robot embodiment. **Method:** Reconstruction–Scheduling–Action–Augmentation, with each stage assigned a distinct failure source. **Evidence:** reconstruction/usability, baseline data quality, task-difficulty stress tests, zero-shot real-system deployment, augmentation ablations, error-source breakdown, and explicit limitations. | Experiments are framed as Q1–Q4: usability, comparative data quality, maximum task difficulty, and real-world deployment. Input-video quality and task difficulty are factorized, the hardware protocol is stated before deployment claims, and the paper closes the loop with module-attributed failures and unsupported cases. |
| WEB-EX-001 | **Official supplement; non-award / top 25%** | *Flow Matching for Generative Modeling* | ICLR 2023 official page labels it “Virtual presentation / top 25% paper” and links the OpenReview record. Full paper read: 28 pages. [Official ICLR page](https://iclr.cc/virtual/2023/poster/11309); [OpenReview](https://openreview.net/forum?id=PqvMRDCJT9t). | **Problem:** scalable diffusion training restricts probability paths, whereas general continuous normalizing flow training is expensive or biased. **Principle:** learn the vector field of a chosen probability path through tractable conditional paths. **Method:** Flow Matching, gradient-equivalent Conditional Flow Matching, and an optimal-transport path instance. **Evidence:** matched-model objective/path ablations, density and sample quality, training/sampling cost, and conditional generation. | Theory and experiments share the same decomposition: first establish objective tractability/equivalence, then compare path choices, then test consequences for accuracy and numerical cost. The supplement is especially relevant for explaining a flow principle without calling it a diffusion variant. |

**Inventory count:** 8 exemplars = 5 local ICLR papers + 2 specified local RSS-facing papers + 1 official ICLR supplement. Only the five local ICLR papers and the official supplement have venue status asserted from explicit PDF/official records; the two RSS-facing rows deliberately leave year and venue unverified.

## Structural Patterns

### Shared Problem–Principle–Method–Evidence Spine

The eight papers vary greatly in age, field, and presentation format, but their strongest shared structure is:

1. **Name a consequential failure, not merely a missing module.** The opening problem is a behavior that matters: incompatible-mode averaging, likelihood/solver coupling, heuristic clipping, unstable GAN training, action-space explosion, or expensive/restricted probability paths.
2. **State a governing principle before listing machinery.** The paper explains what a valid solution must preserve or control: compatibility across horizons, forward-process consistency, bounded distribution shift, stable semantic hierarchy, direct continuous actions with stable targets, or tractable vector-field supervision.
3. **Derive the method as the operational form of that principle.** Equations, algorithms, and components are introduced because each realizes a named requirement. This prevents the method from reading as an inventory of borrowed parts.
4. **Make experiments resolve contribution promises in order.** Main effectiveness comes first; fair comparison or robustness comes next; ablations and mechanism probes explain why; scope or limitations bound the claim.

For Flow-KTO, the intended spine should therefore be:

> **Problem:** unary feedback is easy to collect but does not directly provide paired relative preferences or dense rewards for flow-policy optimization.  
> **Principle:** a valid update must turn independent desirable/undesirable judgments into a calibrated policy-improvement direction while retaining the semantics and tractable training structure of a flow policy.  
> **Method:** define the Flow-KTO objective and training procedure as consequences of that principle.  
> **Evidence:** test unary-feedback use, policy improvement, stability/data efficiency, component necessity, and robot-policy relevance with only user-supported experiments.

The exact technical wording above is a writing constraint, not a scientific claim; it must be reconciled with the confirmed method derivation and available evidence before use in the manuscript.

### Normal Papers: Contemporary Acceptance Pattern

- The three normal ICLR 2026 papers use a compact front-loaded claim. Within roughly two pages, each gives the failure mechanism, a diagram or concrete example, the operative principle, method components, and an empirical preview.
- They explicitly enumerate limitations of the dominant formulation, but the method is narrated as changing the optimization object or inference logic, not as attaching one named algorithm to another.
- Their methods have a two-level structure: a core principle/objective and a practical mechanism that makes it usable. Examples are forward-process improvement plus implementation choices, exact projection plus sparsification, and compatible-mode search plus pruning/resampling.
- Their experiment sections are question-driven. DiffusionNFT literally previews three perspectives; TROLL separates aggregate results from analysis; CDGS moves from core robot planning to scaling and domain stress tests.
- The official supplemental Flow Matching paper follows the same pattern at a more theoretical ratio: objective, tractable conditional form, meaningful path instance, then controlled objective/path comparisons.

### Award Papers: Retrospective Durability Pattern

- The two award papers are **ICLR 2016 papers honored ten years later**, so they should not be treated as templates for current page allocation or reporting requirements.
- Their durable unit is a simple, reusable object: a named algorithm with a small number of stability mechanisms (DDPG), or a named architecture family with explicit design rules (DCGAN). A reader can retain the principle after forgetting individual experimental details.
- Their evidence is deliberately heterogeneous but convergent. DDPG tests task breadth, observation modality, comparison with a privileged planner, and removed components. DCGAN tests transfer, memorization concerns, internal features, intervention, and latent semantics.
- Both introductions begin with field-level stakes, then narrow to one obstruction. This creates a larger arc than the normal 2026 papers, but current Flow-KTO writing should keep that arc concise and quickly expose the unary-feedback bottleneck.
- Historical inheritance language appears in DDPG (the paper openly combines ideas from prior actor-critic and DQN work). Its long-term impact does **not** make “A+B” framing suitable for Flow-KTO. The transferable lesson is the precise problem and stable algorithmic principle, not the historical wording.

### RSS-Facing Section Architecture

The two RSS-facing exemplars place physical feasibility and deployment protocol inside the contribution argument rather than treating them as implementation afterthoughts. Their reusable section architecture is:

1. **First-page capability signal.** The title, abstract, Figure 1, and opening paragraphs show the embodied task, the physical/data bottleneck, and the proposed interface. The figure depicts actual behavior or the end-to-end data path, not a decorative module diagram.
2. **Operational introduction.** Begin with the cost or impracticality of obtaining robot data/feedback, explain why an alternate source is attractive, then identify the embodiment, observability, contact, or generalization gap that prevents direct use. Prior approaches are grouped by what physical assumption they make.
3. **System overview before module details.** State inputs, outputs, deployment-time inputs, shared representations, and the invariant the system must preserve. In *Generalizing from References*, the invariant is one goal-conditioned policy that does not consume reference trajectories at inference. In DexImit, it is physically plausible robot data from monocular video.
4. **Method follows the causal data path.** Each subsection resolves one named failure: behavioral shaping versus reference dependence; reconstruction versus scale/pose ambiguity; scheduling versus bimanual temporal conflicts; constrained action generation versus noisy motion; augmentation versus real-sensor/domain variation.
5. **Experiments begin with research questions and protocol.** State robot/simulator, sensing, tasks, initial-condition ranges, success definitions, baselines, number of trials when available, and whether a result is simulation, sim-to-sim, or real hardware before interpreting performance.
6. **Evidence progresses toward deployment.** Establish component/data usability first, compare alternatives next, stress task difficulty or distribution shift, then report hardware behavior and composition. This order prevents a qualitative hardware montage from carrying an unsupported general claim.
7. **Failure analysis and limitations close the loop.** Attribute failures to pipeline stages or missing capabilities, distinguish estimation error from control/policy failure, and identify unsupported object/task classes. Failure analysis is evidence about scope, not merely future work.

For Flow-KTO, the RSS-facing lesson is not to turn the paper into a long robotics pipeline. It is to make the feedback-collection protocol, policy deployment interface, robot/simulator boundary, trial accounting, and failure attribution as explicit as the loss derivation.

### Recommended Section-Level Architecture for Flow-KTO

| Manuscript unit | Required function | Exemplar-derived constraint |
|---|---|---|
| Abstract | Complete problem → principle → method → evidence chain | Do not open with a taxonomy of KTO, flow matching, and robot policies. State the feedback/optimization obstruction, then what Flow-KTO changes. Use numbers only when supplied by the user's evidence bank. |
| Introduction, opening | Establish why unary feedback matters for robot-policy improvement and identify the exact mismatch | Use one concrete failure/mismatch, as CDGS and TROLL do. Avoid generic “robot learning is important” buildup. |
| Introduction, principle | Explain what an acceptable learning rule must achieve | Make this the conceptual center. It should be understandable without implementation names. |
| Introduction, method preview | Map each method element to a requirement | Prefer “To preserve X, we formulate Y” over a chronological list of components. |
| Background / problem setup | Define flow-policy and unary-feedback objects and assumptions | Include only notation needed for the derivation. Make the feedback protocol and claim boundary explicit. |
| Method | Principle, objective/derivation, implementation, and algorithm | Separate the core objective from practical stabilization or estimation choices, following FM, DiffusionNFT, and TROLL. |
| Robot system / protocol | State embodiment, observation/action interface, feedback origin, data provenance, train/deploy split, and simulator/hardware boundary | Adopt the RSS-facing discipline of declaring what is sensed, labeled, optimized, reset, and measured. Do not let “real robot” stand in for a reproducible protocol. |
| Experiments | Questions and contribution-linked answers | Organize by claims: effectiveness under unary feedback; comparison fairness; robustness/generalization; ablation/mechanism; limitations. Do not organize merely by datasets. |
| Hardware and failure analysis | Separate simulation, offline diagnostics, and hardware evidence; attribute failures at the correct layer | Report task/trial denominators, success criteria, intervention/reset policy, uncertainty, and failure categories when those records exist. Do not infer deployment success from offline probes. |
| Conclusion / limitations | Restate the solved mismatch and bound generality | Do not convert untested settings into future-tense claims. |

## Rhetorical Patterns

### Abstract Moves

Across the ICLR and RSS-facing exemplars, effective abstracts make five moves in a stable order:

1. **Context with tension:** one sentence establishes the capability and the unresolved obstruction.
2. **Failure mechanism:** one or two sentences explain why the dominant formulation fails, often with a concrete technical consequence.
3. **Principled turn:** “We introduce” is attached to a new objective, constraint, or training paradigm, not to a bundle of familiar nouns.
4. **Operational consequences:** two to four properties follow directly from the formulation.
5. **Evidence and boundary:** representative results cover the core claim; broad statements are paired with the tested scope.

The award abstracts are especially economical. DDPG states the continuous-action obstacle, the actor-critic solution, task breadth, planning comparison, and pixel input. DCGAN states the supervised/unsupervised gap, the architecture class, learned hierarchy, and transfer use. The normal papers use more explicit contrast clauses because they must distinguish themselves in denser modern literatures.

### Introduction Moves

- **Funnel through a mechanism, not a literature list.** Strong introductions move from a high-level need to one causal bottleneck. They do not begin with several paragraphs of named methods.
- **Use a diagnostic question sparingly.** DiffusionNFT's forward-versus-reverse question works because the preceding paragraph establishes why it matters. Flow-KTO may use one equivalent question only after defining the unary-feedback mismatch.
- **Pair limitation with design requirement.** “Existing objective requires paired comparisons” should immediately yield the requirement that independent binary judgments must induce a coherent update; it should not merely motivate replacing a loss.
- **Preview evidence as tests of the principle.** TROLL names models, datasets, and estimators to show invariance; Flow Matching names likelihood, quality, and NFE to connect path geometry to consequences. Flow-KTO should similarly state which experiment tests which promise.
- **End with contribution bullets only when orthogonal.** TROLL and DCGAN use explicit enumerations effectively because each bullet has a distinct object and evidence route. Do not split one loss derivation into several inflated contributions.

### Experimental Rhetoric

- Begin the experiment section with 2–4 questions or perspectives and preserve their order in the subsections.
- Give the fairest comparison a dedicated subsection. Match backbone, data, compute, sampling/evaluation protocol, and tuning opportunity wherever the available materials permit; disclose unavoidable differences.
- Follow headline performance with component ablations that correspond one-to-one with claimed mechanisms. An ablation table is not enough if it cannot distinguish the proposed explanation from a simpler alternative.
- Separate **breadth** from **mechanism**. Multiple tasks/embodiments show scope; diagnostics such as stability curves, update statistics, feedback balance, or data efficiency explain behavior. Only include diagnostics actually available.
- Report trade-offs rather than hiding them. CDGS notes visual-quality trade-offs, Flow Matching reports accuracy/cost, and TROLL reports runtime/memory overhead. Flow-KTO should expose any cost, sensitivity, or failure case supported by user results.

### RSS-Facing Rhetoric and Real-System Evidence

- **Name the physical bottleneck concretely.** The RSS-facing papers say what makes data or behavior difficult: teleoperation cost, embodiment mismatch, contact-rich motion, arbitrary viewpoints, temporal coordination, or reference dependence. They do not use “real-world complexity” as a substitute for a mechanism.
- **Resolve a trade-off with a role change, not A+B.** The most transferable sentence logic is: “Rather than treating reference motion as the deployment target, use it as a behavioral prior.” Although the implementation trains two task types, the contribution is the changed role of the reference and one shared policy. This is directly analogous to the required anti-A+B discipline for Flow-KTO.
- **Write experiment subsections as reviewer questions.** “How robust and generalizable...?”, “Which components are necessary...?”, and DexImit’s Q1–Q4 headings define the burden of proof before results are shown. Flow-KTO should use the same device for unary-feedback effectiveness, matched comparison, mechanism, generalization, and deployment boundary.
- **Put protocol before adjectives.** `Robust`, `generalizable`, `zero-shot`, and `real-world` follow the definition of perturbations, training exposure, hardware, sensing, success criteria, and trials. They are not standalone evidence words.
- **Separate evidence channels.** Simulation success, sim-to-sim transfer, offline probes, qualitative sequences, and hardware trials answer different questions. A result must be labeled by channel and cannot silently inherit strength from another channel.
- **Treat failures as structured observations.** DexImit attributes errors to stages and states unsupported manipulation classes; the multitask paper shows how removing imitation, generalization, or curriculum produces distinct failure modes. The rhetorical pattern is `expected mechanism → observed failure when absent → bounded interpretation`.

### Explicit Comparison: Normal ICLR vs. Award ICLR vs. RSS-Facing

| Dimension | Normal ICLR exemplars | Test-of-Time ICLR exemplars | RSS-facing local exemplars | Implication for Flow-KTO |
|---|---|---|---|---|
| Novelty pressure | Explicit contrast against a crowded current baseline family and a precisely named failure mechanism | One memorable capability shift whose principle remains legible years later | A consequential embodied bottleneck tied to data, contact, generalization, or deployment | Use modern comparison precision, retain a one-sentence durable principle, and connect it to an actual robot-learning constraint. |
| Opening signal | Failure example, optimization diagram, and quantitative preview appear early | Broad field goal narrows quickly to one obstruction and one reusable object | Actual robot behavior or system/data path appears on page one with the operational constraint | Figure 1 should expose unary feedback → justified update → policy consequence, with robot context visible but no decorative pipeline. |
| Method presentation | Core objective plus a scalability/stability mechanism; formal derivation and pseudo-code are prominent | Compact named algorithm or architecture with few moving parts | System overview and interfaces first; modules follow the causal/physical path and deployment boundary | Keep the Flow-KTO objective distinct from implementation details, while stating observation/action/feedback interfaces explicitly. |
| Evidence | Controlled head-to-head, extensive ablations, multiple current settings, efficiency/sensitivity | Heterogeneous convergent demonstrations across tasks, modalities, representations, and removed components | Nominal/OOD, simulation/hardware, task success/behavior quality, long-horizon composition, data usability, and physical deployment | Combine fair optimization controls with robotics evidence channels only when user data support each one. |
| Real-system protocol | Often secondary unless the paper is robotics-focused | Historical papers may report less protocol detail than current expectations | Central: embodiment, sensors, environment, initial conditions, success criterion, trials, train/deploy exposure, resets/interventions | State the exact protocol before using `real-world`, `robust`, or `zero-shot`; distinguish offline probes from hardware success. |
| Failure analysis | Ablations and sensitivity isolate optimization mechanisms | Component removal demonstrates the source of stability or representation quality | Failure taxonomy separates reconstruction/data, planning/control, policy, sensing, and unsupported-task causes | Attribute failures at the correct layer; do not use endpoint success alone to claim the proposed mechanism. |
| Rhetoric | Dense limitation lists and explicit contribution enumeration | Broader field arc and simpler conceptual language | Functional, question-led, physically grounded; qualitative sequences support but do not replace metrics | Use the award papers' compression, normal ICLR's reviewer precision, and RSS's protocol transparency. |
| Metadata/status | Official poster/top-25 labels are stated only from official records | Retrospective Test of Time status is separately verified | Year and venue remain unasserted for these two local PDFs because their title pages do not provide them | Never infer publication status from a directory name, file timestamp, citation year, or formatting style. |

## Language Patterns

### Useful Functional Templates

These are rhetorical functions, not sentences to copy verbatim.

| Function | Preferred pattern | Flow-KTO-oriented realization |
|---|---|---|
| State the gap | “However, this formulation requires/induces ..., which prevents ...” | Name the exact information or optimization mismatch created by unary feedback. |
| State the principle | “A suitable update should ... while preserving ...” | Define the two properties the learning rule must jointly satisfy. |
| Introduce the method | “We formulate [name], which expresses ... as ...” | Present Flow-KTO as its own learning principle/objective, not as a port of KTO to flow policies. |
| Explain a component | “To enforce/estimate/preserve X, we use Y.” | Tie each practical choice to a named need in the derivation. |
| State evidence | “We test whether ... by ...” / “Across ..., the method ...” | Map every experiment to a contribution promise and use only user-verified outcomes. |
| Bound a claim | “Under ..., this establishes ...; it does not test ...” | Distinguish simulation/real-robot, task family, feedback noise, and data regime as applicable. |
| Redefine an existing signal | “Rather than treating X as Y, we use X as Z.” | Explain the new role of unary feedback without describing Flow-KTO as KTO plus a flow model. |
| Introduce a robotics protocol | “We evaluate on [embodiment] under [initialization/data/sensing conditions], defining success as ...” | Put hardware, exposure, denominator, and success criteria before robustness/deployment claims. |
| Report a failure boundary | “Failures arise primarily from ..., while the current method does not address ...” | Attribute supported failure categories and name untested/unsupported settings without speculation. |

### Lexical and Sentence-Level Tendencies

- Use concrete technical nouns early: **unary feedback**, **flow policy**, **policy update**, **trajectory**, **desirable/undesirable judgment**, and the exact objective quantities. Avoid repeated generic nouns such as “framework,” “paradigm,” and “approach” without an object.
- Prefer causal connectors: **because**, **therefore**, **to preserve**, **which makes**, **under this constraint**. Use contrast words only when the compared assumptions are explicit.
- Keep one argumentative job per sentence. Long sentences are acceptable for a definition plus consequence, but not for gap, method, four benefits, and a result at once.
- Use active verbs for contribution: **formulate, derive, estimate, constrain, optimize, evaluate, isolate**. Reserve **enable** for a demonstrated capability.
- Use calibrated verbs for evidence: **shows** for direct observation, **supports** for an interpretation, **suggests** for limited evidence. Do not use **proves** for empirical results.
- Prefer claim-bearing subsection titles such as “Unary feedback improves policy quality without paired comparisons” only after the result is verified. Before results are confirmed, use question titles such as “Can Flow-KTO learn from unary feedback?”

### RSS-Facing Language Discipline

- `Real-world deployment` requires an identified robot, sensors/observations, control interface, task setup, checkpoint/data exposure, success rule, and trial accounting. Otherwise use the narrower channel actually tested.
- `Zero-shot` must say zero-shot with respect to what: no real-world demonstrations, no target-object data, no task-specific fine-tuning, or another explicit condition. The word alone is ambiguous.
- `Robust` requires a named perturbation or distribution shift and repeated outcomes. `Generalizes` requires a stated axis such as initial state, target, object, viewpoint, embodiment, task, or physics engine.
- `Physically plausible` should be attached to a test such as collision/contact validity, executable trajectories, policy-learning usability, or hardware execution; visual plausibility alone is insufficient.
- For qualitative robot sequences, write what the sequence demonstrates and what it cannot establish. Use them to expose behavior or failure mode, not to replace denominators and uncertainty.
- Prefer functional robotics verbs such as `reconstructs`, `retargets`, `schedules`, `executes`, `transfers`, `recovers`, and `fails under`; avoid broad adjectives such as `versatile` or `deployable` unless the protocol supports them.

### Prohibited Identity Framing

Do not describe the paper as:

- “KTO based on flow matching,” “a flow-based extension of KTO,” or “KTO applied to robot policies”;
- “combining KTO and flow policies,” “A+B,” “borrowing KTO for flow matching,” or a list of inherited components;
- “the first” unless a complete, current literature audit makes the priority claim defensible;
- “simple,” “general,” “unified,” “principled,” or “theoretically grounded” unless the manuscript immediately states the formal reason and evidence boundary.

A safer identity sentence has the form:

> **Flow-KTO formulates policy improvement for flow-based robot policies when supervision arrives as independent desirable/undesirable judgments, deriving the training objective from that feedback model.**

This sentence is a narrative template. Its technical truth, precise feedback semantics, and derivation must be checked against the user's method materials before inclusion.

## Constraints for Flow-KTO

### Must Carry Forward

1. **One controlling problem.** Center the paper on the mismatch between unary judgments and optimization of flow-based robot policies. Paired-preference cost, sparse reward engineering, or flow likelihood issues may support that problem but should not become competing motivations unless the user's materials establish them.
2. **One governing principle.** Explain how independent feedback defines desirable and undesirable outcomes and what policy change this justifies. The principle must precede named loss terms.
3. **Method-to-requirement mapping.** Every loss component, reference term, weighting, normalization, or stabilization device must answer an explicit requirement or failure mode.
4. **Contribution-to-evidence mapping.** Each major experiment subsection must validate one promise. A provisional matrix is: unary supervision → core task performance; optimization formulation → matched baseline comparison; design choices → ablation; robot-policy relevance → task/embodiment breadth; practicality → data, compute, or stability evidence.
5. **Fairness before breadth.** A matched comparison on the same policy backbone, data, feedback budget, and evaluation protocol is more persuasive than many loosely controlled tasks.
6. **Mechanism after performance.** Once the main effect is established, use available diagnostics to test why it occurs. Do not infer a mechanism from endpoint success alone.
7. **Explicit claim boundaries.** State whether evidence concerns offline/online learning, simulation/real robots, binary/noisy feedback, task generalization, and the exact policy class.
8. **Figure 1 as an argument.** Prefer a concrete feedback-to-update-to-rollout schematic or failure comparison that makes the unary-feedback mismatch visible. It should not be a decorative pipeline of module boxes.
9. **RSS-facing protocol transparency.** When robot evidence is used, state embodiment, observation/action interface, feedback provenance, train/deploy split, tasks, success criteria, trial denominators, uncertainty, reset/intervention policy, and simulator/hardware channel to the extent recorded in user materials.
10. **Failure ownership.** Separate failures caused by feedback construction, objective/optimization, policy execution, sensing, environment variation, and unsupported tasks. Do not attribute every endpoint failure or success to the Flow-KTO objective.

## Focused Neighboring-Introduction Reads

| ID | Technical narrative learned | Introduction structure learned | Transfer boundary |
|---|---|---|---|
| REF011 / RECAP | Sparse episode outcomes become value estimates and binarized advantages; a CFG-related conditioning mechanism extracts an improved flow VLA from demonstrations, rollouts, and interventions. | Starts from the need for practice, presents the complete system loop immediately, then makes value concrete with long-horizon tasks and deployment outcomes. | Transfer the problem-to-system-loop compression. Do not transfer its online data, critic assumptions, results, practice metaphor, or combination-based novelty claim. |
| REF018 / QAM | A TD critic supplies action gradients; adjoint matching converts those gradients into step-wise flow supervision without unstable full-denoising backpropagation. | Frames one tension, groups existing responses by what they sacrifice, tests a tempting CFG-style shortcut and its hidden assumption, then introduces the method as the direct resolution. | Transfer the tension-to-failed-direct-route-to-method logic. Do not imply that Flow-KTO inherits QAM's critic, guarantees, objective, or empirical results. |

These reads change the Introduction comparison axis. The high-value question is
not which alignment algorithms contain unary loss or CFM terms; it is which
intermediary turns deployment feedback into a flow-policy update. RECAP uses a
value/advantage intermediary, QAM uses a critic-gradient intermediary, and
Flow-KTO proposes a direct current-policy-centered CFM intermediary.

## Suggested Evidence Order (Conditional on Available User Results)

1. Experimental questions, feedback construction, tasks, metrics, baselines, and evaluation protocol.
2. Main matched comparison demonstrating whether unary feedback can improve the flow policy.
3. Feedback-regime comparison: unary versus any paired/dense alternatives actually available, with equal annotation or data budgets where possible.
4. Generalization/breadth across tasks, embodiments, or datasets actually tested.
5. Component ablation and optimization diagnostics tied to the derivation.
6. Sensitivity, resource cost, failure cases, and limitations.

This is an organizational recommendation only. Missing experiments must be reported as missing rather than filled with exemplar results or invented values.

## Non-Transferable Items

- **No exemplar result is Flow-KTO evidence.** Do not reuse CDGS robot success rates, DiffusionNFT efficiency ratios, TROLL success gains, DDPG task counts, DCGAN transfer scores, or Flow Matching FID/NFE results as support for Flow-KTO.
- **Do not transfer domains by analogy.** Image rewards, LLM token distributions, GAN representations, and generative-image probability paths may clarify rhetoric, but they do not establish robot-policy effectiveness, unary-feedback validity, or safety.
- **Do not inherit historical “combination” narratives.** DDPG's influence and DiffusionNFT's relationship to earlier NFT work do not license an “A+B” story. Flow-KTO needs its own problem definition, derivation, and evidence chain.
- **Do not copy paper-specific mechanisms.** Population pruning, sparse token projection, target networks, architectural constraints, OT paths, CFG arguments, or positive/negative image policies belong to their source papers unless the user's method independently contains and justifies an analogous object.
- **Do not copy breadth without a common claim.** Cross-domain demonstrations are useful only when every domain tests the same principle. Unconnected robot tasks or benchmark tables will weaken rather than strengthen the narrative.
- **Do not imitate outdated reporting.** The award papers predate current expectations for seeds, uncertainty, compute disclosure, modern baselines, and limitations. Learn their conceptual compression, not their reporting omissions.
- **Do not overread award status.** DCGAN and DDPG are retrospective Test of Time winners, not ICLR 2016 Best Papers. Flow Matching is officially a top-25% ICLR 2023 paper, not an award paper. The three ICLR 2026 local normal papers are official posters; no award claim is made for them.
- **Do not infer RSS publication metadata.** The two selected RSS-facing PDFs teach robotics structure and evidence organization, but their directory location does not verify year, venue, acceptance, award status, or archival publication.
- **Do not transfer hardware evidence.** Humanoid parkour and DexImit real-system demonstrations do not support Flow-KTO's robot performance. They only teach how to report embodiment, sensing, task protocol, robustness conditions, deployment exposure, and failures.
- **Do not convert rhetoric into priority.** Phrases such as “new paradigm,” “first,” “general,” and “unified” require independent verification. Prefer a narrow, falsifiable statement of what supervision is accepted, what objective is derived, and what settings are tested.

## Final Narrative Constraint

The manuscript should make a reviewer able to answer four questions in order:

1. What concrete learning problem does unary feedback create for a flow-based robot policy?
2. What principle turns that feedback into a justified policy-improvement direction?
3. How does the Flow-KTO objective and algorithm realize that principle?
4. Which user-provided experiments validate each promised property, and where does the evidence stop?

If any section instead answers “which two existing methods were combined,” the contribution narrative has drifted and should be rewritten around the problem → principle → method → evidence chain.
