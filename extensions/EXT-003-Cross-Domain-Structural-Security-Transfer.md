# EXT-003 — Cross-Domain Structural Security Transfer

**Project:** Adversarial Structural Security Intelligence (ASSI)  
**Version:** v0.1.0 — Research Foundation  
**Status:** Exploratory, specification-oriented research proposal; no demonstrated cross-domain security guarantee  
**Date:** 2026-11-02  
**License:** Apache-2.0  
**Repository path:** `extensions/EXT-003-Cross-Domain-Structural-Security-Transfer.md`  
**Foundations:** ASSI-001–012; SPEC-001–006; CASE-001–005; EXT-001–002  
**Related research:** UTN; REN; BCEF; MDT; UCPSF; AQSI; UIERU; SSICR; ISGFTR; Structural Relay; Validated RSI

## Abstract

A compromised cryptocurrency signing service, a misused cloud administrator credential, an over-privileged enterprise workflow, a misdirected AI-agent tool call, and a compromised software release pipeline share a structural pattern: a locally valid action may violate the intended authority, trust boundary, or acceptable consequence of the larger system. This resemblance invites reuse of security reasoning across domains. It does **not** justify directly reusing a source domain's identity labels, policies, evidence scores, attack models, or safety guarantees.

This extension proposes **Cross-Domain Structural Security Transfer (CDSST)**, a contract-first research framework for identifying transferable structural mechanisms, translating domain semantics, preserving non-transferable safety boundaries, and independently validating defensive claims in the target environment. A portable Structural Defense Kernel combines typed, temporal compositional identities (UTN), direction-sensitive evidence navigation (REN), hypothesis-scoped conditional testing (BCEF), provenance-aware Structural Security Units (SSUs), independent authorization controls, adversarial experimentation, Security Residuals, and governed learning. **Domain Adapters** define the target's assets, authority semantics, execution pathways, observability, consequences, recovery constraints, and legal or organizational governance. A **Transfer Contract** specifies which relations are preserved, which are approximated, which must be relearned, and which must not transfer at all.

The main hypothesis is conditional: transfer may improve the speed or quality of defensive discovery when structural correspondences are semantically valid, assumptions are visible, and the target retains independent control over consequential actions. Transfer can fail through false analogies, mismatched authority, unobservable states, correlated evidence, distribution shift, and unsafe reuse of thresholds. The paper specifies transfer units, mappings, gates, synthetic laboratories, counterexamples, metrics, falsifiable hypotheses, and a validation roadmap. No benchmark has been run and no empirical superiority is asserted.

**Keywords:** cross-domain security transfer; structural intelligence; domain adaptation; authorization semantics; UTN; REN; BCEF; security residual; provenance; compositional identity; AI-agent safety; cloud security; supply chain; falsifiable transfer.

---

## 1. Research Motivation: Similar Structure Is Not Equivalent Security

A blockchain signature verifies a cryptographic relationship between a message and a key. A cloud access token verifies a credential under a provider's identity and access model. A software artifact signature verifies an attestation under a signing policy. These mechanisms are analogous only at a chosen abstraction level. Their actual security meanings differ because the subjects, privileges, intended actions, rollback options, and possible losses differ.

ASSI's research opportunity is to carry **questions, evidence disciplines, and structural mechanisms** across domains without pretending that the surrounding security semantics are interchangeable.

A useful transfer asks:

1. Which source-domain contradiction is structurally present in the target?
2. Which typed entities, relations, and time dependencies preserve their meanings?
3. Which source observations are unavailable, weaker, or differently biased in the target?
4. Which assumptions about authorization, recovery, or bounded loss no longer hold?
5. Which controlled experiment could refute the proposed correspondence?
6. Who is independently authorized to accept, deploy, or reject the transferred mechanism?

The fundamental principle is:

> **Transfer structural hypotheses and test methods; do not transfer authority or security guarantees by analogy.**

### 1.1 Four transfer objects

- **Concept transfer:** a security distinction, such as valid credential versus legitimate intent.
- **Representation transfer:** a typed identity graph, provenance structure, or temporal dependency model.
- **Method transfer:** a BCEF test procedure, adversarial drive protocol, or residual triage algorithm.
- **Policy transfer:** actual authorization limits, risk budgets, or enforcement rules. This last category is **non-default, high-risk, and separately governed**.

These objects require different evidence thresholds. A concept can be useful as an analogy; a deployed policy requires target-specific validation and explicit authority.

## 2. Scope and Non-Goals

### 2.1 In scope

The proposed framework covers:

- Structural comparison of trust and authorization boundaries across domains.
- Typed translation of identity, evidence, asset, action, and consequence models.
- Cross-domain hypothesis generation and falsification.
- Synthetic, isolated adversarial evaluation and safe transfer of validated findings.
- Recording uncertainty, negative transfer, and unresolved Security Residuals.
- Governance of candidate improvements and target-domain deployment decisions.

### 2.2 Explicit non-goals

CDSST does not claim a universal policy engine, automatic security certification, transferable identity verification, guaranteed zero loss, or authorization to probe third-party systems. It does not infer that a successful synthetic result transfers to production. It does not permit AI-generated evidence scores to override independent controls.

### 2.3 Research maturity

All algorithms, contracts, test cases, and measurements below are **proposals**. Numerical thresholds appearing in examples are illustrative, not validated operating limits. Target-specific regulatory, privacy, and safety requirements remain authoritative.

## 3. The Structural Defense Kernel and Domain Adapters

The architecture separates a portable research kernel from target-specific semantics.

```text
        Source Domain                         Target Domain
  ┌────────────────────┐                ┌────────────────────┐
  │ Assets / Identities│                │ Assets / Identities│
  │ Trust / Actions    │                │ Trust / Actions    │
  │ Evidence / Recovery│                │ Evidence / Recovery│
  └─────────┬──────────┘                └──────────┬─────────┘
            │                                      │
       Source Adapter                         Target Adapter
            │                                      │
            └──────────┬───────────────────────────┘
                       ▼
             Typed Transfer Contract
                       │
             Semantic / Safety Gates
                       │
     ┌─────────────────┴─────────────────┐
     │ Portable Structural Defense Kernel│
     │ UTN · REN · BCEF · MDT · SSUs     │
     │ Residuals · AQSI · Relay         │
     └─────────────────┬─────────────────┘
                       ▼
             Target Synthetic Lab
                       ▼
          Independent Evaluation Gate
                       ▼
        Governance / Target Deployment
             (separate authorization)
```

