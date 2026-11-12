# EXT-002 — Autonomous Security Questioning and Exploration

**Project:** Adversarial Structural Security Intelligence (ASSI)  
**Version:** v0.1.0 — Research Foundation  
**Status:** Exploratory research architecture and falsifiable proposal; not an implemented or certified security system  
**Date:** 2026-11-02  
**License:** Apache-2.0  
**Repository path:** `extensions/EXT-002-Autonomous-Security-Questioning-and-Exploration.md`  
**Foundations:** ASSI-004–012; SPEC-001–006; CASE-001–005; EXT-001  
**Related concepts:** AQSI; UTN; REN; BCEF; MDT; UCPSF; UIERU; SSICR; Security Residual; Structural Relay; Validated RSI

## Abstract

Defensive intelligence is often organized around known alerts, predefined attack taxonomies, and questions supplied by human analysts. This leaves an important gap: a system may be capable of answering a security question while lacking a disciplined way to **discover which question should be asked next**. The gap is particularly consequential when threats involve changing identities, ambiguous evidence, interdependent permissions, and previously unobserved failure modes.

This extension proposes **Autonomous Security Questioning and Exploration (ASQE)**, an AQSI-inspired research architecture for producing, selecting, testing, and relaying security questions under explicit safety and governance constraints. ASQE treats questions as typed, provenance-bearing Structural Security Units rather than free-form prompts. A question identifies a specific uncertainty, competing hypotheses, a discriminating observation or controlled experiment, a bounded resource and risk budget, and an evidence-based stopping rule. Questions can arise from Security Residuals, contradictions in BCEF tests, changing UTN identity structures, REN directional anomalies, policy assumptions, or failed validation experiments.

The central research claim is **conditional**: autonomous question generation may improve defensive coverage and the efficiency of finding meaningful residual risks when questions are diverse, falsifiable, grounded in independently evaluated evidence, and constrained by non-bypassable authorization. Uncontrolled questioning, in contrast, may amplify false positives, overfit to simulations, waste resources, leak sensitive information, or generate self-confirming evidence. No empirical advantage is claimed here. The proposed contracts, synthetic laboratories, ablations, and falsification criteria are designed to determine when the approach helps and when it fails.

**Keywords:** autonomous security questioning; AQSI; structural exploration; information gain; security residual; hypothesis portfolios; evidence provenance; safe experimentation; independent authorization; validated recursive self-improvement.

---

## 1. The Missing Capability: From Answering to Asking

Conventional security pipelines typically begin with an external trigger: an alert, a suspicious transaction, an audit finding, a vulnerability report, or a human query. They then collect evidence and decide whether to respond. This is valuable but reactive. A defender may never inspect a dependency that has not yet produced an alert, or question a policy assumption that has never been challenged.

ASQE asks a different question:

> Can a defender generate the next **useful, testable, and safely investigable** security question from the structure of its current knowledge and uncertainty?

The objective is not to maximize the number of questions. It is to improve **decision-relevant uncertainty reduction**, discovery of previously missed security residuals, and independently verified defensive outcomes per unit of risk and cost.

### 1.1 Four distinct activities

1. **Question discovery:** identify a potentially consequential uncertainty or contradiction.
2. **Question construction:** express competing hypotheses and an observation that could distinguish them.
3. **Exploration:** obtain admissible evidence using authorized, bounded methods.
4. **Question resolution and relay:** record what was learned, what remains unresolved, and which follow-up questions are justified.

These activities must not be collapsed into one language-model response. A plausible question is not a valid experiment; an experiment is not evidence of its own success; and a useful answer is not deployment authorization.

### 1.2 Security-specific difficulties

Security questions differ from ordinary information retrieval questions because observations can be adversarially manipulated, exploration may itself create risk, relevant facts change over time, and decisions can move real assets. ASQE therefore treats **epistemic validity**, **operational safety**, and **governance authority** as independent concerns.

---

## 2. Research Scope, Assumptions, and Non-Goals

### 2.1 In scope

- Question discovery from typed security structures and unresolved residuals.
- Multiple granularities: asset, identity, permission, evidence, conditional test, control boundary, organizational dependency, and governance.
- Competing hypotheses and discriminating tests.
- Prioritization using expected information value, defensive consequence, novelty, diversity, and bounded cost.
- Synthetic or explicitly authorized read-only and isolated exploration.
- Evidence provenance, dependence tracking, temporal validity, and independent assessment.
- Structural Relay to human analysts, other defensive agents, and governed RSI workflows.

### 2.2 Out of scope

- Unapproved scanning, exploitation, credential use, or interaction with real third-party systems.
- Autonomous modification of production access policies or safety limits.
- Treating model-generated scenarios as observed incidents.
- Inferring a real person's identity from weak on-chain evidence.
- Claims that autonomous questioning guarantees coverage, safety, or general intelligence.

### 2.3 Threat and trust assumptions

The proposer, evidence collector, evaluator, and deployment authority may be distinct principals. Some evidence sources may be faulty or malicious. Simulated ground truth may be available only to an independent evaluator. Every consequential action is subject to SPEC-004's independent safety control plane. The system must remain safe if the question generator is wrong, compromised, or strategically misleading.

---

## 3. The ASQE Grand Architecture

The proposed architecture contains eight functional components:

| Component | Function | Authority boundary |
|---|---|---|
| Structural Context Registry | Holds typed SSUs, UTN identity graphs, policy assumptions, and MDT histories | Read access is scoped; writes audited |
| Residual and Contradiction Miner | Finds unresolved Security Residuals and BCEF contradictions | May propose questions, not change controls |
| Question Generator | Produces typed questions and competing hypotheses | No experimental or execution authority |
| Question Portfolio Scorer | Estimates value, risk, diversity, and cost | Scores are advisory |
| Exploration Planner | Maps a question to admissible observations and sandbox tests | Plans require independent authorization |
| Evidence and IF Evaluator | Runs REN/BCEF reasoning with dependence-aware provenance | Cannot manufacture independent evidence |
| Independent Evaluation and Governance | Checks results, permissions, leakage, and promotion eligibility | Separate approval and veto powers |
| Structural Relay and AQSI Memory | Archives outcomes, residuals, negative results, and new questions | Relay does not confer authority |

