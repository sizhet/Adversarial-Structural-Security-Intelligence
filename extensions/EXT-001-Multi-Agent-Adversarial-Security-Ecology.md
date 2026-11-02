# EXT-001 — Multi-Agent Adversarial Security Ecology

**Project:** Adversarial Structural Security Intelligence (ASSI)  
**Version:** v0.1.0 — Research Foundation  
**Status:** Exploratory architectural extension and falsifiable research proposal; not an implemented or independently validated security system  
**Date:** 2026-11-02  
**License:** Apache-2.0  
**Repository path:** `extensions/EXT-001-Multi-Agent-Adversarial-Security-Ecology.md`  
**Foundations:** ASSI-004–012; SPEC-001–006; CASE-001–005  
**Related concepts:** UTN; REN; BCEF; UCPSF; AQSI; SSICR; UIERU; Structural Relay; Validated RSI

## Abstract

Security is not a contest between one attacker and one defender. It is an evolving ecology of asset owners, users, service providers, human teams, software agents, governance bodies, evaluators, and adversaries. Participants possess different knowledge, incentives, authority, evidence, and operational constraints. Their interactions produce both vulnerabilities and opportunities for collective defense. This extension proposes **Multi-Agent Adversarial Security Ecology (MA-ASE)** as a research architecture for representing that environment through typed, time-dependent structural relationships and governed competitive/cooperative relay.

MA-ASE extends ASSI's four-Drive laboratory—Red, Blue, Evaluation, and Governance—into a multi-participant setting with heterogeneous, potentially overlapping identities. It introduces ecological roles, trust and information boundaries, local and shared Security Residual registries, evidence-aware reputation, strategic adaptation, and independently governed knowledge transfer. It distinguishes **coordination** from **collusion**, **knowledge sharing** from **authority delegation**, and **simulated improvement** from **validated safety**. Its experiments are synthetic and defensive: no real targets, live exploitation, uncontrolled agent autonomy, or transferable attack instructions are required.

The central hypothesis is that structurally diverse, appropriately isolated participants can identify and address some classes of security failure better than a monolithic defender, provided the added coordination cost, information leakage, collusion risk, and governance burden are measured rather than assumed away. A second hypothesis is that ecological security can be improved through portable, typed learning artifacts without transferring sensitive operational data or execution authority. Both propositions remain open to falsification.

**Keywords:** multi-agent security; adversarial ecology; structural intelligence; compositional identity; competitive relay; collective learning; independent evaluation; governance; security residual; validated recursive improvement.

---

## 1. Motivation: From a Security System to a Security Ecology

ASSI's core papers and specifications describe a structured approach to identity, evidence, authorization, adversarial simulation, and validated improvement. The single-laboratory model is useful but incomplete. A real defensive system interacts with actors outside its own design boundary: vendors, custodians, users, regulators, incident responders, auditors, upstream software providers, and independent intelligence sources. Their incentives and evidence differ. Even when a local security policy is sound, an inter-organizational dependency or compromised shared service may invalidate its assumptions.

The ecological perspective asks a broader question:

> Under what conditions can multiple partially informed and differently incentivized agents produce a more resilient defense through competition, cooperation, and structural relay—without creating new channels for privilege escalation, evidence laundering, or collective failure?

An ecology is **not** simply a larger agent swarm. It includes a topology of rights, resources, observations, information asymmetries, trust assumptions, and enforceable constraints. An agent's sophistication is secondary to its position in that topology.

### 1.1 Three transitions

1. **Single-model reasoning → heterogeneous hypothesis portfolios.** Different participants may model the same event differently; disagreement is a research asset if its provenance is preserved.
2. **Single defender → interacting defensive institutions.** A policy owner, independent evaluator, incident responder, and service operator should not silently collapse into one authority.
3. **Local optimization → ecological resilience.** Improvement must account for effects on other participants, shared dependencies, and correlated failure modes.

### 1.2 Scope and non-goals

This extension proposes research contracts and laboratory protocols. It does **not** claim a deployed autonomous defense network, prove multi-agent superiority, prescribe real-world intrusion techniques, or permit agents to change live authorization rules. It does not equate simulation success with operational assurance.

---

## 2. Foundational Principles

The following principles constrain every proposed ecological mechanism.

**P1 — Cryptographic validity is not structural security.** A correctly signed message or authenticated service call does not establish legitimate intent, acceptable exposure, or a trustworthy dependency chain.

**P2 — Identity is compositional and temporal.** An apparent actor may be a person, team, coalition, automated service, or changing combination. Claims must preserve roles, time windows, and competing explanations.

**P3 — Evidence is directional and dependency-aware.** REN relevance and BCEF tests cannot transform repeated or correlated assertions into independent confirmation.

**P4 — Contradiction is hypothesis-scoped.** Refuting a specific controller, role, or interval must not automatically refute a broader team or shared-service hypothesis.

**P5 — Learning and authorization are separate.** Knowledge can be proposed and evaluated across agents; authority to act must remain independently governed.

**P6 — Bounded loss precedes perfect prediction.** Exposure limits, isolation, recovery, and non-bypassable controls remain necessary when all intelligent participants are wrong.

**P7 — Competition does not imply truth.** An adversarially persuasive argument, majority vote, or winning strategy in a simulator is not independent validation.

**P8 — Collective learning requires explicit leftovers.** Rejected hypotheses, failed experiments, unresolved disagreements, and repeated execution traces should remain available as typed research artifacts where retention is authorized.