### 3.1 Kernel components

| Component | Candidate transferable mechanism | Target-dependent meaning |
|---|---|---|
| UTN | Type-safe naming; temporal compositional identities | Who counts as a verified principal; which delegations are legitimate |
| REN | Directional relevance; weak-evidence provenance | Which features indicate risk in this domain |
| BCEF | Forward, reverse, counterfactual, contradiction tests | Observable consequences; valid counterfactual interventions |
| MDT | Time-indexed deltas and structural change | Event ordering, retention, and acceptable temporal granularity |
| SSU | Typed envelopes, audit links, epistemic status | Domain schemas and data sensitivity |
| Safety control | Separate adaptive reasoning from enforcement | Policy authority, budget units, hard constraints, execution coverage |
| Drives | Red/Blue/Evaluation/Governance separation | Legal test scope, hazard constraints, recovery procedures |
| RSI/Relay | Preserve validated lessons and residuals | Promotion authority, acceptable change risk, rollback feasibility |

### 3.2 Adapter responsibilities

Every adapter MUST identify its own authoritative sources for identity, entitlement, action intent, execution confirmation, loss accounting, and recovery. If a source does not exist, the adapter must declare an **observability gap**, not invent an equivalent. A mapping that changes an enforcement meaning requires independent approval.

## 4. A Formal Model of Transfer

Let a source domain be

$$
D_s=(V_s,E_s,T_s,A_s,O_s,C_s,G_s),
$$

and a target domain be

$$
D_t=(V_t,E_t,T_t,A_t,O_t,C_t,G_t),
$$

where the components represent typed entities, relations, temporal semantics, authorization, observability, consequences, and governance. Let $K$ be a candidate kernel mechanism and $\phi$ a **partial, typed mapping** from source structures to target structures.

A proposed transfer is:

$$
\tau=(D_s,D_t,K,\phi,\mathcal A,\mathcal N,\mathcal V),
$$

where $\mathcal A$ is a set of explicit assumptions, $\mathcal N$ is a set of non-transfer conditions, and $\mathcal V$ is a target validation plan.

The mapping is **partial by design**. For some source element $x$, $\phi(x)$ may be undefined. Such gaps are first-class results, not errors to be silently patched with guesses.

### 4.1 Three preservation tests

1. **Type preservation:** source and target roles are mapped without conflating observed addresses, inferred operators, verified principals, or authorized actors.
2. **Relational preservation:** mapped edges preserve the security-relevant relation, such as *can approve* versus merely *can observe*.
3. **Consequence preservation:** mapped actions retain a meaningful risk interpretation, including reversibility, blast radius, and recovery.

A fourth, separate requirement is **governance preservation**: the transfer process cannot manufacture new authority in the target.

### 4.2 Transfer validity is multidimensional

Define a qualitative transfer assessment vector:

$$
Q(\tau)=(q_{type},q_{relation},q_{time},q_{evidence},q_{authority},q_{consequence},q_{recovery}).
$$

This vector is not inherently a probability or a universal scalar. A weighted score may assist research prioritization but **must not substitute for hard safety gates**. An excellent representation match cannot compensate for a missing enforcement boundary.

## 5. Canonical Transfer Unit (CTU)

A Cross-Domain Transfer Unit is an SSU-compatible record that binds a source insight to a target hypothesis and its validation obligations.

Required conceptual fields:

- Stable `transfer_id`, schema version, creator, and provenance.
- Source and target domain IDs with adapter versions.
- Transfer class: concept, representation, method, or policy candidate.
- Typed mapping rules and unmapped elements.
- Preserved invariants, weakened assumptions, and non-transfer constraints.
- Evidence dependencies and epistemic status.
- Target hypotheses, alternatives, and discriminating tests.
- Safety classification, authorized experiment scope, and budgets.
- Evaluation record, governance decision, and rollback references.
- Lifecycle status and immutable audit history.

### 5.1 Example CTU (illustrative, non-normative)

```yaml
schema: assi.cross_domain_transfer.v0.1
transfer_id: ctu-demo-001
kind: method_candidate
source:
  domain: synthetic_crypto_custody
  artifact: independent_authorization_pattern
  adapter_version: 0.1
  evidence_refs: [source-lab-report-001]
target:
  domain: synthetic_ai_agent_tools
  adapter_version: 0.1
mapping:
  - source_type: signing_request
    target_type: tool_invocation_request
    preserves: [declared_intent, operation_parameters]
  - source_type: settlement_execution
    target_type: tool_effect
    preserves: [consequence_accounting]
  - source_type: transaction_signature
    target_type: authenticated_tool_call
    preserves: [authentication_only]
    does_not_preserve: [legitimate_intent, asset_finality]
unmapped_source_concepts: [on_chain_finality]
assumptions:
  - target_executor_is_covered_by_independent_enforcement
  - effects_can_be_attributed_to_a_specific_request
non_transfer_conditions:
  - bypassable_target_executor
  - missing_target_approval_authority
hypotheses:
  - id: h1
    statement: independent_intent_binding_reduces_unauthorized_effects
    alternative: improvement_is_due_only_to_static_policy_rules
validation:
  laboratory: LAB-T3
  dataset_partition: target_holdout
  evaluator_role: independent_evaluation
  measures: [unauthorized_effect_rate, false_block_rate, latency]
safety:
  environment: synthetic_isolated
  live_action_authorized: false
  deployment_requires_separate_approval: true
status: proposed
```

The mapping explicitly marks where a signature and an authenticated tool call are analogous, and where they are not. This prevents a syntactic correspondence from becoming a false authorization equivalence.

## 6. Domain Semantics: What Cannot Be Silently Folded

### 6.1 Identity

A wallet address, cloud service account, enterprise employee, AI-agent instance, and software build identity are different principal types. UTN may describe all of them, but a type-safe graph does not establish equivalence of their real-world controllers.

### 6.2 Authority

Permission to sign a transaction, invoke an API, approve a purchase, publish a release, or change a cloud policy derives from different sources. A mapping must preserve **who grants authority**, **what is authorized**, **for how long**, and **how it is revoked**.

### 6.3 Evidence

Blockchain events may be externally observable and difficult to alter after finalization. Enterprise logs can be incomplete or centrally administered. AI-agent traces may omit hidden tool effects. Build provenance may attest process steps without guaranteeing artifact behavior. The target evidence model must be independently assessed.

### 6.4 Consequences

Financial settlement, infrastructure outage, data disclosure, procurement fraud, and compromised software distribution have different units and tail risks. No generic loss score can erase these differences.