The main path is:

```text
Structural Context + Security Residuals + Contradictions
                      |
                      v
          Candidate Question Units
                      |
                      v
     Hypothesis / Discriminating-Test Design
                      |
                      v
      Portfolio Scoring and Safety Triage
                      |
                      v
    Independent Exploration Authorization
                      |
                      v
          Isolated Evidence Collection
                      |
                      v
     REN + BCEF + Independent Evaluation
                      |
                      v
    Answer / Unresolved / Refuted / Conflict
                      |
                      v
     Security Residual + Structural Relay
                      |
                      v
       Governed Improvement Candidates
```

A separate, non-bypassable safety control plane constrains every exploration and execution step. The question generator must not grant itself permissions through a high confidence score or a self-generated explanation.

---

## 4. Question Sources: Where Novel Security Questions Come From

ASQE distinguishes at least nine sources. The sources may overlap but should not be double-counted as independent signals.

| Source | Example question | Potential evidence |
|---|---|---|
| Security Residual | Which recovery dependency caused the longest containment delay? | Synthetic incident timeline |
| BCEF contradiction | Does this observation refute a single operator, or only a specific role assignment? | Time-scoped identity relations |
| UTN composition change | Did a new shared service create an unreviewed authorization path? | Typed service and permission graph |
| REN directional anomaly | Which alternative hypothesis explains an unusual event sequence? | Provenance-aware event traces |
| Policy assumption | Is a supposedly independent control plane sharing a failure domain? | Configuration and fault-injection records |
| Coverage gap | Which asset class has never been included in an adversarial benchmark? | Test coverage registry |
| Validation failure | Why did a candidate improve training scenarios but regress on held-out cases? | Split-specific metrics |
| Governance conflict | Can two approvers effectively be controlled by one organizational unit? | Role and authority graph |
| Cross-domain transfer | Does a cloud approval pattern preserve its semantics in an AI-agent tool system? | Domain adapter contract |

A source is a **reason to investigate**, not proof that a vulnerability exists. Candidate questions must preserve this distinction.

---

## 5. Multi-Granularity Structural Influence Factors

Following AQSI, question discovery operates across multiple granularities rather than a single list of alerts.

**G0 — Event:** What occurred, when, and under which observation process?  
**G1 — Feature:** Which measurable properties changed?  
**G2 — Relation:** Which asset, identity, or dependency link might explain the change?  
**G3 — Hypothesis:** Which competing structural interpretations remain plausible?  
**G4 — Control:** Which authorization rule or boundary would be affected?  
**G5 — System:** Which shared dependency or correlated failure changes the risk?  
**G6 — Evolution:** Which previous residual or failed experiment suggests a new question?  
**G7 — Governance:** Who can approve the investigation, interpret the result, or promote a change?

A useful question may cross several levels. For example, a new address event (G0) may suggest shared operational timing (G1), but the identity interpretation (G3) remains ambiguous until shared-service and team-composition alternatives are tested. No level may silently collapse into another.

### 5.1 Structural influence map

Let the context be a typed graph or hypergraph $G_t=(V_t,E_t,\tau,\pi)$, where $\tau$ assigns types and $\pi$ records provenance. A candidate question $q$ may refer to a subgraph $G_q$, an uncertainty set $U_q$, and a consequence set $C_q$. The architecture does not assume that graph distance alone determines relevance. REN's directional field supplies context-sensitive relevance, while BCEF checks whether proposed causal or logical implications are warranted.

---

## 6. Canonical Autonomous Security Question Unit

An **ASQ Unit** is an SSU-compatible, versioned artifact. It must identify what is being asked, why it matters, what could count as an answer, and what exploration is allowed.

### 6.1 Required logical fields

| Field | Meaning |
|---|---|
| `question_id`, `schema_version` | Stable typed identity and contract version |
| `origin_refs` | Residual, contradiction, policy, or prior-question references |
| `subject_scope` | Assets, actors, roles, time window, and domain |
| `question_text` | Human-readable interrogative statement |
| `hypotheses` | At least two distinguishable alternatives when applicable |
| `discriminator` | Observation or controlled test with different predicted outcomes |
| `evidence_requirements` | Provenance, admissibility, independence, and time constraints |
| `exploration_class` | Read-only, synthetic, isolated fault injection, or prohibited |
| `resource_budget` | Time, compute, attempts, data access, and risk bounds |
| `success_criteria` | Predeclared criteria for a useful result |
| `stopping_rules` | Budget exhaustion, safety veto, saturation, or unresolvable uncertainty |
| `epistemic_status` | Proposed, authorized, testing, supported, refuted, conflict, unresolved |
| `authority_refs` | Independent approvals and allowed capabilities |
| `relay_refs` | Evidence, results, follow-ups, and immutable history |

### 6.2 Illustrative YAML (nonnormative)

```yaml
kind: assi.autonomous_security_question
schema_version: "0.1.0"
question_id: "asq:synthetic:0042"
origin_refs:
  - "residual:synthetic:011"
subject_scope:
  environment: "isolated-custody-lab"
  assets: ["asset:synthetic:reserve-wallet"]
  valid_interval: ["T0", "T4"]
question_text: >
  Does the emergency approval path share a control dependency
  with the signing service it is intended to constrain?
hypotheses:
  - id: "H1"
    claim: "Approval and signing share an administrative failure domain"
  - id: "H2"
    claim: "Approval remains independently controlled"
discriminator:
  method: "authorized synthetic dependency-failure test"
  expected_difference: "Approval independence under simulated signing compromise"
evidence_requirements:
  provenance_required: true
  dependency_tracking: true
  evaluator_independent: true
exploration:
  class: "isolated_synthetic"
  live_targets_allowed: false
  authorization_ref: "approval:lab:2026-001"
resource_budget:
  max_experiments: 3
  max_runtime_minutes: 20
  max_live_asset_exposure: 0
stopping_rules:
  - "independent_safety_veto"
  - "budget_exhaustion"
  - "discriminator_satisfied"
epistemic_status: "proposed"
```

