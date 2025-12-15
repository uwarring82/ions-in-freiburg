---
description: Timekeeping as Causal Geometry
---

# \[Draft] Causal Clock Unification — A Design Framework for Unified Timekeeping Across Scales

***

**Author:** U. Warring\
**Affiliation:** Institute of Physics, University of Freiburg\
**Version:** 0.1.5\
**Last updated:** 2025-12-15\
**License:** CC BY 4.0

**Disclaimer** — _This document reflects an ongoing effort to clarify how causality constrains timekeeping architectures. Its authority derives from transparency, not finality._

***

### 0. Orientation

This section shows why the document exists, what problem it addresses, and how to read what follows.

Modern timekeeping operates across integration times spanning more than fifteen orders of magnitude—from sub-nanosecond optical interrogation cycles to decade-scale pulsar timing baselines. No single oscillator covers this range. Clocks that agree at one timescale may diverge at another, not because they fail, but because their comparison geometries impose different causal constraints.

This framework introduces a single architectural lens: the causal boundary condition governing phase comparison. It does not replace existing metrology tools, redefine time standards, or propose new physics. It offers a design language for reasoning about why different clock architectures exhibit different stability regimes—and how they might be coupled coherently.

**How to read this document.** Figure 0 below provides visual orientation before symbols appear. Table 0 quantifies the propagation delay bounds referenced in the figure caption. Each subsequent section begins with an explicit statement of its structural contribution. Hypotheses are labeled as such; predictions are testable and non-circular.

***

**Figure 0 — τ-based Coverage Map**

_\[Schematic: Horizontal axis labeled τ (integration time), spanning 10⁻⁹ s to 10⁸ s. Horizontal bars represent clock architectures: optical lattice clocks, microwave fountains, GNSS, VLBI, pulsar timing arrays. Bar color encodes log(L\_comparison/c), darker shades indicating longer propagation delays.]_

**Caption:** Propagation delay is encoded visually; explicit quantification follows in Table 0. This figure primes the reader by showing where each architecture operates in integration time and how comparison baseline length (encoded by color) varies across regimes.

***

**Table 0 — Propagation Delay Bounds by Architecture**

| Architecture                   | L\_comparison | τ\_min = L\_comparison/c | Typical Operating τ | η Range      |
| ------------------------------ | ------------- | ------------------------ | ------------------- | ------------ |
| Optical lattice clocks (local) | \~1 m         | \~3 ns                   | 10⁰–10⁴ s           | \~10⁻¹²–10⁻⁸ |
| Optical clock networks         | \~10³ km      | \~3 ms                   | 10³–10⁵ s           | \~10⁻²–10⁻¹  |
| Microwave fountains            | \~10⁴ km      | \~30 ms                  | 10⁴–10⁶ s           | \~10⁻³–10⁻²  |
| GNSS                           | \~10⁴ km      | \~30 ms                  | 10⁰–10⁴ s           | \~10⁻²–10⁰   |
| VLBI                           | \~10⁴ km      | \~30 ms                  | 10³–10⁵ s           | \~10⁻²–10⁻¹  |
| Pulsar timing arrays           | \~10¹⁶–10¹⁹ m | \~10⁸–10¹¹ s             | 10⁸–10⁹ s           | ≪10⁻²        |

**Note:** Values are representative orders of magnitude. Actual η depends on network topology and noise sources (see §3).

***

#### Scope Exclusions

This framework explicitly excludes:

* **Quantum gravity and Planck-scale physics.** The dimensional limit ℓ\_P = √(ℏG/c³) appears only as an endpoint of dimensional analysis, not as a physical regime addressed here.
* **Microscopic atomic transition theory.** Oscillator physics (atomic structure, transition rates, systematic shifts) is assumed, not derived.
* **Sociopolitical governance of civil time.** Decisions by ITU, BIPM, or national agencies regarding leap seconds, UTC definitions, or civil timekeeping policy lie outside this framework.

This framework does not introduce new physical laws, redefine existing standards, or replace Allan variance, TAI, UTC, or IERS products.

***

### 1. The Regime Shift: Why This Framework Is Needed Now

This section shows that a qualitative change in clock technology has created an architectural mismatch that existing frameworks do not address.

