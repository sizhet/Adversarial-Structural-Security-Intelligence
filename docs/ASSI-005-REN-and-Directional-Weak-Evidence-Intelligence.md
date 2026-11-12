# ASSI-005 — REN and Directional Weak-Evidence Intelligence

**Project:** Adversarial Structural Security Intelligence (ASSI)  
**Version:** v0.1.0 — Research Foundation  
**Status:** Research hypothesis and proposed architecture; no claim of deployed or experimentally validated attribution capability  
**Date:** 2026-11-02  
**License:** Apache-2.0

## Abstract

Cryptographic validity, transaction visibility, and conventional anomaly scores do not by themselves establish the intent, controller, or security significance of an observed action. Security analysts routinely reason from incomplete, heterogeneous, correlated, and sometimes contradictory evidence. This paper proposes **Relational Evidence Navigation (REN)** as a composable structural intelligence mechanism for navigating such evidence within **Adversarial Structural Security Intelligence (ASSI)**. REN combines typed similarity, perspective-dependent directional relevance, explicit weak-evidence handling, competing hypotheses, counterevidence, and provenance-aware updates. It does not treat resemblance as identity, correlation as control, or an inferred link as an observed fact. REN integrates with **Universal Typing and Naming (UTN)** for typed and compositional referents, **Metric Differential Trees (MDT)** for temporal change, **Bidirectional Conditional Evidence Feedback (BCEF)** for testable conditional implications, and scoring/control planes for bounded security decisions. We present a conceptual evidence model, a directional scoring framework, rules for dependent evidence, an example of composition-aware on-chain reasoning, interfaces and invariants, and a falsifiable evaluation program. The immediate research objective is to improve the *quality, calibration, auditability, and revisability* of structural security hypotheses—not to identify private persons from blockchain traces.

**Keywords:** REN; relational evidence navigation; weak evidence; directional scoring; metric similarity; counterevidence; evidence provenance; uncertainty calibration; compositional identity; UTN; MDT; BCEF; on-chain analysis; structural security intelligence.

---

## 1. The problem: visible transactions, uncertain explanations

A public blockchain can expose addresses, transactions, contract interactions, token movements, and timestamps. These records are often precise about *what was recorded* and substantially less informative about *who directed the activity*, *why it occurred*, and *whether two patterns have a common cause*. Shared behavior may reflect common control, a widely used service, automated execution, coordinated activity, market-wide responses, or coincidence. The observed chain graph and the inferred control graph are different objects.

Traditional similarity measures help discover candidates. They do not settle which explanation is correct. Security intelligence therefore requires a disciplined mechanism to combine weak and strong signals, explicitly compare alternative explanations, test predicted consequences, and revise judgments when counterevidence appears.

**Central thesis:** Directional weak evidence becomes useful security intelligence only when it is typed, contextualized, provenance-aware, compared across competing hypotheses, and connected to revisable structural decisions.

### 1.1 Scope

This article develops REN as a proposed research component, not as an established method with demonstrated superiority. It focuses on defensive investigation, synthetic/permissioned benchmark data, authorization anomaly interpretation, and risk triage. It excludes operational deanonymization of private individuals, unsupported allegations, and instructions for evading investigations.

### 1.2 Relationship to the ASSI series

- **ASSI-001** separates cryptographic validity from system-level structural security.
- **ASSI-002** identifies four cryptocurrency security contradictions.
- **ASSI-003** defines trust relocation and structural security boundaries.
- **ASSI-004** establishes UTN compositional identity and hypothesis-scoped contradiction.
- **ASSI-005** specifies how REN evaluates directional evidence for these typed hypotheses.
- **ASSI-006** will develop BCEF: conditional testing and impact propagation into the scoring structure.

---

## 2. Distinguish observation, interpretation, hypothesis, and decision

A trustworthy evidence pipeline preserves four separate layers:

1. **Observation:** A transaction, timestamp, verified contract call, or documented system event.
2. **Feature or interpretation:** A derived temporal pattern, graph relation, behavioral descriptor, or anomaly indicator.
3. **Hypothesis:** A proposed explanation such as shared operator, shared team, shared service, or independent activity.
4. **Decision:** A bounded operational response, such as request more evidence, raise review priority, restrict a privileged action under a predefined policy, or take no action.

