# CASE-003 — Bidirectional IF and False Rejection

**Project:** Adversarial Structural Security Intelligence (ASSI)  
**Version:** v0.1.0 — Research Foundation  
**Status:** Synthetic research case, protocol proposal, and falsifiable benchmark design; no executed experiment or validated performance claim  
**Date:** 2026-11-02  
**License:** Apache-2.0  
**Repository path:** `cases/CASE-003-Bidirectional-IF-and-False-Rejection.md`  
**Related:** ASSI-004–006, ASSI-009–011; SPEC-001–003, SPEC-005–006; CASE-002

## Abstract

Security intelligence frequently encounters observations that contradict a current explanation. A naive system may translate a failed conditional test into rejection of an entire identity cluster, an entire investigation, or all hypotheses that share a related concept. This **false rejection** is especially damaging when actors are compositional: evidence that excludes one individual as the sole controller of an operation may still support a team, shared-service, or delegated-control explanation. Conversely, a system that never rejects anything becomes unfalsifiable. This case specifies a synthetic benchmark for **Bidirectional Conditional Evidence Feedback (BCEF)**: Forward IF, Reverse IF, Counterfactual IF, and Contradiction IF tests; four-valued assessments; hypothesis-scoped refutation; dependency-aware evidence; and typed Impact proposals capable of updating a scoring tree or hypothesis graph without rewriting observations. It introduces controlled examples, contracts, reference algorithms, baselines, conformance vectors, falsifiable hypotheses, and independent evaluation procedures. All actors and events are fictional. The objective is to measure whether BCEF can improve *correct rejection*, *avoid erroneous rejection*, and *preserve justified alternatives* at acceptable complexity and cost—not to assume that it does.

**Keywords:** BCEF; bidirectional IF; false rejection; hypothesis-scoped contradiction; conditional evidence; compositional identity; scoring tree; structured Impact; REN; UTN; counterfactual; conformance.

---

## 1. Research Problem and Scope

### 1.1 The failure mode

Consider a cluster of synthetic wallet addresses that appears to operate under one controller. An observed transaction occurs while the suspected person is demonstrably unable to initiate it. A flat classifier might issue `NOT SAME CONTROLLER` and split the entire cluster. That conclusion does not follow. The evidence may refute **sole control by that person**, while leaving open shared team control, delegated signing, scheduled execution, or a third-party service. Equally, some alternatives may be ruled out by additional independent evidence. The system needs a precise language for *what* was contradicted, *under which assumptions*, *over which interval*, and *with what consequences*.

False rejection here means **incorrectly discarding a hypothesis or structural relationship that remains compatible with the ground truth and admissible evidence at the evaluation time**. It is distinct from a correct rejection, a conservative unknown decision, and a false acceptance. Ground truth is available only to the benchmark evaluator, not to the inference engine.

### 1.2 Primary research question

Can typed, scoped, bidirectional conditional tests reduce false rejection of compositional identity hypotheses compared with global negative-score updates or unscoped logical rules, while maintaining useful correct-rejection power?

### 1.3 Secondary questions

1. When does a reverse conditional test add information, and when does it merely restate a forward observation?
2. Can explicit evidence-dependency tracking reduce overconfident rejection caused by duplicated signals?
3. Can structural Impact proposals improve hypothesis-portfolio quality compared with scalar score changes alone?
4. How do counterfactual tests behave when intervention assumptions are unidentifiable?
5. What accuracy, latency, storage, and governance costs accompany richer conditional reasoning?
6. How can a test result be replayed, challenged, revised, or invalidated without changing the original evidence record?

### 1.4 Exclusions

This case does not identify real people, infer ownership of actual blockchain addresses, authorize transfers, or supply a deployed threat-detection product. The synthetic evidence is not a claim about any real exchange, individual, or service. Counterfactual outputs are **model-dependent estimates**, not automatically causal conclusions. A conditional test result cannot grant or revoke operational authorization; SPEC-004 governs that boundary.

---

## 2. Conceptual Foundations

### 2.1 Four distinct layers

The benchmark preserves the following separation:

| Layer | Example | May be revised? | Authority |
|---|---|---|---|
| Observation | Synthetic transaction `tx-041` was signed by key `k-7` at event time `t` | Corrections append new records; original retained | Evidence only |
| Interpretation | `k-7` is associated with service `svc-A` | Yes, with provenance | Derived claim |
| Hypothesis | Person `P` was the sole initiator of all cluster transactions | Yes, hypothesis-scoped | Inference only |
| Decision | Escalate for human review | Yes, subject to policy | Cannot execute protected action |

**Invariant:** A negative test of a hypothesis must not retroactively erase a valid observation.

### 2.2 Conditional logic is directional

For a hypothesis `H`, a condition `C`, and expected observation `E`, the implication `H ∧ C => E` does not imply `E => H`. Nor does failure to observe `E` prove `not H` unless `C` is satisfied, `E` would have been observable, and the rule is sufficiently reliable. A practical test must therefore represent rule scope, observability, alternative causes, exceptions, and evidentiary strength.

The notation `P(E | H, C)` is meaningful only if a probabilistic model has been specified and calibrated. The proposed benchmark does not treat arbitrary similarity scores as probabilities.

### 2.3 Four-valued assessment

A hypothesis may have evidence supporting it, evidence refuting it, both, or neither:

