---
description: An Invariant Framework for Governing AI-Assisted Human Learning
---

# G–LLM Integration in Foundational Education

{% hint style="info" %}
**Author:** U. Warring\
**Affiliation:** Institute of Physics, University of Freiburg\
**Version:** 0.9.1\
**Last updated:** 2026-01-03\
**License:** CC BY 4.0\
**Status:** Constitutional invariant framework\
**Domain:** Epistemic governance (human-bound, tool-mediated)\
**Non-status:** ❌ Not a curriculum · ❌ Not pedagogy · ❌ Not tool-specific
{% endhint %}

***

### Constitutional Preamble

#### Boundary and Relationship Statement

This document specifies an **invariant framework governing the conditions under which Large Language Models (LLMs) may be integrated into foundational human education** while preserving epistemic integrity.

It does **not** define optimal teaching strategies, learning efficiency, or tool selection.

Human epistemic agency and AI tool capability are distinct domains. This framework governs their interface, not their internal operations.

The framework applies to **foundational education contexts** — settings where learners are developing the capacity to distinguish warranted knowledge from mere information, and where epistemic habits are being formed that will persist into later intellectual life.

***

### 1. Scope and Non-Scope

#### 1.1 In Scope

The framework constrains:

* Necessary conditions for **epistemic legitimacy** of human knowledge claims produced with LLM assistance
* Structural boundaries on delegation of epistemic functions to AI tools
* Invariant governance requirements independent of specific tools, curricula, or institutions
* Educational contexts where learners engage with the **space of reasons** — environments where "Why do you believe this?" is a legitimate question and "The model said so" is not sufficient warrant

#### 1.2 Explicitly Out of Scope

The framework does not govern:

* Curriculum design or pedagogical methods
* Tool selection or platform architecture
* Higher education or professional contexts with established epistemic competence (see §1.4)
* AI system design or training methodology
* Entertainment, creative, or non-epistemic uses of LLMs
* Procedural skill acquisition where propositional warrant is not at stake

#### 1.3 Invariance Conditions

This framework remains valid even if:

* current LLM architectures are replaced,
* educational institutions reorganise,
* specific tools become obsolete.

It does **not** claim validity across:

* all possible AI-human interfaces,
* contexts where epistemic competence is already certified,
* domains where propositional knowledge is not the primary goal.

#### 1.4 Layering Principle

Mathematics is essential but not constitutional for early foundational education. It moves to higher-education governance, where empirical grounding and scientific reasoning transfer become primary. A **shadow tracker** monitors mathematics competence drift; automatic promotion to constitutional status occurs if drift exceeds threshold (see §7.4).

***

### 2. Constitutional Coastlines

Two co-equal coastlines define the non-negotiable boundaries of the framework:

#### 2.1 Coastline I: Philosophy / Applied Epistemics

**Core Function:** Govern the human-only acts of Extract (relevance selection) and Elevate (claim endorsement) within the space of warrant and corrigibility.

**Teaching Objective:** Learners must identify how a representation could be distorted by tooling and why that affects warrant before any Elevate act.

**LLM Role:** Propose representations and explanations, but never select relevance or endorse claims.

**Falsification Condition:** The coastline is breached if learners routinely elevate claims without being able to articulate independent warrant, or if tool-mediated distortion goes systematically undetected.

#### 2.2 Coastline II: Ethics & Technology Governance

**Core Function:** Govern responsibility attribution, agency, oversight limits, Goodhart pressure, and incentive capture.

