# ASSI-012 — From Cryptocurrency Security to General Structural Defense

**Project:** Adversarial Structural Security Intelligence (ASSI)  
**Version:** v0.1.0 — Research Foundation  
**Status:** Research architecture and transfer hypotheses; not an empirically validated security system  
**Date:** 2026-11-02  
**Series:** ASSI-012 of ASSI-001–012  
**License:** Apache-2.0

## Abstract

Cryptocurrency systems expose an unusually clear security contradiction: a cryptographically valid action may still violate legitimate intent, organizational authority, acceptable asset exposure, or the assumptions on which trust was delegated. The same contradiction appears in cloud administration, enterprise authorization, software supply chains, autonomous AI agents, industrial control, and multi-party institutions. This paper generalizes the Adversarial Structural Security Intelligence (ASSI) research program beyond cryptocurrency without assuming that mechanisms effective in one domain automatically transfer to another. It identifies a portable *structural defense kernel*: typed and time-indexed trust relationships; Universal Typing and Naming (UTN) for compositional identity; Relational Evidence Navigation (REN) for direction-sensitive and weak evidence; Bidirectional Conditional Evidence Feedback (BCEF) for hypothesis-scoped testing; independent authorization and safety control planes; adversarial Red/Blue/Evaluation/Governance drives; Security Residuals; and governed, independently validated Recursive Self-Improvement (RSI). Domain-specific adapters supply assets, authorities, hazards, observability, and recovery semantics. We formulate transfer contracts, reference architectures, synthetic cross-domain cases, explicit non-transfer conditions, and falsifiable experiments. The central proposal is not that structural intelligence replaces cryptography, policy enforcement, or conventional security engineering. It is that **structural reasoning can complement them, while independent controls limit consequences when that reasoning is incomplete or wrong**.

**Keywords:** structural security; cross-domain defense; trust boundaries; compositional identity; UTN; REN; BCEF; authorization; safety control plane; adversarial relay; security residual; validated RSI; AI agents; cloud security; supply-chain security.

---

## 1. Why Generalize from Cryptocurrency?

Cryptocurrency provides a demanding starting point because signatures, transactions, custody arrangements, ownership claims, liquidity, and irreversible settlement can be observed or tested with unusually explicit artifacts. Yet the deeper problem is not peculiar to a blockchain. A credential can be valid while the actor using it is compromised; an authorized administrator can exceed the intent of a change request; an AI agent can execute an API call that is syntactically permitted but materially unsafe; a supplier can deliver a correctly signed component that violates the expected provenance or change-control process.

ASSI-001 through ASSI-003 distinguish **cryptographic validity**, **legitimate authorization**, **structural trust**, and **acceptable consequences**. ASSI-004 through ASSI-006 develop UTN, REN, and BCEF for identities and evidence. ASSI-007 establishes independent safety controls. ASSI-008 and ASSI-009 add adversarial drives, residuals, and validated learning. ASSI-010 integrates these into Structural Security Units (SSUs); ASSI-011 proposes benchmark laboratories. The present paper asks what survives transfer to other domains, what must change, and what cannot be inferred.

The generalization is a **testable design proposal**, not a declaration of universal applicability. A useful transfer preserves causal and authorization semantics, not merely similar-looking graphs.

### 1.1 The general structural security gap

Let an action be `a`, an actor or composition of actors be `s`, a resource be `r`, an environment be `c`, and a time be `t`. A conventional local validator may establish `Valid(a, c, t)`. Security additionally requires consideration of:

- **Authority:** Who may act, under which delegation and role composition?
- **Intent:** Is this the action that an accountable principal actually approved?
- **Exposure:** What immediate and downstream consequences can follow?
- **Evidence:** Which observations support the decision, and which alternatives remain plausible?
- **Boundary:** Which decisions may an adaptive component influence, and which controls remain independent?
- **Recovery:** Can the system contain, reverse, or compensate for a bad action?

A conceptual decision condition is:

`Permit(a) = Valid(a) AND Authorized(s,a,r,c,t) AND WithinIndependentLimits(a,c,t)`.

This is **not** a complete universal policy formula. It illustrates that validity is necessary in some systems but insufficient for safe execution. Different domains may add physical interlocks, regulatory constraints, separation of duties, or human approvals.

### 1.2 Four generalization questions

1. Which structural representations are portable across domains?
2. Which domain semantics must be provided explicitly by adapters?
3. How can transfer improve detection or decision quality without eroding independent enforcement?
4. How can a failed transfer become a Security Residual rather than an unexamined success claim?

---

## 2. A General Theory of Structural Defense Boundaries

A security boundary is not merely a firewall, key, account, or API permission. It is a constraint on **who can cause what consequence through which dependencies under which conditions**. The following boundaries should be represented separately:

| Boundary | Question | Cryptocurrency example | General counterpart |
|---|---|---|---|
| Credential | Is the presented proof valid? | Signature | API token, certificate, signed artifact |
| Identity | Who or what controls the actor? | Wallet operator or team | Human, service account, agent coalition |
| Authority | What is the actor permitted to do? | Custody mandate | IAM role, purchase approval, change authority |
| Intent | Was this action actually requested? | Withdrawal approval | Deployment request, agent task mandate |
| Consequence | How much harm can the action cause? | Asset drain | Data exfiltration, outage, unsafe actuation |
| Evidence | What is observed versus inferred? | Chain event and attribution | Audit event and operator attribution |
| Governance | Who may alter rules or models? | Custody policy board | Security governance, change advisory board |
| Recovery | Can harm be contained or undone? | Freeze or compensation | Rollback, credential revocation, safe shutdown |