| State | Support | Refutation | Meaning |
|---|---:|---:|---|
| `SUPPORTED` | Yes | No | Some admissible support, not necessarily proof |
| `REFUTED` | No | Yes | Some admissible refutation, scoped to tested claim |
| `CONFLICT` | Yes | Yes | Contradictory admissible signals coexist |
| `UNKNOWN` | No | No | No sufficient directional evidence |

A production implementation may retain separate continuous support and refutation magnitudes, but must not collapse `CONFLICT` into a deceptively confident scalar.

---

## 3. Synthetic Case Narrative

### 3.1 Fictional entities

- `person:Ada`: a fictional operator with access to some tasks.
- `person:Ben`: another fictional operator.
- `team:Orion`: a fictional team containing Ada and Ben during part of the experiment.
- `service:RelayS`: a fictional shared transaction-scheduling service used by several teams.
- `key:K1`, `key:K2`, `key:KS`: synthetic signing keys.
- `addr:X1`, `addr:X2`, `addr:X3`: inert ledger addresses.
- `event:E1..E8`: timestamped synthetic events.

Ground truth includes control relationships, delegation, membership changes, signing routes, and the exact origin of each generated feature. The inference engine sees only designated observations and permitted metadata.

### 3.2 Timeline

| Time | Hidden synthetic ground truth | Visible observation |
|---|---|---|
| `t0` | Ada operates `K1` for Orion | `X1` sends transaction with `K1` |
| `t1` | Ben operates `K2` for Orion | `X2` sends transaction with `K2` |
| `t2` | Orion delegates scheduled tasks to RelayS | `X1` and `X2` show correlated timing |
| `t3` | Ada is offline; RelayS executes a scheduled task | `X1` sends another transaction |
| `t4` | Orion membership changes; Ada leaves | A new signing pattern appears |
| `t5` | Another team also uses RelayS | `X3` shares timing and infrastructure |
| `t6` | Orion revokes a delegation | Subsequent Orion activity no longer uses `KS` |
| `t7` | A delayed event log arrives | Previously incomplete evidence is supplemented |

All timestamps are benchmark-relative. The scenario intentionally combines legitimate contradictions, confounders, missing data, and time-dependent relationships.

### 3.3 Competing hypotheses

- **H1:** Ada personally initiated every `X1` event during `[t0,t4)`.
- **H2:** Orion collectively controlled `X1` and `X2` during `[t0,t4)`.
- **H3:** RelayS initiated selected scheduled events on behalf of Orion.
- **H4:** `X1`, `X2`, and `X3` share a single controller.
- **H5:** Two independent teams used a common service without shared ownership.
- **H6:** All observed timing similarities are attributable to an external common trigger.

Hypotheses can overlap. `H2` and `H3` may both be true; `H4` and `H5` may be competing explanations for `X3`. The evaluation must not force a single mutually exclusive class unless the question explicitly requires one.

---

## 4. The Four BCEF Test Modes

### 4.1 Forward IF — predictive implication

**Question:** If `H1` is true under condition `C`, what observation should be expected?

Example: If Ada personally initiated a transaction, and the system records authenticated initiator actions completely, an Ada-authenticated initiation event should be present. This is a *conditional* expectation. An absent log is informative only if logging completeness, clock alignment, and authentication integrity are established.

Required outputs: tested hypothesis, preconditions, predicted evidence, observation coverage, exceptions, status, and provenance.

### 4.2 Reverse IF — diagnostic alternatives

**Question:** Given an observation, which hypotheses could produce it, and which cannot?

Example: A transaction signed by `KS` is compatible with RelayS delegation, a compromised service, or authorized shared infrastructure. It is not sufficient evidence that Ada personally initiated it. Reverse reasoning must enumerate relevant alternatives and avoid the converse fallacy.

Required outputs: observation, candidate causes, differentiating conditions, excluded explanations, and unknown alternatives.

### 4.3 Counterfactual IF — assumption-bound comparison

**Question:** Under a specified hypothetical intervention, what should change?

Example: If Orion had not delegated to RelayS at `t2`, would the `t3` transaction still have occurred? In the synthetic simulator, the generator can produce paired worlds with the same exogenous seeds and changed delegation. The resulting comparison is valid **within that generator**. It does not establish a causal effect in real organizations without additional identification assumptions.

Required outputs: intervention, fixed variables, changed variables, simulator version, predicted outcome difference, and identifiability warnings.

### 4.4 Contradiction IF — scoped refutation

**Question:** Does admissible evidence contradict the exact proposition asserted by `H`?

Example: Independent evidence that Ada did not initiate `t3` can refute the `t3` portion of `H1` if initiation and identity evidence are reliable. It does **not** refute `H2`, which permits team or delegated operation, or `H3`, which specifically predicts service execution.

Required outputs: proposition fragment, interval, assumed conditions, refuting evidence, refutation strength, and impact scope.

### 4.5 Test mode is not verdict

Any of the four test modes can return `SUPPORTED`, `REFUTED`, `CONFLICT`, or `UNKNOWN`; the mode specifies the question, not the answer. Reverse tests do not inherently validate identity. Counterfactual tests must declare their modeling assumptions. Contradiction tests must preserve hypothesis scope.

---

## 5. False Rejection Taxonomy

