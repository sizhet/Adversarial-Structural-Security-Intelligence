# ASSI-010 — ASSI Grand Architecture and Structural Security Units

**Adversarial Structural Security Intelligence (ASSI)**  
**Version:** v0.1.0 — Research Foundation  
**Status:** Architectural proposal; not an implemented or validated security product  
**Date:** 2026-11-02  
**Repository:** `Adversarial-Structural-Security-Intelligence`  
**Series:** ASSI-010 of ASSI-001–012

## Abstract

Adversarial Structural Security Intelligence (ASSI) proposes an integrated, auditable architecture for understanding, constraining, testing, and improving the security of complex asset-bearing systems. Its motivating distinction is that cryptographic validity, business legitimacy, and acceptable systemic exposure are separate properties. ASSI combines a structural trust and asset graph, compositional identity hypotheses, directional evidence assessment, bidirectional conditional testing, independent authorization controls, adversarial simulation, security-residual accounting, and governed recursive improvement. The architecture uses canonical **Structural Security Units (SSUs)** and explicit contracts to connect otherwise heterogeneous components. It treats intelligent scoring as advisory unless an independently governed policy explicitly delegates a bounded decision. It prioritizes bounded loss and recoverability over claims of perfect detection. This document specifies functional domains, unit types, information flows, trust boundaries, state transitions, failure modes, and a falsifiable validation roadmap. All performance benefits remain hypotheses until measured against strong baselines.

**Keywords:** structural intelligence; security architecture; trust relocation; authorization; UTN; REN; BCEF; control plane; adversarial drives; security residual; validated RSI; provenance; bounded loss.

---

## 1. Purpose, Scope, and Architectural Commitments

ASSI-001–003 motivate the shift from cryptographic correctness to structural security and identify relocated trust as an explicit engineering responsibility. ASSI-004–006 develop compositional naming, directional weak-evidence reasoning, and hypothesis-scoped bidirectional IF feedback. ASSI-007–009 address independent authorization, adversarial drives, residual discovery, and validated recursive improvement. **ASSI-010 integrates those elements into one contract-first architecture.**

The proposed initial domain is cryptocurrency custody and transaction authorization, but the architecture is designed for later evaluation in cloud administration, enterprise identity, AI-agent execution, and other high-impact systems.

The architecture commits to:

1. **Observations before attribution.** Directly observed facts are not silently promoted into inferred identity or control claims.
2. **Explicit trust boundaries.** Every critical decision has an identifiable authority, dependency, and failure domain.
3. **Hypothesis-scoped inference.** Evidence against one person does not automatically disprove a shared team or coalition.
4. **Independent enforcement.** Adaptive models cannot bypass immutable or separately governed safety controls.
5. **Bounded exposure.** Security objectives include maximum credible loss, containment time, and recovery capacity.
6. **Auditable evolution.** Simulated improvements require independent evaluation and authorized promotion.
7. **Open-world uncertainty.** Unknown, conflicting, stale, and insufficient evidence remain first-class states.

**Non-goals:** ASSI does not claim that public-chain data alone identifies real people; does not replace cryptographic verification, hardware key protection, established security engineering, or incident response; does not authorize autonomous offensive operations against real systems; and does not establish that RSI guarantees safety.

## 2. The Grand Architecture: Six Functional Domains

### Domain D1 — Structural Asset and Trust Intelligence

Constructs a time-aware graph of assets, accounts, wallets, keys, signing services, contracts, identities, roles, organizations, network dependencies, policy authorities, and recovery mechanisms. It captures *who can cause what action under which conditions* and *which components share a failure domain*.

**Outputs:** AssetUnit, TrustDependencyUnit, ControlBoundaryUnit, ExposureUnit, and graph snapshots.  
**Core question:** If one component or principal is compromised, what can it authorize, alter, or disable?

### Domain D2 — Structural Evidence and Identity Intelligence

Uses UTN typing and naming, REN directional evidence assessment, and MDT temporal deltas. It maintains competing individual, group, coalition, shared-service, and independent-control hypotheses without treating behavioral similarity as identity proof.