These boundaries are connected but not interchangeable. Strong authentication does not prove correct authorization; high-confidence attribution does not authorize retaliation; good detection does not imply recoverability.

### 2.1 Trust relocation rather than trust elimination

Replacing a human approval with a smart contract moves trust to code, keys, deployment, oracles, and governance. Replacing an administrator with an AI agent moves trust to its tool permissions, instructions, observations, runtime, and supervisory controls. A structural defense system should record each relocation as an explicit dependency and should not call a system “trustless” merely because one trust intermediary disappears.

### 2.2 Bounded loss as a separate engineering objective

Perfect identification and prediction are unattainable as general assumptions. A defense architecture should therefore specify maximum permitted action scope, rate, exposure, privilege lifetime, blast radius, and recovery conditions independently of model confidence. Some physical or societal harms cannot be captured by a single monetary loss bound; the relevant constraints must be domain-specific and may be categorical prohibitions.

---

## 3. The Portable Structural Defense Kernel

We propose a **General Structural Defense Kernel (GSDK)** as a reference abstraction assembled from the ASSI mechanisms. GSDK is a research name for a set of interfaces and invariants, not a deployed software product.

### 3.1 Kernel components

1. **Structural asset and dependency graph:** resources, actors, delegations, dependencies, consequences, and temporal change.
2. **UTN identity layer:** typed names for observed entities, inferred actors, shared services, teams, coalitions, and unresolved identities.
3. **REN evidence layer:** evidence provenance, quality, directional relevance, alternative explanations, and dependence relationships.
4. **BCEF hypothesis testing:** forward, reverse, counterfactual, and contradiction tests with scoped conclusions.
5. **Scoring and policy advisory plane:** ranked hypotheses and proposed actions, explicitly non-authoritative unless independently permitted.
6. **Independent enforcement plane:** hard policy, exposure limits, approvals, interlocks, revocation, and emergency containment.
7. **Adversarial drives:** bounded Red/Blue experiments with independent Evaluation and Governance.
8. **Residual and validated-RSI layer:** typed failures, proposed improvements, held-out evaluation, approval, rollback, and audit.

### 3.2 A reference data flow

```text
Domain events / asset inventories / approvals / audit trails
                         |
                         v
             Typed observations + provenance
                         |
                         v
            UTN identities and trust relations
                         |
                         v
       REN evidence graph + competing hypotheses
                         |
                         v
       BCEF tests -> structured Evidence Impacts
                         |
                         v
        Advisory scoring / AQSI question portfolio
                         |
                  proposals only
                         v
      INDEPENDENT AUTHORIZATION & SAFETY CONTROLS
                         |
                  bounded execution
                         v
              Outcomes + recovery telemetry
                         |
                         v
         Security Residuals / adversarial lab
                         |
                         v
     Independent evaluation -> governance -> relay
```

The control plane is not downstream merely as an optional “final score.” It must have authority to deny, limit, delay, require human approval, or place the system in a safe state irrespective of an AI recommendation.

### 3.3 Kernel invariants

**K-01.** Observations, interpretations, hypotheses, and permissions have distinct types.  
**K-02.** Inferred identity never silently becomes verified identity.  
**K-03.** Contradictions are scoped to the hypothesis and conditions tested.  
**K-04.** Reused or correlated evidence cannot be counted as independent support without justification.  
**K-05.** Missing evidence is not automatically negative evidence.  
**K-06.** Model scores are not treated as calibrated probabilities without validation.  
**K-07.** Advisory intelligence cannot unilaterally override independent safety constraints.  
**K-08.** An experimental improvement cannot be promoted on the strength of its training or development scenarios alone.  
**K-09.** Governance decisions and model/policy versions are attributable and auditable.  
**K-10.** Transfer across domains requires explicit semantic mappings and a new validation claim.

---

## 4. Domain Adapters: What Must Not Be Abstracted Away

A general kernel is only meaningful if its domain adapters preserve essential distinctions. An adapter is a typed mapping, not a string substitution.

### 4.1 Adapter contract

Each adapter must declare:

- **Assets and protected interests:** funds, data, availability, physical safety, privacy, integrity, legal authority.
- **Actors and compositions:** persons, services, teams, automated agents, vendors, delegates, shared operators.
- **Actions and side effects:** reads, writes, transfers, deployments, physical actuation, irreversible decisions.
- **Authority semantics:** credential, role, delegation, approval, mandate, separation of duties, expiration.
- **Observability:** events available, delayed, missing, manipulable, and independently verifiable.
- **Threat model:** attacker capabilities, insider privileges, compromised dependencies, collusion, and environmental failures.
- **Independent controls:** mechanisms that can actually prevent or bound execution.
- **Recovery:** rollback, isolation, revocation, restoration, compensation, and incident command.
- **Hazard model:** unacceptable outcomes, including non-financial and non-reversible harm.
- **Evaluation boundaries:** permitted synthetic data, isolation, authorization, and independent review.

### 4.2 Example transfer mapping

