# SPEC-002 — Compositional Identity and UTN Contract

**Project:** Adversarial Structural Security Intelligence (ASSI)  
**Version:** v0.1.0 — Research Foundation  
**Status:** Proposed normative domain contract; not an implemented or certified identity service  
**Date:** 2026-11-02  
**License:** Apache-2.0  
**Repository path:** `specs/SPEC-002-Compositional-Identity-and-UTN-Contract.md`  
**Depends on:** `specs/SPEC-001-Structural-Security-Unit-Contract.md`  
**Related research:** ASSI-004, ASSI-005, ASSI-006, ASSI-007, ASSI-010, ASSI-011  
**Next specification:** `SPEC-003-Bidirectional-IF-and-Evidence-Impact-Contract.md`

## Abstract

This specification defines an interoperable contract for **Universal Typing and Naming (UTN)** and **Compositional Identity Intelligence** in adversarial structural security systems. The core premise is that a controller of an account, signing service, workflow, or other resource may be an individual, a team, a subgroup, a coalition, a shared service, or a time-varying composition of these. Address equality, behavioral similarity, control of a cryptographic key, and verified real-world identity are different assertions. A security system must not silently collapse them into one identity claim.

SPEC-002 provides typed identity and relation units, scoped naming, temporal membership and control edges, hypergraph semantics, competing hypothesis portfolios, provenance and uncertainty constraints, evidence-to-identity inference boundaries, merge/split lifecycle rules, and conformance tests. It is compatible with the common Structural Security Unit (SSU) envelope in SPEC-001. Inference may support an identity hypothesis, but **must never independently grant authorization or establish legal identity**. This is a proposed research and engineering contract, not evidence that the described methods have been validated.

**Keywords:** UTN; compositional identity; temporal hypergraph; entity resolution; provenance; hypothesis-scoped contradiction; overlapping teams; on-chain attribution; SSU; authorization boundary.

---

## 1. Scope, Language, and Design Goals

### 1.1 Normative vocabulary

**MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** express requirements for a claimed conformance profile. They are proposed requirements of this research specification, not external standards. Implementations MUST state their conformance profile and known deviations.

### 1.2 Scope

This contract covers:

1. Type-safe names and identifiers for observed objects, inferred entities, and verified principals.
2. Compositions of persons, services, accounts, teams, and organizations, including overlap and time variation.
3. Role-, action-, resource-, and interval-scoped relations of membership, operation, delegation, and control.
4. Competing identity hypotheses, evidence lineage, uncertainty, contradiction, and revisions.
5. Safe interaction with REN evidence navigation, BCEF tests, scoring structures, and independent authorization.
6. Synthetic sandbox benchmarks and machine-checkable conformance tests.

It does **not** specify an identity-proofing provider, cryptographic signature scheme, graph database, production trust policy, or universal probabilistic attribution model. It does not assert that a blockchain address identifies a natural person.

### 1.3 Objectives and non-objectives

The principal objectives are to prevent category confusion, false merges, false splits, temporal leakage, evidence laundering, and privilege escalation through identity inference. The contract aims for explicit semantics and reversible, auditable hypothesis evolution. It does not aim to infer every hidden controller, force a unique identity resolution, or eliminate uncertainty. A portfolio of unresolved hypotheses is a valid result.

---

## 2. Conceptual Identity Layers

An ASSI implementation MUST distinguish the following layers even when their display labels look similar.

| Layer | Meaning | Typical evidence | What it does not prove |
|---|---|---|---|
| L0 — Observed object | Directly recorded address, key, transaction, process, account, or endpoint | Signed event, ledger record, authenticated log | Human identity or ultimate control |
| L1 — Structural actor | A behaviorally or operationally inferred actor grouping | Timing, funding flow, service telemetry | A unique individual or organization |
| L2 — Compositional entity | A modeled set of members, roles, and coordination relations | Membership and control evidence | Stable composition across all times |
| L3 — Verified principal | Identity attested by an independently specified process | Identity proofing and credential records | Unbounded authorization |
| L4 — Authorized principal-in-context | Principal satisfying an independent policy for a specific action | Valid credential plus authorization decision | Permission outside that context |

**Invariant:** no inference-only transition from L0–L2 to L3 or L4 is permitted. A verified principal may be linked to an inferred actor only through a separately identified and auditable binding claim. L4 is a policy outcome, not an intrinsic property of the name.

A single L0 object may be associated with multiple candidate L1 actors. A single L1 actor may participate in several L2 compositions. The model MUST NOT require one-to-one mappings.

---

## 3. Canonical UTN Namespace and Type System

### 3.1 UTN name structure

A proposed canonical name is:

```text
utn:<authority>/<domain>/<kind>/<local-id>@<revision>
```

Example:

```text
utn:lab-alpha/chain-test/address/a-0042@1
utn:lab-alpha/identity/hypothesis/h-team-17@3
utn:lab-alpha/operations/composition/ops-coalition-2@5
```

