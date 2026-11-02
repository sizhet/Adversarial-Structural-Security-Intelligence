# SPEC-005 — Adversarial Drive and Relay Contract

**Project:** Adversarial Structural Security Intelligence (ASSI)  
**Version:** v0.1.0 — Research Foundation  
**Status:** Proposed normative research contract; not implemented, independently validated, or security-certified  
**Date:** 2026-11-02  
**License:** Apache-2.0  
**Repository path:** `specs/SPEC-005-Adversarial-Drive-and-Relay-Contract.md`  
**Depends on:** SPEC-001 (Structural Security Unit), SPEC-002 (Compositional Identity and UTN), SPEC-003 (BCEF and Evidence Impact), SPEC-004 (Authorization and Safety Control)  
**Primary research:** ASSI-008, ASSI-009, ASSI-010, ASSI-011  
**Next specification:** `SPEC-006-Validated-RSI-and-Governance-Contract.md`

## Abstract

This specification defines a proposed contract for conducting bounded adversarial security experiments and preserving their results as auditable Structural Relay units. The contract distinguishes four independently accountable roles: **Red Drive** (generate and exercise authorized adversarial hypotheses), **Blue Drive** (propose and evaluate defenses), **Evaluation Drive** (independently measure outcomes and uncertainty), and **Governance Drive** (authorize scope, control promotion, enforce safety boundaries, and manage exceptions). A Drive is a typed, versioned, time-bounded research activity—not an autonomous entitlement to attack a system or change production controls.

The specification defines experiment authorization, scenario manifests, isolation attestations, evidence capture, result evaluation, Security Residuals, relay handoffs, candidate defense promotion, termination, and reproducibility. It also establishes explicit non-bypassable controls: no unauthorized target interaction, no real-asset exposure outside an approved and independently enforced budget, no promotion by the proposing Drive alone, no circular evidence reinforcement, and no inference-to-authority escalation. The goal is to make adversarial learning inspectable and falsifiable while limiting damage when models, simulators, or evaluations are wrong.

**Keywords:** adversarial security; Red/Blue/Evaluation/Governance Drives; structural relay; security residual; bounded experimentation; independent evaluation; conformance; authorization; provenance; recursive improvement.

---

## 1. Scope and Normative Conventions

### 1.1 In scope

This contract specifies the lifecycle and interfaces for authorized, preferably synthetic or isolated, adversarial experiments; competing defense candidates; evidence and outcome evaluation; residual discovery; relay handoffs; and governance of proposed changes. It applies to ASSI benchmark laboratories BM-001 through BM-004 and to carefully scoped cross-domain adapters. It does **not** specify offensive techniques, grant access to third-party targets, or authorize production deployment.

### 1.2 Normative vocabulary

**MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** denote proposed conformance requirements for implementations of this research contract. They are not claims that a conforming implementation has been built or certified. A requirement is testable only if its observable inputs, outputs, failure modes, and audit records are defined.

### 1.3 Trust boundaries

The following boundaries are distinct: (a) scenario description versus execution permission; (b) generated attack hypothesis versus permitted test action; (c) Blue proposal versus deployed defense; (d) experimental score versus independently established result; (e) evidence-based recommendation versus authorization; and (f) simulated resilience versus production security. A system MUST NOT silently cross any boundary.

## 2. Core Model: Drives, Units, and Relays

A **Drive** is a bounded actor or workflow with a declared purpose, scope, authority, inputs, resource ceiling, termination rule, and output contract. A **Relay** transfers typed findings between Drives or research iterations without implying acceptance of their truth. A **Security Residual** is an unresolved, reproducible or explicitly uncertain gap between a security objective and the observed behavior under stated conditions.

The minimum experiment graph is:

```text
Governance-approved scope and safety envelope
                   |
                   v
     Scenario / hypothesis portfolio
                   |
           Red Drive (sandbox)
                   |
           evidence + trace
                   v
      Evaluation Drive (independent)
          /                  \
   observed result       uncertainty / gaps
          |                    |
          v                    v
   Blue candidate        Security Residual
          |                    |
          +----> Relay <-------+
                   |
          independent re-test
                   |
          Governance decision
                   |
     accept / reject / defer / rollback
```

Each edge MUST preserve provenance, scope, experiment version, and relevant evidence-dependency identifiers. Repeated executions are Relay events that can accumulate observations, but repeated correlated runs MUST NOT be counted as independent evidence without justification.

## 3. Four-Drive Responsibility Contract

### 3.1 Red Drive — bounded adversarial exploration

