# Glossary — Adversarial Structural Security Intelligence (ASSI)

**Version:** v0.1.0 — Research Foundation  
**Status:** Terminology reference for research proposals, draft specifications, and synthetic benchmark designs  
**License:** Apache-2.0 (subject to repository `LICENSE`)  
**Repository placement:** `GLOSSARY.md`

> **Interpretation rule:** A defined term is not a claim of demonstrated effectiveness. The terms below distinguish observed facts, structural hypotheses, governance decisions, and authorized actions. Unless explicitly stated otherwise, the ASSI mechanisms remain research proposals awaiting implementation and independent validation.

## 1. Purpose and conventions

This glossary supplies a common vocabulary for the twelve `ASSI` research articles, six `SPEC` contracts, five `CASE` studies, and four `EXT` explorations. It aims to prevent a recurring class of security errors: promoting a result from one epistemic or authority layer into another without an explicit, independently verified transition.

- **Normative vocabulary:** `MUST`, `MUST NOT`, `SHOULD`, and `MAY` describe intended requirements *within draft specifications*. Their appearance here does not imply conformance certification or a deployed implementation.
- **Research vocabulary:** *Hypothesis*, *proposed*, *candidate*, and *synthetic* identify statements or artifacts that require empirical testing.
- **Identity vocabulary:** *Observed*, *inferred*, *verified*, and *authorized* refer to different assertions and MUST NOT be silently equated.
- **Time vocabulary:** An event's occurrence time, its observation time, the time an assessment was made, and the validity interval of a relationship can differ.
- **Abbreviations:** Expanded on first entry; cross-references use **bold** terms.

## 2. Foundational security concepts

### Adversarial Structural Security Intelligence (ASSI)
A proposed research architecture for representing security-relevant assets, identities, evidence, permissions, threats, tests, residual weaknesses, and governed improvements as interoperable structural units. ASSI combines adaptive intelligence with an independently enforced safety boundary. **ASSI is not a cryptographic protocol or a certified security product.**

### Structural Security
The security properties arising from the arrangement of identities, dependencies, privileges, control paths, assets, information, and recovery mechanisms across a system. It extends beyond the correctness of an individual cryptographic or software operation.

### Cryptographic Validity
Successful verification of a cryptographic property, such as a signature against a public key and message. It does **not** by itself establish the signer's real-world identity, business intent, organizational authorization, or acceptable risk.

### Legitimate Intent
An action purpose supported by the applicable business process and authoritative approval context. Intent requires evidence and policy checks distinct from the mathematical validity of a signature.

### Structural Contradiction
A persistent tension between desirable system properties that cannot reliably be eliminated by optimizing a single local metric. ASSI studies, among others, autonomy versus control, identity observability versus authorization, efficiency versus safety, and open-ended evolution versus stable safety boundaries.

### Trust Relocation
Moving a trust dependency from one component or actor to another without necessarily removing the underlying exposure. For example, transferring custody decisions from a person to a signing service may reduce one risk while introducing concentration in service credentials or operational administration.

### Trust Boundary
A boundary across which assertions, authority, or control must be revalidated. A network or process boundary is not automatically an effective trust boundary; the actual dependency and bypass paths matter.

### Common-Mode Failure
A failure that affects supposedly independent safeguards because they share credentials, administrators, software, infrastructure, data, assumptions, or recovery dependencies. Independence claims require explicit examination of these shared dependencies.

### Attack Surface
The set of interfaces, operations, privileges, dependencies, and pathways that could be used to affect protected assets or security properties. ASSI emphasizes the *structural reachability* of sensitive operations, not just their count.

### Bounded Loss
A design objective that constrains the maximum harm reachable under stated assumptions, including exposure budgets, independent execution controls, and recovery limits. **A claimed loss bound is invalid if its assumptions, including control-plane independence and complete enforcement coverage, do not hold.**

### Structural Exposure
The assets, operations, permissions, or contingent obligations reachable through an authority path. Exposure may include direct transfer value, delegated spending power, privileged configuration changes, and cascading dependencies; it is not always additive.

### Liquidity–Exposure Tension
The conflict between keeping assets readily available for legitimate operations and limiting the assets reachable by compromised or misused authority. Liquidity is an operational capability; exposure depends on the authority graph.

## 3. Structural representation and identity

