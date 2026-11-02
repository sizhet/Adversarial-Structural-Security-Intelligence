# SPEC-001 — Structural Security Unit Contract

**Project:** Adversarial Structural Security Intelligence (ASSI)  
**Version:** v0.1.0 — Research Foundation  
**Status:** Proposed normative interface specification; reference design, not a certified implementation  
**Date:** 2026-11-02  
**License:** Apache-2.0  
**Repository path:** `specs/SPEC-001-Structural-Security-Unit-Contract.md`  
**Related documents:** ASSI-004, ASSI-005, ASSI-006, ASSI-007, ASSI-008, ASSI-009, ASSI-010, ASSI-011, ASSI-012; SPEC-002–006 (planned)

## Abstract

This specification defines a canonical **Structural Security Unit (SSU)** envelope and a contract for safely exchanging security-relevant records among the six functional domains of Adversarial Structural Security Intelligence (ASSI). An SSU can represent an asset, identity hypothesis, observation, conditional test, authorization request, enforcement receipt, adversarial scenario, evaluation result, security residual, or governed improvement. Its purpose is to preserve type, provenance, time, epistemic status, authority boundaries, dependency lineage, and auditability across heterogeneous structural intelligence components. The contract distinguishes *data validity* from *evidence reliability*, *hypothesis support* from *identity verification*, and *advisory scoring* from *authorization authority*. It establishes field-level requirements, semantic invariants, canonical examples, validation algorithms, lifecycle rules, threat considerations, and conformance test vectors. The proposed contract is deliberately conservative: schema validation does not confer trust or authorize actions. The specification is a falsifiable engineering proposal and requires implementation, adversarial testing, and independent review before operational deployment.

**Keywords:** structural security unit; canonical contract; typed provenance; epistemic status; UTN; REN; BCEF; authorization; audit; conformance; governance.

---

## 1. Scope and Normative Language

### 1.1 Purpose

ASSI-010 introduced SSUs as a common interchange primitive across six functional domains: (D1) structural assets and trust, (D2) evidence and compositional identity, (D3) BCEF reasoning, (D4) independent authorization, (D5) adversarial drives, and (D6) residual-driven improvement and governance. SPEC-001 defines the shared envelope; the domain-specific semantics are delegated to SPEC-002–006. A record may be well formed under SPEC-001 while failing a domain-specific contract or being unfit for any consequential decision.

### 1.2 In scope

- A minimum interoperable envelope, extensible without semantic ambiguity.
- Typed identifiers, versions, provenance, temporal validity, dependency and integrity references.
- Separation of observation, inference, hypothesis, evaluation, and authorization.
- State transitions, append-only revisions, redaction and retention obligations.
- Conformance profiles and negative test vectors.
- Cross-domain transfer rules and explicit authority limits.

### 1.3 Out of scope

- A universal ontology of assets, persons, teams, jurisdictions, or threats.
- A particular cryptographic signature algorithm, key-management product, or storage engine.
- Numerical score calibration or an assertion that scores are probabilities.
- Automatic promotion of research hypotheses to operational policy.
- The domain-specific rules in SPEC-002–006 or any certification of deployed security.

### 1.4 Requirement terms

**MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** indicate respectively mandatory, prohibited, recommended, discouraged, and optional requirements **within this proposed contract**. These terms do not assert external standards compliance. A conforming implementation MUST declare the contract version and profile against which it was tested.

---

## 2. Design Commitments

1. **Type before interpretation.** Every SSU identifies its family and unit type; consumers MUST reject unknown consequential types unless explicitly handled as opaque, non-actionable data.
2. **Provenance before confidence.** A score without identifiable origin, derivation, and calibration context MUST NOT be treated as a validated probability.
3. **Temporal and contextual specificity.** An observation, identity, permission, or risk assessment is not timeless.
4. **Evidence does not equal authority.** No SSU's confidence or provenance field, by itself, grants authorization.
5. **Hypotheses remain scoped.** Contradictions and validation claims apply to the precise proposition tested.
6. **Independent hard controls.** The SSU interface MUST NOT allow adaptive scoring to override independently governed enforcement policy.
7. **Append-only accountability.** Revisions and structural edits MUST preserve a traceable prior state.
8. **Safe uncertainty.** Unknown, unavailable, conflicting, and unobserved are distinct states; absence of evidence is not automatically negative evidence.
9. **Bounded generalization.** Cross-domain adapters MUST explicitly declare what semantics they preserve and what they do not.
10. **Conformance before runtime.** Schema, semantic, lifecycle, and authority tests precede live integration.

---

## 3. Canonical SSU Model

### 3.1 Top-level envelope

An SSU consists of an envelope and a typed payload. The envelope carries shared control information; the payload is interpreted under a registered `unit_type` and `payload_schema`.

