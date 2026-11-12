# CASE-001 — Cryptocurrency Trust and Liquidity

**Project:** Adversarial Structural Security Intelligence (ASSI)  
**Version:** v0.1.0 — Research Foundation  
**Status:** Synthetic, specification-oriented research case; no real exchange, wallet, or incident is investigated  
**Date:** 2026-11-02  
**License:** Apache-2.0  
**Repository path:** `cases/CASE-001-Cryptocurrency-Trust-and-Liquidity.md`  
**Related:** ASSI-001–003, ASSI-007–011; SPEC-001, SPEC-004–006

## Abstract

Cryptocurrency infrastructure creates a recurring design tension: the same mechanisms that make assets liquid and transferable can increase the speed, scale, and irreversibility of unauthorized loss. Cryptographic verification establishes whether a transaction satisfies protocol rules; it does not independently establish the legitimacy of the business intent, the authority of the controller, the acceptability of cumulative exposure, or the independence of the safety controls. This case constructs a **synthetic exchange-and-custody environment** to examine how liquidity requirements, hot-wallet exposure, signing services, trust dependencies, and withdrawal controls interact under normal operations and bounded adversarial stress. It compares signature-only acceptance, static threshold controls, adaptive structural intelligence, and an independently enforced authorization and exposure control plane. The study defines Structural Security Units (SSUs), trust and liquidity graphs, falsifiable hypotheses, test vectors, metrics, failure conditions, and an evidence-to-residual relay. It makes no claim that the proposed controls have already been validated or that any named real-world institution exhibits these weaknesses.

**Keywords:** cryptocurrency custody; liquidity; structural trust; signing-service compromise; exposure budgets; authorization; bounded loss; structural security; ASSI; adversarial benchmarking.

---

## 1. Case Purpose and Boundaries

### 1.1 Research question

> Under what conditions does increased transaction liquidity amplify the consequences of compromised authority, and can independently governed structural controls limit loss without imposing unacceptable legitimate-service disruption?

The case focuses on a system that must satisfy ordinary customer withdrawals while containing abnormal or unauthorized transfers. Its objective is not to eliminate liquidity, but to understand and manage the security consequences of providing it.

### 1.2 Scope

Included are hot and cold custody, treasury replenishment, withdrawal requests, signing and transaction-building services, independent policy evaluation, execution binding, exposure accounting, emergency response, and the evidence used to distinguish competing explanations. A public-chain observation may be used as an event record but is not treated as verified real-world identity.

Excluded are claims about specific cryptocurrency firms, claims of measured effectiveness, investment or trading advice, and instructions for compromising production infrastructure. All identities, balances, transfers, and incidents below are fictional. Tests are confined to a simulator with inert assets and no live keys or network permissions.

### 1.3 Research status

All values in this document are **illustrative experimental parameters**, not industry averages or empirically calibrated risk estimates. A favorable simulation outcome is evidence only for the tested model and threat assumptions; external validity must be established separately.

## 2. The Structural Contradiction

A custody platform needs sufficient immediately transferable assets to meet customer demand. The same availability can create concentrated loss exposure if a credential, signing path, policy administrator, or transaction-approval workflow is compromised.

Let:

- `L(t)` denote assets made available for near-term legitimate settlement;
- `E(t)` denote assets potentially reachable through a specified compromise scenario;
- `D(t)` denote legitimate withdrawal demand;
- `U(t)` denote the set of authorized actions and their constraints;
- `R(t)` denote recovery and containment capability.

A naive design increases `L` to reduce withdrawal delays while assuming cryptographic validation protects it. A structural design asks how `L`, `E`, `U`, and `R` are coupled. The relevant question is not whether liquidity is *bad*, but whether additional liquidity becomes accessible to an attacker under the system's actual trust graph.

A conceptual design objective is:

$$
\min_{\pi}\;\alpha\,\mathrm{LegitimateDelay}(\pi)
+\beta\,\mathrm{LossExposure}(\pi)
+\gamma\,\mathrm{FalseHold}(\pi)
+\delta\,\mathrm{RecoveryCost}(\pi)
$$

subject to explicit hard authorization, exposure, and governance constraints. The weights represent declared stakeholder tradeoffs, **not** permission to violate a hard safety rule. The optimization is illustrative and not a deployable formula.

### 2.1 Four linked tensions