The grammar is illustrative; implementations MAY use an equivalent structured encoding if the semantic fields are preserved. A UTN name is a **typed reference**, not proof of the named entity's existence or identity. Names MUST include a namespace authority and kind; names MUST NOT be treated as globally unique absent a documented namespace-governance mechanism.

### 3.2 Required name fields

| Field | Requirement | Semantics |
|---|---|---|
| `namespace_authority` | MUST | Issuer and governance domain for the name |
| `domain` | MUST | Application or evidence domain |
| `kind` | MUST | Explicit type, e.g., `address`, `actor_hypothesis`, `team`, `service` |
| `local_id` | MUST | Opaque stable identifier within authority and kind |
| `revision` | MUST | Immutable name-record revision |
| `display_label` | MAY | Human-readable label; never a matching key by itself |
| `resolution_policy` | MUST | How the record is resolved and whose authority applies |
| `alias_of` | MAY | Explicitly scoped alias relation, not implicit equality |

### 3.3 Identifier separation

`object_id`, `entity_hypothesis_id`, `principal_id`, `composition_id`, and `authorization_subject_id` MUST be distinct typed fields. Their lexical strings MAY coincide, but software MUST NOT interpret coincident strings as equality across types. An address or public key MUST NOT be cast into `principal_id` by string conversion.

### 3.4 Aliases and namespace collisions

Aliases MUST specify issuing authority, valid interval, evidence, and the type of equivalence asserted: exact same object, same service instance, possible common controller, or verified binding. A resolver MUST reject an alias cycle that silently changes the asserted equivalence type. Conflicting authorities MAY publish different hypotheses; the consumer MUST retain the authority and scope rather than pick a winner by display name.

---

## 4. Canonical Compositional Identity Model

### 4.1 Typed temporal hypergraph

Define an identity model at time `t` and context `c` as:

\[
G_{t,c}=(V,E,\mathcal H,\tau,\pi),
\]

where `V` contains typed objects and candidate entities; `E` contains typed binary relations; `\mathcal H` contains n-ary composition or coordination relations; `\tau` carries event, observation, and validity times; and `\pi` carries provenance, scope, and epistemic state. A hyperedge may represent joint authorization by three signers, a rotating team, or a shared operational service. A graph-only implementation MAY reify hyperedges as typed relation nodes, provided membership, role, and time semantics are preserved.

### 4.2 Composition semantics

A composition is not automatically a set-theoretic union of stable identities. It MUST define:

- A `composition_kind`: `team`, `subgroup`, `coalition`, `shared_service`, `workflow`, or extension type.
- A `membership_policy`: explicit, inferred, rotating, conditional, or externally verified.
- A `control_semantics`: unilateral, threshold, delegated, coordinated, observed-only, or unknown.
- A `valid_interval` and a `scope` of resources/actions.
- The source and epistemic status of each member or role relation.

Membership does not imply control. Control does not imply legal ownership. Shared infrastructure does not imply common human control. A composition MUST support overlapping membership and nested compositions without requiring a unique parent.

### 4.3 Identity hypothesis portfolio

For observed activity involving addresses A, B, and C, a portfolio might retain:

- `H-person`: one person controls all three addresses.
- `H-team`: distinct people within one coordinated team control them.
- `H-service`: unrelated clients share a service that produces similar transaction patterns.
- `H-trigger`: independent actors respond to a common external event.

These hypotheses may be mutually exclusive, partially overlapping, or hierarchically related. The portfolio MUST declare those relationships; it MUST NOT assume that all candidates form a complete probability partition. A contradiction of `H-person` MUST NOT automatically refute `H-team` or `H-service`.

---

## 5. SSU Compatibility and Domain Payloads

SPEC-002 units MUST use the common SSU envelope of SPEC-001. The following fields describe a **domain payload**, not a replacement for the envelope. In the examples, `ssu_id`, `ssu_type`, `schema_version`, `epistemic_status`, `provenance`, `event_time`, `observed_at`, `valid_time`, and `revision` represent common-envelope concepts; a conforming implementation MUST follow the authoritative field spelling and validation rules of SPEC-001.

### 5.1 Identity hypothesis payload

```yaml
identity_hypothesis:
  hypothesis_id: "utn:lab-alpha/identity/hypothesis/h-team-17@3"
  hypothesis_kind: "common_team_control"
  subject_refs:
    - "utn:lab-alpha/chain-test/address/a-0042@1"
    - "utn:lab-alpha/chain-test/address/a-0043@1"
  claimed_relation: "coordinated_by_same_team"
  scope:
    resources: ["synthetic-wallet-cluster-7"]
    actions: ["test-transfer"]
    domain: "synthetic-chain"
  valid_time:
    start: "2026-10-01T00:00:00Z"
    end: "2026-10-07T00:00:00Z"
  epistemic_status: "hypothesized"
  support_evidence_refs: ["ssu:obs-101", "ssu:obs-108"]
  counter_evidence_refs: ["ssu:obs-119"]
  dependency_group_refs: ["dep:timing-pattern-4"]
  alternative_hypothesis_refs: ["hyp:shared-service-9"]
  scoring_ref: "ssu:score-27"
  decision_authority: "none"
```