**Outputs:** EvidenceUnit, IdentityHypothesisUnit, CompositionUnit, EvidenceDependencyUnit.  
**Core question:** Which interpretations are supported, contradicted, or still unresolved?

### Domain D3 — Conditional Reasoning and Scoring Intelligence

BCEF generates and evaluates forward, reverse, counterfactual, and contradiction IF tests. Its structured impacts may revise scores, provenance links, hypothesis portfolios, or proposed follow-up tests. Correlated evidence is tracked to prevent double counting.

**Outputs:** IFTestUnit, ImpactUnit, ScoringSnapshot, QuestionCandidate.  
**Core question:** What conditions underlie a risk judgment, and what would falsify it?

### Domain D4 — Independent Authorization and Safety Control

Evaluates cryptographic validity, caller authority, business intent, contract semantics, asset exposure, transaction limits, separation of duties, and recovery constraints. **Hard policy decisions are enforced by a separately governed authority.** Advisory scoring may trigger review or tighter controls but cannot grant exemptions from hard constraints.

**Outputs:** AuthorizationRequestUnit, PolicyDecisionUnit, EnforcementReceipt, RecoveryEvent.  
**Core question:** Even if an attacker controls an upstream service, what irreversible damage remains possible?

### Domain D5 — Adversarial Security Laboratory

Runs authorized, isolated Red, Blue, Evaluation, and Governance Drives. Scenarios model compromised signing services, authorization drift, shared control failures, identity misattribution, recovery gaps, and strategic adaptation. Independent evaluators assess both attack and defense performance.

**Outputs:** ScenarioUnit, DriveUnit, EvaluationUnit, FailureTrace, ResidualUnit.  
**Core question:** Which assumptions break under adaptive opposition or compound failures?

### Domain D6 — Structural Relay, Validated RSI, and Governance

Transforms residuals into AQSI research questions and candidate improvements. Candidate defenses are tested against frozen baselines, held-out scenarios, and explicit safety constraints; approved changes enter a versioned relay registry. Rollback and termination remain available.

**Outputs:** ResidualUnit, QuestionUnit, ImprovementCandidateUnit, ValidationRecord, RelayRecord, GovernanceDecision.  
**Core question:** Which measured improvements can safely be retained and transferred?

### 2.1 End-to-end conceptual flow

```text
                   External observations / authorized telemetry
                                      |
                                      v
                    [D1 Asset + Trust Structural Graph]
                                      |
                                      v
                     [D2 UTN / REN / MDT Evidence]
                                      |
                                      v
                    [D3 BCEF + Hypothesis Portfolio]
                                      |
                      risk advice / proposed tests
                                      v
 Transaction request ----------> [D4 Independent Safety Plane] ---> Allow / Deny / Hold
                                      |                                |
                                      |                           Enforcement log
                                      v                                |
                         [Audit + Exposure Evidence] <---------------+
                                      |
                                      v
                       [D5 Isolated Adversarial Drives]
                                      |
                                Failure traces
                                      v
                          [Security Residual Registry]
                                      |
                                      v
                        [D6 AQSI + Validated RSI Relay]
                                      |
                         independently approved changes
                                      v
                     Versioned models / tests / policies

 IMPORTANT: D6 cannot unilaterally alter D4 hard safety invariants.
```

This is a logical architecture, not a required microservice topology. Some domains may share storage or compute, but **critical enforcement independence must be demonstrated**, not assumed from diagrammatic separation.

## 3. Structural Security Units (SSUs)

An SSU is a typed, versioned, provenance-bearing record describing a security-relevant object, hypothesis, test, decision, or change. SSUs provide interoperability across domains; they are not a claim that every unit carries the same semantics or authority.

### 3.1 Canonical envelope