| Code | Error | Example | Required safeguard |
|---|---|---|---|
| FR-01 | Scope expansion | Reject Orion because Ada was offline | Hypothesis- and interval-scoped refutation |
| FR-02 | Converse fallacy | Infer sole control from matching timing | Reverse alternatives |
| FR-03 | Missing-as-negative | Treat absent logs as proof of non-action | Observability gate |
| FR-04 | Dependency inflation | Count one event log and its derived features as independent | Evidence dependency DAG |
| FR-05 | Temporal flattening | Apply a post-membership-change observation to an earlier interval | Valid-time and event-time checks |
| FR-06 | Shared-service confusion | Reject common-team hypothesis solely due to shared provider | Compositional role model |
| FR-07 | Contradictory-score collapse | Convert support plus refutation into a neutral score | Four-valued state |
| FR-08 | Counterfactual overclaim | Interpret simulator output as real causal proof | Explicit model boundary |
| FR-09 | Premature pruning | Delete alternatives before differentiating evidence arrives | Hypothesis portfolio retention |
| FR-10 | Feedback amplification | Reuse a derived IF result as independent evidence for its own parent | Cycle and lineage checks |
| FR-11 | Role conflation | Treat key possession as human identity or authorization | UTN type separation |
| FR-12 | Late evidence overwrite | Rewrite historical inference without revision record | Append-only assessment revisions |

False rejection is **not** simply the presence of a negative score. A correct, supported rejection is a desired outcome; the benchmark evaluates both erroneous and missed rejections.

---

## 6. Hypothesis-Scoped Contradiction Semantics

A contradiction record should specify a tuple:

`Contradiction = (hypothesis_id, proposition_id, subject_role, relation, valid_interval, condition_set, evidence_set, dependency_set, assessment, evaluator_version)`.

The effect of the contradiction is limited to the intersection of these scopes. If the hypothesis contains multiple propositions, the system must identify whether the contradiction refutes the conjunction, one subclaim, or an optional alternative.

### 6.1 Illustrative logic

`H1 = sole_initiator(Ada, X1, all_events, [t0,t4))`.

`E3 = independently_observed(initiation_by(RelayS, X1, t3))`.

If `E3` is reliable and the meaning of `sole_initiator` excludes delegated initiation, `E3` contradicts `H1` for the `t3` event and therefore the universal quantifier `all_events`. It does not imply `not controls(Orion, X1, [t0,t4))`. The team-control hypothesis has different quantifiers and different allowed roles.

### 6.2 Quantifier discipline

- `EVERY` is falsified by one valid counterexample within its defined domain.
- `SOME` is not falsified by a counterexample to one candidate instance.
- `ONLY` requires explicit exclusion of other permitted actors.
- `MAY` is a possibility claim; failure to observe one realization does not refute it.
- `USUALLY` is statistical and requires an agreed tolerance and observation model.

Tests must preserve these distinctions rather than flattening all propositions into a generic identity match.

### 6.3 Revision, not erasure

When a contradiction is accepted, the system may create `H1-revised` (e.g., Ada initiated some earlier events) and retain the original `H1` with status `REFUTED` and a traceable supersession edge. A previously recorded observation remains intact. If later evidence challenges the contradiction, a new assessment revision is appended.

---

## 7. Evidence Provenance, Observability, and Dependence

### 7.1 Evidence groups

Each observation has an immutable source reference, acquisition method, event time, observation time, integrity status, and dependency group. Derived features inherit upstream lineage. An authenticated event log and three machine-learned features extracted from that same log are **one underlying source family**, not four independent witnesses.

### 7.2 Observability gates

Before treating an expected-but-missing observation as refutation, the evaluator checks:

1. Was the observation mechanism operating during the relevant interval?
2. Was its coverage complete for the tested event class?
3. Were clocks and identities aligned sufficiently?
4. Could alternative channels or delegated execution bypass the observation point?
5. Was data retention or delivery delayed?
6. Is the absence independently attested or only inferred?

If these conditions are not met, the result is ordinarily `UNKNOWN`, not `REFUTED`.

### 7.3 Dependence-aware scoring

Let `G(E)` be a graph of evidence derivation and common-cause relationships. A proposed score update `ΔS(H)` must include the evidence groups and a declared aggregation rule. No universal numeric aggregation formula is mandated by this case; implementers must pre-register and calibrate their model. The benchmark reports performance under both independent and deliberately correlated evidence conditions.

### 7.4 No self-supporting loops

An IF result derived from evidence `E` cannot be reintroduced as a new independent observation that increases confidence in `E`. Any recursive inference must carry lineage and be rejected or explicitly discounted when it creates a dependency cycle.

---

## 8. Structured Impact: Beyond Scalar Scoring

A BCEF result proposes a **typed Impact** rather than directly mutating the hypothesis registry. Supported proposals include:

| Impact kind | Meaning | Example |
|---|---|---|
| `SCORE_ADJUST` | Revise evidence-conditioned assessment | Lower support for `H1` |
| `SCOPE_NARROW` | Restrict proposition or interval | Ada initiated only pre-`t2` events |
| `HYPOTHESIS_SPLIT` | Propose more precise competing variants | Personal vs delegated initiation |
| `HYPOTHESIS_MERGE` | Propose equivalence with provenance | Two redundant team variants |
| `RELATION_RETYPE` | Correct a graph-edge semantic type | `owns` → `uses_service` |
| `TEMPORAL_REVISION` | Update interval without erasing history | Membership ends at `t4` |
| `EVIDENCE_REASSESS` | Mark a source incomplete or compromised | Delayed log coverage |
| `REQUEST_EVIDENCE` | Generate differentiating observation request | Verify delegation record |
| `REQUEST_AQSI` | Formulate a falsifiable follow-up question | Which observation distinguishes H3 from H5? |
| `ESCALATE_REVIEW` | Require independent assessment | Conflicting high-impact evidence |
| `NO_CHANGE` | Record informative null effect | Test inconclusive |