| ASSI primitive | Cloud infrastructure | Enterprise workflows | AI agent systems | Software supply chain |
|---|---|---|---|---|
| Asset | Compute, secrets, data | Payment, records, approval | Tool access, external actions | Package, build, release |
| Compositional identity | Human + role + workload | Employee + team + delegate | Agent + operator + tools | Maintainer + CI + signer |
| Evidence | Logs, configuration history | Requests, approvals, audit | Traces, tool calls, outputs | Provenance, builds, attestations |
| BCEF hypothesis | Compromised service account | Collusive approval chain | Prompt/tool authority confusion | Compromised build dependency |
| Hard control | IAM, segmentation, quotas | Dual approval, spending limits | Tool allowlists, transaction caps | Protected branches, release gates |
| Residual | Privilege escalation gap | Separation-of-duties failure | Unsafe delegated action | Untrusted artifact promotion |

This table establishes *candidate analogies*, not evidence that an ASSI technique improves these systems.

---

## 5. UTN and Compositional Identity Across Domains

The classical one-account/one-actor assumption is fragile. A cloud role may be assumed by many workloads; one person may control multiple service identities; a vendor team may share deployment responsibilities; an AI agent may be assembled from a model, tools, orchestration service, and human sponsor. Identity is therefore often **compositional, overlapping, and time-dependent**.

### 5.1 Typed identity distinctions

A general UTN representation should distinguish:

- `ObservedIdentifier`: account, certificate subject, wallet, service principal, process ID.
- `InferredController`: an unverified explanation of who exercises control.
- `VerifiedPrincipal`: identity established under an explicit verification procedure.
- `CompositeActor`: team, coalition, shared service, or agent-plus-tools composition.
- `AuthorityRole`: a scoped permission, not a claim of personal identity.
- `TemporalMembership`: membership or control relationship valid during an interval.

For example, evidence that two deployments share a CI runner may support a *shared-service hypothesis* without supporting the claim that the same human authored both. This distinction matters both for accurate security response and for avoiding unjustified attribution.

### 5.2 Graph and hypergraph choices

A conventional graph can model roles and events as intermediate nodes. A hypergraph may better represent multi-party approval or simultaneous control. Neither representation is universally superior. Compare expressive adequacy, update complexity, false merges, false splits, query latency, and explainability under realistic domain workloads.

### 5.3 Hypothesis-scoped contradiction

Suppose two administrative actions are signed by different humans but occur through the same deployment service. The observation may contradict `H_person: same human operator`, yet remain compatible with `H_team: same operations team` and `H_service: shared deployment service`. The system must not turn rejection of `H_person` into rejection of all related hypotheses.

---

## 6. REN: Directional Evidence Without an Attribution Oracle

Security evidence has a direction: a log entry may be relevant to the question “Was this credential compromised?” but weakly informative about “Who initiated the compromise?” Similarity alone does not establish causation, control, or malicious intent.

REN generalizes through four functions:

1. **Question-relative relevance:** evaluate evidence relative to a named hypothesis, alternative, and decision context.
2. **Weak-evidence preservation:** retain tentative signals without presenting them as confirmed facts.
3. **Provenance and dependence:** record common sources, derived features, and missing observations.
4. **Directional exploration:** propose what additional observation would discriminate between hypotheses.

### 6.1 Example: anomalous cloud API activity

An unusual API call may support hypotheses of credential theft, legitimate automation, a scheduled migration, or misconfigured monitoring. REN should preserve these alternatives, their evidence dependencies, and the limitations of each signal. It should not collapse anomaly detection into a person-level accusation.

### 6.2 Failure modes

Directional relevance can become a disguised subjective score. To prevent this, the adapter must record the hypothesis, direction, source, scoring rationale, uncertainty, and independent evidence. Where probabilities are reported, calibration must be measured on representative held-out data. A score without such validation remains an ordinal or heuristic value.

---

## 7. BCEF: Conditional Testing Across Security Domains

BCEF extends evidence assessment from pattern matching to **explicit conditional tests**:

- **Forward IF:** If hypothesis `H` is true under assumptions `A`, what observation `E` should follow?
- **Reverse IF:** Given observation `E`, which competing hypotheses remain plausible? Reverse inference is not logical inversion.
- **Counterfactual IF:** Under a controlled change `do(X=x)` or a carefully defined alternative scenario, what should differ?
- **Contradiction IF:** Which specific hypothesis-condition pair is inconsistent with a reliable observation?

### 7.1 Avoiding the converse error

`H => E` does not establish `E => H`. For example, “compromised credentials may produce unusual access” does not mean every unusual access event proves compromise. Reverse reasoning requires alternatives, base rates where justified, source reliability, and the limits of observability.

### 7.2 Structured impacts

A BCEF result should produce more than a numeric score. Possible impact types include:

- revise support for a named hypothesis;
- invalidate a specific conditional assumption;
- propose splitting a composite identity;
- flag evidence dependence or provenance defects;
- request a discriminating observation;
- recommend containment for independent policy evaluation;
- create a Security Residual when a test reveals an unresolved safety gap.

### 7.3 Feedback without circular amplification

An IF result derived from existing evidence is not new independent evidence. Feedback must link to source observations and carry dependency metadata. The system should reject or discount self-reinforcing loops, cap iterative inference, and preserve the pre-update state for audit and rollback.

---

## 8. Independent Authorization: The Non-Transferable Safety Obligation

A transferable intelligence kernel does **not** imply transferable safety guarantees. A cloud service, an AI tool executor, and an industrial actuator have different failure costs, control surfaces, and recovery windows.

### 8.1 Two planes, distinct authority