The `decision_authority: none` field is explanatory defense in depth. The record's lack of authority is enforced by the independent authorization system, not merely by trusting this field.

### 5.2 Composition and membership payload

```yaml
composition:
  composition_id: "utn:lab-alpha/operations/composition/rotation-team-2@2"
  composition_kind: "team"
  membership_policy: "rotating_inferred"
  members:
    - member_ref: "utn:lab-alpha/operations/actor/operator-a@1"
      role: "initiator"
      relation_status: "supported"
      valid_from: "2026-10-01T00:00:00Z"
      valid_until: "2026-10-04T00:00:00Z"
      evidence_refs: ["ssu:obs-201"]
    - member_ref: "utn:lab-alpha/operations/actor/operator-b@1"
      role: "approver"
      relation_status: "hypothesized"
      valid_from: "2026-10-03T00:00:00Z"
      valid_until: null
      evidence_refs: ["ssu:obs-202"]
  control_semantics: "threshold_or_coordinated_unknown"
  controlled_resource_refs: ["resource:synthetic-wallet-7"]
  competing_explanations: ["hyp:shared-automation-service"]
  authorization_effect: "none"
```

A composition's membership records MUST carry their own validity intervals; the composition's overall interval does not imply that every member was present throughout.

### 5.3 Typed relation payload

```yaml
relation:
  relation_id: "ssu:relation-301"
  relation_type: "operates"
  source_ref: "utn:lab-alpha/operations/actor/operator-a@1"
  target_ref: "utn:lab-alpha/chain-test/address/a-0042@1"
  scope: {action: "synthetic-sign", resource: "wallet-7"}
  valid_time: {start: "2026-10-02T10:00:00Z", end: null}
  epistemic_status: "derived"
  evidence_refs: ["ssu:obs-301", "ssu:obs-302"]
  dependency_group_refs: ["dep:session-301"]
  alternative_relation_refs: ["ssu:relation-302"]
```

### 5.4 Field semantics

`null` interval end means *not established*, not infinite verified validity. Missing evidence references are not negative evidence. `supported` is not `verified`. A scoring reference is an advisory assessment whose calibration and dependency handling must be specified separately. Cross-reference resolution MUST preserve type, issuer, version, and trust boundaries.

---

## 6. Temporal Semantics and Identity Continuity

### 6.1 Four clocks

An identity record SHOULD preserve:

1. **Event time:** when the underlying event occurred.
2. **Observation time:** when the system recorded the event.
3. **Assessment time:** when an identity claim was inferred or revised.
4. **Validity time:** when the asserted relation is claimed to hold.

Backdated evidence MUST NOT be treated as if it was available to a historical decision maker. Benchmark replay MUST use an explicit information cutoff to prevent future-data leakage.

### 6.2 Rotating membership

When an operator leaves a team, the team name MAY persist while membership and authorization change. Conversely, identical members at two times do not guarantee unchanged roles or control thresholds. Identity continuity SHOULD be represented as a distinct claim with evidence, not inferred solely from a stable label.

### 6.3 Temporal conflict

Two conflicting relation claims can coexist when issued by different authorities, inferred under different assumptions, or valid in different intervals. A resolver MUST preserve the disagreement. It MUST NOT erase the earlier claim through an in-place overwrite.

---

## 7. Evidence Provenance and Inference Boundaries

### 7.1 Evidence classes

- `direct_observation`: authenticated logs, ledger events, or controlled experiment observations.
- `derived_feature`: timing similarity, flow statistics, address clustering, or graph features.
- `external_attestation`: assertions from an identified authority, with its scope and verification procedure.
- `analyst_hypothesis`: a proposed interpretation.
- `verified_binding`: an independently evaluated identity linkage under a declared proofing policy.

The same underlying event may produce many derived features. The system MUST retain their shared dependency lineage so they cannot be counted as independent corroboration.

### 7.2 Attribution limits

An observed transfer from address A establishes an event involving that address under the ledger's rules. It does not, without additional evidence, establish who chose the transfer, who controlled the key, whether control was delegated, or whether the controller had legitimate authority. This distinction applies equally to API keys, cloud accounts, and AI-agent tool credentials.

### 7.3 REN integration

REN may prioritize directional weak evidence for a specific hypothesis and decision context. A REN score MUST specify the target hypothesis, direction, context, feature sources, and dependency assumptions. Similarity between two addresses is not equivalent to common human identity. Evidence ranking MAY guide exploration; it MUST NOT become an identity-proofing shortcut.

### 7.4 BCEF integration

BCEF tests MUST declare which identity claim they test and what would count as support, refutation, unknown, or conflict. Reverse IF reasoning MUST NOT treat the converse of a conditional as logically established. Counterfactual tests MUST record intervention assumptions and observability limits. BCEF Impact records MAY recommend hypothesis revision, splitting, merging, or additional evidence collection; such recommendations are not self-executing authoritative identity changes.

---

## 8. Hypothesis-Scoped Contradiction Contract

### 8.1 Principle