These layers must not be collapsed. In particular:

- An address is not automatically a person.
- A transaction edge is not automatically a common-control edge.
- A cluster label is not proof of an organization.
- A high risk score is not authorization to accuse, seize, or punish.
- An inferred relationship must retain its source, assumptions, and uncertainty.

A REN implementation should be able to answer: **What exactly was observed, what was inferred, which assumptions were used, and what evidence would change the conclusion?**

---

## 3. REN: Relational Evidence Navigation

The working name **REN** emphasizes three dimensions:

**Relational:** Evidence concerns relations among entities, actions, conditions, roles, and time, not only isolated feature vectors.

**Evidence:** Both supporting and opposing observations matter; evidence quality, origin, independence, and missingness are first-class properties.

**Navigation:** The system moves among candidate explanations, discriminating tests, and unresolved questions rather than forcing a single irreversible label.

REN is proposed as a *hypothesis-oriented evidence navigation layer*. It is not a substitute for formal probability, causal inference, graph analytics, or security policy. It can use those methods when their assumptions are satisfied.

### 3.1 The “REN” relational intuition

A useful conceptual picture is two structures connected by a proposed similarity relation and examined under a target direction or purpose. Without a directional objective, REN reduces toward ordinary metric comparison. Without sufficient matching features, directional assessment may still express which observations would be relevant to a question, but cannot legitimately fabricate evidence of similarity. These are **limiting cases**, not proofs that all inference reduces to one metric.

---

## 4. Metric similarity and directional relevance are distinct

Let observations or typed structural units be $x$ and $y$, and let $c$ denote context. A similarity function can be written:

$$
M(x,y\mid c) \in [0,1].
$$

This is a representation of feature resemblance under a specified metric. It is not a probability of common control unless empirically calibrated for that interpretation.

Let $h$ denote a hypothesis and $d$ a **directional field**—a task, security objective, or inquiry perspective. A directional relevance function is:

$$
R(e,h,d,c) \in \mathbb{R},
$$

where $e$ is an evidence item. Directionality can change the importance of the same feature across tasks. For example, synchronized timing might be relevant when investigating automation, but weakly discriminative when many users react to a public market event.

A conceptual scoring architecture is:

$$
S(h\mid E,d,c)=F\!\left(S_0(h),\;\{R(e_i,h,d,c),q_i,p_i\}_{i=1}^{n},\;D(E),\;A\right),
$$

where:

- $S_0(h)$: initial hypothesis assessment or prior, with declared semantics;
- $q_i$: evidence quality or reliability metadata;
- $p_i$: provenance and dependency information;
- $D(E)$: dependency structure among evidence items;
- $A$: alternative hypotheses and relevant counterevidence;
- $F$: an explicitly chosen and validated aggregation/update rule.

**This equation is an architectural schema, not a validated estimator.** A score must not be called a posterior probability unless the model, likelihood assumptions, and calibration support that claim.

### 4.1 Direction is not permission to bias

A directional field identifies the *question* and *relevance criterion*. It must not suppress counterevidence or guarantee a favored conclusion. REN should evaluate the same observation against multiple candidate hypotheses, including benign alternatives.

---

## 5. Weak evidence, strong evidence, and counterevidence

Evidence strength is conditional on a hypothesis and the alternatives, not an intrinsic property of a feature name.

**Weak evidence** may be suggestive but non-unique, noisy, dependent on context, or poorly verified. Examples in a synthetic on-chain dataset include overlapping activity windows or similar transaction cadence.

**Stronger evidence** may be independently corroborated, more discriminating, or directly tied to a relevant control mechanism. A documented, consented operational record may distinguish two hypotheses more clearly than numerous similar behavioral traces. Even apparently strong evidence must be evaluated for scope and provenance.

**Counterevidence** is evidence whose expected occurrence differs across hypotheses in a direction unfavorable to one or more of them. It does not automatically refute every related hypothesis.

