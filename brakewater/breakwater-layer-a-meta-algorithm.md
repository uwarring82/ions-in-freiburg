---
description: Claim Analysis Ledger
---

# Apendix: Breakwater Layer — A Meta-Algorithm

{% hint style="info" %}
**Stewardship:** Ulrich Warring\
**Endorsement:** Local candidate framework (no parity implied with externally validated laws). \
**Version:** 1.0-rc \
**Status:** Release candidate. Schema cleared by Council-3 adversarial review and refined through two rounds of external peer commentary. Core architecture frozen; companion materials under development.
{% endhint %}

***

### Position in the Harbour

The Open-Science Harbour separates three architectural layers:

| Layer                            | Function                                    | Tone                 |
| -------------------------------- | ------------------------------------------- | -------------------- |
| **Harbour** (Coastlines)         | Stable frameworks that survive disagreement | Silent, formal       |
| **Sails & Repair Kits** (Essays) | Interpretation, context, exploration        | Careful              |
| **Breakwater** (Ledger)          | Claim stress-testing                        | Forensic, impersonal |

The Breakwater Layer sits adjacent to but outside the Harbour core. It absorbs incoming waves — contested, ambiguous, or untested scientific claims — through a fixed measurement protocol. It does not redirect ships.

**Behavioural invariant:** The Ledger's outputs are purely descriptive and are not permitted to embed or reference action-guidance. Governance systems elsewhere may restrict uses of Ledger outputs; the Ledger itself never specifies such uses.

The Ledger produces data points. It never produces the curve.

**Self-reference exclusion:** Claims about the Ledger's own function, bias, or institutional effects are analysed in the Sails layer or Harbour governance documents, never in the Breakwater. The Ledger does not process claims about itself.

***

### What the Ledger Does

The Claim Analysis Ledger receives scientific claims and subjects them to a derivation chain:

```
Claim → Predictions → Constraints → Comparison → Classification
```

Each entry terminates in exactly one of three values:

| Classification      | Meaning                                                                                                                                                                                             |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **COMPATIBLE**      | Predictions align with established constraints under the stated decision rule. This does not mean "confirmed with high probability" — only "not in conflict given present constraint set and rule." |
| **UNDERDETERMINED** | Available evidence neither confirms nor contradicts. A discriminant condition is specified.                                                                                                         |
| **INCONSISTENT**    | Predictions conflict with established constraints under the stated decision rule.                                                                                                                   |

No commentary, recommendation, or implication follows the classification. The entry ends.

***

### What the Ledger Does Not Do

* It does not rank claims, authors, or theories.
* It does not publish summary statistics across entries.
* It does not route claims into or out of the Harbour.
* It does not adjudicate between rival frameworks.
* It does not attribute intent or assess competence.
* It does not label any classification as "strongly supported." Degrees of confidence belong in Sails.

If any of these functions are observed in a Ledger entry, the entry is structurally non-compliant.

***

### Safeguards

Four meta-level protections prevent the Ledger from drifting into a judgement system:

**1. Selection transparency.** Each entry declares its intake mode. In REQUEST mode, the Ledger analyses only claims brought to it externally; it never self-selects targets. In SWEEP mode, all claims within a predefined corpus and time window are analysed. No mixed mode is permitted within a single deployment.

**2. Resolution paths.** Every UNDERDETERMINED classification must specify a Discriminant Condition: the observable, the conditions, and the decision boundary that would resolve the ambiguity. Each Discriminant Condition carries a feasibility flag:

| Flag                | Meaning                                                                                               |
| ------------------- | ----------------------------------------------------------------------------------------------------- |
| FEASIBLE-NOW        | The required observation can be conducted with existing methods and infrastructure.                   |
| FEASIBLE-WITHIN-10Y | The observation requires foreseeable but not yet available methods or resources.                      |
| SPECULATIVE         | The observation depends on capabilities that do not currently exist and cannot be reliably projected. |

This prevents the specification of resolution paths that are conceptually neat but practically unachievable.

**3. Cross-entry consistency.** Each entry declares its constraint selection rule (MINIMAL, CANONICAL, or HIERARCHICAL) and its domain. Domain is declared per entry as the narrowest field classification under which the claim's predictions and constraints are jointly legible (e.g., "consciousness detection," not "neuroscience"). For entries sharing the same domain, the constraint set must follow the declared rule. Asymmetric treatment across comparable claims is a structural violation.