---

## 3. Formal Ecological Model

Define a time-indexed ecology:

\[
\mathcal{E}_t=(\mathcal{A}_t,\mathcal{R}_t,\mathcal{X}_t,\mathcal{O}_t,\mathcal{P}_t,\mathcal{K}_t,\mathcal{G}_t).
\]

Here:

- \(\mathcal{A}_t\): agents and compositional actor hypotheses;
- \(\mathcal{R}_t\): typed relationships, memberships, delegations, and dependencies;
- \(\mathcal{X}_t\): protected assets, services, and resources;
- \(\mathcal{O}_t\): observations and their provenance;
- \(\mathcal{P}_t\): policy, authorization, and safety constraints;
- \(\mathcal{K}_t\): knowledge units, questions, residuals, and relay artifacts;
- \(\mathcal{G}_t\): governance roles, decisions, and accountability records.

The model is a **temporal typed hypergraph**, not a presumption that every edge is a verified fact. A relation must declare whether it is observed, derived, hypothesized, contested, or independently validated. A hyperedge may describe a coalition controlling a service during a bounded interval without reducing that coalition to a single person.

### 3.1 Actor dimensions

Each participant can be characterized by a tuple:

\[
a_i=(\text{type},\text{roles},\text{capabilities},\text{authority},\text{visibility},\text{incentives},\text{constraints},\text{provenance}).\]

Roles and authority must be evaluated per context. A participant may simultaneously be a defensive service operator, an evidence contributor, and a member of a shared infrastructure team. Those overlapping roles create conflicts of interest that a flat agent identifier would conceal.

### 3.2 Ecological state versus truth

The laboratory may contain hidden ground truth \(Z_t\), but no ordinary agent is assumed to observe it directly. An agent holds a belief or hypothesis portfolio \(H_i(t)\), supported by accessible observations \(O_i(t)\). The evaluator can inspect sealed ground truth under an independently controlled protocol. This separation is essential to measuring whether collaboration genuinely improves inference.

---

## 4. Ecological Roles and Separation of Duties

MA-ASE expands the four Drives into independently accountable roles. A role is a **contract**, not necessarily a distinct model vendor or machine.

| Role | Primary contribution | Restricted behavior |
|---|---|---|
| Red research agent | Generates bounded adversarial hypotheses and synthetic test scenarios | Cannot access live targets or change production controls |
| Blue design agent | Proposes detection, containment, and recovery improvements | Cannot self-approve its own deployment |
| Evaluation agent | Tests hypotheses, baselines, and candidate defenses | Cannot alter sealed ground truth or evaluation criteria post hoc |
| Governance agent | Reviews risk, authorization, policy, and promotion gates | Cannot treat model output as sufficient authority |
| Evidence steward | Maintains provenance, dependency graphs, and permitted sharing | Cannot silently upgrade inferred evidence to verified identity |
| Identity steward | Maintains UTN namespaces and composition records | Cannot infer execution rights from identity similarity |
| Relay coordinator | Routes typed questions, results, and unresolved residuals | Cannot erase negative results or grant execution permission |
| Recovery custodian | Maintains independent halt, rollback, and recovery paths | Cannot be subordinated to adaptive scoring |
| External observer | Supplies bounded, possibly conflicting observations | Cannot require trust merely by institutional reputation |

### 4.1 Role separation is not identity separation

Two nominally different agents may depend on the same model, prompt, training data, tool, administrator, or vendor. Evaluation independence is therefore a property to **measure and document**, not an assertion based on agent count. The architecture should record common dependencies and reduce confidence when supposedly independent findings share their origin.

### 4.2 Governance quorum

For consequential changes, require a documented policy-defined approval quorum with independently controlled credentials. The quorum design must consider common-mode failure, collusion, unavailable reviewers, and emergency recovery. No universal quorum size is prescribed here; it is a domain-specific security decision to be validated.

---

## 5. Compositional Identity in a Multi-Agent Ecology

The UTN contract (SPEC-002) is extended to agents whose membership and operational identity evolve. Relevant distinctions include:

1. **Instance identity:** a running software process or service instance.
2. **Principal identity:** a verified human, organization, or service principal.
3. **Behavioral cluster:** a hypothesis that observations share a controller or operational pattern.
4. **Coalition identity:** a time-bounded group acting jointly or through delegation.
5. **Authority identity:** a principal whose permissions are independently verified for a specified action.

A shared API gateway, orchestration service, or model provider can produce correlated behavior without proving common human control. Conversely, one team can operate through many accounts and services without presenting a stable behavioral signature.

### 5.1 Hypothesis portfolio example

For synchronized changes across three fictional services:

- \(H_1\): one operator controls all services;
- \(H_2\): a coordinated team controls them;
- \(H_3\): independent operators use one shared automation provider;
- \(H_4\): an external scheduled event triggers similar behavior.

A contradiction against \(H_1\) must not automatically eliminate \(H_2\)–\(H_4\). The record should state the proposition, role, interval, conditions, and evidence lineage actually tested.

### 5.2 Ecological false merge and false split

An incorrect merge can wrongly attribute malicious intent or privileges across organizations. An incorrect split can hide shared control or correlated compromise. The experiment must report both error classes and their operational consequences; optimizing only one is inadequate.

---

## 6. Information, Trust, and Evidence Boundaries