### Structural Security Unit (SSU)
A typed, versioned, provenance-bearing representation of a security-relevant object, assertion, hypothesis, decision, experiment, or governance event. A proposed canonical envelope includes an identifier, type, schema version, provenance, temporal metadata, epistemic status, lifecycle status, and audit references. See `specs/SPEC-001-Structural-Security-Unit-Contract.md`.

### Universal Typing and Naming (UTN)
A proposed method for assigning typed, scoped identifiers to structural entities and relationships so that observations, inferred subjects, independently verified identities, and authorized principals remain distinguishable. A UTN identifier is a reference, **not proof of identity or permission**.

### Namespace Authority
The entity or governance process responsible for issuing and maintaining identifiers within a defined namespace. Namespace authority does not imply authority over the assets or identities referenced by those identifiers.

### Compositional Identity
A model in which an apparent actor may be a person, subgroup, team, coalition, shared service, delegated operator, or changing combination of these. Membership and control relations may overlap and vary over time. Compositional identity is a hypothesis-bearing structure rather than a forced one-to-one attribution.

### Temporal Compositional Hypergraph
A time-indexed graph or hypergraph representing relationships among multiple entities, roles, and shared resources. Hyperedges can express multi-party relationships; equivalent typed role/activity nodes may be used in an ordinary graph implementation.

### Observed On-Chain Address
A blockchain address present in recorded transactions or events. Its existence and activity may be directly observable, but a real-world controller or organization cannot be concluded from the address alone.

### Inferred Controller
A proposed actor or group believed to exercise control over one or more observed addresses, credentials, or operations. The inference must retain its evidence, uncertainty, alternatives, and temporal scope.

### Independently Verified Identity
An identity assertion corroborated through an independent verification process appropriate to its context. Verification is still distinct from current authorization for a particular action.

### Authorized Principal
An actor, service, or role granted a specific permission by an applicable authoritative policy, subject to scope, validity, conditions, and revocation. Authorization is not inherited from an inferred identity link.

### Identity Hypothesis Portfolio
A maintained set of competing identity explanations, such as one operator, one team, a shared service, or independent actors reacting to a common event. The portfolio allows evidence to discriminate among alternatives without premature global merging or rejection.

### False Merge
An identity-model error that combines distinct controllers or subjects into one when the ground truth requires separation.

### False Split
An identity-model error that divides a genuinely connected controller or composite subject into separate unrelated identities.

### Recomposition
A versioned revision of a compositional identity structure, including membership changes, role reassignment, merge/split proposals, and temporal corrections. Historical evidence and superseded hypotheses must remain traceable.

### Hypothesis-Scoped Contradiction
A principle requiring a contradiction to affect only the precise hypothesis, role, conditions, and time interval actually tested. Refuting “one person controls both addresses” does not automatically refute “one team coordinates both addresses.”

## 4. Evidence, directional reasoning, and feedback

### Evidence Unit
A provenance-bearing record of an observation or derived claim, with source, collection method, time, dependencies, and stated limitations. A derived feature must not be counted as an independent observation when it is computed from the same underlying data.

### Provenance
The traceable history of an assertion or artifact: its source, transformation, dependencies, authorship or process, and applicable versions. Provenance supports auditability; it does not by itself establish truth.

### Epistemic Status
A label describing what is known about an assertion, such as observed, derived, hypothesized, supported, contested, refuted, or validated under a specified test. It must be kept separate from workflow status and authorization status.

### Weak Evidence
Information that modestly discriminates among hypotheses but is insufficient for a decisive conclusion. Weak evidence may be useful when its relevance, alternatives, dependence, and limitations are explicit.

### Directional Evidence
Evidence whose significance depends on the hypothesis, task, perspective, or direction of inquiry. A pattern can be relevant to one hypothesis while offering little information about another.

### REN — Relational Evidence Navigation
A proposed mechanism for navigating relational and directional evidence across structural hypotheses. REN combines context-sensitive relevance, alternative explanations, evidence dependence, and provenance. It is not an identity oracle and does not turn correlation into causation.

### Metric Similarity
A measure of likeness between objects or patterns under a chosen representation and metric. Similarity alone cannot establish shared control, legitimate authority, or a causal relation.

### Directional Field
A context-dependent representation of which differences or relations matter for a particular hypothesis or decision. A directional field can guide investigation, but its scores must be empirically calibrated before probabilistic interpretations are claimed.

### Evidence Dependency Graph
A structure recording which evidence items, transformations, tests, and conclusions depend on which underlying observations. It helps detect duplicate counting, correlated features, and circular support.