**Adaptive structural intelligence plane:** analyzes evidence, scores alternatives, recommends investigation, suggests policy changes, and discovers residuals.

**Independent safety and authorization plane:** enforces allow/deny rules, least privilege, approvals, exposure limits, isolation, emergency stop, and versioned change control. It must not depend on the adaptive plane being correct to enforce its declared hard constraints.

### 8.2 Example control patterns

| Domain | Advisory proposal | Independent control |
|---|---|---|
| Cryptocurrency | Flag withdrawal as suspicious | Withdrawal cap, custody approval, key separation |
| Cloud | Flag unusual privilege escalation | IAM boundary, just-in-time access, network isolation |
| Enterprise | Flag collusive approval pattern | Separation of duties, independent payment release |
| AI agent | Recommend external API action | Tool allowlist, scoped credentials, transaction limit |
| Industrial | Predict abnormal control trajectory | Certified interlock, safe-state controller, human procedure |

The existence of a control is not proof that it works. Each claim requires a defined threat model, conformance tests, fault injection where safe, and independent verification. For safety-critical environments, established domain-specific engineering and certification obligations take precedence over this research architecture.

### 8.3 The governance recursion problem

If an adaptive system may rewrite its own guardrails, the “independent” plane ceases to be independent. Proposed control modifications must be versioned, reviewed by a separately authorized process, tested against invariant suites, and deployable with rollback. A learning system may recommend a change but cannot self-authorize it.

---

## 9. Four Cross-Domain Defense Laboratories

The BM-001–BM-004 laboratories of ASSI-011 can be adapted into cross-domain evaluation suites. All scenarios below are **synthetic and permissioned**.

### 9.1 LAB-X1: Cloud privilege and shared-service identity

**Scenario.** A shared deployment service performs actions for multiple teams. An attacker compromises one service credential; legitimate maintenance produces overlapping patterns.

**Research challenge.** Distinguish service sharing, team membership, and compromise without false person-level attribution.

**Baselines.** Flat account identity, conventional graph correlation, rule-based anomaly detection, and a domain-appropriate statistical model.

**Endpoints.** False merge/split rates, time-to-containment, legitimate deployment disruption, evidence provenance correctness, and exposure under independently enforced quotas.

**Failure condition.** ASSI increases unjustified attribution or disruption without a compensating, independently verified containment benefit.

### 9.2 LAB-X2: Enterprise multi-party authorization

**Scenario.** A purchase workflow includes initiator, manager, delegated approver, and payment operator. Temporary team changes and shared administrative systems complicate accountability.

**Research challenge.** Separate valid credentials from legitimate approval chains, and detect policy violations without assuming collusion from mere correlation.

**Baselines.** Static role-based access control, separation-of-duties rules, conventional workflow analytics.

**Endpoints.** Unauthorized approvals prevented, false blocks, decision latency, audit completeness, recovery time, and business continuity.

**Failure condition.** Structural scoring bypasses an independent approval rule or degrades operations beyond predeclared tolerances.

### 9.3 LAB-X3: AI agent tool-use authorization

**Scenario.** An agent receives a legitimate user task but encounters misleading external content or an overbroad tool credential. The agent proposes a high-impact external action.

**Research challenge.** Represent the distinction among user intent, retrieved content, agent plan, tool permission, and external consequence.

**Baselines.** Tool allowlists alone, policy checks without structural evidence, and human approval gates.

**Endpoints.** Unauthorized tool actions prevented, legitimate task completion, false refusals, audit traceability, approval burden, and damage bounded by tool constraints.

**Failure condition.** Agent-generated rationale is allowed to promote untrusted content into authorization, or a model can override the tool executor's hard limits.

### 9.4 LAB-X4: Software supply-chain release integrity

**Scenario.** A package is signed correctly, but the build pipeline or a dependency has been compromised; multiple maintainers and automated services contribute to release production.

**Research challenge.** Distinguish signature validity from provenance, authorization, and expected build lineage.

**Baselines.** Signature verification alone, conventional artifact attestations, rule-based release gates.

**Endpoints.** Unauthorized release promotion prevented, provenance defects detected, false holds, time to rollback, and integrity of independent release controls.

**Failure condition.** The structural system treats a valid signature as conclusive proof of safe provenance or cannot trace a claim to source artifacts.

---

## 10. A Typed Cross-Domain Transfer Contract

The following YAML is a **nonnormative research illustration**. Formal field validation and canonical schemas belong in the ASSI specification series.

```yaml
assi_transfer_contract:
  contract_id: TRANSFER-EXAMPLE-001
  version: "0.1.0"
  source_domain: cryptocurrency_custody
  target_domain: ai_agent_tool_execution
  research_status: hypothesis_only

  source_pattern:
    structural_problem: valid_credential_without_legitimate_intent
    source_asset_type: digital_asset
    source_authority: custody_mandate
    source_hard_control: independent_withdrawal_limit

  target_mapping:
    protected_interest: external_side_effect_and_user_resources
    observed_actor: agent_runtime_identity
    composite_actor_types:
      - human_sponsor
      - agent_runtime
      - tool_service
    action_type: external_tool_call
    authority_basis: user_mandate_and_tool_policy
    proposed_hard_control: independent_tool_executor_limit

  evidence_rules:
    distinguish_observation_from_inference: true
    preserve_competing_hypotheses: true
    track_common_source_dependencies: true
    prohibit_reverse_implication_shortcut: true
    preserve_hypothesis_scoped_contradiction: true

  safety_rules:
    adaptive_plane_may_override_hard_control: false
    deployment_requires_separate_approval: true
    rollback_required: true
    prohibited_experiment_targets: unauthorized_real_world_systems

  evaluation:
    primary_outcomes:
      - unauthorized_actions_prevented
      - legitimate_task_completion
      - false_refusal_rate
      - worst_case_exposure_under_threat_model
    required_baselines:
      - tool_allowlist_only
      - conventional_policy_gate
    held_out_domain_scenarios: required
    independent_evaluator: required

  open_assumptions:
    - target_tool_actions_have_enforceable_scope
    - user_intent_can_be_recorded_with_usable_provenance
    - external_content_is_not_authoritative_for_permission
```

