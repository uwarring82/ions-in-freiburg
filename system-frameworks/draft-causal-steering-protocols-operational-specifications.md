# \[DRAFT] Causal Steering Protocols — Operational Specifications

{% hint style="info" %}
**Author:** U. Warring\
**Affiliation:** Institute of Physics, University of Freiburg\
**Version:** 0.0.1\
**Last updated:** 2025-12-15\
**License:** CC BY 4.0\
\
**Disclaimer** — _This document reflects an ongoing effort to clarify how to engineer causal system steering. Its authority derives from transparency, not finality._
{% endhint %}

***

### Scope Statement

This document specifies **operational protocols** for implementing the Causal Clock Unification Framework (CCUF). It is a companion to CCUF, not a replacement.

**Dependency direction:** CSP depends on CCUF; CCUF does not depend on CSP. The framework document (CCUF) is intended to remain stable across CSP revisions.

**Scope boundary:** CSP addresses _how_ to implement causal clock steering; CCUF addresses _what_ constraints govern phase comparison. If CSP development reveals conceptual gaps in CCUF, those gaps are addressed through explicit CCUF amendments with version increments, not through CSP content.

***

### Placeholder Sections

The following sections are reserved for future development. Content is not yet specified.

#### 1. Candor Weighting Update Laws

**Status:** Reserved

**Planned content:**

* Candidate update formulas (e.g., exponential downweighting)
* Statistical thresholds for "unexplained deviation"
* Convergence properties and stability analysis
* Reference to BIPM and NMI steering algorithms

**Principle (from CCUF §6.3):** Clocks with statistically significant unexplained deviations are downweighted relative to demonstrated consistency.

***

#### 2. Architecture-Specific η\_opt Ranges

**Status:** Reserved

**Planned content:**

* Optical clock networks: expected η\_opt range and noise-transition signatures
* VLBI baselines: expected η\_opt range and tropospheric-noise coupling
* PTA regimes: geometry-insensitivity criteria
* Tabulated results from experimental campaigns (when available)

**Note:** Numeric η\_opt values are implementation-dependent and architecture-specific. CCUF §8.1 specifies the measurement protocol; this section will record observed values.

***

#### 3. Autonomy Levels (L1–L3)

**Status:** Reserved

**Planned content:**

* L1: Manual steering with human oversight at each comparison epoch
* L2: Semi-autonomous steering with human-defined policy constraints
* L3: Fully autonomous steering with candor-weighted self-correction
* Transition criteria between levels
* Failure-mode handling and fallback protocols

***

#### 4. Protocol Templates

**Status:** Reserved

**Planned content:**

* Comparison campaign checklists
* Data-logging requirements
* Uncertainty propagation procedures
* Interoperability with TAI/UTC steering infrastructure

***

### References

* CCUF v0.1.5: [Causal Clock Unification Framework](https://claude.ai/chat/CCUF-v1.0-RC.md)
* BIPM Circular T documentation
* IERS Conventions (2010), Technical Note 36

***

### Version History

| Version | Date       | Summary                                                                                         |
| ------- | ---------- | ----------------------------------------------------------------------------------------------- |
| v0.1    | 2025-12-14 | Initial stub. Scope statement and placeholder sections established. No operational content yet. |

***

_This document is authorized as a CCUF companion. It does not modify CCUF definitions or boundary conditions._