Optical clocks now routinely achieve fractional frequency uncertainties below 10⁻¹⁸, surpassing the best microwave standards by more than two orders of magnitude (Riehle, 2018). This advance creates an operational discontinuity: the comparison infrastructure—not the oscillators—limits achievable agreement.

Three developments define this regime shift:

1. **Optical clock maturity.** Multiple independent laboratories have demonstrated reproducibility at the 10⁻¹⁸ level using distinct atomic species and trapping geometries.
2. **Continental-scale optical links.** Stabilized fiber networks now enable phase-coherent comparison over baselines exceeding 1000 km, with transfer instabilities below the clock noise floor for integration times beyond 10⁴ s.
3. **Multi-messenger timing coordination.** Gravitational-wave detection, pulsar timing arrays, and geodetic VLBI increasingly require common timing frameworks across instruments with incommensurable comparison geometries.

The existing metrology toolkit—Allan variance for noise characterization, TAI/UTC for civil timekeeping, IERS products for Earth-rotation monitoring—remains essential. But these tools describe what clocks do, not why different architectures exhibit different stability regimes. A design framework addressing comparison geometry has become necessary.

***

### 2. The Causal Boundary as a Design Constraint

This section shows that a single inequality constrains all phase-comparison operations and defines the causal boundary that clocks cannot circumvent.

#### 2.1 The Realisability Horizon

Every comparison of two oscillators requires information exchange. The propagation time along the longest required signal path sets an irreducible lower bound on the timescale at which their phases can be correlated.

**Definition 2.1 (Realisability Horizon).**\
For any phase comparison operation requiring causal information exchange over a longest required signal path L\_path, the integration time must satisfy:

\$$\tau \ge \frac{L\_{\text{path\}}}{c}\$$

For mutual verification (bidirectional / round-trip causal closure), this becomes:

\$$\tau \ge \frac{2L\_{\text{path\}}}{c}\$$

L\_path reduces to L\_comparison in direct two-node comparisons; for star/mesh topologies, L\_path is the maximum required path for the chosen protocol.

This inequality is termed the **realisability horizon**. It is a boundary condition, not a dynamical law. It does not describe how clocks evolve; it describes which comparisons are possible.

Any architecture proposing agreement over baseline L in time τ < L/c violates causality. No oscillator improvement, no signal processing technique, and no statistical method can circumvent this bound.

#### 2.2 Three Orthogonal Length Scales

Clocks involve three distinct spatial scales that must not be conflated:

* **L\_source**: the spatial extent of the oscillator (e.g., ion trap dimension, lattice extent, pulsar magnetosphere).
* **L\_apparatus**: the interrogation and control region (e.g., vacuum chamber, antenna, telescope baseline).
* **L\_comparison**: the baseline over which phase agreement is sought between two or more oscillators.

Only L\_comparison enters the causal constraint. Advances in L\_source (better oscillators) or L\_apparatus (better interrogation) do not relax the realisability horizon.

This distinction clarifies why optical clocks with exquisite local stability may exhibit degraded performance when networked: their L\_source and L\_apparatus have improved, but L\_comparison introduces constraints absent in local operation.

***

### 3. Causal Efficiency as an Architectural Control Parameter

This section shows that a dimensionless ratio characterizes how close any architecture operates to its causal limit.

#### 3.1 Definition

For any clock architecture operating at integration time τ with comparison baseline L\_comparison, define the **causal efficiency**:

\$$\eta(\tau) = \frac{L\_{\text{comparison\}}}{c , \tau}\$$

This ratio has the following properties:

* η ∈ (0, 1] by the realisability horizon.
* η = 1 means the architecture operates at the causal limit: all available integration time is consumed by propagation.
* η ≪ 1 means the architecture operates far inside the causal limit: propagation delay is negligible compared to integration time.

Causal efficiency is not an optimization target by default. Different architectures may exhibit optimal noise performance at different values of η, determined by their dominant noise sources and comparison geometries.

#### 3.2 The η\_opt Hypothesis

**Hypothesis 3.1 (Optimal Causal Efficiency).**\
Each clock architecture exhibits a noise-regime transition at some characteristic efficiency η\_opt, determined by comparison geometry and dominant noise sources.

This hypothesis is testable: for a given architecture, measure stability as a function of integration time while holding L\_comparison fixed. If a transition in noise scaling (e.g., from white frequency noise to flicker floor) correlates with a characteristic value of η, the hypothesis is supported. If no such correlation exists, the hypothesis is falsified.