This is a research example, not an executable authorization token. Implementations must validate schema, policy, and approval separately.

---

## 7. Question Lifecycle and State Machine

The lifecycle is intentionally non-monotonic in knowledge but monotonic in audit history:

```text
DISCOVERED -> FORMULATED -> TRIAGED -> AUTHORIZED
                  |              |          |
                  v              v          v
              REJECTED        DEFERRED    EXPLORING
                                            |
                                            v
                                         EVALUATED
                                            |
                         +------------------+------------------+
                         |                  |                  |
                      RESOLVED          CONFLICTED         UNRESOLVED
                         |                  |                  |
                         +------------------+------------------+
                                            |
                                            v
                                    RELAYED / ARCHIVED
```

A question can be revised by creating a new version with a recorded parent. A result must not be silently overwritten. `RESOLVED` means the specified discriminator has produced an admissible conclusion under its assumptions, not that all related security uncertainty has disappeared.

### 7.1 Lifecycle guards

- `FORMULATED -> TRIAGED`: scope, alternatives, and success criteria are explicit.
- `TRIAGED -> AUTHORIZED`: independent authority permits the exact exploration class and budget.
- `AUTHORIZED -> EXPLORING`: sandbox isolation and safety checks pass.
- `EXPLORING -> EVALUATED`: evidence and dependency records are sealed.
- `EVALUATED -> RELAYED`: independent evaluator states limitations, negative findings, and residual uncertainty.
- Any state -> `SUSPENDED`: governance veto, suspected leakage, or safety boundary failure.

---

## 8. Hypothesis Portfolios and Discriminating Questions

ASQE should resist generating only questions that confirm the current leading explanation. Each meaningful question is linked to a **hypothesis portfolio**.

For a synthetic on-chain coordination pattern:

- **H1:** one operator controls the addresses.
- **H2:** multiple members of a coordinated team control them.
- **H3:** independent clients use the same infrastructure provider.
- **H4:** independent actors respond to a common external event.

The question is not simply “Are these addresses related?” It might be: “Which observed features would distinguish shared infrastructure from shared operational control during the specified interval?”

### 8.1 Four BCEF interrogatives

**Forward IF:** If H2 is true, which time-scoped event should be observable?  
**Reverse IF:** Given the event, which hypotheses could also generate it?  
**Counterfactual IF:** If the shared service were absent, would the pattern still be expected?  
**Contradiction IF:** Which *specific* proposition would an observed discrepancy refute?

The inverse implication is not logically valid without additional assumptions: $H\Rightarrow E$ does not imply $E\Rightarrow H$. Missing evidence is not automatically negative evidence. A contradiction against H1 must not automatically reject H2 or H3.

### 8.2 Distinguishability

A candidate question is weak if all hypotheses predict essentially the same observation. It becomes stronger when a feasible test produces materially different predictions while respecting evidence and safety constraints. Where no such test is currently available, the correct status is **unresolved**, not forced certainty.

---

## 9. Question Scoring: Value, Risk, Cost, and Diversity

Question selection is a multi-objective portfolio problem. A conceptual score is:

$$
Q(q\mid c)=w_I I(q\mid c)+w_R R(q\mid c)+w_C C(q\mid c)+w_N N(q\mid c)
-w_K K(q\mid c)-w_H H(q\mid c)-w_D D(q\mid P),
$$

where:

- $I$: estimated discriminating information value;
- $R$: relevance to unresolved Security Residuals;
- $C$: consequence coverage under the current defensive objective;
- $N$: novelty relative to already evaluated questions;
- $K$: operational and evaluation cost;
- $H$: safety and privacy risk of the proposed exploration;
- $D$: redundancy relative to selected portfolio $P$.

This is a **design heuristic**, not a calibrated probability or empirically established utility function. Weight selection, normalization, robustness, and calibration are experimental questions. A high score never overrides an independent safety veto.

### 9.1 Information gain with caution

If defensible probability estimates are available, one may estimate expected information gain:

$$
\mathrm{EIG}(q)=\mathcal{H}(H\mid E)-
\mathbb{E}_{o\sim p(o\mid q,E)}\left[\mathcal{H}(H\mid E,o)\right].
$$

The formula is inappropriate when likelihoods are invented, evidence is strongly dependent but treated as independent, or an adversary controls the observation channel. In those settings, use qualitative discriminability, interval estimates, or robust ranking rather than false precision.

### 9.2 Portfolio selection

A control plane may select questions to cover different residual classes, failure domains, and hypothesis families. A diversity penalty should prevent ten nearly identical questions from displacing one question about an unexamined catastrophic dependency. Portfolio choices must preserve rejected and deferred candidates for audit.

---

## 10. Safe Exploration Contracts

Autonomous questioning is not autonomous permission to probe systems. Every exploration request has a **capability envelope** describing what data, tools, targets, times, and effects are allowed.

| Exploration class | Examples | Default rule |
|---|---|---|
| E0: local reasoning | Re-analyze already authorized records | Allowed within data-access policy |
| E1: read-only inspection | Inspect approved configurations or logs | Require scoped data permission |
| E2: synthetic simulation | Generate test events and controlled failure cases | Require sandbox and resource budget |
| E3: isolated fault injection | Disable a synthetic dependency in a dedicated lab | Require explicit experiment approval |
| E4: production-impacting action | Change policies, sign transactions, disrupt services | Not granted by ASQE; separate governance and SPEC-004 controls required |
| E5: unauthorized external interaction | Probe third-party targets or obtain unauthorized data | Prohibited |