Multi-agent learning adds pathways for both useful signals and contamination. Every cross-agent transfer should identify:

- origin and custodian;
- epistemic status and confidence semantics;
- permitted audience and purpose;
- sensitivity and redaction requirements;
- dependencies on previously shared artifacts;
- validity interval and expiration;
- challenge and revocation mechanisms;
- whether independent corroboration exists.

### 6.1 Four distinct trust questions

**Source trust:** Was the artifact supplied by the claimed source?  
**Content trust:** Is the claim supported by evidence?  
**Context trust:** Does the claim apply to this asset, actor, and time interval?  
**Authority trust:** Is the source permitted to authorize the proposed action?

These questions must not be folded into one reputation score. A well-authenticated source may be mistaken. A highly accurate source may have no authority to change policy.

### 6.2 Evidence laundering

Suppose Agent A observes one event and publishes a hypothesis. Agents B and C repeat that hypothesis in summaries. A naïve aggregator sees three endorsements; a provenance-aware system sees one original observation and two derived reports. The latter may still value independent analysis, but it must not count three independent observations.

A relay artifact therefore carries a **lineage DAG** and dependency identifiers. Claims without sufficient provenance remain explicitly uncertain.

---

## 7. REN, BCEF, and Ecological Hypothesis Revision

REN provides directional evidence relevance: how much an observation bears on a particular hypothesis under a declared perspective and context. BCEF adds conditional tests:

- **Forward IF:** If hypothesis \(H\) holds, what observable consequences should follow?
- **Reverse IF:** Given observation \(E\), which alternative hypotheses could explain it?
- **Counterfactual IF:** If a relevant condition were absent or changed, what should differ?
- **Contradiction IF:** Which precisely scoped proposition is incompatible with the evidence and assumptions?

The inverse of an implication is not generally valid: \(H\Rightarrow E\) does not establish \(E\Rightarrow H\).

### 7.1 Structured ecological impact

A BCEF result may propose:

- reweighting a hypothesis with dependency-aware evidence;
- splitting an actor hypothesis into distinct teams or time intervals;
- reclassifying an edge as shared infrastructure rather than common control;
- opening a question for independent corroboration;
- withdrawing an outdated relay artifact;
- marking an unresolved contradiction for further study.

It may **not** directly modify authorization, transfer assets, bypass a safety policy, or promote itself to validated status.

### 7.2 Disagreement as a first-class object

Represent a disagreement as a typed object with competing claims, evidence sets, common dependencies, proposed discriminating tests, and stopping conditions. Persistent disagreement is not necessarily a defect; premature consensus can be more dangerous than explicit uncertainty.

---

## 8. Competitive and Cooperative Structural Relay

A multi-agent relay is a transfer protocol for **research artifacts**, not a transfer of power. Its stages are:

1. **Propose:** an agent submits a typed question, observation, candidate, or Security Residual.
2. **Normalize:** UTN and SSU contracts check types, provenance, time, and policy scope.
3. **Route:** a coordinator selects eligible recipients by role and information permissions.
4. **Challenge:** competing agents identify alternatives, contradictions, and missing evidence.
5. **Evaluate:** an independent evaluator tests claims against registered criteria.
6. **Govern:** an authorized body decides whether a validated candidate can be promoted.
7. **Archive:** results, negative findings, dependencies, and explicit leftovers are retained.

### 8.1 Cooperation mechanisms

Cooperation can include sharing non-sensitive residual categories, common test specifications, anonymized failure signatures, and reusable conformance vectors. Cooperation need not reveal private assets, customer data, access paths, or sensitive incident details.

### 8.2 Competition mechanisms

Competition can include parallel defensive proposals, alternative causal explanations, blind evaluation, and independently generated tests. The competition objective must not reward sensational attack narratives, fabricated vulnerabilities, or the suppression of legitimate service.

### 8.3 Relay portfolio selection

A candidate relay portfolio \(Q\) can be chosen under resource and risk constraints:

\[
\max_Q \sum_{q\in Q} V(q)-\lambda C(Q)-\mu R(Q)-\nu D(Q),
\]

where \(V\) is estimated information or defensive value, \(C\) is operational cost, \(R\) is bounded experimental risk, and \(D\) penalizes redundant or correlated questions. These quantities are **research design variables**, not calibrated probabilities or a proven optimal policy.

---

## 9. Ecological Security Residuals

A local Security Residual is a gap between a declared objective and observed or hypothesized behavior. An **ecological residual** also captures the way that gap crosses organizational or agent boundaries.

| Residual class | Ecological failure mode | Candidate measurement |
|---|---|---|
| Shared dependency | Several agents fail through one provider | Common-mode failure concentration |
| Identity composition | Shared service mistaken for one controller | False-merge / false-split rates |
| Evidence contamination | Repeated claims treated as independent | Provenance duplication rate |
| Coordination delay | Relevant warning fails to reach authorized owner | Detection-to-response latency |
| Governance conflict | No clear authority for cross-party response | Unresolved decision time |
| Policy mismatch | Local defenses conflict at a shared boundary | Cross-policy incompatibility count |
| Relay degradation | Artifact loses context or validity over hops | Semantic fidelity / stale-artifact rate |
| Evaluation capture | Participants influence their own benchmarks | Independence violation count |
| Recovery coupling | Multiple participants rely on one recovery path | Recovery common-mode exposure |
| Incentive misalignment | Agents optimize local metrics at collective cost | Externality-adjusted loss |