```yaml
ssu_version: "0.1.0"
unit_id: "urn:assi:ssu:example-0001"
unit_type: "EvidenceUnit"
created_at: "2026-11-02T00:00:00Z"
observed_at: "2026-11-01T23:55:00Z"
valid_from: "2026-11-01T23:55:00Z"
valid_until: null
source:
  source_id: "synthetic-lab-01"
  source_class: "simulation"
  integrity_reference: "sha256:<illustrative-digest>"
provenance:
  parent_unit_ids: []
  transformation_id: null
  independence_group: "lab-trace-01"
assertion:
  subject_ref: "urn:assi:address:synthetic-A"
  predicate: "transferred_to"
  object_ref: "urn:assi:address:synthetic-B"
  epistemic_status: "observed"
confidence:
  value: null
  calibration_profile: null
scope:
  environment: "isolated-sandbox"
  chain_id: "synthetic"
  jurisdiction: null
policy:
  sensitivity: "internal-test"
  retention_class: "research"
  permitted_uses: ["evaluation"]
audit:
  schema_validation: "pending"
  reviewer: null
```

All IDs, timestamps, and fields in this example are illustrative. The authoritative schema is deferred to **SPEC-001**.

### 3.2 Mandatory distinctions

- **Observed:** directly recorded event or verified artifact, with explicit source limitations.
- **Derived:** deterministic or statistical transformation of observations.
- **Hypothesized:** defeasible interpretation of observed or derived material.
- **Validated:** a claim meeting a named, reproducible validation criterion; not a blanket assertion of truth.
- **Rejected / superseded:** retained for audit rather than silently erased.

Confidence values are meaningful only relative to their calibration procedure and target population. A numeric score is not automatically a probability.

### 3.3 Principal unit families

| Family | Representative units | Responsible domain | Distinctive invariant |
|---|---|---|---|
| Structural | Asset, Dependency, Boundary, Exposure | D1 | Explicit control and failure-domain references |
| Identity | TypedEntity, Composition, IdentityHypothesis | D2 | Hypothesis is not personal identification |
| Evidence | Observation, Evidence, Dependency, CounterEvidence | D2 | Source and dependence traceability |
| Reasoning | IFTest, Impact, ScoringSnapshot | D3 | Test scope and derivation recorded |
| Authorization | Request, PolicyDecision, EnforcementReceipt | D4 | Decision authority independently verifiable |
| Adversarial | Scenario, Drive, Evaluation, FailureTrace | D5 | Authorized, isolated execution scope |
| Evolution | Residual, Question, Candidate, Validation, Relay | D6 | Independent approval before promotion |

## 4. UTN and Compositional Identity Integration

The identity model is **many-to-many, overlapping, role-aware, and time-bounded**. A Name may denote an individual, role, group, coalition, service, or activity-specific composition. A single address can be jointly operated; a team can control several addresses; two independent groups can use the same service.

Represent identity hypotheses as a portfolio rather than forcing a single winner:

- H1: one operator controls addresses X and Y;
- H2: different operators within one team control X and Y;
- H3: independent operators share infrastructure;
- H4: unrelated operators exhibit coincidentally similar behavior.

A contradiction to H1 does **not** logically refute H2. Group identity persistence is not equivalent to membership persistence. Temporal revisions must preserve the earlier hypothesis, evidence basis, and change reason.

**Privacy boundary:** public-chain inference must not be represented as verified personal identity absent independently obtained, lawful, and appropriately authorized corroboration. Inference results must be treated as uncertain and contestable.

## 5. REN, MDT, and Evidence Provenance

REN scores evidence relative to a named direction or hypothesis. MDT captures changes in evidence, behavior, relationships, and controls over time. Their integration requires:

1. A direction field or decision target for each scoring context.
2. Source reliability separated from hypothesis relevance.
3. Explicit dependence groups for duplicated or correlated evidence.
4. Competing explanations, including shared-service and common-cause alternatives.
5. Counterevidence retained alongside supporting evidence.
6. Temporal validity windows and revocation/supersession events.

**Invariant:** Similarity is not identity; correlation is not control; repeated evidence is not independent corroboration.

## 6. BCEF: Conditional Tests and Structural Impacts

Four IF modes are proposed:

| Mode | Question | Typical effect |
|---|---|---|
| Forward IF | If H were true, what observations should follow? | Generates testable predictions |
| Reverse IF | Given observation E, how strongly does it distinguish H from alternatives? | Updates comparative evidence assessment |
| Counterfactual IF | Could E arise if H were false? | Identifies alternative causal explanations |
| Contradiction IF | Does E conflict with a necessary implication of H? | Narrows or rejects a *scoped* hypothesis |