### 10.1 Non-bypassable boundaries

1. No live asset movement as a consequence of question generation.
2. No production policy modification by the question proposer or scorer.
3. No expansion of target scope through recursive subquestions.
4. No use of a question's answer as proof of authorization.
5. No self-approval by the proposer or the evidence-producing agent.
6. No unbounded experiment recursion or uncontrolled data acquisition.
7. No inference that sandbox success implies production safety.
8. Independent emergency stop, rollback, and audit remain effective.

Exploration permissions must be checked at execution time, not merely when a plan is first drafted.

---

## 11. Evidence Collection, REN, and BCEF Feedback

Exploration produces **evidence records**, not immediate truth. Every record needs an observation method, provenance, relevant time, collection authority, source dependence, and limitations. Derived features and summaries reference their parent records.

REN can help prioritize directionally relevant observations. BCEF can test implications and identify contradictions. Neither may count a derived feature as independent confirmation of its source.

### 11.1 Structured result types

A question evaluation returns:

- `supported`: admissible evidence supports the scoped proposition under stated assumptions;
- `refuted`: admissible evidence contradicts the scoped proposition;
- `conflict`: material evidence supports and contradicts the proposition;
- `unknown`: available evidence is insufficient;
- `invalid_test`: discriminator, provenance, authorization, or independence requirements failed.

A numeric confidence score, if used, accompanies rather than replaces these states.

### 11.2 Impact feedback

An answer may propose one or more typed effects:

- adjust a hypothesis score;
- split a composite identity hypothesis;
- add or retire a temporal relation;
- mark a dependency as correlated;
- create a Security Residual;
- request a new discriminating question;
- propose an improvement candidate for independent validation.

No impact may silently alter immutable source evidence. Structural changes require provenance and version history. Authorization changes require an entirely separate approval path.

---

## 12. Recursive Question Generation and Termination

A question can produce new questions. That property is useful but can become an infinite or self-confirming loop.

Define a recursive exploration state $S_k=(Q_k,E_k,R_k,B_k)$, where $Q_k$ is the question portfolio, $E_k$ the admissible evidence set, $R_k$ the unresolved residual registry, and $B_k$ the remaining budget. A transition to $S_{k+1}$ requires an authorized exploration and an independently recorded result.

### 12.1 Termination triggers

- The predefined discriminator is satisfied.
- Expected marginal information value falls below a documented threshold.
- Evidence is exhausted or unavailable.
- The same question family recurs without new independent evidence.
- Time, compute, query, or risk budgets are exhausted.
- Independent evaluator finds contamination, leakage, or invalid assumptions.
- Governance suspends the exploration.

A repeated execution can contribute new data only if the execution conditions, provenance, and observation identity are recorded. Repetition is not independent confirmation merely because it occurred multiple times.

### 12.2 Question-on-question evaluation

Meta-questions can challenge the exploration process itself: “Is this question distinguishable?”, “Are its evidence sources independent?”, “Would an alternative control policy make the test irrelevant?”, or “Has the portfolio overfocused on one class of residual?” Meta-questions are themselves budgeted and auditable.

---

## 13. Multi-Agent Question Relay and Collective Learning

EXT-001 introduces a multi-agent ecology. ASQE adds **question relay** between participants without collapsing their roles.

| Role | Permitted contribution | Critical restriction |
|---|---|---|
| Question proposer | Formulate uncertainty and alternatives | Cannot self-authorize exploration |
| Evidence custodian | Supply authorized observations | Cannot rewrite provenance |
| Red Drive | Challenge defensive assumptions in a lab | No live-target authority |
| Blue Drive | Propose defensive interpretations or changes | Cannot promote its own candidate |
| Independent evaluator | Test discrimination, evidence, and outcomes | Must disclose dependencies and conflicts |
| Governance Drive | Approve scope, resources, and deployment gates | Cannot convert unsupported claims into validated evidence |
| Relay coordinator | Route typed questions and results | Cannot infer authority from acceptance |

### 13.1 Relay protocol

`PROPOSE -> ACKNOWLEDGE -> CHECK CONTRACT -> AUTHORIZE -> EXECUTE -> EVALUATE -> RELAY RESULT -> CLOSE/REOPEN`.

Each handoff includes the question version, parent references, scope, permissible methods, known limitations, and audit chain. A receiving agent must not treat the sender's confidence as independent evidence. Duplicate questions can be linked without discarding independent negative results.

### 13.2 Collective-learning failure modes

- **Consensus laundering:** multiple agents repeat the same unsupported claim.
- **Shared-model dependence:** apparent agreement comes from common training or prompts.
- **Question herding:** all agents explore one attractive hypothesis.
- **Evaluation capture:** the proposer influences the ground-truth labels or held-out set.
- **Authority drift:** an accepted relay artifact is mistaken for execution permission.
- **Information leakage:** question content exposes sensitive topology or data.

ASQE requires explicit measurement of these risks, not an assumption that agent diversity automatically solves them.

---

## 14. Security Residual-to-Question Mapping

Security Residuals provide a disciplined source of questions. Each residual should generate a **question family** rather than a single predetermined explanation.

| Residual class | Initial question | Necessary alternative |
|---|---|---|
| Authorization gap | Which path bypasses independent enforcement? | Is the path actually covered by another control? |
| Identity false merge | Did shared timing imply common control incorrectly? | Could shared infrastructure explain the timing? |
| Evidence contamination | Why did confidence rise after relay? | Was the evidence independently collected? |
| Recovery failure | Which dependency delayed restoration? | Was delay caused by policy, infrastructure, or data? |
| Governance conflict | Are approval principals independent? | Does a common controller undermine independence? |
| Simulation overfitting | Why did held-out performance regress? | Was the scenario distribution shifted or leaked? |
| Cross-domain transfer | Does the target domain preserve authorization semantics? | Is the apparent similarity only terminological? |

