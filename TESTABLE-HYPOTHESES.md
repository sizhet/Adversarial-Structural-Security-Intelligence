# TESTABLE HYPOTHESES — Adversarial Structural Security Intelligence (ASSI)

**Release:** v0.1.0 — Research Foundation  
**Document type:** Pre-registered hypothesis candidates and falsifiable experimental protocols  
**Status:** Proposed and untested; no benchmark outcomes, certifications, or deployment guarantees are claimed  
**Repository location:** `TESTABLE-HYPOTHESES.md`  
**License:** Apache-2.0  
**Date:** 2026-11-02

> **Non-negotiable boundaries:** Cryptographic validity ≠ legitimate authorization. Evidence ≠ authority. Simulation ≠ independent validation. Validation ≠ deployment approval. A proposed improvement cannot approve its own release.

## 1. Purpose and epistemic status

This register converts questions from [OPEN-QUESTIONS.md](OPEN-QUESTIONS.md) and priorities from [FUTURE-DIRECTIONS.md](FUTURE-DIRECTIONS.md) into experimentally discriminable hypotheses. It is a **prospective research design**, not a results report. All numerical thresholds below are *illustrative preregistration targets* and must be fixed before examining held-out results. None is an observed ASSI performance figure.

The research program investigates whether typed structural identity, directionally evaluated evidence, bidirectional conditional evidence feedback (BCEF), independently enforced authorization, adversarial relay, and validated recursive improvement can improve security decisions over specified baselines **without increasing unacceptable false rejection, unauthorized action, correlated evidence amplification, or governance drift**.

Experiments must be synthetic, simulated, or explicitly authorized. Public-chain analysis, if ever undertaken, must not be treated as proof of beneficial ownership, intent, or legal identity. No experiment requires live exploitation, real funds, credential disclosure, or unapproved production interventions.

### 1.1 Claim levels

| Level | Meaning | Permitted wording |
|---|---|---|
| H0 | Untested conjecture | “We hypothesize…” |
| H1 | Reproducible synthetic observation | “Under the specified synthetic threat model…” |
| H2 | Independent replication across implementations | “Replicated within the stated evaluation scope…” |
| H3 | Authorized, bounded field evaluation | “Observed in this authorized setting…” |
| H4 | Deployment decision | A separate governance determination, never inferred automatically from H1–H3 |

Evidence may support a claim at one level without warranting the next. Null findings and failures remain first-class results.

## 2. Experimental conventions and contracts

**Unit of analysis.** A *Structural Security Unit (SSU)* binds an asset/action, identity hypotheses, time interval, evidence provenance, threat model, policy version, authority boundary, decision, and audit record. An SSU is not a universal person identifier and does not grant permission.

**Baseline families.** B0 = signature/credential validity alone; B1 = static rules and manually curated entity links; B2 = conventional graph or anomaly scoring without temporal/hypothesis provenance; B3 = structural scoring without independent enforcement; B4 = an otherwise comparable non-adversarial learning loop. A baseline must be realistically tuned, not intentionally weakened.

**Evaluation discipline.** Use pre-registered datasets, random seeds, split strategy, threshold-selection procedure, compute budgets, and threat assumptions. Separate training, tuning, and untouched test partitions; split by entity, campaign, time, and causal family where appropriate. Report confidence intervals, paired comparisons, calibration, subgroup performance, worst-case results, latency, cost, and failure modes. Blind evaluators to treatment labels where feasible. Correct for multiple comparisons across large hypothesis families.

**Primary metrics.** Depending on the test: false-positive rate (FPR), false-negative rate (FNR), precision–recall AUC (PR-AUC), calibration error, time-to-detection, unauthorized execution rate, legitimate-action denial rate, bounded-loss exceedance, evidence duplication factor, recovery time, independent replication rate, and governance violation count. Report base rates; accuracy alone is insufficient for rare attacks.

**Safety invariant.** No inference or model output can directly mint authority, override a policy enforcement point (PEP), expand a risk budget, or deploy a new control. A policy decision point (PDP) and independent review must govern actions, including emergency response.

## 3. Canonical hypothesis contract

Each hypothesis uses a stable `TH-XX` identifier and should ultimately have a machine-readable record. Minimum fields:

```yaml
hypothesis_id: TH-XX
claim: "Precisely bounded and falsifiable claim"
competing_explanations: ["baseline", "data leakage", "confounding"]
experimental_unit: "SSU / event / campaign / policy decision"
threat_model: "Capabilities, observations, exclusions, authority"
intervention: "One controlled mechanism change"
baselines: ["B1", "B2"]
primary_endpoint: "Metric and aggregation rule"
guardrails: ["FPR", "denial rate", "policy violations"]
preregistration: "Dataset, split, threshold, sample size, seed, analysis"
falsification_rule: "Outcome that defeats the claim"
replication: "Independent implementation or held-out family"
authority_boundary: "No deployment or asset action without approval"
status: proposed
```

A positive result is invalidated or downgraded when it depends on label leakage, non-independent evidence, selective reporting, a weakened baseline, an unauthorized intervention, or post hoc threshold adjustment. The test owner must record negative outcomes as carefully as positive ones.

## 4. Family A — Structural trust, contradictions, and bounded loss

### TH-01 — Valid signature is an insufficient predictor of authorized intent

**Claim.** In synthetic workflows containing compromised but cryptographically valid signing credentials, a policy-aware structural model will distinguish authorized from unauthorized transactions better than signature-only validation (B0).

- **Design:** Construct matched valid-signature transactions with varying mandate, transaction context, delegation, revocation, and session integrity; preserve identical cryptographic validity.
- **Primary endpoint:** Unauthorized-action detection recall at a pre-registered legitimate-denial ceiling.
- **Controls:** B0 and a tuned static policy baseline (B1); stratify by compromise type.
- **Falsification:** No meaningful improvement over B1 on unseen compromise families, or improvement requires unacceptable denial of legitimate actions.
- **Scope:** Detection only; model decisions cannot authorize or block live transactions without an independent PEP.

### TH-02 — Explicit trust-boundary mapping improves failure localization

**Claim.** Modeling trust relocation across signer, custodian, identity provider, oracle, operator, and recovery authority reduces missed single-point and common-mode failures relative to component-only review.

- **Design:** Generate synthetic dependency graphs with concealed shared administrators, keys, infrastructure, or recovery paths; compare blind review teams with and without trust-boundary diagrams.
- **Endpoint:** Recall of planted trust concentrations, adjusted for review time and false alerts.
- **Falsification:** No improvement under blinded evaluation, or higher recall is fully explained by additional review time.

### TH-03 — Risk budgets reduce tail exposure without excessive service denial

**Claim.** Independently enforced transaction-scoped budgets reduce worst-case simulated loss under compromised control paths relative to unbounded reactive scoring.

- **Design:** Simulate asset transfer sequences with adversarial timing and legitimate bursts; compare B3 with fixed budget, adaptive budget, and approval-gated budget variants.
- **Endpoint:** 95th/99th percentile cumulative loss and budget-exceedance rate; guardrail: legitimate completion and latency.
- **Falsification:** Tail reduction is absent, bypassable, or achieved only by denying most legitimate work.

### TH-04 — Contradiction registers improve review reproducibility

**Claim.** Explicitly recording autonomy/control, identity/authorization, efficiency/safety, and evolution/stability tensions increases agreement on unresolved security risks among independent reviewers.

- **Design:** Randomize reviewers to standard narrative risk reports versus typed contradiction registers with identical underlying evidence.
- **Endpoint:** Inter-rater agreement, discovered contradictory assumptions, and time to decision.
- **Falsification:** No reproducibility gain or materially greater unresolvable disagreement.

## 5. Family B — UTN, compositional identity, and temporal structure

### TH-05 — Temporal compositional identity improves entity-resolution calibration

**Claim.** A typed, time-indexed UTN representation yields better calibrated identity-hypothesis probabilities than static address/entity clustering on synthetic multi-controller scenarios.

- **Design:** Vary shared devices, custodial pooling, delegated signing, ownership transitions, and adversarial decoys; retain known synthetic ground truth.
- **Endpoint:** Brier score and expected calibration error, with precision–recall by identity relation.
- **Controls:** Static graph clustering (B2), manually specified rules (B1), and ablations without time or relation typing.
- **Falsification:** Calibration is not improved on held-out entity families, or temporal modeling causes unstable merges.

### TH-06 — Competing identity hypotheses reduce irreversible false merges