### Evidence Laundering
A failure mode in which a claim gains apparent credibility by being repeatedly copied, summarized, or endorsed by dependent agents or sources without new independent evidence.

### BCEF — Bidirectional Conditional Evidence Feedback
A proposed framework that tests conditions in multiple directions and returns structured impacts on hypotheses, scores, relationships, and next investigations. It distinguishes **Forward IF**, **Reverse IF**, **Counterfactual IF**, and **Contradiction IF**. See `docs/ASSI-006-Bidirectional-Conditional-Evidence-Feedback.md` and `specs/SPEC-003-Bidirectional-IF-and-Evidence-Impact-Contract.md`.

### Forward IF
A conditional test asking what observable consequences would be expected if a specified hypothesis and its preconditions held. Failure to observe a predicted consequence is not automatically decisive unless observability and other assumptions are established.

### Reverse IF
A diagnostic test asking which hypotheses could explain an observed consequence. The inference from `H → E` to `E → H` is not logically valid without additional assumptions and comparison with alternatives.

### Counterfactual IF
A test asking how expected observations or outcomes would change under a specified hypothetical intervention or altered condition. Counterfactual conclusions require a justified model; they are not direct observations.

### Contradiction IF
A test asking whether evidence is incompatible with a specified hypothesis under declared conditions. A contradiction must be scoped and its provenance retained.

### Four-Valued Assessment
An assessment model distinguishing **SUPPORTED**, **REFUTED**, **CONFLICT**, and **UNKNOWN**. `CONFLICT` means meaningful support and refutation coexist; `UNKNOWN` means the available information is insufficient. Neither should be silently collapsed into a confident binary verdict.

### Evidence Impact
A structured proposed consequence of an evidence test: for example, revise a score, split a hypothesis, reclassify a relation, correct a time interval, or request more evidence. An impact is not automatically an authorized mutation or deployment decision.

### Scoring Tree / Scoring Forest
A structured arrangement of factors, perspectives, dependencies, and scoring operations. ASSI uses such structures to organize evidence and hypotheses while guarding against duplicated support and inappropriate authority promotion.

### Structural Feedback
A proposed update to the structure of a reasoning model, not merely to a numerical score. Structural feedback can revise nodes, edges, dependencies, hypothesis scopes, or evidence requests, subject to validation and audit.

### Metric Differential Tree (MDT)
A structural representation of differences or changes across versions, states, or time. In ASSI it can track changes in evidence, identity, policy, exposure, and governance, rather than replacing authoritative audit records.

### Circular Evidence Reinforcement
A failure mode where a conclusion is reused as evidence for itself, often through recursive scoring or multi-agent repetition. Dependency tracking and independent evidence requirements are intended to prevent this.

## 5. Authorization and independent safety

### Independent Safety Control Plane
A separately governed mechanism that enforces hard operational constraints regardless of adaptive model scores or recommendations. Its independence must be evaluated against shared failure modes, privileged administrators, bypass paths, and deployment dependencies.

### Adaptive Intelligence Plane
The component that interprets evidence, proposes hypotheses, recommends decisions, and generates improvements. It may advise, but must not unilaterally authorize actions or rewrite non-bypassable safety constraints.

### Policy Decision Point (PDP)
A component that evaluates a proposed action against authoritative policies and returns a policy decision. Independence from the proposing system matters when the PDP is relied upon as a safety boundary.

### Policy Enforcement Point (PEP)
The mechanism that prevents an operation unless the authoritative decision and its binding conditions are satisfied. A PEP is effective only if all consequential execution paths are covered.

### Authorization Request
A typed description of a proposed action, its actor, target, business purpose, amount or scope, contextual evidence, and validity constraints. It is a request for evaluation, not evidence of permission.

### Canonical Transaction Binding
A mechanism that ties an approval to an unambiguous representation of the intended transaction, including destination, amount, operation, parameters, policy version, and expiry where applicable. It prevents a valid approval from being repurposed for a materially different execution.

### Risk Budget / Exposure Budget
A governed allowance for specified classes of consequential actions over a defined interval or context. Concurrent updates require atomic or otherwise provably safe accounting to avoid double spending of the budget.

### Fail-Closed Behavior
The rule that an action is not executed when necessary authorization or safety checks are unavailable, invalid, or inconclusive. Fail-closed design can affect availability and requires explicit operational recovery plans.

### DENY / HOLD / ESCALATE / ALLOW
Proposed authorization outcomes: reject an action, pause pending a condition, require additional independently authorized review, or permit execution under exact conditions. These are policy outcomes, not evidence confidence labels.

