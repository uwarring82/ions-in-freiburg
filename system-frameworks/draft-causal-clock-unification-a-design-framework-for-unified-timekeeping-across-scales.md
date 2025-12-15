---
description: Timekeeping as Causal Geometry
---

# \[DRAFT] Causal Clock Unification — A Design Framework for Unified Timekeeping Across Scales

***

{% hint style="info" %}
**Author:** U. Warring\
**Affiliation:** Institute of Physics, University of Freiburg\
**Version:** 0.5.0\
**Last updated:** 2025-12-15\
**License:** CC BY 4.0\
\
**Disclaimer** — _This document clarifies how causality constrains timekeeping architectures. Its authority derives from transparency, not finality. The framework is designed to guide near-term infrastructure decisions under existing technical constraints, while remaining compatible with future advances._
{% endhint %}

***

### 0. Orientation

Modern timekeeping operates across integration times spanning more than fifteen orders of magnitude—from sub-nanosecond optical interrogation cycles to decade-scale pulsar timing baselines. No single oscillator covers this range. Clocks that agree at one timescale may diverge at another, not because they fail, but because their comparison geometries impose different causal constraints.

This framework introduces a single architectural lens: the causal boundary condition governing phase comparison. It does not replace existing metrology tools, redefine time standards, or propose new physics. It offers a design language for reasoning about why different clock architectures exhibit different stability regimes—and how they might be coupled coherently.

**How to read this document.** Table 1 provides quantitative orientation across clock architectures. Each subsequent section states its structural contribution explicitly. Hypotheses are labeled; predictions are testable and non-circular. Open questions are marked as such.

***

#### Table 1 — Clock Architectures: Parameter Overview

| Architecture                  | L\_comparison | τ\_min = L/c | Typical τ | η Range     | Dominant Noise Source   | Current σ\_y(τ) |
| ----------------------------- | ------------- | ------------ | --------- | ----------- | ----------------------- | --------------- |
| Optical lattice (local)       | \~1 m         | \~3 ns       | 1–10⁴ s   | 10⁻¹²–10⁻⁸  | Quantum projection      | \~10⁻¹⁸ @ 10⁴ s |
| Optical ion (local)           | \~1 mm        | \~3 ps       | 1–10⁴ s   | 10⁻¹⁵–10⁻¹¹ | Quantum projection      | \~10⁻¹⁸ @ 10⁴ s |
| Optical network (continental) | 10²–10³ km    | 0.3–3 ms     | 10³–10⁵ s | 10⁻²–10⁻¹   | Fiber phase noise       | \~10⁻¹⁸ @ 10⁴ s |
| Microwave fountain            | \~10⁴ km      | \~30 ms      | 10⁴–10⁶ s | 10⁻³–10⁻²   | Dick effect, cavity     | \~10⁻¹⁶ @ 10⁵ s |
| Hydrogen maser                | \~10⁴ km      | \~30 ms      | 10²–10⁵ s | 10⁻³–10⁻¹   | Cavity drift            | \~10⁻¹⁵ @ 10⁴ s |
| GNSS (GPS/Galileo)            | \~2×10⁴ km    | \~70 ms      | 1–10⁴ s   | 10⁻²–10⁰    | Ionosphere, multipath   | \~10⁻¹⁴ @ 10³ s |
| TWSTFT                        | \~10⁴ km      | \~30 ms      | 10²–10⁵ s | 10⁻³–10⁻¹   | Troposphere, delay cal. | \~10⁻¹⁵ @ 10⁴ s |
| VLBI                          | 6×10³–10⁴ km  | 20–30 ms     | 10³–10⁵ s | 10⁻²–10⁻¹   | Troposphere, clocks     | \~10⁻¹⁵ @ 10⁴ s |
| Pulsar timing (single)        | \~10¹⁹ m      | \~10¹¹ s     | 10⁷–10⁹ s | ≪10⁻²       | Timing noise, ISM       | \~10⁻¹⁵ @ 10⁸ s |
| PTA (array correlation)       | \~10¹⁶ m      | \~10⁸ s      | 10⁸–10⁹ s | \~0.3       | Pulsar red noise        | \~10⁻¹⁵ @ 10⁸ s |