### 6.5 Recovery

Some actions can be rolled back, some compensated, and some remain irreversible. Transfer must carry explicit recovery assumptions and reject any claim that rollback is universal.

## 7. Trust Relocation and Structural Contradictions

A security control often moves trust rather than eliminates it. Replacing an exchange signing service with a cloud KMS, or replacing manual approval with an AI agent, can shift reliance to an identity provider, policy engine, administrator, logging service, or model provider.

For each target, a transfer analysis should enumerate:

1. Original trusted component and failure mode.
2. New trusted component after adaptation.
3. Shared administrative or infrastructure dependencies.
4. Independent observation and enforcement pathways.
5. New common-mode failures introduced by the transfer.
6. Residual loss if both source-inspired controls and target controls fail.

A useful transfer may improve one boundary while worsening another. That is a measurable outcome, not a contradiction to hide.

## 8. UTN Transfer: Compositional Identity Across Domains

UTN provides typed naming and temporal identity hypotheses, not automatic identity verification. Across domains, the transferable structure is the distinction between **observed object**, **inferred controller**, **verified principal**, **delegated role**, and **authorized actor**.

### 8.1 Example mapping

| Crypto custody | Cloud infrastructure | AI agent tools |
|---|---|---|
| Wallet address | Resource or workload identity | Tool endpoint or agent instance |
| Signing service | Workload credential service | Tool invocation broker |
| Custody operations team | IAM/admin team | Agent operator and tool owner |
| Shared signing infrastructure | Shared CI/CD or identity provider | Shared model/tool gateway |
| Transaction authorization | Change authorization | Tool-effect authorization |

These are **candidate structural analogies**, not identity equalities. An organization may use multiple cloud roles, a single role may be shared by services, and an agent may act through a human-delegated tool account. Temporal hypergraphs can represent these overlapping control relationships.

### 8.2 Identity transfer tests

- Does the mapping incorrectly merge a shared provider with its customers?
- Does it split a single team because credentials rotated?
- Does it confuse a service account with a human owner?
- Does it preserve the time interval of delegated authority?
- Does a contradiction about one actor inappropriately refute a team-level hypothesis?

Measure false merge, false split, temporal identity error, and unauthorized authority promotion separately.

## 9. REN Transfer: Directional Weak Evidence and Calibration

REN's reusable idea is that evidence relevance depends on a **hypothesis, direction, context, and alternative explanations**. Features that signal suspicious cryptocurrency withdrawals may not signal suspicious cloud administration or AI-agent actions.

A target-specific relevance model should record:

$$
R_t(e,h,d,c),
$$

with provenance, observability, and dependencies. Source-domain weights, thresholds, and empirical calibration must be treated as **unvalidated priors** in the target.

### 9.1 Avoid evidence laundering

A transferred feature derived from a source alert cannot be treated as independent confirmation of that alert. Similarly, three AI agents repeating the same underlying log interpretation do not provide three independent observations. The transfer contract should carry a dependency graph and identify shared data, model, and infrastructure lineage.

### 9.2 Directional mismatch

High transaction velocity can indicate liquidity management or abuse. High cloud API activity can indicate an incident response or a compromise. Rapid AI-agent tool use can indicate a legitimate batch job or runaway automation. A direction-sensitive scoring model must evaluate these competing hypotheses instead of transferring a universal anomaly label.

## 10. BCEF Transfer: Conditional Reasoning Without False Rejection

BCEF transfers four *methods of inquiry*, not universal implications:

- **Forward IF:** If hypothesis $H$ holds, what observable evidence $E$ should follow under specified conditions?
- **Reverse IF:** Given $E$, which competing hypotheses explain it, and what discriminates among them?
- **Counterfactual IF:** Under a permitted intervention or simulation, how would outcomes differ if a key condition changed?
- **Contradiction IF:** Which exact proposition, role, and time interval does the evidence refute?

The logical warning remains fundamental: $H\Rightarrow E$ does not imply $E\Rightarrow H$. Transferring an implication from one domain to another requires verifying its premises in the target.

### 10.1 Hypothesis-scoped example

A set of transactions does not fit a single-operator timing model. That observation may challenge a *single operator* hypothesis but does not automatically refute a *team controller* or *shared service* hypothesis. Likewise, inconsistent tool-call timing may refute a single-agent execution hypothesis without disproving a coordinated multi-agent workflow.

### 10.2 Impact transfer

A BCEF result may propose a score revision, identity split, new edge type, evidence request, or policy review. Such proposals remain **evidence-level or research-level effects**. They cannot authorize real transactions, alter cloud IAM, or deploy agent tools.

## 11. Independent Authorization and Non-Transferable Safety Boundaries

The portable principle is **separation of adaptive reasoning from independently governed action authorization**. The concrete implementation is target-specific.

| Target domain | Consequential action | Independent boundary example | Critical caveat |
|---|---|---|---|
| Cryptocurrency custody | Transfer assets | Separate approval, exact transaction binding, exposure budget | Every execution path must be covered |
| Cloud | Change privileged policy | Independent change gate and privileged action enforcement | Shared admin compromise may bypass both |
| Enterprise | Approve payment or contract | Segregated approval with budget and beneficiary binding | Collusion and emergency exceptions matter |
| AI agent | Invoke consequential tool | External tool broker with scoped permissions | Broker must mediate all actual effects |
| Software supply chain | Publish release artifact | Independent release policy and provenance checks | Signed malicious builds remain possible |

**No source-domain budget or policy threshold may be copied into production without target authorization and validation.** An apparently analogous control may have different failure consequences and latency costs.

### 11.1 Loss bounding

Let $L_t$ denote target-domain loss under a specified threat model and test horizon. A research objective is to reduce a defined upper-tail measure or bounded exposure subject to acceptable operational availability. A finite, credible loss bound requires assumptions about enforcement coverage, independence, atomic budgets, common-mode compromise, and recovery. If any assumption fails, the bound must be withdrawn or revised.

## 12. Four Primary Cross-Domain Laboratories

All laboratories use synthetic or explicitly authorized isolated systems. Each must publish scenario definitions, hidden ground truth, split methodology, evaluator independence, and limitations.

### LAB-T1 — Crypto Custody to Cloud IAM

**Source insight:** a valid signing capability is not equivalent to legitimate transaction intent.  
**Target:** an authenticated privileged cloud API call may violate an approved change request.

