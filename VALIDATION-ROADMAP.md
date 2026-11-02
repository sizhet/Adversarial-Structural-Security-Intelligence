# VALIDATION ROADMAP — Adversarial Structural Security Intelligence (ASSI)

**Release:** v0.1.0 — Research Foundation  
**Document type:** Prospective validation program, conformance plan, and evidence-gated research roadmap  
**Status:** Proposed; no completed ASSI benchmarks, independently replicated results, certifications, or production-security claims are implied  
**Repository location:** `VALIDATION-ROADMAP.md`  
**License:** Apache-2.0  
**Date:** 2026-11-02

> **Research boundary:** A valid signature does not prove legitimate authorization. An inferred identity does not confer authority. A passing simulation is not independent validation. Independent validation is not deployment approval. No candidate system may authorize its own promotion.

## 1. Mission and scope

This roadmap turns the research agenda in [FUTURE-DIRECTIONS.md](FUTURE-DIRECTIONS.md), the question register in [OPEN-QUESTIONS.md](OPEN-QUESTIONS.md), and the thirty preregistration candidates in [TESTABLE-HYPOTHESES.md](TESTABLE-HYPOTHESES.md) into an auditable validation program. The objective is not to maximize a single security score. It is to discover **which structural mechanisms work, against which specified baselines and threat models, under what assumptions, with which failure modes, and at what operational and governance cost**.

ASSI combines Structural Security Units (SSUs), UTN compositional identity, REN directional evidence, Bidirectional Conditional Evidence Feedback (BCEF), independently enforced authorization, Red/Blue/Evaluation/Governance adversarial drives, Security Residuals, AQSI autonomous questioning, and independently validated recursive self-improvement (RSI). These are **research proposals**, not an implemented or verified security product.

The roadmap has three complementary outputs:

1. **Conformance evidence:** whether an implementation respects typed contracts, policy boundaries, evidence provenance, and decision semantics.
2. **Empirical evidence:** whether it improves measured outcomes relative to preregistered baselines on held-out, reproducible scenarios.
3. **Governance evidence:** whether evaluation, authorization, change approval, and rollback remain independent when the system adapts or fails.

A result in one category cannot substitute for another.

## 2. Validation principles

| Principle | Operational requirement | Failure that invalidates the claim |
|---|---|---|
| Specifications before runtime | Versioned SSU and component contracts precede experiments | Ambiguous or shifting outcome semantics |
| Threat-model specificity | Declare adversary capabilities, protected assets, time horizon, and trust boundaries | Broad “secure” claim without a defined setting |
| Independent evaluation | Hold-out data, evaluator identity, and scoring rules are separated from candidate generation | Candidate can modify or inspect hidden tests |
| Explicit unknowns | Unknown, conflicting, stale, and absent evidence are distinct | Unknown silently converted into rejection or approval |
| Hypothesis-scoped contradiction | Contradictions attach to specific hypotheses, claims, times, and provenance | Local contradiction globally invalidates unrelated identities |
| Authority separation | Inference and model confidence cannot issue, expand, or waive authorization | High score bypasses independent policy enforcement |
| Bounded exposure | Risk budgets, transaction binding, time limits, and recovery are testable | Unbounded exposure or replay permitted |
| Negative results are results | Null, adverse, and inconclusive outcomes are registered | Only favorable trials retained |
| Explicit leftovers | Unresolved residuals, failures, and repeated observations enter relay records | Failures silently discarded or repeated as novelty |
| Safe evaluation | Synthetic or explicitly authorized settings only | Live exploitation, real funds, or unapproved interventions |

## 3. Evidence and claim maturity ladder

| Level | Description | Required evidence | Permitted claim |
|---|---|---|---|
| **H0 — Hypothesis** | Design and falsifiable prediction | Contract, threat model, baseline, planned metrics | “We hypothesize…” |
| **H1 — Synthetic observation** | Reproducible result in a bounded lab | Frozen protocol, seeds, code, data, logs, uncertainty, failures | “Observed under this synthetic threat model…” |
| **H2 — Independent replication** | External evaluator or independently built implementation reproduces result | Replication report, implementation separation, discrepancy log | “Independently replicated within the specified scope…” |
| **H3 — Authorized field study** | Bounded, reviewed, real-world observation | Written authorization, monitoring, rollback, incident handling, governance sign-off | “Observed in this authorized setting…” |
| **H4 — Deployment decision** | Separate operational authorization | Explicit accountable approval, risk acceptance, continuous controls | “Approved for this bounded use,” never “universally secure” |

