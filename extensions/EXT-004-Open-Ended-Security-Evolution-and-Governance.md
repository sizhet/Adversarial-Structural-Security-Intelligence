# EXT-004 — Open-Ended Security Evolution and Governance

**Project:** Adversarial Structural Security Intelligence (ASSI)  
**Version:** v0.1.0 — Research Foundation  
**Status:** Exploratory research architecture and proposed contracts; not an implemented or certified security system  
**Date:** 2026-11-02  
**License:** Apache-2.0  
**Repository path:** `extensions/EXT-004-Open-Ended-Security-Evolution-and-Governance.md`  
**Foundations:** ASSI-001–012; SPEC-001–006; CASE-001–005; EXT-001–003  
**Related research:** UTN, REN, BCEF, MDT, UCPSF, AQSI, UIERU, SSICR, ISGFTR, Structural Relay, Validated RSI

## Abstract

Security is not a finite optimization problem. New identities, asset classes, services, adversarial incentives, software dependencies, and institutional arrangements continuously change the threat landscape. A fixed defense may become obsolete, while an unconstrained self-improving defense can itself become a source of unacceptable risk. **Open-ended security evolution** therefore presents a dual engineering obligation: expand the system's capacity to discover and address new threats while keeping consequential actions within independently governed limits, including when its models, evaluations, and governance assumptions are wrong.

This paper proposes **Open-Ended Security Evolution and Governance (OESEG)** as a research extension of Adversarial Structural Security Intelligence (ASSI). OESEG combines a portfolio of evolving Security Residuals, autonomous question generation (AQSI), heterogeneous Red/Blue/Evaluation/Governance Drives, typed evidence and identity structures (UTN, REN, BCEF), candidate defense generation, independent validation, and Structural Relay. It introduces a **dual-loop architecture**: an adaptive learning loop may generate and evaluate proposals, while a separately authorized safety-and-governance loop determines what may affect consequential environments. The latter is not presumed infallible; its independence, coverage, recoverability, and failure modes must also be tested.

The paper defines open-endedness operationally, specifies governance invariants and lifecycle contracts, examines ecological and institutional failure modes, develops synthetic laboratories and falsifiable hypotheses, and proposes a staged validation roadmap. It does not claim that recursive self-improvement guarantees security, that multi-agent agreement constitutes independent evidence, or that a universal safety boundary can be derived from intelligence alone.

**Keywords:** open-ended security; adversarial evolution; governed recursive self-improvement; structural relay; security residuals; autonomous questioning; independent authorization; institutional governance; collective learning; falsifiable security.

---

## 1. The Central Problem: Security Must Evolve Without Self-Authorizing

A defender faces an evolving environment. New vulnerabilities emerge, benign workflows change, attackers exploit unexpected combinations, and previously effective rules can become harmful. Adaptation is necessary. But a system that can rewrite its own safety constraints without independent authorization creates a second, potentially more consequential, attack surface.

OESEG treats these as separate questions:

1. **Discovery:** Can the system detect or hypothesize previously unmodeled security residuals?
2. **Learning:** Can it distinguish useful defense improvements from artifacts of a benchmark, evaluator, or evidence source?
3. **Authority:** Who may approve a change to a consequential control?
4. **Containment:** What happens when learning, evaluation, authorization, or governance fails?
5. **Continuity:** How are successful, failed, and unresolved discoveries preserved across agents, versions, and organizations?

The central principle is:

> Open-ended discovery may expand the space of proposed defenses; it must not silently expand the authority to deploy them.

The goal is **governed adaptability**, not unconstrained autonomy.

## 2. Research Scope and Non-Claims

### 2.1 In scope

- Evolving security-question and Security Residual portfolios.
- Multi-agent adversarial and cooperative Structural Relay.
- Evidence-dependent hypothesis revision and explicit uncertainty.
- Independent validation, promotion, rollback, and governance.
- Cross-domain transfer with typed semantic boundaries.
- Safety-control coverage, failure, and recovery experiments.
- Longitudinal evaluation of defense performance under changing conditions.

### 2.2 Out of scope

- Autonomous exploitation of live third-party systems.
- Unapproved modification of production authorization rules.
- Claims that AI reasoning can certify itself as safe.
- Unbounded recursive experimentation or asset exposure.
- Treating a simulated attack outcome as proof of real-world safety.
- Assigning real identities from weak or on-chain evidence alone.

All adversarial scenarios in this proposal are synthetic or explicitly authorized and isolated.

## 3. Operationalizing Open-Endedness

The term *open-ended* should be measurable rather than rhetorical. Let a research system maintain, at time \(t\):

- \(Q_t\): active, unresolved, and archived security questions;
- \(R_t\): typed Security Residuals;
- \(H_t\): competing security hypotheses;
- \(C_t\): candidate controls and defense strategies;
- \(V_t\): validation records, including negative results;
- \(G_t\): independently approved governance and execution constraints.