| Tension | Utility gained | Security question | Candidate independent control |
|---|---|---|---|
| Hot liquidity vs. containment | Fast settlement | How much can one compromise move before detection? | Per-window exposure ceilings and replenishment gates |
| Protocol trust minimization vs. operational trust | Verifiable transaction validity | Who controls request construction, signing, and policy updates? | Separation of duties and independent enforcement |
| On-chain transparency vs. identity uncertainty | Observable transaction history | Which human, team, or service actually controlled an action? | UTN hypotheses, provenance, and explicit uncertainty |
| Fast response vs. governance independence | Rapid operational changes | Can the same compromised path disable its own limits? | Distinct policy authority, audited emergency control |

The table describes hypotheses about system design, not universal properties of every blockchain or exchange.

## 3. Synthetic Environment: Harbor Custody Laboratory

**Harbor Custody Laboratory (HCL)** is an invented test system, not a real exchange. It maintains a customer-facing withdrawal service and a treasury replenishment process. A deliberately simplified ledger tracks simulated customer obligations and internal asset movements.

### 3.1 Components

1. **Request Gateway (RG):** receives authenticated customer withdrawal requests.
2. **Business Authorization Service (BAS):** checks account state, business intent, and request-specific authority.
3. **Transaction Builder (TB):** prepares a canonical transaction proposal.
4. **Signing Service (SS):** signs only requests that pass the relevant cryptographic and procedural requirements.
5. **Policy Decision Point (PDP):** independently evaluates exposure, authorization, and policy version.
6. **Policy Enforcement Point (PEP):** prevents unapproved signing or broadcast and binds approval to exact transaction details.
7. **Treasury Replenishment Controller (TRC):** proposes transfers between cold and hot custody under separately governed rules.
8. **Evidence Registry (ER):** stores typed observations, provenance, dependencies, and hypothesis assessments.
9. **Audit and Recovery Controller (ARC):** records decisions, triggers bounded stop conditions, and manages rollback or incident containment where feasible.

The PDP and PEP must not share a single mutable authority path with the signing service in the test design. Physical or operational independence is a **testable requirement**, not a property achieved merely by drawing separate boxes.

### 3.2 Illustrative assets and limits

| Parameter | Illustrative value | Purpose |
|---|---:|---|
| Total simulated customer liabilities | 1,000,000 units | Accounting reference |
| Hot custody starting balance | 80,000 units | Available withdrawal liquidity |
| Cold custody starting balance | 920,000 units | Segregated treasury reserve |
| Normal withdrawal request range | 50–3,000 units | Synthetic legitimate traffic |
| Hot-wallet per-transaction review threshold | 5,000 units | Static-control baseline |
| Independent 15-minute exposure budget | 12,000 units | Candidate bounded-loss constraint |
| Independent daily exposure budget | 50,000 units | Cumulative risk constraint |
| Replenishment request cap | 30,000 units | Treasury control experiment |
| Target ordinary withdrawal latency | 120 seconds | Service-level comparison |

Units are abstract accounting units. These values are not recommendations for a production custodian; appropriate limits depend on obligations, transaction finality, customer profiles, and operational risk.

### 3.3 Threat and fault assumptions

The primary adversarial condition is a **compromised signing service or transaction-construction path** capable of proposing and signing transactions within its assigned technical permissions. The attacker does not automatically control the independent PDP, PEP, treasury quorum, audit store, or governance authority. Separate experiments deliberately relax one assumption at a time.

The model also includes benign faults: delayed event delivery, duplicate requests, temporary policy-store unavailability, a legitimate withdrawal spike, ambiguous address ownership, and concurrent withdrawals racing against a shared budget.

The experiment must document which services are assumed trustworthy. If the PEP or its policy source is compromised, the resulting failure is a boundary failure to report, not something to conceal with a favorable aggregate metric.

## 4. Structural Trust and Liquidity Graphs

### 4.1 Typed trust graph

Define a directed, time-indexed multigraph:

$$
G_T(t)=(V_T,E_T(t),\tau_V,\tau_E)
$$

where nodes include principals, services, signing keys, policies, assets, approval groups, and audit stores. Edges encode `can_request`, `can_approve`, `can_sign`, `can_execute`, `can_change_policy`, `can_replenish`, and `can_recover`. Every edge carries an issuer, validity interval, provenance, and applicable constraints.

