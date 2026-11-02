# OPEN QUESTIONS — Adversarial Structural Security Intelligence (ASSI)

**Release:** v0.1.0 — Research Foundation  
**Document type:** Open research questions, falsification prompts, and collective-learning backlog  
**Status:** Unresolved research questions; not validated findings or security assurances  
**Repository location:** `OPEN-QUESTIONS.md`  
**License:** Apache-2.0  
**Date:** 2026-11-02

> **Research stance.** Cryptographic validity does not establish legitimate intent. Observed activity does not establish a human controller. Evidence assessment does not confer authority. Simulation does not guarantee operational security. Recursive improvement must not authorize itself.

## 1. Purpose

This file is a question-oriented companion to [FUTURE-DIRECTIONS.md](FUTURE-DIRECTIONS.md), [TESTABLE-HYPOTHESES.md](TESTABLE-HYPOTHESES.md), and [VALIDATION-ROADMAP.md](VALIDATION-ROADMAP.md). It identifies the unresolved questions most likely to clarify, challenge, or falsify the Adversarial Structural Security Intelligence (ASSI) research program. A question appearing here is **not** an assertion that its proposed mechanism works.

ASSI's research foundation comprises twelve conceptual papers (`docs/ASSI-001`–`ASSI-012`), six draft specifications (`specs/SPEC-001`–`SPEC-006`), five synthetic cases (`cases/CASE-001`–`CASE-005`), and four exploratory extensions (`extensions/EXT-001`–`EXT-004`). The questions below are intended to become typed **Question Units**, bounded experiments, evidence records, and eventually independently reviewable results.

Questions are grouped by research theme, not by presumed answer. For each group, **discriminating tests** describe evidence that could distinguish competing explanations. **Failure conditions** identify outcomes that would weaken or defeat the proposed approach. Proposed experiments must use synthetic or explicitly authorized environments; no live exploitation or unauthorized asset interaction is implied.

## 2. How to use this question register

Each question has a stable identifier `OQ-XX-NN`. Its priority is provisional and may change when new evidence appears. Suggested handling:

1. **Register:** state the target claim, domain, threat model, relevant authority, and competing hypotheses.
2. **Scope:** distinguish observations, derived features, hypotheses, independently verified facts, and permitted actions.
3. **Discriminate:** identify a test that could favor one hypothesis over another, including a null or simpler baseline.
4. **Constrain:** set experimental authorization, sandbox boundaries, compute/time budgets, and stop conditions.
5. **Evaluate:** preregister metrics, failure criteria, dataset partitions, and independent evaluation responsibilities.
6. **Relay:** preserve outcomes, inconclusive evidence, negative transfer, and new questions with provenance.

Suggested priorities: **P0** = foundational safety or logical soundness; **P1** = essential benchmark discriminant; **P2** = exploratory extension. These are research-planning labels, not severity ratings of deployed vulnerabilities.

## 3. OQ-ST — Structural trust, authority, and bounded loss

**Core issue:** security is not reducible to valid signatures or to a single risk score.

| ID | Priority | Open question | Discriminating test or failure signal |
|---|---|---|---|
| OQ-ST-01 | P0 | Can trust relocation be represented without assuming that moving custody or signing responsibility eliminates trust? | Enumerate trust dependencies before and after a synthetic architecture change; failure if a critical dependency disappears from the model but not the system. |
| OQ-ST-02 | P0 | Which trust dependencies must be modeled as shared control points rather than independent edges? | Introduce a common administrator or recovery service; check whether estimated blast radius increases appropriately. |
| OQ-ST-03 | P0 | Under which explicit assumptions can a meaningful upper bound on unauthorized asset loss be established? | Vary bypass routes, delegated approvals, concurrent requests, and administrator compromise; any counterexample invalidates the claimed bound for that model. |
| OQ-ST-04 | P1 | How should direct transfers, contingent permissions, and cascading exposure be compared without misleading unit conversion? | Compare typed exposure vectors with one-number aggregation; measure hidden high-impact cases. |
| OQ-ST-05 | P1 | Can structural exposure metrics improve decisions beyond static per-transaction limits without excessive false holds? | Holdout synthetic custody workloads; report loss, service availability, and review burden together. |
| OQ-ST-06 | P1 | When does increased operational liquidity require increased reachable exposure, and when can the two be decoupled? | Vary replenishment policies, reserve partitioning, and withdrawal demand under matched service targets. |