An evolution event proposes:

\[
(Q_t,R_t,H_t,C_t,V_t) \rightarrow (Q_{t+1},R_{t+1},H_{t+1},C_{t+1},V_{t+1}).
\]

The proposal **does not imply** \(G_t \rightarrow G_{t+1}\). A governance transition requires a separate authorization and conformance process.

Candidate measures of open-ended learning include:

- **Novelty with relevance:** distinct newly identified residual classes that survive independent review.
- **Discriminative progress:** newly formulated tests that distinguish plausible competing hypotheses.
- **Transfer quality:** verified reuse of structural mechanisms in previously unseen domains.
- **Retained learning:** previously validated knowledge that remains useful under distribution shift.
- **Correction capacity:** time and evidence needed to retract a false claim.
- **Bounded operational impact:** maximum consequential exposure during learning and deployment.

Novelty alone is not success: a system that invents many unverifiable questions may become less useful.

## 4. Dual-Loop Grand Architecture

```text
Changing environment / authorized observations
                  |
                  v
       Typed SSU + UTN + Provenance
                  |
                  v
      REN + BCEF + Hypothesis Portfolio
                  |
                  v
       Security Residual Registry
                  |
                  v
        AQSI Question Portfolio
                  |
                  v
   Red / Blue / Evaluation Drives (sandbox)
                  |
                  v
     Candidate Improvements + Evidence
                  |
                  v
        Independent Validation
                  |
          proposal only
                  v
   +----------------------------------+
   | Independent Governance Gate      |
   | policy, authorization, audit,    |
   | exposure, staged rollout,        |
   | emergency stop and rollback      |
   +----------------------------------+
                  |
         approved transition
                  v
     Constrained execution / monitoring
                  |
                  v
   Residuals, outcomes, negative results
                  |
                  +----> Structural Relay Registry

    Hard safety and execution controls are
    independent of adaptive scoring authority.
```

The adaptive loop learns from data and experiments. The governance loop evaluates whether and how a proposed change can be used. Both loops require external scrutiny; calling a component “independent” is not evidence that it is independent.

## 5. Four Complementary Evolution Axes

### 5.1 Epistemic evolution

Improve what is known and how confidently it is known: provenance, alternative hypotheses, evidence dependencies, uncertainty, and falsification.

### 5.2 Structural evolution

Improve the representations themselves: new UTN types, compositional identity relationships, security-unit contracts, dependency graphs, and residual taxonomies.

### 5.3 Strategic evolution

Improve defensive portfolios: detection, containment, authorization, recovery, operational continuity, and countermeasure selection under competing objectives.

### 5.4 Institutional evolution

Improve governance processes: evaluator separation, conflict-of-interest handling, policy review, auditability, incident response, and revocation of unsafe changes.

The axes interact, but progress on one is not proof of progress on the others. A better evidence model can still be paired with an unsafe execution policy.

## 6. The Security Residual as an Evolution Seed

A **Security Residual** is a structured record of a discrepancy between a specified security objective and what the available evidence supports. It may describe:

- A demonstrated failure in an isolated experiment.
- A suspected gap requiring additional evidence.
- A control that is effective only under narrow assumptions.
- A missing or ambiguous identity/authorization relationship.
- An evaluation blind spot or benchmark overfit.
- A governance, recovery, or cross-domain transfer failure.

A residual is not necessarily a confirmed vulnerability. Each residual should contain an epistemic status, provenance, affected hypothesis, domain and time scope, potential consequence, severity rationale, and proposed discriminating test.

### 6.1 Residual-to-question transformation

A useful AQSI question identifies at least two distinguishable explanations and a feasible, authorized observation or experiment. Example:

**Residual:** A synthetic signing-service compromise caused an unauthorized transfer despite valid cryptographic signatures.

**Competing explanations:** (H1) independent policy enforcement was absent; (H2) policy enforcement existed but was bypassable; (H3) the policy allowed an unintended class of operations; (H4) a shared administrator compromised both signing and policy controls.

**Discriminating questions:** Which execution paths reached the asset without the independent enforcement point? Could a compromised common administrator modify both trust domains? Did canonical transaction binding cover the exact executed action?

These questions are more informative than merely asking whether the model can detect an anomaly.

## 7. AQSI Question Portfolio Governance

Questions should be treated as first-class, versioned Structural Security Units (SSUs). A question portfolio may consider:

\[
U(q) = F(\text{expected information gain},\text{risk relevance},
\text{testability},\text{novelty},\text{diversity},\text{cost},\text{authorization}).
\]

This is a conceptual prioritization function, not a calibrated probability or validated optimization formula. No single score should override hard experimentation constraints.

Question portfolios should retain:

1. Questions answered with independent support.
2. Questions refuted or shown ill-posed.
3. Questions unresolved because evidence is unavailable.
4. Questions deferred because exploration would exceed authorized risk.
5. Meta-questions about the adequacy of the current scoring, evaluator, or governance structure.