Residuals must include scope, affected assets, assumptions, evidence, owner, severity method, and validation status. A hypothetical residual is not an observed breach.

---

## 10. Independent Authorization and Ecological Safety

The Independent Safety Control Plane specified in ASSI-007 and SPEC-004 remains outside adaptive agent control. Each consequential operation must be checked against the relevant owner’s authorization and policy, including:

- authenticated principal and independently verified role;
- explicit action, target, amount or resource scope;
- canonical request-to-execution binding;
- time limits and replay protection;
- aggregate and concurrent exposure budgets;
- separation of proposal, approval, and execution;
- emergency halt, revocation, and recovery;
- auditable decisions and failure handling.

### 10.1 Cross-boundary rule

**An agent's right to observe or recommend in one domain does not imply a right to act in another.** This rule applies even when the receiving agent trusts the source, when many agents agree, or when a simulated evaluation reports improvement.

### 10.2 Bounded loss is conditional

A claimed exposure bound must state which execution paths are covered, how budgets are synchronized, whether common administrators can override controls, and what happens under partition, stale policy, or simultaneous compromise. If those assumptions are not established, no hard loss guarantee should be claimed.

### 10.3 Safe research environment

All proposed Red activities are confined to owned, explicitly authorized, synthetic or isolated laboratory resources. No live intrusion, credential theft, persistence, lateral movement, or operational exploitation is required to evaluate the hypotheses in this paper.

---

## 11. Ecological Dynamics and Strategic Adaptation

Multi-agent security has feedback loops. An agent changes its behavior after observing another; shared infrastructure changes the feasible actions of many; governance responds to incidents; and a defensive improvement can shift risk elsewhere.

### 11.1 Local optimization versus global effects

A local defender may minimize its false-negative rate by aggressively blocking shared services, thereby imposing unacceptable availability costs on other participants. Another may improve speed by centralizing authorization, increasing common-mode exposure. Therefore report both **local metrics** and **system-level externalities**.

### 11.2 Diversity and correlation

A larger agent population is not necessarily more robust. If agents share identical assumptions, datasets, policies, and dependencies, their errors may be highly correlated. Effective diversity should be measured through disagreement quality, independent evidence, complementary capabilities, and distinct failure modes—not merely the number of agents.

### 11.3 Ecological stability

Repeated strategy updates may cause oscillation: one defender changes a rule, another adapts, and both repeatedly reverse course. A governed update mechanism should use hold periods, regression tests, rollback triggers, and a maximum update rate. Stability is an empirical question, not an automatic outcome of feedback.

---

## 12. Canonical Ecological Security Unit (ESU)

An **Ecological Security Unit** extends the SPEC-001 SSU envelope rather than replacing it. The following YAML is an illustrative, non-normative proposal; exact schema validation belongs to future conformance work.

```yaml
schema: assi.ecology.esu.v0.1.0
unit_id: esu:synthetic:0007
unit_type: ecological_security_residual
status: hypothesized
created_at: 2026-11-02T00:00:00Z
scope:
  laboratory: lab-ecology-synthetic
  domain: shared-signing-dependency
  valid_from: 2026-11-01T00:00:00Z
  valid_to: null
actors:
  - utn:synthetic:operator-team-a
  - utn:synthetic:service-provider-b
hypothesis:
  statement: >
    Two independent defenders may share one operational dependency.
  alternatives:
    - independent_dependencies
    - correlated_behavior_without_shared_control
evidence:
  references: [obs:synthetic:12, obs:synthetic:19]
  dependency_groups: [origin:synthetic:provider-log-1]
  independent_corroboration: false
impact:
  type: request_independent_test
  affected_hypotheses: [hyp:synthetic:shared-dependency]
  authorization_effect: none
relay:
  audience: synthetic-evaluation-drive
  confidentiality: laboratory_only
  expiry: 2026-12-01T00:00:00Z
governance:
  owner: role:synthetic:research-steward
  promotion_state: not_eligible
  audit_required: true
```

**Implementation note:** The two illustrative actor values above are placeholders; a concrete UTN schema should use the exact namespace syntax defined by SPEC-002. This example intentionally conveys no executable authorization.

### 12.1 Mandatory semantic properties

An ESU should preserve: globally unique identity, type, version, epistemic status, temporal scope, actor references, source lineage, dependency groups, confidentiality, intended recipients, validity constraints, and an explicit declaration that evidence-transfer permissions do not constitute execution permissions.

---

## 13. Relay and Governance Contracts

### 13.1 Relay submission

Inputs: typed artifact, sender identity, source provenance, permitted recipients, declared research purpose, sensitivity, validity period, and dependencies.  
Outputs: accepted, quarantined, rejected, or request-for-clarification, with a reason and audit identifier.

### 13.2 Independent challenge

Inputs: artifact, hypothesis portfolio, evaluation policy, permitted evidence.  
Outputs: supported, refuted, conflicted, or unknown, together with tested scope, evidence lineage, limitations, and candidate discriminating tests.

### 13.3 Candidate promotion

Inputs: candidate version, frozen benchmark, holdout results, safety regression report, governance approvals, rollback plan.  
Outputs: deny, hold, escalate, or allow within explicitly bounded deployment scope. A relay coordinator must not issue this decision on its own authority.

### 13.4 Revocation and correction