### 8.1 Impact lifecycle

`PROPOSED → VALIDATED → APPROVED → APPLIED → AUDITED`, with explicit `REJECTED`, `EXPIRED`, and `ROLLED_BACK` paths. Validation checks schema, lineage, scope, graph invariants, and conflicts. Approval is a separate governance step for consequential structural changes. A failed proposal leaves the current accepted graph unchanged.

### 8.2 Scoring tree structural changes

A scoring tree may be extended with separate branches for personal initiation, team control, delegated execution, and shared infrastructure. These branches are not necessarily mutually exclusive. The tree must preserve the original question and the mapping between old and new scores, preventing a structural revision from silently changing the target variable.

### 8.3 Safety boundary

No Impact kind may directly authorize a transaction, change an independent safety policy, release an asset, or bypass SPEC-004. `ESCALATE_REVIEW` is a recommendation, not a privilege escalation.

---

## 9. Reference Contracts (Illustrative YAML)

The following is a **non-normative example**; the authoritative machine-readable schema is to be defined and tested under SPEC-001 and SPEC-003.

```yaml
schema: assi.case003.conditional_test.v0.1
unit_id: ssu:test:00041
unit_type: conditional_test
mode: CONTRADICTION_IF
hypothesis_ref: ssu:hypothesis:H1
proposition_ref: ssu:proposition:H1-sole-initiation
scope:
  subject: utn:person:Ada
  role: sole_initiator
  object: utn:address:X1
  valid_time: [t0, t4)
  event_ref: ssu:event:E3
preconditions:
  - initiation_source_is_authenticated
  - role_semantics_exclude_delegated_initiation
observability:
  status: verified
  coverage_ref: ssu:coverage:003
input_evidence:
  - ref: ssu:evidence:003
    dependency_group: initiation-log-family-1
alternative_hypotheses:
  - ssu:hypothesis:H2
  - ssu:hypothesis:H3
assessment:
  support: false
  refutation: true
  state: REFUTED
  certainty_kind: synthetic_benchmark_assessment
impact_proposals:
  - kind: SCOPE_NARROW
    target: ssu:hypothesis:H1
    permitted_scope: ssu:proposition:H1-sole-initiation
    rationale: counterexample_to_universal_claim
  - kind: REQUEST_EVIDENCE
    target: ssu:hypothesis:H3
    request: independently_verify_delegation
provenance:
  evaluator_version: bcef-prototype-0.1
  evidence_lineage_hash: synthetic-lineage-hash
  audit_ref: ssu:audit:0041
safety:
  grants_authority: false
  mutates_protected_policy: false
```

### 9.1 Required contract semantics

A valid test must declare the exact proposition, time scope, evidence references, observation coverage, rule assumptions, alternative hypotheses, assessment state, and evaluator version. A valid Impact must reference its originating test, expected structural effect, evidence dependencies, and review status. An incomplete test may be retained as `UNKNOWN`, but must not be promoted to a conclusive contradiction.

### 9.2 Example of a rejected Impact

```yaml
unit_id: ssu:impact:bad-0042
origin_test: ssu:test:00041
kind: HYPOTHESIS_SPLIT
target: ssu:hypothesis:H2
reason: Ada_offline_implies_team_does_not_exist
validation:
  accepted: false
  error_codes:
    - HYPOTHESIS_SCOPE_MISMATCH
    - UNSUPPORTED_LOGICAL_ENTAILMENT
```

The test against Ada's sole initiation does not logically justify destroying the team-control hypothesis.

---

## 10. Reference Evaluation Algorithm

```text
function evaluate_conditional_test(test, registry, evidence_store, policy):
    validate_schema_and_types(test)
    H = registry.get_hypothesis(test.hypothesis_ref)
    assert test.scope is_subset_of H.testable_scope
    E = evidence_store.resolve_immutable(test.input_evidence)
    lineage = evidence_store.build_dependency_dag(E)
    if lineage.has_unresolved_cycle():
        return UNKNOWN(reason="EVIDENCE_DEPENDENCY_CYCLE")
    if not preconditions_established(test.preconditions, E):
        return UNKNOWN(reason="PRECONDITIONS_NOT_ESTABLISHED")
    if test.requires_absence_as_evidence and not coverage_verified(test):
        return UNKNOWN(reason="OBSERVABILITY_INSUFFICIENT")
    alternatives = registry.get_alternatives(test.alternative_hypotheses)
    result = run_mode_specific_logic(test.mode, H, E, alternatives)
    result = preserve_support_and_refutation_separately(result)
    proposals = construct_scoped_impact_proposals(result, test, lineage)
    for proposal in proposals:
        validate_scope(proposal, H)
        validate_provenance_and_dependencies(proposal, lineage)
        reject_if_authority_escalation(proposal)
    append_immutable_test_record(result, proposals)
    return result, proposals  # never auto-deploy
```

A separate function handles governance-approved application of Impact. This separation is essential for test reproducibility and rollback.

---

## 11. Experimental Arms and Baselines