### Separation of Duties
A governance property requiring distinct parties, processes, or independently controlled roles for incompatible responsibilities, such as proposing an action and approving its own deployment.

### Recovery Boundary
The independently controlled capabilities needed to freeze, revoke, restore, or roll back affected operations after a security event. Recovery is part of the security architecture and may itself have common-mode failure risks.

### Authority Drift
A cumulative change in effective permissions through successive small modifications, where individually plausible changes collectively create a previously prohibited execution path. Evaluation requires comparing authority reachability across versions, not merely checking each edit in isolation.

## 6. Adversarial experimentation and structural relay

### Adversarial Drive
A bounded, authorized experimental role that generates challenges, defenses, evaluations, or governance decisions within a defined scenario and resource budget. A Drive is not permission to attack real systems.

### Red Drive
The role that proposes adversarial hypotheses and tests within an authorized, isolated environment. Its outputs are candidate findings requiring independent evaluation.

### Blue Drive
The role that proposes or implements candidate defensive measures in a controlled test setting. Its success claims require evaluation outside the Blue role.

### Evaluation Drive
An independent role that assesses evidence, test validity, performance, confounders, and failure conditions. Independence must include scrutiny of shared data, models, and evaluation incentives.

### Governance Drive
The role that authorizes experimental boundaries, reviews proposed changes, and controls promotion, rollback, and accountability. Governance approval is distinct from experimental success.

### Competitive Relay
A structured transfer of scenarios, claims, counterclaims, tests, residuals, and improvement proposals among competing and cooperating roles. Accepting a relay artifact does not validate its evidence or authorize its deployment.

### Structural Relay
The transfer and reuse of typed, provenance-bearing intelligence units across tasks, agents, versions, or domains. The recipient must check semantics, evidence, compatibility, and authority boundaries.

### Security Residual
A documented weakness, unexplained failure, uncertainty, uncovered scenario, or governance gap remaining after a test or defense. A residual is a research input, not automatically a confirmed exploitable vulnerability.

### Residual Registry
A versioned collection of Security Residual units with provenance, severity assumptions, ownership, test status, related hypotheses, and follow-up actions.

### Synthetic Sandbox
An isolated test environment with generated or otherwise explicitly authorized data and assets. A synthetic result can test an architectural hypothesis but cannot by itself prove real-world security.

### Ground Truth
The reference labels or states used to score an experiment, especially in synthetic datasets. Ground truth must be protected from models or evaluators when leakage would invalidate a test.

### Baseline
A simpler or alternative method against which a proposed mechanism is compared under matched conditions. Examples include signature-only checks, static rules, address clustering, or unstructured agent collaboration.

### Ablation Study
An experiment that removes or disables a component while keeping other conditions as comparable as possible, to estimate the component's incremental contribution.

### Conformance Invariant
A property that a conforming implementation must preserve, such as provenance retention, hypothesis scope, bounded budgets, or independent authorization. Draft invariants need executable test definitions and independent implementation checks.

### Test Vector
A specified input, precondition, expected outcome, and rationale used to assess a contract or implementation. Negative vectors test forbidden transitions and unsafe edge cases.

### Benchmark Families BM-001–BM-004
The proposed ASSI evaluation groups: **BM-001** compositional identity; **BM-002** BCEF evidence revision; **BM-003** authorization and bounded loss; and **BM-004** adversarial relay and validated RSI. These are *planned* benchmark programs, not reported experimental results.

## 7. Questioning, learning, and governance

### AQSI — Autonomous Questioning Structural Intelligence
A proposed mechanism for generating, prioritizing, testing, and relaying research questions from structural factors, evidence gaps, history, and residuals. A question is not evidence, and an answer is not authorization.

### Question Unit
A typed research object specifying the question, context, competing hypotheses, discriminating evidence, test plan, risk boundary, priority, and lifecycle status.

### Information Value / Value of Information
The anticipated benefit of obtaining evidence that could change a hypothesis ranking or consequential decision, weighed against cost, uncertainty, and risk. It should not be interpreted as a calibrated numerical quantity without validation.

### Question Portfolio
A selected set of questions balancing expected information gain, diversity, coverage, risk, and experimental cost rather than optimizing only a single high-scoring question.

### Validated Recursive Self-Improvement (Validated RSI)
A proposed governed cycle in which residuals generate questions and improvement candidates, which undergo independent testing, policy review, and controlled promotion. **“Validated” describes the required process, not a claim that a particular improvement has passed it.**