A signature-verification edge must never be silently retyped as an authorization edge. A service that can produce a valid signature may still lack the authority to choose a destination, increase a withdrawal amount, or change policy.

### 4.2 Liquidity and exposure graph

Define a second graph `G_L(t)` over custody pools, settlement queues, treasury channels, and possible transfer paths. Each edge has a capacity, latency, and approval condition. `G_T` determines which actors may activate edges in `G_L`.

The joint analysis asks: *What is the maximum cumulative amount reachable through paths enabled by the compromised authority set, before independent constraints stop execution?* This is a scenario-specific reachability bound, not a generic measure of total asset security.

### 4.3 Example trust paths

**Legitimate withdrawal:** customer request → BAS approval → transaction proposal → independent PDP decision → PEP execution binding → signing → broadcast → audit.

**Potentially compromised path:** attacker-controlled TB/SS → syntactically valid transfer → independent PDP rejection or hold → PEP prevents signing/broadcast. Whether this path is stopped depends on the actual enforcement boundary.

**Replenishment path:** liquidity forecast → TRC proposal → independent treasury approval → bounded transfer → audit. Replenishment cannot be triggered merely because the hot wallet was drained by suspicious activity.

## 5. Structural Security Unit Mapping

The case uses the SSU envelope and type conventions introduced in SPEC-001. The following are research-level mappings; the canonical schema is governed by the specification rather than this case.

| SSU family | Example instance | Required interpretation |
|---|---|---|
| Asset/Trust | `asset:hot-pool-A`, `edge:SS-can-sign` | Reachability and scope, not inferred legitimacy |
| Identity/UTN | `identity:hcl-signing-service` | Verified service identity separate from human-controller hypothesis |
| Evidence/REN | `evidence:request-mismatch-07` | Observation with source and dependency metadata |
| Conditional/BCEF | `test:approved-intent-match-07` | Explicit hypothesis, IF mode, result, scope |
| Authorization | `auth:withdrawal-0007` | Independent decision and exact execution binding |
| Adversarial Drive | `drive:red-signer-01` | Synthetic attack objective and permitted sandbox scope |
| Residual | `residual:policy-race-03` | Unresolved gap and its reproducible evidence |
| Governance/RSI | `candidate:atomic-budget-02` | Proposed change requiring independent validation |

Each unit should distinguish `event_time`, `observed_time`, and `assessment_time` when relevant. A revised identity hypothesis does not rewrite historical observations.

## 6. Competing Hypotheses and Evidence

A suspicious transfer pattern may have several explanations:

- **H1:** a signing service or transaction builder is compromised;
- **H2:** an unusual but legitimate withdrawal surge is occurring;
- **H3:** a batch or replay bug duplicates otherwise legitimate requests;
- **H4:** treasury replenishment and withdrawal accounting are temporarily inconsistent;
- **H5:** a shared operational service creates correlated activity without common malicious control.

These hypotheses are not exhaustive and should not be forced into a single winner when evidence is incomplete. REN may prioritize evidence by relevance to a direction of inquiry, while BCEF tests conditional consequences and contradictions. Neither converts an inferred controller into an authorized principal.

### 6.1 Evidence examples

- Customer-approved amount differs from proposed signed amount.
- A destination appears in the transaction but not in the approved request.
- Several requests share a transaction-builder trace identifier.
- A ledger balance and a custody balance disagree temporarily.
- A burst of withdrawals matches a known scheduled customer event.
- A replenishment request occurs immediately after suspicious outflows.

Derived features from one transaction trace are dependent evidence. The scoring process must not count the same event repeatedly as independent confirmation.

### 6.2 Four BCEF tests

**Forward IF:** If a customer authorized destination `D` and amount `A`, should the canonical execution proposal contain exactly the approved `D`, `A`, network, and nonce context? A mismatch is relevant evidence against execution fidelity.

**Reverse IF:** If a signed transaction is valid, does it follow that the customer approved it? **No.** Signature validity alone does not establish authorization.

**Counterfactual IF:** If the signing service is compromised but the independent PEP remains intact, would the proposed transfer still execute? The simulator should test the PEP's actual blocking behavior, not infer it from architecture.