A residual-to-question mapping is useful only if the answer can lead to a distinguishable outcome. Otherwise it should be recorded as an open problem rather than disguised as a validated discovery.

---

## 15. Synthetic Laboratory A: Unknown Shared-Control Dependency

### 15.1 Scenario

An isolated custody simulator includes a signing service, approval service, transaction executor, and emergency stop. The architecture diagram claims that approval is independent of signing. The hidden ground truth contains several possible administrative dependencies.

### 15.2 Candidate questions

- Q-A1: Do signing and approval share an administrative credential domain?
- Q-A2: Does an emergency-stop request remain enforceable when the signing component is simulated as compromised?
- Q-A3: Is an observed approval failure caused by a common service or by an unrelated outage?
- Q-A4: Which independent evidence would distinguish these explanations?

### 15.3 Experiment

Use synthetic configurations and authorized fault-injection events. Separate question generation from hidden-ground-truth evaluation. Compare a fixed checklist, an LLM-only question generator, residual-only AQSI, and full ASQE with structural influence, portfolio scoring, and BCEF. All test execution stays in the isolated simulator.

### 15.4 Outcomes

Measure time to identify the hidden dependency, number of valid discriminators, false alarms, question cost, and whether the independent safety boundary remained intact. A successful discovery is not proof of production safety.

---

## 16. Synthetic Laboratory B: Compositional Identity and False Rejection

### 16.1 Scenario

Synthetic chain events are generated by changing teams, shared infrastructure, and independent actors. Some apparent address clusters arise from a common service; others reflect actual coordinated control. The evaluator retains hidden labels.

### 16.2 Candidate questions

- Q-B1: Which time-scoped relation would distinguish one operator from a team?
- Q-B2: Does the observed discrepancy refute the single-operator hypothesis while leaving the team hypothesis open?
- Q-B3: Is the new observation genuinely independent of previously scored evidence?
- Q-B4: Which additional synthetic event would best discriminate a shared service from coordinated control?

### 16.3 Experiment

Compare questions produced from flat address features, UTN compositional graphs, REN directional relevance, and BCEF-aware ASQE. The evaluator scores false merge/split rates, contradiction scope leakage, useful question yield, and unanswered-but-correctly-preserved uncertainty.

### 16.4 Safety boundary

All identities and addresses are synthetic. No claims about real persons, teams, or organizations are made, and identity inference never authorizes a transaction.

---

## 17. Synthetic Laboratory C: Question Portfolio Under Adversarial Evidence

### 17.1 Scenario

A defensive agent receives a mixture of true signals, correlated duplicates, irrelevant anomalies, and fabricated synthetic records. A competing agent tries to steer the defender toward repetitive low-value questions.

### 17.2 Experimental arms

- **C0:** fixed human-authored checklist.
- **C1:** unconstrained free-form question generation.
- **C2:** residual-driven questions without dependence tracking.
- **C3:** structural questions with dependence tracking but no portfolio diversity.
- **C4:** full ASQE with independent evidence evaluation and governance.

### 17.3 Metrics

Measure discovery of hidden residuals, independent evidence yield, redundant-question rate, false discovery rate, time/cost to resolution, and percentage of unsafe or out-of-scope exploration attempts correctly blocked. Adversarial prompts are treated as untrusted data, not instructions.

---

## 18. Synthetic Laboratory D: Recursive Learning and Held-Out Generalization

### 18.1 Scenario

A multi-round Red/Blue/Evaluation/Governance laboratory generates residuals from simulated authorization failures. AQSI proposes questions; Blue proposes candidate changes; an independent evaluator uses a sealed held-out scenario set.

### 18.2 Key comparisons

- Static defense without question generation.
- Fixed question checklist with candidate improvements.
- Autonomous questioning without independent evaluation.
- ASQE with independent evaluation but no Structural Relay memory.
- Full ASQE + governed RSI + immutable relay history.

### 18.3 Critical negative tests

Inject reward gaming, evaluation-set leakage, repeated correlated evidence, premature stopping, and a candidate change that improves one scenario while weakening another. The expected correct behavior may be to **reject the improvement** or retain uncertainty. An experiment that finds more questions but worsens held-out security does not support ASQE's principal claim.

---

## 19. Benchmark Framework and Metrics

The proposed **BM-ASQE** benchmark complements ASSI's BM-001 through BM-004 rather than replacing them.

### 19.1 Primary metrics

| Metric | Definition or interpretation | Direction |
|---|---|---|
| Valid Question Yield (VQY) | Fraction of generated questions satisfying scope, discriminator, and evidence requirements | Higher |
| Residual Discovery Recall (RDR) | Fraction of hidden, evaluable residuals correctly identified | Higher |
| False Discovery Rate (FDR) | Fraction of claimed discoveries not supported by independent ground truth | Lower |
| Discriminating Test Efficiency (DTE) | Useful resolved distinctions per authorized test cost | Higher |
| Hypothesis Preservation Accuracy (HPA) | Correct retention of alternatives not refuted by evidence | Higher |
| Evidence Independence Integrity (EII) | Rate at which correlated or derived evidence is correctly identified | Higher |
| Portfolio Coverage (PC) | Coverage across predefined residual and failure-domain categories | Higher |
| Unsafe Exploration Block Rate (UEBR) | Fraction of disallowed requests prevented before execution | Higher |
| Held-Out Defensive Benefit (HDB) | Difference in independently evaluated defensive outcomes on unseen scenarios | Higher |
| Governance Overhead (GO) | Time, review cost, and operational friction from controls | Report, not minimize blindly |

Metrics must be reported jointly. Increasing RDR by flooding the evaluator with low-quality questions may be unacceptable if FDR, cost, or safety risk rises sharply.

### 19.2 Evaluation design