| Field | Type | Requirement | Meaning |
|---|---|---|---|
| `ssu_version` | semver-like string | MUST | Version of this common contract |
| `unit_id` | stable identifier string | MUST | Globally scoped logical unit identifier |
| `revision` | positive integer | MUST | Monotonically increasing revision for `unit_id` |
| `unit_family` | enum | MUST | Structural, Identity, Evidence, Reasoning, Authorization, Adversarial, Evolution, Governance |
| `unit_type` | registered string | MUST | Precise semantic type |
| `payload_schema` | versioned schema identifier | MUST | Contract governing the payload |
| `created_at` | UTC timestamp | MUST | Record creation time |
| `time` | object | MUST | Event, observation, validity and assessment times, as applicable |
| `scope` | object | MUST | Environment, domain and applicable contextual boundary |
| `epistemic` | object | MUST | Knowledge status and claim scope |
| `source` | object | MUST | Origin, trust limitations, integrity reference if available |
| `provenance` | object | MUST | Parent units, transformations and dependence group |
| `lifecycle` | object | MUST | Current state and reason for state change |
| `policy` | object | MUST | Sensitivity, permitted uses and retention class |
| `payload` | object | MUST | Type-specific data |
| `audit` | object | MUST | Validation status and reviewer/automation references |
| `integrity` | object | SHOULD | Digest, signing context or external tamper-evidence reference |
| `extensions` | object | MAY | Namespaced, non-authoritative extensions |

A required object MAY contain null fields where explicitly allowed. A producer MUST NOT replace a required field with an undocumented omission. Consumers MUST distinguish an explicit `null` (not available/not applicable according to the field contract) from a missing field (potentially malformed input).

### 3.2 Canonical illustrative record

```yaml
ssu_version: "0.1.0"
unit_id: "urn:assi:ssu:synthetic-observation-0001"
revision: 1
unit_family: "Evidence"
unit_type: "ObservationUnit"
payload_schema: "urn:assi:schema:observation:0.1.0"
created_at: "2026-11-02T10:00:00Z"
time:
  event_at: "2026-11-02T09:58:00Z"
  observed_at: "2026-11-02T09:58:04Z"
  assessed_at: null
  valid_from: "2026-11-02T09:58:00Z"
  valid_until: null
scope:
  domain: "synthetic-ledger"
  environment: "isolated-sandbox"
  tenant_ref: "urn:assi:tenant:lab-01"
  boundary_ref: "urn:assi:boundary:lab-only"
  jurisdiction: null
epistemic:
  status: "observed"
  proposition_ref: "urn:assi:proposition:transfer-0001"
  limitations:
    - "Transaction event does not establish real-world controller identity"
source:
  source_id: "urn:assi:source:lab-ledger"
  source_class: "simulation"
  acquisition_method: "sandbox-event-log"
  integrity_reference: null
  verification_status: "source-checked"
provenance:
  parent_unit_ids: []
  transformation_id: null
  independence_group: "urn:assi:dependency:lab-event-0001"
  derivation_depth: 0
lifecycle:
  state: "active"
  transition_reason: "initial-ingestion"
  supersedes_revision: null
policy:
  sensitivity: "internal-test"
  permitted_uses: ["research", "evaluation"]
  retention_class: "research"
  authority_class: "none"
payload:
  subject_ref: "urn:assi:synthetic-address:A"
  predicate: "transferred_to"
  object_ref: "urn:assi:synthetic-address:B"
  amount: "12.50"
  unit: "SYN"
audit:
  schema_validation: "passed"
  semantic_validation: "pending"
  validated_against: "urn:assi:schema:observation:0.1.0"
  reviewer_ref: null
integrity:
  digest_algorithm: null
  digest: null
  signature_ref: null
extensions: {}
```

This is a **synthetic, non-normative instance** illustrating the normative field rules. `schema_validation: passed` in an example is not evidence that an external validator actually ran. A real system MUST generate audit claims from its validation process, not accept producer-supplied claims as authoritative.

---

## 4. Identity, Naming and Versioning

### 4.1 Stable identifiers

`unit_id` MUST be unique within its declared namespace. Producers SHOULD use a resolvable internal registry or collision-resistant identifier scheme. The illustrative `urn:assi:...` syntax is a project convention, not a globally registered URN namespace. Identity of a unit is not identity of the person, team, service, or asset it describes.

### 4.2 Revision semantics

A revision is a new immutable representation of the *same logical unit*. It MUST increment `revision`, preserve `unit_id`, and link to the prior revision through the revision chain. A new claim that materially changes the proposition SHOULD receive a new `unit_id` and a `derived_from` or `supersedes` relationship rather than silently replacing the original. A consumer MUST NOT infer that the highest revision is the most credible without checking its provenance and lifecycle.

### 4.3 Unit reference types

References SHOULD declare their intended relation: `supports`, `contradicts`, `derived_from`, `evaluates`, `authorizes`, `enforced_by`, `supersedes`, `member_of`, `controlled_by`, or `related_to`. The relation is a typed assertion, not automatically a fact. A relationship to an authorization decision MUST NOT itself grant the referenced unit authority.

### 4.4 Type registry

The registry MUST associate each `unit_type` with an owning domain, schema version, allowed epistemic states, lifecycle, validation rules, and authority classification. Unknown types MAY be stored for forensic review but MUST NOT be executed, promoted, or used to satisfy a hard authorization requirement.