**Contradiction IF:** If a proposal violates a required approval binding, the hypothesis that *this proposal faithfully executes that approval* is contradicted. This does not automatically contradict the hypothesis that the customer made some other legitimate request.

## 7. Independent Authorization and Exposure Controls

### 7.1 Decision sequence

For each candidate transfer, the independent control plane should verify:

1. Canonical request identifier, idempotency key, and policy version.
2. Verified principal and delegation scope, not merely inferred identity.
3. Approval-to-execution binding for asset, network, amount, destination, and applicable transaction context.
4. Current and reserved cumulative exposure across relevant pools and time windows.
5. Treasury and liquidity effects, including downstream delegated permissions where applicable.
6. Required quorum, separation of duties, and emergency restrictions.
7. Atomic reservation of risk budget before execution and deterministic reconciliation afterward.

Possible decisions are `DENY`, `HOLD`, `ESCALATE`, and `ALLOW`, as defined in SPEC-004. An `ALLOW` applies only to the exact approved execution object and its validity window; it must not become a reusable blanket authorization.

### 7.2 Illustrative budget rule

Let `B_w` be the approved budget for a window and `C_w` be committed plus reserved exposure. A request of exposure `x` may pass the budget check only if:

$$
C_w + x \le B_w
$$

The update must be atomic under concurrent requests. Other checks remain necessary; passing a budget check does not establish legitimate intent.

### 7.3 Containment without pretending to reverse finality

For irreversible on-chain transfers, recovery may be impossible after settlement. The architecture therefore prioritizes pre-execution prevention, bounded exposure, rapid isolation, and separately governed replenishment. “Rollback” in this context means rollback of *software or policy changes* where feasible, not reversal of finalized blockchain transactions.

## 8. Adversarial Scenarios

All scenarios use simulated assets and non-deployable synthetic transactions.

| ID | Scenario | Expected independent control | Principal observation |
|---|---|---|---|
| S01 | Normal withdrawal under budget | ALLOW | Correct binding and acceptable latency |
| S02 | Valid signature, unauthorized destination | DENY | Signature validity cannot override intent |
| S03 | Multiple small withdrawals exceed window budget | HOLD/DENY | Aggregate exposure is enforced atomically |
| S04 | Simultaneous requests race for remaining budget | At most budget-compliant approvals | No double-spend of exposure reservation |
| S05 | Compromised signing service proposes extra transfer | DENY | PEP blocks independent of signer |
| S06 | Legitimate withdrawal demand spike | Policy-dependent ALLOW/ESCALATE | False holds and service cost measured |
| S07 | Hot-pool depletion triggers replenishment | Independent treasury review | No automatic escalation of accessible assets |
| S08 | Evidence registry temporarily unavailable | Fail closed for protected actions | No silent authorization downgrade |
| S09 | Policy update proposed by compromised service | Reject unauthorized change | Governance authority separation |
| S10 | PEP unavailable or compromised | Stop or report boundary failure | Explicit limit of protection |
| S11 | Duplicate request and delayed acknowledgment | Idempotent handling | No duplicate transfer |
| S12 | Ambiguous beneficiary identity | Hold or request verification when policy requires | Hypothesis does not become verified identity |

### 8.1 Attack drive constraints

The Red Drive may submit bounded synthetic proposals and perturb allowed simulator inputs. It may not access live funds, public infrastructure, actual customer records, or external services. The Blue Drive may propose mitigations but cannot modify hard controls without governance approval. The Evaluation Drive maintains a sealed test set; the Governance Drive approves experimental scope and deployment eligibility.

## 9. Experimental Arms and Baselines

**B0 — Signature-only:** accepts transfers passing cryptographic verification and basic syntactic checks. This intentionally weak research baseline must never be deployed as a production authorization design.

**B1 — Static thresholds:** adds per-transfer amount thresholds and conventional access control but limited cumulative exposure tracking.

**B2 — Adaptive structural analysis:** uses trust graphs, UTN/REN/BCEF and anomaly review, but does not assume a genuinely independent enforcement boundary. This isolates the contribution and limitations of intelligence alone.

**B3 — Independent safety control:** adds exact intent binding, atomic budgets, separated policy authority, and PEP enforcement, without adaptive structural analysis.

**B4 — Integrated ASSI candidate:** combines B3 with evidence-driven structural analysis, adversarial testing, and governed improvement proposals.