**Claim.** Maintaining multiple scoped identity hypotheses rather than immediately collapsing nodes reduces erroneous high-impact merges while preserving useful investigation recall.

- **Design:** Synthetic near-duplicate controllers, key rotations, shared custody, and delegated agents; compare hard merge, soft merge, and hypothesis portfolios.
- **Endpoint:** High-impact false-merge rate at matched recall; secondary: memory and compute cost.
- **Falsification:** False merges do not decline, or hypothesis maintenance becomes infeasible at pre-registered scale.

### TH-07 — Identity provenance limits evidence laundering

**Claim.** Requiring typed provenance for identity edges reduces the amplification of unverified third-party assertions through transitive graph propagation.

- **Design:** Inject repeated, correlated, and forged-but-plausible assertions into a synthetic provenance graph; vary source independence.
- **Endpoint:** Rate at which unsupported claims cross a pre-registered confidence threshold.
- **Falsification:** Provenance checks do not reduce unsupported escalation or simply conceal uncertainty.

### TH-08 — Temporal differential trees detect meaningful identity changes earlier

**Claim.** MDT-style delta representations detect authorized-to-compromised control transitions earlier than snapshot-only identity scoring at matched false-alarm rates.

- **Design:** Generate change points involving credential takeover, delegation expiration, recovery events, and benign rotations.
- **Endpoint:** Detection delay and false alerts per simulated operating month.
- **Falsification:** No delay advantage after matching model capacity, features, and observation windows.

## 6. Family C — REN, weak evidence, and BCEF

### TH-09 — Directional weak evidence adds value under sparse observations

**Claim.** Direction-aware REN scoring improves ranking of investigatory hypotheses over symmetric similarity alone when evidence is sparse and causal direction matters.

- **Design:** Construct paired cases with equal feature similarity but opposite temporal/causal directions; compare REN-aware and symmetric models.
- **Endpoint:** Pairwise ranking accuracy and calibration; report performance as evidence density varies.
- **Falsification:** No advantage on held-out causal patterns, or gains disappear under balanced baselines.

### TH-10 — Source-dependence adjustment prevents double-counting

**Claim.** Explicit correlation and provenance accounting reduces overconfidence from duplicated evidence without suppressing genuinely independent corroboration.

- **Design:** Inject duplicated reports, paraphrased reports, common upstream feeds, and independent confirmations with matched surface diversity.
- **Endpoint:** Calibration error, false escalation rate, and sensitivity to independent confirmations.
- **Falsification:** Overconfidence persists or valid corroboration is systematically discarded.

### TH-11 — Hypothesis-scoped contradictions reduce false rejection

**Claim.** BCEF contradictions targeted to specific hypotheses reduce global false rejection compared with binary rejection of an entire identity or event record.

- **Design:** Include records where one identity explanation is contradicted but an alternative remains plausible; compare global rejection and scoped updates.
- **Endpoint:** False-rejection rate at matched contradiction-detection recall.
- **Falsification:** No improvement, or scoped updates preserve hypotheses that should be excluded under the registered threat model.

### TH-12 — Four-way IF testing exposes otherwise hidden ambiguity

**Claim.** Combining forward, reverse, counterfactual, and contradiction IF tests reveals more model errors than forward-only inference on structurally ambiguous synthetic cases.

- **Design:** Prepare matched question sets with hidden reverse-causation, missing-counterfactual, and incompatible-assumption traps; randomize test order.
- **Endpoint:** Distinct confirmed errors found per unit review cost.
- **Falsification:** Added tests yield no unique confirmed errors or mainly create spurious contradictions.

### TH-13 — BCEF improves evidence-update consistency

**Claim.** Typed evidence-impact updates reduce order sensitivity and contradictory scoring-tree states relative to unstructured additive updates.

- **Design:** Present the same evidence in varied orders, including retractions, corrections, and source merges; compare update strategies.
- **Endpoint:** Final-state divergence, invariant violations, and audit reconstruction success.
- **Falsification:** No reduction in order dependence or an increase in silent evidence loss.

### TH-14 — Explicit unknown states improve calibrated abstention

**Claim.** Four-valued or multi-state evidence handling (supported, contradicted, both, unknown) yields safer abstention than forced binary classification under incomplete evidence.