Reverse inference must not confuse `H ⇒ E` with `E ⇒ H`. Impact is not restricted to a scalar score: it may propose reweighting, a split/merge of candidate compositions, a request for independent evidence, or a policy review. Such changes are **proposals subject to the receiving domain's authority**.

```yaml
impact_id: "urn:assi:impact:synthetic-01"
origin_test_id: "urn:assi:if:synthetic-07"
target_hypothesis_id: "urn:assi:hypothesis:H1"
result: "contradicted"
impact_scope: "single-operator-control"
actions:
  - action: "decrease_support"
    target: "H1"
  - action: "retain_alternative"
    target: "H2"
  - action: "request_independent_test"
    target: "H2-versus-H3"
evidence_dependency_groups: ["lab-trace-01"]
authority: "advisory-only"
```

A contradiction is meaningful only when its premises and applicability conditions hold. Unknown is not False. Recursive IF evaluation must have budgets, stopping conditions, and external checks against self-confirmation.

## 7. Independent Authorization: Safety and Advisory Planes

The safety plane should enforce hard constraints independently of the adaptive intelligence plane. Example hard constraints include transaction ceilings, segregated custody limits, restricted delegation, quorum requirements, contract allowlists where appropriate, and emergency freeze or recovery procedures.

A conceptual authorization sequence:

1. Verify transaction syntax and cryptographic signatures.
2. Verify principal, role, and delegation authority.
3. Bind the request to a specific approved business intent and asset scope.
4. Evaluate hard safety policy and current exposure budget.
5. Consult advisory structural risk evidence where policy permits.
6. Return `ALLOW`, `DENY`, or `HOLD_FOR_REVIEW` with a traceable decision receipt.
7. Record enforcement outcome and update exposure state atomically where possible.

**Fail-safe design:** stale risk models, unavailable inference, or policy-plane ambiguity must not silently turn a denial into an approval. Safe behavior depends on the transaction class and predefined operational policy; blanket fail-open is unacceptable for high-risk asset movement.

**Independence test:** separate services are not independent if they share a compromised administrative root, key, deployment pipeline, or recovery authority. Common-cause failure must be explicitly modeled and tested.

## 8. Adversarial Drives and Evaluation Separation

The laboratory defines four drives:

- **Red:** generate bounded, authorized adversarial scenarios in isolated test environments.
- **Blue:** propose detection, containment, and recovery responses.
- **Evaluation:** independently measure outcomes against preregistered objectives and held-out cases.
- **Governance:** approve scope, validate evidence quality, decide on promotion, and preserve rollback rights.

Scenario contracts must declare isolation guarantees, synthetic or authorized assets, prohibited external targets, resource budgets, stopping conditions, and an auditable experiment identifier. Production credentials and real asset transfers are excluded from the initial research laboratory.

An adversarial win in simulation is **not** proof of exploitability in production. A defensive win in simulation is **not** proof of real-world safety. Report simulator fidelity, coverage gaps, and distribution shift.

## 9. Security Residuals and Validated RSI

A Security Residual records a security-relevant shortfall not resolved by the current system. Residual classes include authorization gaps, excessive loss exposure, detection latency, identity uncertainty, recovery failure, governance failure, evidence gaps, and simulation mismatch.

The improvement loop is:

```text
Observed failure or limitation
    -> ResidualUnit
    -> AQSI QuestionUnit
    -> ImprovementCandidateUnit
    -> Isolated test + independent evaluation
    -> Governance decision
    -> Versioned RelayRecord
    -> monitored rollout / rollback
    -> next residual
```

A candidate must not promote itself. Evaluators must be sufficiently independent of the candidate generator; test suites must include held-out cases and adversarial variations. Track negative results and regressions, not just improvements. No adaptive component may rewrite the invariants governing its own approval.

## 10. Cross-Domain Contracts and Interfaces