If an artifact is later found erroneous or contaminated, downstream recipients must be able to identify dependent conclusions and receive a correction notice. Historical records should remain auditable; revocation is not silent deletion.

---

## 14. Conformance Invariants

A conforming research implementation should test at least the following invariants:

1. **Typed identity:** actor references distinguish observed services, inferred controllers, verified principals, and authorization subjects.
2. **Temporal identity:** group membership and delegation include validity intervals.
3. **Hypothesis scope:** negative findings do not automatically propagate beyond tested hypotheses.
4. **Evidence lineage:** derived endorsements retain source dependency references.
5. **No vote-to-truth:** majority agreement does not change epistemic status to independently validated.
6. **No relay-to-authority:** receipt or acceptance of a research artifact never grants execution permission.
7. **Independent evaluation:** a candidate author cannot unilaterally approve its own test outcome.
8. **Protected ground truth:** synthetic hidden labels are inaccessible to proposing agents during blind evaluation.
9. **Policy immutability:** adaptive agents cannot directly weaken protected safety policies.
10. **Bounded execution:** every experiment has explicit scope, resources, time limits, and stop controls.
11. **Recipient control:** sensitive artifacts are delivered only to authorized roles.
12. **Version binding:** conclusions identify the tested candidate, policy, and environment versions.
13. **No silent evidence duplication:** re-shared evidence cannot be counted as independent corroboration.
14. **No inferred delegation:** high identity similarity cannot create new privileges.
15. **Recovery independence:** recovery paths do not depend solely on the component being recovered.
16. **Auditability:** each consequential transition has a durable decision and provenance record.
17. **Conflict preservation:** unresolved competing hypotheses remain visible unless a scoped test resolves them.
18. **Revocation propagation:** corrected or withdrawn artifacts identify affected downstream claims.
19. **Explicit leftovers:** inconclusive and failed experiments retain authorized residual records.
20. **Safe termination:** budget exhaustion, policy violations, and isolation failures stop the relevant experiment.
21. **No unreviewed promotion:** deployment requires a separate governance decision.
22. **Common-mode disclosure:** claimed independence is qualified by shared tools, vendors, administrators, and datasets.
23. **Domain-bound transfer:** cross-domain mappings preserve the receiving domain's authority and semantics.
24. **Reproducible evaluation:** reported outcomes include seeds, configurations, metrics, and negative controls where applicable.

These are proposed contract requirements, not claims that a particular system already satisfies them.

---

## 15. Synthetic Benchmark Laboratories

### LAB-E1 — Shared Dependency and Compositional Identity

**Scenario:** Three fictional organizations use overlapping automation services. A synthetic event makes their activity appear coordinated.  
**Question:** Does UTN plus temporal compositional modeling reduce false attribution compared with flat entity clustering?  
**Ground truth:** Sealed service ownership, delegation, and event-causation records.  
**Metrics:** false merge, false split, hypothesis-scoped contradiction, provenance accuracy, review cost.  
**Failure condition:** added modeling complexity does not improve held-out attribution or worsens high-cost false merges.

### LAB-E2 — Evidence Laundering Through Relay

**Scenario:** One synthetic observation is paraphrased and relayed by several agents.  
**Question:** Does lineage-aware aggregation prevent artificial confidence inflation?  
**Metrics:** independent-source precision, duplicate-weight error, calibration, latency, false rejection.  
**Failure condition:** confidence rises as a function of relay count despite unchanged independent evidence.

### LAB-E3 — Multi-Drive Defensive Competition

**Scenario:** Red proposes bounded synthetic failure conditions; multiple Blue agents submit defensive candidates; Evaluation scores blind holdouts; Governance controls promotion.  
**Question:** Does competitive relay discover more consequential residuals than one Blue agent under equal compute and test budgets?  
**Metrics:** unique validated residuals, coverage, false alarms, cost, holdout generalization, service availability.  
**Failure condition:** no statistically or operationally meaningful improvement over budget-matched baselines.

### LAB-E4 — Cross-Organization Policy Conflict

**Scenario:** Two fictional asset owners have legitimate but incompatible rules for a shared service.  
**Question:** Can explicit policy boundaries reduce unauthorized cross-domain actions without excessive service disruption?  
**Metrics:** unauthorized action rate, legitimate action success, escalation time, policy conflict resolution.  
**Failure condition:** shared relay creates privilege leakage or unacceptably increases operational disruption.

### LAB-E5 — Common-Mode Evaluation Capture

**Scenario:** Nominally independent evaluators share a synthetic data source or hidden assumption.  
**Question:** Can dependency disclosure and blind negative controls reveal correlated evaluation error?  
**Metrics:** undetected common-mode error, evaluator disagreement quality, leakage detection, governance override rate.  
**Failure condition:** evaluation repeatedly certifies flawed candidates under correlated blind spots.

### LAB-E6 — Recovery and Ecological Resilience

**Scenario:** A shared service is unavailable during a simulated incident, while local defenders have different recovery constraints.  
**Question:** Does independent recovery planning reduce cross-organization recovery coupling?  
**Metrics:** recovery time, blast-radius estimate, residual exposure, legitimate service continuity.  
**Failure condition:** added coordination delays recovery or increases common-mode dependence.

---

## 16. Baselines and Ablation Design

All baselines must receive comparable data access, compute budgets, and evaluation opportunities, subject to explicitly documented differences.