**Notes:**

* L\_comparison = baseline over which phase agreement is sought
* τ\_min = minimum integration time for causal closure (one-way)
* η = L\_comparison/(cτ), the causal efficiency parameter
* σ\_y(τ) = modified Allan deviation at specified τ; values are representative best-case
* ISM = interstellar medium scattering/dispersion

***

#### Scope

This framework explicitly excludes:

* **Quantum gravity and Planck-scale physics.** The dimensional limit ℓ\_P = √(ℏG/c³) appears only as a dimensional endpoint, not as a physical regime addressed here.
* **Microscopic atomic transition theory.** Oscillator physics (atomic structure, transition rates, systematic shifts) is assumed, not derived.
* **Sociopolitical governance of civil time.** Decisions by ITU, BIPM, or national agencies regarding leap seconds, UTC definitions, or civil timekeeping policy lie outside this framework.

***

### 1. The Regime Shift: Why This Framework Is Needed Now

Optical clocks now routinely achieve fractional frequency uncertainties below 10⁻¹⁸, surpassing the best microwave standards by more than two orders of magnitude. This advance creates an operational discontinuity: the comparison infrastructure—not the oscillators—limits achievable agreement.

Three developments define this regime shift:

**Optical clock maturity.** Multiple independent laboratories have demonstrated reproducibility at the 10⁻¹⁸ level using distinct atomic species (Sr, Yb, Al⁺, Ca⁺, Hg) and trapping geometries (lattice, single-ion).

**Continental-scale optical links.** Stabilized fiber networks now enable phase-coherent comparison over baselines exceeding 1000 km, with transfer instabilities below the clock noise floor for integration times beyond 10⁴ s. The European fiber network (PTB–SYRTE–NPL–INRIM) demonstrates this capability operationally.

**Multi-messenger timing coordination.** Gravitational-wave detection, pulsar timing arrays, and geodetic VLBI increasingly require common timing frameworks across instruments with incommensurable comparison geometries.

The existing metrology toolkit—Allan variance for noise characterization, TAI/UTC for civil timekeeping, IERS products for Earth-rotation monitoring—remains essential. But these tools describe what clocks do, not why different architectures exhibit different stability regimes. A design framework addressing comparison geometry has become necessary.

***

#### Table 2 — Current Optical Clock Performance (Representative Systems)

| Species | Trap Type  | Institution | σ\_y @ 1 s | σ\_y @ 10⁴ s | Systematic Uncertainty | Reference        |
| ------- | ---------- | ----------- | ---------- | ------------ | ---------------------- | ---------------- |
| ⁸⁷Sr    | Lattice    | JILA        | 4×10⁻¹⁷/√τ | \~4×10⁻¹⁹    | 2×10⁻¹⁸                | Bothwell (2022)  |
| ⁸⁷Sr    | Lattice    | PTB         | 6×10⁻¹⁷/√τ | \~6×10⁻¹⁹    | 2×10⁻¹⁸                | Schwarz (2020)   |
| ¹⁷¹Yb   | Lattice    | NIST        | 3×10⁻¹⁷/√τ | \~3×10⁻¹⁹    | 1.4×10⁻¹⁸              | McGrew (2018)    |
| ¹⁷¹Yb⁺  | Single-ion | PTB         | 8×10⁻¹⁶/√τ | \~8×10⁻¹⁸    | 3×10⁻¹⁸                | Huntemann (2016) |
| ²⁷Al⁺   | Single-ion | NIST        | 2×10⁻¹⁵/√τ | \~2×10⁻¹⁷    | 9×10⁻¹⁹                | Brewer (2019)    |

**Note:** Performance continues to improve; these values represent state-of-the-art as of 2024. The comparison geometry framework applies regardless of which oscillator achieves lowest instability.

***

### 2. The Causal Boundary as a Design Constraint

Every comparison of two oscillators requires information exchange. The propagation time along the longest required signal path sets an irreducible lower bound on the timescale at which their phases can be correlated.

#### 2.1 The Realisability Horizon

