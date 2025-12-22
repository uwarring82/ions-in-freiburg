---
description: A Proposed Framework for Optical Time & Frequency Comparison
---

# Correlation Access and Causal Efficiency

> **Status:** Proposed framework (Stage 1) — validation pending\
> **Scope:** Comparison geometry and access constraints only\
> **Exclusions:** Oscillator physics; relativistic modelling (IAU/IERS); quantum gravity\
> **Feedback:** Testing and critique welcome

***

### 0. Reader Contract (Protective Framing)

* This document **proposes** an architectural lens.
* It does **not** claim field consensus.
* Cited literature provides **empirical foundations**, not proof of the constructs introduced here.
* Validation of proposed constraints and predictions remains open.

***

### 1. Motivation and Context

* Optical clocks now outperform many comparison channels.
* Stability gains increasingly **saturate without diagnostic clarity**.
* This framework introduces an **access-geometry lens** to diagnose such plateaus.

**Context anchors:**\
Allan (1966); Rutman (1978); Lisdat et al. (2016); Zhang et al. (2022)

***

### 2. Core Quantities (Orthogonal by Design)

#### 2.1 Correlation length ξ — _Physical availability_

* **Definition:** Spacetime extent over which fluctuations remain correlated.
* **Properties:**
  * Set by environment, medium, turbulence, noise processes
  * Independent of interrogation or protocol
* **Examples:** fibre acoustic/thermal noise; atmospheric turbulence; ionospheric phase correlations

**Anchors:**\
Allan (1966); Rutman (1978); Coddington et al. (2008)

***

#### 2.2 Causal efficiency η(τ) — _Architectural utilisation_

\[ \eta(\tau)=\frac{L\_{\mathrm{comparison\}}(\tau)}{c,\tau} ]

* **Definitions:**
  * (L\_{\mathrm{comparison\}}(\tau)): maximum spatial extent that must act coherently to produce one comparison sample
* **Properties:**
  * Dimensionless **operational control parameter**
  * Not a thermodynamic efficiency
* **Regimes:**
  * η ≪ 1: under-utilised causal envelope
  * η ≈ 1: causal limit for single round-trip
  * η > 1: delayed or multi-cycle closure

**Anchors:**\
Ma et al. (1994); Calonico et al. (2014); IEEE 1139-2008

***

### 3. Proposed Interface Condition (C1)

#### 3.1 Constraint C1 — _Proposed access condition_

\[ \xi ;\lesssim; L\_{\mathrm{comparison\}}(\tau) ]

* **Epistemic status:** Framework prediction (testable; not yet validated across architectures)
* **Meaning:** Correlations not jointly accessible within one comparison cycle cannot contribute coherently.
* **Non-claims:** Not a new physical law; not a causality bound.

**Context anchors (not proofs):**\
Lisdat et al. (2016); Riehle et al. (2015); Zhang et al. (2022)

***

### 4. Architectural Intuition (Non-prescriptive)

#### 4.1 Phase-stabilised fibre links

* Two-way / round-trip causal closure
* Active suppression **extends the accessible correlation length**
* Enables high-η operation without violating C1

**Anchors:**\
Ma et al. (1994); Calonico et al. (2014); Lisdat et al. (2016)

***

#### 4.2 Free-space optical transfer

* Physical correlation length limited by turbulence and reciprocity
* η-optimisation alone eventually saturates performance
* **Framework prediction:** C1 may fail in this regime (validation required)

**Anchors:**\
Coddington et al. (2008); Zhang et al. (2022)

***

### 4.5 Worked Example (Minimal, Numerical)

#### Case study: GPS carrier-phase comparison _(illustrative)_

* **Approximate parameters (order-of-magnitude estimates):**
  * ξ\_iono ≈ 300 km (ionospheric correlation scale; typical mid-latitude conditions)
  * L\_comparison ≈ 20 000 km (global GNSS network baseline)
* **Regime:**
  * C1 satisfied (ξ ≪ L\_comparison)
  * η ≪ 1 due to global geometry and timing latency
* **Prediction:** Synchronisation improvements should yield gains; environmental mitigation is secondary.

**Anchors:**\
Allan (1966); Rutman (1978); IEEE 1139-2008

***

### 5. Falsifiable Prediction

#### S1 — Saturation Test

* **Statement:** At fixed physical conditions, reducing η(τ) ceases to improve measured instability once C1 fails.
* **Observable:** Plateau in σ\_y(τ) versus protocol timing.
* **Status:** Architecture-specific; data-driven validation required.

**Anchors:**\
Allan (1966); NIST SP 1065 (2008; 2014 update)

***

#### 5.1 Validation Pathway to Handbook Status (Stage 2)

**Minimum evidence required:**

* C1 tested in ≥2 distinct architectures (e.g. fibre and free-space)
* η(τ) calculation method specified and reproduced independently
* S1 saturation behaviour documented with published datasets
* ≥1 η\_opt prediction confirmed or falsified

**Current status:** None of these criteria yet met.

***

### 6. Conditional Design Guidance (Guarded)

> **Applies only where C1 and S1 are testable**

* If performance saturates under η-optimisation → investigate physical limits on ξ
* If ξ is abundant → optimise synchronisation, geometry, and closure latency

_No universal optimisation strategy is implied._

***

### 7. Scope and Aspirational Outlook

* **If validated**, this framework could re-centre comparison science on interrogation geometry.
* **Present status:** Proposal awaiting multi-architecture testing.

***

### 8. Note on References (Protective)

The references below establish the empirical foundations of time-frequency metrology and optical transfer.\
The ξ/η separation, C1, and S1 are **novel architectural constructs** introduced here to unify and interrogate these results.

***

### 9. References (Alphabetical; year-verified)

* Allan, D. W. (1966). _Proc. IEEE_ **54**, 221–230.
* Barnes, J. A. et al. (1971). _IEEE TIM_ **IM-20**, 105–120.
* Calonico, D. et al. (2014). _Appl. Phys. B_ **117**, 979–986.
* Coddington, I., Swann, W. C., & Newbury, N. R. (2008). _Phys. Rev. Lett._ **100**, 013902.
* Lisdat, C. et al. (2016). _Nat. Commun._ **7**, 12443.
* Ma, L.-S., Ye, J., & Hall, J. L. (1994). _Opt. Lett._ **19**, 1777–1779.
* Newbury, N. R. (2011). _Nat. Photonics_ **5**, 186–188.
* Riehle, F. et al. (2015). _C. R. Physique_ **16**, 506–515.
* Rutman, J. (1978). _Proc. IEEE_ **66**, 1048–1075.
* Zhang, H. et al. (2022). _Nature_ **607**, 687–692.
* IEEE 1139-2008. _Definitions of Frequency and Time Metrology._
* NIST SP 1065. _Handbook of Frequency Stability Analysis_ (2008; 2014 update).

***