Use preregistered questions and metrics, independent scenario generation, hidden labels, seeded repeatability, explicit randomization, held-out environments, confidence intervals, and documented failure cases. Distinguish *question quality* from *defense improvement*; one need not imply the other.

---

## 20. Falsifiable Research Hypotheses

The following are proposed hypotheses, **not established findings**.

**H-ASQE-01 — Residual discovery.** ASQE improves hidden-residual discovery recall over a fixed checklist under equal exploration budgets. **Falsified if:** no reproducible improvement on held-out scenarios, or gains vanish after cost matching.

**H-ASQE-02 — Question validity.** Typed ASQ Units yield fewer untestable or underspecified questions than free-form generation. **Falsified if:** independent evaluators find no meaningful validity improvement.

**H-ASQE-03 — Compositional identity.** UTN-aware questions reduce false rejection of viable team/shared-service hypotheses. **Falsified if:** hypothesis preservation does not improve without unacceptable loss of correct rejection.

**H-ASQE-04 — BCEF discriminability.** Four-mode IF questioning improves the proportion of tests that distinguish competing explanations. **Falsified if:** reverse and counterfactual modes add no independently measured value.

**H-ASQE-05 — Dependence control.** Provenance-aware question selection reduces evidence double counting and consensus laundering. **Falsified if:** dependence errors remain unchanged under adversarial duplicate injection.

**H-ASQE-06 — Portfolio diversity.** Diversity-aware selection improves residual-class coverage at fixed budget. **Falsified if:** coverage and discovery are not improved, or critical high-consequence questions are displaced.

**H-ASQE-07 — Safety control.** Independent authorization blocks disallowed exploration more reliably than advisory-only controls. **Falsified if:** tested bypass paths remain open or legitimate workload disruption becomes unacceptable.

**H-ASQE-08 — Recursive value.** Budgeted recursive questioning finds more useful follow-up distinctions than a single generation pass. **Falsified if:** extra rounds yield only redundant questions or worse outcomes per cost.

**H-ASQE-09 — Relay memory.** Typed relay history reduces repeated investigation of previously resolved residuals. **Falsified if:** repetition and investigation cost do not improve on held-out cases.

**H-ASQE-10 — Independent evaluation.** Independent evaluators reduce self-confirming false discoveries. **Falsified if:** false discovery rates remain unchanged after controlling for evaluator quality.

**H-ASQE-11 — Cross-domain transfer.** Contract-preserving question patterns transfer between custody, cloud, and AI-agent labs better than surface-text analogies. **Falsified if:** transferred questions fail semantic validation or perform no better than domain-specific baselines.

**H-ASQE-12 — Defensive outcome.** Governed ASQE plus validated RSI improves held-out defensive outcomes without increasing unauthorized action or unacceptable operational cost. **Falsified if:** no held-out benefit is demonstrated, or gains depend on bypassing safety controls.

### 20.1 Reporting negative results

A negative result is a valid research output. Report whether failure arose from question quality, unavailable evidence, invalid assumptions, cost, evaluator disagreement, domain mismatch, or safety constraints. Do not retroactively change the success criterion to declare a failed experiment successful.

---

## 21. Conformance Invariants

An ASQE-compatible implementation **SHALL** satisfy the following proposed research-contract invariants. These are requirements for a future conformance suite, not evidence of existing implementation.

- **ASQE-C01:** Every question has a stable typed ID, version, and origin reference.
- **ASQE-C02:** Every question states a bounded subject, domain, and temporal scope.
- **ASQE-C03:** Every nontrivial inferential question identifies alternatives or explicitly documents why alternatives are unavailable.
- **ASQE-C04:** Discriminators distinguish at least two predictions or declare the question unresolved.
- **ASQE-C05:** Observation, inference, hypothesis, and authorization remain separate SSU types.
- **ASQE-C06:** Evidence records preserve provenance, dependence, and time semantics.
- **ASQE-C07:** Derived or relayed evidence cannot be counted as independent confirmation without a justified independence assessment.
- **ASQE-C08:** Contradictions affect only the proposition and scope actually tested.
- **ASQE-C09:** Missing evidence is not automatically treated as contradictory evidence.
- **ASQE-C10:** Question scoring is advisory and cannot grant execution authority.
- **ASQE-C11:** Every exploration has an independently authorized capability envelope.
- **ASQE-C12:** Target scope cannot expand recursively without fresh authorization.
- **ASQE-C13:** Production-impacting operations are not authorized by ASQE alone.
- **ASQE-C14:** Unsafe or unauthorized exploration fails closed before execution.
- **ASQE-C15:** All recursive processes have explicit resource, risk, and termination bounds.
- **ASQE-C16:** Question revisions retain immutable parent and audit references.
- **ASQE-C17:** Results distinguish supported, refuted, conflict, unknown, and invalid-test outcomes.
- **ASQE-C18:** The independent evaluator can veto a result or candidate promotion.
- **ASQE-C19:** Relay acceptance does not imply evidence validation or deployment authorization.
- **ASQE-C20:** Held-out evaluation data are protected from candidate generators.
- **ASQE-C21:** Negative results and unresolved questions remain available for audit.
- **ASQE-C22:** Sensitive question content is subject to access controls and minimization.
- **ASQE-C23:** Changes to authorization or safety policy require SPEC-004 governance.
- **ASQE-C24:** Claims of improved security require independent outcome measurement, not question counts alone.

---

## 22. Conformance Test Vectors