### Candidate Improvement
A proposed change to a model, evidence process, policy, test, architecture, or recovery procedure. It is not an accepted improvement until its declared claims survive appropriate validation.

### Promotion Gate
An independently governed decision boundary controlling whether a tested candidate may advance to another environment or level of operational consequence.

### Rollback
A governed return to an earlier approved state, including restoring policies, versions, permissions, or configurations where feasible. Rollback feasibility and recovery time must be tested rather than assumed.

### Recursive Budget
A limit on the depth, duration, number of iterations, computational cost, or risk of recursive exploration. Exhausting a budget must not grant the system permission to bypass safety constraints.

### Evaluation Contamination
A condition where a candidate system obtains information about supposedly independent tests, or where evaluators share biases or data that compromise the credibility of performance claims.

### Reward Hacking / Metric Gaming
Optimizing an evaluation score in a way that fails to improve the intended security property, including exploiting weaknesses in a simulator or benchmark.

### Open-Ended Security Evolution
A research direction exploring ongoing generation of new questions, structures, defenses, and governance approaches without presuming a fixed endpoint. Open-ended learning must remain subordinate to independently maintained execution boundaries.

### Governance of Governance
The explicit process for reviewing and changing the rules that govern security decisions. Changes to governance must themselves be authorized through a distinct and accountable procedure.

### Collective Structural Learning
The accumulation and exchange of typed, testable, provenance-preserving knowledge across participants or agents. Independent disagreement, negative results, and failed transfer attempts are valuable inputs.

## 8. Cross-domain transfer

### General Structural Defense Kernel (GSDK)
A proposed reusable set of structural representation, evidence reasoning, experimentation, and governance interfaces for different security domains. Its portability does not imply portable security guarantees.

### Domain Adapter
A domain-specific mapping from general structural concepts to the target environment's assets, identity semantics, policies, actions, and recovery processes. Domain adapters must not silently infer permissions from superficial structural similarities.

### Cross-Domain Structural Security Transfer (CDSST)
The proposed process of transferring hypotheses, mechanisms, tests, and lessons between security domains while independently validating mappings and target-domain constraints.

### Canonical Transfer Unit (CTU)
A proposed typed record describing a source concept, target mapping, assumptions, unsupported correspondences, evidence, validation status, and governance disposition.

### Typed Partial Mapping
A cross-domain mapping that explicitly permits some source concepts to remain unmapped. It is safer to record a missing correspondence than to fabricate a false equivalence.

### Negative Transfer
A transfer that worsens security, validity, or performance because source-domain assumptions do not hold in the target domain. Such failures should be recorded rather than hidden.

### Non-Transfer Register
A structured record of mappings or mechanisms found unsuitable for particular targets, with reasons, evidence, and conditions under which re-evaluation might be justified.

### Multi-Agent Adversarial Security Ecology (MA-ASE)
A proposed system of interacting security agents and organizations that compete, cooperate, challenge evidence, and relay findings under bounded authority and explicit governance. More agents do not automatically produce more independent evidence.

### Autonomous Security Questioning and Exploration (ASQE)
An ASSI extension applying AQSI to discover and investigate security questions through authorized, bounded experiments. Exploration rights are narrower than production execution rights.

### Open-Ended Security Evolution and Governance (OESEG)
An ASSI extension studying how security knowledge, structures, defenses, and governance can evolve while preserving independent safety boundaries and monitoring authority drift.

## 9. Essential non-equivalences

These distinctions should be preserved in research text, contracts, implementations, benchmarks, and governance reviews.

| Do not equate | With | Why the distinction matters |
|---|---|---|
| Valid signature | Legitimate business intent | Compromised signers can produce valid signatures |
| Observed address | Real-world controller | On-chain activity does not identify a person or organization by itself |
| Inferred identity | Verified identity | Inference may be uncertain, composite, or time-limited |
| Verified identity | Authorized principal | Verification does not grant permission |
| Metric similarity | Shared control or causation | Similar patterns can arise from common services or triggers |
| Missing evidence | Contradictory evidence | Non-observation depends on observability assumptions |
| Reverse IF explanation | Logical proof | `H → E` does not imply `E → H` |
| Local contradiction | Global hypothesis rejection | Scope, role, and time must be preserved |
| Repeated reports | Independent corroboration | Dependent sources may repeat one underlying claim |
| High model score | Permission to act | Only independently governed policy can authorize execution |
| Relay acceptance | Evidence validation | Transporting a claim does not establish its truth |
| Evidence validation | Deployment authorization | Operational consequence requires a separate approval |
| Simulation success | Real-world safety | Models omit conditions and can be gamed |
| Proposed improvement | Validated improvement | Candidate benefits must survive independent tests |
| Local policy compliance | Global bounded loss | Bypass paths and common-mode failures can invalidate a bound |
| Cross-domain analogy | Safe domain transfer | Target semantics and authority rules may differ |
| Multiple agreeing agents | Independent evidence | Agents may share data, models, or errors |
| Research specification | Certified implementation | A written contract is not proof of conformance |