**No automatic promotions.** H1 does not entail H2; H2 does not entail H3; H3 does not entail H4. Results may be demoted if assumptions, data provenance, evaluator independence, or reproducibility fail.

## 4. Seven-stage research and validation sequence

### Stage 0 — Freeze definitions, threat models, and governance boundaries

**Goal:** Make the research testable before implementing any candidate algorithm.

**Work packages:**

- Version the six normative contracts: [SPEC-001](specs/SPEC-001-Structural-Security-Unit-Contract.md) through [SPEC-006](specs/SPEC-006-Validated-RSI-and-Governance-Contract.md).
- Define typed asset, action, identity hypothesis, evidence source, timestamp, decision, policy version, authority, and audit records.
- Record threat models for compromised signing services, correlated evidence, identity churn, evaluator contamination, and unauthorized model-driven actions.
- Identify who may propose, evaluate, approve, deploy, revoke, and audit each artifact; document prohibited role combinations.
- Preregister the initial hypotheses, baselines, metrics, statistical analyses, and stopping rules before inspecting held-out results.

**Exit gate G0:** Contract schemas, threat-model register, role matrix, and preregistration bundle receive independent review. All unresolved assumptions remain explicit. **No algorithmic success claim.**

### Stage 1 — Conformance-first synthetic laboratory

**Goal:** Establish deterministic, non-networked test harnesses and contract tests.

**Work packages:**

- Create synthetic entity/event graphs, simulated transaction-intent records, policy decisions, evidence provenance graphs, and change histories.
- Build fixtures for missing evidence, contradictory observations, clock skew, repeated events, source correlation, identity merges/splits, policy changes, and replay.
- Test parser/schema validation, state transitions, audit completeness, policy decision determinism, fail-closed behavior where specified, and safe abstention.
- Run property-based and metamorphic tests: e.g., duplicating a dependent source must not increase independent evidence count; changing a transaction binding must invalidate the old authorization.
- Establish reproducible environment manifests, immutable fixture hashes, seed control, and baseline implementations.

**Exit gate G1:** Mandatory contract tests pass; every failed invariant has a traceable defect record; no production credentials or real funds enter the lab. Passing G1 establishes **conformance to tested contracts**, not security effectiveness.

### Stage 2 — Four benchmark families and falsifiable comparisons

**Goal:** Evaluate mechanism-specific hypotheses against strong, declared alternatives.

**BM-001 — Compositional Identity:** identity uncertainty, provenance, temporal change, false merges/splits.  
**BM-002 — BCEF Evidence Revision:** dependent evidence, four-way IF, scoped contradiction, abstention and calibration.  
**BM-003 — Authorization and Bounded Loss:** independent enforcement, transaction binding, replay resistance, budget limits, recovery.  
**BM-004 — Adversarial Relay and Validated RSI:** role independence, residual retention, evaluator leakage, regression gates, bounded improvement.

Run matched seeds and data splits; include ablations that remove one mechanism at a time. Report false acceptance and false rejection, calibrated uncertainty, exposure severity, detection delay, compute and human-review costs, and failure clusters. Do not collapse safety constraints into a single weighted score that allows unacceptable breaches to be traded away.

**Exit gate G2:** A complete benchmark report includes both positive and negative results, confidence intervals or uncertainty estimates, held-out outcomes, reproducible manifests, and predeclared decision rules. No hidden-test contamination.

### Stage 3 — AQSI and Security Residual research

**Goal:** Determine whether autonomous question generation identifies *new, testable* security gaps rather than merely generating plausible text.

**Work packages:**

- Represent each residual with trigger, violated invariant, affected scope, provenance, reproduction recipe, and unresolved status.
- Compare AQSI-generated questions with expert-authored, random, and retrieval-only question baselines under blinded evaluation.
- Require a question to specify discriminating hypotheses, safe experiment, expected information value, and conditions under which it should be retired.
- Measure novel failure discovery on held-out scenario families, not overlap with training cases or rhetorical novelty.
- Preserve unanswered questions, repeated observations, and invalidated hypotheses as explicit leftovers.

**Exit gate G3:** Question utility and residual traceability are independently assessed. A generated question does not create authorization to run a hazardous experiment.

### Stage 4 — Independently validated, bounded RSI

