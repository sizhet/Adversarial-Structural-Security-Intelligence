# Changelog

**Project:** Adversarial Structural Security Intelligence (ASSI)  
**Release track:** Research Foundation  
**Current release:** `v0.1.0`  
**Status:** Initial research documentation; release preparation  
**License:** Apache-2.0

This changelog records the evolution of the **ASSI research repository**: its hypotheses, conceptual models, draft contracts, synthetic cases, validation plans, and publication assets. It does not imply that the proposed mechanisms have been implemented, benchmarked, independently audited, or approved for operational deployment.

The format follows the spirit of [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), with research-specific categories and explicit evidence-status distinctions. Version identifiers describe **repository artifacts and research scope**, not security-assurance levels.

## [Unreleased]

### Planned / under consideration

- Establish a reproducible, fully synthetic test harness for four proposed benchmark families: BM-001 compositional identity, BM-002 BCEF evidence revision, BM-003 independent authorization and bounded loss, and BM-004 adversarial relay and validated RSI.
- Publish machine-readable conformance fixtures for the six draft specifications, with positive, negative, boundary, and adversarial test cases.
- Define provenance-aware evidence fixtures to examine correlated observations, hypothesis-scoped contradictions, and false rejection.
- Introduce an experiment registry with immutable configuration snapshots, seeds, baselines, ablations, negative results, and independent review records.
- Develop governance-oriented review gates for proposed changes to identity models, scoring rules, authorization policy, and recursive-improvement workflows.
- Investigate portability across cryptocurrency systems, enterprise identity, cloud authorization, AI-agent execution, and software supply chains, without presuming cross-domain guarantees.
- Confirm that the eight proposed figures exist as **eight separately exported PNG assets**, and reconcile their filenames and placement with `FIGURE-INDEX.md` before release.
- Complete and verify release metadata, citation information, repository links, and the ResearchGate overview against the final public repository state.

**Important:** These are candidate work items, not delivered features or promised timelines.

---

## [0.1.0] — 2026-11-02 (research foundation; release candidate)

### Added — research foundation

- Defined ASSI as a **specification-first, adversarial structural security research program** rather than a deployed security product.
- Established the core proposition that **cryptographic validity does not entail structural security or legitimate authorization**.
- Identified four structural tensions: control versus autonomy, identity versus authorization, efficiency versus safety, and evolution versus stability.
- Introduced trust relocation, structural risk exposure, and bounded-loss analysis as cross-cutting research concerns.
- Distinguished **observed**, **inferred**, **verified**, and **authorized** states; prohibited automatic promotion from evidence or confidence to authority.
- Defined the conceptual roles of UTN compositional identity, REN directional weak evidence, MDT temporal differential structures, and BCEF bidirectional conditional evidence feedback.
- Proposed independently governed authorization and safety control planes, including policy decision and enforcement separation, transaction binding, risk budgets, and recovery paths.
- Described Red, Blue, Evaluation, and Governance adversarial drives and their separation of responsibilities.
- Connected security residuals to AQSI autonomous questioning, candidate improvements, independently validated recursive self-improvement (RSI), and structural relay.
- Established explicit distinctions among **simulation**, **experimental validation**, **independent replication**, **authorization**, and **deployment**.

### Added — core research papers (`docs/`)

| ID | Document | Focus |
|---|---|---|
| ASSI-001 | [From Cryptographic Validity to Structural Security](docs/ASSI-001-From-Cryptographic-Validity-to-Structural-Security.md) | Motivation and security boundary |
| ASSI-002 | [Four Structural Contradictions of Cryptocurrency Security](docs/ASSI-002-Four-Structural-Contradictions-of-Cryptocurrency-Security.md) | Four persistent tensions |
| ASSI-003 | [Trust Relocation and Structural Security Boundaries](docs/ASSI-003-Trust-Relocation-and-Structural-Security-Boundaries.md) | Trust relocation and loss exposure |
| ASSI-004 | [UTN and Compositional Identity Intelligence](docs/ASSI-004-UTN-and-Compositional-Identity-Intelligence.md) | Typed, time-sensitive identity hypotheses |
| ASSI-005 | [REN and Directional Weak Evidence Intelligence](docs/ASSI-005-REN-and-Directional-Weak-Evidence-Intelligence.md) | Weak evidence and directional scoring |
| ASSI-006 | [Bidirectional Conditional Evidence Feedback](docs/ASSI-006-Bidirectional-Conditional-Evidence-Feedback.md) | BCEF, contradictions, and feedback |
| ASSI-007 | [Structural Authorization and Independent Control Planes](docs/ASSI-007-Structural-Authorization-and-Independent-Control-Planes.md) | Independent policy and enforcement |
| ASSI-008 | [Adversarial Security Drives and Competitive Relay](docs/ASSI-008-Adversarial-Security-Drives-and-Competitive-Relay.md) | Separated adversarial roles |
| ASSI-009 | [Security Residuals and Validated Recursive Self-Improvement](docs/ASSI-009-Security-Residuals-and-Validated-Recursive-Self-Improvement.md) | Governed improvement lifecycle |
| ASSI-010 | [ASSI Grand Architecture and Structural Security Units](docs/ASSI-010-ASSI-Grand-Architecture-and-Structural-Security-Units.md) | Overall architecture and units |
| ASSI-011 | [Benchmark Laboratories and Falsifiable Security Hypotheses](docs/ASSI-011-Benchmark-Laboratories-and-Falsifiable-Security-Hypotheses.md) | Benchmark design and falsifiability |
| ASSI-012 | [From Cryptocurrency Security to General Structural Defense](docs/ASSI-012-From-Cryptocurrency-Security-to-General-Structural-Defense.md) | Cross-domain research boundaries |