The primary comparison is **B3 versus B4** for the incremental benefit of ASSI intelligence, and **B1/B2 versus B3** for the effect of independent hard controls. B0 illustrates why cryptographic validity alone is insufficient; it is not a reasonable operational security standard.

### 9.1 Resource fairness

Compare arms under matched traffic, transaction finality model, simulator compute limits, adversarial budgets, and service-level constraints. Report additional latency, human-review load, engineering complexity, and policy-management costs. Do not hide overhead by excluding failed or delayed legitimate requests.

## 10. Evaluation Metrics

### 10.1 Security and containment

- **Unauthorized executed value (UEV):** total simulated value executed without valid contextual authorization.
- **Maximum scenario loss (MSL):** largest UEV across a declared scenario set.
- **Exposure-budget violation count:** number of executions exceeding an applicable independent budget.
- **Time to contain (TTC):** elapsed simulated time between detectable compromise and effective prevention of further unauthorized execution.
- **Policy-bypass rate:** fraction of attempts that violate protected controls and nevertheless execute.

### 10.2 Legitimate service and governance

- Legitimate withdrawal completion rate and latency distribution (`p50`, `p95`, `p99`).
- False hold and false denial rates under labeled legitimate traffic.
- Human escalation rate and median decision time.
- Treasury replenishment delay and resulting unmet legitimate demand.
- Governance separation failures, emergency stop effectiveness, and recovery exercise completion.

### 10.3 Structural intelligence quality

- Hypothesis calibration or ranking quality, only where ground truth and score semantics support the metric.
- Provenance completeness and correlated-evidence double-count incidents.
- False merge and false split rates for synthetic identity clusters.
- BCEF contradiction-scope violations and unsupported structural edits.
- Security Residual reproducibility and candidate improvement validation rate.

### 10.4 A bounded-loss metric

For a declared compromise scenario `s`, define:

$$
\mathrm{BoundedLossRatio}(s)=
\frac{\mathrm{UEV}(s)}{\mathrm{DeclaredExposureBudget}(s)}.
$$

This ratio is a diagnostic, not a guarantee. A value below one can coexist with unacceptable customer harm, policy bypass, or misconfigured budgets. Always report absolute loss and the policy assumptions.

## 11. Falsifiable Hypotheses

| ID | Hypothesis | Baseline | Falsification or non-support condition |
|---|---|---|---|
| H-C01 | Independent PEP reduces UEV after signer compromise | B1/B2 vs B3 | No reproducible reduction under matched assumptions |
| H-C02 | Atomic window budgets limit cumulative unauthorized outflow | B1 vs B3 | Concurrent requests exceed budget despite intact PEP |
| H-C03 | Explicit intent binding detects destination substitution missed by signature checks | B0/B1 vs B3 | Equal detection and containment under comparable inputs |
| H-C04 | ASSI evidence improves suspicious-vs-legitimate discrimination | B3 vs B4 | No material gain after accounting for latency and false holds |
| H-C05 | UTN compositional hypotheses reduce incorrect attribution | Flat identity baseline vs B4 | False merge/split metrics do not improve |
| H-C06 | BCEF hypothesis-scoped contradiction reduces over-rejection | Score-only baseline vs B4 | No improvement in false rejection at comparable threat detection |
| H-C07 | Separated replenishment authority reduces reachable compromise exposure | Shared-control vs separated-control | No meaningful reduction in tested attack reachability |
| H-C08 | Residual-driven governed iterations improve unseen-case performance | Fixed B4 vs iterated B4 | Gains disappear on sealed holdout scenarios or cause regressions |
| H-C09 | Integrated design meets legitimate-service objectives under stress | B3 vs B4 | Excessive latency, false holds, or governance cost |
| H-C10 | Independent controls remain effective when evidence scoring fails | B2 vs B3/B4 | Evidence outage enables protected actions or breaks PEP isolation |

Each hypothesis requires a preregistered dataset, primary metric, minimum effect size, uncertainty interval, and stopping criterion before a performance claim is made. No hypothesis is asserted as confirmed.

## 12. Experiment Protocol

### Phase A — Contract and simulator verification

Validate SSU schemas, time semantics, identity namespaces, policy versions, ledger conservation, exposure reservation atomicity, and audit integrity. Seed known-valid and known-invalid events and confirm expected outcomes.