**Definition 2.1 (Realisability Horizon).**\
For any phase comparison operation requiring causal information exchange over a longest required signal path L\_path, the integration time must satisfy:

\$$\tau \ge \frac{L\_{\text{path\}}}{c}\$$

For mutual verification (bidirectional / round-trip causal closure):

\$$\tau \ge \frac{2 L\_{\text{path\}}}{c}\$$

L\_path reduces to L\_comparison in direct two-node comparisons; for star/mesh topologies, L\_path is the maximum required path for the chosen protocol.

This inequality is a **boundary condition**, not a dynamical law. It does not describe how clocks evolve; it describes which comparisons are possible. Any architecture proposing agreement over baseline L in time τ < L/c violates causality. No oscillator improvement, no signal processing technique, and no statistical method can circumvent this bound.

#### 2.2 Three Orthogonal Length Scales

Clocks involve three distinct spatial scales that must not be conflated:

| Scale      | Symbol        | Definition                   | Examples                                                   |
| ---------- | ------------- | ---------------------------- | ---------------------------------------------------------- |
| Source     | L\_source     | Spatial extent of oscillator | Ion trap: \~1 mm; Lattice: \~1 cm; Pulsar: \~10 km         |
| Apparatus  | L\_apparatus  | Interrogation/control region | Vacuum chamber: \~1 m; Antenna: \~10 m; Telescope: \~100 m |
| Comparison | L\_comparison | Baseline for phase agreement | Lab: \~1 m; Continental: \~10³ km; Galactic: \~10¹⁹ m      |

Only L\_comparison enters the causal constraint. Advances in L\_source (better oscillators) or L\_apparatus (better interrogation) do not relax the realisability horizon.

This distinction clarifies why optical clocks with exquisite local stability may exhibit degraded performance when networked: their L\_source and L\_apparatus have improved, but L\_comparison introduces constraints absent in local operation.

***

### 3. Causal Efficiency as an Architectural Control Parameter

#### 3.1 Definition

For any clock architecture operating at integration time τ with comparison baseline L\_comparison, define the **causal efficiency**:

\$$\eta(\tau) = \frac{L\_{\text{comparison\}}}{c , \tau}\$$

This dimensionless ratio has the following properties:

| η Value      | Interpretation                                             | Regime     |
| ------------ | ---------------------------------------------------------- | ---------- |
| η = 1        | Causal limit: all integration time consumed by propagation | Boundary   |
| η \~ 0.1–0.5 | Moderate: propagation comparable to integration            | Transition |
| η ≪ 0.01     | Deep interior: propagation negligible                      | Asymptotic |

Causal efficiency is not an optimization target by default. Different architectures may exhibit optimal noise performance at different values of η, determined by their dominant noise sources and comparison geometries.

#### 3.2 The η\_opt Hypothesis

**Hypothesis 3.1 (Optimal Causal Efficiency).**\
Each clock architecture exhibits a noise-regime transition at some characteristic efficiency η\_opt, determined by comparison geometry and dominant noise sources.

This hypothesis is testable: for a given architecture, measure stability as a function of integration time while holding L\_comparison fixed. If a transition in noise scaling correlates with a characteristic value of η, the hypothesis is supported. If no such correlation exists, the hypothesis is falsified.

The experimental protocol is specified in §10.1.

***

#### Table 3 — Causal Efficiency by Architecture

| Architecture              | L\_comparison | τ (typical) | η = L/(cτ) | Regime          |
| ------------------------- | ------------- | ----------- | ---------- | --------------- |
| Optical lattice (local)   | 1 m           | 10⁴ s       | 3×10⁻¹³    | Deep interior   |
| Optical network (1000 km) | 10⁶ m         | 10⁴ s       | 0.033      | Transition zone |
| VLBI baseline (6000 km)   | 6×10⁶ m       | 10⁴ s       | 0.20       | Moderate        |
| GNSS (orbital)            | 2×10⁷ m       | 10³ s       | 0.07       | Transition zone |
| PTA (Earth-pulsar)        | 10¹⁹ m        | 10⁸ s       | 0.3        | Moderate        |
| PTA (inter-pulsar)        | 10¹⁶ m        | 10⁸ s       | 3×10⁻⁴     | Deep interior   |