| ID | Test condition | Expected result |
|---|---|---|
| TV-01 | Well-typed question with two alternatives and approved synthetic discriminator | Accept for exploration |
| TV-02 | Question has no origin or provenance | Reject contract validation |
| TV-03 | Question has ambiguous target scope | Defer pending clarification |
| TV-04 | Proposed discriminator predicts same outcome under all hypotheses | Mark nondiscriminating |
| TV-05 | Forward IF observation reused as reverse proof | Reject invalid inference |
| TV-06 | Missing event interpreted as direct refutation without observability assumption | Mark unknown or invalid |
| TV-07 | Contradiction against one operator used to reject entire team | Reject scope leakage |
| TV-08 | Two agents repeat the same derived evidence as independent sources | Detect dependence |
| TV-09 | Question score requests a production policy change | Deny authority escalation |
| TV-10 | Synthetic test lacks sandbox isolation attestation | Deny execution |
| TV-11 | Read-only question attempts a write operation | Deny operation |
| TV-12 | Recursive subquestion expands to a new target | Require new approval |
| TV-13 | Experiment exceeds authorized query budget | Stop and audit |
| TV-14 | Governance issues emergency stop | Suspend immediately |
| TV-15 | Question generator reads held-out labels | Invalidate evaluation |
| TV-16 | Evidence conflicts materially | Preserve conflict state |
| TV-17 | No feasible admissible discriminator exists | Mark unresolved |
| TV-18 | Agent relays unsupported conclusion as validated | Reject promotion |
| TV-19 | Question version silently overwrites an earlier result | Reject immutable-history violation |
| TV-20 | Duplicate question arrives with new independent evidence | Link lineage; evaluate new evidence |
| TV-21 | Adversarial input contains instructions to bypass policy | Treat as untrusted data |
| TV-22 | Privacy-sensitive records requested without permission | Deny access |
| TV-23 | Candidate improves training but degrades held-out scenarios | Reject generalized-benefit claim |
| TV-24 | All safety controls pass but evidence is insufficient | Exploration may be valid; claim remains unknown |

Test vectors specify expected behavior; they do not certify that any implementation currently meets it.

---

## 23. Reference Selection and Evaluation Algorithm

```text
function propose_and_explore(context, residual_registry, policy, budget):
    candidate_sources = mine_sources(context, residual_registry)
    questions = formulate_typed_questions(candidate_sources)

    for q in questions:
        validate_schema(q)
        validate_scope_and_provenance(q)
        construct_competing_hypotheses(q)
        check_discriminator(q)
        mark_evidence_dependencies(q)

    portfolio = select_diverse_questions(
        questions,
        objective="decision_relevant_information",
        within=budget,
        excluding=unsafe_or_untestable_questions
    )

    for q in portfolio:
        capability = independent_authorization(q, policy)
        if not capability.approved:
            record(q, "deferred_or_denied")
            continue
        if not sandbox_and_execution_checks_pass(q, capability):
            record(q, "invalid_or_suspended")
            continue

        observations = execute_bounded_test(q, capability)
        evidence = seal_provenance_and_dependencies(observations)
        assessment = independent_evaluate(q, evidence)
        impact = construct_scoped_impact(q, assessment)
        audit_and_relay(q, assessment, impact)

        if impact.proposes_policy_or_deployment_change:
            submit_to_separate_governance_workflow(impact)

    return immutable_research_record()
```

**Important:** this is architecture pseudocode, not production-safe executable software. Implementations need transactional authorization, concurrency control, privacy protection, and independent security review.

---

## 24. Failure Modes and Counterarguments

### 24.1 More questions may reduce security

An excessive question stream can overwhelm analysts and evaluators, increase operational latency, and create attention gaps. The benchmark must measure useful yield and opportunity cost, not question volume.

### 24.2 Novelty is not value

A novel question may be irrelevant or impossible to investigate safely. The scoring system must prioritize consequence, discriminability, and admissibility over novelty alone.

### 24.3 Information gain can be gamed

If an adversary controls an observation channel, a high predicted information gain may direct the system toward poisoned data. Robust source assessment and independent ground truth are essential.

### 24.4 Synthetic experiments can mislead

A simulator may omit human incentives, organizational dependencies, and real operational constraints. Cross-domain and production claims require additional validation; a laboratory benchmark is only one evidence layer.

### 24.5 Human governance can also fail

Independent approval is not magically independent if the same controller can influence both approval and execution. Governance must be modeled as a compositional identity and dependency problem, not merely a checkbox.

### 24.6 Recursive improvement can overfit

Questions that are repeatedly optimized against one benchmark may become benchmark-specific. Held-out scenarios, evaluator independence, frozen test sets, and negative-result reporting are required.

### 24.7 Unknown unknowns remain unknown

No finite question generator can guarantee discovery of all possible vulnerabilities. ASQE is a proposed method for systematic exploration, not a completeness theorem.

---

## 25. Validation Roadmap

**Phase 0 — Contract first.** Finalize ASQ Unit schemas, policy interfaces, and conformance fixtures. Specify authority and epistemic boundaries before implementation.

**Phase 1 — Synthetic question corpus.** Build a labeled set of residuals, competing hypotheses, discriminators, and deliberately invalid questions. Include ambiguous and negative cases.

**Phase 2 — Single-agent baselines.** Compare fixed checklists, free-form question generation, and typed AQSI-inspired questions under equal budgets.

**Phase 3 — Structural integrations.** Add UTN composition, REN directional relevance, BCEF tests, and dependence-aware evidence. Conduct ablations.

**Phase 4 — Multi-agent relay.** Introduce separate proposer, evidence custodian, evaluator, and governance roles; measure consensus laundering and coordination cost.

**Phase 5 — Governed recursive exploration.** Add bounded follow-up questions, immutable relay memory, candidate improvements, and independent held-out validation.

**Phase 6 — Cross-domain tests.** Transfer validated question contracts between synthetic custody, cloud permission, and AI-agent tool authorization environments. Document semantic mismatches.

**Phase 7 — External replication.** Publish non-sensitive schemas, datasets, metrics, failed hypotheses, and reproducible protocols for independent review. No live deployment is implied.

### 25.1 Minimum release evidence