The experimental protocol and falsification criteria are described in §8.1.

***

### 4. Clocks as Architectures, Not Devices

This section shows that the framework treats clocks as extended systems defined by their comparison geometry, not as point-like devices characterized solely by oscillator quality.

A clock, in this framework, is not an atomic transition or a cavity mode. It is a complete architecture comprising:

1. An oscillator (the frequency source).
2. An interrogation apparatus (the local control system).
3. A comparison baseline (the infrastructure for phase agreement).

This architectural view has consequences:

**No universal clock metric.** Two clocks cannot be ranked by a single figure of merit without specifying the comparison baseline and integration time. An optical lattice clock may outperform a hydrogen maser at τ = 10⁴ s over a 100 km baseline, but underperform at τ = 10⁷ s over a 6000 km baseline, depending on dominant noise sources.

**Comparison is constitutive.** A clock achieves its stated performance only relative to a specified comparison architecture. Stability numbers quoted without comparison context are incomplete.

**Modularity.** Oscillators, apparatus, and comparison links can be designed, characterized, and upgraded independently. Improving one component improves the architecture only if the other components do not become limiting.

***

### 5. Agreement Requires Causal Closure

This section shows that meaningful phase agreement between clocks requires causal closure—the round-trip exchange of phase information within the integration interval.

#### 5.1 Causal Closure Condition

Two oscillators at separation L achieve causal closure at integration time τ if and only if:

\$$2L \le c , \tau\$$

where L is the relevant one-way path length for the verification loop.

The factor of 2 accounts for round-trip propagation: phase information must travel from one clock to the other and return (or equivalently, both clocks must send and receive) within the integration window.

This is the bidirectional special case of Definition 2.1.

Without causal closure, clocks may be individually stable but cannot verify mutual agreement. They run independently, not in concert.

#### 5.2 Implications for Network Design

For optical clock networks, this condition constrains topology. A network spanning continental distances (L \~ 1000 km) achieves causal closure only for τ ≳ 10 ms. At shorter integration times, clocks at network edges cannot verify agreement with clocks at the center.

For pulsar timing arrays, baselines are astronomical (L \~ 10¹⁹ m for galactic-scale correlations). Causal closure requires τ ≳ 10¹¹ s—decades. The multi-year integration times used in gravitational-wave searches are not a choice but a consequence of this constraint.

**Worked example (PTA):**\
For a pulsar timing array with L\_comparison \~ 10¹⁹ m and τ \~ 10¹¹ s:

\$$\eta = \frac{10^{19} , \text{m\}}{3 \times 10^8 , \text{m/s} \times 10^{11} , \text{s\}} = \frac{10^{19\}}{3 \times 10^{19\}} \approx 0.3\$$

However, for typical PTA operations at τ \~ 10⁸ s with L\_comparison \~ 10¹⁶ m (inter-pulsar correlations rather than Earth-pulsar baselines):

\$$\eta = \frac{10^{16} , \text{m\}}{3 \times 10^8 , \text{m/s} \times 10^{8} , \text{s\}} = \frac{10^{16\}}{3 \times 10^{16\}} \approx 0.3\$$

At these values, PTAs operate moderately inside the causal limit. For Earth-based timing references compared to pulsars at \~kpc distances with decade-scale integrations, η ≪ 1 applies. If PTA stability showed _systematic_ baseline dependence at fixed τ, this would motivate revision of the η ≪ 1 geometry-insensitivity assumption.

***

### 6. Strongly-Coupled Clockwork (Operational Synthesis)

This section shows how the framework synthesizes existing timekeeping infrastructure into a coherent multi-architecture system with explicit coupling and feedback.

#### 6.1 Five-Gear Clockwork

Modern precision timekeeping already operates as a coupled system, though this coupling is rarely made explicit. The framework identifies five principal gear-trains:

1. **Optical clocks** — highest stability at τ = 10³–10⁵ s, L\_comparison ≲ 10³ km.
2. **Microwave fountains** — intermediate stability, long-term accuracy realization, L\_comparison ≲ 10⁴ km.
3. **GNSS** — global distribution, real-time access, L\_comparison \~ 10⁴ km.
4. **VLBI** — Earth-orientation determination, L\_comparison \~ 10⁴ km.
5. **Pulsar timing arrays** — ultra-long-term stability, gravitational-wave detection, L\_comparison \~ 10¹⁶–10¹⁹ m.