**Note:** The "transition zone" (η \~ 0.01–0.5) is where comparison geometry may dominate noise budgets. This is where the η\_opt hypothesis makes its strongest predictions.

***

### 4. Clocks as Architectures, Not Devices

A clock, in this framework, is not an atomic transition or a cavity mode. It is a complete architecture comprising:

1. **Oscillator** — the frequency source
2. **Interrogation apparatus** — the local control system
3. **Comparison baseline** — the infrastructure for phase agreement

This architectural view has consequences:

**No universal clock metric.** Two clocks cannot be ranked by a single figure of merit without specifying the comparison baseline and integration time. An optical lattice clock may outperform a hydrogen maser at τ = 10⁴ s over a 100 km baseline, but underperform at τ = 10⁷ s over a 6000 km baseline.

**Comparison is constitutive.** A clock achieves its stated performance only relative to a specified comparison architecture. Stability numbers quoted without comparison context are incomplete.

**Modularity.** Oscillators, apparatus, and comparison links can be designed, characterized, and upgraded independently. Improving one component improves the architecture only if the other components do not become limiting.

***

### 5. Agreement Requires Causal Closure

#### 5.1 Causal Closure Condition

Two oscillators at separation L achieve causal closure at integration time τ if and only if:

\$$2L \le c , \tau\$$

where L is the relevant one-way path length. This is the bidirectional special case of Definition 2.1.

Without causal closure, clocks may be individually stable but cannot verify mutual agreement. They run independently, not in concert.

#### 5.2 Implications by Architecture

| Architecture     | L (one-way) | τ for closure | Implication                   |
| ---------------- | ----------- | ------------- | ----------------------------- |
| Lab comparison   | 10 m        | 67 ns         | Instantaneous on human scales |
| City network     | 10 km       | 67 μs         | Sub-ms closure feasible       |
| Continental link | 1000 km     | 6.7 ms        | Limits short-τ comparison     |
| Intercontinental | 10,000 km   | 67 ms         | \~100 ms minimum epoch        |
| Earth-Moon       | 4×10⁸ m     | 2.7 s         | Multi-second epochs required  |
| Earth-pulsar     | 10¹⁹ m      | 10¹¹ s        | Decades for round-trip        |

For optical clock networks, a network spanning continental distances (L \~ 1000 km) achieves causal closure only for τ ≳ 7 ms. At shorter integration times, clocks at network edges cannot verify agreement with clocks at the center.

For pulsar timing arrays, the multi-year integration times used in gravitational-wave searches are not a choice but a consequence of the causal constraint.

***

### 6. Strongly-Coupled Clockwork (Operational Synthesis)

Modern precision timekeeping already operates as a coupled system, though this coupling is rarely made explicit. The framework identifies five principal gear-trains that must interoperate.

#### Table 4 — Five-Gear Clockwork: Architecture Coupling

| Gear | Systems             | L\_comparison | τ Domain  | Role                 | Couples To          |
| ---- | ------------------- | ------------- | --------- | -------------------- | ------------------- |
| 1    | Optical clocks      | ≲10³ km       | 10³–10⁵ s | Highest stability    | Gear 2 (steering)   |
| 2    | Microwave fountains | ≲10⁴ km       | 10⁴–10⁶ s | SI realization, TAI  | Gear 1, 3           |
| 3    | GNSS                | \~2×10⁴ km    | 1–10⁴ s   | Global distribution  | Gear 2, 4           |
| 4    | VLBI                | \~10⁴ km      | 10³–10⁵ s | Earth orientation    | Gear 3, 5           |
| 5    | Pulsar timing       | 10¹⁶–10¹⁹ m   | 10⁷–10⁹ s | Ultra-long stability | Gear 4, 1 (decadal) |

**Coupling principle:** Each gear-train contributes stability in its native regime and accepts constraints from adjacent regimes. The coupling is bidirectional: optical clocks inform fountain steering; pulsars provide decade-scale stability checks on optical standards.

#### 6.1 TA-OPT (Design Target)