**Contradiction Must Be Hypothesis-Scoped.** A test can invalidate the claim that one person directly performed two simultaneous operations without invalidating a team, automation, delegation, or shared-service explanation.

### 8.2 Required contradiction record

```yaml
contradiction:
  test_id: "bcef:test-71"
  target_hypothesis_ref: "hyp:single-human-controller"
  tested_predicate: "same_person_performed_both_actions"
  assumptions:
    - "both events require contemporaneous manual interaction"
    - "timestamps are sufficiently synchronized"
  observed_result: "incompatible_under_assumptions"
  impact:
    target_status: "contested"
    scope: "single-human-controller-only"
    unaffected_hypotheses:
      - "hyp:coordinated-team"
      - "hyp:shared-service"
    recommended_action: "reassess"
  evidence_refs: ["ssu:event-71", "ssu:event-72"]
  independent_validation: "pending"
```

### 8.3 Propagation rules

Contradiction MAY propagate to another hypothesis only through a separately documented logical dependency. A child hypothesis is not automatically disproven because a parent is contested unless the child logically entails the disproven predicate. The inference engine MUST expose the propagation justification and dependency graph.

### 8.4 Unknown and conflicting evidence

The contract SHOULD support at least four evidence outcomes: `supports`, `refutes`, `unknown`, and `conflicting`. An absence of telemetry is ordinarily `unknown`, not `refutes`. Conflicting evidence MUST be retained with provenance until reconciled or explicitly bracketed.

---

## 9. Merge, Split, and Recomposition Lifecycle

### 9.1 Candidate merge

A candidate merge proposes that two references describe the same entity **under a specified equivalence relation**. It MUST identify source nodes, relation type, temporal scope, supporting and counter-evidence, and expected effects on dependent claims. The system MUST NOT merge merely because two objects share a device, IP address, transaction counterparty, or behavioral cluster.

### 9.2 Candidate split

A split may be required when a previous cluster contains distinct operators or changes composition over time. A split MUST preserve historical aliases and decision lineage. Past decisions MUST remain reproducible against the identity graph version used at the time.

### 9.3 Recomposition

A recomposition changes membership, roles, or control semantics without necessarily declaring a prior entity invalid. This is preferable to repeated destructive merge/split operations for rotating teams. A recomposition MUST create a new revision or event and state its effective interval.

### 9.4 Proposed lifecycle

```text
observed objects
    -> candidate actor links
    -> competing identity hypotheses
    -> evidence and BCEF tests
    -> proposed merge / split / recomposition
    -> independent evaluation
    -> append-only accepted revision OR rejected proposal
    -> updated hypothesis portfolio and audit trail
```

Acceptance of a revised **analytical identity graph** does not confer permission to execute an action. Any change to authorization bindings requires a separate, authorized governance process.

---

## 10. Identity-to-Authorization Boundary

### 10.1 Non-escalation invariant

An inferred identity relation MUST NOT automatically create, expand, or transfer permissions. In particular:

- `same_cluster` MUST NOT imply `same_principal`.
- `same_principal` MUST NOT imply `same_role`.
- `same_role` MUST NOT imply `authorized_for_action`.
- `authorized_for_action` MUST NOT imply authorization at another time, resource, or risk level.

### 10.2 Independent binding

A consequential authorization decision MUST be evaluated by the independent safety control plane specified in SPEC-004. It MUST use a trusted principal binding, action/resource scope, current policy, exposure limits, and relevant approvals. The analytical UTN graph MAY provide advisory signals or risk flags, but MUST NOT override non-bypassable limits.

### 10.3 Compromise scenarios

A valid signature can be produced by a compromised service, an authorized signer acting outside intended workflow, or an automated delegate. Therefore, key possession is neither a sufficient identity proof nor a sufficient business-authorization proof. An ASSI implementation SHOULD model credential, operator, service, principal, and policy as distinct typed objects.

---

## 11. Privacy, Minimization, and Governance

Identity correlation can expose sensitive associations even when individual source events are public. Implementations MUST establish a lawful and authorized purpose for collection and correlation, limit retention, restrict analyst access, and document permissible disclosure. They SHOULD minimize raw personal data and use pseudonymous references where possible.

The system MUST preserve the distinction between **observed association** and **accusation of wrongdoing**. Low-confidence or contested attribution MUST NOT be presented as verified identity. Human review, correction, and challenge procedures SHOULD be available for consequential use. Immutable audit records MAY contain protected references or cryptographic commitments rather than unrestricted personal details.

A UTN namespace authority MUST NOT be assumed to be a legal or institutional identity authority unless that role has been separately established.

---

## 12. Threat Model and Failure Modes

| Threat | Mechanism | Required defense |
|---|---|---|
| False merge | Shared service makes unrelated actors appear identical | Alternative hypotheses; dependence-aware evidence; split tests |
| False split | Rotating team appears to be unrelated identities | Temporal compositions and continuity claims |
| Sybil behavior | One actor operates many addresses | Do not equate address count with person count |
| Evidence laundering | Multiple features derived from one event appear independent | Provenance dependency groups |
| Timestamp manipulation | False simultaneity or sequence | Clock provenance and uncertainty intervals |
| Alias collision | Two authorities reuse a local identifier | Typed, authority-scoped UTN names |
| Graph poisoning | Adversary injects misleading relations | Source trust, quarantine, independent validation |
| Authority confusion | Identity score used as permission | Independent control plane and non-escalation checks |
| Historical leakage | Future evidence contaminates replay | Explicit information cutoff |
| Unbounded correlation | Excessive deanonymization | Purpose limits, minimization, review |