***

**Figure 1 — Five-Gear Clockwork**

_\[Schematic: Five interconnected nodes arranged in a network topology (not a hierarchy). Nodes labeled: Optical Clocks, Fountains, GNSS, VLBI, Pulsar Ensembles. Bidirectional arrows indicate coupling: Optical ↔ Fountains (frequency comparison), Fountains ↔ GNSS (steering), GNSS ↔ VLBI (Earth orientation), VLBI ↔ Pulsars (long-baseline correlation), Pulsars → Optical (decadal stability transfer). Feedback loops shown as dashed return paths.]_

**Caption:** The five gear-trains of modern timekeeping shown as a coupled network. Arrows indicate phase-information coupling; dashed lines indicate feedback. This is not a hierarchy but a mesh: each gear-train contributes stability in its native regime and accepts constraints from adjacent regimes.

***

These gear-trains are not independent. Each couples to its neighbors through explicit comparison operations. The framework makes this coupling visible and designable.

#### 6.2 TA-OPT and Continuous Earth-Rotation Tracking

The following definition is adopted for operational clarity:

**TA-OPT** — a timescale realized exclusively from optical clocks, with candor-weighted steering and without intermediate microwave fly-wheels, serving as the high-stability reference against which Earth-rotation deviations are tracked.

TA-OPT is not a successor to TAI, not a new primary standard, and carries no claim of institutional authority. It is a design target: a timescale whose stability derives entirely from optical standards, against which the variable Δ(t) = UT1 − TA-OPT can be monitored as a smooth, continuous function rather than managed through leap-second discontinuities.

***

**Figure 2 — Leap-Second Exit Architecture**

_\[Single-panel schematic: Horizontal axis is time (years). Three curves: (1) TA-OPT as a smooth continuous line; (2) Δ(t) = UT1 − TA-OPT as a smooth polynomial curve, bounded within ±0.9 s band; (3) UT1 shown as a scatter band around the Δ(t) curve, reflecting Earth-rotation variability. No step discontinuities appear. Vertical dashed lines indicate epoch boundaries but no jumps.]_

**Caption:** Conceptual architecture for leap-second elimination. TA-OPT provides a continuous optical reference. The deviation Δ(t) is tracked as a smooth function, eliminating the need for step corrections. UT1 remains observable but is not used to steer the primary timescale.

***

#### 6.3 Candor Weighting

Steering algorithms for composite timescales must account for clock reliability, not merely stability.

**Candor weighting (principle):** Clocks with statistically significant unexplained deviations are downweighted relative to demonstrated consistency. Specific update laws are implementation-dependent and documented in CSP v0.1.

This principle assigns influence based on a clock's demonstrated consistency between predicted and observed performance—downweighting clocks that exhibit unexplained excursions regardless of their nominal stability specifications.

***

### 7. What This Framework Is — and Is Not

This section shows the explicit boundaries of the framework's claims and applicability.

#### What This Framework Is

* A **design language** for reasoning about clock architectures in terms of comparison geometry.
* A **boundary condition** (L\_comparison ≤ c τ) that constrains all phase-comparison operations.
* An **architectural control parameter** (η) that characterizes proximity to the causal limit.
* A **synthesis** that makes explicit the coupling between existing timekeeping gear-trains.

#### What This Framework Is Not

* **Not a new physical theory.** No equations of motion are proposed. Causality is assumed, not derived.
* **Not a replacement for Allan variance.** Noise characterization remains essential; this framework addresses comparison geometry, not oscillator statistics.
* **Not a redefinition of TAI, UTC, or SI units.** Existing standards retain their definitions and authority.
* **Not a policy proposal.** Decisions about leap seconds, civil time, or institutional governance lie outside scope.
* **Not a claim of optimality.** The framework identifies η\_opt as a hypothesis to be tested, not a design prescription.
* **Not a complete implementation specification.** Algorithms, hardware designs, and software implementations lie outside this document; see CSP v0.1 for operational protocols.
* **Not a substitute for relativistic corrections.** IERS conventions for relativistic time transfer are assumed, not replaced.
* **Not a legal traceability standard.** UTC, TAI, and SI second remain the legal standards for civil timekeeping and metrological traceability.