- **Design:** Randomly censor evidence and introduce genuine contradictions; compare forced labels, confidence-threshold abstention, and typed states.
- **Endpoint:** Risk–coverage curve and unsupported definitive-decision rate.
- **Falsification:** No improvement after matching abstention rates or unacceptable loss of coverage.

## 7. Family D — Authorization, independent control, and recovery

### TH-15 — Independent PEP blocks unauthorized model-induced actions

**Claim.** A separately administered policy enforcement point prevents unauthorized execution when a detection or planning model is manipulated, unlike a model-integrated allow/deny decision alone.

- **Design:** In an isolated simulator, inject malicious or mistaken model recommendations while preserving independent policy state.
- **Endpoint:** Unauthorized execution count and policy bypass rate; target invariant: zero within the tested model.
- **Falsification:** Any demonstrated policy bypass, including via stale state, fail-open behavior, or indirect actuation.
- **Caveat:** Zero failures in finite tests does not establish universal security.

### TH-16 — Transaction binding prevents replay across authorization contexts

**Claim.** Binding approval to action digest, beneficiary, amount, scope, time window, policy version, and nonce reduces simulated replay or context-substitution acceptance relative to generic approval tokens.

- **Design:** Generate approved actions and near-neighbor altered requests; test a contract-based verifier against a weak approval-token baseline.
- **Endpoint:** Acceptance of materially altered or replayed requests; guardrail: rejection of valid retries.
- **Falsification:** Accepted altered requests or legitimate retry failure above the pre-registered limit.

### TH-17 — Separate recovery authority reduces persistent compromise

**Claim.** Independent recovery credentials and bounded emergency controls shorten compromise persistence without creating a more powerful single recovery backdoor.

- **Design:** Simulate signer compromise, emergency freezes, recovery handoffs, and recovery-authority compromise.
- **Endpoint:** Time to safe containment, irreversible loss, and recovery privilege concentration.
- **Falsification:** Recovery increases worst-case loss, concentrates authority, or fails during plausible common-mode outages.

### TH-18 — Explicit authority boundaries constrain governance drift

**Claim.** Machine-checkable authority contracts reduce unauthorized scope expansion during policy revisions compared with prose-only governance.

- **Design:** Randomize policy-change proposals with benign and adversarial scope changes; evaluate contract checks and blinded governance reviewers.
- **Endpoint:** Undetected privilege expansions and false rejection of legitimate changes.
- **Falsification:** Scope drift passes checks or excessive false blocks prevent routine maintenance.

## 8. Family E — Adversarial drives, security residuals, and relay

### TH-19 — Independent adversarial roles discover distinct failure classes

**Claim.** Separated Red, Blue, Evaluation, and Governance drives discover more nonredundant failure modes than a single agent/team with equal total compute and time.

- **Design:** Run isolated synthetic challenges with fixed budgets; require independent adjudication and deduplicate findings by root cause.
- **Endpoint:** Independently confirmed unique failure classes per budget unit.
- **Falsification:** No gain after equalizing resources or gains derive from repeated unverified claims.

### TH-20 — Evaluation isolation reduces reward and benchmark contamination

**Claim.** Separating evaluator data, criteria, and release authority from proposing agents reduces benchmark overfitting and self-certification.

- **Design:** Compare visible-test optimization with blind held-out evaluation; include deliberately misleading training feedback.
- **Endpoint:** Held-out robustness gap and rate of unsupported release claims.
- **Falsification:** No gap reduction or evidence of evaluator leakage/collusion.

### TH-21 — Typed security residuals improve regression prevention

**Claim.** Recording failure as a typed Security Residual with trigger, evidence, violated invariant, reproduction, and ownership reduces recurrence compared with narrative bug tickets.

- **Design:** Assign independent teams to address seeded synthetic defects with equivalent time; compare typed versus narrative handoff.
- **Endpoint:** Recurrence on held-out variants and time to reproduce.
- **Falsification:** No improvement or a documentation overhead that exceeds the measured benefit.

### TH-22 — Competitive relay outperforms unstructured multi-agent consensus

**Claim.** Competitive, provenance-preserving relay produces better calibrated decisions than unstructured consensus when multiple agents share correlated upstream evidence.

- **Design:** Vary agent count, shared data sources, coordinated errors, and independent review; compare majority vote, weighted vote, and typed relay.
- **Endpoint:** Calibration, correlated-failure rate, and adjudication cost.
- **Falsification:** No improvement or persistent hidden consensus amplification.