**TA-OPT** — a timescale realized exclusively from optical clocks, with reliability-weighted steering and without intermediate microwave fly-wheels, serving as the high-stability reference against which Earth-rotation deviations are tracked.

TA-OPT is not a successor to TAI, not a new primary standard, and carries no claim of institutional authority. It is a design target: a timescale whose stability derives entirely from optical standards, against which the variable Δ(t) = UT1 − TA-OPT can be monitored as a smooth, continuous function.

#### 6.2 Candor Weighting (Principle)

**Candor weighting (principle):** Clocks with statistically significant unexplained deviations are downweighted relative to demonstrated consistency. Specific update laws are implementation-dependent.

This principle assigns influence based on demonstrated consistency between predicted and observed performance—downweighting clocks that exhibit unexplained excursions regardless of their nominal stability specifications.

***

### 7. What This Framework Is — and Is Not

#### What This Framework Is

* A **design language** for reasoning about clock architectures in terms of comparison geometry
* A **boundary condition** (L\_comparison ≤ cτ) that constrains all phase-comparison operations
* An **architectural control parameter** (η) characterizing proximity to the causal limit
* A **synthesis** making explicit the coupling between existing timekeeping gear-trains
* **Action-guiding** for near-term infrastructure decisions

#### What This Framework Is Not

| Exclusion                                     | Clarification                                                   |
| --------------------------------------------- | --------------------------------------------------------------- |
| Not a new physical theory                     | No equations of motion proposed; causality assumed, not derived |
| Not a replacement for Allan variance          | Noise characterization remains essential                        |
| Not a redefinition of TAI/UTC/SI              | Existing standards retain definitions and authority             |
| Not a policy proposal                         | Governance decisions lie outside scope                          |
| Not a claim of optimality                     | η\_opt is a hypothesis to be tested, not a prescription         |
| Not a complete implementation specification   | Algorithms, hardware, software lie in companion documents       |
| Not a substitute for relativistic corrections | IERS conventions assumed, not replaced                          |
| Not a legal traceability standard             | UTC/TAI/SI remain legal standards                               |

***

### 8. Open Design Questions and Near-Term Frontiers

The value of this framework lies not in closing design questions, but in making them explicit, comparable, and discussable across institutions. The following questions are deliberately left open.

#### 8.1 Architecture: Topology and Layering (Explicitly Open)

**The framework does not prescribe a single network topology** (all-to-all, hub-and-spoke, federated meshes). Different layers (local, regional, continental, planetary) may legitimately use different architectures.

The framework specifies boundary conditions for verification, not a canonical network architecture. The optimal topology depends on scale, geography, application, and institutional context—and is an active design question rather than a settled choice.

| Scale                 | Candidate Topologies    | Open Questions                                 |
| --------------------- | ----------------------- | ---------------------------------------------- |
| Local (lab)           | Point-to-point          | Which comparison protocol minimizes dead time? |
| Regional (100 km)     | Star, ring              | How does topology affect η\_opt?               |
| Continental (1000 km) | Mesh, redundant paths   | Failure-mode resilience vs. complexity         |
| Intercontinental      | Hybrid satellite+fiber  | Cost-performance tradeoffs                     |
| Planetary             | Hierarchical federation | Governance and protocol interoperability       |

#### 8.2 Steering, Weighting, and Authority (Explicitly Deferred)

**The framework does not prescribe how clocks should be steered, weighted, or combined into a timescale.** It is compatible with existing practices (ensemble averaging, post-processed steering, UTC/TAI).

The framework separates the question of _how clocks are compared_ from _how a timescale is steered_. Steering remains an institutional and governance decision, informed—but not dictated—by verification geometry.

| Steering Aspect     | Current Practice           | Framework Contribution             |
| ------------------- | -------------------------- | ---------------------------------- |
| Weight assignment   | BIPM Circular T algorithms | Makes comparison geometry explicit |
| Outlier detection   | Statistical thresholds     | Candor weighting principle         |
| Authority hierarchy | NMI → BIPM → UTC           | No change proposed                 |
| Update cadence      | Monthly (TAI)              | Informs feasible cadence           |

