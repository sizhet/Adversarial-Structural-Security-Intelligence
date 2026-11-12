# ASSI-003 — Trust Relocation and Structural Security Boundaries

**Adversarial Structural Security Intelligence (ASSI)**  
**Research Foundation · v0.1.0 · November 2026**  
**Status:** Architectural hypothesis and specification-oriented research; not a deployed or validated security product.

## Abstract

Cryptographic systems can reduce the need to trust a transaction intermediary while leaving consequential trust dependencies in signing infrastructure, software supply chains, administrators, custody arrangements, recovery procedures, and organizational governance. This paper develops the **Trust Relocation Principle** as a structural modeling discipline: a local reduction in one trust dependency does not, by itself, establish a reduction in end-to-end security exposure. We define a typed **Structural Trust Graph**, distinguish cryptographic validity from authorization intent and business legitimacy, and specify security boundaries that must remain effective even when intelligent detection fails. We introduce trust-relocation records, cross-boundary propagation analysis, blast-radius and loss-exposure measures, and a separation between hard enforcement, probabilistic evidence scoring, and independent recovery. The proposed architecture connects ASSI to Universal Typing and Naming (UTN), directional weak-evidence reasoning (REN), Bidirectional Conditional Evidence Feedback (BCEF), Universal Control Planes and Scoring Folding (UCPSF), and adversarial structural relay. The contribution is a testable research framework, not a claim that any particular cryptocurrency incident has been explained or prevented.

**Keywords:** trust relocation; structural security; trust boundaries; custody; authorization; signing services; least privilege; loss containment; UTN; evidence provenance; adversarial resilience; ASSI.

---

## 1. Research question and central thesis

A protocol may replace discretionary intermediary approval with verifiable signatures and deterministic transaction execution. That is a significant achievement. It does not follow that users, custodians, or platform operators no longer depend on trusted actors or components. The dependency may instead reside in private-key custody, transaction construction, endpoint integrity, contract upgrades, privileged operators, or the infrastructure that presents a transaction for signing.

**Central thesis:**

> Trust can be minimized at a particular interface while security responsibility and failure exposure are relocated elsewhere in the system.

This is a claim about **system composition**, not an argument against cryptography or decentralization. Cryptographic verification remains essential; the problem arises when its local guarantee is mistaken for a complete end-to-end safety guarantee.

The primary research questions are:

1. How can trust dependencies be explicitly represented across protocol, application, infrastructure, organizational, and recovery layers?
2. Which trust relocations concentrate risk or create unrecognized single points of catastrophic failure?
3. How can structural authorization prevent a technically valid action from violating owner intent or an independent safety policy?
4. What residual exposure remains when one or more security boundaries fail?
5. How can adversarial simulation and validated structural relay improve the model without granting an adaptive intelligence system unconstrained authority?

### 1.1 Scope and exclusions

The immediate motivating domain is cryptocurrency custody and transaction authorization. The same abstractions may be useful for cloud administration, payment infrastructure, AI-agent tool execution, and enterprise identity systems, but cross-domain transfer is a research hypothesis. This paper does not attribute a real-world compromise to a named company, person, or mechanism; such claims require independently verified evidence.

---

## 2. Five distinctions that a structural security model must preserve

### 2.1 Verification versus intent

A signature check answers a constrained question: *does this signature verify under the relevant cryptographic and protocol rules?* It does not independently answer whether the owner understood the transaction, whether the signing endpoint was compromised, whether the destination was authorized, or whether the requested operation satisfies business policy.

A useful conceptual decomposition is:

- **Cryptographic validity:** the protocol-level verification predicate passes.
- **Authorization provenance:** the action originated from an appropriately delegated authority under a trustworthy process.
- **Intent consistency:** the action matches the intended economic or administrative purpose.
- **Policy admissibility:** the action satisfies independent limits, allowlists, segregation-of-duties rules, and emergency restrictions.
- **System safety:** the action and its possible failure consequences remain within acceptable exposure bounds.

These predicates are related but nonidentical. Passing one does not imply passing the others.

### 2.2 Trust minimization versus trust elimination

Trust minimization can reduce the number or power of intermediaries. It does not eliminate reliance on code, hardware, key management, governance, or the integrity of information shown to users. Some dependencies are transformed rather than removed.

### 2.3 Observability versus identity knowledge