### 10.1 Transfer lifecycle

`Candidate analogy -> Semantic mapping -> Threat-model review -> Contract conformance -> Synthetic benchmark -> Held-out validation -> Independent governance decision -> Bounded pilot or rejection -> Residual relay`.

A failed stage should yield a typed rejection or unresolved residual, not a silently revised success criterion.

### 10.2 Transfer conformance requirements

**T-01.** Source and target authority semantics are separately documented.  
**T-02.** Assets and protected interests are explicitly mapped.  
**T-03.** At least one plausible alternative hypothesis is represented for contested attribution.  
**T-04.** Observability differences and missing-data mechanisms are recorded.  
**T-05.** The target domain has independently enforceable safety limits or explicitly records their absence.  
**T-06.** Source-domain benchmark performance is not reported as target-domain performance.  
**T-07.** Baselines are credible for the target domain.  
**T-08.** Evaluation data are separated from tuning and policy design.  
**T-09.** Negative results and regressions remain in the relay record.  
**T-10.** No transfer grants permission for unauthorized real-world experimentation.  
**T-11.** Recovery and rollback are domain-specific and tested where feasible.  
**T-12.** A governance authority other than the candidate model approves promotion.

---

## 11. Structural Security Units and Interoperability

ASSI-010 introduces Structural Security Units (SSUs) as typed objects shared across layers. Cross-domain use requires a small portable envelope and explicit domain payloads.

### 11.1 Portable envelope

```yaml
structural_security_unit:
  ssu_id: SSU-EXAMPLE-001
  ssu_type: evidence_impact
  schema_version: "0.1.0"
  domain: cloud_infrastructure
  observed_at: "2026-11-02T10:00:00Z"
  assessed_at: "2026-11-02T10:05:00Z"
  source_references:
    - SYNTHETIC-EVENT-042
  hypothesis_id: H-SHARED-SERVICE
  scope:
    actor_composition: service_and_team
    valid_time_window: synthetic_test_window
  conclusion:
    status: unresolved
    rationale: shared_service_does_not_identify_human_operator
  proposed_effect:
    type: request_additional_observation
    enforcement_authority: none
  governance:
    experiment_only: true
    review_status: pending
```

A portable envelope does not imply that all domains use the same payload fields. Identity evidence, industrial hazards, financial exposure, and software provenance may require specialized schemas and validators.

### 11.2 Interoperability boundaries

The SSU interface should support provenance pointers, typed hypothesis references, evidence dependencies, temporal scope, uncertainty, authority restrictions, and lifecycle state. It should not require exporting sensitive raw data to a central shared repository. Federated or privacy-preserving exchange may be preferable where disclosure itself creates risk.

---

## 12. Adversarial Drives and Competitive Relay Beyond Finance

ASSI-008 proposes four complementary drives:

- **Red:** formulate bounded attack hypotheses and synthetic challenge scenarios.
- **Blue:** propose and test defensive policies, detection, and containment.
- **Evaluation:** independently measure outcomes, failures, and uncertainty.
- **Governance:** define permitted experiments, approval criteria, and non-bypassable limits.

The separation matters more than the label. A single model playing all roles may be useful for early exploration but does not constitute independent validation.

### 12.1 Cross-domain relay unit

A transferable relay record should include:

`scenario -> assumptions -> adversarial strategy class -> defense candidate -> baseline comparison -> observations -> residual -> proposed follow-up -> governance disposition`.

Relay must preserve failed candidates, unresolved questions, and the fact that repeated executions are new observations rather than necessarily new independent hypotheses. It must also record where a simulation is an inadequate model of production reality.

### 12.2 Avoiding unsafe autonomous escalation

Adversarial drives should run in isolated, authorized environments with synthetic assets and explicit scope. Autonomous experimentation must not infer permission to target third-party services, exploit live systems, or modify production policies. The ability to generate an attack hypothesis is not authority to execute it.

---

## 13. Security Residuals as a Cross-Domain Learning Currency

A **Security Residual** is a structured record of a gap between required and observed security behavior, including uncertainty about the gap. The term does not mean that every unexplained anomaly is a vulnerability.

### 13.1 Residual classes

| Class | General meaning | Example |
|---|---|---|
| `AUTH` | Authorization mismatch | Valid token exceeds user mandate |
| `IDENTITY` | Identity/composition ambiguity | Shared service mistaken for one person |
| `EVIDENCE` | Missing, correlated, or misleading evidence | Duplicated logs counted independently |
| `BOUNDARY` | Trust dependency not modeled | CI signer trusted without build provenance |
| `EXPOSURE` | Unbounded downstream consequences | Broad tool credential permits mass changes |
| `DETECTION` | Detection delay or false signal | Alert too late for containment |
| `RECOVERY` | Inadequate containment or restoration | Rollback not available |
| `GOVERNANCE` | Improper policy promotion | Candidate bypasses review |
| `SIMULATION` | Lab-production mismatch | Synthetic traces omit real latency |
| `TRANSFER` | Invalid cross-domain analogy | Custody assumptions do not fit physical safety |

