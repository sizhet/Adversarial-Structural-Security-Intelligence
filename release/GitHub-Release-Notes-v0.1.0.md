# ASSI v0.1.0 — Research Foundation

**Adversarial Structural Security Intelligence (ASSI)**  
**Release type:** Initial research foundation  
**Status:** Specification-first, hypothesis-driven, pre-validation research  
**Repository:** https://github.com/sizhet/Adversarial-Structural-Security-Intelligence  
**License:** Apache-2.0

> **Cryptographic validity is not structural security.** A valid signature, an inferred identity, or a high confidence score does not, by itself, establish permission to perform a consequential action.

## Overview

ASSI v0.1.0 establishes an open research foundation for studying security as an evolving **structural problem**: identities are compositional, evidence is incomplete and dependent, authority can drift, adversaries adapt, and system improvements can introduce new failure modes. Cryptocurrency-related trust, custody, signing, and liquidity scenarios motivate the initial inquiry; the architecture is intended to support carefully bounded exploration in other domains.

The release proposes a separation between **security intelligence**, which may observe, infer, challenge, simulate, and recommend, and an **independent safety control plane**, which alone may authorize and enforce consequential operations. The work prioritizes contracts, falsifiable hypotheses, controlled experiments, failure preservation, and independent validation over premature implementation or performance claims.

**This is a research-document release, not a security product or certification.** No operational deployment, measured benchmark improvement, independent replication, or security assurance is claimed.

## What is new in v0.1.0

### 1. A structural account of security

The initial research identifies four recurring tensions—**control versus autonomy, identity versus authorization, efficiency versus safety, and evolution versus stability**—and examines how risk may move across boundaries even when cryptographic checks are correct. It treats *trust relocation* and *bounded loss* as first-class design questions.

### 2. Compositional identity with UTN

ASSI proposes typed, time-sensitive structural identity representations, including compositional relationships and competing hypotheses. Identity evidence is treated as revisable and scoped; an identity inference does not create an authorization grant.

### 3. REN and BCEF for disciplined evidence revision

**REN (Relational Evidence Navigation)** frames weak evidence directionally rather than as an unqualified match. **BCEF (Bidirectional Conditional Evidence Feedback)** proposes forward, reverse, counterfactual, and contradiction-oriented conditional tests. Contradictions remain hypothesis-scoped; correlated observations must not be silently counted as independent corroboration. Evidence impact may revise a scoring structure without silently rewriting enforcement policy.

### 4. Independent structural authorization

A separate control plane is proposed for policy decision and enforcement, transaction binding, segregation of duties, exposure budgets, recovery, and auditability. The architecture distinguishes **inference**, **verification**, **authorization**, and **execution**. A model or an adversarial research agent must not self-approve privileged actions.

### 5. Adversarial Drives and competitive Structural Relay

ASSI defines distinct **Red**, **Blue**, **Evaluation**, and **Governance** roles for controlled adversarial research. Findings are represented as reusable structural residuals and relay units, with explicit provenance, limits, negative results, and evaluation independence.

### 6. Security Residual → AQSI → Validated RSI

Residual risks and failures can seed **Autonomous Questioning Structural Intelligence (AQSI)**. Proposed improvements enter a **validated recursive self-improvement (RSI)** pipeline with held-out tests, independent evaluation, rollback criteria, and explicit governance approval. Improvement proposals do not automatically become deployment decisions.

### 7. Generalization with explicit transfer limits

The foundation explores potential structural transfer to cloud authorization, software supply chains, enterprise workflows, and AI-agent governance. Similarity of structure does **not** imply portability of guarantees; negative transfer is an expected, recordable research result.

## Research package

The intended v0.1.0 research corpus comprises **27 substantive documents**, organized as follows:

| Series | Count | Coverage |
|---|---:|---|
| `docs/ASSI-001`–`ASSI-012` | 12 | Security foundations, structural contradictions, UTN, REN, BCEF, independent control, adversarial drives, RSI, architecture, benchmarks, and generalization |
| `specs/SPEC-001`–`SPEC-006` | 6 | Security units, compositional identity, evidence impact, authorization, adversarial relay, and governed RSI contracts |
| `cases/CASE-001`–`CASE-005` | 5 | Cryptocurrency trust, identity sandbox, BCEF false rejection, compromised signing-service defense, and adversarial RSI scenarios |
| `extensions/EXT-001`–`EXT-004` | 4 | Multi-agent ecology, autonomous questioning, cross-domain transfer, and open-ended security governance |

The supporting publication and research-navigation materials are:

- `README.md`, `START-HERE.md`, `CONTENTS.md`, and `GLOSSARY.md`;
- `FIGURE-INDEX.md` and the proposed eight-figure architecture set;
- `FUTURE-DIRECTIONS.md` and `OPEN-QUESTIONS.md`;
- `TESTABLE-HYPOTHESES.md` (TH-01–TH-30) and `VALIDATION-ROADMAP.md`;
- `CHANGELOG.md`, `CITATION.cff`, and `.zenodo.json`.