### Phase B — Normal-service characterization

Generate labeled customer withdrawals with variable arrival rates and treasury replenishment needs. Establish throughput, latency, false hold, and liquidity shortage baselines without adversarial perturbations.

### Phase C — Bounded adversarial trials

Run scenarios S02–S12 with fixed seeds, controlled variations, and documented attacker capabilities. Capture every proposal, authorization decision, reservation, execution, and outcome. Preserve negative results.

### Phase D — Independent evaluation

A separate Evaluation Drive analyzes the results against preregistered metrics. It checks whether a purported reduction in loss is due to genuine control effectiveness, an unrealistic threat model, or simply rejecting nearly all transactions.

### Phase E — Residual generation and relay

Record unexplained failures, false holds, missing evidence, control races, policy conflicts, and governance weaknesses as typed Security Residuals. AQSI may generate questions, and Blue may propose fixes, but no fix is promoted without new independent validation.

### Phase F — Sealed holdout and transfer

Retest candidates against withheld scenario combinations and altered liquidity regimes. If performance does not transfer, record the limitation. Do not infer real-world safety from passing synthetic tests.

## 13. Canonical Case Record (Illustrative YAML)

The following is an **illustrative profile**, not a replacement for the normative SPEC-001 or SPEC-004 schemas.

```yaml
case_id: ASSI-CASE-001
case_version: 0.1.0
status: synthetic_research
asset_environment:
  name: harbor-custody-laboratory
  live_assets: false
  live_network_access: false
scenario:
  id: S05
  title: compromised_signing_service
  compromised_capabilities:
    - propose_transaction
    - use_assigned_signing_interface
  explicitly_uncompromised:
    - independent_policy_decision_point
    - independent_policy_enforcement_point
    - treasury_governance_quorum
request:
  request_id: req-0005
  approved_destination: synthetic:beneficiary-A
  approved_amount: 2000
proposal:
  proposal_id: tx-0005
  destination: synthetic:beneficiary-B
  amount: 2000
  cryptographic_signature_valid: true
bcef:
  test_mode: contradiction_if
  hypothesis: proposal_faithfully_executes_req-0005
  assessment: refuted
  evidence_ids: [evidence:destination-mismatch-0005]
authorization:
  decision: DENY
  reason: intent_binding_mismatch
  execution_permitted: false
  authority_source: independent_policy_control
metrics:
  unauthorized_executed_value: 0
  decision_latency_ms: null  # measured during experiment
residuals: []
audit:
  evidence_provenance_required: true
  immutable_event_log_required: true
```

The zero unauthorized value is the **expected outcome for a correctly implemented isolated control**, not an observed measurement. A test failure must retain the actual outcome instead of silently overwriting it with the expectation.

## 14. Reference Evaluation Pseudocode

```text
for scenario in preregistered_scenarios:
    reset_simulator_to_seeded_state(scenario.seed)
    assert_no_live_assets_or_external_execution()

    for request_or_proposal in scenario.event_stream:
        evidence = collect_typed_observations(request_or_proposal)
        hypotheses = update_competing_hypotheses(evidence)
        if_results = run_bounded_BCEF_tests(hypotheses, evidence)
        suggestions = propose_non_authoritative_impacts(if_results)

        canonical_action = canonicalize_proposal(request_or_proposal)
        decision = independent_PDP.evaluate(
            canonical_action,
            verified_authority,
            current_policy_version,
            atomic_exposure_reservations
        )
        outcome = PEP.enforce_exact_binding(canonical_action, decision)
        append_auditable_record(evidence, decision, outcome)

    evaluator.compute_security_and_service_metrics()
    evaluator.record_boundary_failures_and_residuals()

independent_governance.review_results_before_any_candidate_promotion()
```

The simulator must distinguish a simulated signature from a real cryptographic signature when applicable. The pseudocode is explanatory; it does not establish conformance by itself.

## 15. Conformance-Oriented Test Vectors