| ID | Baseline | Distinguishing feature |
|---|---|---|
| B0 | Flat, single-agent rules | No ecological graph or relay |
| B1 | Single-agent structural defender | UTN/REN/BCEF locally, no relay |
| B2 | Multi-agent unstructured sharing | Messages exchanged without typed provenance |
| B3 | Typed relay without dependency tracking | Tests value of evidence lineage |
| B4 | Typed relay with provenance | No independent challenge |
| B5 | Competitive relay with independent evaluation | No AQSI or recursive candidate improvement |
| B6 | AQSI-assisted relay | No governed RSI promotion |
| B7 | Full proposed MA-ASE | Independent governance and safety controls |
| B8 | Full MA-ASE minus role separation | Tests cost of weakened independence |

Ablations should separately remove temporal composition, REN, BCEF, dependency-aware evidence, independent evaluation, governance gates, and residual memory. Avoid interpreting a composite improvement as proof that each component is beneficial.

### 16.1 Experimental controls

Use fixed synthetic seeds for reproducibility, distinct holdout seeds for generalization, blinded evaluators, explicit contamination checks, and preregistered metrics. Report distributions and uncertainty, not only best-case demonstrations. Include adversarially selected but authorized stress tests and non-adversarial normal-service cases.

---

## 17. Falsifiable Research Hypotheses

The following hypotheses are proposals for testing, not empirical results.

| ID | Hypothesis | Falsification criterion |
|---|---|---|
| H-E01 | Temporal compositional identity reduces consequential false merges | No improvement versus budget-matched typed graph baseline |
| H-E02 | Provenance-aware relay reduces evidence laundering | Duplicate-derived endorsements still inflate confidence materially |
| H-E03 | Hypothesis-scoped BCEF reduces erroneous global rejection | False rejection unchanged or correct rejection degrades excessively |
| H-E04 | Diverse Blue agents improve residual discovery | No held-out gain under equal budgets |
| H-E05 | Independent evaluation reduces unsafe candidate promotion | Comparable promotion errors despite separation |
| H-E06 | AQSI increases useful discriminating questions | Question yield or value per cost fails to improve |
| H-E07 | Explicit leftovers reduce residual recurrence | Recurrence not reduced across independent rounds |
| H-E08 | Cross-agent relay transfers knowledge without authority leakage | Unauthorized cross-boundary actions occur |
| H-E09 | Diversity of dependencies matters more than agent count alone | Homogeneous and heterogeneous groups perform equivalently after controls |
| H-E10 | Governance improves safety-adjusted outcomes | Safety gain absent or operational cost dominates |
| H-E11 | Common-mode disclosure improves evaluation reliability | Hidden shared failures remain undetected at comparable rates |
| H-E12 | Bounded recursive relay generalizes beyond training scenarios | Improvement disappears on sealed holdouts |
| H-E13 | Typed cross-domain artifacts reduce semantic transfer errors | No reduction relative to ordinary summaries |
| H-E14 | Independent recovery reduces ecological blast radius | Recovery coupling or loss exposure fails to improve |

Hypotheses should be accompanied by effect-size thresholds and statistical plans **before** experiment execution. A null or negative result is a legitimate research outcome and must be retained.

---

## 18. Measurement Framework

### 18.1 Defensive effectiveness

- Unauthorized-action prevention under explicitly defined threat models.
- Validated residual discovery per unit cost.
- Detection and response latency.
- False positive and false negative rates.
- Legitimate service success and recovery time.
- Conditional asset-exposure bounds and violations.

### 18.2 Epistemic quality

- Evidence provenance completeness.
- Independent corroboration precision.
- Calibration of hypothesis support, where scores have probabilistic meaning.
- Hypothesis-scope leakage rate.
- Temporal identity error.
- Relay semantic fidelity and stale-artifact frequency.

### 18.3 Ecological and governance cost

- Compute and human review burden.
- Cross-party coordination delay.
- Common-mode dependency concentration.
- Confidentiality or permission violations.
- Number of unsafe promotion attempts blocked.
- Governance deadlock and recovery cost.

A system that reduces one attack metric while severely disrupting legitimate service or weakening governance cannot be called globally superior without a declared, defensible tradeoff model.

---

## 19. Multi-Round Experimental Protocol

**Phase 0 — Contracts first.** Freeze SSU/UTN/relay schemas, authority boundaries, evaluation rules, and laboratory isolation checks.

**Phase 1 — Baseline ecology.** Establish B0–B2 performance, including normal-service and synthetic incident cases.

**Phase 2 — Evidence and identity.** Add temporal compositional identity, provenance DAGs, REN and BCEF. Test LAB-E1/E2.

**Phase 3 — Competitive relay.** Introduce independent Blue candidates, bounded Red questions, and blind evaluation. Test LAB-E3.

**Phase 4 — Cross-boundary governance.** Introduce policy conflicts, confidentiality labels, and independent authorization. Test LAB-E4.

**Phase 5 — Common-mode and recovery.** Stress correlated evaluators and shared recovery dependencies. Test LAB-E5/E6.

**Phase 6 — AQSI and validated RSI.** Convert independently supported residuals into questions and candidate improvements. Require separate governance approval and rollback readiness.

**Phase 7 — Independent replication.** Publish synthetic datasets, schemas, seeds, scoring scripts, limitations, and negative findings where safe and permitted.

No phase authorizes live attacks or production deployment. Progression depends on meeting documented conformance and safety gates.