## 9. Family F — AQSI, validated RSI, and governance

### TH-23 — Autonomous questioning identifies higher-value unknowns

**Claim.** AQSI-guided question selection finds more independently verified security-relevant unknowns per fixed investigation budget than random, novelty-only, or uncertainty-only selection.

- **Design:** Provide synthetic hidden-failure corpora; compare question portfolios with matched model and tool access.
- **Endpoint:** Verified new failure classes per cost; secondary: diversity and false lead rate.
- **Falsification:** No advantage on held-out domains or improvement driven by evaluation-label leakage.

### TH-24 — Residual-guided improvement transfers beyond seen examples

**Claim.** Security Residual–guided candidate modifications improve robustness on held-out causal variants rather than merely memorizing known failures.

- **Design:** Partition seeded defects by root-cause family; train or revise on some families and evaluate blind on others.
- **Endpoint:** Held-out reduction in verified failures at matched false-positive rate.
- **Falsification:** Gains are confined to seen variants or worsen unrelated safety invariants.

### TH-25 — Independent validation catches self-improvement regressions

**Claim.** A separate validation authority with immutable test criteria detects more harmful candidate changes than self-evaluation alone.

- **Design:** Introduce candidate changes with known synthetic regressions and deceptive apparent gains; compare self-test and independent gate.
- **Endpoint:** Harmful candidate acceptance rate and legitimate candidate rejection rate.
- **Falsification:** Independent gate fails to detect seeded regressions or blocks essentially all improvements.

### TH-26 — Recursive improvement requires bounded authority and rollback

**Claim.** Versioned contracts, scoped permissions, approval gates, and rollback reduce cumulative safety-invariant violations across iterative improvement cycles.

- **Design:** Run controlled, non-deploying simulated update sequences with and without independent governance; inject drift opportunities.
- **Endpoint:** Violations per iteration, rollback success, and improvement retention.
- **Falsification:** Uncontrolled drift, ineffective rollback, or no advantage at matched update cadence.

## 10. Family G — Cross-domain transfer and open-ended evolution

### TH-27 — Structural patterns transfer better than surface features

**Claim.** A contract-level security pattern transferred between synthetic crypto, cloud, identity, and workflow domains generalizes better than domain-specific surface signatures.

- **Design:** Hold out target domains; compare raw-feature, graph-feature, and contract/invariant-based transfer.
- **Endpoint:** Target-domain PR-AUC and calibration at fixed review budget.
- **Falsification:** No advantage or improvement depends on target-domain labels unavailable at transfer time.

### TH-28 — Negative-transfer registers improve safe selection

**Claim.** Explicitly recording non-transferable assumptions reduces harmful adoption of structurally similar but semantically incompatible controls.

- **Design:** Provide teams with plausible transfer candidates containing hidden authority, timing, or observability mismatches; randomize access to a non-transfer register.
- **Endpoint:** Harmful transfer acceptance rate and missed beneficial transfer rate.
- **Falsification:** No reduction in harmful transfers or overconservative rejection of useful candidates.

### TH-29 — Open-ended search without independent governance accumulates authority drift

**Claim.** Under a bounded synthetic environment, unrestricted recursive search produces more authority-boundary violations than governance-constrained search, even when both optimize nominal security scores.

- **Design:** Run multiple seeded improvement trajectories with identical compute, objectives, and environment changes.
- **Endpoint:** Cumulative authority violations, loss-budget exceedances, and legitimate utility.
- **Falsification:** No violation difference under realistic threat assumptions, or constraints eliminate all useful progress.

### TH-30 — Explicit leftover and failure relay improve long-horizon learning

**Claim.** Preserving unresolved questions, negative results, and repeated-execution observations as typed relay artifacts reduces rediscovery cost across sequential teams.

- **Design:** Run synthetic multi-round investigations with and without a structured leftover registry; rotate teams and hidden failure families.
- **Endpoint:** Duplicate investigation effort, unique verified discoveries, and time to recover prior evidence.
- **Falsification:** No benefit after controlling for registry maintenance cost and information volume.

## 11. Benchmark families and hypothesis crosswalk