***

### 8. Testable Predictions (Non-Circular)

This section shows what empirical outcomes would support or falsify the framework's central hypothesis.

#### 8.1 Prediction: η\_opt Location for Optical Clock Networks

**Setup:** An optical clock network with fixed baseline L\_comparison = 1000 km.

**Protocol:** As integration time τ increases from 10² s to 10⁵ s, measure modified Allan deviation while scanning the causal efficiency η(τ) = L\_comparison / (c τ) through the range η ∈ \[0.01, 0.5].

**Prediction:** The measured frequency instability will exhibit a transition in noise scaling at some characteristic η\_opt within this range. Below η\_opt, instability decreases with increasing τ; above η\_opt, instability floors or increases due to comparison-link noise.

**Falsification criterion:** If no changepoint in noise scaling is observed over the pre-registered interval η ∈ \[0.01, 0.5]—if instability continues to decrease monotonically without any transition—the hypothesis is not supported for this architecture.

**Note:** The specific value of η\_opt is not predicted _a priori_; it is the observable to be measured. Pre-registering the search interval prevents post-hoc boundary adjustment.

#### 8.2 Prediction: η\_opt Location for VLBI Baselines

**Setup:** VLBI baseline L\_comparison = 6000 km, integration times τ from 10³ s to 10⁵ s.

**Prediction:** A noise-regime transition will occur at a different η\_opt than for optical networks, reflecting the different dominant noise sources (tropospheric delay for VLBI vs. fiber phase noise for optical links).

**Falsification criterion:** If both architectures exhibit identical η\_opt values despite different noise environments, the hypothesis that η\_opt is architecture-specific is falsified.

#### 8.3 Prediction: Pulsar Timing Array Regime

**Setup:** Pulsar timing array with L\_comparison \~ 10¹⁶ m (galactic-scale correlations), τ \~ 10⁸ s (multi-year integrations).

**Prediction:** At the low η values typical of PTA operations (see §5.2), stability at these timescales should be limited by intrinsic pulsar timing noise and interstellar medium effects, not by comparison geometry.

**Falsification criterion:** If PTA stability shows _systematic_ sensitivity to comparison baseline at fixed τ, the framework's prediction that η ≪ 1 regimes are geometry-insensitive requires revision.

#### 8.4 Non-Circularity

These predictions are non-circular because:

1. The η\_opt values are not assumed; they are measured.
2. The noise sources (link noise, tropospheric noise, timing noise) are characterized independently of the framework.
3. The framework predicts correlations between η and noise-regime transitions; it does not define those transitions.
4. The search intervals are pre-registered to prevent post-hoc boundary adjustment.

***

### Appendix A — Illustrative Comparison of Causal Efficiency (Not a Validation)

**Protective Preamble:** This comparison is illustrative; it assumes independently measured noise floors and does not validate the existence or location of an optimal causal efficiency η\_opt. Values here are not used to derive the falsification criteria in §8.1.

#### Comparison Setup

| Architecture          | Comparison Baseline | τ     | η(τ)  |
| --------------------- | ------------------- | ----- | ----- |
| Optical clock network | 1000 km = 10⁶ m     | 10⁴ s | 0.033 |
| VLBI baseline         | 6000 km = 6 × 10⁶ m | 10⁴ s | 0.20  |

#### Calculation

For the optical network:

\$$\eta = \frac{L\_{\text{comparison\}}}{c , \tau} = \frac{10^6 , \text{m\}}{3 \times 10^8 , \text{m/s} \times 10^4 , \text{s\}} = \frac{10^6}{3 \times 10^{12\}} \approx 0.033\$$

For the VLBI baseline:

\$$\eta = \frac{L\_{\text{comparison\}}}{c , \tau} = \frac{6 \times 10^6 , \text{m\}}{3 \times 10^8 , \text{m/s} \times 10^4 , \text{s\}} = \frac{6 \times 10^6}{3 \times 10^{12\}} = 0.20\$$

#### Assumptions and Limitations

The values above are point estimates at a single integration time. No optimization is performed. Error bars on η derive from uncertainties in effective comparison baseline (for networks with multiple links) and are not computed here.