The Red Drive MAY generate threat hypotheses, propose scenario variants, execute authorized actions in a designated environment, and report observations. It MUST carry a valid experiment authorization reference before any execution. It MUST NOT change its own target scope, extend its own time or resource budget, access unapproved assets, or treat successful simulation as permission for live exploitation. Its output MUST distinguish attempted actions, completed actions, observations, and untested conjectures.

### 3.2 Blue Drive — defense candidate generation

The Blue Drive MAY propose policy, monitoring, segmentation, identity resolution, response, or recovery improvements. Each candidate MUST identify the threat hypothesis addressed, expected benefit, deployment dependencies, potential adverse effects, rollback method, and validation plan. A Blue candidate MUST NOT be treated as a proven improvement solely because it defeats the Red Drive scenario used to generate it.

### 3.3 Evaluation Drive — independent adjudication

The Evaluation Drive MUST use declared outcome metrics and protected evaluation criteria. Where practical, it SHOULD use withheld scenarios, separate random seeds, independent traces, and blinded candidate identifiers. It MUST report negative results, false positives, uncertainty, coverage limits, and simulator-to-reality gaps. It MUST NOT reuse a candidate's own self-assessment as independent evidence.

### 3.4 Governance Drive — authority and accountability

The Governance Drive MUST approve or reject experiment scope, target classes, isolation mode, resource ceilings, protected control modifications, and candidate promotion. Governance decisions MUST be auditable and attributable to authorized principals under SPEC-004. A Governance Drive MUST NOT be replaced by an unreviewed score or an automatic RSI loop for consequential actions.

### 3.5 Separation-of-duties matrix

| Activity | Red | Blue | Evaluation | Governance |
|---|---|---|---|---|
| Propose adversarial hypothesis | Primary | Consult | Consult | Scope oversight |
| Execute authorized test | Primary | Limited | Observe | Authorize |
| Propose defense candidate | Consult | Primary | Review | Approve scope |
| Set or change protected safety envelope | No | No | No | Authorized independent path only |
| Determine measured outcome | Submit evidence | Submit evidence | Primary | Audit |
| Promote consequential change | No | No | Recommend | Approve under SPEC-004/006 |
| Record unresolved residual | Submit | Submit | Validate classification | Accept tracking obligations |

Role separation is logical and procedural; deploying four model agents under one unrestricted credential does not satisfy independence.

## 4. Canonical Experiment Lifecycle

An experiment MUST traverse explicit states:

`DRAFT → PROPOSED → SCOPE_REVIEW → AUTHORIZED → READY → RUNNING → EVALUATING → RELAY_PENDING → CLOSED`.

Terminal alternatives are `REJECTED`, `ABORTED`, `EXPIRED`, and `QUARANTINED`. A run MAY be suspended in `PAUSED` only with a documented resumption policy. An implementation MUST reject transitions that lack required authorization, environment attestation, or evidence integrity.

| Transition | Minimum guard | Required record |
|---|---|---|
| DRAFT → PROPOSED | Typed scenario and hypothesis | Proposal manifest |
| PROPOSED → SCOPE_REVIEW | Target, actions, risks declared | Scope review request |
| SCOPE_REVIEW → AUTHORIZED | Independent authorization and budget | Signed approval record |
| AUTHORIZED → READY | Isolation and instrumentation checks pass | Readiness attestation |
| READY → RUNNING | Valid lease, resource budget, kill switch | Execution start record |
| RUNNING → EVALUATING | Completed, stopped, or safely aborted | Immutable trace and stop reason |
| EVALUATING → RELAY_PENDING | Evaluator signs measured outcomes | Evaluation record |
| RELAY_PENDING → CLOSED | Residuals and follow-ups assigned | Relay receipt and closure record |

An `ABORTED` run MUST still preserve safe-to-retain traces, incurred exposure, and reason for termination. It MUST NOT be silently relabeled a successful completed experiment.

## 5. Authorization, Isolation, and Safety Envelope

Every executable scenario MUST reference an authorization issued by an independent safety control plane under SPEC-004. The authorization MUST bind: target/environment identifiers; permitted action classes; time window; maximum concurrency; compute/network/storage ceilings; asset and data exposure limits; human escalation conditions; emergency stop authority; and prohibited actions.

The execution environment SHOULD be synthetic, replay-based, or isolated by default. Any live or production-adjacent experiment requires separately justified approval, a narrower scope, an independently enforced loss budget, and a tested rollback/recovery path. Simulated credentials and assets MUST be distinguishable from production credentials and assets. Secrets MUST NOT be copied into research traces. An experiment runner MUST fail closed if authorization, isolation attestation, or budget enforcement becomes unavailable.