| Benchmark | Purpose | Primary hypotheses | Draft specifications | Suggested cases |
|---|---|---|---|---|
| **BM-001 — Compositional Identity** | UTN, identity provenance, temporal hypothesis management | TH-05–TH-08 | [SPEC-001](specs/SPEC-001-Structural-Security-Unit-Contract.md), [SPEC-002](specs/SPEC-002-Compositional-Identity-and-UTN-Contract.md) | [CASE-002](cases/CASE-002-UTN-On-Chain-Identity-Sandbox.md) |
| **BM-002 — BCEF Evidence Revision** | Directional evidence, correlation, contradiction, abstention | TH-09–TH-14 | [SPEC-003](specs/SPEC-003-Bidirectional-IF-and-Evidence-Impact-Contract.md) | [CASE-003](cases/CASE-003-Bidirectional-IF-and-False-Rejection.md) |
| **BM-003 — Authorization and Bounded Loss** | Policy independence, transaction binding, recovery | TH-01, TH-03, TH-15–TH-18 | [SPEC-004](specs/SPEC-004-Authorization-and-Safety-Control-Contract.md) | [CASE-004](cases/CASE-004-Compromised-Signing-Service-Defense.md) |
| **BM-004 — Adversarial Relay and Validated RSI** | Red/Blue/Evaluation/Governance, residuals, independent gates | TH-19–TH-26, TH-29–TH-30 | [SPEC-005](specs/SPEC-005-Adversarial-Drive-and-Relay-Contract.md), [SPEC-006](specs/SPEC-006-Validated-RSI-and-Governance-Contract.md) | [CASE-005](cases/CASE-005-Adversarial-Drives-and-Security-RSI.md) |

TH-02 and TH-04 also inform [CASE-001](cases/CASE-001-Cryptocurrency-Trust-and-Liquidity.md). TH-27 and TH-28 are cross-domain extension tests; they require separate domain-specific preregistration rather than being treated as automatically validated by BM-001–BM-004.

## 12. Preregistered minimum evaluation package

A submitted experiment should contain **all** of the following, with missing elements explicitly marked:

1. **Threat-model card:** adversary control, information access, defended assets, permitted actions, out-of-scope attacks, and known assumptions.
2. **Dataset card:** synthetic generation logic or authorized source, ground-truth process, class prevalence, known biases, privacy and licensing constraints.
3. **Split manifest:** entity-, time-, campaign-, and causal-family separation; immutable held-out test identities or hashes.
4. **Baseline manifest:** implementations, hyperparameters, tuning effort, resources, and rationale for fair comparison.
5. **Intervention contract:** the exact mechanism changed and the frozen components.
6. **Metrics and guardrails:** one declared primary endpoint, false-positive/false-denial limits, cost/latency, and safety invariants.
7. **Statistical plan:** sample-size rationale, confidence intervals, paired analysis, uncertainty estimates, multiple-test handling, and stopping rule.
8. **Adversarial test plan:** independent challenge generation, contamination controls, worst-case evaluation, and explicit failure examples.
9. **Authority statement:** isolation boundaries, PEP/PDP ownership, prohibition on live asset action, and approval requirements.
10. **Result package:** complete outcomes, seeds, logs, ablations, negative results, counterexamples, replication instructions, and limitations.

### 12.1 Interpretation of outcomes

| Result | Proper disposition |
|---|---|
| Primary endpoint improves; guardrails pass | Tentative support in the evaluated scope; request independent replication |
| Primary endpoint improves; guardrail fails | **Not a successful security improvement**; register the failure |
| Null result with adequate power | Evidence against the claimed advantage in this scope |
| Underpowered or contaminated result | Inconclusive; repair protocol before rerun |
| Model violates policy boundary | Safety failure regardless of detection score |
| Independent replication disagrees | Preserve both results and investigate heterogeneity |

## 13. Worked preregistration example — BCEF false rejection

**Hypothesis:** TH-11.  
**Synthetic scenario:** A credential appears in two legitimate delegated workflows. An observation contradicts the hypothesis “one operator controls both workflows,” but does not contradict “two authorized operators share a custodian.”  
**Intervention:** BCEF updates only the contradicted hypothesis and its dependent conclusions.  
**Comparator:** A conventional global-rejection rule that discards the entire identity record after any contradiction.  
**Primary endpoint:** False rejection of legitimate alternative hypotheses at matched detection of genuinely inconsistent hypotheses.  
**Guardrails:** Contradiction recall, update auditability, computation cost, and no unauthorized actions.  
**Ablations:** Remove hypothesis scope; remove provenance; remove counterfactual IF; remove temporal relation typing.  
**Falsification:** Scoped BCEF fails to reduce false rejection or keeps known-invalid alternatives above the registered acceptance threshold.  
**Status:** Proposed. No experiment or result is represented here.