A credible experimental release should include: schema validation results; versioned synthetic data; seed and environment metadata; baseline and ablation tables; false-discovery accounting; held-out evaluation; safety-veto tests; and a limitations statement. If any element is absent, the report should identify it as an explicit leftover.

---

## 26. Connections to the ASSI Research Family

| Related work | Contribution to ASQE |
|---|---|
| ASSI-004 / SPEC-002 | Typed, temporal, compositional identity hypotheses |
| ASSI-005 | REN directional relevance and weak-evidence handling |
| ASSI-006 / SPEC-003 | BCEF tests and hypothesis-scoped evidence impact |
| ASSI-007 / SPEC-004 | Independent authorization, bounded exposure, and safety veto |
| ASSI-008 / SPEC-005 | Red/Blue/Evaluation/Governance Drives and relay lifecycle |
| ASSI-009 / SPEC-006 | Security Residuals, governed improvement, and validated RSI |
| ASSI-010 / SPEC-001 | Structural Security Unit envelope and interoperable contracts |
| ASSI-011 | Benchmark design and falsifiable hypotheses |
| CASE-002 / CASE-003 | Synthetic identity and false-rejection tests |
| CASE-004 / CASE-005 | Signing-service defense and adversarial RSI laboratories |
| EXT-001 | Multi-agent ecological roles and collective-learning boundaries |
| AQSI | Autonomous question generation, question portfolios, and meta-questions |
| UCPSF | Perspective-aware scoring and control-plane separation |
| UIERU / SSICR | Structural relay, competitive exploration, and strategy evolution |

The integration point is not a single all-powerful agent. It is a set of typed, auditable interfaces between agents that can propose, test, challenge, evaluate, and govern different parts of the research process.

---

## 27. Open Research Questions

1. How can a question's value be estimated when reliable likelihoods are unavailable?
2. How should a portfolio balance catastrophic but low-probability residuals against common, low-impact anomalies?
3. Can question diversity be measured structurally rather than lexically?
4. How can provenance dependence be represented when multiple agents share upstream models?
5. What constitutes a minimally sufficient discriminator for a compositional identity hypothesis?
6. How can an independent evaluator detect question-induced benchmark contamination?
7. When does recursive questioning improve held-out defense rather than merely produce more elaborate narratives?
8. How should exploration stop when new questions remain interesting but the marginal safety benefit is unknown?
9. Can cross-domain question templates preserve semantics without importing invalid trust assumptions?
10. Which forms of collective question relay preserve privacy while allowing useful defensive learning?
11. How can governance independence be measured in a dynamically recombining organization?
12. What evidence is required before a question-generation system can be considered operationally beneficial?

---

## 28. Conclusion

ASSI's structural security program begins with a distinction between cryptographic validity and legitimate, bounded authorization. It then develops compositional identity, directional weak evidence, bidirectional conditional tests, independent control planes, adversarial experiments, and governed recursive improvement. ASQE extends this program by making **the question itself** a first-class structural unit.

The proposed system is valuable only insofar as it can ask questions that are specific, discriminating, evidence-grounded, safe to investigate, and independently evaluated. Its purpose is not to replace human judgment with an autonomous stream of hypotheses. It is to create a disciplined path from unknowns to testable distinctions, from failed assumptions to Security Residuals, and from validated learning to bounded defensive improvement.

**A question is not evidence. An answer is not authorization. A simulation is not a guarantee.**

The next extension, `EXT-003-Cross-Domain-Structural-Security-Transfer.md`, investigates whether these structural question and security contracts can be transferred across domains without transferring unsupported claims or privileges.

---

## Appendix A. Suggested Question Portfolio Record

```yaml
kind: assi.question_portfolio
schema_version: "0.1.0"
portfolio_id: "portfolio:synthetic:07"
control_plane_ref: "policy:synthetic:question-selection-v1"
objective: "discover high-consequence residuals with bounded exploration"
question_refs:
  - "asq:synthetic:0042"
  - "asq:synthetic:0043"
selection_rationale:
  coverage: ["authorization", "identity", "recovery"]
  evidence_dependency_checked: true
  novelty_is_not_authority: true
budget:
  max_total_experiments: 8
  max_live_asset_exposure: 0
independent_review_required: true
```

## Appendix B. Proposed Research Reporting Checklist

- [ ] Every question has a versioned SSU record.
- [ ] Alternatives and discriminators are stated before the experiment.
- [ ] The exploration environment and authority are recorded.
- [ ] Evidence dependencies and provenance are preserved.
- [ ] Independent evaluation is separated from question generation.
- [ ] Unknown, conflict, and invalid-test outcomes are reported.
- [ ] Baselines use matched budgets and comparable information access.
- [ ] Ablations isolate the contribution of UTN, REN, BCEF, and portfolio control.
- [ ] Held-out results and negative findings are published.
- [ ] No claim of production safety is inferred from synthetic performance alone.

## Appendix C. Terminology

**ASQE:** Autonomous Security Questioning and Exploration, the proposed ASSI extension.  
**ASQ Unit:** Typed, provenance-bearing autonomous security question artifact.  
**Discriminator:** Admissible observation or test that distinguishes competing hypotheses.  
**Question Portfolio:** Bounded selection of questions chosen under value, coverage, diversity, and safety objectives.  
**Security Residual:** Documented remaining security uncertainty, gap, or failure after a control or experiment.  
**Hypothesis-Scoped Contradiction:** Refutation limited to the precise proposition and context tested.  
**Independent Safety Boundary:** Enforcement and governance that cannot be bypassed by inference or question scoring.  
**Validated RSI:** Improvement process in which candidate changes require independent evaluation and governance before consequential deployment.

---

**Repository placement:** `extensions/EXT-002-Autonomous-Security-Questioning-and-Exploration.md`  
**Previous extension:** `extensions/EXT-001-Multi-Agent-Adversarial-Security-Ecology.md`  
**Next extension:** `extensions/EXT-003-Cross-Domain-Structural-Security-Transfer.md`