A compliant implementation SHOULD test adversarially selected shared infrastructure, intentional mimicry, coordinated behavior, and deliberately ambiguous identity evidence. The system MUST support a safe `unresolved` result.

---

## 13. Conformance Invariants

The following proposed invariants are normative for the `ASSI-UTN-CI-v0.1` profile.

**CI-01 — Typed identity.** Every identity reference MUST carry a type and namespace authority.

**CI-02 — No lexical equality shortcut.** Equal identifier strings across types MUST NOT imply equal entities.

**CI-03 — Distinct epistemic layers.** Observed, inferred, attested, verified, and authorized states MUST remain distinguishable.

**CI-04 — Composition plurality.** The model MUST permit overlapping, nested, and time-varying compositions.

**CI-05 — Role specificity.** Membership MUST NOT automatically imply control, ownership, or authorization.

**CI-06 — Temporal validity.** Material identity relations MUST declare a validity interval or explicitly mark it unknown.

**CI-07 — Provenance.** Every inferred relation MUST cite evidence or explicitly state that it is an unsupported proposal.

**CI-08 — Dependency accounting.** Derived features from common evidence MUST be linked for dependence-aware evaluation.

**CI-09 — Alternative retention.** Competing plausible hypotheses MUST NOT be silently discarded by a single score threshold.

**CI-10 — Hypothesis-scoped contradiction.** A negative test MUST affect only hypotheses logically covered by the test.

**CI-11 — No converse fallacy.** Reverse IF tests MUST NOT assume `E implies H` merely because `H implies E`.

**CI-12 — Missing is not false.** Missing observation MUST NOT be treated as negative evidence without a validated detection model.

**CI-13 — Append-only revision.** Accepted merge/split/recomposition changes MUST preserve prior states and provenance.

**CI-14 — Reproducible replay.** Historical decisions MUST identify the graph and evidence snapshot used.

**CI-15 — Authority non-transfer.** Identity inference MUST NOT grant or enlarge authorization.

**CI-16 — Verification boundary.** An L0–L2 record MUST NOT be relabeled as verified principal without independently documented binding evidence.

**CI-17 — Namespace governance.** Resolution MUST preserve issuer and kind, including across aliases.

**CI-18 — Conflict preservation.** Contradictory observations MUST remain inspectable rather than being overwritten by a preferred interpretation.

**CI-19 — Safe uncertainty.** The resolver MUST support unknown, contested, and unresolved outputs.

**CI-20 — Privacy governance.** Correlation and retention MUST be governed by explicit purpose and access rules.

**CI-21 — Cross-domain semantic mapping.** Transfers between identity domains MUST declare mapping assumptions and validation evidence.

**CI-22 — Independent consequential decisions.** Authorization, sanctions, or other consequential actions MUST use a separate accountable decision process.

---

## 14. Conformance Profiles

| Profile | Required capabilities | Intended use |
|---|---|---|
| `UTN-Core` | CI-01, CI-02, CI-03, CI-06, CI-07, CI-17, CI-19 | Typed naming and traceable references |
| `CI-Analytical` | `UTN-Core` plus CI-04, CI-05, CI-08–CI-14, CI-18 | Hypothesis-driven identity analysis |
| `CI-Security` | `CI-Analytical` plus CI-15, CI-16, CI-20–CI-22 | Security decision support under independent controls |

These profiles are proposals. An implementation claiming `CI-Security` MUST document its independent authorization integration and demonstrate negative tests against inference-based privilege escalation. Passing schema tests alone is insufficient.

---

## 15. Conformance Test Vectors

The table lists expected outcomes for an implementation claiming `CI-Security`.