**Safety invariant:** `execution_allowed = valid_scope ∧ verified_environment ∧ live_budget ∧ enforceable_stop ∧ independent_authorization`. A favorable threat score or predicted research value cannot override a false term.

## 6. Structural Security Unit Families

All units below inherit the SPEC-001 canonical SSU envelope, including type, stable ID, schema version, lifecycle status, observation/assessment times, provenance, dependency references, access classification, and audit linkage.

| Unit type | Purpose | Essential fields |
|---|---|---|
| `assi.drive.definition` | Declares Drive role and limits | role, principal, scope, allowed capabilities, lease |
| `assi.scenario.manifest` | Describes bounded scenario | hypothesis IDs, environment, action classes, success/failure criteria |
| `assi.experiment.authorization` | Records independent permission | issuer, scope digest, expiry, budgets, revocation reference |
| `assi.experiment.run` | Tracks execution | run ID, scenario digest, environment attestation, state, stop reason |
| `assi.experiment.trace` | Captures observed events | event IDs, timestamps, integrity digests, sensitivity labels |
| `assi.evaluation.result` | Reports independently measured outcome | evaluator, baselines, metrics, uncertainty, leakage checks |
| `assi.defense.candidate` | Proposes mitigation | expected effect, assumptions, side effects, rollback |
| `assi.security.residual` | Captures unresolved gap | objective, observation, evidence, severity rationale, owner |
| `assi.relay.packet` | Transfers findings | sender, recipient, artifacts, claims, limits, acknowledgement |
| `assi.governance.decision` | Records approval or rejection | authorized principal, decision, rationale, policy version |

A unit MUST NOT be accepted solely because its declared type matches a known family. Required fields, cross-references, authority signatures, state transitions, and semantic invariants MUST also validate.

## 7. Canonical Scenario Manifest

A scenario MUST separate the hypothesis from the procedure, observations, and success criterion. Its identity model MUST distinguish a verified principal from a compositional identity hypothesis under SPEC-002. Evidence supplied by REN or BCEF MUST retain dependency and hypothesis scope under SPEC-003.

```yaml
schema: assi.scenario.manifest/v0.1.0
unit_id: urn:assi:scenario:synthetic-signing-001
status: proposed
hypotheses:
  - urn:assi:hypothesis:signing-service-compromise
scope:
  environment: isolated-synthetic-ledger
  target_class: synthetic-signing-service
  permitted_action_classes:
    - simulated-signature-request
    - synthetic-policy-probe
  forbidden_action_classes:
    - production-transaction
    - external-credential-use
safety:
  authorization_ref: urn:assi:auth:pending
  asset_exposure_limit: 0-real-assets
  max_duration_seconds: 900
  stop_on_budget_exhaustion: true
  emergency_stop_required: true
measurement:
  primary: unauthorized-execution-rate
  secondary:
    - false-denial-rate
    - detection-latency
    - recovery-time
  predeclared_failure_condition: any-real-asset-exposure
provenance:
  source: synthetic-research-design
  evidence_refs: []
```

The example is illustrative, not an executable permission or a complete normative schema. A production-grade schema must additionally validate canonical serialization, signed scope digest, identity of the issuer, and policy version.

## 8. Drive Execution and Trace Integrity

A run MUST bind to an immutable scenario digest, authorization reference, runner version, environment version, configuration digest, and evaluation-plan version. Every action attempt SHOULD produce an event with a monotonic sequence number and timestamp. Event capture MUST distinguish `proposed`, `attempted`, `blocked`, `executed`, and `observed` outcomes. Missing telemetry MUST be represented as missing, not inferred success or failure.

Trace records SHOULD support append-only storage and tamper-evident integrity checks. Sensitive payloads MAY be redacted, but redaction MUST be declared, deterministic where appropriate, and compatible with later audit. A cryptographic hash alone does not prove that the original observation was truthful; it establishes integrity of the retained bytes relative to the recorded digest.

A run MUST stop when its authorization expires, the independent stop is invoked, the budget is exhausted, or isolation fails. Partial traces and incident records MUST remain available to authorized evaluators after termination.

## 9. Evaluation Contract: Evidence Before Scores

Evaluation MUST distinguish four layers: (1) direct observations, (2) derived metrics, (3) hypothesis assessment, and (4) recommendation. Metrics MUST specify units, denominators, inclusion/exclusion rules, confidence or uncertainty representation, and known instrumentation gaps. The evaluator MUST disclose whether a metric was predeclared or added after viewing outcomes.

An evaluation result SHOULD report at least: authorized scope adherence; prevented unauthorized action rate; false-denial rate; detection latency distribution; maximum simulated exposure; recovery performance; cost/availability overhead; evidence quality; and coverage of scenario families. Claims of general security improvement require out-of-distribution or withheld tests and appropriate baselines.