An unanswered question can be valuable knowledge when its missing evidence and boundary conditions are explicit.

## 8. Evidence Discipline: UTN, REN, BCEF, and MDT

### 8.1 UTN and compositional identity

Observed addresses, credentials, services, inferred controllers, teams, and independently verified subjects must retain distinct types. Identities may overlap and change over time. Identity inference must never itself grant authorization.

### 8.2 REN and directional weak evidence

Evidence relevance depends on the hypothesis, decision direction, context, and alternative explanations. Relevance is not truth, and weak evidence cannot be promoted into independent proof through repetition.

### 8.3 BCEF and hypothesis-scoped contradiction

Forward, reverse, counterfactual, and contradiction IF tests should preserve the exact proposition tested. Refuting “one person controlled both actions” does not refute “one team coordinated both actions.” Structured Impact may recommend revising a score or hypothesis graph but cannot bypass governance.

### 8.4 MDT and temporal provenance

The system must distinguish event time, observation time, assessment time, and policy-validity time. Changes should be append-only or otherwise auditably versioned. Corrections should not erase earlier decisions and their supporting evidence.

### 8.5 Preventing evidence laundering

Multiple agents repeating the same source are not independent witnesses. Every derived assertion should carry dependency references. A cycle of model-generated claims must not inflate confidence merely because each claim cites another.

## 9. Multi-Agent Ecology: Cooperation, Competition, and Independence

A useful ecology includes heterogeneous roles:

| Role | May do | Must not do |
|---|---|---|
| Red Drive | Propose authorized synthetic adversarial scenarios | Execute unauthorized live attacks |
| Blue Drive | Generate candidate defenses and recovery plans | Self-approve consequential deployment |
| Evaluation Drive | Test candidates against preregistered criteria | Conceal failed or unfavorable outcomes |
| Governance Drive | Review evidence, approve or reject controlled changes | Treat agent consensus as proof of safety |
| Evidence Steward | Preserve provenance, dependencies, and audit trails | Rewrite historical records without trace |
| Relay Coordinator | Transfer validated and unresolved knowledge | Reclassify unvalidated claims as established facts |

Independence requires attention to shared models, datasets, operators, infrastructure, incentives, and evaluation leakage. A nominally separate evaluator may still be correlated with the defender it evaluates.

## 10. Structural Relay as Cumulative, Correctable Learning

A Relay record should preserve a claim's full lifecycle:

```text
question -> hypothesis -> experiment -> evidence
        -> assessment -> review -> accepted/rejected/deferred
        -> versioned relay -> later revalidation or retraction
```

Relay acceptance is not evidence validation. Evidence validation is not deployment authorization. Repeated execution can contribute data, but repeated identical failures or successes do not automatically constitute independent evidence.

Useful Relay artifacts include counterexamples, failed transfers, negative results, dependency graphs, model limitations, and explicit leftover questions. **Retraction** is as important as publication: the registry must be able to invalidate earlier conclusions without deleting their history.

## 11. Governance Is a Separate Control Plane

A governance plane should define:

- **Policy ownership:** which human or institutional authority can approve each change class.
- **Scope:** affected assets, identities, services, and environments.
- **Risk budget:** allowable loss, exposure, operational disruption, and experiment cost.
- **Separation of duties:** distinct proposal, validation, approval, and execution responsibilities.
- **Promotion stages:** offline, isolated, shadow, limited rollout, general rollout.
- **Rollback:** preconditions, rollback artifacts, monitoring triggers, and responsible operators.
- **Emergency stop:** independently accessible controls with tested recovery paths.
- **Audit:** immutable or tamper-evident decision evidence and policy version history.

Governance must not be reduced to a model's final “safety score.” It is a set of accountable decision and execution authorities.

## 12. Non-Bypassable Safety: A Conditional Engineering Claim

The phrase *non-bypassable* is meaningful only relative to a stated threat model and a demonstrated enforcement topology. It cannot be asserted universally.

For a proposed protected action \(a\), define a policy check:

\[
\operatorname{Permit}(a) = \operatorname{AuthorizedSubject}(a)
\land \operatorname{IntentBound}(a)
\land \operatorname{PolicyAllows}(a)
\land \operatorname{ExposureWithinBudget}(a)
\land \operatorname{ExecutionBound}(a).
\]

This is a design sketch, not a complete implementation. A robust system must ensure that every consequential execution path is mediated by an enforcement point, that budgets are enforced atomically under concurrency, and that shared administrative dependencies do not silently defeat independence.

Where such coverage cannot be demonstrated, the safety claim must be weakened explicitly. Fail-closed behavior may protect assets while harming availability; that tradeoff must also be measured.

## 13. The Governance-of-Governance Problem

Even an independent governance plane can become obsolete, compromised, captured, or internally inconsistent. OESEG therefore separates three levels:

- **Level A — Operational policies:** asset limits, permissions, transaction binding, incident response.
- **Level B — Policy-change governance:** approval thresholds, independent review, testing, staged deployment.
- **Level C — Constitutional constraints:** who may amend Level B, emergency powers, oversight, audit retention, and dispute resolution.

No finite hierarchy proves its own correctness. The practical research aim is to make authority transitions explicit, accountable, reviewable, and bounded—not to claim an infinite chain of perfect supervisors.

Governance changes should be slower and more demanding than ordinary learning updates. In particular, an AI system should not be able to redefine the approval procedure that governs its own promotion.

## 14. Policy Evolution Without Authority Drift

**Authority drift** occurs when successive apparently small changes cumulatively expand a system's effective power beyond its approved scope. Controls should evaluate both individual changes and their combined effect.

Examples include:

- A new tool permission combined with an existing credential creates a previously unavailable transfer path.
- Two individually modest risk-budget increases produce an excessive aggregate exposure.
- A new identity merge indirectly grants a team the privileges of a verified individual.
- An emergency override becomes a routine workflow.

An authority-change review should compute a structural diff: newly reachable assets, newly executable actions, changed approval dependencies, enlarged risk envelopes, and reduced recovery options.

## 15. Candidate Promotion and Revalidation

A proposed defense must traverse explicit gates:

1. **Proposal registration:** immutable candidate ID, provenance, affected contracts.
2. **Static contract checks:** schema, type, permissions, dependencies, safety constraints.
3. **Isolated tests:** synthetic scenarios and regression suite.
4. **Independent adversarial evaluation:** previously unseen conditions and competing baselines.
5. **Governance review:** residual risk, business tradeoffs, authority changes, rollback plan.
6. **Limited promotion:** approved scope, exposure budget, monitoring, automatic stop criteria.
7. **Post-promotion validation:** measured outcomes, regressions, incident reports.
8. **Relay and revalidation:** preserve evidence and reopen claims after relevant change.

A candidate that passes one benchmark remains a candidate for other contexts. Performance under distribution shift must be established separately.

## 16. Recursive Budgets, Termination, and Exploration Rights

Open-ended learning does not imply infinite runtime. Every experimental cycle should specify limits on:

- Iterations and recursive depth.
- Compute, storage, and model calls.
- Time and operator attention.
- Synthetic environment resources.
- Data access and retention.
- Consequential asset exposure (normally zero for unapproved experiments).
- Number and scope of candidate promotions.

Termination events include budget exhaustion, insufficient evidence, unstable evaluator, policy conflict, suspected contamination, and emergency stop. A terminated cycle should still produce a useful residual or explicit unresolved-state record.

## 17. Canonical OESEG Units

The following proposed unit families extend SPEC-001 without replacing its canonical SSU envelope:

| Unit | Purpose | Key relationships |
|---|---|---|
| EvolutionCycleUnit | Bounded research iteration | Question, residual, policy, budget |
| SecurityResidualUnit | Typed unresolved or demonstrated gap | Evidence, affected objective |
| SecurityQuestionUnit | Falsifiable inquiry | Competing hypotheses, test plan |
| CandidateDefenseUnit | Proposed control change | Source residual, expected effect |
| ValidationRecordUnit | Independent experimental result | Candidate, baseline, evaluator |
| GovernanceDecisionUnit | Accountable approval or rejection | Authority, policy version, scope |
| PromotionRecordUnit | Controlled deployment transition | Gate results, rollout, rollback |
| RelayKnowledgeUnit | Portable, versioned learning | Evidence, status, retraction links |
| AuthorityDiffUnit | Change in effective permissions | Before/after reachability, reviewers |
| NegativeTransferUnit | Failed cross-domain analogy | Source/target semantics, failure |

Every unit should identify its epistemic status and distinguish proposed, observed, inferred, validated, and authorized states.

## 18. Proposed Machine-Readable Evolution Contract

The following YAML is **illustrative**, not a final normative schema:

```yaml
schema: assi.oeseg.evolution-cycle.v0.1.0
unit_id: assi:cycle:synthetic-0007
kind: EvolutionCycleUnit
status: proposed
scope:
  environment: isolated-synthetic-lab
  domain: synthetic-custody
  production_actions_allowed: false
inputs:
  residual_refs: [assi:residual:0042]
  question_refs: [assi:question:0093]
  evidence_refs: [assi:evidence:0114]
  provenance_required: true
hypotheses:
  - id: H1
    claim: independent-policy-enforcement-is-bypassable
  - id: H2
    claim: common-admin-compromises-both-control-domains
exploration:
  permitted_modes: [offline-analysis, isolated-simulation]
  prohibited_modes: [unauthorized-live-execution]
  max_iterations: 12
  max_runtime_minutes: 90
  asset_exposure_budget: 0
validation:
  independent_evaluator_required: true
  preregistered_metrics: [unauthorized-action-rate, false-block-rate]
  holdout_scenarios_required: true
  evidence_dependency_audit: true
governance:
  candidate_promotion: prohibited-until-separate-approval
  approval_authority_ref: assi:authority:lab-governance
  rollback_plan_required: true
  policy_change_requires_independent_review: true
relay:
  preserve_negative_results: true
  preserve_unresolved_questions: true
  allow_retraction: true
```