| Interface | Producer → Consumer | Required payload | Safety condition |
|---|---|---|---|
| I-01 | D1 → D2 | Asset graph snapshot, trust boundaries | Provenance and timestamp |
| I-02 | D2 → D3 | Evidence + hypothesis portfolio | Explicit dependency groups |
| I-03 | D3 → D4 | Advisory risk + explanation | No authority to bypass hard policy |
| I-04 | D4 → D1/D5 | Decision and enforcement receipts | Immutable or tamper-evident log |
| I-05 | D5 → D6 | Evaluation and failure traces | Isolation and evaluator independence |
| I-06 | D6 → D2/D3 | Approved model/test revisions | Versioning, rollback, review |
| I-07 | D6 → D4 | Proposed policy revisions | Separate governance approval required |

### 10.1 Minimal conformance expectations

- Every consequential unit has a stable ID, type, version, source, and timestamp.
- Every inferred claim identifies its premises and alternative hypotheses.
- Every scoring update records the evidence lineage and avoids known double counting.
- Every authorization decision references the applicable policy version and authority.
- Every hard-deny condition remains non-overridable by advisory model output.
- Every experimental drive has an authorized scope and stop condition.
- Every promoted change has a reproducible validation record and rollback plan.
- Every structural merge or split is reversible at the record level and auditable.
- Every critical dependency has a failure-domain analysis.
- Every security claim declares its evidence level and applicability limits.

These are preliminary invariants. Detailed machine-checkable definitions belong in SPEC-001–006.

## 11. Lifecycle and State Machines

### 11.1 Evidence lifecycle

`INGESTED → NORMALIZED → REVIEWED → ACTIVE → SUPERSEDED/REVOKED/ARCHIVED`

Invalid or untrusted inputs may be quarantined. Archiving does not erase historical audit references.

### 11.2 Identity hypothesis lifecycle

`PROPOSED → TESTING → SUPPORTED / CONTESTED → REVISED / REJECTED / DEFERRED`

A supported hypothesis remains defeasible. A rejected individual-control hypothesis does not imply rejection of a team-control hypothesis.

### 11.3 Improvement lifecycle

`PROPOSED → SANDBOXED → INDEPENDENTLY_EVALUATED → APPROVED / REJECTED → STAGED → MONITORED → RETAINED / ROLLED_BACK`

Promotion requires explicit governance authority. No model score alone can transition a candidate to `APPROVED`.

## 12. Threat Model and Architectural Failure Modes

ASSI must model attacks on the **security intelligence system itself**, not only on its protected assets.

| Failure mode | Potential consequence | Required mitigation direction |
|---|---|---|
| Compromised signer | Unauthorized transfers or delegations | Independent limits, quorum, separation of duties |
| Shared administrative root | Multiple nominal controls fail together | Failure-domain isolation and independent recovery |
| Poisoned evidence | Incorrect attribution or risk scores | Provenance, source separation, counterevidence |
| Identity over-merging | Innocent entities grouped with attackers | Compositional hypotheses, false-merge audits |
| IF scope error | Incorrect rejection of a valid group hypothesis | Hypothesis-scoped contradiction tests |
| Feedback self-confirmation | Artificially rising confidence | Evidence lineage and independent holdouts |
| Simulator overfitting | Illusory defensive gains | Held-out scenarios and external validation |
| Reward hacking | RSI optimizes proxy rather than safety | Multimetric evaluation and governance gates |
| Policy bypass via AI | Irreversible loss despite risk detection | Non-bypassable independent enforcement |
| Recovery plane compromise | Failure to contain or restore | Independent recovery tests and authority controls |

Threats may be correlated. Risk evaluation should examine joint failure paths rather than multiply independent-failure probabilities without justification.

## 13. Security Objectives and Metrics

No single score adequately captures system safety. ASSI proposes a multidimensional scorecard:

**Preventive effectiveness:** unauthorized-action success rate, policy bypass rate, exposure-limit violations.  
**Containment:** maximum realized or simulated loss, peak accessible assets, time to isolate compromised authority.  
**Inference quality:** precision/recall, false merge/split rates, calibration error, abstention quality, counterevidence handling.  
**Operational burden:** false holds, transaction latency, reviewer workload, compute cost.  
**Evolution quality:** held-out improvement, regression rate, rollback success, retained residual reduction.  
**Resilience:** recovery time, restoration completeness, common-cause failure survivability.