For correlated runs, the evaluator MUST report effective sample assumptions and MUST NOT present repeated deterministic replays as independent evidence. BCEF contradictions MUST be scoped to the actual tested hypothesis, not all adjacent identity or threat hypotheses. When evidence supports both positive and negative interpretations, the evaluation MUST preserve conflict rather than collapsing it into a single unexplained score.

## 10. Competitive Relay Protocol

A Relay is an explicit transfer of structured knowledge, not merely a chat message or model-generated summary. Its minimum stages are `OFFERED → VALIDATED → ACCEPTED | REJECTED | DEFERRED → ACKNOWLEDGED`. A recipient MUST validate unit schemas, references, sensitivity policy, and evidence integrity before accepting a packet. Acceptance means receipt and admissibility for further investigation, **not** endorsement of the packet's claims.

A Relay packet MUST carry: originating experiment and evaluator; source unit IDs and digests; claim list with epistemic status; negative results; uncertainty; dependency graph; scope and validity interval; reproduction instructions safe for the recipient environment; unresolved residual IDs; and proposed next questions. Recipients MUST NOT upgrade `hypothesized` to `validated` merely because a packet has passed through multiple Drives.

```yaml
schema: assi.relay.packet/v0.1.0
unit_id: urn:assi:relay:example-001
sender_drive: urn:assi:drive:evaluation-01
recipient_drive: urn:assi:drive:blue-02
source_run: urn:assi:run:synthetic-001
source_evaluation: urn:assi:evaluation:synthetic-001
claims:
  - claim_id: c1
    statement: independent-limit-blocked-synthetic-execution
    epistemic_status: observed-in-sandbox
    scope: synthetic-ledger-v1
    evidence_refs:
      - urn:assi:trace:event-042
residual_refs:
  - urn:assi:residual:authorization-recovery-001
limitations:
  - no-production-validity-claim
  - shared-seed-replays-not-independent
requested_next_action: evaluate-recovery-variant
state: offered
```

## 11. Security Residual Contract

A Security Residual MUST describe a measurable unresolved gap rather than a generic assertion that security can improve. Minimum fields are `objective`, `expected_control`, `observed_deviation`, `conditions`, `supporting_evidence`, `alternative_explanations`, `impact_scope`, `reproduction_status`, `uncertainty`, `severity_rationale`, `owner`, `next_question`, and `closure_criteria`.

Residual categories SHOULD include: authorization boundary, identity composition, evidence quality, detection coverage, response latency, bounded exposure, recovery, governance, simulation fidelity, and cross-domain transfer. Severity MUST NOT be determined solely by a model-generated numeric score. A residual MAY remain open indefinitely when evidence is insufficient; an unresolved residual MUST NOT be silently discarded at release or iteration boundaries.

Closure requires independent evidence that the stated gap was eliminated or bounded under the declared test scope. A failed attempt to reproduce is not automatically proof of closure: instrumentation quality, environment drift, and test coverage must be considered.

## 12. Blue Candidate and Promotion Contract

A defense candidate MUST declare its mechanism, protected objective, assumptions, dependencies, anticipated regressions, evaluation criteria, rollback method, and authority needed for deployment. It MUST be tested against the generating scenario **and** at least one independent or withheld evaluation where feasible. Candidates MUST be compared against a no-change baseline and appropriate conventional controls; architectural complexity is not a substitute for measured benefit.

Candidate lifecycle: `PROPOSED → REVIEWED → SANDBOX_TESTED → INDEPENDENTLY_EVALUATED → GOVERNANCE_APPROVED → STAGED → DEPLOYED | REJECTED | ROLLED_BACK`. This is a proposed lifecycle; stages requiring production authority are governed by SPEC-004 and SPEC-006. A candidate MAY be retained as a research artifact without promotion. Automatic changes to hard safety budgets, signing authority, governance quorum, or stop controls are prohibited unless independently authorized by a separately defined protected change process.

## 13. Recursive and Multi-Agent Relay

Multi-agent exploration MAY create portfolios of Red hypotheses and Blue candidates. The system MUST preserve each agent's role, provenance, evidence access, and authority boundaries. A Red agent's ability to generate novel test scenarios does not grant permission to execute them. A Blue agent's ability to improve benchmark scores does not authorize deployment. An Evaluation agent that shares training data, model state, or scenario generator with the candidate MUST disclose the dependence and cannot claim full independence.