An implementation must validate all referenced units and permissions; a YAML field by itself does not enforce anything.

## 19. Proposed Conformance Invariants

The following are design requirements for a future conformant OESEG implementation, not claims that one already exists.

**OESEG-INV-01 — Typed provenance:** Every consequential claim identifies its source and derivation.

**OESEG-INV-02 — Epistemic separation:** A hypothesis is not represented as an observation or authorization.

**OESEG-INV-03 — Hypothesis scope:** Contradictions affect only the proposition and conditions tested.

**OESEG-INV-04 — Dependency awareness:** Derived and repeated evidence cannot be silently counted as independent.

**OESEG-INV-05 — Temporal traceability:** Material decisions retain time and policy-version context.

**OESEG-INV-06 — Independent promotion:** Proposal generation cannot self-authorize deployment.

**OESEG-INV-07 — Execution mediation:** Protected actions require independently governed enforcement.

**OESEG-INV-08 — Bounded experiments:** Every experimental cycle has explicit resource and exposure limits.

**OESEG-INV-09 — Evaluator separation:** Evaluation conflicts and shared dependencies are recorded.

**OESEG-INV-10 — No evidence laundering:** Agent consensus is not treated as independent evidence without provenance analysis.

**OESEG-INV-11 — Safe failure:** Missing required authorization results in hold or denial, not implicit permission.

**OESEG-INV-12 — Rollback readiness:** Consequential promotions require a tested rollback or a documented irreversibility decision.

**OESEG-INV-13 — Authority-diff review:** Changes that expand effective power require independent review.

**OESEG-INV-14 — Governance versioning:** Policy and approval-procedure changes are auditably versioned.

**OESEG-INV-15 — No governance self-rewrite:** Adaptive agents cannot unilaterally change their own approval rules.

**OESEG-INV-16 — Retraction support:** Relay claims can be corrected or invalidated without erasing history.

**OESEG-INV-17 — Negative-result preservation:** Failed experiments and failed transfers remain inspectable.

**OESEG-INV-18 — Domain-specific authority:** Cross-domain transfer never imports source-domain execution privileges.

**OESEG-INV-19 — Distribution-shift review:** Significant context changes trigger claim revalidation.

**OESEG-INV-20 — Emergency control:** Stop and recovery procedures are independently accessible and tested.

**OESEG-INV-21 — Common-mode analysis:** Independence claims account for shared operators, infrastructure, and credentials.

**OESEG-INV-22 — Human accountability:** Consequential governance decisions identify accountable authorities.

**OESEG-INV-23 — Observable failure:** Monitoring detects when declared safety assumptions no longer hold.

**OESEG-INV-24 — Honest status:** No unrun benchmark, unverified hypothesis, or untested control is presented as validated.

## 20. Synthetic Laboratory Portfolio

### LAB-O1 — Residual-Driven Open-Ended Discovery

**Question:** Does AQSI identify useful previously hidden residual classes more effectively than a fixed checklist?

**Setup:** Generate a sequence of synthetic custody environments with new combinations of permissions, services, and workflows. Hide selected failure mechanisms from the question generator and from the initial benchmark suite.

**Measure:** independently confirmed novel residuals, redundant questions, false alarms, test cost, and time to discriminating experiment.

**Failure condition:** increased question volume without improved independently validated discovery.

### LAB-O2 — Competitive Relay Under Correlated Agents

**Question:** Does structural provenance prevent false consensus when multiple agents share the same erroneous source?

**Setup:** Multiple synthetic agents receive partially overlapping evidence; some are derived from a common misleading observation. Compare naive voting with provenance-aware Relay.

**Measure:** false confidence amplification, dependency-detection recall, correct retraction rate, and evaluation cost.

**Failure condition:** structured Relay reinforces unsupported conclusions as much as naive aggregation.

### LAB-O3 — Governed RSI Under Evaluator Shift

**Question:** Can candidate improvements survive changes to the evaluator and unseen scenario distributions?

**Setup:** Generate Blue candidates against one benchmark, then independently evaluate on held-out scenario families and a separately designed evaluator.

**Measure:** sample-out performance, regression rate, promotion errors, and rollback time.

**Failure condition:** gains disappear or become negative after independent evaluation.

### LAB-O4 — Authority Drift and Governance Capture

**Question:** Can an authority-diff gate detect unsafe cumulative privilege expansion that per-change reviews miss?

**Setup:** Construct synthetic sequences of individually plausible policy changes that jointly create a prohibited execution path. Include shared-administrator and emergency-override cases.