---

## 5. Time and Validity Semantics

A single timestamp is insufficient for security reasoning. The contract distinguishes:

- `event_at`: when the underlying event is claimed to have occurred.
- `observed_at`: when a collector or analyst obtained the observation.
- `assessed_at`: when an inference, test, or evaluation was produced.
- `created_at`: when the SSU record was materialized.
- `valid_from` / `valid_until`: interval for which the claim or authorization is asserted to apply.

All populated timestamps MUST use an unambiguous UTC representation; timestamps from untrusted sources MUST carry uncertainty or a source-clock limitation when material. `valid_until: null` MUST NOT be interpreted as permanent validity. For authorization-related units, a domain contract MUST specify expiry and freshness constraints. Consumers MUST NOT silently treat an out-of-window assertion as current. Event time and recording time MAY differ legitimately; a validator MUST NOT reject all late-arriving evidence merely because `observed_at` exceeds `event_at`.

### 5.1 Bitemporal corrections

Where retrospective corrections matter, an implementation SHOULD preserve both the claimed valid-time interval and the time the system learned or recorded that claim. This permits questions such as: *What did the defender know at the moment of authorization?* and *What later evidence revised that understanding?* Benchmarks MUST avoid leaking later knowledge into earlier decisions.

---

## 6. Epistemic and Evidence Contract

### 6.1 Epistemic states

| State | Meaning | Prohibited inference |
|---|---|---|
| `observed` | Source records a defined event or artifact | Does not prove controller identity or causality |
| `derived` | Output of an identified transformation | Does not constitute independent corroboration |
| `hypothesized` | Defeasible claim with explicit alternatives | Does not establish an authorized principal |
| `supported` | Evidence favors a scoped hypothesis under named criteria | Does not mean certain or globally true |
| `contested` | Material support and counterevidence coexist | Does not mean false |
| `validated` | Named test criteria were met in a defined context | Does not imply universal truth or operational approval |
| `rejected` | Scoped proposition failed specified criteria | Does not refute broader alternative hypotheses |
| `unknown` | Evidence insufficient or unavailable | Does not imply negative evidence |

`validated` MUST be accompanied by `validation_method_ref`, `validation_scope`, and an auditable result when used for a consequential claim. Evidence acquisition, inferential transformation, and independent evaluation MUST be distinguishable.

### 6.2 Hypothesis portfolios

Identity or control attribution SHOULD maintain competing hypotheses (e.g., same person, shared team, common service, independent actors responding to a common trigger). A contradiction to one hypothesis MUST NOT be propagated to another without an explicit test. This is the **hypothesis-scoped contradiction invariant**.

### 6.3 Confidence and calibration

A confidence object, when present, SHOULD include `measure_type`, `value`, `range`, `calibration_profile`, `population_scope`, and `assessment_ref`. Producers MUST NOT label an arbitrary score as a posterior probability. Consumers MUST NOT combine scores from incompatible calibration profiles without a documented mapping. Missing confidence MUST NOT be replaced with zero confidence or zero risk by default.

---

## 7. Provenance, Dependence and Integrity

### 7.1 Provenance graph

Every derived or hypothesized unit MUST identify its immediate input units or explicitly document why they cannot be disclosed. Redacted provenance MUST include an authorized reference to the restricted evidence, rather than fabricate an independent source. The provenance graph MUST be acyclic for derivation relations; cross-references representing discourse or mutual evaluation MUST be modeled separately from derivation edges.

### 7.2 Independence groups

`independence_group` records potential shared origin or correlation. It is a conservative bookkeeping aid, not a statistical proof of independence. Multiple features extracted from one transaction trace SHOULD share a dependence group. A BCEF test of an evidence unit MUST NOT be counted as a new independent observation of the same event. Producers SHOULD record source family, collection pipeline, and transformation chain to support dependency-aware aggregation.

### 7.3 Integrity is not truth

A digest or signature may show that a representation has not changed or that a key endorsed it. It does **not** prove the source is honest, the inference is sound, or the action is legitimate. Consumers MUST verify the declared integrity mechanism independently when its result matters. Placeholder digests, malformed signatures, and untrusted producer assertions MUST NOT be accepted as verified.

### 7.4 Canonicalization

A deployment claiming byte-level integrity MUST define a deterministic serialization and canonicalization algorithm, including field ordering, numeric representation, Unicode handling, nulls, and excluded signature fields. This draft intentionally does not prescribe one; therefore cross-implementation digest equivalence is **not** claimed at v0.1.0. Implementations MUST NOT compare digests across incompatible canonicalization profiles as if they were equivalent.

---

## 8. Structural Security Unit Families