**Related:** [ASSI-001](docs/ASSI-001-From-Cryptographic-Validity-to-Structural-Security.md), [ASSI-002](docs/ASSI-002-Four-Structural-Contradictions-of-Cryptocurrency-Security.md), [ASSI-003](docs/ASSI-003-Trust-Relocation-and-Structural-Security-Boundaries.md), [CASE-001](cases/CASE-001-Cryptocurrency-Trust-and-Liquidity.md).

## 4. OQ-ID — UTN, compositional identity, and temporal structure

**Core issue:** observed addresses, inferred controllers, composite teams, verified identities, and authorized principals are different kinds of objects.

| ID | Priority | Open question | Discriminating test or failure signal |
|---|---|---|---|
| OQ-ID-01 | P0 | Which identity types must be distinct in a canonical UTN ontology to prevent accidental inference-to-authorization promotion? | Deliberately cross-wire address, controller hypothesis, verified principal, and authorization subject; validators must reject invalid transitions. |
| OQ-ID-02 | P0 | Can a temporal compositional hypergraph represent overlapping teams, shared services, and changing membership more faithfully than flat clustering? | Compare false merge/split rates and time-consistency on seeded synthetic ground truth. |
| OQ-ID-03 | P0 | How can contradiction against a single-person controller hypothesis be prevented from refuting a team or shared-service hypothesis? | Generate evidence incompatible with one controller but consistent with collective control; measure scope leakage. |
| OQ-ID-04 | P1 | What evidence can distinguish shared infrastructure from shared human control? | Construct matched cases with common hosting, signing, or timing but distinct operators. |
| OQ-ID-05 | P1 | How should identity hypotheses survive address rotation, delegation, reorganization, and time-limited authority? | Measure temporal continuity and unjustified persistence across known transitions. |
| OQ-ID-06 | P1 | When should the system split, merge, suspend, or retain competing identity hypotheses? | Compare structural revision policies against immutable clustering and unrestricted merges. |
| OQ-ID-07 | P2 | Can identity uncertainty be expressed as a portfolio without forcing incomparable evidence into calibrated probabilities? | Test set-valued, ordinal, and probabilistic representations for error and interpretability. |

**Related:** [ASSI-004](docs/ASSI-004-UTN-and-Compositional-Identity-Intelligence.md), [SPEC-002](specs/SPEC-002-Compositional-Identity-and-UTN-Contract.md), [CASE-002](cases/CASE-002-UTN-On-Chain-Identity-Sandbox.md).

## 5. OQ-EV — REN, directional evidence, and epistemic provenance

**Core issue:** evidence may be weak, correlated, direction-dependent, and consistent with several competing hypotheses.

| ID | Priority | Open question | Discriminating test or failure signal |
|---|---|---|---|
| OQ-EV-01 | P0 | What operational meaning should a directional relevance score have, and when is a probabilistic interpretation unjustified? | Evaluate calibration and ranking separately; reject probability claims unsupported by data. |
| OQ-EV-02 | P0 | How can derived features and reused observations be prevented from masquerading as independent evidence? | Inject duplicated and transformed observations; confidence should not rise merely through re-encoding. |
| OQ-EV-03 | P1 | Which provenance fields are necessary to distinguish source reliability, observation quality, inference quality, and applicability? | Remove each field in ablation tests; measure traceability and incorrect conclusions. |
| OQ-EV-04 | P1 | When does weak evidence become decision-relevant, and what must remain unknown? | Compare against alternative hypotheses and evidence-absence controls; evaluate abstention quality. |
| OQ-EV-05 | P1 | Can a metric-native directional field outperform metric similarity alone in clearly specified tasks? | Compare REN, similarity-only, and simple heuristics on blinded scenarios. |
| OQ-EV-06 | P2 | How should conflicting sources, late evidence, and revoked observations propagate through MDT histories? | Replay temporal revisions and test audit reconstruction and stale-score detection. |