**Synthetic setup:** workloads, human administrators, delegated roles, service accounts, change tickets, privileged operations, and audit streams. Some credentials are valid but used outside the approved change scope.

**Transfer candidate:** typed actor/role graph, request-to-effect binding, independent privileged-action gate, BCEF hypothesis portfolio.

**Alternatives:** static least-privilege policy alone may provide comparable protection; adding structural reasoning may increase false blocks.

**Measures:** unauthorized privileged changes, false blocks, time to detect, shared-admin bypass coverage, recovery time, evaluation cost.

**Failure test:** source-inspired policy appears successful until the same administrator can modify both the identity provider and the gate.

### LAB-T2 — Crypto Custody to Enterprise Approval

**Source insight:** control of a credential or approval channel does not alone establish valid business intent.  
**Target:** payments, procurement, delegated spending, and multi-stage approvals.

**Synthetic setup:** employees, teams, approvers, vendors, contracts, delegated limits, and conflicting authority records. Teams reconfigure over time and approvals may be valid yet inconsistent with purchase intent.

**Transfer candidate:** UTN compositional authority, hypothesis-scoped contradiction, budget accounting, independent approval provenance.

**Alternatives:** simple segregation-of-duties may outperform an elaborate structural system at lower cost.

**Measures:** unauthorized payment rate, false rejection, workflow latency, identity merge/split errors, audit completeness.

**Failure test:** an inferred team membership is mistaken for verified spending authority.

### LAB-T3 — Crypto Custody to AI-Agent Tool Governance

**Source insight:** a valid action token or signature cannot alone establish acceptable consequence.  
**Target:** autonomous agent tool calls, delegated scopes, tool-chain effects, and multi-agent workflows.

**Synthetic setup:** agents, human principals, tool gateways, read-only and mutating APIs, action budgets, approvals, and hidden tool side effects.

**Transfer candidate:** independent tool broker, exact request/effect binding, REN evidence about anomalous intent, BCEF hypothesis tests, AQSI-generated questions about overlooked tool dependencies.

**Alternatives:** static scoped permissions and deterministic policy checks may be sufficient; learned anomaly scores may add noise.

**Measures:** unauthorized tool effects, missed indirect effects, false blocks, decision latency, tool-path coverage, rollback success.

**Failure test:** a supposedly read-only tool triggers a consequential side effect outside the broker's observation.

### LAB-T4 — Crypto Custody to Software Supply Chain

**Source insight:** cryptographic validity is narrower than structural legitimacy.  
**Target:** signed builds, provenance attestations, dependency approvals, release promotion, and distribution.

**Synthetic setup:** source repositories, build services, dependency graphs, signing keys, release approvers, CI identities, and artifact registries.

**Transfer candidate:** provenance-aware SSUs, typed build identity, independent release approval, contradictory evidence tests, adversarial release-drive scenarios.

**Alternatives:** reproducible builds, conventional provenance policies, and deterministic allowlists may already dominate performance.

**Measures:** unauthorized release promotion, compromised dependency detection, false release holds, provenance gaps, recovery cost.

**Failure test:** a malicious but correctly signed artifact passes because the mapping equates signature validity with release legitimacy.

## 13. Additional Transfer Frontiers and Explicit Exclusions

Potential future domains include healthcare workflow authorization, industrial control, robotics, and critical infrastructure. These have distinct safety, regulatory, physical, and human-factors constraints. The current extension **does not** assert that the proposed laboratories validate deployment in those settings. Any physical-safety domain would require a new hazard model, independent expert review, domain-specific certification where applicable, and strict prohibitions on uncontrolled live experimentation.

A transferable question may still be useful even when a transferable action policy is not. This distinction permits research exploration without overstating deployment readiness.

## 14. Negative Transfer: A First-Class Research Result

**Negative transfer** occurs when an adapted mechanism performs worse than an appropriate target-only baseline, introduces unacceptable new hazards, or yields misleading confidence.

### 14.1 Failure taxonomy

| ID | Failure mode | Example | Required response |
|---|---|---|---|
| NT-01 | Semantic mismatch | Wallet owner mapped to cloud resource owner | Reject mapping; refine types |
| NT-02 | Authority mismatch | Observed actor treated as authorized actor | Block promotion; audit identity path |
| NT-03 | Observability mismatch | Target lacks source-quality event evidence | Mark unknown; redesign tests |
| NT-04 | Temporal mismatch | Delegation expired before action | Use interval-aware identity and policy |
| NT-05 | Evidence dependence | Multiple signals share one compromised log | Collapse dependencies; recalibrate |
| NT-06 | Distribution shift | Source risk weights miscalibrate in target | Target calibration and holdout tests |
| NT-07 | Consequence mismatch | Reversible API call assumed equivalent to final settlement | Rebuild loss and recovery model |
| NT-08 | Enforcement gap | Some target actions bypass independent gate | Fail deployment gate |
| NT-09 | Common-mode failure | Same admin controls policy and evaluator | Add independent boundary or reject |
| NT-10 | Reward / metric gaming | Defender optimizes benchmark rather than safety | Hidden scenarios and external evaluation |
| NT-11 | Privacy / legal mismatch | Source evidence sharing violates target restrictions | Minimize or prohibit data transfer |
| NT-12 | Governance mismatch | Source release approval reused without target authority | Require target governance decision |

### 14.2 Non-transfer register

Each transfer project should publish a `NonTransferRegister` containing rejected correspondences, unresolved assumptions, observed failures, and the evidence needed to revisit them. Negative results should remain discoverable through Structural Relay so that later agents do not repeat the same unsafe analogy.

## 15. Cross-Domain Security Residuals

A target experiment may expose residuals absent in the source. These should be classified rather than absorbed into an aggregate success score:

- **Identity residual:** controller, team, service, or delegated role remains ambiguous.
- **Evidence residual:** missing, correlated, manipulated, or temporally invalid observations.
- **Inference residual:** an IF implication or contradiction is misapplied.
- **Authority residual:** the target's actual approval semantics are unmodeled.
- **Enforcement residual:** an action path bypasses the intended safety control.
- **Exposure residual:** risk is underestimated due to indirect or cascading effects.
- **Recovery residual:** rollback or containment assumptions fail.
- **Transfer residual:** source-to-target analogy lacks validated semantic preservation.
- **Governance residual:** independent evaluators or authorized approvers are missing.
- **Ecological residual:** agents share hidden dependencies or mutually amplify errors.

Residuals should carry provenance, severity rationale, affected assumptions, affected domains, test reproducibility, and proposed next questions.