### 5.1 Evidence strength should be comparative

Where a probabilistic model is justified, the discriminative value of evidence $e$ for hypotheses $h_1$ and $h_2$ may be expressed by a likelihood ratio:

$$
\Lambda(e;h_1,h_2)=\frac{P(e\mid h_1)}{P(e\mid h_2)}.
$$

This highlights an essential distinction: a feature may be common under a hypothesis and yet offer little support if it is equally common under an alternative. Likelihood ratios require defensible likelihood estimates; they are not inferred from resemblance alone.

### 5.2 Unknown is not false

An absent observation may mean: not collected, not visible, outside the time window, withheld, corrupted, or genuinely absent. REN should represent **unknown**, **not applicable**, and **observed negative** separately. Treating missing evidence as contradiction creates systematic errors.

---

## 6. Dependency-aware evidence: avoiding artificial confidence

A major failure mode is counting several correlated features as independent confirmations. For example, transaction timing, burstiness, and inter-arrival statistics may all derive from the same underlying sequence. Likewise, multiple reports may repeat one unverified source.

REN should maintain a provenance/dependency graph linking:

- Raw observations to derived features;
- Features to transformation versions;
- Reports to original sources;
- Evidence items to shared latent causes where known;
- Tests to the evidence used to generate them.

A simple additive rule $S=\sum_i w_i e_i$ can become overconfident when dependencies are ignored. Candidate implementations should use dependency-aware aggregation, hierarchical models, or conservative evidence grouping, and must validate their behavior empirically.

**Invariant REN-DEP-01:** Deriving additional features from one observation must not, by itself, be treated as obtaining independent corroboration.

**Invariant REN-DEP-02:** An IF test that reuses its parent evidence must not be fed back as an independent supporting observation.

---

## 7. Compositional identity and competing explanations

ASSI-004 establishes that the target of attribution may be an individual, team, organization, shared service, temporary coalition, or overlapping subgroup. REN must score these as **different typed hypotheses**.

Consider synthetic addresses X and Y with similar transaction timing. A useful hypothesis portfolio might contain:

- $H_1$: One human operator controls both.
- $H_2$: Different operators belong to the same team.
- $H_3$: Both use the same external automation service.
- $H_4$: Independent operators respond to a shared public trigger.

The same observation can have different implications for each hypothesis. A mismatch in operator working hours may weaken $H_1$, but not necessarily $H_2$. Shared infrastructure may support $H_3$ without proving $H_2$.

### 7.1 Hypothesis-scoped contradiction

**REN-HYP-01:** Every counterevidence impact must identify the precise hypothesis, assumptions, and scope to which it applies.

**REN-HYP-02:** Rejecting a one-person explanation must not automatically reject a team, coalition, or shared-service explanation.

**REN-HYP-03:** A common service must not be silently equated with common ownership or common intent.

### 7.2 Naming lifecycle

UTN names should refer to evidence-grounded *candidate structural entities*, with lifecycle states such as proposed, active, split, merged, superseded, or withdrawn. REN supplies evidence impacts; UTN governs typed identity references and their history. Neither component alone establishes legal or real-world identity.

---

## 8. Time and MDT: evidence changes meaning

Evidence is time-indexed. A shared control relationship may exist during one operational interval and cease later. A service may change infrastructure. A team may split or reconfigure. Static clustering can obscure these changes.

REN can use **Metric Differential Trees (MDT)** to represent differences between successive structural states:

$$
\Delta_t = \mathrm{Diff}(G_{t-1},G_t),
$$

where $G_t$ is a typed, provenance-aware structural graph at time $t$. The difference may concern a new observed transaction, changed evidence quality, revised membership hypothesis, altered risk policy, or retracted source.

A useful temporal record distinguishes:

- **Event time:** when the observed action occurred;
- **Observation time:** when the system learned of it;
- **Assessment time:** when an inference was made;
- **Validity interval:** when the inferred relationship is claimed to apply.

This distinction supports replay, correction, and audit without rewriting history.

---

## 9. Bidirectional IF as a test operator, not a score amplifier