| ID | Input condition | Expected result | Invariants |
|---|---|---|---|
| T01 | Two typed names with same local ID but different authority | Distinct references | CI-01, CI-17 |
| T02 | Address ID used as verified principal without binding | Reject verification transition | CI-02, CI-16 |
| T03 | Two operators belong to overlapping teams | Accept both relations | CI-04 |
| T04 | Membership evidence but no control evidence | Do not infer control | CI-05 |
| T05 | Relation without time interval or unknown marker | Reject as incomplete | CI-06 |
| T06 | Two derived timing features from same transaction | Mark dependency, prevent independent double count | CI-08 |
| T07 | Simultaneous manual actions contradict single-person hypothesis | Contest only single-person claim | CI-10 |
| T08 | Same evidence supports team or shared-service hypothesis | Retain alternatives | CI-09 |
| T09 | `H -> E` observed E, reverse inference attempted | Do not assert H without alternative analysis | CI-11 |
| T10 | Telemetry absent during outage | Mark unknown unless detection assumptions justified | CI-12 |
| T11 | Identity cluster split | Preserve previous graph version and lineage | CI-13, CI-14 |
| T12 | High identity confidence requests asset transfer | No authorization without independent policy | CI-15, CI-22 |
| T13 | Conflicting sources assert different operators | Preserve both claims and provenance | CI-18 |
| T14 | Shared automation service induces false clustering | Require alternative explanation and uncertainty | CI-09, CI-19 |
| T15 | Historical replay includes future-observed evidence | Reject leakage | CI-14 |
| T16 | Cross-domain alias lacks equivalence semantics | Reject mapping | CI-17, CI-21 |
| T17 | Personal-data correlation without purpose/access policy | Reject `CI-Security` conformance | CI-20 |
| T18 | Team member removed while team persists | Create time-scoped recomposition | CI-04, CI-06, CI-13 |
| T19 | Contradiction applies only under disputed timestamp assumptions | Record conditional/contested outcome | CI-10, CI-18, CI-19 |
| T20 | Unverified inferred identity used to issue credential | Deny and audit | CI-15, CI-16, CI-22 |

### 15.1 Test fixture design

A test fixture MUST provide synthetic ground truth, event and observation times, allowed information cutoff, evidence-dependency groups, identity-hypothesis alternatives, and expected output semantics. The fixture SHOULD include deliberate label ambiguity and counterexamples. Ground truth MUST be withheld from the inference engine during evaluation.

### 15.2 Example negative test

```yaml
vector_id: "T12"
profile: "CI-Security"
input:
  inferred_identity:
    kind: "actor_hypothesis"
    score: 0.98
    verified_principal_binding: null
  requested_action:
    kind: "transfer"
    asset_ref: "synthetic-asset-7"
    amount: 100
expected:
  identity_analysis: "advisory_only"
  authorization: "deny_or_require_independent_authorization"
  audit_required: true
  must_not:
    - "promote_actor_hypothesis_to_verified_principal"
    - "bypass_authorization_control_plane"
```

The numerical score is illustrative and is not a calibrated probability. A real authorization result may depend on independently established credentials and policy; the key invariant is that inference score alone cannot authorize.

---

## 16. Reference Validation Algorithm

```text
function validate_compositional_identity(ssu, registry, policy):
    require validate_SPEC_001_envelope(ssu)
    require ssu.payload_kind in ALLOWED_IDENTITY_KINDS
    require typed_and_authority_scoped(ssu.references)
    require no_implicit_cross_type_equality(ssu.references)
    require valid_temporal_fields(ssu)
    require provenance_present_or_explicitly_unsupported(ssu)

    if ssu.kind == "composition":
        require explicit_membership_and_control_semantics(ssu)
        require time_scoped_member_relations(ssu)
        allow_overlap_and_nesting(ssu)

    if ssu.kind == "identity_hypothesis":
        require explicit_predicate_and_scope(ssu)
        require dependencies_and_alternatives_recorded(ssu)
        require status_is_not_implicitly_verified(ssu)

    if ssu.kind == "contradiction_impact":
        require target_hypothesis_and_test_assumptions(ssu)
        require impact_scope_subset_of_logical_entailment(ssu)
        require no_automatic_global_refutation(ssu)

    if ssu.kind in ["merge", "split", "recomposition"]:
        require immutable_revision_and_history(ssu)
        require auditable_proposal_and_review(ssu)

    if requests_authority_change(ssu):
        reject("identity graph cannot self-authorize")

    return VALID_WITH_DECLARED_EPISTEMIC_LIMITS
```

This pseudocode is intentionally conservative. Implementations must define formal schemas, graph consistency rules, authorization integration, and error codes before claiming executable conformance.

---

## 17. Benchmark Laboratory: UTN On-Chain Identity Sandbox

### 17.1 Research question

Can a typed temporal compositional model reduce false identity merges and splits, relative to flat address clustering, without introducing unacceptable latency, complexity, or privacy costs?

### 17.2 Synthetic scenarios

**S1 — One operator, many addresses.** A single simulated operator rotates through keys and addresses. Evaluate missed continuity and false splits.

**S2 — One team, multiple operators.** Several operators coordinate with different roles and overlapping shifts. Evaluate whether the system distinguishes team continuity from single-person identity.

**S3 — Shared service.** Independent clients use the same signing or transaction relay service. Evaluate false merges caused by infrastructure similarity.

**S4 — Rotating coalition.** A temporary coalition shares access for a limited period, then dissolves. Evaluate temporal precision and recomposition handling.

**S5 — Mimicry and poisoning.** A simulated adversary imitates timing and transaction patterns or injects misleading aliases. Evaluate robustness and uncertainty reporting.

**S6 — Contradiction under uncertain clocks.** Events appear simultaneous but timestamp uncertainty overlaps. Evaluate whether the system avoids unjustified refutation.

**S7 — Delegation and compromise.** A valid signature is produced by a delegated or compromised service. Evaluate separation of key possession, operator inference, and legitimate authorization.

### 17.3 Baselines