## 10. Abbreviation index

| Abbreviation | Expansion | Primary use |
|---|---|---|
| ASSI | Adversarial Structural Security Intelligence | Overall research program |
| SSU | Structural Security Unit | Typed structural artifacts |
| UTN | Universal Typing and Naming | Typed identity and naming |
| REN | Relational Evidence Navigation | Directional weak-evidence reasoning |
| BCEF | Bidirectional Conditional Evidence Feedback | Conditional tests and impact feedback |
| MDT | Metric Differential Tree | Structural change tracking |
| AQSI | Autonomous Questioning Structural Intelligence | Question generation and exploration |
| RSI | Recursive Self-Improvement | Governed candidate improvement cycle |
| PDP | Policy Decision Point | Independent policy evaluation |
| PEP | Policy Enforcement Point | Execution constraint enforcement |
| GSDK | General Structural Defense Kernel | Proposed cross-domain kernel |
| CTU | Canonical Transfer Unit | Typed transfer record |
| CDSST | Cross-Domain Structural Security Transfer | Transfer research program |
| MA-ASE | Multi-Agent Adversarial Security Ecology | Multi-agent security extension |
| ASQE | Autonomous Security Questioning and Exploration | Security-questioning extension |
| OESEG | Open-Ended Security Evolution and Governance | Open-ended evolution extension |
| BM | Benchmark | Planned experimental family |
| SPEC | Specification | Draft normative contract |
| CASE | Case study | Synthetic scenario or experimental design |
| EXT | Extension | Exploratory research direction |

## 11. Where to find the canonical discussion

| Theme | Research | Contract | Synthetic case / extension |
|---|---|---|---|
| Structural validity and trust | `docs/ASSI-001`–`003` | `specs/SPEC-004` | `cases/CASE-001` |
| Compositional identity and UTN | `docs/ASSI-004` | `specs/SPEC-002` | `cases/CASE-002` |
| REN and BCEF | `docs/ASSI-005`–`006` | `specs/SPEC-003` | `cases/CASE-003` |
| Authorization and bounded loss | `docs/ASSI-007` | `specs/SPEC-004` | `cases/CASE-004` |
| Adversarial drives and relay | `docs/ASSI-008` | `specs/SPEC-005` | `cases/CASE-005`, `extensions/EXT-001` |
| Residuals and validated RSI | `docs/ASSI-009` | `specs/SPEC-006` | `cases/CASE-005`, `extensions/EXT-004` |
| Architecture and benchmarks | `docs/ASSI-010`–`011` | `specs/SPEC-001` | `cases/CASE-001`–`005` |
| Generalization and transfer | `docs/ASSI-012` | Domain-specific future contracts | `extensions/EXT-003` |
| Autonomous questioning | `docs/ASSI-009` | `specs/SPEC-006` | `extensions/EXT-002` |

For exact file names and links, see [CONTENTS.md](CONTENTS.md). For the introductory reading paths, see [START-HERE.md](START-HERE.md). For experimental status and validation planning, see [VALIDATION-ROADMAP.md](VALIDATION-ROADMAP.md) when available.

## 12. Terminology maintenance and contribution policy

A proposed new term SHOULD specify: (1) its exact definition and scope; (2) the type of claim it represents; (3) its distinction from existing terms; (4) required provenance and time semantics; (5) any authority implications; (6) a falsifiable test or example where appropriate; and (7) the documents and contract versions affected.

Terminology revisions SHOULD preserve backward references, explain semantic changes, and avoid quietly converting hypotheses into facts or recommendations into authorization. Competing definitions MAY be recorded as explicit alternatives until resolved through evidence and governance.

---

**Research position:** ASSI favors specifications before runtime, conformance before claims of implementation, independent evaluation before claims of effectiveness, and governance before consequential deployment. Open research and collective learning are encouraged; unverified security guarantees are not.