**Related:** [ASSI-005](docs/ASSI-005-REN-and-Directional-Weak-Evidence-Intelligence.md), [SPEC-001](specs/SPEC-001-Structural-Security-Unit-Contract.md).

## 6. OQ-IF — BCEF, conditional reasoning, and structural impact

**Core issue:** conditional reasoning is not reversible by default, and a contradiction should not indiscriminately erase related hypotheses.

| ID | Priority | Open question | Discriminating test or failure signal |
|---|---|---|---|
| OQ-IF-01 | P0 | How can Forward IF, Reverse IF, Counterfactual IF, and Contradiction IF be given distinct machine-checkable semantics? | Use truth-preserving and adversarial test vectors, including `H ⇒ E` with `E` observed but `H` false. |
| OQ-IF-02 | P0 | What is the minimal scope descriptor for a contradiction: proposition, subject, role, context, time, and assumptions? | Delete individual scope fields; measure unjustified rejection of unaffected hypotheses. |
| OQ-IF-03 | P0 | How can the system distinguish `UNKNOWN`, `SUPPORTED`, `REFUTED`, and `CONFLICT` without collapsing disagreement into a scalar? | Test missing evidence, contradictory sources, and mutually consistent alternatives. |
| OQ-IF-04 | P1 | When should an Evidence Impact change a score versus propose a graph split, merge, retyping, or new question? | Compare score-only revision with structured edits under held-out synthetic truth. |
| OQ-IF-05 | P0 | How can recursive IF-on-IF testing avoid self-confirmation, cycles, and unbounded computation? | Feed cyclic dependency graphs and correlated results; enforce termination and no confidence amplification. |
| OQ-IF-06 | P1 | Can BCEF reduce false rejection without materially sacrificing correct rejection recall? | Report both error types, abstentions, and cost; no single-metric success claims. |
| OQ-IF-07 | P2 | What is the value of an additional IF test when evidence acquisition has cost or operational risk? | Compare value-of-information scheduling against random, fixed, and greedy baselines. |

**Related:** [ASSI-006](docs/ASSI-006-Bidirectional-Conditional-Evidence-Feedback.md), [SPEC-003](specs/SPEC-003-Bidirectional-IF-and-Evidence-Impact-Contract.md), [CASE-003](cases/CASE-003-Bidirectional-IF-and-False-Rejection.md).

## 7. OQ-AU — Independent authorization and safety control planes

**Core issue:** a model may recommend an action, but the model must not thereby gain permission to execute it.

| ID | Priority | Open question | Discriminating test or failure signal |
|---|---|---|---|
| OQ-AU-01 | P0 | What architectural evidence demonstrates that every consequential execution path is mediated by an independent PEP? | Enumerate all synthetic asset-changing paths; a single bypass invalidates complete-mediation claims. |
| OQ-AU-02 | P0 | How can signed intent, canonical transaction content, policy version, and execution be bound without ambiguity? | Mutate amount, destination, call data, expiry, and policy version between approval and execution. |
| OQ-AU-03 | P0 | Can exposure budgets remain correct under concurrent requests, retries, partial failures, and replay? | Race-test atomic reservation and settlement; check for double spending of budget. |
| OQ-AU-04 | P0 | What assumptions make the safety control plane independent of the signing service and its administrators? | Model shared credentials, shared deployment, and common recovery authority; record correlated failure paths. |
| OQ-AU-05 | P1 | How should `DENY`, `HOLD`, `ESCALATE`, and `ALLOW` behave under stale evidence and service outages? | Test fail-closed semantics alongside availability and recovery burden. |
| OQ-AU-06 | P1 | What is the smallest set of emergency controls that can limit loss without making recovery authority an even larger single point of failure? | Compare freeze, revocation, multi-party recovery, and recovery-service compromise. |
| OQ-AU-07 | P1 | Can intelligent triage improve service quality while independent policy preserves the same loss bound? | Separate detection/triage metrics from authorization invariants in controlled ablations. |