| Arm | Configuration | Purpose |
|---|---|---|
| B0 | Flat similarity clustering, threshold rejection | Conventional simple baseline |
| B1 | Single-direction forward rules | Test value of additional IF modes |
| B2 | Forward + reverse, no explicit alternatives | Isolate alternative-hypothesis representation |
| B3 | Four IF modes, global negative score | Test hypothesis scoping |
| B4 | Four IF modes, scoped contradictions, scalar Impact | Test structural feedback |
| B5 | B4 plus dependency tracking and four-valued status | Test evidence controls |
| B6 | Full BCEF with typed structural Impact and review gates | Proposed integrated system |
| B7 | Oracle access to synthetic truth, evaluation only | Upper bound, never a deployable competitor |

The experimental arms must share identical observation budgets, data splits, and evaluation timing. Computational resources and human review effort must be reported rather than hidden.

### 11.1 Ablation matrix

For B6, separately remove: reverse tests; counterfactual tests; contradiction scoping; evidence dependency graph; observability gates; four-valued status; structural Impact; temporal validity; alternative-hypothesis retention. Each ablation should be pre-registered with a predicted effect and a potential null result.

### 11.2 Information parity

The oracle arm is not compared as an ordinary operational method. A proposed system must not gain access to hidden ground truth, generator parameters, future observations, or evaluator labels. Distinguish training-time knowledge from test-time access.

---

## 12. Synthetic Dataset Generation

### 12.1 Generator factors

The synthetic generator varies: team size, delegation rate, shared-service prevalence, identity overlap, membership turnover, delayed logging, observation dropout, timestamp noise, correlated feature families, confounding common triggers, compromise simulations, and alternative-hypothesis ambiguity.

### 12.2 Split discipline

Use disjoint generator seeds and scenario families for development, validation, and held-out evaluation. Include out-of-distribution tests with unseen team sizes, service-sharing patterns, and evidence gaps. Publish the generator configuration, random seeds, dataset version, and evaluation scripts where legally and safely possible.

### 12.3 Ground-truth manifest

The evaluator stores separately: actual initiation actor, delegated principal, team membership intervals, service use, address-control relationships, evidence source lineage, and authorized operation status. The inference system must not access this manifest. Authorization truth is not an output target for the identity inference test.

### 12.4 Annotation consistency

Label each hypothesis at the granularity of proposition and interval. For partially true hypotheses, use decomposed proposition labels instead of forcing a single global truth value. Have a second evaluator independently review ambiguous labels and adjudicate disagreements under a documented protocol.

---

## 13. Benchmark Scenarios

| ID | Scenario | Key expected distinction |
|---|---|---|
| S01 | Single actor, complete logs | Correctly reject unsupported alternatives |
| S02 | Two-person team, alternating initiators | Reject sole-person claim, preserve team claim |
| S03 | Delegated scheduled execution | Distinguish initiator from principal |
| S04 | Shared service across unrelated teams | Avoid false merge |
| S05 | Common external timing trigger | Avoid causal overattribution |
| S06 | Missing logs during service outage | Return unknown rather than false refutation |
| S07 | Delayed event ingestion | Revise assessment without history erasure |
| S08 | Repeated derived features | Prevent double counting |
| S09 | Contradictory independent witnesses | Preserve conflict state |
| S10 | Membership change at boundary | Respect temporal scopes |
| S11 | Address rotation | Preserve continuity only with adequate evidence |
| S12 | Key compromise in synthetic lab | Distinguish key use from legitimate intent |
| S13 | Simulator intervention | Mark counterfactual as model-conditional |
| S14 | Unsupported intervention | Return unidentifiable/unknown |
| S15 | Feedback cycle | Reject self-supporting score amplification |
| S16 | Erroneous Impact proposal | Reject cross-hypothesis scope expansion |
| S17 | Nested team and subgroup | Preserve composition under partial contradiction |
| S18 | High confidence, wrong initial cluster | Test recovery without unauthorized actions |
| S19 | Evidence source later discredited | Reassess descendants via lineage |
| S20 | Valid counterexample to universal claim | Correctly reject quantified proposition |

The benchmark must include both easy cases and intentionally ambiguous cases. A method that always returns `UNKNOWN` should perform poorly on coverage and correct-rejection metrics, even if its false-rejection rate appears low.

---

## 14. Evaluation Metrics

### 14.1 Primary metrics

**False Rejection Rate (FRR):** among hypotheses that are true or still admissible under the evaluation ground truth and evidence policy, the fraction incorrectly marked `REFUTED`. Define the denominator and treatment of partially true propositions before evaluation.

**Correct Rejection Recall (CRR):** among hypotheses genuinely contradicted by admissible evidence, the fraction correctly refuted within the right scope.

**Scope Leakage Rate (SLR):** fraction of accepted negative Impacts that modify a hypothesis, relation, or time interval outside the justified contradiction scope.

**Alternative Preservation Rate (APR):** fraction of ground-truth-compatible alternatives retained after a contradiction to a related hypothesis.

**Unsupported Certainty Rate (UCR):** fraction of conclusive assessments made without sufficient preconditions, provenance, or observability.

### 14.2 Secondary metrics