**Measure:** drift detection, missed prohibited paths, false rejections, and review latency.

**Failure condition:** policy drift remains undetected or review becomes operationally unusable.

### LAB-O5 — Cross-Domain Evolution and Negative Transfer

**Question:** Does retaining negative transfer records improve future adaptation from custody to cloud IAM, enterprise approval, AI-agent tools, and release pipelines?

**Setup:** Use typed source-target mappings with seeded semantic mismatches; compare transfer with and without a Non-Transfer Register.

**Measure:** unsafe mapping rate, time to correct mapping, cross-domain detection quality, and false authority inference.

**Failure condition:** no measurable improvement or new transfer-induced security errors.

### LAB-O6 — Independent Control Under Adaptive-System Failure

**Question:** Do independent controls bound loss when the adaptive defense is intentionally wrong or unavailable?

**Setup:** In an isolated synthetic environment, inject incorrect scores, missing evidence, compromised signing service, delayed approvals, and common-mode control failures.

**Measure:** unauthorized action rate, worst-case exposure, availability cost, enforcement-path coverage, and recovery success.

**Failure condition:** protected execution bypasses the claimed control or exposure exceeds the declared bound.

## 21. Benchmark Baselines and Ablation Matrix

| Baseline | Configuration | Purpose |
|---|---|---|
| B0 | Fixed controls, no adaptive discovery | Operational reference |
| B1 | Static checklist plus human review | Conventional question discovery |
| B2 | Single adaptive agent, no provenance graph | Isolate provenance benefit |
| B3 | Multi-agent voting, no independence checks | Expose false consensus |
| B4 | Structural Relay without independent validation | Isolate validation gate |
| B5 | Validated RSI without AQSI | Isolate autonomous questioning |
| B6 | AQSI + Relay + independent validation | Isolate governance and authority review |
| B7 | Full OESEG with independent governance and controls | Proposed integrated system |

Ablations should independently remove UTN compositional identity, REN directional evidence, BCEF hypothesis-scoped tests, dependency-aware provenance, authority-diff review, holdout evaluation, negative-result retention, and rollback gates.

Comparisons must hold experiment budgets and access to evidence as constant as practicable. If a baseline receives less information or fewer resources, the comparison must report that asymmetry.

## 22. Falsifiable Research Hypotheses

The following are **hypotheses**, not demonstrated results.

**H-OE-01 — Discovery yield:** Under matched budgets, residual-driven AQSI finds more independently confirmed unseen residual classes than a fixed question checklist.

**H-OE-02 — Question efficiency:** Portfolio selection yields more useful discriminating tests per unit cost than novelty-only selection.

**H-OE-03 — Evidence integrity:** Dependency-aware Relay reduces false consensus amplification relative to naive multi-agent voting.

**H-OE-04 — Scoped revision:** BCEF reduces incorrect hypothesis rejection without unacceptable loss of correct rejection recall.

**H-OE-05 — Governance effectiveness:** Independent promotion gates reduce unsafe candidate deployment relative to self-approval.

**H-OE-06 — Generalization:** Improvements selected through independent holdout evaluation perform better under scenario shift than in-sample-only selection.

**H-OE-07 — Authority drift:** Structural authority-diff review detects cumulative privilege expansion missed by per-change policy review.

**H-OE-08 — Bounded loss:** Independently mediated execution reduces unauthorized consequential actions under compromised adaptive components.

**H-OE-09 — Negative transfer:** A versioned Non-Transfer Register reduces repeated cross-domain mapping errors.

**H-OE-10 — Correction capacity:** Explicit retraction and provenance reduce time to correct false security claims.

**H-OE-11 — Institutional resilience:** Tested emergency controls improve recovery under governance or evaluator failures without unacceptable availability degradation.

**H-OE-12 — Longitudinal utility:** The integrated system retains useful defensive performance across multiple evolving environment generations better than a fixed-policy baseline.

Each hypothesis requires preregistered metrics, uncertainty estimates, an independent test set, and a failure threshold before experimental results are interpreted.

## 23. Evaluation Metrics and Reporting

### 23.1 Security outcomes

- Unauthorized consequential action rate.
- Maximum and distribution of realized or simulated exposure.
- False block / false approval rates.
- Detection and containment latency.
- Recovery time and rollback success.

### 23.2 Knowledge outcomes

- Independently validated residual discovery rate.
- Novel useful question rate, not raw question count.
- Hypothesis calibration and correct retraction.
- Evidence dependency and contradiction-scope error rates.
- Negative transfer recurrence.

### 23.3 Governance outcomes

- Unauthorized policy-change attempts blocked.
- Authority-drift detection recall and false positives.
- Evaluator independence and contamination findings.
- Promotion regression rate.
- Governance workload and decision latency.

### 23.4 Longitudinal outcomes

- Performance under new assets, actors, and workflows.
- Stability under distribution shift.
- Cost per validated improvement.
- Persistence of previously corrected failure modes.
- Resilience to shared infrastructure and institutional failures.