**Related:** [ASSI-007](docs/ASSI-007-Structural-Authorization-and-Independent-Control-Planes.md), [SPEC-004](specs/SPEC-004-Authorization-and-Safety-Control-Contract.md), [CASE-004](cases/CASE-004-Compromised-Signing-Service-Defense.md).

## 8. OQ-DR — Adversarial Drives, independence, and Competitive Relay

**Core issue:** adversarial simulation can discover candidate weaknesses but can also reward unrealistic scenarios, shared assumptions, or benchmark gaming.

| ID | Priority | Open question | Discriminating test or failure signal |
|---|---|---|---|
| OQ-DR-01 | P0 | What minimum separation is required between Red, Blue, Evaluation, and Governance roles? | Introduce shared prompts, datasets, evaluators, and policy control; measure evaluation contamination. |
| OQ-DR-02 | P1 | Does Competitive Relay discover more distinct, reproducible security residuals than a single-agent workflow? | Match compute budgets; compare independently confirmed unique residuals, not raw scenario counts. |
| OQ-DR-03 | P0 | How can relay acceptance avoid being mistaken for evidence validation or deployment approval? | Attempt state transitions with missing independent signatures and validation records. |
| OQ-DR-04 | P1 | How should a scenario encode attacker capabilities, defender observability, environmental assumptions, and safety constraints? | Test whether third parties can reproduce results and detect omitted threat assumptions. |
| OQ-DR-05 | P1 | What prevents repeated Red/Blue cycles from overfitting to the generator or evaluator? | Use unseen threat families, independent generators, and delayed holdouts. |
| OQ-DR-06 | P2 | How can cooperation and competition coexist without encouraging agents to manufacture findings? | Compare reward functions based on scenario quantity, novelty, and independently verified impact. |

**Related:** [ASSI-008](docs/ASSI-008-Adversarial-Security-Drives-and-Competitive-Relay.md), [SPEC-005](specs/SPEC-005-Adversarial-Drive-and-Relay-Contract.md), [CASE-005](cases/CASE-005-Adversarial-Drives-and-Security-RSI.md).

## 9. OQ-RSI — Security Residuals, AQSI, and Validated RSI

**Core issue:** identifying a problem, proposing an improvement, demonstrating a synthetic gain, and authorizing deployment are separate transitions.

| ID | Priority | Open question | Discriminating test or failure signal |
|---|---|---|---|
| OQ-RSI-01 | P1 | Which residual taxonomy best preserves causal and operational distinctions across authorization, identity, evidence, recovery, and governance failures? | Measure inter-rater agreement and downstream usefulness versus a flat issue list. |
| OQ-RSI-02 | P1 | Can AQSI produce more discriminating, falsifiable security questions than fixed templates or random exploration? | Blindly score question quality and eventual information gain under equal budgets. |
| OQ-RSI-03 | P0 | How can improvement proposals be evaluated without allowing the proposing agent to control the evaluator or promotion gate? | Attempt self-approval and test rejection by independent governance. |
| OQ-RSI-04 | P1 | Do validated recursive cycles improve out-of-distribution defense or merely optimize known synthetic tests? | Track unseen scenarios, negative controls, regression failures, and calibration over multiple cycles. |
| OQ-RSI-05 | P0 | What stopping criteria prevent runaway recursive experimentation or unauthorized policy mutation? | Exhaust depth, cost, time, and exposure budgets; verify deterministic termination. |
| OQ-RSI-06 | P1 | How should negative results and inconclusive experiments alter future question portfolios? | Compare learning systems with and without a durable failed-experiment registry. |
| OQ-RSI-07 | P2 | What constitutes meaningful open-ended improvement if benchmark novelty and safety cannot be summarized by one scalar? | Use Pareto evaluation across discovery, risk, cost, governance, and generalization. |