## 16. AQSI-Guided Transfer Prospecting

EXT-002 proposes autonomous security questioning. In cross-domain transfer, AQSI can generate **candidate transfer questions**, not permissions to experiment on real systems.

Example question templates:

- Which target-domain action is locally valid but may violate higher-level intent?
- Which target principal is actually a dynamic composition of people, services, and roles?
- Which source-domain evidence feature becomes unreliable after translation?
- What observation would distinguish a compromised credential from an authorized emergency response?
- Can an independent target gate constrain loss if the adaptive model is wrong?
- Which residual recurs across domains, and which only appears superficially similar?

### 16.1 Question scoring

Question selection may combine expected information gain, severity relevance, testability, novelty, domain diversity, and cost. It must separately enforce hard restrictions on privacy, authorization, data handling, and experiment scope. The highest-scoring question is not necessarily permissible to investigate.

### 16.2 Cross-domain question relay

A source-domain residual can produce a target-domain question; a target experiment can return a refined structural principle or a documented non-transfer condition. Each relay records the mapping and its validation status. Repeated transmission of the same unverified hypothesis does not upgrade its epistemic status.

## 17. Multi-Agent Transfer Ecology

EXT-001's multi-agent security ecology introduces potential benefits and hazards. Independent domain experts, evidence analysts, adversarial testers, and governance reviewers may catch mapping errors that a single agent misses. But shared models, prompts, or training data can create correlated agreement.

A recommended research-role partition is:

- **Source Analyst:** describes the source mechanism and its evidence.
- **Target Domain Analyst:** specifies target semantics and failure consequences.
- **Mapping Agent:** proposes partial typed correspondences and non-transfer conditions.
- **Red Evaluator:** constructs counterexamples in an authorized sandbox.
- **Independent Evaluator:** checks holdout results and evidence dependencies.
- **Governance Authority:** determines whether a candidate may advance to a consequential stage.

These are logical roles, not proof of organizational independence. Independence must be assessed at the level of authority, data, infrastructure, and incentives.

## 18. Transfer Lifecycle and Gates

A proposed transfer proceeds through a bounded lifecycle:

```text
DISCOVER_SOURCE_PATTERN
    ↓
FORMULATE_TARGET_HYPOTHESIS
    ↓
BUILD_TYPED_PARTIAL_MAPPING
    ↓
REGISTER_ASSUMPTIONS_AND_NON_TRANSFER
    ↓
CHECK_TARGET_SAFETY_AND_AUTHORIZATION
    ↓
RUN_SYNTHETIC_OR_AUTHORIZED_TEST
    ↓
INDEPENDENTLY_EVALUATE_AND_ABLATE
    ↓
RECORD_SUCCESS / NEGATIVE_TRANSFER / UNKNOWN
    ↓
GOVERNANCE_REVIEW
    ↓
ARCHIVE_AND_RELAY
    ↓
[Optional separate target-specific deployment process]
```

### Gate G0 — Source evidence

The source insight must have a traceable provenance and explicit maturity label. A conceptual hypothesis may generate a target hypothesis but cannot be described as an empirically proven mechanism.

### Gate G1 — Semantic mapping

Required types, relations, time semantics, and authority sources must be explicit. Unknown or unmapped elements cannot silently default to an identity or permission.

### Gate G2 — Safety feasibility

The target test must have authorization, isolation, bounded resource use, data-handling controls, and stop conditions. If these cannot be established, the experiment does not proceed.

### Gate G3 — Independent evaluation

Target holdouts, alternative hypotheses, baselines, negative cases, and dependency-aware evidence must be evaluated. The result may be `SUPPORTED`, `REFUTED`, `CONFLICT`, or `UNKNOWN` for the specific tested claim.

### Gate G4 — Governance

Promotion requires a target-domain authority, an explicit change scope, rollback or containment planning, and monitoring. An evaluation pass does not itself grant deployment permission.

## 19. Contract-First Interfaces

A reference implementation could expose the following logical interfaces:

```text
propose_transfer(source_artifact, target_domain, transfer_class)
    -> CrossDomainTransferUnit

validate_mapping(transfer_unit, source_adapter, target_adapter)
    -> SemanticValidationRecord

register_non_transfer(transfer_id, constraint, evidence_refs)
    -> NonTransferRecord

plan_target_experiment(transfer_unit, hypothesis_portfolio, safety_scope)
    -> AuthorizedExperimentProposal

assess_target_results(experiment_id, evidence_graph, baselines)
    -> IndependentEvaluationRecord

emit_security_residual(evaluation_id, failed_assumption, impact)
    -> SecurityResidualUnit

request_governance_review(transfer_id, evaluation_id, change_scope)
    -> GovernanceDecisionRequest

relay_transfer_outcome(transfer_id, evaluation_id, residual_refs)
    -> StructuralRelayRecord
```

These interfaces are conceptual and should be reconciled with SPEC-001 through SPEC-006 before implementation. Their return types must retain stable IDs, versions, epistemic states, and provenance.

### 19.1 Reference decision logic

```python
# Research pseudocode; not production authorization logic.
def evaluate_transfer_candidate(ctu, source_adapter, target_adapter):
    assert ctu.provenance_is_traceable()
    mapping = check_typed_partial_mapping(ctu, source_adapter, target_adapter)
    if mapping.has_authority_confusion or mapping.has_unresolved_hard_safety_gap:
        return reject_or_hold(ctu, mapping.failures)

    if not target_adapter.experiment_is_authorized_and_isolated(ctu):
        return hold(ctu, reason="target experiment lacks independent authorization")

    plan = pre_register_hypotheses_baselines_and_metrics(ctu)
    result = run_synthetic_or_authorized_experiment(plan)
    assessment = independent_evaluation(result, plan)

    record_assumptions_and_negative_transfer(ctu, assessment)
    emit_residuals_for_failures(ctu, assessment)
    archive_relay(ctu, assessment)

    # No deployment action is performed here.
    return assessment
```

## 20. Conformance Invariants (Proposed)

The following requirements are intended as testable design constraints, not evidence of implementation:

**CT-01 — Type fidelity.** Every mapped identity, asset, action, and authority relation retains a declared type.  
**CT-02 — Partial mappings.** Unmapped elements remain explicit and cannot be filled with unsupported equivalences.  
**CT-03 — Provenance.** Source and target evidence preserve origin, derivation, and dependencies.  
**CT-04 — Epistemic status.** Hypotheses are not silently upgraded to validated facts.  
**CT-05 — Time validity.** Delegation, membership, and policy intervals are preserved or explicitly redefined.  
**CT-06 — Authority isolation.** Identity or evidence inference cannot create authorization.  
**CT-07 — Target governance.** Source approvals do not authorize target actions.  
**CT-08 — Safety gates.** Consequential experiments require independently authorized, bounded scope.  
**CT-09 — Enforcement coverage.** Unmediated action paths block any bounded-loss claim.  
**CT-10 — Evidence dependence.** Reused or correlated evidence is not counted as independent confirmation.  
**CT-11 — Scoped contradiction.** Refutation is limited to the actual tested hypothesis and context.  
**CT-12 — Alternative explanations.** Material target-domain alternatives are retained until tested.  
**CT-13 — Baseline comparison.** Performance claims require relevant target-only baselines.  
**CT-14 — Negative transfer.** Target regressions and failed mappings are reported, not discarded.  
**CT-15 — Holdout integrity.** Target evaluation data are separated from tuning and scenario construction.  
**CT-16 — No score-to-policy promotion.** A transfer score alone cannot change an enforcement rule.  
**CT-17 — Independent evaluation.** Evaluators cannot silently approve their own candidate for deployment.  
**CT-18 — Resource bounds.** Exploration and recursion respect compute, time, and risk limits.  
**CT-19 — Reversibility honesty.** Rollback claims identify irreversible effects and limits.  
**CT-20 — Privacy and legal constraints.** Source data are not transferred beyond target authorization and applicable obligations.  
**CT-21 — Auditability.** Mapping revisions, gate outcomes, and governance decisions remain versioned and traceable.  
**CT-22 — Failure transparency.** Unknown, conflicted, and failed outcomes remain visible in relay records.  
**CT-23 — Common-mode analysis.** Shared identity, infrastructure, evaluator, and policy dependencies are tested.  
**CT-24 — No automatic certification.** Passing synthetic benchmarks does not establish real-world safety certification.

## 21. Conformance Test Vectors (Proposed)

| Test | Input condition | Expected outcome |
|---|---|---|
| TV-01 | Fully typed conceptual mapping | Accept for research review |
| TV-02 | Source principal mapped to incompatible target type | Reject mapping |
| TV-03 | Missing target authority source | Hold; request target authority definition |
| TV-04 | Source approval copied into target | Reject authorization promotion |
| TV-05 | Source evidence reused three times | Preserve shared dependency |
| TV-06 | Target log missing required observation | Mark unknown; do not infer absence |
| TV-07 | Expired target delegation | Reject authority inference |
| TV-08 | Single-agent hypothesis refuted; team alternative viable | Preserve team hypothesis |
| TV-09 | Strong source performance, target regression | Record negative transfer |
| TV-10 | Transfer score high, safety gate fails | Block consequential progression |
| TV-11 | Source policy threshold copied unchanged | Hold pending target validation |
| TV-12 | Target action bypasses independent enforcement | Fail bounded-loss claim |
| TV-13 | Source finality assumed for reversible target action | Flag consequence mismatch |
| TV-14 | Target irreversible action treated as reversible | Reject recovery mapping |
| TV-15 | Evaluator shares candidate tuning data | Flag evaluation leakage |
| TV-16 | Red and Blue share hidden model dependency | Record common-mode risk |
| TV-17 | Unapproved live target probe proposed | Reject experiment |
| TV-18 | Valid signed malicious release | Require intent/provenance checks |
| TV-19 | Authenticated agent invokes unauthorized side effect | Independent broker must deny or report enforcement gap |
| TV-20 | Correctly scoped target experiment | Allow isolated test, not deployment |
| TV-21 | Missing privacy basis for evidence transfer | Prohibit transfer of restricted data |
| TV-22 | Failed mapping later revised | Preserve immutable prior failure record |
| TV-23 | Transfer evaluation supports limited claim only | Restrict claim to tested scope |
| TV-24 | Passing evaluation without governance approval | Do not deploy |

Test outcomes should be evaluated against a documented schema and reproducible synthetic fixtures. The table is not a claim that such a harness already exists.

## 22. Benchmark Design and Baselines

### 22.1 Baseline families

- **B0 — Target-only conventional controls:** standard deterministic policies and logs.
- **B1 — Naive analogy:** reuse source patterns without typed semantic checks; expected to expose negative-transfer risks.
- **B2 — Typed representation only:** UTN and SSUs without directional evidence or BCEF.
- **B3 — Typed representation + REN:** adds target-calibrated directional evidence.
- **B4 — Typed representation + BCEF:** adds scoped conditional tests and structured revisions.
- **B5 — Independent control only:** target-specific policy gate without adaptive structural inference.
- **B6 — Full transfer candidate:** typed mapping, REN, BCEF, independent control, and governance.
- **B7 — Full candidate + AQSI/Relay:** adds governed question generation and residual-driven learning.

### 22.2 Metrics

Report both security outcomes and transfer quality:

| Dimension | Candidate metrics | Interpretation caution |
|---|---|---|
| Security | Unauthorized-effect rate, loss exposure, missed harmful actions | Depends on threat model and coverage |
| Availability | False block rate, approval latency, recovery time | Security gains may impose operational cost |
| Identity | False merge, false split, temporal identity error | Requires hidden ground truth |
| Evidence | Calibration, dependence error, contradiction-scope leakage | Scores are not automatically probabilities |
| Transfer | Negative-transfer rate, semantic mapping defects, target generalization gap | Compare against target-only baseline |
| Efficiency | Validated residuals found per cost, time to useful finding | Discovery count alone can be gamed |
| Governance | Unauthorized promotions, audit completeness, rollback readiness | Must test independent authority |
| Robustness | Holdout performance, common-mode failure coverage, scenario shift | Synthetic success is not production proof |

### 22.3 Experimental safeguards

Use pre-registered primary outcomes; fixed train/validation/test partitions; hidden target holdouts; scenario-family separation; repeated seeds; confidence intervals or uncertainty estimates appropriate to the design; and independent evaluators. Report failures, costs, and uncertainty rather than only aggregate improvements.

## 23. Twelve Falsifiable Research Hypotheses

Each hypothesis below is a proposal, not a finding.

**H-T01 — Type-safe mapping.** Explicit typed partial mappings reduce authority-confusion defects relative to naive analogy. *Falsification:* no reduction, or higher target error at comparable cost.

**H-T02 — Temporal composition.** UTN temporal compositional identities reduce false merges/splits under dynamic delegation relative to static identity graphs. *Falsification:* target-only graph methods perform as well or better.