REN identifies and evaluates evidence; **BCEF**, developed in ASSI-006, tests conditional implications and propagates impacts to the scoring structure. Four test modes are proposed:

1. **Forward IF:** If $h$ is true, what observations should follow under stated assumptions?
2. **Reverse IF:** Given observation $e$, how does it discriminate $h$ from alternatives?
3. **Counterfactual IF:** If $h$ were false, could $e$ still arise under another explanation?
4. **Contradiction IF:** Which specific version of $h$, if any, is incompatible with $e$?

The implication $h\Rightarrow e$ does not entail $e\Rightarrow h$. A positive test result must not be mistaken for logical proof, and a failed prediction should be interpreted in light of observability, context, and assumptions.

### 9.1 Structural impact, not only numeric delta

A BCEF result can suggest:

- Reweighting an evidence node;
- Marking an assumption as unsupported;
- Splitting a candidate cluster;
- Reopening a benign alternative;
- Requiring an independent measurement;
- Changing investigation priority;
- Deferring judgment when evidence is insufficient.

The update should be recorded as an **impact proposal** and applied according to validation and governance rules. In production security controls, soft inference must not override hard authorization policies.

---

## 10. Proposed REN evidence-unit contract

The following YAML is a **non-normative design sketch**, not a finalized specification. Field names and enumerations will be stabilized in `SPEC-001`, `SPEC-002`, and `SPEC-003`.

```yaml
ren_evidence_unit:
  id: REN-E-0007
  schema_version: 0.1.0
  observation:
    type: synthetic_transaction_timing_pattern
    source_id: SYNTHETIC-DATASET-01
    observed_at: 2026-11-02T12:00:00Z
    raw_record_refs: [TX-SYN-102, TX-SYN-103]
  derivation:
    method: temporal_feature_extraction
    method_version: 0.1.0
    parent_evidence_ids: [REN-E-0001, REN-E-0002]
  subject_refs: [UTN-ADDR-X, UTN-ADDR-Y]
  hypothesis_ref: UTN-HYP-SHARED-TEAM-01
  directional_field: common_control_inquiry
  relation_type: temporal_similarity
  polarity: supporting
  strength_class: weak
  reliability:
    status: provisional
    rationale: pattern_is_non_unique
  dependence_group: SYNTH-TIMING-SERIES-01
  valid_time:
    from: 2026-10-01T00:00:00Z
    to: 2026-10-31T23:59:59Z
  counter_hypotheses:
    - UTN-HYP-SHARED-SERVICE-01
    - UTN-HYP-COMMON-TRIGGER-01
  limitations:
    - does_not_establish_personal_identity
    - derived_features_are_correlated
  audit:
    created_by: sandbox_pipeline
    review_status: unreviewed
```

### 10.1 Required properties of an eventual normative contract

A conformant REN implementation should preserve: typed observation; source/provenance; derivation lineage; time semantics; hypothesis scope; directional purpose; uncertainty semantics; dependencies; alternatives; counterevidence; update history; and permitted downstream uses. It should also support explicit abstention.

---

## 11. Proposed processing pipeline

```text
Authorized / Synthetic Data Sources
              |
              v
      Observed Event Registry
              |
              v
    UTN Typing + Provenance
              |
              v
  MDT Temporal Structural Features
              |
              v
  REN Directional Evidence Analysis
       /       |        \
  support   counter   unknown
       \       |        /
              v
     Hypothesis Portfolio
              |
              v
      BCEF Conditional Tests
              |
              v
  Scoring Tree Impact Proposals
              |
              v
  Review / Policy / Audit Controls
              |
              v
     Updated Structural State
              |
              +----> AQSI Next Question
```

This is an architecture for research and controlled deployment. It is not a license to convert inferred identity into punitive action, nor to allow a probabilistic score to authorize high-value asset transfers.

### 11.1 Separation of authority

- **Evidence plane:** records and interprets observations.
- **Inference plane:** maintains uncertain hypotheses and counterevidence.
- **Control plane:** enforces separately specified policies.
- **Independent safety plane:** constrains exposure, protects keys, and supports recovery.