| Family | Example types | Key contract concern | Specialized contract |
|---|---|---|---|
| Structural | `AssetUnit`, `TrustBoundaryUnit`, `ExposureUnit` | Asset scope, dependencies, failure domains | Domain adapter / ASSI-010 |
| Identity | `TypedEntityUnit`, `CompositionUnit`, `IdentityHypothesisUnit` | UTN, overlapping membership, hypothesis scope | SPEC-002 |
| Evidence | `ObservationUnit`, `EvidenceUnit`, `CounterEvidenceUnit` | Source lineage, dependence, time | SPEC-002/003 |
| Reasoning | `IFTestUnit`, `EvidenceImpactUnit`, `ScoringSnapshotUnit` | Conditional semantics, scoped impact | SPEC-003 |
| Authorization | `AuthorizationRequestUnit`, `PolicyDecisionUnit`, `EnforcementReceiptUnit` | Authority, policy version, independent enforcement | SPEC-004 |
| Adversarial | `ScenarioUnit`, `DriveUnit`, `EvaluationUnit`, `FailureTraceUnit` | Authorization, isolation, evaluator separation | SPEC-005 |
| Evolution | `SecurityResidualUnit`, `QuestionUnit`, `CandidateImprovementUnit`, `ValidationUnit`, `RelayUnit` | Evidence of improvement, controlled promotion | SPEC-006 |
| Governance | `ApprovalUnit`, `ExceptionUnit`, `RollbackUnit` | Authorized decision, accountability, expiry | SPEC-004/006 |

An SSU's family does not determine who may create it, who may approve it, or whether it may trigger action. Those are explicit, independently enforced capabilities.

---

## 9. Structural Relations and Compositional Identity

### 9.1 Relation contract

A structural relation SHOULD carry `relation_id`, typed endpoints, `relation_type`, `scope`, validity interval, source references, and epistemic status. Relations between actors and roles MAY be many-to-many and overlapping. Hyperedges or reified relation nodes SHOULD be supported for coalition or shared-service hypotheses. A graph edge labeled `controlled_by` MUST distinguish verified control from inferred behavioral similarity.

### 9.2 Reversible merge and split

When a scoring system proposes merging identity nodes, the proposal MUST be represented as a new derived hypothesis or reversible graph operation. The original nodes and supporting evidence MUST remain recoverable. Splitting a previously merged identity MUST preserve the history of the earlier inference and the reason for revision. No structural merge MAY silently rewrite past authorization receipts.

### 9.3 Domain separation

A synthetic on-chain address, enterprise user, service account, and AI agent identity may share a structural representation but MUST retain their domain-specific authority semantics. A cross-domain mapping MUST explicitly declare semantic losses and verification limits.

---

## 10. Scoring, BCEF and Impact Feedback

### 10.1 Advisory scoring contract

Scoring units MUST state the target hypothesis, evidence snapshot, directional context, score definition, calibration status, dependency treatment, and model version. Scores MUST NOT be treated as authorization decisions. A model update MUST produce a new scoring snapshot with lineage to its predecessor.

### 10.2 Conditional tests

BCEF test units SHOULD identify one of four modes: `forward`, `reverse_diagnostic`, `counterfactual`, or `contradiction`. A reverse diagnostic test MUST NOT equate `H implies E` with `E implies H`; it must consider alternatives and base rates where relevant. A counterfactual test MUST document its intervention assumptions. A contradiction test MUST specify the exact proposition being challenged.

### 10.3 Structured impacts

An `EvidenceImpactUnit` SHOULD separate:

1. The proposition or score affected.
2. The sign and magnitude of any justified revision.
3. The supporting and counterevidence lineage.
4. Proposed structural edits (merge, split, add relation, retract relation).
5. Uncertainty and alternative hypotheses.
6. The proposed next test or AQSI question.
7. Any requested policy change, clearly marked **proposal only**.

Impact propagation MUST preserve provenance and MUST NOT double count the same underlying observation. Recursive impact processing MUST have bounded depth, a termination condition, and loop detection. A structural impact MUST NOT alter hard authorization policy without separate governance approval.

---

## 11. Authorization and Independent Safety Boundaries

### 11.1 Authority separation

`policy.authority_class` MUST distinguish `none`, `advisory`, `request`, `evaluation`, `approval`, and `enforcement_receipt` (or a documented compatible profile). A unit claiming `approval` MUST include an independently verifiable approval authority, scope, policy version, and decision record. A unit claiming `enforcement_receipt` MUST identify the enforcement point and the independently observed outcome. The producer's claimed class is never sufficient proof.

### 11.2 Mandatory safety invariants

- A syntactically valid SSU MUST NOT bypass a hard deny, spending cap, time lock, multi-party authorization, or recovery gate.
- An `EvidenceImpactUnit` MUST NOT be reinterpreted as an approval or policy exception.
- A policy exception MUST be explicit, narrowly scoped, time-bounded, and approved through the independent governance path.
- An advisory score MAY inform a stricter review decision but MUST NOT automatically weaken a mandatory control.
- The system MUST preserve a safe failure mode when provenance, policy version, evaluator status, or required approval cannot be verified.

### 11.3 Decision versus receipt

An authorization decision expresses what a policy engine decided; an enforcement receipt records what an enforcement point actually did. These MUST be separate records or separately verifiable fields. A `permit` decision without an enforcement receipt MUST NOT be reported as a completed authorized action.

---

## 12. Lifecycle and State Transitions