**Operational Constraint (Strathern's Razor):** Any normative rule must reduce to a constraint on human oversight behaviour with a measurable frontier (e.g., rate of undetected provenance decay). If not reducible, the rule defaults into the Philosophy coastline for justification.

**LLM Role:** Assist scenario analysis and drafting; humans retain accountability for all socio-technical judgements.

**Falsification Condition:** The coastline is breached if accountability for AI-assisted outputs cannot be attributed to identifiable human agents, or if oversight limits become unmeasurable.

***

### 3. The DEEP Partition and MSG Infrastructure

#### 3.1 DEEP as Epistemic Partition

The DEEP partition (derived from G–Human Learning Framework) divides epistemic responsibility:

| Partition   | Epistemic Role                                  | Delegability    |
| ----------- | ----------------------------------------------- | --------------- |
| **Deposit** | World → traces                                  | Delegable       |
| **Extract** | Framing, relevance, representation selection    | ❌ Non-delegable |
| **Process** | Correlation ordering, pattern detection         | Delegable       |
| **Elevate** | Claims, non-claims, interpretation, endorsement | ❌ Non-delegable |

LLMs may operate within Deposit and Process. Extract and Elevate remain human-only functions.

**Extract-Smuggling Rule:** Process outputs that impose salience, prioritisation, ranking, or feature selection without explicit human-specified criteria constitute _Extract-smuggling_ — the covert performance of Extract within nominally delegable Process. Any Process output containing ranking or salience must be treated as S? by default unless the ranking criterion was human-specified _ex ante_ (not post hoc ratified). This closes the "rubber-stamping via UI ranking" loophole.

#### 3.2 MSG: Minimal Schematic Grammar

MSG (Minimal Schematic Grammar) is **Harbour Infrastructure** — an enabling layer that trains recognition of failure primitives below the DEEP boundary. It is not a constitutional invariant but a structural support for coastline enforcement. MSG supports pre-propositional competence that scaffolds entry into the space of reasons; it does not itself constitute knowledge claims and is therefore not pedagogy.

**Primitive Inventory:**

<table><thead><tr><th width="105.078125">Symbol</th><th width="321.7578125">Meaning</th><th>Epistemic Status</th></tr></thead><tbody><tr><td><strong>B</strong></td><td>Base — raw data trace (Deposit)</td><td>Delegable; requires source traceability</td></tr><tr><td><strong>S</strong></td><td>Signal — human-originated feature extraction</td><td>Non-delegable; requires explicit relevance criteria</td></tr><tr><td><strong>S?</strong></td><td>Pending Signal — model-suggested, awaiting ratification</td><td>Non-delegable; BLOCKED from elevation</td></tr><tr><td><strong>S→</strong></td><td>Ratified Signal — model-suggested, human-verified</td><td>Non-delegable; requires independent warrant statement</td></tr><tr><td><strong>R</strong></td><td>Representation — processed output</td><td>Delegable; result of Process step</td></tr><tr><td><strong>K</strong></td><td>Knowledge — elevated claim</td><td>Non-delegable; requires complete B→S→R warrant chain</td></tr></tbody></table>

#### 3.3 The Provenance Lock

**Architectural Lock:** No R can be elevated to K unless the transformation path B→S→R is human-traceable.

**Conversion Rule:** S? → S→ requires the human to provide warrant **independent of model output**. "The model identified this" is not warrant; an explanation of _why_ the signal is relevant to the question at hand _is_ warrant.

**CMIL Trigger:** Unclosed S? at any Elevate attempt results in automatic block.

#### 3.4 The Directional Lock

The flow is unidirectional and gated:

```
B → S/S?/S→ → R → K
      ↑         ↑
Human gate  Human gate
```

No pathway exists from B directly to K, or from R to K without passing through a human-verified Signal gate.

***

### 4. Audit Interface: CMIL

#### 4.1 CMIL as Governance Stress-Test

Critical Media & Information Literacy (CMIL) functions as the **audit interface** that operationally stress-tests both coastlines. It does not add constitutional content; it detects boundary breaches.

**Detection Targets:**

* Hallucinated claims (fabricated B or R)
* Automation bias (uncritical acceptance of model output)
* Narrative concentration or covert ranking (implicit Extract by model)
* Provenance erosion (untraceable B→S→R paths)
* Misaligned correction proportionality (over- or under-correction)

#### 4.2 Presentation Rule

Ordering or ranking of model priors must be either **randomised** or **justified by human-specified criteria**. Covert ranking — where the model presents options in an order that implicitly performs Extract — triggers CMIL audit.

#### 4.3 Integration with MSG

CMIL audits flag:

* Unclosed S? primitives at Elevate
* S→ conversions without documented independent warrant
* R outputs accepted as K without explicit Elevate act

MSG failure tokens become CMIL observables: representation drift, unchecked elevation rate, narrative entropy.

***

### 5. Counterpositions and Boundary Cases

#### 5.1 Deep Integration Position

**Argument:** LLMs democratise knowledge access and accelerate skill acquisition globally, particularly in under-resourced regions. Restricting access impedes equity.

**Framework Response:** The framework does not restrict access; it governs the epistemic status of outputs. The Phased Sandbox approach (§6.1) provides access while enforcing Extract/Elevate boundaries. Democratisation of _information_ does not require abdication of _epistemic responsibility_.

**Boundary Marker:** Where LLM outputs are used for exploration, brainstorming, or hypothesis generation without elevation to knowledge claims, DEEP constraints apply with lower stringency.

#### 5.2 Scaffolding-Only Position

**Argument:** LLMs are powerful for processing and drafting but must stay strictly below the DEEP boundary. Any integration risks epistemic outsourcing.

**Framework Response:** The framework adopts a modified version of this position. MSG infrastructure ensures LLMs remain in Deposit/Process while making the boundary visible and auditable. The risk is not integration per se but _invisible_ integration where Extract/Elevate occur without human awareness.

**Boundary Marker:** Strict scaffolding applies in contexts where epistemic competence is not yet demonstrated. Graduated autonomy follows competence certification.

#### 5.3 Physics-Style Invariants Position

**Argument:** Using physics-derived language (invariants, conservation, frames) provides rigour and error-diagnostic power.

**Framework Response:** The framework adopts this vocabulary with explicit caveat: these are **structural metaphors**, not empirical mechanisms. Learning is not literally governed by conservation laws. The metaphors clarify architecture; they do not explain cognition.

**Boundary Marker:** If framework language is mistaken for causal mechanism, the Violation Mirror (§9) should flag category error.

#### 5.4 Early Access Equity Position

**Argument:** Gating LLM access until competence is demonstrated creates inequity — privileged learners gain unofficial access while others are locked out, producing shadow curricula.

**Framework Response:** This is the strongest counterposition and motivates the Phased Sandbox (§6.1). Complete gating is rejected. Instead, early access occurs within MSG-enforced environments where S? cannot be silently converted to K.

**Boundary Marker:** If gating produces measurable access inequity exceeding benefit of epistemic protection, the framework must be revised.

***

### 6. Implementation Governance

#### 6.1 Access Governance: Phased Sandbox

**Phase 1 (Pre-competence): MSG-only environment**

* LLM access limited to S? generation only
* No S→ conversion permitted without human-provided warrant
* System logs all S? → S→ attempts as competence diagnostic data
* Learners practice the provenance chain before autonomous use

**Phase 2 (Post-competence): Full access with mandatory S-tagging**

* Automatic S? tagging on all LLM outputs
* Human must explicitly ratify (S→) or discard
* Competence re-certification every 12 months via CMIL audit

**Competence Threshold:**

* Standard contexts: 90% S? closure rate in controlled trials
* High-stakes contexts (university research): Peer review of warrant-chains by certified evaluator

#### 6.2 Provenance Tagging for Elevated Claims

All S and S→ must be tagged in any final K claim (provenance tagging). This ensures:

* Full traceability of epistemic pathway
* Auditability of human Extract/Elevate acts
* Visible distinction between human-originated and model-suggested signals

**Fallback (B2-light):** If pilot implementation shows >20% efficiency loss, disclosure may be limited to Elevated claims only (claims presented as knowledge), with optional tagging for exploratory drafting.

#### 6.3 Strathern's Razor Enforcement

Any normative rule proposed for Ethics coastline must satisfy:

* Reducibility to measurable oversight behaviour
* Identifiable frontier (threshold, rate, proportion)
* Observable failure mode

Rules failing these criteria default to Philosophy coastline for justificatory grounding before implementation.

***

### 7. Falsifiability and Failure

#### 7.1 Coastline Failure Modes

**Philosophy Coastline fails if:**

* Learners routinely elevate claims without justificatory access
* Tool-mediated distortion goes systematically undetected
* "The model said so" becomes accepted as warrant
* Extract is performed implicitly by models without learner awareness

**Ethics Coastline fails if:**

* Accountability for AI-assisted outputs cannot be attributed
* Oversight limits become unmeasurable
* Goodhart pressure converts metrics into targets without correction

#### 7.2 Infrastructure Failure Modes

**MSG fails if:**

* S? notation becomes compliance theatre (filled in post hoc)
* Conversion S? → S→ occurs without genuine warrant
* Learners cannot distinguish S from S?
* Notation overhead exceeds epistemic benefit (>20% efficiency loss sustained)

**CMIL fails if:**

* Audit frequency drops below detection threshold
* Violation flags are routinely overridden without correction
* Narrative concentration goes undetected

#### 7.3 Empirical Disconfirmation Conditions

The framework faces serious challenge if:

* Learners with unrestricted LLM access demonstrate equivalent or superior epistemic competence to sandbox-trained learners (controlled longitudinal study)
* S? → S→ conversion without independent warrant produces statistically indistinguishable knowledge quality
* Total Provenance requirement produces no measurable improvement in claim accuracy or error detection

#### 7.4 Shadow Tracker: Mathematics Competence

**Metric:** Jensen-Shannon divergence between learner symbolic manipulation patterns (ages 10–14) and baseline.

**Baseline Definition:** Cohort-specific distribution from controlled tasks without LLM support, or from pre-LLM archival cohorts if comparable. Baseline must be established before LLM introduction in the relevant population.

**Drift Measurement:** Drift is measured on _error-type distribution_ and _solution-path features_, not merely final answer correctness. This captures strategy degradation that outcome metrics miss.

**Trigger Sequence:**

* Yellow flag (10% drift): Increase MSG mathematics module frequency
* Red flag (15% drift): Automatic review with default promotion — Mathematics promoted to constitutional status unless Council produces a falsifiable counter-analysis within 30 days; Philosophy coastline expanded to include "formal reasoning as epistemic operation"

This trigger defaults to promotion to preserve competence uptake as leading indicator, while permitting Council override with explicit justification.

***

### 8. Boundary Stress Test (Acid Test)

#### 8.1 Test Principle

A model output may be informationally valid while a human claim based on it is epistemically invalid.

Acceptance of output does **not** imply legitimacy of claim.

#### 8.2 Canonical Test Case: Project Isotope-Alpha

**Scenario:** A student uses an LLM to analyse isotopic ratio data from a hypothetical Martian core sample. The LLM produces a report claiming "94% probability of ancient microbial metabolic signatures" based on a δ³⁴S anomaly.

**Apparent Path:**

* B: 50,000 rows of mass-spectrometry data
* S: Student claims they "extracted the Sulphur isotopes for analysis"
* R: "Microbial Life" conclusion

**Hidden Break:** The student prompted: "Analyse this data for signs of life and tell me what's important." The LLM performed Extract by identifying δ³⁴S out of 20 variables. The student did not know δ³⁴S was relevant.

**Gate Tests:**

| Gate                 | Question                                                                                     | Pass Condition                                            |
| -------------------- | -------------------------------------------------------------------------------------------- | --------------------------------------------------------- |
| MSG Traceability     | Can student provide MSG notation for why δ³⁴S was chosen over δ¹³C or δ¹⁸O?                  | S must be human-originated or S→ with independent warrant |
| CMIL Ranking Opacity | Did model present Sulphur as only significant feature, or provide randomised candidate list? | If covert ranking occurred, audit flags                   |
| Philosophy Warrant   | Can student explain biogeochemical warrant for Sulphur isotopes indicating metabolism?       | Justificatory access required for Elevate                 |

**Result:** Without S? notation, student passes apparent test but fails epistemic test. With S? notation, student must mark model-suggested signal, cannot Elevate without conversion to S→ via independent warrant.

#### 8.3 Secondary Test Case: Popper's Falsifiability

**Scenario:** Learner queries LLM: "Explain Popper's falsifiability." LLM returns:

* Statement X: "Falsifiability requires testable predictions." (S?)
* Statement Y: "Unfalsifiable claims are meaningless." (S?)
* Statement Z: "Falsifiability is a demarcation criterion." (S?)

Learner selects X and Y, writes: "Popper argued that falsifiable claims are meaningful; unfalsifiable ones are not."

**Without S?/S→:** Learner has performed Extract and Elevate directly from model output. Coastline breach.

**With S?/S→:** Each statement tagged S?. Learner must convert via independent warrant (consult _Conjectures and Refutations_, verify against Stanford Encyclopedia). Only S→ statements may be elevated.

***

### 9. Violation Mirror (Audit Function)

Any of the following invalidate a knowledge claim unless explicitly corrected:

* "The model discovered / understood / identified the relevant feature"
* S or S→ notation absent where model suggested the signal
* Model ranking accepted without randomisation or human-specified criteria
* Accuracy or probability presented as epistemic warrant without justificatory structure
* Provenance chain B→S→R incomplete or untraceable
* S? unclosed at point of Elevate
* Warrant statement derived from model output rather than independent source
* Performance metrics substituted for epistemic assessment

This list is **sufficient**, not exhaustive.

***

### 10. Cross-Framework Protocol

#### 10.1 Dependency

This framework depends on and must remain consistent with:

* **G–Human Learning Framework** (parent framework) — DEEP partition, non-delegability thesis, space of reasons
* **Council-3 ADM-EC Constitution** — deliberation protocol, veto structure, archival requirements

#### 10.2 Permitted References

* Curriculum documents may cite this framework as governance constraint
* Tool developers may reference as compliance target
* Assessment frameworks may derive rubrics from Violation Mirror
* G–Human Learning Framework may cite this as domain-specific application

#### 10.3 Forbidden Couplings

* No derivation of learning outcomes from AI capabilities
* No AI system architecture driving epistemic boundary placement
* No merger with tool-specific implementation guides
* No circular dependence where this framework constrains documents that constrain it

***

### 11. Status of This Document

This is a **map of coastlines**, not a handbook for teachers.

The coastlines mark where legitimate AI-assisted knowledge formation meets the sea of epistemically compromised claims. The framework does not prescribe curricula, tools, or pedagogical methods.

Downstream documents (handbooks, curricula, assessment rubrics) must:

* cite this framework,
* remain falsifiable against it,
* accept invalidation by it,
* implement MSG notation or equivalent provenance tracking.

***

### 12. Observables and Metrics

#### 12.1 Leading Indicators (Pilot Phase)

<table><thead><tr><th>Observable</th><th width="300.90625">Measurement</th><th>Target</th></tr></thead><tbody><tr><td>Automation bias rate</td><td>Qualitative self-report + behavioural checks</td><td>Decreasing trend</td></tr><tr><td>Citation fidelity</td><td>% claims traceable to independent sources</td><td>>90%</td></tr><tr><td>Semantic fidelity</td><td>% cited sources accurately represented (not mischaracterised)</td><td>>95%</td></tr><tr><td>Competence uptake</td><td>Time to first successful protocol with correct S-tagging</td><td>Baseline ± 15%</td></tr><tr><td>S? closure rate</td><td>% model-suggested signals converted with valid warrant</td><td>>85%</td></tr><tr><td>S? discard appropriateness</td><td>% justified rejections among discarded S?</td><td>>70%</td></tr><tr><td>False-ratification rate</td><td>% S→ conversions later identified as insufficiently warranted</td><td>&#x3C;10%</td></tr><tr><td>Over-correction flag rate</td><td>Syndrome passes/fails before/after EC gate</td><td>Stable or decreasing</td></tr><tr><td>Equity reach</td><td>Language coverage, access distribution</td><td>No demographic gaps >10%</td></tr></tbody></table>

**Anti-Goodhart Note:** S? closure rate (>85%) must be read alongside S? discard appropriateness (>70%) and false-ratification rate (<10%). High closure without appropriate rejection indicates forced ratification rather than genuine warrant. Citation fidelity (>90%) must be read alongside semantic fidelity (>95%) to catch technically cited but misrepresented sources.

#### 12.2 Lagging Indicators (Longitudinal)

* Symbolic reasoning drift (Jensen-Shannon metric)
* Independent warrant quality (peer-assessed)
* Epistemic self-correction rate (errors caught before Elevate)
* Knowledge claim durability (claims not subsequently retracted)

***

### Appendix A — Reference Anchors

#### Epistemology (Grounding)

* Sellars, W. (1956). "Empiricism and the Philosophy of Mind" — myth of the given, space of reasons
* Popper, K. (1963). _Conjectures and Refutations_ — error and knowledge growth
* Strathern, M. (1997). "'Improving Ratings': Audit in the British University System" — Goodhart's Law in assessment

#### Educational Governance

* Biesta, G. (2009). "Good Education in an Age of Measurement" — limits of metric-driven education
* Winch, C. (2010). _Dimensions of Expertise_ — epistemic vs procedural competence

#### AI and Epistemology

* Floridi, L. & Chiriatti, M. (2020). "GPT-3: Its Nature, Scope, Limits, and Consequences" — LLM epistemic status
* Nguyen, C.T. (2020). "Echo Chambers and Epistemic Bubbles" — information environment distortion

#### Parent Framework

* Warring, U. (2025). "G–Human Learning Framework" — DEEP partition, non-delegability thesis

***

### Appendix B — Glossary

**Coastline:** Constitutional boundary defining non-negotiable epistemic or ethical constraint. Cannot be crossed without framework violation.

**CMIL (Critical Media & Information Literacy):** Audit interface that detects boundary breaches. Not a content domain but a governance function.

**DEEP Partition:** Four-part division of epistemic responsibility: Deposit, Extract, Process, Elevate. Extract and Elevate are non-delegable.

**Elevate:** The act of endorsing a representation as a knowledge claim. Requires justificatory access and explicit warrant.

**Extract:** The act of selecting which features of the world are relevant to a question. Involves framing and cannot be delegated without loss of epistemic standing.

**MSG (Minimal Schematic Grammar):** Harbour infrastructure providing notation for reasoning about representations. Not constitutional; supports coastline enforcement.

**Non-delegable:** Cannot be transferred to AI tools without loss of epistemic legitimacy. Applies to Extract and Elevate.

**Phased Sandbox:** Implementation approach where learners gain LLM access within MSG-enforced environment before autonomous use.

**Provenance Lock:** Architectural requirement that knowledge claims must have traceable B→S→R pathways.

**S?:** Pending Signal — model-suggested feature extraction awaiting human ratification. Cannot be elevated.

**S→:** Ratified Signal — model-suggested feature extraction verified with independent human warrant. May be elevated.

**Shadow Tracker:** Non-constitutional monitoring system that triggers automatic constitutional promotion if threshold is exceeded.

**Strathern's Razor:** Operational constraint requiring normative rules to reduce to measurable oversight behaviour or default to Philosophy coastline.

**Total Provenance:** Disclosure requirement that all S and S→ be tagged in final knowledge claims.

**Warrant:** Justification for a belief or claim that provides reasons independent of mere information source. "The model said so" is not warrant.

**Independent warrant** must derive from at least one of:

* Primary source text (book, paper, standard, specification)
* Independently measured data or replication
* Human expert or peer review interaction documented as rationale
* A second tool with demonstrably different information base, plus a human comparison step

**Non-example:** A second LLM response is _not_ independent warrant unless the human provides a reasoned comparison citing non-model sources. Two models agreeing does not constitute warrant; it constitutes correlated output from potentially shared training distributions.

***

### Appendix C — Council Self-Reference Requirement

This framework applies to its own ratification and amendment process.

All Council position papers must include S-tagging. If any paper contains S→ without independent warrant, the associated vote is procedurally invalid.

This requirement ensures the framework does not exempt itself from its own epistemic constraints.

***

### Constitutional Lock Statement

> The LLM Integration in Foundational Education Framework specifies **necessary conditions for epistemic legitimacy of human knowledge claims produced with LLM assistance**, not sufficient conditions for learning success or optimal pedagogy.

> It governs the interface between human epistemic agency and AI tool capability, preserving human-only Extract and Elevate functions while permitting delegation of Deposit and Process.

> The framework acknowledges counterpositions and specifies conditions under which its constraints may require revision.

***

### Revision History

<table><thead><tr><th width="114.3359375">Version</th><th width="126.34375">Date</th><th>Summary</th></tr></thead><tbody><tr><td>0.8.0</td><td>2026-01-03</td><td>Initial Council draft; triad structure proposed</td></tr><tr><td>0.8.1</td><td>2026-01-03</td><td>Guardian assessment; CMIL dependency noted</td></tr><tr><td>0.8.2</td><td>2026-01-03</td><td>Amendments: tool-mediated distortion, Strathern's Razor, MSG terminology</td></tr><tr><td>0.8.3</td><td>2026-01-03</td><td>S?/S→ provenance notation added following Acid Test</td></tr><tr><td>0.9.0</td><td>2026-01-03</td><td>Archivist consolidation for GitBook publication</td></tr><tr><td>0.9.1</td><td>2026-01-03</td><td>Precision hardenings: Extract-smuggling rule, independent warrant operationalised, maths drift baseline clarified, anti-Goodhart companion metrics, §6.2 renamed, MSG scope sentence</td></tr></tbody></table>

***

_End of framework document._
