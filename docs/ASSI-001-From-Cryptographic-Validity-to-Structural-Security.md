# ASSI-001 — From Cryptographic Validity to Structural Security

**Project:** Adversarial Structural Security Intelligence (ASSI)  
**Version:** v0.1.0 — Research Foundation  
**Status:** Research framework and testable hypotheses; not a deployed or validated security product  
**Date:** 2026-11-02  
**License:** Apache-2.0

## Abstract

Cryptographic validity is necessary for many digital asset operations, but it is not sufficient to establish that an operation is authorized in the broader organizational, economic, or security sense. A transaction can have a valid signature while violating the asset owner's intent, a risk policy, an operational separation-of-duties rule, or an acceptable loss boundary. Moreover, eliminating trust in one protocol layer may relocate trust and risk to key custody, transaction construction, signing infrastructure, smart-contract administration, human governance, and recovery procedures.

This paper introduces **Adversarial Structural Security Intelligence (ASSI)** as a research framework for explicitly modeling these dependencies, testing conditional evidence and authorization hypotheses, and continuously improving defensive controls through bounded adversarial simulation and independently validated structural relay. ASSI combines structural security graphs, compositional identity hypotheses, directional weak-evidence scoring, bidirectional conditional tests, independent authorization controls, security residuals, and governed recursive self-improvement. It treats adversarial learning as a source of candidate improvements, **not** as a substitute for hard safety limits, verification, or recovery.

**Keywords:** structural security; cryptographic validity; authorization intent; trust relocation; compositional identity; bidirectional IF; security residual; adversarial simulation; bounded loss; structural relay.

---

![Fig-001-ASSI-Grand-Architecture.png](figures/Fig-001-ASSI-Grand-Architecture.png)
    
*Figure 1. Proposed ASSI grand architecture: structural evidence and adaptive learning inform, but do not override, independently governed authorization and safety enforcement.*

---

## 1. The central distinction

A cryptographic verifier typically answers a narrow question: *Does this operation satisfy the protocol's verification rules under the relevant keys and state?* A security operator needs to answer broader questions:

- Was the operation requested by an appropriate principal for a legitimate purpose?
- Does it conform to current organizational policy and separation of duties?
- Does it create a dangerous change in authority, exposure, or recoverability?
- Can the system prevent or contain loss even when a component is compromised?
- Can the rationale for the decision be independently reconstructed and challenged?

A valid signature establishes neither the signer's uncompromised intent nor the legitimacy of the surrounding workflow. Likewise, a successfully executed smart-contract call does not by itself establish economic authorization.

We distinguish four concepts:

1. **Cryptographic validity:** a protocol-level proof or check succeeds.
2. **Contextual authorization:** the operation is permitted under independently defined ownership, role, purpose, and policy constraints.
3. **Structural security:** the system's interacting dependencies and controls keep risk within acceptable bounds, including under component failure or compromise.
4. **Adversarial resilience:** the system detects, limits, responds to, and learns from adaptive attacks without surrendering independent safety controls.

These are related but not interchangeable.

## 2. Trust is relocated, not automatically eliminated

Trust-minimizing protocols can reduce reliance on particular intermediaries, but a practical asset system still depends on other components. Examples include key generation and storage, wallet software, signing services, user interfaces, RPC providers, oracles, bridge operators, upgrade authorities, access-control procedures, incident response, and organizational decision makers.

**Trust Relocation Principle:** Reducing a trust dependency at one layer does not imply an equivalent reduction in total system security responsibility. The remaining dependencies must be explicitly identified, bounded, and independently tested.

ASSI proposes a **Structural Trust Graph** with typed nodes for assets, principals, credentials, services, contracts, policies, dependencies, and recovery mechanisms. Edges distinguish *observed* relationships from *inferred* relationships and carry provenance, time validity, confidence, and failure implications. The graph is not assumed to be complete.

A crucial output is the **loss-exposure path**: which assets could be affected if a particular key, signer, policy administrator, or workflow were compromised? This is a different question from whether an individual transaction passes a cryptographic check.

## 3. From transaction checks to structural authorization

ASSI separates hard safety decisions from probabilistic evidence scoring.

### 3.1 Hard policy plane

Examples of independently enforceable restrictions include asset segregation, transaction ceilings, allowlists where appropriate, separation of duties, approval quorums, time delays, emergency suspension, and limits on authority delegation. The applicable controls depend on the system's threat model. A risk model's high confidence must never override an explicit prohibition.

### 3.2 Evidence and intelligence plane

The intelligence plane can assess anomalies, intent inconsistencies, changes in authority, historical behavior, structural similarity, and competing explanations. Its results can trigger escalation, review, additional verification, or reduced operating limits. Such assessments are uncertain and must expose their evidence and counterevidence.

### 3.3 Independent recovery plane

A resilient system must plan for failures of both the primary authorization infrastructure and the intelligence layer. Recovery, audit, key rotation, asset isolation, and incident response should not depend entirely on the component whose compromise they are intended to contain.