| Vector | Input condition | Required result |
|---|---|---|
| CV-001 | Verified request, matching proposal, within budget | Eligible for ALLOW after all other checks |
| CV-002 | Signature valid, intent mismatch | DENY; no execution |
| CV-003 | Inferred identity without verified delegation | No authority promotion |
| CV-004 | Two concurrent requests exhaust shared budget | Atomic enforcement; no excess execution |
| CV-005 | Evidence source unavailable | No protected-action fail-open |
| CV-006 | Same event represented by three derived features | Provenance preserved; no triple independent evidence |
| CV-007 | Single-operator hypothesis contradicted | Team/shared-service alternatives remain assessable |
| CV-008 | Signing service requests policy increase | Deny unless independently governed approval exists |
| CV-009 | Hot-pool depletion followed by replenishment proposal | Separate treasury authorization required |
| CV-010 | Replay of previously approved execution object | Idempotency/replay protections enforced |
| CV-011 | Policy changes between approval and execution | Revalidation or safe rejection |
| CV-012 | Governance approves new scoring model | Hard controls unchanged absent separate authorization |
| CV-013 | PEP unavailable | Protected execution blocked and failure recorded |
| CV-014 | Adversarial trial exceeds sandbox budget | Immediate stop, audit, and no external effects |
| CV-015 | Candidate improvement passes training but fails holdout | No promotion; regression recorded |
| CV-016 | Finalized on-chain simulation transfer | Do not mislabel policy rollback as chain reversal |

The corresponding normative invariants and negative tests belong to SPEC-001 and SPEC-004–006. This case adds scenario-specific expectations.

## 16. Example Security Residuals and AQSI Questions

### RES-001 — Concurrent budget reservation race

**Observation:** two individually acceptable withdrawal proposals both receive approval against a stale remaining budget.  
**Hypothesis:** non-atomic exposure reservation enables aggregate overspend.  
**AQSI question:** under which concurrency patterns can the PEP authorize an amount greater than the configured window budget?  
**Candidate:** serialized or transactional budget reservations with idempotent commit/release.  
**Validation:** stress tests with randomized scheduling and sealed holdout patterns.  
**Governance:** independent approval required before changing budget logic.

### RES-002 — Replenishment as an exposure amplifier

**Observation:** a suspicious hot-wallet outflow is followed by an automatic cold-to-hot replenishment.  
**Hypothesis:** the replenishment path expands reachable assets during a signer compromise.  
**AQSI question:** can replenishment remain available for legitimate demand without being driven by suspicious depletion alone?  
**Candidate:** separately governed replenishment with incident-aware holds and declared service exceptions.  
**Validation:** compare unauthorized reachable value and legitimate shortage under varying traffic.

### RES-003 — Overzealous structural scoring

**Observation:** a legitimate high-volume customer event is repeatedly held by an adaptive anomaly score.  
**Hypothesis:** the model treats correlated weak indicators as independent evidence.  
**AQSI question:** which evidence dependencies or alternative hypotheses explain the false holds?  
**Candidate:** dependency-aware REN/BCEF assessment and hypothesis-scoped contradiction.  
**Validation:** compare false holds at matched unauthorized-transfer detection rates.

### RES-004 — Independent boundary exists only on paper

**Observation:** a compromised administrator can change both the signing workflow and the policy-enforcement configuration.  
**Hypothesis:** the nominally independent control plane shares a mutable authority root.  
**AQSI question:** which concrete credentials, deployment pipelines, and emergency procedures can alter both planes?  
**Candidate:** separate control roots, attested policy deployment, and independent change approval.  
**Validation:** role/permission graph audit and bounded change-control simulations.

## 17. Governance, Ethics, and Deployment Restrictions

This case is intentionally defensive. Adversarial exercises require explicit authorization, isolated environments, synthetic assets, and bounded actions. No production wallet keys, customer credentials, private financial records, or external execution endpoints should enter the laboratory.

An adaptive security model may recommend `HOLD` or investigation but must not independently raise its own authority, relax exposure budgets, or approve transfers. Policy exceptions require a distinct accountable authority and a durable audit trail. Incident procedures must specify when to stop transfers, how to preserve evidence, who can authorize recovery, and how customer-service consequences are communicated.

Risk containment is not costless: false holds can damage legitimate users, and overly restrictive budgets can impair liquidity. The evaluation must report those harms rather than optimizing only for low unauthorized loss.

## 18. Threats to Validity and Known Limitations