**Goal:** Test whether candidate changes improve generalization without eroding safety controls.

**Work packages:**

- Separate candidate generation, evaluation, and approval; evaluator data and governance rules are immutable to the candidate.
- Require paired baseline/candidate testing, held-out challenge sets, regression suites, drift checks, and rollback rehearsals.
- Set hard ceilings on budget, runtime, tool access, policy scope, and recursion depth.
- Evaluate improvement across unseen failure families, not just previously discovered residuals.
- Maintain immutable ancestry of proposed changes, rejected changes, and rollback events.

**Exit gate G4:** Only independently validated candidates may be *proposed* for a separate approval decision. Any authorization-boundary violation, evaluator tampering, or unrecoverable regression blocks promotion regardless of aggregate score.

### Stage 5 — Cross-domain replication and transfer boundaries

**Goal:** Test whether structural patterns transfer without assuming their guarantees transfer.

**Candidate domains:** synthetic payment authorization, supply-chain access control, agent tool-use governance, distributed service identity, and data-provenance review. Each needs its own lawful, domain-specific threat model and evaluation.

**Work packages:**

- Define a source-to-target semantic mapping and list non-equivalent assumptions.
- Compare structural transfer against surface-feature transfer and target-domain baselines.
- Record negative transfer, abstention, authority mismatches, and new failure classes.
- Replicate results across independent teams and implementation stacks where practical.

**Exit gate G5:** A transfer claim names the exact invariant preserved, conditions broken, and domains tested. Negative-transfer evidence is published alongside successes.

### Stage 6 — Authorized bounded field evaluation (optional, not assumed)

**Goal:** Assess operational fit only if previous evidence warrants a tightly governed pilot.

**Prerequisites:** written authorization; independent risk review; privacy and data minimization; scoped assets and participants; shadow or advisory mode first; safe-stop mechanism; transaction-level approval; exposure caps; incident-response ownership; monitoring and rollback; explicit expiration.

**Exit gate G6:** A separate accountable governance body decides whether the evidence supports a bounded continuation, modification, or termination. This roadmap does not grant field access or deployment approval.

## 5. Benchmark design matrix

| Benchmark | Hypotheses | Primary baseline families | Primary outcomes | Safety-critical failure modes | Reference contracts/cases |
|---|---|---|---|---|---|
| **BM-001** | TH-05–08 | Static identifiers; pairwise matching; time-agnostic clustering | Identity calibration; false merge/split; change-detection latency; provenance integrity | Irreversible identity conflation; leaked inferred identity as authority | [SPEC-002](specs/SPEC-002-Compositional-Identity-and-UTN-Contract.md), [CASE-002](cases/CASE-002-UTN-On-Chain-Identity-Sandbox.md) |
| **BM-002** | TH-09–14 | Simple weighted evidence; naive Bayes under independence; unscoped contradiction logic | Brier/log loss; ECE; false rejection; abstention utility; update consistency | Correlated-source double count; false global rejection; evidence laundering | [SPEC-003](specs/SPEC-003-Bidirectional-IF-and-Evidence-Impact-Contract.md), [CASE-003](cases/CASE-003-Bidirectional-IF-and-False-Rejection.md) |
| **BM-003** | TH-01,03,15–18 | Signature-only checks; model-mediated approval; non-transaction-bound grants | Unauthorized action rate; replay acceptance; exposure tail; recovery time; legitimate denial | Policy bypass; stale grant reuse; compromised recovery; authority drift | [SPEC-004](specs/SPEC-004-Authorization-and-Safety-Control-Contract.md), [CASE-004](cases/CASE-004-Compromised-Signing-Service-Defense.md) |
| **BM-004** | TH-19–26,29–30 | Single evaluator; unstructured multi-agent consensus; ungated adaptation | Distinct failure discovery; evaluator contamination; regression rate; held-out gain; rollback success | Self-approval; benchmark leakage; unbounded recursion; governance drift | [SPEC-005](specs/SPEC-005-Adversarial-Drive-and-Relay-Contract.md), [SPEC-006](specs/SPEC-006-Validated-RSI-and-Governance-Contract.md), [CASE-005](cases/CASE-005-Adversarial-Drives-and-Security-RSI.md) |

**Additional tracks:** TH-02 and TH-04 use trust-boundary and contradiction registers in [CASE-001](cases/CASE-001-Cryptocurrency-Trust-and-Liquidity.md). TH-27–28 require independent cross-domain preregistration, not automatic inclusion in BM-001–004 results.