- B0: address-equals-actor naive identity.
- B1: static graph connected components.
- B2: similarity-threshold clustering.
- B3: temporal graph without explicit compositions.
- B4: temporal compositional model without hypothesis portfolios.
- B5: full UTN + compositional model with provenance and BCEF scope rules.

### 17.4 Metrics

Evaluate pairwise false-merge rate, false-split rate, team-membership precision/recall, temporal relation accuracy, calibration or selective-risk curves where valid, unresolved-case rate, provenance completeness, contradiction-scope error rate, replay reproducibility, runtime/memory cost, and privacy exposure. Report per-scenario results and confidence intervals, not only aggregate accuracy. Identity-level and team-level metrics MUST be separated.

### 17.5 Evaluation protocol

Pre-register the hypothesis, datasets, information cutoff, metrics, and decision thresholds. Partition synthetic entities and behavioral patterns between training and held-out tests to avoid leakage. Use independently generated scenarios and adversarial perturbations. Report cases where the more complex model performs worse. All security-impacting experiments MUST use authorized synthetic or otherwise permitted data.

---

## 18. Falsifiable Hypotheses

**H-CI-01 — Typed naming reduces category errors.** Against B0, UTN type enforcement lowers erroneous promotion of addresses into verified principals. **Falsified if** negative tests show no meaningful reduction or new collision classes dominate.

**H-CI-02 — Composition improves team-level attribution.** Against B1/B2, time-varying compositions reduce false splits in rotating teams at comparable false-merge rates. **Falsified if** no held-out improvement appears.

**H-CI-03 — Alternative portfolios reduce false merges.** Explicit shared-service hypotheses reduce false merges relative to a single-winner cluster model. **Falsified if** gains vanish under blinded shared-service tests.

**H-CI-04 — Hypothesis-scoped contradiction reduces over-rejection.** BCEF scope constraints prevent rejection of viable team explanations after a single-person contradiction. **Falsified if** scope errors are unchanged or increase.

**H-CI-05 — Provenance dependence prevents confidence inflation.** Dependency-aware scoring improves calibration or selective risk when many features share an event source. **Falsified if** no improvement occurs on controlled correlated-evidence fixtures.

**H-CI-06 — Temporal validity improves replay fidelity.** Four-clock modeling reduces historical attribution errors relative to a current-state-only graph. **Falsified if** it does not improve held-out temporal replay.

**H-CI-07 — Non-escalation is enforceable.** Inference-only identity updates cannot change authorization outcomes without independent policy events. **Falsified if** any test path promotes analytical identity into permission.

**H-CI-08 — Compositional modeling has an acceptable cost envelope.** Improvements in error rates justify measured computation and operational overhead for at least one target workload. **Falsified if** resource costs exceed pre-registered limits without adequate benefit.

**H-CI-09 — Cross-domain transfer requires semantic adapters.** A typed adapter outperforms naive name reuse across chain, cloud, and agent domains on semantic consistency tests. **Falsified if** it adds no measurable consistency or creates more mismappings.

These are proposals, not established empirical findings.

---

## 19. Interoperability with Other ASSI Specifications

| Contract | Relationship to SPEC-002 | Boundary |
|---|---|---|
| SPEC-001 — SSU | Common envelope, provenance, time, lifecycle | Domain payload MUST not weaken base invariants |
| SPEC-003 — BCEF | Scoped IF tests and structured identity-impact feedback | Test results do not imply global identity truth |
| SPEC-004 — Authorization | Principal binding, independent policy, bounded exposure | Analytical identity cannot self-grant permissions |
| SPEC-005 — Drives | Synthetic adversarial identity scenarios and relay | Simulated attacks stay within authorized sandboxes |
| SPEC-006 — Validated RSI | Governed revisions to identity models and tests | Model promotion requires independent validation |

An SSU consumer MUST reject or quarantine references whose version, type, issuer, or policy context cannot be resolved. A system MAY provide human-readable best-effort display, but MUST NOT use such fallback resolution for consequential decisions.

---

## 20. Implementation Roadmap

**Phase 0 — Contracts first.** Freeze the normative vocabulary, payload schemas, namespace governance, and negative tests. Resolve all field-level dependencies on SPEC-001.

**Phase 1 — Typed registry.** Implement UTN creation, resolution, alias checks, versioning, and type-safe APIs. Test collisions and cross-type conversion failures.

**Phase 2 — Temporal compositions.** Implement relation nodes/hyperedges, membership intervals, control semantics, and append-only recomposition.

**Phase 3 — Hypothesis portfolio.** Add competing explanations, evidence dependency lineage, uncertainty outcomes, and scope-aware BCEF integration.

**Phase 4 — Sandbox benchmark.** Evaluate against static clustering, temporal graphs, and ablated portfolio models on held-out synthetic scenarios.

**Phase 5 — Security integration.** Demonstrate that all analytical identity updates are advisory and cannot bypass independent authorization. Conduct negative conformance and privacy review.

**Phase 6 — Governed transfer.** Pilot a second domain using explicit semantic adapters, independent review, and rollback mechanisms. Publish limitations and failed hypotheses.