A public transaction graph provides evidence of recorded interactions. It does not automatically reveal a unique real-world controller. One person may use many addresses; one address may be jointly administered; different groups may share infrastructure. Structural identity inference must preserve these alternatives.

### 2.4 Risk scoring versus enforceable limits

A risk model estimates uncertainty. A hard policy determines what must never execute without required authorization. A high composite score must not override a hard prohibition, and a low risk score must not be treated as a proof of safety.

### 2.5 Detection versus loss containment

An alert may arrive too late, be missed, or be deliberately evaded. Independent transaction limits, asset segregation, delayed settlement, and recovery capabilities reduce damage even when detection fails. ASSI treats **bounded loss before perfect defense** as an engineering priority, subject to explicit assumptions and measurable limits.

---

## 3. The Trust Relocation Principle

Consider a system transition from architecture $A$ to architecture $B$. A trust dependency on an intermediary may decline while a dependency on an online signer, upgrade administrator, bridge operator, or user endpoint increases. Thus:

$$
\Delta T_{\mathrm{intermediary}} < 0
\quad\not\Rightarrow\quad
\Delta R_{\mathrm{system}} < 0,
$$

where $T$ denotes a specific trust dependency and $R$ denotes an appropriately defined system-risk measure. This is a conceptual statement, not a universally quantified empirical law. Risk depends on threat likelihood, exposure, control effectiveness, recovery, and the evaluation horizon.

A trust relocation should therefore be documented as a transition:

$$
\mathcal{R}: (d_{\mathrm{old}}, b_{\mathrm{old}})
\longrightarrow (d_{\mathrm{new}}, b_{\mathrm{new}}),
$$

where $d$ is a dependency and $b$ is its trust boundary. The record should include the assumed attacker capabilities, affected assets, new concentration points, evidence supporting the change, and compensating controls.

### 3.1 Examples of relocation

| Design change | Trust reduced | Trust newly emphasized or concentrated | Structural question |
|---|---|---|---|
| Self-custody instead of exchange custody | Exchange discretionary custody | Wallet endpoint, recovery phrase, user signing workflow | Can endpoint compromise authorize catastrophic loss? |
| Exchange hot-wallet automation | Manual operational bottleneck | Online signer, orchestration service, privileged API | Can a single compromise exceed the approved asset exposure? |
| Smart-contract execution | Off-chain discretionary settlement | Contract correctness, upgrade keys, oracles, governance | Which privileged transitions can redirect assets? |
| Multisignature approval | One key's unilateral control | Signer independence, coordination, common-mode compromise | Are nominally separate signers truly independent? |
| Automated anomaly detection | Reliance on manual inspection | Model quality, telemetry integrity, policy integration | Can detection failure bypass a hard safety boundary? |

Trust relocation is not necessarily undesirable. The purpose of analysis is to make the tradeoff **explicit and testable**.

### 3.2 Concentration and correlated failures

Counting keys, signers, or controls is insufficient. Five signers managed by one administrator or running on one compromised platform may behave like one failure domain. The structural model must represent **common-mode dependencies** and distinguish formal quorum from operational independence.

---

## 4. Structural Trust Graph: a typed representation

Define a time-indexed attributed multigraph:

$$
G_t=(V_t,E_t,\tau_V,\tau_E,\alpha_t,\pi_t),
$$

where:

- $V_t$ contains typed entities;
- $E_t$ contains typed directed or undirected relationships;
- $\tau_V$ and $\tau_E$ assign node and edge types;
- $\alpha_t$ stores time-dependent attributes and constraints;
- $\pi_t$ records evidence provenance, uncertainty, and validation state.

**Candidate node types:** asset pool, wallet, key, signer, authorization service, contract, upgrade controller, endpoint, human role, team, organization, external service, monitoring component, recovery mechanism, and policy authority.

**Candidate edge types:** controls, signs-for, delegates-to, can-upgrade, can-transfer, depends-on, observes, approves, blocks, recovers, shares-infrastructure-with, and hypothesized-common-control.

A graph edge representing a verified on-chain transfer must not be conflated with an inferred common-controller edge. The latter needs confidence, supporting evidence, alternatives, and explicit revocation rules.

### 4.1 Compositional principals

The principal at one boundary may be an individual, a multisignature group, an operational team, a temporary coalition, or a role filled by changing members. A group can overlap another group without being identical to it. This requires a composition-aware identity model, described in detail in **ASSI-004** and **SPEC-002**.