### Added — draft contracts (`specs/`)

- [SPEC-001 — Structural Security Unit Contract](specs/SPEC-001-Structural-Security-Unit-Contract.md).
- [SPEC-002 — Compositional Identity and UTN Contract](specs/SPEC-002-Compositional-Identity-and-UTN-Contract.md).
- [SPEC-003 — Bidirectional IF and Evidence Impact Contract](specs/SPEC-003-Bidirectional-IF-and-Evidence-Impact-Contract.md).
- [SPEC-004 — Authorization and Safety Control Contract](specs/SPEC-004-Authorization-and-Safety-Control-Contract.md).
- [SPEC-005 — Adversarial Drive and Relay Contract](specs/SPEC-005-Adversarial-Drive-and-Relay-Contract.md).
- [SPEC-006 — Validated RSI and Governance Contract](specs/SPEC-006-Validated-RSI-and-Governance-Contract.md).

These documents describe proposed interfaces and invariants; their existence is **not** evidence of runtime conformance.

### Added — synthetic research cases (`cases/`)

- [CASE-001 — Cryptocurrency Trust and Liquidity](cases/CASE-001-Cryptocurrency-Trust-and-Liquidity.md).
- [CASE-002 — UTN On-Chain Identity Sandbox](cases/CASE-002-UTN-On-Chain-Identity-Sandbox.md).
- [CASE-003 — Bidirectional IF and False Rejection](cases/CASE-003-Bidirectional-IF-and-False-Rejection.md).
- [CASE-004 — Compromised Signing Service Defense](cases/CASE-004-Compromised-Signing-Service-Defense.md).
- [CASE-005 — Adversarial Drives and Security RSI](cases/CASE-005-Adversarial-Drives-and-Security-RSI.md).

These are **illustrative, synthetic cases**, not incident reports or completed experimental results.

### Added — exploratory extensions (`extensions/`)

- [EXT-001 — Multi-Agent Adversarial Security Ecology](extensions/EXT-001-Multi-Agent-Adversarial-Security-Ecology.md).
- [EXT-002 — Autonomous Security Questioning and Exploration](extensions/EXT-002-Autonomous-Security-Questioning-and-Exploration.md).
- [EXT-003 — Cross-Domain Structural Security Transfer](extensions/EXT-003-Cross-Domain-Structural-Security-Transfer.md).
- [EXT-004 — Open-Ended Security Evolution and Governance](extensions/EXT-004-Open-Ended-Security-Evolution-and-Governance.md).

### Added — repository navigation and research planning

- `README.md`: scope, architecture, research positioning, and safety boundaries.
- `START-HERE.md`: reader pathways, core distinctions, and suggested synthetic first exercise.
- `CONTENTS.md`: navigable repository and cross-topic index.
- `GLOSSARY.md`: controlled terminology and conceptual boundaries.
- `FIGURE-INDEX.md`: eight proposed figure descriptions, captions, and insertion guidance.
- `FUTURE-DIRECTIONS.md`: longer-term research program and staged directions.
- `OPEN-QUESTIONS.md`: research questions and candidate discriminating experiments.
- `TESTABLE-HYPOTHESES.md`: TH-01 through TH-30, including baselines, outcomes, and falsification criteria.
- `VALIDATION-ROADMAP.md`: stage-gated experimental plan, BM-001 through BM-004, conformance testing, independent evaluation, and failure records.
- `CHANGELOG.md`: this version and evidence-status history.