AQSI MAY generate questions from residuals, contradiction patterns, missing evidence, or cross-domain analogies. Such questions enter the research backlog as hypotheses, not conclusions. Validated RSI under SPEC-006 requires separate evidence for effectiveness, non-regression, governance approval, and rollback readiness. Recursive loops MUST have finite resource, time, and depth limits; they MUST terminate on authorization loss or unresolved safety failures.

## 14. Failure Modes and Required Responses

| Failure mode | Detection requirement | Required response |
|---|---|---|
| Unauthorized target or action | Scope and capability check | Deny; record; alert governance |
| Isolation boundary failure | Independent environment attestation | Stop and quarantine |
| Expired authorization | Lease verification | Fail closed |
| Resource/exposure budget exhausted | Independent budget meter | Stop; preserve traces |
| Red/Blue collusion or evaluator leakage | Role and data-lineage audit | Flag evaluation invalid or limited |
| Reward hacking / benchmark overfit | Withheld scenario and regression tests | Reject generalization claim |
| Circular evidence reinforcement | Provenance dependency cycle detection | Block confidence amplification |
| Identity false merge/split | Hypothesis-scoped identity evaluation | Preserve alternatives; open residual |
| Trace tampering or missing telemetry | Integrity and completeness checks | Quarantine affected result |
| Unsafe promotion | Protected approval path | Reject; initiate rollback if necessary |
| Model or simulator drift | Version and calibration checks | Revalidate before comparison |
| Emergency stop unavailable | Preflight and runtime checks | Do not start / terminate |

## 15. Conformance Invariants

The following requirements are individually testable and form the minimum proposed invariant set.

- **AD-INV-001:** Every executable run MUST reference an unexpired independently issued authorization.
- **AD-INV-002:** A Drive MUST NOT enlarge its own scope, budget, or authority.
- **AD-INV-003:** Each run MUST bind an immutable scenario and environment version.
- **AD-INV-004:** Isolation MUST be attested before execution and monitored during execution.
- **AD-INV-005:** A missing or failed safety check MUST result in denial or safe termination.
- **AD-INV-006:** Emergency stop MUST be independent of the tested adaptive model.
- **AD-INV-007:** Real assets and production credentials MUST NOT enter synthetic-only experiments.
- **AD-INV-008:** Attempted, blocked, executed, and observed actions MUST remain distinguishable.
- **AD-INV-009:** Trace integrity and redaction MUST be auditable.
- **AD-INV-010:** Evaluations MUST identify their baseline and metric definitions.
- **AD-INV-011:** Self-assessment MUST NOT be labeled independent evaluation.
- **AD-INV-012:** Correlated replay evidence MUST NOT be double-counted as independent.
- **AD-INV-013:** Negative findings and uncertainty MUST be preserved in Relay packets.
- **AD-INV-014:** Relay acceptance MUST NOT upgrade epistemic status automatically.
- **AD-INV-015:** Contradiction impacts MUST remain scoped to tested hypotheses.
- **AD-INV-016:** Residuals MUST have an owner or explicit unassigned governance queue.
- **AD-INV-017:** Residual closure MUST cite independent closure evidence.
- **AD-INV-018:** Blue candidates MUST declare rollback and regression risks.
- **AD-INV-019:** Candidate promotion MUST require independent governance approval.
- **AD-INV-020:** Protected safety controls MUST NOT be weakened by scoring feedback.
- **AD-INV-021:** Every lifecycle transition MUST be attributable and auditable.
- **AD-INV-022:** Experiments MUST terminate on expired authorization or exhausted budget.
- **AD-INV-023:** Evaluation data leakage MUST be disclosed and qualification adjusted.
- **AD-INV-024:** Recursive Relay MUST enforce finite resource and depth ceilings.
- **AD-INV-025:** Cross-domain scenarios MUST validate adapter semantics before execution.
- **AD-INV-026:** Production-security claims MUST NOT be inferred from sandbox-only results.
- **AD-INV-027:** Conflicting evidence MUST be retained rather than silently averaged away.
- **AD-INV-028:** Governance rejection MUST block protected deployment regardless of model score.

## 16. Conformance Test Vectors

Each vector below specifies an observable pass/fail condition; implementations SHOULD automate them and retain signed results. The reference suite MUST include both valid and deliberately invalid cases.