For example, evidence inconsistent with *one individual controlling two addresses* need not contradict *two members of one organization controlling those addresses*. Contradiction must be scoped to the precise hypothesis being tested.

### 4.2 Explicit boundary objects

A **Security Boundary** is not merely a line on an architecture diagram. It is a first-class object with:

1. **Protected assets and operations**;
2. **Authorized principals and permitted actions**;
3. **Enforcement mechanism and independence assumptions**;
4. **Trust dependencies and possible bypass paths**;
5. **Failure modes, maximum exposure, and recovery provisions**;
6. **Evidence and conformance tests**.

This makes boundaries inspectable and comparable across versions.

---

## 5. Six security boundaries in a cryptocurrency custody system

### B1 — Protocol and cryptographic boundary

Validates transaction encoding, signature rules, nonce or replay protections, and chain-specific semantics. It establishes protocol validity but not the user's informed intent.

### B2 — Intent and transaction-construction boundary

Connects an authenticated business request to the exact transaction to be signed. Critical checks include destination, amount, asset, chain, contract call semantics, approval scope, and protection against substituted transaction payloads.

### B3 — Key and signing boundary

Controls who can request signing, under which conditions, and with what separation of duties. Hardware isolation or distributed signing can help, but the policy enforcement path and administrative privileges must also be modeled.

### B4 — Asset-exposure and execution boundary

Enforces asset segmentation, transaction ceilings, velocity limits, allowlists, staged withdrawals, and risk-sensitive delays. These controls should constrain the consequences of upstream compromise.

### B5 — Organizational and governance boundary

Defines decision rights for policy changes, emergency overrides, signer rotation, deployment, and incident response. Independence must be substantive, not merely reflected in an organizational chart.

### B6 — Recovery and continuity boundary

Supports incident containment, key revocation or rotation where feasible, backup integrity, reconciliation, forensic preservation, and business continuity. Some blockchain transfers are irreversible; recovery planning cannot assume they can be rolled back.

### 5.1 Cross-boundary failure example

In a synthetic scenario, a malicious actor compromises a transaction-orchestration service. The service may generate correctly formatted requests and obtain valid signatures through a misconfigured signer. B1 passes; B2 and B3 may fail to preserve intent; B4 is the last independent opportunity to cap losses. If the same administrator can disable B4, the apparent layering collapses into a common failure domain.

**Key design question:** which boundary remains effective after every single upstream component in the modeled threat set is compromised?

---

## 6. Quantifying exposure without confusing a score with a guarantee

ASSI should maintain several separate measurements rather than fold all safety claims into one opaque number.

### 6.1 Reachable asset exposure

Let $A$ be a set of assets and $C$ a compromised component or coalition. Define:

$$
X(C,t,h)=\sum_{a\in A} v_a(t)\,\rho(a\mid C,t,h),
$$

where $v_a(t)$ is asset value and $\rho$ is the fraction operationally reachable under the specified compromise, controls, and horizon $h$. The fractions are scenario assumptions or experimentally established bounds, not probabilities by default.

### 6.2 Conditional loss distribution

For policy $\pi$, attack scenario $\omega$, and horizon $h$, define $L(\pi,\omega,h)$ as realized or simulated loss. Evaluation should include:

- Expected loss under a stated scenario distribution;
- Tail-loss measures for severe but plausible scenarios;
- Maximum demonstrated loss in the tested scenario set;
- Detection and containment latency;
- False-blocking and operational disruption;
- Recovery time and residual exposure.

A simulation maximum is **not** a universal worst-case bound. A defensible hard bound requires enforceable constraints and clearly stated assumptions about bypass, timing, liquidity, and valuation.

### 6.3 Minimal-cut and blast-radius analysis

Graph analysis can identify small sets of compromised components whose loss of integrity permits unauthorized asset movement. However, graph connectivity alone is not proof of exploitability. Paths require validated capability semantics, preconditions, and enforcement behavior.

A useful design goal is to ensure that no single modeled administrative or technical failure can authorize movement beyond a specified asset-exposure budget.

---

## 7. Structural authorization: three planes, separate authorities

ASSI proposes a disciplined separation:

| Plane | Function | May directly authorize prohibited transactions? |
|---|---|---|
| **Hard Safety Control Plane** | Enforce non-negotiable limits and required approvals | **No**; it must reject violations |
| **Evidence and Intelligence Plane** | Score anomalies, interpret context, generate IF tests, recommend escalation | **No**; its outputs are advisory or may tighten controls under predefined rules |
| **Independent Recovery and Governance Plane** | Manage containment, exceptional authorization, rollback of deployments, and audit | Only through explicitly governed, independently authenticated procedures |

The phrase *independent* must be tested: a separate service administered by the same compromised credentials is not necessarily an independent control.

### 7.1 Decision sequence

1. Receive an authenticated request and preserve its provenance.
2. Resolve the exact transaction semantics and intended business operation.
3. Apply mandatory policies and exposure limits.
4. Evaluate evidence-based anomalies and conditional hypotheses.
5. Route uncertainty to additional approval, delay, or rejection as policy requires.
6. Execute only after all applicable enforcement predicates pass.
7. Record evidence, decisions, and subsequent observations for audit and learning.

**Non-negotiable invariant:** no probabilistic score, model-generated explanation, or recursive improvement process may silently override an applicable hard safety policy.

---

## 8. UTN, REN, and BCEF as supporting intelligence mechanisms

### 8.1 UTN: typed entities and identity hypotheses

UTN provides typed names for assets, roles, addresses, services, groups, and time-bounded compositions. A Name should be interpreted according to its type and evidentiary status. An inferred group label is not proof of a person's real-world identity.

### 8.2 REN: directional and weak-evidence evaluation

REN can assess behavioral similarity, directional evidence, and counterevidence under a stated investigative question. The same observation may carry different relevance for *shared infrastructure*, *shared operator*, and *shared organization* hypotheses. Scores must retain uncertainty and provenance.

### 8.3 BCEF: bidirectional conditional testing

For a hypothesis $H$ and evidence $E$, BCEF asks:

- **Forward IF:** If $H$ were true, what should be observed?
- **Reverse IF:** How diagnostic is the observed $E$ for $H$?
- **Counterfactual IF:** Could $E$ arise without $H$?
- **Contradiction IF:** Which precise formulation of $H$, if any, does $E$ challenge?

The logical warning is fundamental:

$$
H\Rightarrow E\quad\not\Rightarrow\quad E\Rightarrow H.
$$

An IF test may modify scores, evidence dependencies, graph edges, candidate partitions, or the next test to run. It should **not** manufacture independent evidence by repeatedly reusing the same observation.

### 8.4 A minimal evidence-impact record

```yaml
impact_id: example-if-impact-001
status: illustrative
hypothesis_id: H_shared_individual_controller
hypothesis_scope: individual
observation_ref: E_activity_timing_difference
if_test_type: contradiction
result: weakens_hypothesis
provenance_refs:
  - E_activity_timing_difference
alternative_hypotheses:
  - H_shared_organization_different_operators
  - H_independent_operators
allowed_actions:
  - reweight_hypothesis
  - request_independent_test
forbidden_inference:
  - automatically_reject_shared_organization
```

This is an illustrative contract sketch, not a finalized schema. **SPEC-003** will define conformance requirements.

---

## 9. Trust relocation as a change-management operation

A new security feature can create a new failure mode. ASSI therefore treats architectural change as a controlled trust-relocation event.

For each proposed change, record:

1. **Before/after graph delta:** which nodes, privileges, and dependencies changed?
2. **Boundary delta:** which enforcement points moved, weakened, or became shared?
3. **Threat delta:** which attacker capabilities now suffice to reach an asset?
4. **Exposure delta:** which asset pools and limits are affected?
5. **Observability delta:** what new telemetry exists, and what becomes invisible?
6. **Governance delta:** who can approve, disable, or reverse the change?
7. **Residual:** what risk remains unexplained or unmitigated?

This process aligns with structural differential analysis and provides input to ASSI's Security Residual registry.

### 9.1 Example: adding an automated signing workflow

An automation may reduce human error and latency. It may also place greater authority in a transaction-building service. The change should not be accepted merely because the signing key remains in a secure module. The relevant question is whether a compromised upstream requester can induce the secure module to sign an economically unauthorized operation.

Candidate mitigations include transaction-aware signing policies, independent destination controls, per-asset limits, multi-party approval for exceptional transfers, and pre-authorized emergency isolation. Their effectiveness must be tested under the actual threat model.

---

## 10. Adversarial drives and Security Residuals