### 13.2 Residual-to-question transformation

AQSI may propose questions such as: “Which missing observation distinguishes a shared-service explanation from credential compromise?” or “What independent limit would contain this action if identity inference is wrong?” These questions should be scored for expected information value, feasibility, safety, and cost. A question's novelty is not evidence of usefulness.

### 13.3 Validated RSI, not automatic self-authorization

Candidate improvements pass through specification checks, independent evaluation, regression tests, governance review, bounded rollout, and rollback readiness. RSI success must be measured on held-out cases and operationally relevant constraints. A model that optimizes benchmark scores while weakening enforcement or inflating false positives has not demonstrated a security improvement.

---

## 14. Cross-Domain Threats to the ASSI Architecture Itself

The structural defense system introduces new attack surfaces and epistemic risks.

### 14.1 Evidence poisoning and provenance laundering

An adversary may inject logs, synthetic identities, or fabricated attestations. The system must distinguish raw observations, transformed features, and independently corroborated sources. Provenance metadata alone does not prove that a source is trustworthy.

### 14.2 Feedback loops and score inflation

Repeated BCEF passes can manufacture apparent confidence from one observation. Track source dependency and reject circular support. Preserve prior scoring states for audit.

### 14.3 Model-induced overblocking

Aggressive anomaly detection may harm legitimate users, interrupt essential services, or create discriminatory effects. Evaluate false blocks, appeals, reversibility, and operational burden—not only attack detection.

### 14.4 Composite-identity misattribution

Graph clustering may incorrectly merge independent people or organizations. Maintain alternatives, scoped claims, time intervals, and explicit human review for consequential attribution.

### 14.5 Control-plane capture

A compromised governance process can approve unsafe rules even when model enforcement is technically separated. Apply separation of duties, immutable audit trails where feasible, emergency procedures, and external review appropriate to the threat model.

### 14.6 Distribution shift and adversarial adaptation

Attackers adapt to visible scoring rules; cloud environments and agent tools change rapidly. Hold out attack families, environments, and time periods. Report failures under distribution shift rather than averaging them away.

### 14.7 Privacy and concentration risk

Cross-domain identity graphs may aggregate sensitive behavioral data. Data minimization, retention controls, access restrictions, lawful processing, and scoped sharing are architectural requirements. A universal intelligence layer should not imply a universal surveillance database.

---

## 15. Falsifiable Cross-Domain Research Hypotheses

All hypotheses below are proposals. They require predeclared protocols, credible baselines, independent evaluation, and confidence intervals or appropriate uncertainty reporting.

### H-X01 — Compositional identity portability

**Claim:** A typed compositional identity model reduces false identity merges and splits relative to flat identifiers across at least two target domains.  
**Test:** Synthetic cloud and enterprise identity suites with overlapping membership and shared services.  
**Falsification:** No meaningful improvement, or unacceptable latency/interpretability cost, under predeclared criteria.

### H-X02 — Hypothesis-scoped BCEF

**Claim:** BCEF reduces invalid global rejection of competing explanations compared with unscoped contradiction rules.  
**Test:** Inject counterexamples that refute person-level but not team-level hypotheses.  
**Falsification:** Comparable or worse scoped error rate than baselines.

### H-X03 — Evidence dependence control

**Claim:** Provenance-aware REN/BCEF reduces overconfidence caused by correlated evidence.  
**Test:** Duplicate and derive synthetic observations with known dependencies.  
**Falsification:** No improvement in calibration or decision quality, or substantial degradation in useful detection.

### H-X04 — Independent enforcement under model failure

**Claim:** A separately enforced control plane limits specified action exposure even when advisory models are wrong or compromised.  
**Test:** Fault-inject incorrect recommendations against sandboxed tool and cloud actions.  
**Falsification:** A model-only pathway can exceed the declared hard limit, or the control cannot enforce its specification.

### H-X05 — Better cross-domain transfer than naïve reuse

**Claim:** Explicit semantic adapters outperform direct reuse of source-domain scoring rules under held-out target scenarios.  
**Test:** Compare adapter-based, naïvely ported, and domain-native approaches.  
**Falsification:** No reliable gain or materially higher complexity without benefit.

### H-X06 — Residual-driven question utility

**Claim:** AQSI questions derived from typed residuals identify useful discriminating tests more efficiently than generic anomaly follow-up.  
**Test:** Blind evaluators score information gain, actionability, safety, and cost.  
**Falsification:** No advantage or increased unsafe/irrelevant investigations.

### H-X07 — Validated relay generalization

**Claim:** Independent validation and governance reduce benchmark overfitting and regression relative to unreviewed iterative improvement.  
**Test:** Multi-round Red/Blue experiments with held-out attack families and delayed test sets.  
**Falsification:** No measurable generalization benefit, or unacceptably high cost for the gain.

### H-X08 — Bounded-loss / usability tradeoff