A compromised or mistaken evidence model must not be able to rewrite its own hard security limits.

---

## 12. Illustrative synthetic case: similarity without common ownership

**Scenario.** A permissioned sandbox contains four synthetic operators: A, B, C, and D. A and B belong to one team; B and C share a service provider; C and D coordinate during a short joint activity. Address clusters X and Y show similar transaction cadence.

**Initial REN observations.** Timing similarity and overlapping counterparties create a weak signal of association. The signals share underlying transaction records and must not be counted as independent confirmations.

**Competing hypotheses.** The portfolio contains same person, same team, shared service, temporary coalition, and unrelated-but-correlated activity.

**BCEF tests.** A synthetic record showing distinct authorized operators contradicts the same-person hypothesis for the relevant time interval, but may be consistent with team operation. A verified shared-service record may explain the timing correlation without implying common ownership.

**Structural update.** The system weakens or withdraws the single-person naming proposal, preserves the shared-service explanation, and defers group naming until independent evidence becomes available. Every revision retains provenance.

**Desired outcome.** The system avoids a false merge and preserves meaningful uncertainty. Whether REN+BCEF actually reduces such errors compared with baselines is an empirical question.

---

## 13. Evaluation: falsifiable hypotheses and benchmarks

### 13.1 Hypotheses

**H-REN-01 — Directional utility.** A context-aware directional model improves discrimination between shared control and shared-service behavior relative to a fixed, non-directional similarity baseline on held-out synthetic/permissioned data.

**H-REN-02 — Dependency control.** Provenance-aware evidence aggregation reduces overconfidence and calibration error compared with naive independent-feature aggregation.

**H-REN-03 — Counterevidence.** Explicit alternatives and counterevidence reduce false identity merges without unacceptable increases in false splits or abstention.

**H-REN-04 — Composition.** Modeling team/coalition/service hypotheses improves hypothesis-level accuracy over single-operator-only attribution in datasets with overlapping actors.

**H-REN-05 — Temporal revision.** MDT-backed evidence history improves correction latency and auditability under controlled changes of group membership and control.

**H-REN-06 — BCEF integration.** Hypothesis-scoped IF impacts reduce false rejections relative to global contradiction penalties.

These are proposals for testing, **not reported findings**.

### 13.2 Baselines and ablations

Compare at least:

1. Fixed metric similarity with a single-label classifier;
2. Graph clustering without compositional identity;
3. Directional scoring without provenance/dependency controls;
4. REN without explicit counterevidence;
5. REN with compositional hypotheses but without BCEF;
6. Full REN + UTN + MDT + BCEF prototype.

Ablate directionality, evidence dependence, alternatives, temporal modeling, and IF impact separately. Use pre-registered datasets, splits, and metrics where practical.

### 13.3 Metrics

- Hypothesis-level precision, recall, F1, and confusion by actor type;
- False merge rate and false split rate;
- Calibration (Brier score, log loss where probabilities are meaningful, reliability diagrams);
- Selective prediction accuracy and abstention rate;
- Counterevidence handling and contradiction-scope error rate;
- Time to correct an invalid naming hypothesis;
- Provenance completeness and replay reproducibility;
- Runtime, review burden, and evidence acquisition cost;
- Group-specific and scenario-specific error disparities.

### 13.4 Failure conditions

The research claim should be weakened or rejected if gains vanish under held-out scenarios, calibration deteriorates, false accusations increase, dependency-aware scoring offers no improvement, or results depend on leaked ground-truth features. A method that improves recall by indiscriminately merging unrelated actors is not successful.

---

## 14. Security, privacy, and governance constraints

REN may generate sensitive or consequential inferences. Research and deployments must therefore apply:

- **Lawful data scope:** synthetic, permissioned, or properly governed public organizational evidence;
- **Purpose limitation:** defensive investigation and authorized security analysis;
- **Data minimization:** avoid unnecessary personal information;
- **Evidence provenance:** preserve source quality, collection authority, and correction history;
- **Human review:** require independent review for consequential real-world attribution;
- **Uncertainty disclosure:** display alternative explanations and abstentions;
- **Access controls:** protect raw evidence, inferred links, and audit logs;
- **Policy separation:** never treat an inference score as a substitute for transaction authorization;
- **Adversarial robustness:** test poisoning, misleading correlations, manipulated labels, and feedback loops;
- **Reproducibility:** publish synthetic benchmark definitions and non-sensitive evaluation protocols.