**Related:** [ASSI-009](docs/ASSI-009-Security-Residuals-and-Validated-Recursive-Self-Improvement.md), [SPEC-006](specs/SPEC-006-Validated-RSI-and-Governance-Contract.md), [EXT-002](extensions/EXT-002-Autonomous-Security-Questioning-and-Exploration.md).

## 10. OQ-MA — Multi-agent ecology, evidence independence, and collective learning

| ID | Priority | Open question | Discriminating test or failure signal |
|---|---|---|---|
| OQ-MA-01 | P0 | How can agents recognize that apparently independent reports derive from the same source or model? | Construct provenance laundering chains; detect confidence inflation. |
| OQ-MA-02 | P1 | Does agent diversity improve resilience when diversity includes independently different evidence and methods rather than just role labels? | Compare identical-agent ensembles, heterogeneous methods, and independent-data groups. |
| OQ-MA-03 | P1 | How should cross-organization relay handle incompatible authority, confidentiality, and evidence disclosure rules? | Test minimal-disclosure evidence contracts and refusal/partial-acceptance semantics. |
| OQ-MA-04 | P1 | What new attack surfaces emerge from shared registries, relay coordinators, and collective reputation? | Simulate compromised registries and malicious submissions in an isolated lab. |
| OQ-MA-05 | P2 | Can disagreement among agents be retained as a productive, testable hypothesis portfolio? | Compare disagreement preservation with majority-vote collapse. |

**Related:** [EXT-001](extensions/EXT-001-Multi-Agent-Adversarial-Security-Ecology.md).

## 11. OQ-TR — Cross-domain transfer and negative transfer

| ID | Priority | Open question | Discriminating test or failure signal |
|---|---|---|---|
| OQ-TR-01 | P0 | Which SSU fields and invariants are truly domain-neutral, and which encode cryptocurrency-specific assumptions? | Map custody, cloud IAM, enterprise approval, AI agents, and supply-chain workflows; record unmappable fields. |
| OQ-TR-02 | P0 | How can a typed partial mapping refuse false equivalence between a signing key, human principal, service account, and delegated agent? | Seed tempting but invalid mappings; measure semantic boundary violations. |
| OQ-TR-03 | P1 | Can structural transfer outperform fresh domain-specific design once adapter and validation costs are included? | Compare time-to-correctness, security metrics, and total engineering cost. |
| OQ-TR-04 | P1 | How should a Non-Transfer Register record failures so they prevent recurrence without freezing future discovery? | Replay revised adapters against historical failed mappings and new valid cases. |
| OQ-TR-05 | P1 | Which claims require full revalidation in every target domain, regardless of structural similarity? | Identify target-specific authorization, exposure, recovery, and governance requirements. |
| OQ-TR-06 | P2 | Can transfer of **questions** be useful even when transfer of policies or scores is unsafe? | Compare question-only transfer against mechanism transfer and no transfer. |

**Related:** [ASSI-012](docs/ASSI-012-From-Cryptocurrency-Security-to-General-Structural-Defense.md), [EXT-003](extensions/EXT-003-Cross-Domain-Structural-Security-Transfer.md).

## 12. OQ-GV — Open-ended evolution and governance of governance