Report both means and adverse tails. A defense that improves average detection but creates rare catastrophic execution paths may be worse overall.

## 24. Threats to Validity

### 24.1 Simulation realism

Synthetic environments may omit social engineering, institutional incentives, unknown dependencies, and real-world recovery constraints. Passing a synthetic benchmark does not establish deployment safety.

### 24.2 Benchmark contamination

Agent or evaluator familiarity with test scenarios can produce apparent improvement without genuine generalization. Use independent scenario authorship, holdouts, and audit trails.

### 24.3 Common-mode failure

Separate agents may share training data, toolchains, credentials, cloud accounts, or organizational incentives. Independence must be measured, not presumed.

### 24.4 Measurement ambiguity

Security outcomes can be sparse, delayed, and costly to observe. Proxy metrics may be gamed. Explicitly distinguish direct observations from inferred security benefits.

### 24.5 Governance capture

Human governance can be inconsistent, slow, or compromised. Formal approval steps alone do not prove accountability or independence.

### 24.6 Overconstraint

Fail-closed controls can damage availability, liquidity, or incident response. Security evaluation must include operational harm and recovery costs.

## 25. Counterarguments and Design Responses

**Counterargument A: Open-ended security is impossible to validate because the future is unknown.**  
Response: Universal validation is impossible; bounded claims under specified distributions and threat models remain testable. Revalidation and explicit unknowns are central, not optional.

**Counterargument B: Governance will slow innovation until adaptation is useless.**  
Response: Separate low-risk offline exploration from consequential deployment. Apply risk-proportionate gates and measure approval latency rather than eliminating oversight.

**Counterargument C: More agents only produce more noise.**  
Response: That is a credible failure mode. Heterogeneity, provenance, adversarial evaluation, and ablation studies must demonstrate whether the ecology adds value.

**Counterargument D: A sufficiently capable AI could govern itself.**  
Response: Capability does not establish legitimate authority, accountability, or absence of correlated error. Self-governance may be studied, but cannot be assumed to satisfy independent authorization requirements.

**Counterargument E: Structural security is too general to be useful.**  
Response: The kernel should remain narrow and typed; domain adapters must own actual policy semantics. Failed mappings should be recorded rather than forced into a universal analogy.

## 26. Staged Validation Roadmap

**Phase 0 — Contract consistency.** Reconcile EXT-004 with SPEC-001–006; verify unit typing, lifecycle states, authority boundaries, and provenance fields.

**Phase 1 — Synthetic baseline suite.** Implement fixed-rule and static-question baselines with reproducible data and seeded failures.

**Phase 2 — Evidence and identity layer.** Add UTN, REN, BCEF, dependency graphs, and explicit hypothesis portfolios; test false merge/split and false rejection.

**Phase 3 — Multi-agent Relay.** Add distinct Red/Blue/Evaluation/Governance roles, with provenance-aware knowledge exchange and negative-result retention.

**Phase 4 — Governed candidate evolution.** Implement candidate promotion gates, authority-diff review, rollback, budget controls, and independent evaluation.

**Phase 5 — Cross-domain holdouts.** Test cloud, enterprise, AI-agent, and supply-chain adapters; measure negative transfer and semantic mismatch.

**Phase 6 — Independent replication.** Publish benchmark contracts, synthetic generators, failure cases, evaluation criteria, and limitations for third-party review.

**Phase 7 — Limited real-world study, only if authorized.** Any operational pilot requires independent security review, explicitly bounded exposure, accountable operators, and rehearsed rollback. This phase is not implied by completion of earlier phases.

## 27. Open Research Questions

1. How can a system distinguish genuinely new security structure from renamed variants of known failures?
2. What is the right unit of evidence independence in a multi-agent ecosystem?
3. How should governance adapt when policy conflicts are discovered but no safe resolution is known?
4. Can authority drift be detected efficiently in large, evolving compositional permission graphs?
5. Which security questions have the highest long-run value when outcomes are delayed or unobservable?
6. How can retraction propagate across already-consumed Relay artifacts?
7. What forms of negative transfer generalize without becoming overly conservative?
8. How should rare catastrophic outcomes be weighted against everyday operational continuity?
9. Can governance diversity reduce common-mode failures without creating paralysis?
10. What minimum independently enforced safety kernel is required for a meaningful bounded-loss claim?
11. When should a recurring residual trigger redesign of the representation rather than another scoring adjustment?
12. How can longitudinal improvement be established when environments and evaluation objectives both evolve?

## 28. Relationship to the ASSI Research Series