**Design invariant:** No self-improving model or adversarial simulation component may unilaterally modify or bypass production safety boundaries.

## 4. ASSI research architecture

The proposed framework comprises six cooperating functional domains:

| Domain | Responsibility | Principal outputs |
|---|---|---|
| Structural Asset & Trust Graph | Represent assets, control paths, dependencies, roles, and exposure | Typed graph, provenance, attack and loss paths |
| Authorization & Policy Control Plane | Enforce independent constraints and examine contextual intent | Permit, deny, hold, escalate; auditable reasons |
| Structural Evidence Intelligence | Assess observations, identity hypotheses, and counterevidence | Scoring tree, competing hypotheses, confidence limits |
| Adversarial Simulation Laboratory | Run authorized, isolated red/blue/evaluation exercises | Reproducible scenarios and measured failures |
| Structural Relay & Validated RSI | Convert failures into questions and tested candidate changes | Security residuals, validation records, approved updates |
| Independent Safety & Recovery Plane | Bound loss and restore operations when other layers fail | Exposure ceilings, containment, rollback and recovery |

The domains are logically distinct even when implementations share infrastructure. Their separation of authority is a security property, not merely a software organization preference.

## 5. Evidence-grounded structural reasoning

ASSI draws on several related Structural Intelligence (SI) research directions:

- **UTN (Universal Typing and Naming):** type and name structural units, including individual, group, coalition, role-based, and time-bounded identity hypotheses.
- **REN (Relational Evidence Navigation):** evaluate directional similarity, weak evidence, and counterevidence without treating similarity as proof of identity.
- **MDT (Metric Differential Trees):** represent changes in structure, scores, and relationships over time.
- **BCEF (Bidirectional Conditional Evidence Feedback):** test hypotheses in forward, reverse, counterfactual, and contradiction-oriented directions, then return scoped impacts to the scoring structure.
- **UCPSF:** coordinate scoring and policy perspectives while preserving explicit control boundaries.
- **AQSI:** generate follow-up questions where evidence is missing, contradictory, or strategically valuable.
- **SSICR / UIERU / RSI:** organize competitive simulations, reusable findings, structural relay, and validated improvement.

These connections are proposed architectural integrations. Their incremental effectiveness must be demonstrated experimentally rather than assumed.

### 5.1 Hypothesis-scoped contradiction

Consider two blockchain addresses, X and Y. Evidence may weaken the hypothesis that one individual controls both, without weakening the different hypothesis that two members of the same team operate them. A contradiction must be applied to the **specific proposition** it tests; it must not automatically reject a broader group or organizational hypothesis.

Identity hypotheses should therefore support overlapping membership, role changes, multiple levels of control, and explicit time bounds. On-chain observations alone generally do not establish the real-world identity of a person.

### 5.2 Conditional feedback is more than a Boolean result

A bidirectional IF test should report its target hypothesis, assumptions, supporting and conflicting evidence, provenance, uncertainty, and proposed impact. That impact may change a score, an evidence dependency, a graph edge, a hypothesis portfolio, or the priority of the next test.

Crucially, evidence reused by several tests must not be counted as independent confirmations. ASSI requires dependency-aware aggregation and independent validation when possible.

## 6. Adversarial drives and security residuals

A security architecture cannot assume attackers remain static. ASSI proposes authorized adversarial **Drives** with distinct responsibilities:

- **Red Drive:** explore plausible attack objectives and failure paths in an isolated test environment.
- **Blue Drive:** propose detection, prevention, containment, and recovery measures.
- **Evaluation Drive:** independently measure outcomes, false positives, costs, and residual exposure.
- **Governance Drive:** approve, reject, or defer proposed changes according to explicit constraints.

After each exercise, the system records a **Security Residual**: an uncovered attack path, delayed detection, excessive exposure, failed recovery, missing evidence, flawed assumption, or other unresolved safety issue. Residuals become inputs to autonomous questioning and the next test cycle.

The proposed loop is:

`Scenario → Adversarial Drive → Evaluation → Security Residual → Question → Candidate Control → Independent Validation → Governed Relay`

Simulation is a way to discover weaknesses and evaluate candidates. It cannot prove the absence of unknown vulnerabilities. Recursive self-improvement can overfit to its own generated attacks; held-out scenarios, external assessments, and real-world incident lessons are therefore essential.

## 7. Security objectives and loss bounds

ASSI does not optimize only for the probability of intrusion. A practical objective must also account for severity, tail risk, recoverability, and operating cost.

A simplified research formulation is:

\[
\min_{\pi}\;\mathbb{E}[L\mid\pi]
\]

subject to enforceable policy constraints and an explicitly defined maximum acceptable exposure. Here, \(\pi\) denotes a defensive policy and \(L\) denotes loss under a specified threat model. This is a modeling objective, not a guarantee that all losses can be capped under every conceivable failure.

Evaluation should include:

- Attack success and unauthorized-authorization rates.
- Maximum reachable asset exposure after a component compromise.
- Detection and containment latency.
- False rejection of legitimate operations and service availability.
- Recovery time and completeness.
- Evidence calibration, traceability, and auditability.
- Cost of controls and cost of continuous improvement.
- Performance on held-out and independently designed adversarial scenarios.

**Bounded Loss Before Perfect Defense** is an engineering priority: when perfect prevention is unattainable, independently enforce limits on the damage a compromised component can cause.

## 8. Initial falsifiable hypotheses

The following are **research hypotheses**, not established results.

**H1 — Structural authorization:** Adding independent contextual authorization and exposure controls to cryptographic checks reduces simulated catastrophic-loss scenarios relative to a signature-validity-only baseline, at a measurable operational cost.

**H2 — Compositional identity:** Explicit group, coalition, and time-bounded identity models reduce false entity merges and false hypothesis rejections compared with single-operator assumptions on controlled datasets.

**H3 — Bidirectional evidence feedback:** Dependency-aware forward/reverse/counterfactual/contradiction tests improve hypothesis calibration and reduce unsupported identity assertions compared with similarity-only scoring.

**H4 — Adversarial relay:** Repeated red/blue/evaluation cycles with independently validated residual-driven updates improve held-out defensive performance relative to fixed policies or unvalidated self-improvement.

**H5 — Safety-plane independence:** Separately enforced asset and authority limits reduce maximum reachable exposure even when the intelligence or signing workflow is compromised, subject to the stated threat model.

Each hypothesis requires an explicit baseline, synthetic or authorized test data, measurable outcomes, failure criteria, and independent replication where feasible.

## 9. First benchmark roadmap

1. **Compositional UTN sandbox:** synthetic addresses, persons, teams, shared infrastructure, changing roles, and time-bounded group membership; measure false merges, false splits, and confidence calibration.
2. **BCEF hypothesis laboratory:** compare similarity-only, unidirectional conditional, and dependency-aware bidirectional reasoning; measure mistaken rejection of group hypotheses.
3. **Compromised signer defense:** in an isolated simulator, assume a signing component is compromised; test whether independent policy and exposure controls constrain unauthorized operations.
4. **Adversarial RSI evaluation:** run reproducible defensive improvement cycles with held-out scenarios, rollback tests, and separate evaluators.

These benchmarks do not require the handling of real user funds or attribution of real-world individuals.

## 10. Scope, limits, and responsible research

ASSI v0.1.0 is a conceptual research foundation. It does **not** claim that the framework is implemented, audited, or proven to prevent cryptocurrency theft. It does not establish responsibility for any specific publicized incident. News reports and incident narratives must be distinguished from verified technical facts, and all case studies must record their sources and uncertainties.

On-chain behavior can support structural hypotheses but rarely proves a natural person's identity without lawful, independently corroborated off-chain evidence. Research should minimize privacy harms and avoid publishing unverified accusations.

Adversarial experiments must be conducted only on systems and data for which testing is authorized, using isolated or otherwise explicitly approved environments. The framework's defensive objective does not justify probing third-party infrastructure without permission.

## 11. Relationship to the ASSI repository

This introductory paper defines the problem and overall research contract. Detailed treatment is assigned to:

- **ASSI-002:** Four Structural Contradictions of Cryptocurrency Security.
- **ASSI-003:** Trust Relocation and Structural Security Boundaries.
- **ASSI-004:** UTN and Compositional Identity Intelligence.
- **ASSI-005:** REN and Directional Weak-Evidence Intelligence.
- **ASSI-006:** Bidirectional Conditional Evidence Feedback.
- **ASSI-007:** Structural Authorization and Independent Control Planes.
- **ASSI-008:** Adversarial Security Drives and Competitive Relay.
- **ASSI-009:** Security Residuals and Validated Recursive Self-Improvement.
- **ASSI-010:** ASSI Grand Architecture and Structural Security Units.
- **ASSI-011:** Benchmark Laboratories and Falsifiable Security Hypotheses.
- **ASSI-012:** From Cryptocurrency Security to General Structural Defense.

Normative data and process contracts will be developed separately in `specs/SPEC-001` through `SPEC-006`; case studies and extensions will be developed in their respective directories. The architecture diagram is planned as `figures/Fig-001-ASSI-Grand-Architecture.png`.

## 12. Conclusion

Cryptographic verification is indispensable, but it answers only part of the security question. Complex asset systems require explicit models of trust dependencies, compositional control, contextual authorization, competing evidence, independent loss limits, and recovery. ASSI proposes to connect these concerns through Structural Intelligence and disciplined adversarial learning.

The central research proposition is not that AI can guarantee security. It is that **structural modeling can make security assumptions inspectable; conditional evidence tests can make judgments revisable; adversarial relay can make improvements systematic; and independent safety controls can keep learning failures from becoming unrestricted asset losses.**

---

### Research maturity statement

**ASSI v0.1.0 is a hypothesis-driven research framework.** Architectural components, benchmark outcomes, and cross-domain generality remain to be implemented and independently validated. This paper is intended to guide subsequent specifications, controlled experiments, and open collective research.