A static Trust Graph will become stale. ASSI therefore connects structural modeling to adversarial testing:

$$
\text{Model}\rightarrow\text{Red/Blue Drive}
\rightarrow\text{Independent Evaluation}
\rightarrow\text{Residual}\rightarrow\text{Candidate Improvement}
\rightarrow\text{Validation}\rightarrow\text{Governed Relay}.
$$

**Red Drive:** probes the modeled boundaries in an isolated, authorized environment.  
**Blue Drive:** proposes containment and detection strategies.  
**Evaluation Drive:** measures performance using independent criteria and withheld scenarios.  
**Governance Drive:** approves, rejects, or rolls back proposed changes.

A **Security Residual** is an observed or plausibly demonstrated gap between the desired security property and the currently validated protection. Residuals include unbounded exposure, untested privilege combinations, correlated control failures, detection delay, false positives, or recovery weaknesses.

Recursive self-improvement (RSI) is appropriate only as a **candidate-generation and learning process subject to independent validation**. Self-generated attack suites are not sufficient evidence of real-world robustness; held-out attacks, external review, and deployment safeguards are necessary.

---

## 11. Proposed specifications and conformance criteria

This paper informs the following ASSI documents:

- **SPEC-001 — Structural Security Unit Contract:** typed trust graph, boundary objects, provenance, and exposure attributes.
- **SPEC-002 — Compositional Identity and UTN Contract:** individual, group, role, coalition, and time-dependent identity hypotheses.
- **SPEC-003 — Bidirectional IF and Evidence Impact Contract:** hypothesis-scoped tests, counterevidence, and feedback constraints.
- **SPEC-004 — Authorization and Safety Control Contract:** independent enforcement, hard/soft policy separation, and bounded loss.
- **SPEC-005 — Adversarial Drive and Relay Contract:** authorized simulation, scenario isolation, and residual recording.
- **SPEC-006 — Validated RSI and Governance Contract:** independent evaluation, approvals, rollback, and audit.

### 11.1 Minimum conformance properties

A prototype should be able to demonstrate that:

- Every critical asset has an identifiable set of authorizing principals and enforcement boundaries.
- Every inferred identity or trust edge is distinguished from a directly observed fact.
- A hard policy violation is rejected regardless of model risk score.
- A change to signer or administrative authority produces a traceable graph delta.
- A hypothesized compromise yields a reproducible exposure estimate with stated assumptions.
- A single evidence source cannot be counted as multiple independent confirmations merely because several derived IF tests refer to it.
- An AI-generated policy change cannot enter production without the required independent approvals.

---

## 12. Falsifiable hypotheses and benchmark design

The hypotheses below are **proposals**, not reported results.

| ID | Hypothesis | Baseline | Primary measurement | What would challenge the claim? |
|---|---|---|---|---|
| TR-H1 | Explicit trust-relocation modeling discovers more consequential single-failure paths | Conventional component inventory | Independently confirmed critical paths per review-hour | No improvement after accounting for review effort and false positives |
| TR-H2 | Boundary-aware authorization reduces simulated unauthorized asset movement | Signature validity plus conventional access control | Attack success and conditional loss | Similar losses or unacceptable business disruption |
| TR-H3 | Composition-aware identity modeling reduces false rejection of team-level hypotheses | Single-controller clustering | False-rejection rate at fixed precision | No improvement on held-out labeled compositions |
| TR-H4 | BCEF improves hypothesis calibration under contradictory evidence | Static weighted evidence scoring | Calibration error, false merges/splits | Equal or worse performance, or evidence double counting |
| TR-H5 | Adversarial relay improves defenses beyond fixed testing | Periodic fixed red-team scenarios | Held-out attack containment, cost, false-blocking | Gains vanish on unseen attacks or are outweighed by regressions |

### 12.1 Benchmark A — Trust Graph and boundary discovery

Construct a synthetic custody platform with documented asset flows, signing authorities, service dependencies, and deliberately hidden common-mode administrative paths. Compare a structural review against a standard inventory review under equal time and information budgets. Use independent adjudicators to classify discovered paths.

### 12.2 Benchmark B — Signing-service compromise

Assume an adversary controls a transaction requester but not an independently administered asset-limit service. Compare transaction acceptance, unauthorized value moved, time to containment, and legitimate-transaction blocking across policy configurations. Repeat with correlated compromise of both services to expose the dependence on independence assumptions.