**4. Anti-aggregation posture.** The Ledger does not compute or publish corpus-level statistics from its own classifications. Individual entries are measurement results. Aggregate patterns across entries are emergent and not endorsed as institutional positions. There are no dashboards, no trend reports, no field-health summaries. If any aggregation is generated by third parties reading this repository, it is not produced, governed, or endorsed by this framework.

Self-audit of entry distributions, when conducted, is an irregular Supervisor governance action logged in the Harbour's operations archive. It is not a standing analytical layer with its own outputs. Self-audit findings may recommend schema changes for future entries or adjustments to constraint libraries under Harbour governance; they may not retroactively alter existing classifications.

***

### Schema (v1.0-rc)

```markdown
# LEDGER ENTRY: [ENTRY_ID]
**Metadata**
- **Intake Mode:** [REQUEST | SWEEP]
- **Constraint Rule:** [MINIMAL | CANONICAL | HIERARCHICAL]
- **Domain:** [Narrowest field classification under which predictions and constraints are jointly legible]
- **Scope:** [Optional: system class, context, time window]
- **Endorsement:** Local candidate framework (no parity implied with externally validated laws).
- **Waiver:** [Optional: WAIVER: Wx.x — Justification]
- **Timestamp:** [ISO 8601]

---

### A. Claim Extraction
**Operational Form:** [Variables and relations only. Max 25 words.]

Operationalisation fidelity: state whether the operational form is
EQUIVALENT to the source claim or a LOAD-BEARING SUBSET.

### B. Observable Consequences
1. [Prediction P1]
2. [Prediction P2]

Predictions may be deterministic ("marker sets agree across all test cases")
or probabilistic ("distribution of O lies in region R with probability ≥ p").
Directionality must be explicit: state whether the prediction runs
from property to classification, classification to property, or both.

### C. Established Constraints
1. [Type: THEORETICAL | EMPIRICAL | METHODOLOGICAL] [Constraint C1]
2. [Type: THEORETICAL | EMPIRICAL | METHODOLOGICAL] [Constraint C2]
*Ref:* [Bibliographic key only]

Type tags describe provenance, not quality. THEORETICAL denotes a
framework commitment. EMPIRICAL denotes an observational result.
METHODOLOGICAL denotes a procedural or statistical standard.
No credibility or controversiality ratings are permitted.

### D. Comparison Procedure
**Rule:** [Decision rule (formal, empirical, or hybrid).]

The decision rule may take any well-defined form: logic gate,
mathematical inequality, Bayesian model comparison, Neyman–Pearson
test, dominance relation, or qualitative evidence audit.
The rule must be stated before results are examined.

### E. Result
**Execution:** [Step-by-step application of Rule D to B and C.]

### F. Classification
**[COMPATIBLE | UNDERDETERMINED | INCONSISTENT]**

> [IF UNDERDETERMINED]
> **Discriminant Condition:** [Observable O under Condition C required for resolution.]
> **Feasibility:** [FEASIBLE-NOW | FEASIBLE-WITHIN-10Y | SPECULATIVE]

---

### G. Bibliography
* [Full citations isolated from reasoning.]
```

#### Schema notes

**Parallel entries.** When constraints are contested, an analyst may produce parallel entries for the same claim under different constraint sets (e.g., CL-2026-001-A under CANONICAL, CL-2026-001-B under ALT-CONSTRAINTS). Each entry is independent and self-contained. Cross-references between parallel entries are permitted in metadata only, not in analytical sections.

**Conjunctive claims.** When a source claim is a conjunction ("X causes Y via mechanism M under conditions Z"), the analyst may decompose it into sub-claims with separate B–F blocks sharing a common entry ID (e.g., CL-2026-002.1, CL-2026-002.2). Each sub-claim must be independently classifiable.

***

### Companion layers (not part of the Ledger)

The following resources support the Ledger but live in the Sails or Handbook layers. They are not governed by the Ledger's syntactic constraints.

**Sensitivity analyses** explore how classifications shift when constraints are modified ("if C2 is dropped, classification moves from INCONSISTENT to UNDERDETERMINED"). These belong in Sails-layer essays accompanying individual entries.