### 12.1 Common lifecycle

The generic SSU lifecycle is:

`draft → submitted → schema_checked → semantically_checked → active → superseded / revoked / archived`

A failed check moves the unit to `quarantined` or `rejected`; it does not delete it from the audit trail. `active` means eligible for the uses permitted by its type and policy, not globally trustworthy or authorized. Domain-specific lifecycles may be stricter.

### 12.2 Transition rules

Every state transition MUST record `from_state`, `to_state`, `timestamp`, `actor_or_service_ref`, `reason`, and a link to the prior revision or transition event. Transitions MUST be checked against the declared type registry. A revoked unit MUST NOT be used for new consequential decisions unless a domain-specific exception is independently approved and recorded. Historical replay MAY reference revoked evidence to reconstruct what was known earlier, but MUST label it as historical.

### 12.3 Validation is multidimensional

The contract distinguishes at least four checks: **schema**, **semantic**, **provenance/integrity**, and **authority**. Passing schema validation MUST NOT imply that the other three passed. A single unqualified `validated: true` field is insufficient for consequential use.

---

## 13. Cross-Domain Interface Contract

The ASSI-010 interfaces are refined as follows:

| Interface | Units exchanged | Minimum consumer obligation |
|---|---|---|
| I-01 D1→D2 | Asset, boundary, dependency | Check scope, graph snapshot and time |
| I-02 D2→D3 | Evidence, identity hypotheses | Check provenance, alternatives, dependency groups |
| I-03 D3→D4 | IF tests, impacts, advisory scores | Enforce advisory-only authority and freshness |
| I-04 D4→D1/D5 | Decisions and enforcement receipts | Verify policy authority and actual enforcement |
| I-05 D5→D6 | Scenarios, evaluation and failure traces | Verify isolation, authorization and evaluator separation |
| I-06 D6→D2/D3 | Approved model/test revisions | Verify promotion, reproducibility and rollback metadata |
| I-07 D6→D4 | Proposed policy revisions | Treat as proposals pending independent approval |

### 13.1 Consumer negotiation

A consumer MUST declare supported `ssu_version`, `unit_type`, `payload_schema`, and authority profile. Unknown major versions MUST be rejected for consequential workflows. Minor-version extension fields MAY be preserved as opaque data but MUST NOT silently change the interpretation of existing fields. Producers SHOULD support explicit capability negotiation rather than relying on permissive parsing.

### 13.2 Idempotency and ordering

Ingestion MUST be idempotent for the same `(unit_id, revision, integrity profile)` tuple. Conflicting bytes for the same tuple MUST raise a conflict event, not silently overwrite. Consumers MUST NOT assume delivery order equals event order. Replayed or delayed records MUST be evaluated against current validity and policy constraints.

---

## 14. Validation Algorithm (Reference Pseudocode)

The following is illustrative and deliberately separates data checks from authority checks:

```text
function validate_ssu(unit, registry, context):
    errors = []
    require_fields(unit, registry.common_required, errors)
    check_version_compatibility(unit.ssu_version, context, errors)
    check_id_and_revision(unit.unit_id, unit.revision, errors)
    check_registered_type(unit.unit_type, unit.unit_family, errors)
    check_payload_schema(unit.payload_schema, unit.payload, errors)
    check_timestamp_formats_and_intervals(unit.time, unit.created_at, errors)
    check_scope_and_permitted_uses(unit.scope, unit.policy, context, errors)
    check_provenance_links(unit.provenance, context, errors)
    check_dependency_cycles(unit.provenance, context, errors)
    check_lifecycle_transition(unit.lifecycle, context, errors)
    check_epistemic_requirements(unit.epistemic, unit.unit_type, errors)

    if errors is not empty:
        return QUARANTINED(errors)

    semantic_result = domain_validator(unit, context)
    integrity_result = independent_integrity_verifier(unit, context)
    authority_result = independent_authority_verifier(unit, context)

    return ValidationRecord(
        schema = PASSED,
        semantic = semantic_result,
        integrity = integrity_result,
        authority = authority_result,
        permitted_actions = policy_engine_decision(unit, context)
    )
```

`policy_engine_decision` MUST be implemented by the appropriate independent control path, not by a caller-supplied SSU field. An unavailable authority verifier MUST NOT default to `approved`.

---

## 15. Conformance Invariants

A proposed SPEC-001 conformant implementation MUST satisfy all applicable invariants:

| ID | Invariant | Test intent |
|---|---|---|
| SSU-INV-01 | Every consequential record has a unique ID, revision, type and schema | Reject missing or conflicting identity |
| SSU-INV-02 | All required timestamps are explicit and parseable | Detect ambiguity and stale use |
| SSU-INV-03 | Provenance is retained for derived and inferred claims | Trace source lineage |
| SSU-INV-04 | Derivation cycles are rejected or quarantined | Prevent circular evidence amplification |
| SSU-INV-05 | Epistemic status is distinct from authority | Reject hypothesis-as-approval |
| SSU-INV-06 | Confidence requires declared meaning and calibration context | Reject uncalibrated probability claims |
| SSU-INV-07 | Hypothesis contradiction is scoped | Prevent invalid team-level rejection |
| SSU-INV-08 | Dependency groups prevent naive evidence duplication | Detect correlated feature counting |
| SSU-INV-09 | Revisions and structural edits preserve audit history | Reconstruct prior decisions |
| SSU-INV-10 | Schema pass does not imply semantic/integrity/authority pass | Separate validators |
| SSU-INV-11 | Hard controls cannot be overridden by advisory units | Negative authorization test |
| SSU-INV-12 | Decision and enforcement outcome are independently distinguishable | Reject false execution claims |
| SSU-INV-13 | Unknown types/major versions are non-actionable | Safe version negotiation |
| SSU-INV-14 | Revocation and expiry are enforced at decision time | Reject stale evidence/permission |
| SSU-INV-15 | Redaction preserves auditable restricted references | Prevent provenance fabrication |
| SSU-INV-16 | Experimental units cannot escape authorized sandbox scope | Contain adversarial drives |
| SSU-INV-17 | Model or policy promotion requires independent approval | Reject self-promotion |
| SSU-INV-18 | Replay and conflicting revisions are detected | Prevent silent overwrite |
| SSU-INV-19 | Cross-domain transfer declares semantic limits | Reject invalid ontology equivalence |
| SSU-INV-20 | Validation outcomes and exceptions are recorded separately | Support independent audit |

These are contract requirements, not a statement that an implementation currently passes them.

---

## 16. Conformance Test Vectors

A test harness SHOULD include at least the following cases. All examples use synthetic records; expected outcomes are normative for the proposed profile.

| Test | Input condition | Expected result |
|---|---|---|
| CT-001 | Fully formed synthetic observation with valid provenance | Schema pass; semantic/integrity/authority separately assessed |
| CT-002 | Missing `unit_type` | Reject/quarantine |
| CT-003 | Unknown major contract version in authorization path | Reject |
| CT-004 | Derived evidence with absent parent lineage | Reject or quarantine pending restricted reference |
| CT-005 | Two derived features from same event submitted as independent | Flag dependency conflict; no independent corroboration |
| CT-006 | Hypothesis of same individual rejected, same team remains plausible | Reject only scoped individual hypothesis |
| CT-007 | `EvidenceImpactUnit` declares `permit` | No authorization; reject authority escalation |
| CT-008 | Policy decision says permit but enforcement receipt absent | Decision recorded; action not reported executed |
| CT-009 | Unit validity interval expired | Reject for current consequential use |
| CT-010 | Conflicting bytes under same ID and revision | Conflict/quarantine; no overwrite |
| CT-011 | Provenance derivation cycle | Reject or quarantine |
| CT-012 | `validated` epistemic status with no method or scope | Reject consequential validation claim |
| CT-013 | Sandbox drive requests production resource | Deny and record scope violation |
| CT-014 | Candidate improvement self-approves its policy revision | Reject promotion |
| CT-015 | Cross-domain unit lacks semantic mapping declaration | Reject transfer for consequential use |
| CT-016 | Redacted evidence with authorized restricted provenance pointer | Permit controlled review, not automatic trust |

### 16.1 Acceptance criteria

For each profile, the implementer MUST publish: schema coverage, negative-test coverage, unresolved deviations, and independently reproduced test results. Passing the positive example alone is insufficient. A claim of conformance MUST identify the implementation version, test suite version, evaluation date, and known limitations.

### 16.2 Property-based tests

Recommended generated properties include: uniqueness under randomized ingestion order; immutability of prior revisions; no authority escalation through arbitrary extension fields; noninterference between hypothesis scopes; idempotent replay; rejection of unknown consequential types; and stable provenance reconstruction after merge/split proposals.

---

## 17. Security and Privacy Threat Model

### 17.1 Threats to the unit layer

- **Provenance laundering:** forged parent chains make weak evidence appear independent.
- **Type confusion:** a low-trust observation masquerades as an approval or enforcement receipt.
- **Score laundering:** an uncalibrated similarity metric is labeled a probability or authorization basis.
- **Temporal manipulation:** stale or future-dated records influence current decisions.
- **Namespace collision:** attacker-controlled identifiers impersonate trusted assets or authorities.
- **Replay and equivocation:** old or conflicting revisions are presented as current.
- **Schema downgrade:** a permissive parser accepts semantics unsupported by its version.
- **Evaluation contamination:** benchmark labels or future observations leak into earlier decision snapshots.
- **Policy bypass through extensions:** an unrecognized field is treated as an executable instruction.
- **Privacy leakage:** composition and identity graphs reveal sensitive affiliations without necessity.

### 17.2 Required mitigations

Implementations MUST treat all incoming payloads as untrusted data, apply least-privilege access controls, separate provenance verification from producer assertions, and restrict executable or policy-bearing semantics to registered types. Sensitive identity hypotheses SHOULD use pseudonymous identifiers, purpose-limited access, retention policies, and documented review procedures. A proposed identity relationship MUST NOT be presented as verified personal identity merely because it appears in a well-formed graph.