**Packaging note:** This list describes the intended release contents. Before publishing the GitHub release, verify that each file is committed at its stated repository path, all figure references resolve to eight individual PNG assets, and the license and metadata are present. Do not interpret a listed asset as proof it has been committed.

## Proposed benchmark families — not yet results

The research defines four experimental families:

| Benchmark | Focus | Example failure modes to test |
|---|---|---|
| **BM-001** | Compositional identity and UTN | False identity merges, stale links, temporal identity drift |
| **BM-002** | REN/BCEF evidence revision | Correlated evidence double-counting, hypothesis leakage, false rejection |
| **BM-003** | Independent authorization and bounded loss | Valid signature with invalid authorization, missing transaction binding, authority drift |
| **BM-004** | Adversarial Relay and validated RSI | Evaluation contamination, overfitting, unsafe self-approval, failed rollback |

These are **benchmark designs and evaluation targets**. v0.1.0 does not report benchmark scores, comparative wins, operational exploit rates, or independently reproduced findings.

## Validation and falsifiability

The companion roadmap proposes a staged progression:

1. Freeze contracts, threat models, assumptions, and safety invariants.
2. Build a synthetic, isolated conformance laboratory.
3. Run BM-001–BM-004 against declared baselines and ablations.
4. Convert observed Security Residuals into scoped AQSI questions.
5. Evaluate RSI proposals independently, including regression and rollback checks.
6. Replicate across domains while recording negative transfer.
7. Consider any bounded field evaluation **only** under separate authorization and governance.

TH-01–TH-30 provide a proposed hypothesis inventory; their presence does not establish empirical confirmation. Experimental failures, inconclusive results, and counterexamples should be preserved as reusable research artifacts.

## Safety, scope, and limitations

- **Inference ≠ authority.** A score, model conclusion, or agent consensus cannot bypass an independent enforcement decision.
- **Simulation ≠ validation.** Synthetic demonstrations cannot establish real-world security assurance.
- **Validation ≠ deployment approval.** Deployment requires separate review, policy, and accountability.
- **A valid signature ≠ an authorized transaction.** Cryptographic validity is necessary in many settings but insufficient for complete structural security.
- **Generalize structures, not guarantees.** Cross-domain reuse requires renewed threat modeling and evidence.
- **Adversarial experiments must remain authorized and contained.** Examples are research scenarios, not instructions to attack live systems.

This initial release does not provide production-ready controls, a formal verification proof, security certification, an audited implementation, or a guarantee of loss prevention.

## Suggested reading paths

- **First-time reader:** [`README.md`](../README.md) → [`START-HERE.md`](../START-HERE.md) → `docs/ASSI-001` → `docs/ASSI-010`.
- **Security architect:** `docs/ASSI-003` → `docs/ASSI-004` → `docs/ASSI-007` → `specs/SPEC-002` and `specs/SPEC-004`.
- **Evidence / AI researcher:** `docs/ASSI-005` → `docs/ASSI-006` → `specs/SPEC-003` → `cases/CASE-003`.
- **Evaluation researcher:** `docs/ASSI-011` → [`TESTABLE-HYPOTHESES.md`](../TESTABLE-HYPOTHESES.md) → [`VALIDATION-ROADMAP.md`](../VALIDATION-ROADMAP.md).
- **Governance / collective learning:** `docs/ASSI-008` → `docs/ASSI-009` → `specs/SPEC-006` → `extensions/EXT-004`.

Paths above are repository-relative from the `release/` directory; refer to [`CONTENTS.md`](../CONTENTS.md) for full filenames and links.

## Open research and collective learning

ASSI is offered as an open, testable research foundation. Useful contributions include precise counterexamples, alternative contracts, conformance test proposals, falsification attempts, synthetic benchmarks, independently reproducible results, and explicit records of unsuccessful transfer. Contributions should state their assumptions, evidence provenance, scope, and limits; they should not be represented as independently validated without supporting artifacts.

## Citation, licensing, and DOI

- **Project:** Adversarial Structural Security Intelligence (ASSI)
- **Version:** `v0.1.0` — Research Foundation
- **Repository:** https://github.com/sizhet/Adversarial-Structural-Security-Intelligence
- **Citation metadata:** `CITATION.cff`
- **Zenodo metadata:** `.zenodo.json`
- **License:** Apache License 2.0 (subject to the repository's committed `LICENSE` file)
- **DOI:** To be added only after a DOI has actually been minted; no DOI is asserted here.

For an archival release, confirm that the tag, committed content, citation metadata, Zenodo metadata, and eventual DOI all refer to the same version. The release date should be the actual publication date, not a draft date.

---

**ASSI v0.1.0 is a starting point for disciplined structural-security inquiry—not a claim that structural security has been solved.**