| Prior work | Contribution to EXT-004 |
|---|---|
| ASSI-001–003 | Structural security contradictions and trust relocation |
| ASSI-004–006 | Compositional identity, REN, BCEF, and evidence discipline |
| ASSI-007 | Independent authorization and bounded-loss reasoning |
| ASSI-008–009 | Adversarial Drives, residuals, and Validated RSI |
| ASSI-010–011 | Grand architecture and falsifiable benchmark laboratories |
| ASSI-012 | General structural defense and domain adapters |
| SPEC-001–003 | SSU, UTN, and evidence-impact contracts |
| SPEC-004–006 | Safety control, adversarial Relay, RSI, and governance contracts |
| CASE-001–005 | Synthetic custody, identity, conditional evidence, and adversarial laboratories |
| EXT-001 | Multi-agent security ecology |
| EXT-002 | Autonomous security questioning and exploration |
| EXT-003 | Cross-domain structural security transfer and negative transfer |

EXT-004 is a research synthesis and forward extension. It does not replace the more specific normative contracts, nor does it claim those contracts have already been implemented.

## 29. Conclusion

Open-ended security evolution is best understood not as an endlessly self-modifying defense, but as a **continuously revisable, independently evaluated, and governably deployable research-and-defense ecosystem**. Its strength would come from discovering new residuals, asking better questions, retaining competing explanations, preserving provenance, testing adversarially, and learning from both successful and failed transfers. Its legitimacy would come from separate authorization, accountable governance, bounded exposure, auditability, and correction mechanisms.

The architectural separation is fundamental: intelligence can propose, evidence can support, independent evaluation can challenge, governance can authorize, and execution controls must enforce. None of these functions should silently collapse into the others.

> **Keep discovery open-ended, evidence revisable, authority bounded, governance accountable, and failure learnable.**

That is the research direction proposed by OESEG. Whether it yields measurable improvements remains an open empirical question.

---

## Appendix A — Suggested Conformance Test Vectors

| ID | Synthetic condition | Expected result |
|---|---|---|
| OE-T01 | New residual with valid provenance | Register as unresolved; not automatically validated |
| OE-T02 | Agent repeats its own derived evidence | Dependency flagged; no independent confidence gain |
| OE-T03 | Single-controller hypothesis contradicted | Preserve compatible team hypothesis |
| OE-T04 | Candidate attempts self-promotion | Reject without independent authorization |
| OE-T05 | Policy changes cumulatively create new asset path | Require authority-diff review |
| OE-T06 | Experiment exceeds iteration budget | Terminate and preserve partial results |
| OE-T07 | Evaluation and Blue share hidden test data | Record contamination; invalidate affected claim |
| OE-T08 | Cross-domain mapping imports source permissions | Reject transfer of authority |
| OE-T09 | Relay claim is later refuted | Publish retraction and dependent-claim review |
| OE-T10 | Emergency stop invoked during rollout | Stop execution and enter approved recovery workflow |
| OE-T11 | Common administrator compromises two nominally separate controls | Mark independence assumption failed |
| OE-T12 | Missing required evidence | Unknown/hold, not implicit approval |
| OE-T13 | Unseen scenario reduces candidate performance | Block promotion or trigger rollback review |
| OE-T14 | Negative transfer recorded | Preserve source-target failure rationale |
| OE-T15 | Governance rule amendment proposed by adaptive agent | Require independent constitutional approval |
| OE-T16 | Successful synthetic benchmark | Report bounded experimental result only |

## Appendix B — Minimal Experiment Report Template

```yaml
experiment_id: assi:oe:experiment:001
version: 0.1.0
status: planned
question_ref: assi:question:0093
hypothesis_ids: [H-OE-01]
scenario_generator_version: synthetic-v1
baseline_ids: [B0, B1, B7]
preregistered_metrics:
  - independently_validated_residual_discovery_rate
  - false_discovery_rate
  - cost_per_validated_discovery
holdout_policy: independent-scenario-author
shared_dependency_audit: required
safety:
  environment: isolated
  live_assets: prohibited
  experiment_budget: bounded
results: null
limitations:
  - synthetic_only
independent_reviewer: pending
promotion_authorization: none
```

## Appendix C — Research and Publication Integrity Checklist

- [ ] Distinguish proposal, implementation, experiment, and validated result.
- [ ] Define the threat model and scope of every safety claim.
- [ ] Identify all synthetic data and simulated outcomes.
- [ ] Record baselines, holdouts, and independent evaluator dependencies.
- [ ] Preserve negative results, retractions, and failed transfers.
- [ ] Avoid claims that agent consensus proves independence.
- [ ] Verify that authority never follows automatically from identity inference or scoring.
- [ ] Review shared infrastructure and administrative control paths.
- [ ] Document experiment budgets, emergency stop, and recovery.
- [ ] Require independent approval before consequential deployment.
- [ ] Publish limitations and open questions alongside successful findings.

---

**Repository placement:** `extensions/EXT-004-Open-Ended-Security-Evolution-and-Governance.md`  
**Previous extension:** `extensions/EXT-003-Cross-Domain-Structural-Security-Transfer.md`  
**Series status:** EXT-001–004 complete as research drafts; validation and implementation remain future work.