### 12.3 Benchmark C — Identity composition and contradiction

Generate labeled individual, group, and coalition behavior with overlapping membership and time-varying roles. Evaluate whether a contradiction to a single-person hypothesis incorrectly eliminates a viable team hypothesis. Require train/test separation and report abstention rates.

### 12.4 Benchmark D — Security Residual and adversarial relay

Use isolated attack-and-defense scenarios, with a withheld evaluator scenario set. Track whether candidate improvements reduce residual exposure without creating new bypasses or operational instability.

### 12.5 Evaluation discipline

Pre-register threat models, baselines, stopping criteria, metrics, and the distinction between simulated and enforced guarantees. Report negative findings, failure cases, and sensitivity to assumptions. Do not equate synthetic benchmark performance with production security assurance.

---

## 13. Failure modes and limitations of the ASSI approach

1. **Incomplete graph:** unknown dependencies or hidden administrator paths can invalidate exposure estimates.
2. **False independence:** separately named controls may share infrastructure, personnel, or credentials.
3. **Misleading identity inference:** chain observations can support multiple explanations; a structural Name may remain pseudonymous.
4. **Correlated evidence:** multiple derived indicators can inflate confidence if treated as independent.
5. **Model exploitation:** an adversary may manipulate telemetry or exploit learned decision boundaries.
6. **Simulation-to-reality gap:** training against a narrow attack generator may produce brittle defenses.
7. **Governance capture:** emergency exceptions or policy updates may bypass nominal technical protections.
8. **Irreversibility:** on-chain transfers may not be recoverable even when compromise is detected.
9. **Privacy and due process:** inferred relationships must not be treated as verified real-world identity or grounds for unsupported accusation.
10. **Complexity cost:** structural modeling and multiple control planes can introduce latency, operational burden, and new attack surfaces.

ASSI is useful only if its measured benefits exceed these costs under the relevant operational constraints.

---

## 14. Relationship to the ASSI research sequence

**ASSI-001** establishes the distinction between cryptographic validity and structural security.  
**ASSI-002** identifies four interacting cryptocurrency-security tensions.  
**ASSI-003 (this paper)** defines trust relocation, typed trust dependencies, and enforceable security boundaries.  
**ASSI-004** develops UTN compositional identity.  
**ASSI-005** develops directional weak-evidence intelligence.  
**ASSI-006** formalizes BCEF and Scoring Tree impact.  
**ASSI-007** develops structural authorization and independent control planes.  
**ASSI-008–009** develop adversarial drives, Security Residuals, and validated RSI.  
**ASSI-010–012** integrate architecture, benchmarks, and cross-domain implications.

Related research programs include UTN, REN/MDI, UCPSF, SIF, AQSI, SSICR, UIERU, and structural recursive self-improvement. Their mention indicates conceptual integration opportunities, not experimentally demonstrated interoperability.

---

## 15. Conclusion

Cryptographic correctness is indispensable but local. System safety depends on who controls keys and policies, how authority crosses boundaries, which assets remain reachable after compromise, and whether independent mechanisms can constrain loss. Trust relocation makes these dependencies explicit instead of treating reduced intermediary trust as a blanket security guarantee.

ASSI proposes a path from this diagnosis to engineering practice: typed trust graphs, composition-aware principals, hypothesis-scoped evidence tests, hard authorization boundaries, quantified exposure, adversarial simulation, Security Residuals, and independently governed improvement. The strongest claim at this stage is methodological: **a security architecture should account for where trust moved, what failures it enables, and which independently enforced limits remain when intelligent defenses are wrong.**

> **Trust can move; responsibility remains.**

### Research maturity statement

This is a **v0.1.0 research-foundation paper**. Models, interfaces, and benchmarks are proposed for evaluation. No empirical effectiveness, breach attribution, comprehensive loss bound, or production deployment is asserted. The next step is to turn the graph and boundary definitions into testable contracts and controlled benchmark cases.

### Suggested figure placement

- **Fig-002 — Four Structural Security Contradictions:** after Section 3, to show the motivating trust-relocation tensions.
- **Fig-005 — Structural Authorization Control Plane:** after Section 7, to illustrate independent enforcement and evidence-scoring separation.
- **Fig-001 — ASSI Grand Architecture:** optionally in Section 10 as a cross-reference to the full research program.