**H-T03 — Directional calibration.** Target-calibrated REN improves discriminating evidence quality over source-weight reuse. *Falsification:* calibration or decision quality does not improve on holdout cases.

**H-T04 — Scoped BCEF.** Hypothesis-scoped contradiction lowers false rejection without unacceptable loss of correct rejection. *Falsification:* correct rejection collapses or false rejection remains unchanged.

**H-T05 — Dependency control.** Provenance-aware evidence handling reduces overconfidence from correlated observations. *Falsification:* no improvement in calibration or dependency-related errors.

**H-T06 — Independent enforcement.** Target-specific independent authorization limits unauthorized effects after a valid credential is compromised. *Falsification:* bypass or common-mode failure negates the claimed protection.

**H-T07 — Negative-transfer registry.** Preserving failed mappings reduces recurrence of the same transfer defects in later rounds. *Falsification:* defect recurrence is not reduced at comparable workload.

**H-T08 — Cross-domain AQSI.** Autonomous transfer-question portfolios discover more independently validated residuals per unit cost than fixed question lists. *Falsification:* equal or worse validated yield, or unacceptable false discoveries.

**H-T09 — Multi-agent diversity.** Independent source/target/red/evaluation roles reduce mapping errors compared with a single-agent workflow. *Falsification:* gains disappear after controlling for shared dependencies and extra compute.

**H-T10 — Generalization.** A validated structural mechanism transfers across at least two target scenario families better than a target-only baseline. *Falsification:* improvement is restricted to tuned or near-duplicate scenarios.

**H-T11 — Governed RSI.** Residual-driven candidate refinement improves out-of-sample security outcomes without increasing unauthorized policy changes. *Falsification:* performance regresses or governance violations occur.

**H-T12 — Transfer boundary transparency.** Explicit non-transfer conditions reduce unsupported safety claims and deployment mistakes. *Falsification:* no measurable reduction in claim overreach or consequential errors.

A claim may be supported in one domain and refuted in another. The result must retain its domain, threat model, and evaluation conditions.

## 24. Ablation and Counterexample Program

### 24.1 Ablations

Remove one element at a time while holding the target test set and safety controls constant:

1. UTN type distinctions.
2. Temporal composition.
3. REN directional context.
4. BCEF contradiction scoping.
5. Evidence dependency tracking.
6. Target-specific independent authorization.
7. Non-transfer register.
8. AQSI question portfolio.
9. Independent evaluator role.
10. Governance promotion gate.

For any ablation that removes a safety control, restrict testing to an isolated synthetic environment. Do not deliberately remove production controls.

### 24.2 Counterexample families

**CE-1 — Correct credential, wrong intent.** Valid identity, invalid requested consequence.  
**CE-2 — Shared service ambiguity.** Several principals use one infrastructure provider.  
**CE-3 — Missing target evidence.** Source method relies on unavailable target logs.  
**CE-4 — Reversible/irreversible mismatch.** Recovery assumptions fail across domains.  
**CE-5 — Common-mode control failure.** One actor controls both the action channel and the gate.  
**CE-6 — Adversarial evidence contamination.** A compromised observer fabricates multiple correlated features.  
**CE-7 — Policy semantic inversion.** A source denial condition becomes a target exception.  
**CE-8 — Benchmark overfitting.** Transferred mechanism succeeds on public scenarios and fails hidden variants.

A transfer framework should be judged by its ability to **recognize when not to transfer**, not only by the number of successful mappings it proposes.

## 25. Validated RSI and Governance of Transfer

Validated RSI is a bounded, evidence-driven improvement process, not a self-certifying optimization loop.

A cross-domain improvement cycle is:

```text
Target Security Residual
   → AQSI Question Unit
   → Competing Transfer Hypotheses
   → Typed Mapping Revision
   → Authorized Synthetic Experiment
   → Independent Evaluation
   → Governance Decision
   → Structural Relay Archive
   → Next Residual / Question
```

### 25.1 Promotion levels

- **Research hypothesis:** a proposed structural analogy with no target validation.
- **Lab-supported candidate:** target synthetic tests support a narrow claim.
- **Independently replicated candidate:** an external or separate evaluator reproduces results.
- **Governance-approved pilot:** a target authority permits a limited, monitored pilot.
- **Operational control:** separately engineered and approved target enforcement, subject to ongoing review.

No promotion level follows automatically from a score or from a prior level in another domain.

### 25.2 Rollback and monitoring

Every consequential target pilot should define stop triggers, telemetry integrity, policy versioning, blast-radius constraints, and rollback or containment options. If an effect is irreversible, the plan must say so and prioritize prevention and bounded exposure rather than relying on rollback.

## 26. Research Roadmap

**Phase 0 — Contracts and taxonomy.** Reconcile CTU with SPEC-001–006; define domain adapter schemas and non-transfer conditions.

**Phase 1 — Synthetic datasets.** Build four laboratory families with hidden identity, authority, action, and consequence ground truth.

**Phase 2 — Baselines.** Implement target-only deterministic controls and naive transfer baselines before the full kernel.

**Phase 3 — Structural transfer.** Add UTN, REN, BCEF, provenance, and explicit mapping gates incrementally.

**Phase 4 — Adversarial evaluation.** Run authorized isolated Red/Blue/Evaluation/Governance scenarios, counterexamples, and distribution shifts.

**Phase 5 — AQSI and Relay.** Test whether autonomous transfer questions and residual registries improve validated discovery efficiency.

**Phase 6 — Independent replication.** Publish schemas, seeds, metrics, failures, and evaluator separation details; seek independent reproduction.

**Phase 7 — Optional target pilots.** Only after independent target authorization, threat modeling, implementation review, and bounded deployment planning. A pilot is not implied by completing prior phases.

### 26.1 Exit criteria

A phase should not advance on narrative plausibility alone. Required evidence includes passing contract tests, documented negative results, target-specific metrics, a safety gate assessment, and an independent reviewer decision.

## 27. Open Research Questions