- Four-state classification quality and confusion matrix.
- Evidence-dependency violation count and lineage coverage.
- Temporal-boundary error and quantifier error.
- False merge / false split rates on compositional identity.
- Structural Impact precision, recall, and reviewer rejection rate.
- Calibration, if a properly defined probabilistic output is provided; otherwise omit probabilistic calibration claims.
- Time to recover from discredited evidence.
- Per-test latency, memory, storage, review minutes, and energy/compute proxies.
- Correct-rejection coverage at fixed FRR and FRR at fixed correct-rejection coverage.
- Number of policy/authorization boundary violations; target zero in the test suite.

### 14.3 Cost-sensitive reporting

Report trade-off curves, not just a single headline number. A system that reduces FRR by retaining every hypothesis indefinitely may be unusable. A system that increases CRR by rejecting entire teams after one contradiction may be unsafe. Compare systems at matched evidence budgets and report abstention and reviewer workload explicitly.

---

## 15. Conformance Test Vectors

| ID | Input / condition | Required result |
|---|---|---|
| CT-01 | Valid forward test with observed prediction | Supported within declared scope |
| CT-02 | `H => E`, observation `E` | Do not conclude `H` by converse alone |
| CT-03 | Missing expected log, coverage unknown | `UNKNOWN`, not `REFUTED` |
| CT-04 | Ada offline, team could delegate | Refute only sole-person proposition if justified |
| CT-05 | Shared-service evidence for two teams | Preserve independent-team alternative |
| CT-06 | Counterfactual simulator lacks intervention support | Flag unidentifiable |
| CT-07 | Same event represented by five derived features | One dependency family, no independent inflation |
| CT-08 | Independent support and refutation | `CONFLICT` |
| CT-09 | Evidence arrives after first assessment | Append revision, retain prior record |
| CT-10 | Contradiction refers to wrong interval | Reject or narrow Impact |
| CT-11 | Hypothesis uses `SOME`; one failed instance | Do not reject existential proposition |
| CT-12 | Universal claim has valid counterexample | Reject universal proposition |
| CT-13 | Impact attempts to delete raw observation | Reject |
| CT-14 | Impact changes unrelated hypothesis | Reject scope mismatch |
| CT-15 | Derived IF result used as own independent source | Reject lineage cycle |
| CT-16 | Identity inference tries to grant transfer authority | Reject and audit |
| CT-17 | Proposal lacks evaluator version | Reject as nonconformant |
| CT-18 | Proposal references missing evidence | Reject or quarantine |
| CT-19 | Membership ends before tested event | Respect temporal validity |
| CT-20 | Reverse test has multiple plausible causes | Preserve alternatives |
| CT-21 | Scoring-tree retype lacks rationale | Require review |
| CT-22 | Valid Impact fails governance approval | Leave accepted graph unchanged |
| CT-23 | Reviewer-approved update later reversed | Preserve audit and rollback lineage |
| CT-24 | Protected policy modification via BCEF | Deny regardless of score |

Each vector requires a machine-checkable fixture, expected status, expected permitted Impact set, expected audit entries, and a negative assertion against prohibited state changes.

---

## 16. Falsifiable Research Hypotheses

**HYP-01 — Scoped contradiction reduces false rejection.** At matched correct-rejection recall, B4 has lower FRR than B3 on compositional-team scenarios. **Falsified if:** the pre-registered improvement threshold is not met or confidence intervals are compatible with no benefit.

**HYP-02 — Alternative portfolios improve preservation.** B6 retains more compatible alternative hypotheses than B2 after a contradiction. **Falsified if:** APR is unchanged or worsens at matched coverage and cost.

**HYP-03 — Observability gates prevent missing-as-negative errors.** B6 produces fewer unsupported rejections than an otherwise identical system without observability gates. **Falsified if:** UCR does not decrease or correct rejection collapses beyond a pre-specified tolerance.

**HYP-04 — Dependency tracking reduces evidence inflation.** B5 outperforms B4 under high feature correlation on false-rejection and unsupported-certainty metrics. **Falsified if:** no robust improvement is observed.

**HYP-05 — Structural Impact improves recovery.** B6 restores correct hypothesis structure faster than B5 after discrediting an evidence source. **Falsified if:** recovery is no faster or produces more invalid structural edits.

**HYP-06 — Reverse IF helps distinguish shared service from shared ownership.** Adding reverse alternatives reduces false merges in scenarios S04 and S05. **Falsified if:** no advantage appears at matched observation budgets.

**HYP-07 — Counterfactual IF adds value only when identifiable.** Simulator-supported interventions improve differentiation on S13 while unsupported interventions appropriately abstain on S14. **Falsified if:** gains vanish or unsupported causal claims increase.

**HYP-08 — Temporal typing reduces boundary errors.** Time-aware scopes reduce false rejection near membership changes compared with temporally flattened baselines. **Falsified if:** error is unchanged or latency cost exceeds the pre-registered practical threshold.

**HYP-09 — Four-valued states improve conflict handling.** Explicit `CONFLICT` handling reduces unsupported certainty compared with scalar cancellation. **Falsified if:** no measurable improvement in conflict-case decision quality.

**HYP-10 — Full BCEF remains computationally feasible.** B6 meets a declared per-test latency and memory budget on target synthetic scales. **Falsified if:** it exceeds the budget, regardless of accuracy gains.

**HYP-11 — Governance gates prevent unsafe structural promotion.** Invalid cross-scope and authority-changing proposals are rejected in all designated negative tests. **Falsified if:** any prohibited proposal is applied.