## 6. Complete thirty-hypothesis validation crosswalk

The authoritative hypothesis definitions and falsification rules remain in [TESTABLE-HYPOTHESES.md](TESTABLE-HYPOTHESES.md). This table is a *planning crosswalk*, not an assertion that any test has run.

| Hypothesis | Proposed validation focus | Primary stage / benchmark |
|---|---|---|
| TH-01 | Separate valid signature from legitimate intent | 2 / BM-003 |
| TH-02 | Locate failures with explicit trust-boundary maps | 2 / CASE-001 |
| TH-03 | Measure exposure-tail reduction versus legitimate denial | 2 / BM-003 |
| TH-04 | Compare reproducibility of contradiction reviews | 2 / CASE-001 |
| TH-05 | Calibrate temporal compositional identity | 2 / BM-001 |
| TH-06 | Compare competing hypotheses versus forced identity merges | 2 / BM-001 |
| TH-07 | Detect provenance-based evidence laundering | 2 / BM-001 |
| TH-08 | Measure temporal change-detection latency | 2 / BM-001 |
| TH-09 | Test directional weak evidence in sparse settings | 2 / BM-002 |
| TH-10 | Measure dependent-source double-count prevention | 2 / BM-002 |
| TH-11 | Measure false rejection under scoped contradictions | 2 / BM-002 |
| TH-12 | Compare four-way IF against one-way rules | 2 / BM-002 |
| TH-13 | Test order and consistency of evidence revisions | 2 / BM-002 |
| TH-14 | Assess calibrated abstention under unknown states | 2 / BM-002 |
| TH-15 | Test independent PEP against model-induced bypass | 1–2 / BM-003 |
| TH-16 | Reject replay after transaction-context changes | 1–2 / BM-003 |
| TH-17 | Compare recovery under separate versus shared authority | 2 / BM-003 |
| TH-18 | Detect and constrain authority-boundary drift | 2–4 / BM-003 |
| TH-19 | Compare independent adversarial roles with single-role tests | 2 / BM-004 |
| TH-20 | Quantify evaluation contamination and leakage | 2–4 / BM-004 |
| TH-21 | Compare typed residual records against unstructured notes | 2–3 / BM-004 |
| TH-22 | Compare competitive relay against unstructured consensus | 2–3 / BM-004 |
| TH-23 | Assess AQSI question value under blinded review | 3 / BM-004 |
| TH-24 | Test residual-guided changes on unseen failure families | 4 / BM-004 |
| TH-25 | Measure independent validator detection of regressions | 4 / BM-004 |
| TH-26 | Enforce recursion budgets and rollback invariants | 4 / BM-004 |
| TH-27 | Compare structural versus surface transfer | 5 / cross-domain |
| TH-28 | Measure negative-transfer selection and abstention | 5 / cross-domain |
| TH-29 | Test governance drift under ungated versus gated search | 4–5 / BM-004 |
| TH-30 | Assess long-horizon reuse of leftover/failure records | 3–5 / BM-004 |

## 7. Minimum dataset and scenario specification

Every dataset or synthetic scenario package must disclose:

- **Scenario identifier and version:** stable ID, schema version, content hash, creation method, and license.
- **Threat model:** adversary goals, observability, capabilities, resources, and explicit exclusions.
- **Ground truth:** independently defined authorized intent, identity links, evidence dependence, policy state, and event timeline where knowable; label uncertainty where not.
- **Evidence lineage:** source IDs, transformations, source dependence, timestamps, and synthetic contamination flags.
- **Counterfactual pairs:** minimal changes to one structural feature, such as authorization scope or evidence provenance, with other factors held fixed.
- **Splits:** train/development/held-out; leakage checks across shared entities, scenarios, templates, and temporal descendants.
- **Difficulty and subgroup strata:** missingness, temporal churn, correlated sources, ambiguity, benign unusual cases, and high-impact actions.
- **Safety:** no private keys, real credentials, real funds, personally identifiable records, or exploit-ready operational targets.

A synthetic label is not a claim about a real person's identity or intent. If an external dataset is ever used, record consent/permission, provenance, privacy review, and legal restrictions before ingestion.

## 8. Baselines, ablations, and experimental controls

Each proposed mechanism requires a **fair baseline** and an **ablation**. At minimum:

1. **Identity:** static matching; temporal matching without UTN composition; full UTN candidate.
2. **Evidence:** simple additive scoring; dependency-aware scoring without BCEF; BCEF with scoped contradiction; BCEF without scope control.
3. **Authorization:** signature-only check; model-mediated policy recommendation; independent PDP/PEP with transaction binding and exposure caps.
4. **Adversarial evaluation:** single agent; homogeneous consensus; independent Red/Blue/Evaluation/Governance roles with frozen evaluator.
5. **RSI:** no adaptation; ungated adaptation in isolated simulation; independent validation and rollback gates.

Keep model capability, compute budget, scenario exposure, data access, and human review cost comparable. Report unequal-resource comparisons explicitly. Predeclare ablations rather than selecting the most favorable ones afterward.

## 9. Metrics and non-compensable safety constraints

### 9.1 Effectiveness and uncertainty

- **Identity:** false-merge and false-split rates; calibration by confidence band; temporal detection latency.
- **Evidence:** Brier score, log loss, expected calibration error, contradiction precision, false rejection, false acceptance, and abstention coverage/utility.
- **Authorization:** unauthorized-action rate, replay acceptance, policy-decision consistency, legitimate-action denial, maximum exposure, time to revoke, and recovery completeness.
- **Adversarial relay:** unique verified failure classes per fixed budget, rediscovery rate, held-out transfer, contamination rate, and reproducibility.
- **RSI:** held-out improvement, regression incidence, constraint violation count, rollback success, evaluator independence, and resource consumption.
- **Cross-domain:** invariant preservation, negative-transfer incidence, abstention appropriateness, and target-domain performance relative to local baselines.

### 9.2 Hard safety gates

A candidate **fails promotion** if any preregistered critical invariant is violated, even if its average performance improves. Example critical gates include: model-generated authorization accepted without independent policy approval; transaction binding bypass; audit-log tampering; evaluator access to hidden scoring rules; unapproved change to governance policy; and rollback that cannot restore the approved state. Thresholds and severity classes must be set before evaluation; do not claim that zero observed violations proves zero real-world risk.

### 9.3 Statistical and reporting discipline

Use paired trials where possible; disclose sample sizes, confidence intervals, effect sizes, variance across seeds, subgroup failure rates, and multiplicity corrections or exploratory labels. Register stopping rules and primary outcomes. Distinguish statistical significance, practical value, and safety acceptability. Preserve all preregistered outcomes, including null and adverse findings.

## 10. Conformance test catalogue

| Test ID | Invariant | Example safe synthetic test | Contract |
|---|---|---|---|
| CT-001 | SSU records are typed and versioned | Reject missing policy version or unbound action | SPEC-001 |
| CT-002 | Identity hypothesis is not authorization | High-confidence identity cannot authorize a simulated payment | SPEC-001/002/004 |
| CT-003 | Identity changes preserve provenance | Split/merge events retain source and time lineage | SPEC-002 |
| CT-004 | Contradictions remain hypothesis-scoped | Evidence contradicting H1 does not automatically reject H2 | SPEC-003 |
| CT-005 | Dependent sources are not independent votes | Duplicate correlated observations do not multiply support | SPEC-003 |
| CT-006 | Unknown is distinct from false | Missing source produces unknown/abstain where specified | SPEC-003 |
| CT-007 | Authorization is transaction-bound | Modify recipient/amount/expiry and reject old grant | SPEC-004 |
| CT-008 | Enforcement is independent | Candidate model attempts policy override; PEP denies | SPEC-004 |
| CT-009 | Exposure and recovery are bounded | Budget exhaustion, expiry, and revocation take effect | SPEC-004 |
| CT-010 | Adversarial roles are separated | Red agent cannot alter evaluator rubric | SPEC-005 |
| CT-011 | Residuals preserve failures | Failed trial retains trace, scope, and unresolved status | SPEC-005 |
| CT-012 | Candidate cannot self-promote | RSI candidate lacks evaluator/approval credentials | SPEC-006 |
| CT-013 | Rollback is demonstrable | Inject a synthetic regression and restore prior approved version | SPEC-006 |
| CT-014 | Evaluation remains auditable | Verify immutable seed, fixture, code, and decision hashes | SPEC-001/005/006 |

A conformance test's pass/fail definition must reference an exact contract version. Conformance is necessary for comparison, but not proof of security against an open-world adversary.