A useful constrained objective is:

\[
\min_{\pi} \mathbb{E}[L(\pi)]
\quad \text{subject to} \quad
\operatorname{Exposure}(\pi) \leq L_{\max},
\quad \operatorname{PolicyInvariants}(\pi)=\mathrm{true}.
\]

Here \(\pi\) denotes a defense policy and \(L\) a defined loss function. Expected loss alone is insufficient: report tail-risk measures, adversarial worst-case scenarios within the test model, and uncertainty in the model itself. The exposure bound is an engineering target, not an absolute guarantee under unmodeled failures.

## 14. Benchmark Architecture and Baselines

ASSI-011 will elaborate four benchmark laboratories:

**BM-001 — Compositional Identity.** Synthetic, labeled overlapping teams and shared services. Compare against single-identity clustering and conventional graph heuristics. Evaluate false merges, false splits, temporal stability, and abstention.

**BM-002 — BCEF Evidence Revision.** Controlled evidence dependencies, contradictory observations, and competing hypotheses. Compare against one-way scoring and rule-only baselines. Evaluate hypothesis-scoped rejection accuracy, calibration, and computational overhead.

**BM-003 — Authorization and Bounded Loss.** Isolated compromised-signing-service simulations with configurable policy planes. Compare against signature-only checks and fixed-rule baselines. Evaluate unauthorized transfers prevented, exposure ceiling adherence, false holds, and latency.

**BM-004 — Adversarial RSI.** Multiple rounds of Red/Blue/Evaluation/Governance drives with held-out scenarios. Compare static controls, non-adversarial tuning, and ungoverned adaptive tuning. Evaluate out-of-distribution performance, regressions, and approval integrity.

All benchmarks must preregister metrics, publish scenario assumptions, and record negative results. Synthetic success does not automatically transfer to real operational settings.

## 15. Falsifiable Architectural Hypotheses

- **H-A1:** Explicit trust-dependency modeling reveals high-impact common-cause failure paths missed by component-only threat modeling.
- **H-A2:** Composition-aware UTN reduces false identity merges relative to single-operator assumptions on labeled overlapping-group scenarios.
- **H-A3:** Hypothesis-scoped BCEF reduces invalid negative conclusions under controlled alternative explanations.
- **H-A4:** Independent authorization constraints reduce simulated maximum loss under signer compromise relative to signature-only authorization.
- **H-A5:** Residual-driven adversarial relay improves held-out defense performance over static or unguided iteration without unacceptable regression.
- **H-A6:** Provenance-aware evidence dependency handling reduces overconfidence from correlated inputs.
- **H-A7:** Governance separation prevents unauthorized model-driven policy promotion under adversarial or faulty improvement candidates.

Each hypothesis can fail. A valid research outcome includes identifying the operating conditions where ASSI mechanisms add cost without measurable benefit.

## 16. Implementation and Validation Roadmap

### Phase 0 — Contract-first specification

Finalize SSU envelope, semantic distinctions, identity composition, IF impacts, authorization invariants, drive scope, and RSI governance contracts (SPEC-001–006). Build schema conformance tests before runtime integration.

### Phase 1 — Evidence and identity sandbox

Create labeled synthetic address/control datasets with overlapping and evolving teams. Implement provenance tracking, UTN naming, REN scoring, and BCEF impact traces. Measure against simple baselines.

### Phase 2 — Authorization sandbox

Model a signing service with simulated assets and independent policy enforcement. Inject authorized synthetic compromise scenarios. Test bounded exposure and recoverability.

### Phase 3 — Competitive drives

Add isolated Red/Blue agents and a separately configured evaluator. Generate residuals, register candidate improvements, and test against frozen and held-out scenarios.

### Phase 4 — Governed relay

Introduce explicit promotion approvals, staged rollouts, regression gates, rollback tests, and longitudinal residual tracking. No real-asset deployment is implied by completing these phases.

### Phase 5 — Cross-domain transfer