### Proposed visual assets (`figures/`)

The initial research design specifies the following figures. **Their presence as individually exported files must be checked independently**; listing them here does not certify that the PNG files exist.

1. `Fig-001-ASSI-Grand-Architecture.png`
2. `Fig-002-Four-Structural-Security-Contradictions.png`
3. `Fig-003-UTN-Compositional-Identity-Hypergraph.png`
4. `Fig-004-BCEF-and-Scoring-Tree-Feedback.png`
5. `Fig-005-Structural-Authorization-Control-Plane.png`
6. `Fig-006-Adversarial-Drives-and-Competitive-Relay.png`
7. `Fig-007-Security-Residual-to-Validated-RSI.png`
8. `Fig-008-ASSI-Benchmark-and-Validation-Roadmap.png`

### Publication preparation

- Planned `CITATION.cff`, `.zenodo.json`, and `LICENSE` metadata (Apache-2.0).
- Planned `release/GitHub-Release-Notes-v0.1.0.md`, `release/ResearchGate-Description.txt`, and `release/ASSI-v0.1.0-ResearchGate-Overview.pdf`.
- Publication status should be confirmed against actual committed files, tags, release assets, and DOI records; this changelog does not assert that a DOI or GitHub Release already exists.

### Research and assurance limitations

- **No benchmark outcomes claimed.** BM-001–BM-004 are proposed evaluation families.
- **No empirical validation claimed.** TH-01–TH-30 are falsifiable hypotheses, not confirmed findings.
- **No runtime implementation or formal verification claimed.** Specifications remain draft research contracts.
- **No security certification or operational endorsement claimed.** Synthetic success does not confer production safety.
- **No autonomous privilege expansion permitted by design.** Evidence, inferred identity, model confidence, or multi-agent consensus must not substitute for independent authorization.
- **No guarantee of cross-domain transfer.** Negative transfer and domain-specific constraints must be reported.

---

## Versioning and change policy

### Semantic intent

- **`0.1.x`** — Initial research foundation, editorial corrections, contract clarification, and validation-plan refinement.
- **`0.x`** — Experimental research evolution; draft interfaces and terminology may change with explicit migration notes.
- **`1.0.0`** — A possible future stable research specification milestone, **not** an assurance certification or declaration of production readiness.

### Change categories

Future entries should distinguish **Added**, **Changed**, **Clarified**, **Deprecated**, **Removed**, **Fixed**, **Security / Governance**, and **Validation Evidence**. A result must not be entered as validated unless its evidence package, test conditions, independent-review status, and limitations are available.

### Required traceability for substantive changes

For changes affecting scoring, identity, authorization, adversarial evaluation, or RSI, record:

1. Affected document IDs and contract versions.
2. Research question, competing hypotheses, and rationale.
3. Expected benefit, possible harm, and protected invariants.
4. Synthetic tests, baselines, negative cases, and regression evidence, if any.
5. Independent reviewer or governance decision, when applicable.
6. Remaining uncertainty, known failures, rollback path, and explicit leftovers.

An editorial change does not imply experimental progress. A model improvement does not imply policy approval. A new release does not silently relax authorization constraints.

## Publication checklist for v0.1.0

- [ ] Verify that all 12 `docs/`, six `specs/`, five `cases/`, and four `extensions/` files are committed and linked correctly.
- [ ] Confirm that all eight figure PNGs are present individually and referenced with accurate relative paths.
- [ ] Check root navigation, glossary terminology, hypothesis numbering, and benchmark identifiers for consistency.
- [ ] Confirm that draft specifications do not claim completed conformance testing.
- [ ] Confirm that synthetic cases are visibly labeled and no simulated outcomes are represented as observed field evidence.
- [ ] Confirm `LICENSE`, `CITATION.cff`, and `.zenodo.json` content and authorship metadata.
- [ ] Confirm release notes, ResearchGate description, and overview PDF match the committed repository version.
- [ ] Check all relative links and document filenames on the intended release tag.
- [ ] Create and inspect the GitHub release tag; verify any Zenodo archive/DOI only after it actually exists.
- [ ] Preserve a list of unresolved research and engineering issues for subsequent releases.

---

## Research ethos

**Contracts before runtime. Conformance before capability claims. Independent authority before consequential action. Negative results before premature certainty. Collective learning without silent privilege transfer.**

The purpose of `v0.1.0` is to establish a coherent, challengeable, and reusable research foundation for adversarial structural security intelligence—not to announce a completed defense system.