## 11. Independence and contamination controls

**Roles:** Proposer (candidate design), Implementer (candidate code), Evaluator (frozen tests and scoring), Governance Approver (policy and promotion), and Auditor (evidence and lineage). A small research team may combine operational tasks, but must explicitly disclose role conflicts; claims of independent validation require genuinely separate evaluation authority.

**Controls:**

- Lock evaluator fixtures, hidden challenge sets, and primary scoring rules before candidate selection.
- Record hashes and timestamps for code, prompts, models, policy files, data splits, and configuration.
- Prevent candidate agents from editing test definitions, evaluation reports, policy versions, or promotion gates.
- Treat evaluator prompts and test data as attack surfaces; audit leakage and prompt injection in synthetic trials.
- Use independent replication to assess whether improvements survive changes in implementation, operators, and random seeds.
- Require governance sign-off for all changes to scope or approval rules; never let favorable metrics silently expand authority.

## 12. Failure taxonomy and residual-to-relay lifecycle

**Canonical failure classes:** F-ID (identity merge/split), F-EV (evidence correlation or provenance), F-IF (BCEF contradiction scope), F-AUTH (authorization bypass/replay), F-REC (recovery), F-EVAL (evaluator contamination), F-RSI (regression or unbounded adaptation), F-XFER (negative transfer), and F-GOV (authority drift).

**Lifecycle:**

`Observed event → Reproducible failure record → Scoped Security Residual → AQSI question candidate → Safe test proposal → Independent evaluation → Validated or rejected change → Governance decision → Relay record`.

A residual may remain open indefinitely. An unsuccessful improvement must not be erased. Repeated executions can accumulate evidence, but are not independent samples when they share causal sources or identical fixtures.

**Minimal residual record:**

```yaml
residual_id: "ASSI-RES-SYN-0001"
status: "open"
scenario_id: "SYN-BM002-EXAMPLE"
failure_class: "F-IF"
violated_invariant: "contradiction_must_be_hypothesis_scoped"
claim_scope: "hypothesis_H1_only"
evidence_refs: ["synthetic-source-A", "synthetic-source-B"]
reproduction: "fixture://synthetic/bm002/scoped-contradiction"
observed_effect: "unrelated_H2_rejected"
severity: "research-triage-pending"
owner_role: "evaluator"
proposed_question: "Can scoped BCEF prevent unrelated rejection?"
authorization: "synthetic-only"
```

This is a **schema illustration**, not a completed test record or an actual measured failure.

## 13. Preregistration and reproducibility package

Each hypothesis test should produce the following versioned artifacts:

```text
validation/<study-id>/
├── protocol.md                # Threat model, hypotheses, primary outcomes, stopping rules
├── preregistration.yaml       # Frozen hypotheses, splits, metrics, exclusions
├── contracts.lock             # Exact SPEC versions and hashes
├── environment.lock           # Runtime and dependency versions
├── data-manifest.json         # Synthetic generation, licenses, splits, hashes
├── baseline-manifest.json     # Baseline versions and resource budgets
├── candidate-manifest.json    # Candidate versions and resource budgets
├── tests/                     # Conformance, unit, metamorphic, regression tests
├── results/                   # Machine-readable observations, including failures
├── analysis.md                # Effect sizes, uncertainty, subgroup results
├── residuals/                 # Open, resolved, and rejected failure records
├── independence-statement.md # Evaluator access and role conflicts
└── decision.md               # Pass/fail/inconclusive; separate governance outcome
```

This directory is a **proposed future structure** and is not represented as currently present in the v0.1.0 repository. Publish enough detail to reproduce results while withholding credentials, private data, and sensitive operational targets.

## 14. Stage-gate decision record

For each gate, record:

| Field | Required content |
|---|---|
| Gate / study ID | Unique versioned identifier |
| Evidence maturity | H0–H4, with rationale |
| Frozen scope | Threat model, protected assets, data, policy versions |
| Tested claims | Exact TH IDs and contract versions |
| Baseline comparison | Resource parity, primary metrics, uncertainty |
| Safety constraints | Hard-gate status and all violations |
| Negative results | Null, adverse, and inconclusive outcomes |
| Independence | Who proposed, evaluated, and approved |
| Open residuals | Severity, owner, follow-up, explicit leftover |
| Decision | Proceed / revise / reject / inconclusive |
| Authorized next action | Separate scoped approval, if any; default none |