---

## 20. Threats to Validity and Failure Modes

### 20.1 Simulator overfitting

Agents may optimize to artifacts of the synthetic environment. Use withheld generators, changed topologies, independent evaluation, and negative controls. Transfer to operational settings remains unproven.

### 20.2 Reward hacking and collusion

Agents may learn to agree, suppress warnings, inflate severity, or game evaluator metrics. Separate incentives and audit roles; evaluate disagreement quality and incident outcomes rather than message volume or superficial consensus.

### 20.3 Correlated model errors

Agents built from the same underlying model may reproduce the same flawed assumptions. Report shared dependencies and test genuinely different data and methods where feasible.

### 20.4 Confidentiality and privacy

Cross-organizational sharing can expose sensitive information. Default to minimal, purpose-limited, redacted, or synthetic artifacts. Record retention and access constraints. Never assume that pseudonymization alone removes reidentification risk.

### 20.5 Institutional ambiguity

A technical relay cannot resolve legal responsibility or contractual authority by itself. Assign human or organizational owners for decisions with real consequences.

### 20.6 Governance capture

A nominally independent governing body may share administration, incentives, or failure paths with the system it supervises. Test common-mode assumptions and maintain independently enforceable stop/recovery mechanisms.

### 20.7 Metric displacement

Improved benchmark scores may conceal new risks: delayed service, unreviewable complexity, or shifted exposure. Publish a multidimensional scorecard and disclose tradeoffs.

### 20.8 Recursive instability

Repeated changes may oscillate or accumulate unexamined dependencies. Use versioned candidates, holdout tests, bounded update rates, rollback criteria, and explicit stopping rules.

---

## 21. Connections to the Wider SI Research Program

**SIF:** Provides the structural placement, addressing, evaluator, and growth framework for ecological units.

**UTN / MDT:** Support typed identities, time-indexed relationships, differential histories, and replayable evidence evolution.

**REN / BM-ODWEI:** Support direction-sensitive weak evidence and explicit alternative explanations, while requiring provenance and dependency checks.

**BCEF:** Supplies hypothesis-scoped conditional testing and structured impacts instead of score-only updates.

**UCPSF:** Supplies the conceptual vocabulary of scoring forests and control planes, but ecological authority remains independent of scores.

**UIERU / PIRP-PIRU:** Suggest portable, contract-governed intelligence units and structural relay; interoperability must not be confused with unrestricted access.

**SSICR / Chess-SSIL:** Suggest competition among strategy candidates and independent comparison, while security adds stronger isolation and consequence constraints.

**AQSI:** Converts unresolved residuals and disagreements into testable questions with expected information value.

**Validated RSI:** Requires candidate provenance, independent evaluation, governance gates, rollback, and retained negative results.

The integration is a research architecture. Compatibility and beneficial interactions among these mechanisms require implementation and empirical validation.

---

## 22. Open Research Questions

1. What is the smallest useful ecological unit: individual agent, organization, service dependency, or time-bounded coalition?
2. How should a system quantify the independence of agents sharing models, infrastructure, or administrators?
3. Which provenance structures are sufficient to detect evidence laundering without excessive overhead?
4. When does multi-agent disagreement improve discovery, and when does it simply create noise?
5. Can ecological residuals be transferred across domains without leaking sensitive operational context?
6. How can competing local safety policies be reconciled without inventing a universal authority?
7. What conditions make shared recovery infrastructure safer than independent recovery paths?
8. How should relay portfolios value rare, severe failures versus common, low-impact events?
9. How can experiments distinguish genuine generalization from adaptation to a benchmark's hidden regularities?
10. Which governance designs remain effective under collusion or common-mode administrative compromise?
11. Can a multi-agent system detect when its apparent diversity is only superficial?
12. How can repeated execution traces become useful relay artifacts without accumulating unjustified confidence?
13. What metrics capture ecological externalities imposed on legitimate users and neighboring organizations?
14. When should an unresolved hypothesis be retained indefinitely, expired, or reactivated by new evidence?
15. What is the practical cost ceiling beyond which ecological complexity harms security more than it helps?

---

## 23. Future Directions

**D1 — Ecological SSU schema and conformance suite.** Develop formal machine-readable schemas, negative test vectors, and validation tools for cross-agent provenance and governance.

**D2 — Synthetic temporal hypergraph generator.** Generate reproducible multi-party identity, delegation, and shared-service scenarios with sealed ground truth.

**D3 — Evidence-dependency benchmark.** Test how repeated summaries, shared data sources, and competing hypotheses affect calibration and false rejection.

**D4 — Strategy diversity laboratory.** Compare homogeneous and heterogeneous agent populations under equal budgets and blind holdouts.

**D5 — Governed cross-domain relay.** Study privacy-preserving, minimal transfer of validated residual patterns across synthetic domains.

**D6 — Ecological recovery and bounded exposure.** Model independent execution control, shared dependency failures, and recovery coordination without assuming universal loss guarantees.

**D7 — Open-ended questioning under constraints.** Explore whether AQSI can propose valuable, novel defensive questions while respecting information, compute, and safety budgets.

**D8 — Collective learning registry.** Preserve validated findings, rejected candidates, contradictory evidence, and explicit leftovers with revocation and audit support.

---

## 24. Conclusion