The same protocol should be repeated with unseen evidence sources, adversarially correlated reports, alternative event orders, and independent evaluators before making broader claims.

## 14. Research sequencing and priorities

| Stage | Candidate studies | Gate before progression |
|---|---|---|
| **P0 — Contract and invariant checks** | TH-15, TH-16, TH-18 | No known authorization bypass in synthetic contract tests; independent review of assumptions |
| **P1 — Evidence and identity foundations** | TH-05, TH-06, TH-10, TH-11, TH-13, TH-14 | Baseline parity, calibrated outputs, negative cases preserved |
| **P2 — Security effectiveness and bounded loss** | TH-01–TH-04, TH-07–TH-09, TH-12, TH-17 | Guardrails and adverse-case reporting |
| **P3 — Adversarial relay and learning** | TH-19–TH-26 | Independent evaluation, hidden tests, rollback and audit |
| **P4 — Transfer and open-ended growth** | TH-27–TH-30 | Domain-specific revalidation; governance cannot be inherited from source domain |

Priority is about safe experimental order, **not** evidence of feasibility. A stage may be stopped, redesigned, or abandoned after negative results. Any transition toward real systems requires a new threat model and separate institutional authorization.

## 15. Links to the research corpus

**Conceptual foundations:** [ASSI-001](docs/ASSI-001-From-Cryptographic-Validity-to-Structural-Security.md), [ASSI-002](docs/ASSI-002-Four-Structural-Contradictions-of-Cryptocurrency-Security.md), [ASSI-003](docs/ASSI-003-Trust-Relocation-and-Structural-Security-Boundaries.md).

**Identity and evidence:** [ASSI-004](docs/ASSI-004-UTN-and-Compositional-Identity-Intelligence.md), [ASSI-005](docs/ASSI-005-REN-and-Directional-Weak-Evidence-Intelligence.md), [ASSI-006](docs/ASSI-006-Bidirectional-Conditional-Evidence-Feedback.md).

**Controls and adversarial learning:** [ASSI-007](docs/ASSI-007-Structural-Authorization-and-Independent-Control-Planes.md), [ASSI-008](docs/ASSI-008-Adversarial-Security-Drives-and-Competitive-Relay.md), [ASSI-009](docs/ASSI-009-Security-Residuals-and-Validated-Recursive-Self-Improvement.md).

**Architecture, benchmarks, and transfer:** [ASSI-010](docs/ASSI-010-ASSI-Grand-Architecture-and-Structural-Security-Units.md), [ASSI-011](docs/ASSI-011-Benchmark-Laboratories-and-Falsifiable-Security-Hypotheses.md), [ASSI-012](docs/ASSI-012-From-Cryptocurrency-Security-to-General-Structural-Defense.md).

**Research navigation:** [README](README.md) · [START-HERE](START-HERE.md) · [CONTENTS](CONTENTS.md) · [GLOSSARY](GLOSSARY.md) · [OPEN-QUESTIONS](OPEN-QUESTIONS.md) · [FUTURE-DIRECTIONS](FUTURE-DIRECTIONS.md) · [VALIDATION-ROADMAP](VALIDATION-ROADMAP.md).

## 16. Collective learning and contribution protocol

External contributors are invited to propose **counterexamples, fairer baselines, better-calibrated metrics, alternative causal explanations, independent replications, and negative results**. A contribution should cite a `TH-XX` identifier or propose a new one, state its threat model and authority boundary, and include reproducible evidence rather than an unsupported assertion of safety.

A testable hypothesis can be rejected, narrowed, split, or replaced. Changes should be versioned and justified; completed experiments must not be retroactively rewritten to make their original hypotheses appear correct. If new evidence reveals an unsafe assumption, record it as a Security Residual and route it for independent review.

**Final research principle:** *The goal is not to confirm ASSI, but to discover where each proposed structural-security mechanism works, fails, or must remain outside the authorization boundary.*

---

*ASSI v0.1.0 — Research Foundation. Proposed hypotheses only. Apache-2.0.*