**Rule templates** provide a menu of pre-validated decision rule formats (Bayesian model comparison, Neyman–Pearson, dominance tests, qualitative evidence audit) that analysts may reference in section D. These belong in a Handbook appendix and will be developed as entry volume increases.

**Boundary guidance** on distinguishing UNDERDETERMINED from INCONSISTENT — a domain-agnostic memo addressing the subtle cases where theoretical divergence does not entail empirical incompatibility — belongs in the Sails layer.

***

### Showcase: CL-2026-001

The following entry was the first claim processed through the Ledger. It was used to validate the schema against a real scientific claim and to identify structural refinements.

***

## LEDGER ENTRY: CL-2026-001

**Metadata**

* **Intake Mode:** REQUEST
* **Constraint Rule:** MINIMAL
* **Domain:** Consciousness detection
* **Scope:** Non-communicating systems (general; not restricted to specific organism class or substrate)
* **Endorsement:** Local candidate framework (no parity implied with externally validated laws).
* **Timestamp:** 2026-02-19T00:00:00Z

***

#### A. Claim Extraction

**Operational Form:** Current consciousness theories (GWT, IIT) yield convergent operational criteria sufficient to detect consciousness in non-communicating systems.

_Operationalisation fidelity: LOAD-BEARING SUBSET. The source material frames a broader argument about urgency and ethical stakes; this entry isolates the empirical convergence claim only._

#### B. Observable Consequences

1. GWT-derived markers and IIT-derived markers identify overlapping sets of systems as conscious across all test cases. _(Deterministic; bidirectional: requires overlap regardless of which theory defines the base set.)_
2. Theory-derived detection criteria produce consistent classifications across independent laboratories using pre-registered protocols. _(Deterministic; unidirectional: from protocol to classification.)_

#### C. Established Constraints

1. \[THEORETICAL] GWT and IIT rest on divergent ontological commitments (functionalist broadcast vs intrinsicist integration), generating formally distinct detection criteria.
2. \[EMPIRICAL] Templeton Foundation adversarial collaborations (2019–2023) produced no convergent falsification boundary across competing theories.

_Ref:_ Melloni et al. 2021; Cogitate Consortium 2023

#### D. Comparison Procedure

**Rule:** P1 requires GWT-marker set ∩ IIT-marker set ≠ ∅ for all tested systems. C1 establishes formal distinctness of marker sets. Convergence holds only if empirical co-occurrence is demonstrated despite definitional divergence. C2 reports the outcome of the principal empirical attempt. _(Hybrid: formal set-intersection criterion evaluated against empirical programme outcomes.)_

#### E. Result

**Execution:** C1 confirms the two theories define detection through incompatible mechanisms (broadcast access vs integrated information). P1 therefore requires empirical demonstration that distinct markers co-occur, not theoretical derivation. C2 shows the primary multi-theory empirical programme did not achieve convergent falsification criteria. P2 lacks available multi-site replication data with pre-registered agreement thresholds.

#### F. Classification

**\[UNDERDETERMINED]**

> **Discriminant Condition:** A multi-site study applying both GWT-derived and IIT-derived markers to the same cohort of non-communicating subjects, with pre-registered inter-theory agreement criteria and a defined threshold for convergence/divergence. **Feasibility:** FEASIBLE-NOW

***

#### G. Bibliography

* Melloni, L., et al. (2021). An adversarial collaboration protocol for testing contrasting predictions of global neuronal workspace and integrated information theory. _PLOS ONE_, 16(2), e0268577.
* Cogitate Consortium (2023). Adversarial collaboration preliminary results. Preregistered at OSF.
* Cleeremans, A., Mudrik, L., Seth, A. (2025). Consciousness science: where are we, where are we going? _Frontiers in Science_, 3, 1546279.
* Baars, B.J. (1988). _A Cognitive Theory of Consciousness_. Cambridge University Press.
* Tononi, G. (2008). Consciousness as integrated information. _Biological Bulletin_, 215(3), 216–242.

***

### Design Notes

This section belongs to the Sails layer (interpretation) and is not part of the Ledger record.

**What the protocol resolved.** The source material (Cleeremans et al. 2025) frames its argument as a call for urgency in consciousness science. That framing is not testable. Forcing the argument into operational form extracted the load-bearing empirical claim — theoretical convergence on detection criteria — from the rhetorical wrapper. The protocol did exactly what it should: separated the measurable from the motivational.