1. What is the smallest transferable structural kernel that provides measurable target value?
2. Can semantic preservation be partially machine-checked without collapsing into shallow schema matching?
3. Which kinds of evidence dependence are most dangerous under cross-domain transfer?
4. How should transfer uncertainty be represented when source and target have different observability?
5. When does a compositional identity hypergraph outperform simpler role-based models?
6. Can BCEF detect false analogies early enough to reduce experiment cost?
7. How can target-only deterministic controls be combined with adaptive evidence without obscuring responsibility?
8. What evidence is sufficient to claim a bounded-loss property under common-mode failures?
9. Can AQSI find high-value negative-transfer questions before deployment?
10. How should multi-agent evaluation independence be quantified when models and infrastructure are shared?
11. Can residual taxonomies transfer without imposing the source domain's threat assumptions?
12. What governance process is needed when a transferred method changes a target organization's accountability structure?
13. Which transfer failures can be prevented through conformance tests, and which require empirical adversarial evaluation?
14. How can privacy-preserving evidence exchange retain enough provenance for independent validation?
15. When does the computational and organizational cost of CDSST exceed its defensive benefit?
16. Can cross-domain Structural Relay improve future research without repeatedly laundering unverified claims?

## 28. Limitations and Responsible Research Boundaries

This extension is a proposed research architecture. It has not demonstrated improved security outcomes in any target domain. Synthetic datasets may omit human behavior, operational incentives, rare events, legal obligations, and coordinated adversaries. Typed graphs can still encode wrong assumptions. Evidence models can be miscalibrated, and independent control planes can share hidden failure modes. Multi-agent evaluation may not be independent if participants use common data or infrastructure. A validated method can become invalid after a target changes its policies, assets, or attack surface.

Experiments must be conducted on owned or explicitly authorized systems, preferably isolated synthetic environments. This document supplies no authority to probe real organizations or change production policies. Sensitive data handling and target-specific regulatory constraints must be addressed independently. The research should publish negative results, unsupported claims, and unknowns as diligently as successful demonstrations.

## 29. Conclusion

Cross-domain structural security transfer is promising precisely because many failures share recurring patterns: valid local operations can conflict with legitimate global intent; control relationships are compositional and time-dependent; weak evidence is directional and correlated; and learning systems need independent safety boundaries. Yet these commonalities do not erase the differences among custody, cloud, enterprise workflows, AI agents, and software releases.

CDSST therefore proposes a disciplined separation: **reuse structural questions, typed representations, and validation methods; translate target semantics explicitly; preserve evidence uncertainty; reject false analogies; and require target-specific independent authorization for consequential actions.** A negative-transfer finding is a valuable research result, and a successful synthetic benchmark remains narrower than a production security guarantee.

The long-term opportunity is a **collective structural security learning ecosystem** in which independently validated insights travel between domains while authority, accountability, and bounded-risk obligations remain local and explicit.

> **Generalize the structure, not the guarantee. Transfer the question, test the mapping, preserve the boundary, and relay the evidence—including failures.**

---

## Appendix A — Suggested Repository Integration

**Primary file:** `extensions/EXT-003-Cross-Domain-Structural-Security-Transfer.md`

**Prior extension:** `extensions/EXT-002-Autonomous-Security-Questioning-and-Exploration.md`  
**Next extension:** `extensions/EXT-004-Open-Ended-Security-Evolution-and-Governance.md`

**Core research links:**

- `docs/ASSI-004-UTN-and-Compositional-Identity-Intelligence.md`
- `docs/ASSI-005-REN-and-Directional-Weak-Evidence-Intelligence.md`
- `docs/ASSI-006-Bidirectional-Conditional-Evidence-Feedback.md`
- `docs/ASSI-007-Structural-Authorization-and-Independent-Control-Planes.md`
- `docs/ASSI-009-Security-Residuals-and-Validated-Recursive-Self-Improvement.md`
- `docs/ASSI-010-ASSI-Grand-Architecture-and-Structural-Security-Units.md`
- `docs/ASSI-011-Benchmark-Laboratories-and-Falsifiable-Security-Hypotheses.md`
- `docs/ASSI-012-From-Cryptocurrency-Security-to-General-Structural-Defense.md`
- `specs/SPEC-001-Structural-Security-Unit-Contract.md`
- `specs/SPEC-002-Compositional-Identity-and-UTN-Contract.md`
- `specs/SPEC-003-Bidirectional-IF-and-Evidence-Impact-Contract.md`
- `specs/SPEC-004-Authorization-and-Safety-Control-Contract.md`
- `specs/SPEC-005-Adversarial-Drive-and-Relay-Contract.md`
- `specs/SPEC-006-Validated-RSI-and-Governance-Contract.md`

## Appendix B — Compact Transfer Review Checklist

- [ ] Source claim and maturity are correctly identified.
- [ ] Target asset, action, authority, and consequence semantics are documented.
- [ ] Typed mapping is partial where necessary; no silent equivalence.
- [ ] Identity, delegation, and policy time validity are represented.
- [ ] Evidence provenance and dependencies are inspectable.
- [ ] Hypotheses, alternatives, and falsification criteria are registered.
- [ ] Non-transfer conditions and common-mode risks are explicit.
- [ ] Experiment is authorized, isolated, bounded, and stoppable.
- [ ] Target-only baselines and hidden holdouts are available.
- [ ] Independent evaluation and governance are separated.
- [ ] Negative results and Security Residuals will be archived.
- [ ] No automatic policy promotion or deployment is possible.

## Appendix C — Glossary of Extension-Specific Terms

**CDSST:** Cross-Domain Structural Security Transfer, the proposed contract-first transfer framework.  
**CTU:** Cross-Domain Transfer Unit, a typed SSU-compatible record of a candidate transfer and its obligations.  
**Structural Defense Kernel:** Reusable structural mechanisms, not a universal security policy.  
**Domain Adapter:** Target- or source-specific definitions of identities, authority, evidence, consequences, and recovery.  
**Typed Partial Mapping:** Explicit correspondence between selected structures with permitted unmapped elements.  
**Semantic Preservation:** Evidence that a mapped relation retains the security meaning relevant to a particular claim.  
**Negative Transfer:** A target regression, invalid analogy, or newly introduced risk resulting from adaptation.  
**Non-Transfer Register:** A durable record of failed or prohibited mappings and their supporting evidence.  
**Target Holdout:** Target-domain evaluation scenarios excluded from candidate tuning.  
**Governance Gate:** Independent authorization required before consequential change.  
**Transfer Residual:** A gap between the proposed source-to-target correspondence and observed target behavior.  
**Structural Relay:** Traceable transmission of hypotheses, evidence, tests, residuals, and independently evaluated outcomes.

---

**Publication note:** This is a research foundation document. It proposes contracts, benchmarks, and falsifiable hypotheses but reports no executed experiments or verified security guarantees. Contributions and independent replication are welcome under the project's Apache-2.0 license.