**HYP-12 — Benefits transfer across synthetic generator families.** B6's improvements persist on held-out scenario families and unseen composition patterns. **Falsified if:** performance deteriorates below pre-registered transfer criteria.

Thresholds must be set *before* the confirmatory experiment, based on application costs and pilot variance; no numeric result is claimed here.

---

## 17. Statistical and Reproducibility Plan

1. **Pre-registration:** publish hypotheses, primary metrics, baseline configurations, success thresholds, exclusions, and planned subgroup analyses.
2. **Pilot phase:** use development seeds to estimate variance and choose a justified sample size; do not use confirmatory seeds to tune models.
3. **Paired comparisons:** evaluate arms on identical synthetic worlds; use paired bootstrap intervals or another justified paired method.
4. **Hierarchy:** account for correlated events nested within teams and scenario seeds; avoid treating every transaction as independent.
5. **Multiple testing:** distinguish confirmatory primary hypotheses from exploratory analyses and apply an appropriate multiplicity strategy.
6. **Failure reporting:** publish regressions, invalid test rates, abstention, resource costs, and scenarios where simple baselines win.
7. **Artifact provenance:** archive generator version, manifests, configuration hashes, evaluation code, model prompts (if used), and policy versions.
8. **Independent replication:** reserve hidden seeds and separate evaluators for a final blind run.
9. **Negative controls:** include random unrelated features and deliberately uninformative evidence to detect spurious confidence.
10. **Sensitivity analysis:** vary missingness, correlation, team size, delegation, and intervention identifiability.

No benchmark outcome, effect size, or significance level should be represented as observed until the experiments have actually been run.

---

## 18. Threats to Validity

### 18.1 Synthetic realism

A simulator may encode the same assumptions that BCEF uses, creating artificial advantage. Counter this with independently implemented generators, adversarial scenario authors, and held-out families that violate convenient modeling assumptions.

### 18.2 Label leakage

Generator IDs, deterministic naming, or time patterns may reveal hidden labels. Remove leakage-prone metadata, audit feature provenance, and run a simple leakage-detection classifier.

### 18.3 Baseline unfairness

An under-tuned flat clustering baseline would exaggerate gains. Use credible baseline implementations, equal information budgets, documented hyperparameter searches, and independent review.

### 18.4 Subjective Impact scoring

Structural changes can be difficult to judge. Define graph-edit correctness against synthetic truth and use blinded human adjudication for ambiguous proposals. Report inter-rater agreement and unresolved cases.

### 18.5 Model-dependent counterfactuals

Counterfactual predictions are conditional on a structural causal or simulation model. Mark unsupported interventions explicitly. Do not extrapolate synthetic causal validity to operational settings without separate evidence.

### 18.6 Goodhart effects

A system could optimize FRR by never rejecting, or optimize CRR by rejecting indiscriminately. Joint metrics and constrained operating points are mandatory.

---

## 19. Security, Privacy, and Governance

The benchmark runs in an isolated, non-production environment with inert identifiers, synthetic assets, and no live signing keys. Red-team scenario descriptions remain at the level needed to test defensive inference and authorization boundaries; they do not require real-world exploitation. Logs and derived artifacts must be access-controlled, versioned, and retained under a documented policy.

The **inference plane** may produce tests, hypothesis assessments, and Impact proposals. The **evaluation plane** independently scores their correctness. The **governance plane** authorizes consequential graph or model promotion. The **safety control plane** independently governs protected operations and is never modified by an inference result. These separations should be verified by negative tests rather than accepted as architecture diagrams alone.

Privacy protection matters even in later real-world adaptations: identity hypotheses can be sensitive, and an unverified link between an address and a person should not be published as fact. Any operational deployment requires its own lawful basis, risk assessment, consent/notice analysis where applicable, appeal or correction mechanisms, and authorization boundaries.

---

## 20. Security Residuals and AQSI Question Relay

Each benchmark failure is recorded as a typed **Security Residual Unit**, not just a scalar metric. A residual contains scenario seed, failure class, evidence lineage, affected hypothesis scope, expected vs observed behavior, uncertainty, reproduction steps, and owner for review.

Example residuals:

- `RES-FR-001`: a sole-person contradiction incorrectly deleted a team hypothesis.
- `RES-DEP-002`: repeated log-derived features inflated negative confidence.
- `RES-OBS-003`: delayed logs were treated as proof of absence.
- `RES-IMP-004`: an Impact changed a graph edge outside the tested interval.
- `RES-CF-005`: an unsupported counterfactual was reported as causal evidence.

AQSI may turn these residuals into falsifiable questions: *Which additional observation distinguishes delegated execution from shared ownership?* *What observability threshold is needed before absence counts as evidence?* *Which structural revision reduces false rejection without increasing false acceptance?*

Proposed improvements follow `RESIDUAL → QUESTION → CANDIDATE → INDEPENDENT TEST → GOVERNANCE REVIEW → RELAY`, consistent with SPEC-005 and SPEC-006. A new candidate does not inherit validity merely because an earlier Relay accepted it.

---

## 21. Phased Implementation Roadmap

**Phase 0 — Contracts first.** Finalize SSU schemas, typed identity roles, four IF modes, Impact types, evidence lineage, and conformance fixtures. Establish a rule that no inference result may alter protected authorization.

**Phase 1 — Deterministic synthetic kernel.** Implement a minimal generator with Ada, Ben, Orion, RelayS, and the eight-event timeline. Produce a separate hidden truth manifest and a public observation stream.