#### 8.3 Compatibility with Future Quantum Enhancements (Future-Facing)

**The framework does not rely on entanglement or quantum-enhanced links.** It is fully applicable with classical optical links and existing technologies.

Nothing in the framework assumes quantum-entangled links. At the same time, its emphasis on causal comparison geometry is compatible with future entanglement-assisted protocols, which may extend verification capabilities but do not remove causal limits.

| Enhancement                 | Framework Compatibility | Note                                    |
| --------------------------- | ----------------------- | --------------------------------------- |
| Entangled photon pairs      | Compatible              | Does not relax τ ≥ L/c                  |
| Quantum repeaters           | Compatible              | Affects L\_apparatus, not L\_comparison |
| Distributed quantum sensing | Compatible              | May reduce σ\_y, not η constraint       |

***

### 9. Near-Term Impact

> **Near-term impact (next 3–5 years)**
>
> * Can be implemented using existing optical clocks, fibre links, satellite transfer, VLBI
> * Requires documentation and coordination, not new physics
> * Improves resilience and trust before performance ceilings are reached
> * Aligns with current funding and infrastructure cycles

#### Table 5 — Implementation Readiness by Component

| Component               | Current Status             | Readiness   | Required Action                       |
| ----------------------- | -------------------------- | ----------- | ------------------------------------- |
| Optical clocks          | Operational at NMIs        | Ready       | Coordinate comparison campaigns       |
| Fiber links             | Continental networks exist | Ready       | Document η at operating points        |
| Satellite transfer      | GPS, Galileo, TWSTFT       | Ready       | Characterize geometry-dependent noise |
| VLBI                    | Global network operational | Ready       | Cross-correlate with optical          |
| Pulsar timing           | IPTA ongoing               | Ready       | Establish optical-PTA cross-checks    |
| Framework documentation | This document              | In progress | Complete companion protocols          |

#### 9.1 Actors and Entry Points

| Actor                       | Entry Point            | Immediate Action                       |
| --------------------------- | ---------------------- | -------------------------------------- |
| NMIs (PTB, NIST, NPL, etc.) | Optical clock networks | Characterize η\_opt for existing links |
| BIPM                        | Timescale algorithms   | Evaluate candor weighting principles   |
| Space agencies (ESA, NASA)  | Satellite timing       | Document comparison geometry in specs  |
| Geodetic community          | VLBI/IERS              | Cross-validate with optical networks   |
| Pulsar timing consortia     | IPTA                   | Establish long-baseline cross-checks   |

***

### 10. Testable Predictions (Non-Circular)

#### 10.1 Prediction: η\_opt Location for Optical Clock Networks

**Setup:** Optical clock network with fixed baseline L\_comparison = 1000 km.

**Protocol:** Measure modified Allan deviation while scanning τ from 10² s to 10⁵ s, covering η ∈ \[0.01, 0.5].

**Prediction:** A transition in noise scaling will occur at some characteristic η\_opt within this range.

**Falsification criterion:** If no changepoint is observed over the pre-registered interval—if instability decreases monotonically without transition—the hypothesis is not supported for this architecture.

#### 10.2 Prediction: Architecture-Specific η\_opt

**Setup:** Compare optical network (1000 km baseline) with VLBI (6000 km baseline) at matched η values.

**Prediction:** Different η\_opt values will be observed, reflecting different dominant noise sources (fiber phase noise vs. tropospheric delay).

**Falsification criterion:** If identical η\_opt values are observed despite different noise environments, the architecture-specificity hypothesis is falsified.

#### 10.3 Prediction: PTA Geometry Insensitivity

**Setup:** Pulsar timing array with L\_comparison \~ 10¹⁶ m, τ \~ 10⁸ s.

**Prediction:** At η ≪ 0.01, stability is limited by intrinsic timing noise, not comparison geometry.

**Falsification criterion:** If PTA stability shows _systematic_ baseline dependence at fixed τ, the geometry-insensitivity prediction requires revision.

#### 10.4 Non-Circularity Safeguards