**Claim:** Structural advice plus independent limits improves a predeclared risk–utility frontier compared with conventional controls alone in selected domains.  
**Test:** Measure prevented unauthorized actions, false refusals, throughput, latency, and worst-case exposure.  
**Falsification:** Dominated tradeoff or inability to satisfy mandatory safety constraints.

### H-X09 — Cross-domain residual reuse

**Claim:** A typed residual taxonomy makes validated lessons reusable across domains without suppressing domain-specific distinctions.  
**Test:** Blindly transfer selected lessons from cloud to agent tool-use scenarios and compare with domain-only discovery.  
**Falsification:** Reused lessons are frequently misleading or require greater correction effort than they save.

### H-X10 — Governance invariants under recursive change

**Claim:** Contract-first change approval prevents candidate RSI improvements from silently weakening hard safety rules.  
**Test:** Inject candidate changes that optimize performance by relaxing limits.  
**Falsification:** Any unapproved candidate can modify or bypass a protected rule within the declared threat model.

---

## 16. Experimental Design and Evaluation Discipline

### 16.1 Required baselines

Compare against appropriate combinations of: conventional access-control and policy engines; rule-based anomaly detection; standard graph analytics; statistical anomaly detection; domain-specific provenance systems; static separation of duties; and independent safety controls without structural intelligence. A weak straw-man baseline cannot establish a contribution.

### 16.2 Ablation matrix

Evaluate the full system against variants removing: compositional identity; directional evidence; BCEF; evidence-dependence handling; AQSI; residual relay; and independent governance. **Do not ablate hard safety controls in a live environment.** In synthetic studies, a control-absent baseline can illustrate risk but cannot justify unsafe deployment.

### 16.3 Metrics

- **Inference:** precision/recall where labels are justified, calibration, false merge/split, scoped contradiction error, attribution uncertainty.
- **Security:** unauthorized actions prevented, policy-violation rate, bounded exposure under the threat model, time to containment, recovery effectiveness.
- **Utility:** false refusals, task completion, throughput, approval burden, cost, latency.
- **Evolution:** held-out improvement, regression frequency, residual closure rate, audit completeness, rollback success.
- **Transfer:** performance change across domains, adapter effort, semantic mapping errors, negative-transfer frequency.

Report distributions and worst-case outcomes where safety requires them. A single aggregate score can hide catastrophic tail behavior.

### 16.4 Data and leakage controls

Separate training, design, validation, and final evaluation scenarios. Prevent near-duplicate attack templates from leaking across partitions. Where possible, use unseen organizations, unseen service compositions, and time-separated scenarios. Independent evaluators should have authority to report negative results without the model developers changing thresholds after inspection.

### 16.5 Statistical and operational interpretation

Predeclare primary endpoints and acceptance criteria. Use uncertainty intervals appropriate to the sample design and report sample size, failure cases, and computational overhead. Avoid translating simulated performance directly into claims of real-world incident prevention. Where real-world testing is permitted, start with shadow-mode analysis and independently bounded pilots.

---

## 17. A Phased Research and Engineering Roadmap

**Phase 0 — Vocabulary and contracts.** Complete ASSI SSU schemas, identity types, evidence provenance, BCEF impact semantics, safety contracts, and transfer adapter requirements.

**Phase 1 — Synthetic reference environments.** Implement isolated custody, cloud, enterprise, AI-agent, and supply-chain scenarios with typed ground truth and reproducible traces.

**Phase 2 — Component conformance.** Verify identity-scoping, evidence dependence, hypothesis-scoped contradiction, non-authoritative scoring, and safety-plane independence.

**Phase 3 — Baselines and ablations.** Execute BM-001–BM-004 and LAB-X1–X4 with credible comparators, recorded costs, and negative findings.

**Phase 4 — Cross-domain transfer studies.** Test explicit adapters against naïve transfer and domain-native methods. Record failures as `TRANSFER` residuals.

**Phase 5 — Adversarial and governance validation.** Run bounded Red/Blue/Evaluation/Governance drives, independently review policy proposals, and test rollback and control invariants.

**Phase 6 — Carefully governed pilots.** Consider only after sufficient evidence, with domain-owner approval, restricted privileges, monitoring, recovery, and independent stop authority. High-consequence physical applications require additional specialist assurance.

A failed phase may justify narrowing the hypothesis rather than proceeding to deployment.

---

## 18. Relationship to the Wider Structural Intelligence Research Program

ASSI is a security-focused integration point, not a replacement for the broader Structural Intelligence (SI) ecosystem:

- **SIF:** supplies a conceptual architecture for structural intelligence, evaluators, and growth.
- **UCPSF:** informs perspective-aware scoring and control-plane organization; scoring does not confer enforcement authority.
- **SSI:** reminds the system to identify the principal whose choices and interests are being represented.
- **UTN / MDT:** support typed naming, temporal changes, and differential evidence histories.
- **BM-ODWEI / REN:** motivate directional weak-evidence reasoning with provenance and alternative explanations.
- **BCEF (ASSI-006):** formalizes bidirectional conditional tests and structured impacts.
- **AQSI:** generates research questions from unresolved security residuals.
- **UIERU / BUI-DSI:** motivate reusable, composable units and dynamic structural relay.
- **SSICR:** contributes competitive strategies and adversarial evaluation concepts.
- **SRSI:** informs iterative improvement, subject to independent validation and governance.
- **ISGFTR:** motivates investigation of spillover and transfer while warning against assuming capability boundaries from surface appearances.