| ID | Priority | Open question | Discriminating test or failure signal |
|---|---|---|---|
| OQ-GV-01 | P0 | How can cumulative **authority drift** be detected when each individual policy change appears legitimate? | Compute authority reachability before/after a sequence of synthetic small changes; detect newly reachable forbidden actions. |
| OQ-GV-02 | P0 | Who may change the rules that authorize changes to the rules, and how is this independence audited? | Attempt recursive self-authorization and shared-admin compromise in a governance sandbox. |
| OQ-GV-03 | P1 | What evidence supports promotion from an experimental security policy to a controlled pilot? | Require independent evaluation, explicit scope, rollback readiness, and recorded approval. |
| OQ-GV-04 | P1 | Can governance procedures evolve without losing a verifiable chain of accountability? | Version governance rules, replay decisions, and verify audit consistency. |
| OQ-GV-05 | P1 | How can safety failures and near misses be learned from without granting experiments authority over real assets? | Compare offline/synthetic learning and bounded read-only observation under authorization constraints. |
| OQ-GV-06 | P2 | What is a meaningful definition of open-ended security intelligence under finite budgets and irreducible uncertainty? | Test whether novel verified findings persist without degrading safety or oversight. |

**Related:** [EXT-004](extensions/EXT-004-Open-Ended-Security-Evolution-and-Governance.md).

## 13. Cross-cutting methodological questions

These questions apply to every benchmark family.

| ID | Priority | Open question | Minimum expectation |
|---|---|---|---|
| OQ-ME-01 | P0 | What exactly is the threat model and what is explicitly out of scope? | Written attacker capabilities, defender assets, control assumptions, and exclusion list. |
| OQ-ME-02 | P0 | How is synthetic ground truth hidden from the evaluated model and from candidate generation? | Seed control, partitioning, leakage tests, and evaluator isolation. |
| OQ-ME-03 | P0 | Which simple baselines must be beaten before structural complexity is justified? | Signature-only, static-rule, flat-clustering, one-way-IF, or fixed-question baselines as applicable. |
| OQ-ME-04 | P1 | How will statistical uncertainty, distribution shift, and rare catastrophic events be reported? | Confidence intervals or uncertainty bounds, stress tests, and explicit low-frequency limitations. |
| OQ-ME-05 | P0 | What would decisively falsify the claimed benefit? | Preregistered failure criteria and negative controls, not only success demonstrations. |
| OQ-ME-06 | P1 | What does independent replication require beyond running the same code? | Separate implementation or independent audit, new seeds, blinded holdouts, and provenance. |
| OQ-ME-07 | P1 | How will the cost of richer structure be compared with measurable security benefit? | Compute, latency, human review, false holds, and maintenance burden. |
| OQ-ME-08 | P0 | How will unsupported certainty be prevented in public claims? | Explicit maturity level and tested-scope language in every result report. |

## 14. Benchmark routing matrix

| Benchmark | Primary open questions | Candidate outcome metrics | Essential negative control |
|---|---|---|---|
| **BM-001 — Compositional Identity** | OQ-ID-01–07, OQ-EV-02, OQ-IF-02 | False merge, false split, temporal continuity, scope leakage, abstention | Shared infrastructure without shared controller |
| **BM-002 — BCEF Evidence Revision** | OQ-IF-01–07, OQ-EV-01–06 | False rejection, correct rejection recall, dependency inflation, structural-edit validity | Reverse implication fallacy and duplicate evidence |
| **BM-003 — Authorization and Bounded Loss** | OQ-ST-03–06, OQ-AU-01–07 | Unauthorized loss, bypass rate, false holds, latency, recovery time | Valid signature with invalid intent; shared-admin compromise |
| **BM-004 — Adversarial Relay and Validated RSI** | OQ-DR-01–06, OQ-RSI-01–07, OQ-GV-01–06 | Verified unique residuals, unseen-case performance, governance violations, regression, cost | Evaluator contamination and recursive self-approval |

Cross-domain laboratories should also test OQ-TR-01–06. Multi-agent studies should add OQ-MA-01–05. **No benchmark is claimed to have been executed in v0.1.0.**

## 15. Canonical Question Unit — illustrative contract

The following YAML is a **non-normative example**, intended to be reconciled with [SPEC-001](specs/SPEC-001-Structural-Security-Unit-Contract.md) and [SPEC-006](specs/SPEC-006-Validated-RSI-and-Governance-Contract.md) before implementation.