Security investigation and privacy protection are not mutually exclusive: a better-calibrated model should be more willing to say **insufficient evidence**.

---

## 15. Open questions and research roadmap

### 15.1 Open questions

1. How should a directional field be represented so that relevance can change without introducing confirmation bias?
2. Which dependency structures can be learned reliably from limited evidence, and which require conservative manual assumptions?
3. When is a numerical score meaningful, and when should REN use qualitative or interval-valued uncertainty?
4. How should evidence strength be calibrated across different entity types and changing operational contexts?
5. Can compositional hypotheses be searched efficiently without combinatorial explosion?
6. What is the correct separation between inferred collaboration and actual organizational control?
7. How should an inference be revised when a source is retracted or a group splits?
8. How can BCEF propose new tests without reusing its own conclusions as fresh evidence?
9. Which independent evaluation protocols best measure transfer from synthetic scenarios to authorized real settings?
10. How should privacy, explanation, and security utility be balanced under explicit governance?

### 15.2 Staged roadmap

**Stage A — Contracts and synthetic data.** Stabilize UTN identity types, REN evidence-unit semantics, provenance, dependency groups, and the hypothesis portfolio. Create controlled datasets with known individuals, teams, services, coalitions, and changing membership.

**Stage B — REN baselines.** Implement conventional similarity and graph baselines; add directional relevance and dependency-aware scoring; measure calibration and error modes.

**Stage C — BCEF integration.** Add forward, reverse, counterfactual, and contradiction tests with hypothesis-scoped impacts and explicit abstention.

**Stage D — MDT temporal replay.** Evaluate historical corrections, evolving groups, evidence retractions, and reproducible revision logs.

**Stage E — Security-system integration.** Feed only validated risk signals into separately governed authorization workflows; assess false blocks, missed threats, maximum loss exposure, and operational cost in isolated simulations.

---

## 16. Conclusion

REN is proposed as a structural mechanism for navigating uncertain security evidence—not a universal identity oracle. Metric similarity finds resemblance; directional relevance asks which resemblance matters for a particular inquiry; weak-evidence reasoning compares competing explanations; UTN provides typed and compositional referents; MDT preserves structural change; and BCEF tests implications and feeds justified impacts back into the scoring structure.

The central discipline is to **retain the difference between observation and inference**. Similarity does not establish control; a weak signal does not become strong merely because several derived metrics repeat it; and counterevidence against one-person control does not automatically refute shared-team or shared-service explanations.

The practical value of REN must be demonstrated by held-out benchmarks, calibrated uncertainty, independent corroboration, and auditable revisions. Within ASSI, its proper role is to improve structural understanding and guide controlled security decisions while independent safety mechanisms constrain loss even when intelligence is wrong.

---

## Suggested methodological references

These are research traditions to consult in subsequent formalization, not claims that ASSI or REN has been validated by them:

- Probabilistic record linkage, entity resolution, and open-world clustering.
- Bayesian model comparison, likelihood ratios, and uncertainty calibration.
- Causal inference, alternative explanations, and counterfactual reasoning.
- Provenance semirings, data lineage, and dependency-aware evidence aggregation.
- Temporal knowledge graphs, event sourcing, and bitemporal databases.
- Assumption-based truth maintenance and belief revision.
- Security threat modeling, least privilege, and independent authorization controls.
- Privacy-preserving analytics and human-governed investigative workflows.

**Repository placement:** `docs/ASSI-005-REN-and-Directional-Weak-Evidence-Intelligence.md`  
**Previous article:** `docs/ASSI-004-UTN-and-Compositional-Identity-Intelligence.md`  
**Next article:** `docs/ASSI-006-Bidirectional-Conditional-Evidence-Feedback.md`