These are conceptual interfaces. Their interoperability, safety, and empirical benefit must be demonstrated rather than inferred from shared terminology.

---

## 19. Open Problems and Limits

### 19.1 How much structure is enough?

Richer identity graphs and conditional tests increase expressive power but also increase storage, latency, governance overhead, and opportunities for modeling errors. Determine the minimum useful representation per threat model.

### 19.2 Can causal claims be justified?

Forward and counterfactual IF language can suggest causality without the necessary intervention or assumptions. Establish explicit criteria for observational versus interventional evidence, and avoid causal labels when they are unsupported.

### 19.3 Who governs the governor?

Independent controls still depend on people, institutions, hardware, and procedures. The architecture must model governance compromise, emergency exceptions, and organizational incentives without assuming that one additional layer eliminates trust.

### 19.4 How can lessons be shared safely?

Cross-organization relay may disclose sensitive infrastructure, incident details, or personal information. Investigate redacted residuals, privacy-preserving summaries, controlled vocabularies, and selective disclosure. Shared structural knowledge must not require sharing every underlying observation.

### 19.5 Can the system recognize non-transferability?

A promising capability is to detect when a source-domain analogy fails because the target has different hazards, irreversible consequences, legal constraints, or observability. A trustworthy system should be able to conclude **“transfer not justified.”**

### 19.6 What remains outside ASSI?

ASSI is not a substitute for cryptographic design, secure software development, formal verification, domain-specific safety engineering, legal compliance, incident response practice, or human institutional accountability. Its claims are constrained to specified threats and measured outcomes. No general architecture guarantees the absence of unknown vulnerabilities.

---

## 20. Synthesis: From Local Security to General Structural Defense

The research trajectory of ASSI can be summarized in six transitions:

1. **From valid actions to legitimate and bounded actions.** A credential or signature proves only what its verification procedure establishes.
2. **From flat identities to compositional, temporal actors.** Security must reason about people, teams, services, tools, and changing control relationships.
3. **From similarity to conditional evidence.** REN and BCEF preserve direction, alternatives, dependence, and hypothesis-scoped contradiction.
4. **From intelligent advice to independently enforced safety.** Adaptive scoring may improve decisions but cannot become its own unreviewable authority.
5. **From isolated incidents to adversarial structural relay.** Red/Blue/Evaluation/Governance drives produce reproducible evidence and explicit residuals.
6. **From repeated optimization to validated, governed evolution.** RSI proposals become accepted improvements only after independent tests, policy review, and bounded deployment.

The unifying proposition is that structural security is about **relationships among authority, identity, evidence, consequences, and governance**. Cryptocurrency makes those relationships visible; it does not own them. The opportunity is to investigate a portable structural defense kernel with domain-specific adapters, while accepting that transfer can fail and that safety obligations remain local, concrete, and independently enforceable.

> **Generalize the structure, not the guarantee. Transfer the questions, test the mechanisms, preserve the boundaries, and bound loss when intelligence fails.**

This is the intended contribution of ASSI-012 and the closing research thesis of the ASSI-001–012 foundation series.

---

## Appendix A. Cross-Document Reading Map

| Article | Primary contribution to the generalization |
|---|---|
| ASSI-001 | Cryptographic validity versus structural security |
| ASSI-002 | Four contradictions motivating defense beyond credentials |
| ASSI-003 | Trust relocation and boundary accounting |
| ASSI-004 | UTN and compositional identity |
| ASSI-005 | REN and directional weak evidence |
| ASSI-006 | BCEF and hypothesis-scoped conditional feedback |
| ASSI-007 | Independent authorization and bounded exposure |
| ASSI-008 | Adversarial drives and competitive relay |
| ASSI-009 | Security residuals and validated RSI |
| ASSI-010 | ASSI architecture and Structural Security Units |
| ASSI-011 | Benchmark laboratories and falsifiable hypotheses |
| **ASSI-012** | **Cross-domain transfer and general structural defense** |

## Appendix B. Proposed Follow-on Specifications and Cases

**Specifications:**

- `SPEC-001-Structural-Security-Unit-Contract.md`
- `SPEC-002-Compositional-Identity-and-UTN-Contract.md`
- `SPEC-003-Bidirectional-IF-and-Evidence-Impact-Contract.md`
- `SPEC-004-Authorization-and-Safety-Control-Contract.md`
- `SPEC-005-Adversarial-Drive-and-Relay-Contract.md`
- `SPEC-006-Validated-RSI-and-Governance-Contract.md`

**Cases:**

- `CASE-001-Cryptocurrency-Trust-and-Liquidity.md`
- `CASE-002-UTN-On-Chain-Identity-Sandbox.md`
- `CASE-003-Bidirectional-IF-and-False-Rejection.md`
- `CASE-004-Compromised-Signing-Service-Defense.md`
- `CASE-005-Adversarial-Drives-and-Security-RSI.md`

**Cross-domain extensions:** cloud administration, enterprise approvals, AI agent tool execution, supply-chain provenance, and eventually safety-critical environments under separately established assurance requirements.

---

**Repository placement:** `docs/ASSI-012-From-Cryptocurrency-Security-to-General-Structural-Defense.md`  
**Previous article:** `docs/ASSI-011-Benchmark-Laboratories-and-Falsifiable-Security-Hypotheses.md`  
**Series status:** Completes the twelve-paper ASSI v0.1.0 Research Foundation conceptual sequence; implementation and validation remain future work.