```yaml
unit_type: assi.research.question
unit_id: OQ-IF-03
schema_version: 0.1.0
status: proposed
research_domain: synthetic_compositional_identity
priority: P0
question: >
  Can four-valued assessment preserve unresolved conflict
  without incorrectly rejecting the team-controller hypothesis?
hypotheses:
  - id: H1
    claim: A single individual controls all observed addresses.
  - id: H2
    claim: A changing team controls the observed addresses.
  - id: H3
    claim: Independent operators use a shared service.
competing_explanations_required: true
observations:
  - synthetic_event_stream_v1
provenance_policy:
  retain_source_ids: true
  dependency_graph_required: true
  synthetic_ground_truth_sequestered: true
proposed_tests:
  - forward_if
  - reverse_if
  - counterfactual_if
  - contradiction_if
scope:
  entity_types: [observed_address, inferred_controller, composite_team]
  time_window: synthetic_epoch_1_to_4
  excludes: [real_world_identity_attribution, production_authorization]
metrics:
  - false_rejection_rate
  - correct_rejection_recall
  - contradiction_scope_leakage
  - abstention_quality
baselines:
  - flat_address_clustering
  - single_score_rejection
falsification_condition: >
  No reliable reduction in scope leakage or false rejection
  at comparable correct-rejection recall and resource cost.
safety:
  environment: isolated_synthetic_sandbox
  real_assets_allowed: false
  production_policy_changes_allowed: false
  independent_evaluation_required: true
relay:
  next_stage: preregistered_experiment
  evidence_status: not_yet_tested
```

**Contract caution:** A question's presence, priority, or score is not evidence of the answer; a passed synthetic test is not production authorization.

## 16. Proposed question lifecycle and acceptance criteria

```text
Proposed Question
    |
    v
Typed + Scoped + Alternative Hypotheses
    |
    v
Safety / Authorization Review
    |
    v
Preregistered Experiment + Independent Evaluation Plan
    |
    v
Synthetic or Explicitly Authorized Execution
    |
    v
Result: Supported / Refuted / Conflicted / Inconclusive
    |
    v
Evidence + Negative Results + Security Residual Registry
    |
    v
Structural Relay / New Question / Governed Candidate
```

A question may be accepted into an experiment portfolio only if it has: (i) a falsifiable claim or explicit exploratory objective; (ii) a threat model and scope; (iii) competing explanations where relevant; (iv) a measurable baseline; (v) independent evaluation criteria; (vi) provenance and dependency handling; and (vii) an authorized, bounded test environment. A result may be **inconclusive** without being a failure of the research process.

Questions should be revised, not silently overwritten. Every revision should preserve the prior wording, rationale, scope, author or generating process, timestamp, and downstream experiments. Results that invalidate a previously useful question should remain discoverable.

## 17. Suggested first experiments — small, decisive, safe

### Experiment A — Hypothesis-scoped contradiction (P0)

Generate four epochs of synthetic address events with one individual, one changing team, and a shared service. Create an observation that contradicts the single-person hypothesis but not team control. Compare unrestricted rejection against scoped BCEF; report both false and correct rejection rates, not merely the number of retained hypotheses. **Fail** if BCEF systematically preserves invalid hypotheses or does not reduce scope leakage.

### Experiment B — Correlated evidence amplification (P0)

Derive multiple features from one underlying synthetic event. Compare a naive additive score with dependency-aware evidence accounting. **Fail** if re-encoding a source increases evidentiary support without independent new information.

### Experiment C — Valid signature, invalid authorization (P0)

In a synthetic custody environment, supply a cryptographically valid transaction that violates the independently approved destination or exposure budget. Test the complete mediation path and concurrency accounting. **Fail** if any execution route bypasses the independent policy enforcement point or exceeds the stated loss bound under the declared assumptions.

### Experiment D — Relay contamination and governance (P0)