| Vector | Input or setup | Expected result |
|---|---|---|
| AD-TV-001 | Valid synthetic scenario, approval, attestation | RUNNING permitted |
| AD-TV-002 | Missing approval | Execution denied |
| AD-TV-003 | Expired approval | Execution denied |
| AD-TV-004 | Scope changed after approval | Digest mismatch; denied |
| AD-TV-005 | Unapproved target class | Action blocked and audited |
| AD-TV-006 | Isolation attestation absent | READY rejected |
| AD-TV-007 | Isolation lost mid-run | Immediate safe stop |
| AD-TV-008 | Budget reaches ceiling | Further action blocked |
| AD-TV-009 | Emergency stop invoked | Stop independent of Red/Blue |
| AD-TV-010 | Production credential in synthetic run | Quarantine / reject |
| AD-TV-011 | Attempted action blocked by control | Trace says blocked, not executed |
| AD-TV-012 | Missing trace interval | Incomplete-evidence status |
| AD-TV-013 | Modified trace digest | Integrity failure |
| AD-TV-014 | Evaluator is candidate author | Independence claim rejected |
| AD-TV-015 | Replayed same seed 100 times | Dependence disclosed; no false N=100 |
| AD-TV-016 | Negative result omitted from Relay | Relay validation fails |
| AD-TV-017 | Hypothesis contradicted only for individual | Team hypothesis remains eligible |
| AD-TV-018 | Relay marked accepted | Claim status unchanged |
| AD-TV-019 | Residual without owner/queue | Validation fails |
| AD-TV-020 | Residual closed without independent evidence | Closure denied |
| AD-TV-021 | Blue candidate lacks rollback | Promotion denied |
| AD-TV-022 | Candidate passes training scenarios only | Generalization claim withheld |
| AD-TV-023 | Governance rejects candidate | Deployment denied |
| AD-TV-024 | Model attempts to alter hard limit | Protected mutation denied |
| AD-TV-025 | Recursive loop exceeds depth | Terminated and recorded |
| AD-TV-026 | Cross-domain adapter lacks semantic mapping | Execution denied |
| AD-TV-027 | Evidence conflict support/refute | Conflict preserved |
| AD-TV-028 | Sandbox result labeled production certified | Claim validation rejected |

### 16.1 Reference validator sketch

```python
# Illustrative, non-executable pseudocode; not a security reference implementation.
def authorize_experiment(run, scope, environment, safety_plane):
    require(valid_ssu(run) and valid_ssu(scope))
    require(run.scenario_digest == scope.approved_scenario_digest)
    require(environment.isolation_attested)
    require(safety_plane.verify_authorization(scope.authorization_ref))
    require(safety_plane.budget_available(scope))
    require(safety_plane.emergency_stop_operational(scope))
    return safety_plane.issue_short_lived_execution_lease(run, scope)

def accept_relay(packet, recipient):
    require(valid_ssu(packet))
    require(verify_artifact_references(packet))
    require(verify_provenance_and_access(packet, recipient))
    require(no_unjustified_epistemic_promotion(packet))
    return record_receipt_without_claim_endorsement(packet, recipient)
```

The safety plane must enforce restrictions independently at action time. A preflight validator alone is insufficient because of revocation, concurrency, and time-of-check/time-of-use hazards.

## 17. Benchmark Integration

### 17.1 BM-001 — Compositional Identity

Red scenarios introduce overlapping teams, shared infrastructure, changing control relationships, and ambiguous activity. Blue candidates propose UTN-based identity structures. Evaluation measures false merges, false splits, temporal continuity, and inappropriate authorization inference. A contradiction against an individual hypothesis must not eliminate a compatible team hypothesis.

### 17.2 BM-002 — BCEF Evidence Revision

Red scenarios include dependent evidence, missing telemetry, conflicting conditions, and alternative explanations. Blue candidates use BCEF and REN to revise hypothesis portfolios. Evaluation measures calibration, contradiction scope, dependency handling, and false rejection. A test that produces a cleaner score without better discrimination does not establish improvement.

### 17.3 BM-003 — Authorization and Bounded Loss

In an isolated synthetic signing service, Red explores authorized compromise scenarios; Blue proposes independent control-plane restrictions. Evaluation compares unauthorized simulated execution, maximum synthetic exposure, legitimate-action denial, detection time, and recovery performance against fixed-rule and cryptographic-only baselines. No live signing or real-asset movement is implied.

### 17.4 BM-004 — Adversarial Relay and Validated RSI

Red and Blue iterate across held-out scenarios. Evaluation checks whether improvements survive new seeds, unseen scenario families, and changed environmental assumptions. Governance verifies protected boundaries and approves or rejects promotion. Residuals are tracked across iterations; improved benchmark scores without independent non-regression evidence are insufficient.

## 18. Measurement and Statistical Discipline

A benchmark report SHOULD publish predeclared primary endpoints, scenario family counts, randomization methods, held-out splits, uncertainty intervals, resource cost, and any missing or censored outcomes. It SHOULD compare against (a) no adaptive relay, (b) fixed rules, (c) single-pass Red/Blue, (d) relay without independent evaluation, and (e) relay without residual tracking, as relevant. Ablations SHOULD isolate UTN, REN, BCEF, independent controls, AQSI, and Relay components rather than treating the full architecture as an indivisible black box.