Noise floors assumed as external inputs:

* **Optical link noise:** Stabilized fiber transfer instability at 10⁴ s, taken from published characterizations.
* **Tropospheric noise:** VLBI path-delay variability, taken from geodetic analyses.

These noise floors are independently measured quantities; they are not derived from the framework.

***

_\[Figure A1: Two data points with error bars. Horizontal axis: Architecture (Optical Network, VLBI). Vertical axis: η at τ = 10⁴ s. Optical network point at η ≈ 0.033; VLBI point at η ≈ 0.20. Error bars reflect baseline uncertainty. No fitted curve. No optimization.]_

**Caption:** Illustrative comparison of causal efficiency for two architectures at identical integration time. This is not a validation of the η\_opt hypothesis; it demonstrates only that different architectures operate at different causal efficiencies.

***

### References

1. A. Einstein, _Zur Elektrodynamik bewegter Körper_, Ann. Phys. **17**, 891–921 (1905).
2. H. Reichenbach, _Axiomatik der relativistischen Raum-Zeit-Lehre_, Vieweg (1924).
3. D. Malament, _Causal theories of time and the conventionality of simultaneity_, Noûs **11**, 293–300 (1977).
4. D. W. Allan, _Statistics of atomic frequency standards_, Proc. IEEE **54**, 221–230 (1966).
5. W. M. Itano et al., _Quantum projection noise: Population fluctuations in two-level systems_, Phys. Rev. A **47**, 3554 (1993).
6. D. J. Wineland et al., _Experimental issues in coherent quantum-state manipulation of trapped atomic ions_, J. Res. NIST **103**, 259–328 (1998).
7. C. W. Chou et al., _Optical clocks and relativity_, Science **329**, 1630–1633 (2010). https://doi.org/10.1126/science.1192720
8. S. Kopeikin et al., _Relativistic Reference Frames for Astrometry and Geodesy_, Springer (2011); see also ISSI Spacetime Metrology program (2015–).
9. J. E. Sovers, C. S. Jacobs, and G. S. Lanyi, _Astrometry and geodesy with radio interferometry_, Rev. Mod. Phys. **70**, 1393 (1998). https://doi.org/10.1103/RevModPhys.70.1393
10. B. Guinot, _History of the Bureau International de l'Heure_, in _Polar Motion: Historical and Scientific Problems_ (ASP Conference Series, Vol. 208), 175–184 (2000).
11. G. Petit and B. Luzum (Eds.), _IERS Conventions (2010)_, IERS Technical Note No. 36, Verlag des Bundesamts für Kartographie und Geodäsie, Frankfurt am Main (2010).
12. S. Lambert and C. Le Poncin-Lafitte, _Improved determination of VLBI delays_, A\&A **529**, A70 (2011). https://doi.org/10.1051/0004-6361/201116599
13. R. N. Manchester et al., _The International Pulsar Timing Array_, PASA **30**, e017 (2013). https://doi.org/10.1017/pasa.2012.017
14. L. Verbiest et al., _The International Pulsar Timing Array: First data release_, MNRAS **458**, 1267–1288 (2016). https://doi.org/10.1093/mnras/stw347
15. F. Riehle, _Optical clock networks_, Nature Photonics **11**, 25–31 (2017). https://doi.org/10.1038/nphoton.2016.235
16. G. Hobbs et al., _The International Pulsar Timing Array: Second data release_, MNRAS **491**, 5951–5969 (2020). https://doi.org/10.1093/mnras/stz3071

***

_Special thanks to all my past, current, and future environments._

***

### Disclaimer