**Phase 2 — Baselines and evaluator.** Implement B0–B4 and blinded metrics for FRR, CRR, SLR, APR, and UCR. Verify the evaluator using hand-checked edge cases.

**Phase 3 — Full BCEF.** Add dependency DAGs, observability gates, four-valued assessment, typed Impact proposals, append-only revisions, and governance validation.

**Phase 4 — Adversarial expansion.** Introduce S01–S20, correlated evidence, delayed observations, team recomposition, counterfactual interventions, and adversarial negative tests.

**Phase 5 — Independent validation.** Freeze model and generator versions, run blind seeds, publish failures and cost trade-offs, and invite independent replication.

**Phase 6 — Governed research relay.** Register residuals and AQSI questions, test candidate revisions under SPEC-006, and document which ideas failed or remain unresolved.

---

## 22. Acceptance Criteria and Stop Conditions

A benchmark release is **experiment-ready** only when schemas validate, the truth manifest is isolated, all mandatory conformance vectors pass, baseline parity is documented, and the evaluation protocol is frozen. It is **research-supported** only when a pre-registered experiment yields reproducible evidence under independent review. These are different milestones.

Stop or quarantine the experiment if a test attempts to operate on live assets, a protected policy can be changed by inference, hidden labels leak into the inference stream, evidence lineage cannot be reconstructed, or an evaluator cannot distinguish a hypothesis contradiction from a different proposition. Any such event is itself a reportable residual.

---

## 23. Conclusions

This case treats contradiction as a **precise, scoped operation on a testable proposition**, not as a universal command to reject related identities. Bidirectional conditional tests may improve the quality of security inference when they preserve alternatives, observability, temporal context, evidence dependence, and structural Impact lineage. But the value of these mechanisms must be demonstrated against strong baselines under controlled, independently evaluated experiments.

The central research proposition is straightforward:

> **Reject what the evidence actually contradicts; preserve what it does not; revise structure with provenance; never convert inference into authority.**

A successful result would not prove that BCEF solves identity attribution or security. It would establish a narrower, falsifiable claim: under specified synthetic conditions, a typed and scoped conditional-feedback architecture can make fewer erroneous rejections while retaining useful discriminatory power at an acceptable cost.

---

## Appendix A — Minimal Fixture Set

```yaml
fixtures:
  - id: false_rejection_team
    truth: {H1: false, H2: true, H3: true}
    evidence: [Ada_offline_at_t3, RelayS_executed_t3]
    expected:
      refuted: [H1]
      retained: [H2, H3]
      forbidden_impacts: [delete_H2, revoke_team_authorization]
  - id: missing_log
    truth: {H3: true}
    evidence: [no_initiation_log_at_t3]
    coverage: unknown
    expected:
      assessment: UNKNOWN
      forbidden_impacts: [refute_H3_due_to_absence]
  - id: conflicting_witnesses
    evidence: [independent_support, independent_refutation]
    expected:
      assessment: CONFLICT
      forbidden_impacts: [silently_cancel_to_neutral]
  - id: repeated_features
    evidence: [raw_log, derived_feature_A, derived_feature_B]
    lineage: {derived_feature_A: raw_log, derived_feature_B: raw_log}
    expected:
      dependency_groups: 1
      forbidden_impacts: [triple_count_raw_log]
```

## Appendix B — Terminology

- **BCEF:** Bidirectional Conditional Evidence Feedback; a family of scoped tests and typed feedback proposals.
- **False rejection:** An unjustified rejection of a true or still-admissible hypothesis at a specified evaluation point.
- **Hypothesis portfolio:** A set of potentially overlapping, competing, or nested explanations with explicit scope.
- **Impact:** A structured, auditable proposal to revise scoring, hypothesis structure, evidence assessment, or follow-up work.
- **Observability gate:** A check that determines whether missing evidence can legitimately inform a test.
- **Provenance:** Traceable source, transformation, evaluator, and revision history.
- **REN:** Relational Evidence Navigation; directional, context-aware evidence interpretation.
- **SSU:** Structural Security Unit; a typed and versioned unit under SPEC-001.
- **UTN:** Universal Typing and Naming; typed naming and identity boundaries.
- **Validated RSI:** Recursive improvement subject to independent evidence, governance, bounded resources, and rollback.

## Appendix C — Repository Navigation

**Prior case:** `cases/CASE-002-UTN-On-Chain-Identity-Sandbox.md`  
**Next case:** `cases/CASE-004-Compromised-Signing-Service-Defense.md`  
**Core research:** `docs/ASSI-006-Bidirectional-Conditional-Evidence-Feedback.md`  
**Formal contract:** `specs/SPEC-003-Bidirectional-IF-and-Evidence-Impact-Contract.md`  
**Unit envelope:** `specs/SPEC-001-Structural-Security-Unit-Contract.md`  
**Identity contract:** `specs/SPEC-002-Compositional-Identity-and-UTN-Contract.md`  
**Governance:** `specs/SPEC-006-Validated-RSI-and-Governance-Contract.md`  
**Benchmark design:** `docs/ASSI-011-Benchmark-Laboratories-and-Falsifiable-Security-Hypotheses.md`

---

*ASSI v0.1.0 Research Foundation. This document proposes a synthetic experiment and normative research direction; it does not report executed results or establish operational security guarantees.*