No phase implies permission for production deployment. Deployment requires separate threat modeling, security assessment, legal/privacy review, and operational governance.

---

## 21. Open Questions

1. Which composition primitives are minimal yet expressive enough for teams, coalitions, delegated services, and autonomous agents?
2. How should the model represent uncertain control thresholds without inventing precise probabilities?
3. When should an identity hypothesis be split versus represented as a time-varying composition?
4. Can dependency-aware weak evidence remain computationally efficient in large streaming graphs?
5. What are the limits of cross-chain, cross-cloud, and cross-agent UTN semantics?
6. How can privacy-preserving provenance support meaningful independent audit?
7. What constitutes sufficient independent evidence to bind an inferred actor to a verified principal?
8. How should contradictory attestations from authorities with different mandates be handled?
9. Which benchmark designs best detect graph poisoning and deceptive behavioral mimicry?
10. Can hypothesis portfolios remain interpretable under recursive structural relay without collapsing into unreviewable complexity?

---

## 22. Conclusion

Compositional identity is a security-relevant structure, not merely a clustering result. A cryptographic address, a service account, a behavioral actor, a rotating team, and a verified principal may be related without being interchangeable. UTN provides a typed naming foundation; temporal graph and hypergraph relations express composition; evidence provenance and alternative hypotheses constrain attribution; and hypothesis-scoped BCEF tests prevent local contradictions from becoming global rejections. The contract's most important boundary is independent of any particular scoring algorithm: **inferred identity is not authorization**.

The proposed contract should be judged by conformance tests, falsifiable identity benchmarks, adversarial evaluation, and operational cost—not by architectural elegance alone. A safe unresolved answer is preferable to an unsupported identity assertion that propagates into security action.

---

## Appendix A — Canonical Entity and Relation Types (Proposed Registry)

| Type | Description | Typical allowed relations |
|---|---|---|
| `address` | Ledger or network address | `emits_event`, `receives_asset` |
| `key` | Cryptographic key reference | `signs`, `bound_to_credential` |
| `credential` | Credential issued by authority | `issued_to`, `authenticates` |
| `service` | Automated or managed service | `operates`, `delegated_by` |
| `actor_hypothesis` | Inferred actor grouping | `possibly_controls`, `correlates_with` |
| `person_principal` | Independently verified natural-person principal | `member_of`, `assigned_role` |
| `organization_principal` | Independently verified organization principal | `owns_resource`, `delegates_to` |
| `team` | Time-varying operational composition | `has_member`, `coordinates` |
| `coalition` | Context-specific composition across teams | `participates_in`, `coordinates` |
| `resource` | Protected object or asset | `controlled_by`, `subject_to_policy` |
| `role` | Context-bound capability grouping | `assigned_to`, `permits_action` |
| `identity_hypothesis` | Testable claim over entities/relations | `supported_by`, `contested_by` |

The registry is extensible only through documented type semantics, issuer governance, and conformance tests.

## Appendix B — Minimal API Sketch

```text
register_name(name_record) -> versioned_name_ref | error
resolve_name(typed_ref, at_time, authority_policy) -> record | unresolved
assert_relation(relation_ssu) -> proposal_ref | error
create_hypothesis(hypothesis_ssu) -> hypothesis_ref | error
record_evidence(hypothesis_ref, evidence_refs) -> assessment_proposal
apply_bcef_impact(impact_ssu) -> scoped_revision_proposal
propose_recomposition(composition_ref, delta) -> revision_proposal
review_revision(proposal_ref, independent_review) -> accepted_revision | rejected
replay_graph(snapshot_ref, information_cutoff) -> historical_graph
```

No API listed above may independently issue credentials, grant permissions, or bypass an authorization control plane.

## Appendix C — Release and Conformance Checklist

- [ ] SPEC-001 envelope and SPEC-002 payload schemas agree on required fields.
- [ ] Names include authority, kind, and immutable revision.
- [ ] Type confusion and alias-collision tests pass.
- [ ] Membership, control, and verification are distinct relations.
- [ ] Overlapping and rotating teams are representable.
- [ ] All material relations have time and provenance semantics.
- [ ] Competing hypotheses and unresolved outputs are supported.
- [ ] Contradiction impacts remain hypothesis-scoped.
- [ ] Evidence dependency groups prevent unsupported double counting.
- [ ] Merge/split/recomposition preserves historical replay.
- [ ] Identity inference cannot promote itself to authorization.
- [ ] Privacy, access, and retention policies are documented.
- [ ] Synthetic benchmark fixtures and negative vectors are reproducible.
- [ ] Security limitations and unvalidated claims are explicitly disclosed.

---

**Repository placement:** `specs/SPEC-002-Compositional-Identity-and-UTN-Contract.md`  
**Previous specification:** `specs/SPEC-001-Structural-Security-Unit-Contract.md`  
**Next specification:** `specs/SPEC-003-Bidirectional-IF-and-Evidence-Impact-Contract.md`  
**Research status:** Proposed; requires independent implementation and validation.