| Item                       | Statement                                                                                                                                                                                                                                                                            |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Scope                      | This document proposes a design-theoretic framework for comparing and optimizing clock architectures. It does not introduce new physical laws, modify established relativity, or claim experimental discovery. _Design language for unified timekeeping across scales._              |
| Status                     | This page presents v1.0-RC (Release Candidate / Editorial Freeze) intended for citation and external review. Core definitions and structure are stable; minor editorial corrections may occur before v1.0 final.                                                                     |
| Relationship to Prior Work | All underlying physical principles—relativistic causality, clock synchronization, noise theory, and time–frequency metrology—are well established. The contribution here is a structural synthesis and formalization of these elements into a unified comparison-geometry framework. |
| Novelty Claim              | To the best of our knowledge, the explicit separation of comparison geometry from oscillator physics, and the formulation of causal efficiency as a design parameter, has not been previously formalized. This claim is made cautiously and remains open to correction.              |
| Non-Claims                 | The framework makes no claims about Planck-scale clocks, quantum gravity, superluminal signaling, or the ultimate nature of time. The Planck point appears only as a dimensional reference, not an empirical target.                                                                 |
| Intended Use               | The framework is intended as a conceptual and architectural guide for analyzing existing clocks and designing distributed timekeeping systems. It should be read as a tool for reasoning, not as a prescription or constraint on future physics.                                     |
| Feedback & Corrections     | Constructive criticism, references to overlooked prior work, and counterexamples are explicitly welcomed. Any demonstrated errors or anticipations will be acknowledged and incorporated in subsequent versions.                                                                     |

***

### Document Metadata

| Field               | Value                                                                                                                                                                                                                 |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Canonical DOI**   | \[TBD — to be assigned upon archival deposit]                                                                                                                                                                         |
| **Git commit hash** | \[TBD — to be populated at publication]                                                                                                                                                                               |
| **Citation string** | Warring, U. (2025). _Causal Clock Unification — A Design Framework for Unified Timekeeping Across Scales_ (v1.0-RC). GitBook. https://uwarring.gitbook.io/ions-in-freiburg/system-frameworks/causal-clock-unification |
| **Errata link**     | \[TBD — to be established if corrections needed post-publication]                                                                                                                                                     |

#### Relationship to Other Documents

**Firewall Statement:** This document (CCUF) defines the conceptual and boundary-condition framework for causal clock unification. It is intended to be **stable across implementation revisions**.

Companion documents may include:

* **CSP (Causal Steering Protocols)** — operational protocols, including candor weighting update laws and architecture-specific η\_opt ranges. CSP versions may evolve without requiring CCUF revision.
* **Implementation notes** — hardware, software, or experimental specifications that instantiate the framework for particular architectures.

**Dependency direction:** CSP and implementation documents depend on CCUF; CCUF does not depend on their contents. If CSP revisions reveal conceptual gaps in CCUF, those gaps are addressed through explicit CCUF amendments with version increments, not through silent drift.

***

### Version History

<table><thead><tr><th width="94.89373779296875">Version</th><th width="109.36566162109375">Date</th><th width="89.92498779296875">Format</th><th>Summary</th></tr></thead><tbody><tr><td>v0.0.1</td><td>2025-12-12</td><td>Internal</td><td>Initial formulation of causal boundary concept linking clock period and effective size. Exploratory scope; definitions not yet fixed.</td></tr><tr><td>v0.0.2</td><td>2025-12-12</td><td>GitBook</td><td>Formalized framework as a boundary-condition design theory. Introduced strict separation of L_source, L_apparatus, and L_comparison. Defined causal efficiency parameter η(τ). Demoted Planck scale to dimensional endpoint only. Language tightened for falsifiability and GitBook presentation.</td></tr><tr><td>v0.1.2</td><td>2025-12-14</td><td>GitBook</td><td>Review-ready structural completion. Added: Executive Orientation (§0) with τ-coverage figure; explicit scope exclusions; Five-Gear Clockwork synthesis (§6) with TA-OPT definition; Testable Predictions (§8) with falsification criteria; Appendix A with protective preamble. All section openers standardized. Forward anchor from §3.2 to §8.1 installed.</td></tr><tr><td><strong>v0.1.5</strong></td><td><strong>2025-12-15</strong></td><td><strong>GitBook</strong></td><td>Table 0 added. Definition 2.1 rewritten for topology-safety (L_path, τ notation). η(τ) formula corrected. Hypothesis 3.1 numbered. §5.2 PTA worked example added. §6.3 candor weighting reduced to principle-only with CSP reference. §7 boundary list expanded (implementation, relativistic, legal exclusions). §8.1 falsification reframed as pre-registered interval criterion without numeric η_opt. §8.3 "systematic" qualifier added. Appendix A typo fixed, notation normalized. Document Metadata and firewall statement added.</td></tr><tr><td>v0.x</td><td>—</td><td>Planned</td><td>make the manuscript more accessible, and actionable</td></tr></tbody></table>