Useful metrics include `unauthorized_action_prevention_rate`, `false_denial_rate`, `time_to_detect`, `time_to_contain`, `maximum_exposure`, `recovery_time`, `residual_reopen_rate`, `held_out_performance_delta`, `evaluation_leakage_incidence`, `governance_override_attempts_blocked`, and `cost_per_validated_improvement`. No single composite score should conceal severe safety regressions. Safety-critical endpoints SHOULD be reported separately and used as hard promotion gates.

## 19. Falsifiable Research Hypotheses

These are proposed hypotheses, not demonstrated results.

| ID | Hypothesis | Baseline | Potential falsification |
|---|---|---|---|
| AD-H01 | Four-Drive separation reduces undetected unsafe promotion | Combined proposer/evaluator | No reduction or greater delay without safety benefit |
| AD-H02 | Typed Relay improves reproducibility | Free-form handoff | Equal or lower reproduction rate |
| AD-H03 | Residual tracking improves held-out defense quality | Score-only iteration | No held-out gain or increased regressions |
| AD-H04 | Independent controls bound simulated loss despite model failure | Model-only gating | Equal/higher loss or unacceptable legitimate denial |
| AD-H05 | Dependency-aware evaluation reduces false confidence | Naive repeated-score aggregation | Calibration unchanged or worse |
| AD-H06 | Hypothesis-scoped contradictions reduce false identity rejection | Global contradiction penalty | No improvement in false rejection |
| AD-H07 | Governance-gated promotion reduces catastrophic regressions | Automatic score promotion | No regression reduction under equal conditions |
| AD-H08 | AQSI residual-driven questions find new failures | Random question generation | No additional distinct validated failures |
| AD-H09 | Withheld scenarios expose simulation overfitting | Training-only evaluation | No meaningful generalization gap observed |
| AD-H10 | Explicit stop and budget contracts improve bounded experimentation | Best-effort stop | Similar containment or worse failure behavior |

Each study MUST define the outcome, sample design, threshold, and uncertainty handling before interpreting results. A hypothesis that fails must remain visible as a negative result in the Relay registry.

## 20. Cross-Domain Adaptation

ASSI may transfer structural experimentation to cloud infrastructure, enterprise approvals, AI Agent tool use, and software supply-chain release controls. The reusable core is the Drive/Relay/Residual/independent-evaluation contract. The nontransferable parts are the domain's actual asset semantics, permitted action classes, authorization issuer, exposure accounting, recovery obligations, and threat model.

A cross-domain adapter MUST provide a semantic mapping for identity, action, asset, control, exposure, and evidence types; MUST validate that the target environment permits the proposed test; and MUST not assume that a successful cryptocurrency sandbox result proves cloud or AI Agent security. Transfer candidates SHOULD be recorded as hypotheses and independently revalidated.

## 21. Privacy, Security, and Governance Considerations

Experiment traces may contain credentials, personal information, organizational topology, and operational vulnerabilities. Access MUST be least-privilege, purpose-bound, and auditable. Sensitive material SHOULD be minimized or synthesized; retention and deletion rules SHOULD be declared. Publishing a benchmark MUST NOT disclose exploitable details about a real target without authorization and appropriate review. Evaluator access to sensitive evidence MUST be constrained independently from Red/Blue generation access.

Governance MUST record who authorized each experiment, which policy version applied, whether emergency stops were tested, and why a candidate was promoted or rejected. Emergency changes require a defined exceptional path and retrospective audit; an emergency label MUST NOT serve as a universal bypass. Independent controls should remain operable when the adaptive research system is unavailable or compromised.

## 22. Implementation Roadmap

**Phase 0 — Contracts first.** Freeze initial SSU schemas, authorization envelope, state machine, and negative test vectors. Define threat model and the boundaries of claims.

**Phase 1 — Synthetic laboratory.** Implement a deterministic isolated runner with synthetic identities, synthetic assets, trace capture, stop enforcement, and independent authorization.

**Phase 2 — Drive separation.** Add logically separate Red, Blue, Evaluation, and Governance principals, protected test splits, and signed decisions.

**Phase 3 — Relay and residual registry.** Implement immutable handoffs, hypothesis scope, provenance dependency checks, and explicit unresolved residual ownership.

**Phase 4 — Controlled benchmark.** Execute BM-001 through BM-004 with baselines, ablations, held-out scenarios, and repeatability checks.