**Decision logic:**

- **Proceed to next research stage** only if required artifacts exist and no hard gate is violated.
- **Revise** if evidence is promising but contracts, calibration, or reproducibility are insufficient.
- **Reject candidate** if a critical invariant is violated or held-out evidence contradicts the preregistered claim.
- **Inconclusive** if statistical power, ground truth, or evaluator independence is inadequate.
- **Never equate research-stage progression with production authorization.**

## 15. Initial pilot studies (synthetic-only)

### Pilot P1 — Hypothesis-scoped BCEF and false rejection

**Targets:** TH-10–14, especially TH-11.  
**Design:** Construct pairs of synthetic identity hypotheses with partially shared evidence; introduce a contradiction that applies only to H1. Compare unscoped rejection, scoped BCEF, and an explicit unknown-state baseline.  
**Primary metrics:** unrelated-H2 false rejection, contradiction localization, calibration, and abstention.  
**Falsifier:** Scoped BCEF does not reduce false rejection under comparable error and resource budgets, or causes unacceptable false acceptance.  
**Gate:** Independent verification of provenance and ground-truth labeling.

### Pilot P2 — Transaction-bound independent authorization

**Targets:** TH-01, TH-15–18.  
**Design:** Simulate valid signatures with intentionally mismatched transaction intent, expired policy, changed recipients, and replayed approvals. Compare signature-only and model-mediated checks with independent PDP/PEP enforcement.  
**Primary metrics:** unauthorized simulated action acceptance, replay acceptance, legitimate-action denial, and recovery latency.  
**Falsifier:** The independent control plane admits an unapproved action or provides no meaningful improvement at acceptable operational cost.  
**Gate:** Any independent-enforcement bypass blocks progression.

### Pilot P3 — Temporal UTN identity ambiguity

**Targets:** TH-05–08.  
**Design:** Generate time-evolving synthetic service/entity relationships with merges, splits, key rotations, and dependent sources. Compare static matching, time-aware matching, and UTN hypothesis portfolios.  
**Primary metrics:** false merge/split, calibration, time-to-detect, provenance completeness.  
**Falsifier:** UTN offers no held-out gain or materially increases irreversible false merges.  
**Gate:** Identity inference must never be converted into authorization.

### Pilot P4 — Independent evaluation of adversarial relay

**Targets:** TH-19–26 and TH-29–30.  
**Design:** Compare single-agent review, homogeneous consensus, and separated Red/Blue/Evaluation/Governance roles on synthetic failures; then allow bounded candidate improvements under frozen hidden tests.  
**Primary metrics:** independently confirmed unique failures, leakage, regression, rollback, held-out improvement, and review cost.  
**Falsifier:** Relay fails to outperform fair baselines or improvement requires evaluator contamination or authority drift.  
**Gate:** Candidate cannot alter evaluation or approve itself.

## 16. Research dependencies and priority order

| Priority | Deliverable | Depends on | Rationale |
|---|---|---|---|
| P0 | Typed SSU, authority, evidence and residual contracts | Stage 0 | Makes outcomes interpretable |
| P0 | Independent PDP/PEP and evaluator isolation conformance | Stages 0–1 | Prevents unsafe research shortcuts |
| P1 | Pilot P1 scoped BCEF | Stage 1 | Tests a narrow, falsifiable core mechanism |
| P1 | Pilot P2 authorization | Stage 1 | Tests the non-negotiable authority boundary |
| P1 | Pilot P3 temporal identity | Stage 1 | Tests the compositional identity thesis |
| P2 | Pilot P4 adversarial relay and AQSI | BM-001–003 fixtures | Requires reliable failure records and baselines |
| P2 | Bounded RSI validation | Stage 3, independent evaluator | Requires stable residuals and rollback |
| P3 | Cross-domain independent replication | Stage 4 | Prevents premature generalization |
| Conditional | Authorized field evaluation | Independent governance review | Not a default research milestone |

The priority labels are **research sequencing**, not calendar promises or claims of implementation progress.

## 17. Publication and release readiness

For a **research-foundation v0.1.0 release**, the publication package should be evaluated on clarity and internal consistency rather than claimed experimental success:

- [ ] All twelve ASSI articles, six SPECs, five CASEs, and four EXTs are present and correctly linked.
- [ ] [README.md](README.md), [START-HERE.md](START-HERE.md), [CONTENTS.md](CONTENTS.md), [GLOSSARY.md](GLOSSARY.md), [FIGURE-INDEX.md](FIGURE-INDEX.md), [FUTURE-DIRECTIONS.md](FUTURE-DIRECTIONS.md), [OPEN-QUESTIONS.md](OPEN-QUESTIONS.md), and [TESTABLE-HYPOTHESES.md](TESTABLE-HYPOTHESES.md) agree on terminology and scope.
- [ ] Eight individual PNGs, if linked, exist under `figures/` and correspond to the figure index; composite sheets alone do not satisfy individual links.
- [ ] All proposed benchmarks and study stages are labeled *not yet run* unless verifiable results are separately supplied.
- [ ] Hypothesis and validation status is not misrepresented as empirical confirmation.
- [ ] Contracts are explicitly labeled draft/research-stage where applicable.
- [ ] No live exploit instructions, secrets, real funds, or unauthorized data are included.
- [ ] Apache-2.0 license, citation metadata, release notes, and Zenodo metadata are checked for consistency.
- [ ] All unresolved questions and known limitations remain visible.

A DOI records a versioned research artifact; it is **not** a security certification, implementation validation, or endorsement of empirical claims.

## 18. Cross-reference map

**Core papers:** [ASSI-001](docs/ASSI-001-From-Cryptographic-Validity-to-Structural-Security.md), [ASSI-004](docs/ASSI-004-UTN-and-Compositional-Identity-Intelligence.md), [ASSI-005](docs/ASSI-005-REN-and-Directional-Weak-Evidence-Intelligence.md), [ASSI-006](docs/ASSI-006-Bidirectional-Conditional-Evidence-Feedback.md), [ASSI-007](docs/ASSI-007-Structural-Authorization-and-Independent-Control-Planes.md), [ASSI-008](docs/ASSI-008-Adversarial-Security-Drives-and-Competitive-Relay.md), [ASSI-009](docs/ASSI-009-Security-Residuals-and-Validated-Recursive-Self-Improvement.md), [ASSI-011](docs/ASSI-011-Benchmark-Laboratories-and-Falsifiable-Security-Hypotheses.md), [ASSI-012](docs/ASSI-012-From-Cryptocurrency-Security-to-General-Structural-Defense.md).

**Contracts:** [SPEC-001](specs/SPEC-001-Structural-Security-Unit-Contract.md), [SPEC-002](specs/SPEC-002-Compositional-Identity-and-UTN-Contract.md), [SPEC-003](specs/SPEC-003-Bidirectional-IF-and-Evidence-Impact-Contract.md), [SPEC-004](specs/SPEC-004-Authorization-and-Safety-Control-Contract.md), [SPEC-005](specs/SPEC-005-Adversarial-Drive-and-Relay-Contract.md), [SPEC-006](specs/SPEC-006-Validated-RSI-and-Governance-Contract.md).

**Cases:** [CASE-001](cases/CASE-001-Cryptocurrency-Trust-and-Liquidity.md), [CASE-002](cases/CASE-002-UTN-On-Chain-Identity-Sandbox.md), [CASE-003](cases/CASE-003-Bidirectional-IF-and-False-Rejection.md), [CASE-004](cases/CASE-004-Compromised-Signing-Service-Defense.md), [CASE-005](cases/CASE-005-Adversarial-Drives-and-Security-RSI.md).

**Extensions:** [EXT-001](extensions/EXT-001-Multi-Agent-Adversarial-Security-Ecology.md), [EXT-002](extensions/EXT-002-Autonomous-Security-Questioning-and-Exploration.md), [EXT-003](extensions/EXT-003-Cross-Domain-Structural-Security-Transfer.md), [EXT-004](extensions/EXT-004-Open-Ended-Security-Evolution-and-Governance.md).

## 19. Collective learning and open research contributions

Contributors can add value without implementing the full ASSI system. Useful submissions include a counterexample to a contract, an alternative baseline, a reproducible synthetic fixture, an independent replication, a failed transfer, a governance-boundary analysis, or a precise reason why a hypothesis is untestable as written. Each submission should state its claim scope, evidence, negative outcomes, dependencies, and authorization limits.

**Closing principle:** *Validate the mechanism; preserve the boundary; retain the failure; separate evidence from authority.*

---

*ASSI v0.1.0 — Research Foundation. Prospective validation roadmap only; no experimental outcomes or deployment approvals are asserted.*