* η\_opt values are measured, not assumed
* Noise sources are characterized independently of the framework
* Search intervals are pre-registered to prevent post-hoc adjustment
* The framework predicts correlations; it does not define the observables

***

### References

1. D. W. Allan, _Statistics of atomic frequency standards_, Proc. IEEE **54**, 221–230 (1966).
2. W. M. Itano et al., _Quantum projection noise_, Phys. Rev. A **47**, 3554 (1993).
3. C. W. Chou et al., _Optical clocks and relativity_, Science **329**, 1630–1633 (2010).
4. G. Petit and B. Luzum (Eds.), _IERS Conventions (2010)_, IERS Technical Note 36.
5. F. Riehle, _Optical clock networks_, Nature Photonics **11**, 25–31 (2017).
6. S. M. Brewer et al., _²⁷Al⁺ quantum-logic clock_, Phys. Rev. Lett. **123**, 033201 (2019).
7. E. Bothwell et al., _JILA SrI optical lattice clock_, Metrologia **59**, 065009 (2022).
8. G. Hobbs et al., _IPTA second data release_, MNRAS **491**, 5951 (2020).
9. J. E. Sovers et al., _Radio interferometry astrometry and geodesy_, Rev. Mod. Phys. **70**, 1393 (1998).

***

### Document Metadata

| Field               | Value                                                    |
| ------------------- | -------------------------------------------------------- |
| Version             | 0.5                                                      |
| Status              | Design Framework — action-guiding, explicitly incomplete |
| Canonical DOI       | \[TBD]                                                   |
| Citation            | Warring, U. (2025). _Causal Clock Unification_ (v0.5).   |
| Companion documents | CSP (Causal Steering Protocols) — to be developed        |

#### Relationship to Companion Documents

**Firewall Statement:** This document (CCUF) defines the conceptual framework. Companion documents (CSP, implementation notes) may evolve without requiring CCUF revision. If companion development reveals conceptual gaps, those are addressed through explicit CCUF amendments with version increments.

***

_The framework is designed to guide near-term infrastructure decisions under existing technical constraints, while remaining compatible with future advances._

***

### Version History

<table><thead><tr><th width="94.89373779296875">Version</th><th width="109.36566162109375">Date</th><th width="103.16363525390625">Format</th><th>Summary</th></tr></thead><tbody><tr><td>v0.0.1</td><td>2025-12-12</td><td>Internal</td><td>Initial formulation of causal boundary concept linking clock period and effective size. Exploratory scope; definitions not yet fixed.</td></tr><tr><td>v0.0.2</td><td>2025-12-12</td><td>GitBook</td><td>Formalized framework as a boundary-condition design theory. Introduced strict separation of L_source, L_apparatus, and L_comparison. Defined causal efficiency parameter η(τ). Demoted Planck scale to dimensional endpoint only. Language tightened for falsifiability and GitBook presentation.</td></tr><tr><td>v0.1.2</td><td>2025-12-14</td><td>GitBook</td><td>Review-ready structural completion. Added: Executive Orientation (§0) with τ-coverage figure; explicit scope exclusions; Five-Gear Clockwork synthesis (§6) with TA-OPT definition; Testable Predictions (§8) with falsification criteria; Appendix A with protective preamble. All section openers standardized. Forward anchor from §3.2 to §8.1 installed.</td></tr><tr><td>v0.1.5</td><td>2025-12-15</td><td>GitBook</td><td>Table 0 added. Definition 2.1 rewritten for topology-safety (L_path, τ notation). η(τ) formula corrected. Hypothesis 3.1 numbered. §5.2 PTA worked example added. §6.3 candor weighting reduced to principle-only with CSP reference. §7 boundary list expanded (implementation, relativistic, legal exclusions). §8.1 falsification reframed as pre-registered interval criterion without numeric η_opt. §8.3 "systematic" qualifier added. Appendix A typo fixed, notation normalized. Document Metadata and firewall statement added.</td></tr><tr><td>v0.5.0</td><td>2025-12-15</td><td>GitBook</td><td>Action-guiding framework with parameter tables, open design questions, near-term impact framing. Figures replaced with comprehensive tables.</td></tr></tbody></table>