Have a candidate-generating agent submit an improvement with attractive synthetic metrics but evaluator leakage. Require independent evaluation and a separate promotion authority. **Fail** if the system self-approves, promotes on contaminated evidence, or modifies hard safety constraints without authorization.

### Experiment E — Negative cross-domain transfer (P1)

Map a cryptocurrency signing role to a cloud IAM service account, then introduce a mismatch in delegation and revocation semantics. Compare typed partial mapping with naive one-to-one mapping. **Fail** if the transfer system silently equates authorities that are not equivalent.

## 18. Open contribution and collective-learning protocol

ASSI welcomes carefully scoped questions, counterexamples, simpler baselines, contract corrections, negative findings, and independent replication plans. Contributions should specify the question ID or propose a new one, the relevant repository documents, assumptions, competing explanations, safety constraints, expected discriminating evidence, and an explicit failure condition.

A useful contribution template:

```markdown
### Proposed Question: OQ-XX-NN
- **Research claim or uncertainty:**
- **Why it matters:**
- **Competing hypotheses / null hypothesis:**
- **Observations versus inferences:**
- **Threat model and excluded assumptions:**
- **Minimal synthetic or authorized experiment:**
- **Baseline and ablation:**
- **Metrics and falsification criteria:**
- **Evidence dependencies and provenance:**
- **Safety boundary and independent reviewer:**
- **Possible negative result / non-transfer lesson:**
- **Related ASSI documents:**
```

**Collective learning does not require consensus.** Reproducible disagreement and well-scoped counterexamples are valuable outputs. A relay recipient may accept the question while rejecting its proposed answer. A validated finding may still require new domain-specific evaluation before reuse.

## 19. What this document does not claim

- It does **not** claim ASSI has demonstrated superior security performance.
- It does **not** identify actual owners of cryptocurrency addresses or imply real-world attribution.
- It does **not** provide permission to test third-party systems or transfer assets.
- It does **not** assert that a benchmark contract, diagram, or YAML example is a formally verified implementation.
- It does **not** claim that agent agreement establishes independent evidence.
- It does **not** treat recursive self-improvement as an independent safety guarantee.
- It does **not** authorize the intelligence layer to revise its own hard safety boundaries.

## 20. Reading map and next steps

- **Architecture:** [README.md](README.md), [START-HERE.md](START-HERE.md), [ASSI-010](docs/ASSI-010-ASSI-Grand-Architecture-and-Structural-Security-Units.md).
- **Definitions:** [GLOSSARY.md](GLOSSARY.md), [SPEC-001](specs/SPEC-001-Structural-Security-Unit-Contract.md).
- **Research agenda:** [FUTURE-DIRECTIONS.md](FUTURE-DIRECTIONS.md).
- **Hypothesis register:** [TESTABLE-HYPOTHESES.md](TESTABLE-HYPOTHESES.md).
- **Validation sequence:** [VALIDATION-ROADMAP.md](VALIDATION-ROADMAP.md), [ASSI-011](docs/ASSI-011-Benchmark-Laboratories-and-Falsifiable-Security-Hypotheses.md).
- **Experimental cases:** [CASE-001](cases/CASE-001-Cryptocurrency-Trust-and-Liquidity.md) through [CASE-005](cases/CASE-005-Adversarial-Drives-and-Security-RSI.md).
- **Open-ended extensions:** [EXT-001](extensions/EXT-001-Multi-Agent-Adversarial-Security-Ecology.md) through [EXT-004](extensions/EXT-004-Open-Ended-Security-Evolution-and-Governance.md).

The next useful step is to select a **small P0 question**, publish its contract and failure conditions, and run a blinded synthetic baseline before expanding architectural complexity. Preserve both success and failure as traceable structural evidence.

---

**Closing principle:** *Keep the question open, the hypothesis scoped, the evidence traceable, the experiment bounded, and the authority independent.*

**License:** Apache-2.0. This research document provides no warranty or operational security assurance.