### 17.3 Failure handling

The default for an invalid or ambiguous SSU is **quarantine for analysis, deny consequential promotion, preserve audit**. This does not mean every uncertainty requires shutting down all benign operations; the independent domain policy determines the safe degraded mode. In no case does schema ambiguity create a new privilege.

---

## 18. Cross-Domain Portability and Domain Adapters

The common envelope can carry structural claims from synthetic ledgers, enterprise identity systems, cloud infrastructure, AI agents, and software supply chains. It cannot make their authority models interchangeable. Each adapter MUST document:

1. Native entity and action ontology.
2. Asset, hazard and exposure semantics.
3. Identity and delegation verification model.
4. Event clock, freshness and observability limitations.
5. Native enforcement and recovery mechanisms.
6. Data privacy, retention and jurisdictional constraints.
7. Unsupported mappings and known semantic loss.
8. Independent policy and governance authority.

A transfer is valid only for the properties explicitly mapped and tested. For example, an on-chain transaction observation may correspond structurally to an enterprise audit event, but neither alone establishes the legitimacy of the human intent behind it.

---

## 19. Validation Roadmap

**Phase 0 — Contract registry.** Establish schema registry, unit type ownership, version compatibility and requirement traceability. Define explicit tests for all 20 invariants.

**Phase 1 — Reference validator.** Implement schema, temporal, provenance and lifecycle checks. Produce negative-test fixtures and deterministic conflict handling.

**Phase 2 — Domain adapters.** Build synthetic ledger and enterprise authorization adapters. Test preservation and loss of identity, time, and authority semantics.

**Phase 3 — BCEF and scoring integration.** Exchange evidence and impacts while measuring double counting, contradiction scope and provenance completeness.

**Phase 4 — Independent authorization.** Demonstrate that forged advisory, score, or impact units cannot bypass hard safety constraints; independently verify enforcement receipts.

**Phase 5 — Adversarial relay and RSI.** Run sandbox drives, residual accounting, candidate improvements and independent promotion gates; measure audit reconstruction and rollback.

**Phase 6 — Independent reproduction.** Publish synthetic fixtures, versioned test suites, known failures and independent results. Do not label the system production secure merely because conformance tests pass.

### 19.1 Suggested metrics

- Schema acceptance/rejection accuracy and false acceptance rate.
- Provenance completeness and reconstructability.
- Dependency double-count detection rate.
- Invalid hypothesis-scope propagation rate.
- Unauthorized promotion or bypass success rate (target: zero in tested conditions).
- Temporal freshness violation rate.
- Revision conflict detection and replay handling.
- Time and storage overhead per unit family.
- Cross-domain semantic mapping error rate.
- Audit replay reproducibility and privacy exposure.

Metrics MUST be accompanied by test population, adversarial assumptions, and confidence intervals or uncertainty bounds when appropriate.

---

## 20. Open Questions and Falsifiable Hypotheses

**H-SSU-01 — Traceability.** A canonical SSU envelope improves the proportion of decisions whose evidence lineage can be independently reconstructed compared with untyped log records. *Falsification:* no meaningful gain or unacceptable overhead on matched scenarios.

**H-SSU-02 — Dependence safety.** Explicit provenance and independence groups reduce double-counting of correlated evidence. *Falsification:* error rates do not improve relative to a strong provenance-aware baseline.

**H-SSU-03 — Authority separation.** Typed advisory/approval/receipt boundaries reduce successful type-confusion escalation. *Falsification:* attack success remains unchanged against a properly configured baseline policy engine.

**H-SSU-04 — Temporal fidelity.** Multi-time SSUs improve retrospective decision reconstruction. *Falsification:* no improvement over an equally detailed bitemporal event store.

**H-SSU-05 — Hypothesis scope.** Explicit proposition references reduce false rejection of team-level identities when individual-level hypotheses fail. *Falsification:* no reduction against a strong multi-hypothesis graph baseline.

**H-SSU-06 — Transfer discipline.** Domain adapters with explicit semantic-loss declarations reduce cross-domain mapping errors. *Falsification:* no gain against well-engineered conventional typed adapters.

**H-SSU-07 — Governance auditability.** Append-only revisions and separate validation/approval records improve independent audit reconstruction of model promotions. *Falsification:* no measurable improvement over standard event-sourced governance systems.

**H-SSU-08 — Feasibility.** The common envelope adds manageable overhead for selected workloads. *Falsification:* latency, throughput, or storage costs exceed predefined domain budgets without offsetting safety or audit benefits.

All hypotheses require preregistered workloads, strong baselines, and independent evaluation. None is established by this document.

---

## 21. Implementation Guidance and Non-Goals

A practical implementation SHOULD begin with a minimal JSON Schema or equivalent typed schema for the envelope, a type registry, an append-only event store, a provenance DAG index, and independent validators. Serialization, transport, and storage MAY vary by deployment. The common schema SHOULD avoid embedding domain-specific business logic; specialized contracts SHOULD define it.