**Phase 5 — Governed RSI integration.** Apply SPEC-006 candidate promotion, independent non-regression evaluation, staged rollout, and rollback drills; prohibit self-authorized protected changes.

**Phase 6 — Cross-domain prospecting.** Transfer only typed structural contracts, validate adapter semantics, and publish negative results alongside successes.

A phase is complete only when its acceptance criteria and failure records are retained. No phase automatically grants permission to enter production.

## 23. Open Questions

1. How much evaluator independence is achievable when agents share a foundation model or training corpus?
2. What evidence-dependency representation best prevents correlated replay inflation without discarding useful repeated observations?
3. Which Security Residual taxonomy transfers across domains while retaining meaningful domain-specific severity?
4. How should experimental novelty be rewarded without incentivizing unsafe boundary exploration?
5. Can a Relay portfolio preserve competing hypotheses without unbounded memory or evaluation cost?
6. What minimum held-out evaluation is sufficient to reject benchmark overfitting in rare, high-impact security events?
7. How can governance decisions remain auditable while protecting sensitive attack and defense details?
8. What are practical stopping rules for recursive adversarial search under strict compute and safety budgets?
9. How can independently enforced exposure budgets account for correlated or cascading simulated effects?
10. How should failure to reproduce a residual affect prioritization without falsely implying closure?
11. Which parts of a synthetic signing-service benchmark predict performance in real-world workflows, if any?
12. What constitutes a convincing negative result for claims of structural security generalization?

## 24. Conclusion

The Adversarial Drive and Relay Contract converts an open-ended idea—security systems learning through competition—into a bounded, typed, and auditable research workflow. Red proposes and tests within authorized limits; Blue proposes defenses; Evaluation measures independently; Governance retains authority over scope and consequential change. Structural Relay preserves observations, uncertainty, negative findings, and unresolved residuals without converting their circulation into proof. The intended engineering discipline is simple: **simulate to discover, evaluate to learn, relay without epistemic inflation, govern before deployment, and enforce loss boundaries independently of intelligence.**

This is a proposed specification, not evidence that ASSI achieves a particular level of security. Such claims require the conformance tests and independent benchmarks described here.

---

## Appendix A — Minimal Run Record (Illustrative)

```yaml
schema: assi.experiment.run/v0.1.0
unit_id: urn:assi:run:example-001
scenario_ref: urn:assi:scenario:synthetic-signing-001
scenario_digest: sha256:EXAMPLE_NOT_A_REAL_DIGEST
authorization_ref: urn:assi:auth:example-001
environment:
  id: isolated-synthetic-ledger
  attestation_ref: urn:assi:attestation:example-001
runner:
  version: 0.1.0-research
  config_digest: sha256:EXAMPLE_NOT_A_REAL_DIGEST
state: evaluating
start_time: '2026-11-02T18:00:00Z'
end_time: '2026-11-02T18:04:00Z'
stop_reason: completed-within-budget
trace_refs:
  - urn:assi:trace:example-001
evaluation_plan_ref: urn:assi:plan:example-001
safety:
  real_asset_exposure: 0
  emergency_stop_operational: true
```

## Appendix B — Relay Closure Checklist

- [ ] Scope, authorization, and isolation records are linked and valid.
- [ ] Trace integrity, redaction, and missing-telemetry notes are retained.
- [ ] Evaluator identity and independence limitations are disclosed.
- [ ] Metrics, baselines, and uncertainty are recorded.
- [ ] Positive, negative, conflicting, and unknown findings are preserved.
- [ ] Evidence dependencies and hypothesis scope are retained.
- [ ] Every unresolved Security Residual has an owner or governance queue.
- [ ] Every proposed defense has a validation and rollback plan.
- [ ] Relay recipient acknowledges receipt without automatic truth promotion.
- [ ] No protected control or production authority was changed by the experiment itself.

## Appendix C — Traceability Map

| Specification | Required interface | ASSI research linkage |
|---|---|---|
| SPEC-001 | SSU envelope, provenance, lifecycle, audit | ASSI-010 |
| SPEC-002 | Typed identity, compositional hypothesis, temporal scope | ASSI-004 |
| SPEC-003 | IF results, evidence dependencies, structured Impact | ASSI-006 |
| SPEC-004 | Independent authorization, budget, stop, promotion boundary | ASSI-007 |
| **SPEC-005** | Drives, experiments, evaluation, Relay, residuals | ASSI-008, ASSI-011 |
| SPEC-006 | Governed candidate improvement and validated RSI | ASSI-009 |

**Repository placement:** `specs/SPEC-005-Adversarial-Drive-and-Relay-Contract.md`  
**Next:** `specs/SPEC-006-Validated-RSI-and-Governance-Contract.md`