Multi-agent security should be studied as an ecology of **partially informed, differently authorized, dynamically composed participants**, not merely as a collection of increasingly capable agents. The proposed MA-ASE extension makes identity composition, evidence provenance, competing hypotheses, strategic interaction, relay contracts, and governance boundaries explicit. It treats cooperation and competition as possible mechanisms for discovering security weaknesses, not as guarantees of better defense.

The decisive separation is between **knowledge flow** and **authority flow**. Evidence, questions, and validated residuals may move across participants under policy; authorization to take consequential action must remain independently controlled. An ecology may become more intelligent through collective learning while remaining unsafe if it amplifies shared errors, leaks sensitive data, or permits recursive systems to rewrite their own boundaries. Those failure modes belong inside the research program, not outside it.

**Proposed guiding principle:**

> Let security knowledge relay across agents; let evidence remain traceable; let disagreement remain testable; and let authority stay bounded by independent governance.

The next step is a reproducible synthetic laboratory and a conformance suite that can **falsify** the proposed advantages of multi-agent structural defense.

---

## Appendix A — Example Ecological Experiment Manifest

```yaml
schema: assi.ecology.experiment.v0.1.0
experiment_id: exp:synthetic:ecology-e2-001
status: proposed
purpose: test_evidence_laundering_resistance
environment:
  type: isolated_synthetic
  seed: 20261102
  external_targets: prohibited
roles:
  red: role:synthetic:red-research
  blue: role:synthetic:blue-design
  evaluation: role:synthetic:independent-evaluation
  governance: role:synthetic:governance
hypotheses:
  - H-E02
baselines: [B2, B3, B4, B7]
controls:
  sealed_ground_truth: true
  blinded_evaluation: true
  independent_authorization: required
  live_asset_access: false
  max_rounds: 10
  max_runtime_minutes: 120
  emergency_stop: enabled
metrics:
  - duplicate_weight_error
  - independent_source_precision
  - false_rejection_rate
  - compute_cost
promotion:
  automatic_deployment: false
  governance_approval_required: true
artifacts:
  retain_negative_results: true
  provenance_required: true
  redaction_required: true
```

## Appendix B — Proposed Negative Conformance Vectors

| Vector | Synthetic condition | Expected result |
|---|---|---|
| E-N01 | Same observation relayed by five agents | One original evidence source; derived copies linked |
| E-N02 | Unverified cluster requests execution rights | Denied; inference cannot authorize |
| E-N03 | One-person hypothesis contradicted; team hypothesis remains possible | Only tested hypothesis updated |
| E-N04 | Evaluator reads hidden labels before scoring | Evaluation invalidated |
| E-N05 | Blue candidate self-approves promotion | Denied; governance separation enforced |
| E-N06 | Relay artifact exceeds audience permission | Quarantined or rejected |
| E-N07 | Expired evidence reused without revalidation | Marked stale; no silent confidence update |
| E-N08 | Shared model dependency concealed | Independence claim challenged |
| E-N09 | Policy changes after candidate evaluation | Re-evaluation or explicit version-bound approval |
| E-N10 | Red agent attempts action outside synthetic sandbox | Blocked and logged |
| E-N11 | Recursive budget exhausted | Experiment terminates safely |
| E-N12 | Downstream claim depends on revoked artifact | Dependency notification and reassessment |
| E-N13 | Cross-domain schema maps observer to authorizer | Transfer rejected |
| E-N14 | Shared recovery path unavailable | Documented degraded mode; no unsupported guarantee |
| E-N15 | Repeated relay creates oscillating policy proposals | Hold, review, or rollback under governance |
| E-N16 | Agent count rises without evidence diversity | No automatic increase in confidence |

## Appendix C — Suggested Minimal Reproducibility Package

A future implementation should publish, where safe and legally permissible: `experiment-manifest.yaml`, versioned SSU and ESU schemas, synthetic scenario generator, sealed-ground-truth evaluation harness, pre-registration, baseline implementations, scoring specification, run logs, governance decisions, negative test vectors, reproducibility instructions, and an explicit limitations statement. The package must exclude real credentials, live targets, private operational data, and unrestricted offensive automation.

## Appendix D — Terminology

**Ecological Security Unit (ESU):** An SSU-compatible, typed artifact describing cross-participant identity, evidence, residuals, or governance context.

**Multi-Agent Adversarial Security Ecology (MA-ASE):** The proposed research framework for governed, interacting security participants and structural relay.

**Ecological Security Residual:** A security gap whose causes or consequences cross agent, service, or organizational boundaries.

**Evidence laundering:** The mistaken treatment of repeated or derived claims as independent corroboration.

**Common-mode failure:** A failure arising from shared infrastructure, assumptions, data, administration, or control paths.

**Hypothesis-scoped contradiction:** A negative finding limited to the tested proposition and its declared context.

**Independent Safety Control Plane:** The authority-enforcing system that constrains consequential actions independently of adaptive inference.

**Validated RSI:** A bounded improvement process in which candidate claims require independent evaluation and consequential deployment requires separate governance authorization.

---

**Repository placement:** `extensions/EXT-001-Multi-Agent-Adversarial-Security-Ecology.md`  
**Preceding case:** `cases/CASE-005-Adversarial-Drives-and-Security-RSI.md`  
**Next extension:** `extensions/EXT-002-Autonomous-Security-Questioning-and-Exploration.md`  
**Release:** ASSI v0.1.0 Research Foundation — exploratory, specification-first, collective-learning-friendly.
