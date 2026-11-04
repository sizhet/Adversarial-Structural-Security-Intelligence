# Contents — Adversarial Structural Security Intelligence (ASSI)

**Version:** v0.1.0 — Research Foundation  
**Status:** Research proposals, draft specifications, synthetic case designs, and validation plans  
**License:** Apache-2.0 (subject to the repository's `LICENSE` file)

> **Cryptographic validity is not structural security.** Inference is not authorization; a simulation is not validation; validated evidence is not permission to deploy.

This index is the canonical navigation map for the ASSI research repository. It organizes **12 core research articles, 6 specification drafts, 5 synthetic case studies, and 4 extensions** (27 substantive documents), alongside eight research figures and publication/navigation materials. File links are relative to the repository root.

## 1. Quick entry points

| Entry | Purpose |
|---|---|
| [README.md](README.md) | Research motivation, overall architecture, scope, and limitations |
| [START-HERE.md](START-HERE.md) | Audience-specific reading paths and a first research exercise |
| **CONTENTS.md** | Complete document and figure index |
| [GLOSSARY.md](GLOSSARY.md) | Shared vocabulary and distinctions *(publication asset)* |
| [FIGURE-INDEX.md](FIGURE-INDEX.md) | Figure descriptions and suggested placements *(publication asset)* |
| [VALIDATION-ROADMAP.md](VALIDATION-ROADMAP.md) | Proposed staged validation program *(publication asset)* |

*Publication asset* indicates an entry in the repository structure, not a claim that the file has already been independently verified or released.

## 2. Core research — `docs/` (ASSI-001–012)

The sequence moves from the motivating security contradictions to identity, evidence, reasoning, authorization, adversarial learning, system architecture, benchmarks, and cross-domain implications.

| No. | Article | Research focus |
|---|---|---|
| 001 | [From Cryptographic Validity to Structural Security](docs/ASSI-001-From-Cryptographic-Validity-to-Structural-Security.md) | Why valid local checks can coexist with systemic insecurity |
| 002 | [Four Structural Contradictions of Cryptocurrency Security](docs/ASSI-002-Four-Structural-Contradictions-of-Cryptocurrency-Security.md) | Fundamental tensions requiring structural management |
| 003 | [Trust Relocation and Structural Security Boundaries](docs/ASSI-003-Trust-Relocation-and-Structural-Security-Boundaries.md) | Trust dependencies, relocated risks, and boundary analysis |
| 004 | [UTN and Compositional Identity Intelligence](docs/ASSI-004-UTN-and-Compositional-Identity-Intelligence.md) | Typed identity, dynamic coalitions, overlapping control, temporal hypotheses |
| 005 | [REN and Directional Weak-Evidence Intelligence](docs/ASSI-005-REN-and-Directional-Weak-Evidence-Intelligence.md) | Relational evidence navigation, directional relevance, evidence dependence |
| 006 | [Bidirectional Conditional Evidence Feedback](docs/ASSI-006-Bidirectional-Conditional-Evidence-Feedback.md) | Forward/reverse/counterfactual/contradiction IF and structured impact |
| 007 | [Structural Authorization and Independent Control Planes](docs/ASSI-007-Structural-Authorization-and-Independent-Control-Planes.md) | Independent authority, execution binding, bounded loss |
| 008 | [Adversarial Security Drives and Competitive Relay](docs/ASSI-008-Adversarial-Security-Drives-and-Competitive-Relay.md) | Red/Blue/Evaluation/Governance roles and security experiments |
| 009 | [Security Residuals and Validated Recursive Self-Improvement](docs/ASSI-009-Security-Residuals-and-Validated-Recursive-Self-Improvement.md) | Residual-to-question-to-candidate-to-independent-validation lifecycle |
| 010 | [ASSI Grand Architecture and Structural Security Units](docs/ASSI-010-ASSI-Grand-Architecture-and-Structural-Security-Units.md) | Integration architecture and interoperable security units |
| 011 | [Benchmark Laboratories and Falsifiable Security Hypotheses](docs/ASSI-011-Benchmark-Laboratories-and-Falsifiable-Security-Hypotheses.md) | Benchmarks, baselines, ablations, metrics, and failure conditions |
| 012 | [From Cryptocurrency Security to General Structural Defense](docs/ASSI-012-From-Cryptocurrency-Security-to-General-Structural-Defense.md) | Cross-domain reuse with target-specific security boundaries |

**Suggested conceptual route:** 001 → 002 → 004 → 005 → 006 → 007 → 008 → 009 → 010 → 011 → 012. Read 003 early when trust-boundary analysis is the primary concern.

## 3. Engineering contracts — `specs/` (SPEC-001–006)

These are **proposed normative contracts** for research and conformance design, not independently certified standards. Implementations must separately demonstrate compliance.

| No. | Specification | Contract scope |
|---|---|---|
| 001 | [Structural Security Unit Contract](specs/SPEC-001-Structural-Security-Unit-Contract.md) | Canonical SSU envelope, types, provenance, versioning, lifecycle |
| 002 | [Compositional Identity and UTN Contract](specs/SPEC-002-Compositional-Identity-and-UTN-Contract.md) | Identity naming, temporal hypergraph, scoped identity hypotheses |
| 003 | [Bidirectional IF and Evidence Impact Contract](specs/SPEC-003-Bidirectional-IF-and-Evidence-Impact-Contract.md) | BCEF tests, four-valued assessments, evidence dependency, impact |
| 004 | [Authorization and Safety Control Contract](specs/SPEC-004-Authorization-and-Safety-Control-Contract.md) | Independent PDP/PEP, bounded exposure, approvals, recovery |
| 005 | [Adversarial Drive and Relay Contract](specs/SPEC-005-Adversarial-Drive-and-Relay-Contract.md) | Role separation, experiment lifecycle, evaluation and relay |
| 006 | [Validated RSI and Governance Contract](specs/SPEC-006-Validated-RSI-and-Governance-Contract.md) | Candidate promotion, independent validation, governance, rollback |

**Implementation order:** SPEC-001 → SPEC-002/003 → SPEC-004 → SPEC-005 → SPEC-006. The slash denotes parallelizable reading, not permission to omit shared contract requirements.

## 4. Synthetic case studies — `cases/` (CASE-001–005)

Cases define **hypothetical scenarios and test designs**. They are not reports of executed benchmarks or claims about identifiable real-world entities.

| No. | Case | Main experimental question |
|---|---|---|
| 001 | [Cryptocurrency Trust and Liquidity](cases/CASE-001-Cryptocurrency-Trust-and-Liquidity.md) | Can liquidity remain useful while compromised authority has bounded exposure? |
| 002 | [UTN On-Chain Identity Sandbox](cases/CASE-002-UTN-On-Chain-Identity-Sandbox.md) | Can compositional, temporal identity models reduce false merges and splits? |
| 003 | [Bidirectional IF and False Rejection](cases/CASE-003-Bidirectional-IF-and-False-Rejection.md) | Can hypothesis-scoped contradiction reduce false rejection without losing correct rejection? |
| 004 | [Compromised Signing-Service Defense](cases/CASE-004-Compromised-Signing-Service-Defense.md) | Can independent authorization constrain loss when a signature is technically valid? |
| 005 | [Adversarial Drives and Security RSI](cases/CASE-005-Adversarial-Drives-and-Security-RSI.md) | Can adversarial relay produce improvements that survive independent, out-of-sample tests? |

## 5. Research extensions — `extensions/` (EXT-001–004)

| No. | Extension | Research focus |
|---|---|---|
| 001 | [Multi-Agent Adversarial Security Ecology](extensions/EXT-001-Multi-Agent-Adversarial-Security-Ecology.md) | Cooperative/competitive agents, evidence independence, common-mode failures |
| 002 | [Autonomous Security Questioning and Exploration](extensions/EXT-002-Autonomous-Security-Questioning-and-Exploration.md) | AQSI question units, bounded exploration, testable unknowns |
| 003 | [Cross-Domain Structural Security Transfer](extensions/EXT-003-Cross-Domain-Structural-Security-Transfer.md) | Typed partial mappings, negative transfer, target-domain validation |
| 004 | [Open-Ended Security Evolution and Governance](extensions/EXT-004-Open-Ended-Security-Evolution-and-Governance.md) | Open-ended learning, authority drift, governance of governance |

## 6. Research figures — `figures/` (Fig-001–008)

These are the **intended individual figure filenames** for the repository. Verify that each individual PNG has been exported and placed at the indicated path before publication; a composite figure sheet does not itself create eight individual PNG assets.

| No. | Figure | Best accompanying content |
|---|---|---|
| 001 | [ASSI Grand Architecture](figures/Fig-001-ASSI-Grand-Architecture.png) | README; ASSI-010 |
| 002 | [Four Structural Security Contradictions](figures/Fig-002-Four-Structural-Security-Contradictions.png) | ASSI-002 |
| 003 | [UTN Compositional Identity Hypergraph](figures/Fig-003-UTN-Compositional-Identity-Hypergraph.png) | ASSI-004; SPEC-002; CASE-002 |
| 004 | [BCEF and Scoring Tree Feedback](figures/Fig-004-BCEF-and-Scoring-Tree-Feedback.png) | ASSI-006; SPEC-003; CASE-003 |
| 005 | [Structural Authorization Control Plane](figures/Fig-005-Structural-Authorization-Control-Plane.png) | ASSI-007; SPEC-004; CASE-004 |
| 006 | [Adversarial Drives and Competitive Relay](figures/Fig-006-Adversarial-Drives-and-Competitive-Relay.png) | ASSI-008; SPEC-005; CASE-005 |
| 007 | [Security Residual to Validated RSI](figures/Fig-007-Security-Residual-to-Validated-RSI.png) | ASSI-009; SPEC-006 |
| 008 | [ASSI Benchmark and Validation Roadmap](figures/Fig-008-ASSI-Benchmark-and-Validation-Roadmap.png) | ASSI-011; VALIDATION-ROADMAP |

See [FIGURE-INDEX.md](FIGURE-INDEX.md) for detailed captions and placement guidance once that index is finalized.

## 7. Benchmark families and their source documents

| Benchmark | Subject | Key reading |
|---|---|---|
| **BM-001** | Compositional identity and temporal control | ASSI-004, SPEC-002, CASE-002 |
| **BM-002** | BCEF evidence revision and false rejection | ASSI-006, SPEC-003, CASE-003 |
| **BM-003** | Independent authorization and bounded loss | ASSI-007, SPEC-004, CASE-001, CASE-004 |
| **BM-004** | Adversarial relay and validated RSI | ASSI-008, ASSI-009, SPEC-005, SPEC-006, CASE-005 |

**Recommended evidence hierarchy:** documented hypothesis → preregistered protocol → controlled baseline/ablation → held-out evaluation → independent replication → narrowly scoped conclusion. An architectural proposal alone does not establish a security guarantee.

## 8. Cross-cutting research themes

| Theme | Research papers | Contracts | Cases / extensions |
|---|---|---|---|
| Identity, UTN, and compositional control | ASSI-004 | SPEC-001, SPEC-002 | CASE-002, EXT-001 |
| REN, weak evidence, and dependence | ASSI-005 | SPEC-001, SPEC-003 | CASE-002, CASE-003 |
| BCEF and hypothesis-scoped contradiction | ASSI-006 | SPEC-003 | CASE-003 |
| Independent authorization and bounded loss | ASSI-003, ASSI-007 | SPEC-004 | CASE-001, CASE-004 |
| Adversarial security and competitive relay | ASSI-008 | SPEC-005 | CASE-005, EXT-001 |
| AQSI, residuals, and validated RSI | ASSI-009 | SPEC-006 | CASE-005, EXT-002, EXT-004 |
| Architecture and interoperability | ASSI-010 | SPEC-001–006 | All cases |
| Benchmarking, falsification, and transfer | ASSI-011, ASSI-012 | SPEC-001–006 | EXT-003, EXT-004 |

## 9. Repository root and publication assets

| File | Role |
|---|---|
| [README.md](README.md) | Main project introduction |
| [START-HERE.md](START-HERE.md) | Guided entry point |
| **CONTENTS.md** | Master navigation index |
| [GLOSSARY.md](GLOSSARY.md) | Terminology, acronyms, and epistemic distinctions |
| [FIGURE-INDEX.md](FIGURE-INDEX.md) | Captions and figure-to-article mapping |
| [FUTURE-DIRECTIONS.md](FUTURE-DIRECTIONS.md) | Long-term research possibilities |
| [OPEN-QUESTIONS.md](OPEN-QUESTIONS.md) | Unresolved problems and counterarguments |
| [TESTABLE-HYPOTHESES.md](TESTABLE-HYPOTHESES.md) | Consolidated falsifiable hypotheses |
| [VALIDATION-ROADMAP.md](VALIDATION-ROADMAP.md) | Experimental milestones and acceptance criteria |
| [CHANGELOG.md](CHANGELOG.md) | Document and release history |
| [CITATION.cff](CITATION.cff) | Machine-readable citation metadata |
| [.zenodo.json](.zenodo.json) | Zenodo deposit metadata |
| [LICENSE](LICENSE) | Authoritative license text |

### Release materials — `release/`

- [GitHub Release Notes v0.1.0](release/GitHub-Release-Notes-v0.1.0.md)
- [ResearchGate Description](release/ResearchGate-Description.txt)
- [ResearchGate Overview PDF](release/ASSI-v0.1.0-ResearchGate-Overview.pdf)

**Publication check:** confirm that all links resolve in the actual GitHub tree, that the eight individual figures exist, that license/citation/Zenodo metadata agree, and that the release tag and DOI references are updated only after publication. Do not substitute a future DOI placeholder with an invented identifier.

## 10. Research status, safety, and participation

ASSI v0.1.0 is a **research foundation**. The repository's specifications are drafts; its case studies and benchmark plans are synthetic; its falsifiable hypotheses are questions for testing rather than established results. It does not assert completed independent evaluation, production readiness, or security certification.

All adversarial work should remain inside explicitly authorized, isolated, bounded environments. Adaptive evidence, identity inference, and autonomous questioning **must not** independently grant execution authority. Consequential actions require target-specific independent controls, review, and recovery.

Contributions are particularly useful when they supply reproducible counterexamples, clearer contract semantics, independent conformance tests, failed transfers, or carefully bounded empirical findings. Negative results should be preserved with provenance rather than silently discarded.

---

**Repository path:** `CONTENTS.md`  
**Related entry points:** [README](README.md) · [START-HERE](START-HERE.md)  
**Guiding principle:** *Specifications first. Falsifiable hypotheses. Independent validation. Collective learning.*