A successful implementation is not a universal security oracle. The SSU layer cannot independently determine a real-world person's intent, eliminate all unknown threats, guarantee source truthfulness, or replace governance and operational controls. Its value, if demonstrated, is to make claims and decisions **more explicit, testable, transferable, and auditable**.

---

## 22. Relationship to the ASSI Series

- **ASSI-001–003:** validity, legitimacy, trust relocation, structural boundaries.
- **ASSI-004:** UTN and compositional identity; specialized by SPEC-002.
- **ASSI-005:** REN, directional evidence, weak-evidence dependence.
- **ASSI-006:** BCEF, scoped conditional tests and structured impacts; specialized by SPEC-003.
- **ASSI-007:** independent authorization and bounded loss; specialized by SPEC-004.
- **ASSI-008:** adversarial drives and competitive relay; specialized by SPEC-005.
- **ASSI-009:** security residuals, validated RSI and governance; specialized by SPEC-006.
- **ASSI-010:** six-domain grand architecture and preliminary SSU envelope.
- **ASSI-011:** four benchmark laboratories and falsifiable evaluation.
- **ASSI-012:** general structural defense and cross-domain adapters.

**SPEC-001** is the common interchange and conformance foundation, not a replacement for the domain-specific contracts.

---

## 23. Conclusion

The Structural Security Unit is proposed as a disciplined interface between structural reasoning and security engineering. Its canonical envelope records **what is claimed, about which entity and context, from which source, at what time, with what evidence dependence, under which epistemic status, and with what authority limitations**. The most important guarantee sought by this contract is not that every claim is correct; it is that claims are not silently promoted across boundaries—from observation to inference, inference to identity, score to authorization, simulation to validation, or candidate improvement to policy. Those transitions require explicit evidence, domain semantics, independent checks, and governance.

**Contract principle:** *Make claims portable, make provenance inspectable, make authority non-transferable by inference, and make consequential transitions independently verifiable.*

---

## Appendix A — Minimal Machine-Readable Envelope Profile (Illustrative)

```json
{
  "ssu_version": "0.1.0",
  "unit_id": "urn:assi:ssu:example-0002",
  "revision": 1,
  "unit_family": "Reasoning",
  "unit_type": "IFTestUnit",
  "payload_schema": "urn:assi:schema:if-test:0.1.0",
  "created_at": "2026-11-02T12:00:00Z",
  "time": {"event_at": null, "observed_at": null, "assessed_at": "2026-11-02T12:00:00Z", "valid_from": "2026-11-02T12:00:00Z", "valid_until": null},
  "scope": {"domain": "synthetic-ledger", "environment": "isolated-sandbox", "tenant_ref": "urn:assi:tenant:lab-01", "boundary_ref": "urn:assi:boundary:lab-only", "jurisdiction": null},
  "epistemic": {"status": "hypothesized", "proposition_ref": "urn:assi:hypothesis:shared-service", "limitations": ["Not a verified controller identity"]},
  "source": {"source_id": "urn:assi:source:reasoner-v1", "source_class": "derived-model", "acquisition_method": "bcef-test", "integrity_reference": null, "verification_status": "unverified"},
  "provenance": {"parent_unit_ids": ["urn:assi:ssu:synthetic-observation-0001"], "transformation_id": "urn:assi:transform:bcef-v1", "independence_group": "urn:assi:dependency:lab-event-0001", "derivation_depth": 1},
  "lifecycle": {"state": "draft", "transition_reason": "test-created", "supersedes_revision": null},
  "policy": {"sensitivity": "internal-test", "permitted_uses": ["research"], "retention_class": "research", "authority_class": "advisory"},
  "payload": {"mode": "contradiction", "target_hypothesis_ref": "urn:assi:hypothesis:shared-service", "outcome": "unknown"},
  "audit": {"schema_validation": "pending", "semantic_validation": "pending", "validated_against": null, "reviewer_ref": null},
  "integrity": {"digest_algorithm": null, "digest": null, "signature_ref": null},
  "extensions": {}
}
```

## Appendix B — Suggested Schema Registry Entry

```yaml
registry_version: "0.1.0"
unit_type: "IFTestUnit"
unit_family: "Reasoning"
payload_schema: "urn:assi:schema:if-test:0.1.0"
owning_domain: "D3-BCEF"
allowed_epistemic_states:
  - hypothesized
  - supported
  - contested
  - rejected
  - unknown
authority_ceiling: "advisory"
requires:
  - provenance.parent_unit_ids
  - epistemic.proposition_ref
  - payload.mode
  - payload.target_hypothesis_ref
  - payload.outcome
forbidden_transitions:
  - "advisory-to-approval"
  - "draft-to-enforcement-receipt"
validation_profile: "SPEC-001 + SPEC-003"
```

## Appendix C — Change Notes

**v0.1.0 — 2026-11-02:** Initial proposed canonical SSU contract, eight unit families, 20 conformance invariants, 16 test vectors, typed authority separation, temporal and provenance semantics, lifecycle rules, and cross-domain adapter obligations. No production conformance claim is made.

**Next specification:** `specs/SPEC-002-Compositional-Identity-and-UTN-Contract.md`.