**What the protocol surfaced.** The boundary between UNDERDETERMINED and INCONSISTENT required careful reasoning. The theories' ontological divergence does not logically entail that their detection criteria cannot converge empirically. Two frameworks may disagree on mechanism while agreeing on observables. The claim is therefore not inconsistent with constraints — it is unsupported by available evidence. The Discriminant Condition carries this nuance by specifying the exact study design that would resolve the classification.

**Sensitivity (Sails-layer observation).** If C2 were replaced by a future Cogitate result demonstrating clean marker divergence across a large cohort, classification would shift from UNDERDETERMINED to INCONSISTENT. Conversely, if marker overlap were demonstrated for a restricted system class (e.g., adult humans under anaesthesia), classification would shift to COMPATIBLE for that restricted scope, while remaining UNDERDETERMINED for the general claim. The Scope field in metadata makes such scope-restricted parallel entries directly comparable.

**UNDERDETERMINED skew in young fields.** Predictions P1 and P2 are deliberately strong ("across all test cases," "consistent classifications"). In fields where strong convergence claims outrun available evidence, many entries will land in UNDERDETERMINED. This is not a design flaw — it is the Ledger accurately reflecting the epistemic state. The skew is the signal.

***

### Review History

The Ledger design was developed through Council-3 adversarial review (Guardian–Architect–Integrator) with Supervisor intervention.

| Version | Date       | Change                                                                                                                                                                                                                        |
| ------- | ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 0.3.0   | 2026-02-19 | Initial schema design                                                                                                                                                                                                         |
| 0.3.1   | 2026-02-19 | Hard EOF rule; syntactic linter ruleset drafted                                                                                                                                                                               |
| 0.3.2   | 2026-02-19 | Structural separation of meta-commentary                                                                                                                                                                                      |
| 0.3.3   | 2026-02-19 | Endorsement marker integrated; degradation field added then vetoed (routing semantics)                                                                                                                                        |
| 0.3.4   | 2026-02-19 | Degradation field removed; schema cleared. Linter deferred to scaling phase. First entry CL-2026-001                                                                                                                          |
| 0.3.5   | 2026-02-19 | Section D broadened. Feasibility flag. Constraint type-tags. Probabilistic predictions. Self-reference exclusion. Behavioural invariant refined. Parallel entry and conjunctive claim guidance. Companion layer documentation |
| 1.0-rc  | 2026-02-19 | Domain definition added. Scope field added. Self-audit non-retroactivity clause. Core architecture frozen                                                                                                                     |

#### Items accepted from peer review

| Suggestion                                    | Verdict  | Placement                                                      |
| --------------------------------------------- | -------- | -------------------------------------------------------------- |
| Refined behavioural invariant wording         | Accepted | Preamble                                                       |
| Feasibility flag on Discriminant Conditions   | Accepted | Schema section F                                               |
| Self-reference exclusion                      | Accepted | Preamble                                                       |
| Constraint type-tagging (descriptive only)    | Accepted | Schema section C                                               |
| Probabilistic prediction language             | Accepted | Schema section B guidance                                      |
| Broadened section D descriptor                | Accepted | Schema section D                                               |
| Parallel entries for contested constraints    | Accepted | Schema notes                                                   |
| Conjunctive claim decomposition               | Accepted | Schema notes                                                   |
| Operationalisation fidelity flag              | Accepted | Schema section A                                               |
| Domain definition for cross-entry consistency | Accepted | Safeguard §3 and metadata                                      |
| Scope field                                   | Accepted | Metadata (optional)                                            |
| Self-audit non-retroactivity clause           | Accepted | Safeguard §4                                                   |
| Sensitivity analysis                          | Accepted | Sails layer only                                               |
| Rule templates                                | Accepted | Handbook appendix, scaling phase                               |
| Boundary guidance memo                        | Accepted | Sails layer, future                                            |
| Machine-readability hooks                     | Deferred | Text already supports future structured extraction             |
| Self-audit meta-layer                         | Resisted | Irregular Supervisor action; standing layer risks aggregation  |
| Controversiality tags on constraints          | Resisted | Imports social evaluation; parallel entries solve this problem |