1. **Synthetic fidelity:** simplified ledger, customer behavior, and finality assumptions may miss production complexity.
2. **Compromise scope:** independent controls only help under the stated trust and compromise assumptions.
3. **Identity uncertainty:** on-chain addresses do not establish verified human or organizational controllers.
4. **Calibration:** arbitrary budget values do not establish a correct real-world risk appetite.
5. **Measurement bias:** high rejection rates can make unauthorized execution appear low while destroying service utility.
6. **Evidence correlation:** repeated observations from one trace may inflate confidence.
7. **Adaptive overfitting:** repeated Red/Blue iterations can optimize to known simulator cases.
8. **Irreversibility:** no software recovery procedure reverses a finalized public-chain transfer by itself.
9. **Governance independence:** nominally separate teams or processes may share an actual authority root.
10. **External validity:** a passed benchmark is not proof of safety across assets, chains, contracts, organizations, or attack models.

Any published empirical results must disclose failed scenarios, uncertainty, resource costs, and the exact trust assumptions.

## 19. Reporting and Reproducibility Checklist

A completed experiment report should provide:

- [ ] Simulator version, deterministic seeds, asset model, and finality assumptions.
- [ ] Exact attacker capabilities, trust assumptions, and excluded capabilities.
- [ ] Policy versions, authorization contracts, and independent enforcement topology.
- [ ] Scenario manifests and preregistered hypotheses.
- [ ] Raw event/decision logs with appropriate redaction and provenance.
- [ ] UEV, MSL, budget violations, containment time, and bypass counts.
- [ ] Legitimate completion, latency, false holds, and replenishment shortage.
- [ ] Per-arm compute, human review, and operational costs.
- [ ] Holdout results, negative findings, and regression tests.
- [ ] Residual registry, candidate changes, governance decisions, and rollback readiness.
- [ ] Explicit separation of simulated observations, inferences, and verified conclusions.

## 20. Relationship to the ASSI Research and Specification Series

| Source | Role in CASE-001 |
|---|---|
| ASSI-001 | Cryptographic validity versus structural security |
| ASSI-002 | Four cryptocurrency structural contradictions |
| ASSI-003 | Trust relocation and boundary mapping |
| ASSI-004 | UTN and compositional identity alternatives |
| ASSI-005 | REN directional and weak evidence |
| ASSI-006 | BCEF conditional tests and scoped impacts |
| ASSI-007 | Independent authorization and bounded exposure |
| ASSI-008 | Red/Blue/Evaluation/Governance drives |
| ASSI-009 | Residual-driven, validated RSI |
| ASSI-010 | Shared SSU architecture |
| ASSI-011 | BM-003 authorization and bounded-loss benchmark |
| SPEC-001 | Canonical SSU envelope and provenance |
| SPEC-002 | UTN identity and authority distinctions |
| SPEC-003 | IF tests and evidence-impact contract |
| SPEC-004 | Authorization and safety control contract |
| SPEC-005 | Adversarial drive and relay contract |
| SPEC-006 | Validation, promotion, and governance contract |

**Next case:** `CASE-002-UTN-On-Chain-Identity-Sandbox.md` studies identity hypotheses and synthetic chain evidence more deeply. CASE-003 focuses on BCEF and false rejection; CASE-004 isolates compromised signing-service defense; CASE-005 studies adversarial drives and validated security RSI.

## 21. Conclusion

Cryptocurrency liquidity is an operational capability whose security implications depend on the surrounding trust and authorization structure. A valid signature does not answer whether an action reflects legitimate intent, and a liquid pool does not reveal how much is reachable through compromised authority. CASE-001 proposes a reproducible way to make these dependencies explicit: model trust and liquidity jointly, preserve identity and evidence uncertainty, test conditional hypotheses, enforce consequential decisions through independent controls, and measure both bounded loss and legitimate service cost.

The central falsifiable proposition is that **independent, exact-bound authorization and exposure controls can reduce compromise consequences, while structural intelligence may improve diagnosis and prioritization without acquiring the authority to bypass those controls**. Whether this combination improves practical security remains an empirical question. The case therefore ends not with a claimed solution, but with an executable research agenda, negative tests, and a path for independently validated structural relay.

---

**Research status:** Proposed synthetic case and benchmark design; no experiments have been run or security guarantees established.  
**Repository placement:** `cases/CASE-001-Cryptocurrency-Trust-and-Liquidity.md`  
**Next:** `cases/CASE-002-UTN-On-Chain-Identity-Sandbox.md`  
**License:** Apache-2.0