Evaluate which SSU contracts and control patterns generalize to other asset-bearing systems; document domain-specific exceptions and failures.

## 17. Governance, Safety, and Responsible Research

ASSI is defensive research. Experiments should use synthetic data, explicit authorization, and isolated infrastructure. Any real-world attribution must respect privacy, lawful access, evidentiary standards, and uncertainty. The system must support contestation, correction, and revocation of identity hypotheses.

Governance decisions should be traceable to accountable human or organizational authorities. Independent safety mechanisms should remain operational when the intelligence subsystem is unavailable or compromised. Red-team outputs should be access-controlled according to risk and must not be treated as authorization to target external systems.

## 18. Relationship to the ASSI Series

| Document | Primary contribution to ASSI-010 |
|---|---|
| ASSI-001 | Motivation: cryptographic validity versus structural security |
| ASSI-002 | Four cryptocurrency security contradictions |
| ASSI-003 | Trust relocation and security boundaries |
| ASSI-004 | Compositional UTN identity and dynamic naming |
| ASSI-005 | REN directional weak evidence and provenance |
| ASSI-006 | BCEF conditional tests and structural feedback |
| ASSI-007 | Independent authorization and safety controls |
| ASSI-008 | Adversarial drives and competitive relay |
| ASSI-009 | Residual-driven, validated recursive improvement |
| ASSI-011 | Benchmark laboratories and falsifiable hypotheses |
| ASSI-012 | General structural defense and transfer boundaries |

The detailed contracts are planned as SPEC-001–006, and applied demonstrations as CASE-001–005. This document is an integration blueprint, not a substitute for those specifications.

## 19. Open Research Questions

1. What is the minimum SSU schema that preserves necessary evidence and authorization semantics without excessive overhead?
2. How should dependency-aware evidence scores be calibrated across domains and changing distributions?
3. When should a composition hypothesis be split, merged, deferred, or revoked?
4. Which independent safety controls survive shared administrative, deployment, or recovery failures?
5. How can conditional reasoning remain interpretable without combinatorial explosion?
6. How can the laboratory estimate real-world transfer limits of simulated security gains?
7. What is the appropriate autonomy ceiling for RSI in high-value asset systems?
8. How should the system represent genuinely unknown adversarial capabilities?
9. Can a portable residual taxonomy support useful cross-domain security transfer?
10. Under which workloads do simpler controls outperform the full ASSI stack?

## 20. Conclusion

ASSI proposes a **structurally aware, evidence-grounded, adversarially tested, and independently governed** approach to complex-system security. Its unifying mechanism is not a single AI model or score but a chain of explicit contracts: trust and asset structures; compositional identity hypotheses; directional evidence and bidirectional conditional tests; bounded authorization; isolated adversarial evaluation; residual accounting; and validated, governed relay. The decisive distinction is between *learning to defend better* and *remaining safe enough when learning is wrong*. ASSI treats both as necessary, separately testable engineering obligations.

**Guiding maxim:** *Cryptography makes actions verifiable; structural intelligence makes their implications inspectable; adversarial evaluation makes defenses improvable; independent safety controls constrain loss when intelligence fails.*

---

## References and Related Research Directions

The following are conceptual anchors rather than claims of empirical validation of ASSI:

- NIST SP 800-207, *Zero Trust Architecture* (2020).
- NIST SP 800-53 Rev. 5, *Security and Privacy Controls for Information Systems and Organizations* (2020; subsequent updates).
- MITRE ATT&CK, adversary behavior knowledge base (consult current version for applied experiments).
- Saltzer and Schroeder, *The Protection of Information in Computer Systems* (1975): least privilege, separation of privilege, and economy of mechanism.
- Pearl, *Causality* (2009): causal and counterfactual reasoning foundations.
- de Kleer, *An Assumption-based TMS* (1986): explicit assumptions and competing interpretations.
- ASSI-001–009 and forthcoming ASSI-011–012, SPEC-001–006 (internal research series).

**Citation note:** These references motivate the architecture; a later literature review should verify bibliographic details, prior art, and comparative novelty before formal publication.

**License intent:** Apache-2.0 (repository-level license applies).
