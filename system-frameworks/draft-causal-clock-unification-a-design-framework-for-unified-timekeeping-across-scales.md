---
description: Timekeeping as Causal Geometry
---

# \[DRAFT] Causal Clock Unification — A Design Framework for Unified Timekeeping Across Scales

***

{% hint style="info" %}
**Author:** U. Warring\
**Affiliation:** Institute of Physics, University of Freiburg\
**Version:** 0.6.0\
**Last updated:** 2025-12-15\
**License:** CC BY 4.0\
\
**Disclaimer** — _This document clarifies how causality constrains timekeeping architectures. Its authority derives from transparency, not finality. The framework is designed to guide near-term infrastructure decisions under existing technical constraints, while remaining compatible with future advances._

**Stability note:** This version is stable for citation and program planning. Algorithms and operational protocols live in companion documents (CSP).
{% endhint %}

***

### 0. Orientation

Modern timekeeping operates across integration times spanning more than fifteen orders of magnitude—from sub-nanosecond optical interrogation cycles to decade-scale pulsar timing baselines. No single oscillator covers this range. Clocks that agree at one timescale may diverge at another, not because they fail, but because their comparison geometries impose different causal constraints.

This framework introduces a single architectural lens: the causal boundary condition governing phase comparison. It does not replace existing metrology tools, redefine time standards, or propose new physics. It offers a design language for reasoning about why different clock architectures exhibit different stability regimes—and how they might be coupled coherently.

**How to read this document.** Figure 1 provides visual orientation across the five gear-trains. Table 1 quantifies parameters. Each section states its structural contribution. Hypotheses are labeled; predictions are testable. Open questions are marked as such.

***

### Quickstart: Compute η and Classify Your System

| Step            | Action                                                                      |
| --------------- | --------------------------------------------------------------------------- |
| **1. Inputs**   | Determine L\_comparison (or L\_path for complex topologies) and operating τ |
| **2. Compute**  | η = L\_comparison / (c × τ)                                                 |
| **3. Classify** | See regime table below                                                      |
| **4. Act**      | Follow recommended next step                                                |

| η Range        | Regime          | Recommended Action                                        |
| -------------- | --------------- | --------------------------------------------------------- |
| η \~ 1         | Causal boundary | Comparison protocol/topology dominates; optimize L\_path  |
| 0.01 < η < 0.5 | Transition zone | Run η\_opt characterization campaign (§10.1)              |
| η ≪ 0.01       | Deep interior   | Focus on oscillator systematics; geometry is not limiting |

**Example:** Continental optical link, L = 1000 km, τ = 10⁴ s\
→ η = 10⁶ m / (3×10⁸ m/s × 10⁴ s) = 0.033\
→ Regime: Transition zone\
→ Action: Characterize η\_opt for this link

***

### Figure 1 — Five-Gear Clockwork Across τ and η

```
                                    CAUSAL EFFICIENCY η = L/(cτ)
                    ←—— Deep Interior (η≪0.01) ——|—— Transition (0.01–0.5) ——|—— Moderate (η~1) ——→

    10⁻² s  ┤                                   
            │  ┌─────────────┐                  
    10⁰ s   ┤  │   OPTICAL   │←——————————————————————————————————————┐
            │  │   CLOCKS    │  steering                             │
    10² s   ┤  │  (Gear 1)   │————————┐                              │
            │  └─────────────┘        │                              │
    10³ s   ┤         ↑               ↓                              │
            │         │        ┌─────────────┐      ┌─────────────┐  │
τ   10⁴ s   ┤   frequency      │  FOUNTAINS  │      │    GNSS     │  │
            │   comparison     │   + TAI     │←————→│  (Gear 3)   │  │ decadal
    10⁵ s   ┤         │        │  (Gear 2)   │      └──────┬──────┘  │ stability
            │         │        └──────┬──────┘             │         │ transfer
    10⁶ s   ┤         │               │                    │         │
            │         │               │   Earth            ↓         │
    10⁷ s   ┤         │               │  orientation ┌─────────────┐ │
            │         │               └—————————————→│    VLBI     │ │
    10⁸ s   ┤         │                              │  (Gear 4)   │ │
            │         │                              └──────┬──────┘ │
    10⁹ s   ┤         │                                     │        │
            │         │               long-baseline         ↓        │
    10¹⁰ s  ┤         │               correlation    ┌─────────────┐ │
            │         └←——————————————-——————————————│  PULSAR     │—┘
    10¹¹ s  ┤                                        │  TIMING     │
            │                                        │  (Gear 5)   │
                                                     └─────────────┘

            ├─────────────────┼─────────────────┼─────────────────┤
           10⁰              10³               10⁶              10⁹   L_comparison (km)
```

**Caption:** The five gear-trains of precision timekeeping shown across integration time (τ, vertical) and comparison baseline (L\_comparison, horizontal), with causal efficiency regimes indicated. Arrows show phase-information coupling between gears. **This is a design lens for reasoning about architecture, not an architecture mandate.** Each gear-train contributes stability in its native regime and accepts constraints from adjacent regimes. For near-term entry points by actor type, see Table 6 (§9.1). Data ranges correspond to Tables 1–4.

**Source note:** Figure is conceptual. Quantitative ranges are derived from Tables 1–4, which cite primary sources.

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

**Optical clock maturity.** Multiple independent laboratories have demonstrated reproducibility at the 10⁻¹⁸ level using distinct atomic species (Sr, Yb, Al⁺) and trapping geometries (lattice, single-ion).

**Continental-scale optical links.** Stabilized fiber networks now enable phase-coherent comparison over baselines exceeding 1000 km, with transfer instabilities below the clock noise floor for integration times beyond 10⁴ s. The European fiber network (PTB–SYRTE–NPL–INRIM) demonstrates this capability operationally \[Lisdat 2016, Delva 2017].

**Multi-messenger timing coordination.** Gravitational-wave detection, pulsar timing arrays, and geodetic VLBI increasingly require common timing frameworks across instruments with incommensurable comparison geometries.

The existing metrology toolkit—Allan variance for noise characterization, TAI/UTC for civil timekeeping, IERS products for Earth-rotation monitoring—remains essential. But these tools describe what clocks do, not why different architectures exhibit different stability regimes. A design framework addressing comparison geometry has become necessary.

***

#### Table 1 — Clock Architectures: Parameter Overview

<table><thead><tr><th width="128.9659423828125">Architecture</th><th width="139.62994384765625">L_comparison</th><th width="94.2606201171875">τ_min = L/c</th><th width="91.4517822265625">Typical τ</th><th width="101.874267578125">η Range</th><th>Dominant Noise</th><th>σ_y(τ)</th><th>Source</th></tr></thead><tbody><tr><td>Optical lattice (local)</td><td>~1 m</td><td>~3 ns</td><td>1–10⁴ s</td><td>10⁻¹²–10⁻⁸</td><td>Quantum projection</td><td>~1×10⁻¹⁸ @ 10⁴ s</td><td>[1]</td></tr><tr><td>Optical ion (local)</td><td>~1 mm</td><td>~3 ps</td><td>1–10⁴ s</td><td>10⁻¹⁵–10⁻¹¹</td><td>Quantum projection</td><td>~1×10⁻¹⁸ @ 10⁴ s</td><td>[2]</td></tr><tr><td>Optical network (continental)</td><td>10²–10³ km</td><td>0.3–3 ms</td><td>10³–10⁵ s</td><td>10⁻²–10⁻¹</td><td>Fiber phase noise</td><td>~1×10⁻¹⁸ @ 10⁴ s</td><td>[3]</td></tr><tr><td>Microwave fountain</td><td>~10⁴ km</td><td>~30 ms</td><td>10⁴–10⁶ s</td><td>10⁻³–10⁻²</td><td>Dick effect</td><td>~1×10⁻¹⁶ @ 10⁵ s</td><td>[4]</td></tr><tr><td>Hydrogen maser</td><td>~10⁴ km</td><td>~30 ms</td><td>10²–10⁵ s</td><td>10⁻³–10⁻¹</td><td>Cavity drift</td><td>~1×10⁻¹⁵ @ 10⁴ s</td><td>[5]</td></tr><tr><td>GNSS (GPS/Galileo)</td><td>~2×10⁴ km</td><td>~70 ms</td><td>1–10⁴ s</td><td>10⁻²–10⁰</td><td>Ionosphere, multipath</td><td>~1×10⁻¹⁴ @ 10³ s</td><td>[6]</td></tr><tr><td>TWSTFT</td><td>~10⁴ km</td><td>~30 ms</td><td>10²–10⁵ s</td><td>10⁻³–10⁻¹</td><td>Troposphere</td><td>~5×10⁻¹⁶ @ 10⁴ s</td><td>[7]</td></tr><tr><td>VLBI</td><td>6–10×10³ km</td><td>20–30 ms</td><td>10³–10⁵ s</td><td>10⁻²–10⁻¹</td><td>Troposphere, clocks</td><td>~1×10⁻¹⁵ @ 10⁴ s</td><td>[8]</td></tr><tr><td>Pulsar timing (single)†</td><td>~10¹⁹ m</td><td>~10¹¹ s</td><td>10⁷–10⁹ s</td><td>≪10⁻²</td><td>Timing noise, ISM</td><td>~1×10⁻¹⁵ @ 10⁸ s</td><td>[9]</td></tr><tr><td>PTA (array correlation)†</td><td>~10¹⁶ m</td><td>~10⁸ s</td><td>10⁸–10⁹ s</td><td>~0.03–0.3</td><td>Pulsar red noise</td><td>~1×10⁻¹⁵ @ 10⁸ s</td><td>[10]</td></tr></tbody></table>

**Table 1 Sources:**\
\[1] Bothwell et al. 2022, Metrologia 59:065009 (JILA Sr)\
\[2] Brewer et al. 2019, PRL 123:033201 (NIST Al⁺)\
\[3] Lisdat et al. 2016, Nat. Commun. 7:12443 (PTB-SYRTE link)\
\[4] Guéna et al. 2012, IEEE TUFFC 59:391 (SYRTE Cs fountain)\
\[5] Parker 2012, Metrologia 49:S86 (H-maser ensemble)\
\[6] Petit & Jiang 2008, Metrologia 45:S35 (GPS time transfer)\
\[7] Fujieda et al. 2014, Metrologia 51:253 (TWSTFT carrier-phase)\
\[8] Schuh & Behrend 2012, J. Geodyn. 61:68 (IVS VLBI)\
\[9] Hobbs et al. 2020, MNRAS 491:5951 (IPTA DR2)\
\[10] NANOGrav 2023, ApJL 951:L8 (15-year dataset)

**Notes:**

* L\_comparison = baseline over which phase agreement is sought
* τ\_min = minimum integration time for causal closure (one-way)
* η = L\_comparison/(cτ), the causal efficiency parameter
* σ\_y(τ) values are representative of demonstrated performance; actual values vary by implementation
* ISM = interstellar medium scattering/dispersion

†**PTA semantics:** For single-pulsar timing, L\_comparison is Earth-pulsar distance (\~kpc). For array correlation (gravitational-wave detection), L\_comparison is the inter-pulsar angular separation projected onto the gravitational-wave wavelength; values here use \~10¹⁶ m as representative for spatial correlations at nHz frequencies. See §10.3 for falsification criteria involving baseline dependence.

***

#### Table 2 — Current Optical Clock Performance (Representative Systems)

| Species | Trap       | Institution | σ\_y @ 1 s   | σ\_y @ 10⁴ s | Systematic | Reference      |
| ------- | ---------- | ----------- | ------------ | ------------ | ---------- | -------------- |
| ⁸⁷Sr    | Lattice    | JILA        | 4.8×10⁻¹⁷/√τ | \~5×10⁻¹⁹    | 2.0×10⁻¹⁸  | Bothwell 2022  |
| ⁸⁷Sr    | Lattice    | PTB         | 1.3×10⁻¹⁶/√τ | \~1×10⁻¹⁸    | 2.0×10⁻¹⁸  | Schwarz 2020   |
| ¹⁷¹Yb   | Lattice    | NIST        | 3.2×10⁻¹⁶/√τ | \~3×10⁻¹⁸    | 1.4×10⁻¹⁸  | McGrew 2018    |
| ¹⁷¹Yb⁺  | Single-ion | PTB         | 8×10⁻¹⁶/√τ   | \~8×10⁻¹⁸    | 3.2×10⁻¹⁸  | Huntemann 2016 |
| ²⁷Al⁺   | Single-ion | NIST        | —            | \~1×10⁻¹⁷    | 9.4×10⁻¹⁹  | Brewer 2019    |

**Note:** Values represent published results as of late 2024. The comparison geometry framework applies regardless of which oscillator achieves lowest instability.

***

### 2. The Causal Boundary as a Design Constraint

Every comparison of two oscillators requires information exchange. The propagation time along the longest required signal path sets an irreducible lower bound on the timescale at which their phases can be correlated.

#### 2.1 The Realisability Horizon

**Definition 2.1 (Realisability Horizon).**\
For any phase comparison operation requiring causal information exchange over a longest required signal path L\_path, the integration time must satisfy:

<p align="center"><span class="math">\tau \ge \frac{L_{\text{path}}}{c}</span></p>

For mutual verification (bidirectional / round-trip causal closure):

<p align="center"><span class="math">\tau \ge \frac{2 L_{\text{path}}}{c}</span></p>

L\_path reduces to L\_comparison in direct two-node comparisons; for star/mesh topologies, L\_path is the maximum required path for the chosen protocol.

This inequality is a **boundary condition**, not a dynamical law. It does not describe how clocks evolve; it describes which comparisons are possible. Any architecture proposing agreement over baseline L in time τ < L/c violates causality. No oscillator improvement, no signal processing technique, and no statistical method can circumvent this bound.

#### 2.2 Three Orthogonal Length Scales

Clocks involve three distinct spatial scales that must not be conflated:

| Scale      | Symbol        | Definition                   | Examples                                              |
| ---------- | ------------- | ---------------------------- | ----------------------------------------------------- |
| Source     | L\_source     | Spatial extent of oscillator | Ion trap: \~1 mm; Lattice: \~1 cm; Pulsar: \~10 km    |
| Apparatus  | L\_apparatus  | Interrogation/control region | Vacuum chamber: \~1 m; Antenna: \~10 m                |
| Comparison | L\_comparison | Baseline for phase agreement | Lab: \~1 m; Continental: \~10³ km; Galactic: \~10¹⁹ m |

Only L\_comparison enters the causal constraint. Advances in L\_source (better oscillators) or L\_apparatus (better interrogation) do not relax the realisability horizon.

***

### 3. Causal Efficiency as an Architectural Control Parameter

#### 3.1 Definition

For any clock architecture operating at integration time τ with comparison baseline L\_comparison, define the **causal efficiency**:

<p align="center"><span class="math">\eta(\tau) = \frac{L_{\text{comparison}}}{c \, \tau}</span></p>

| η Value        | Interpretation                                             | Regime        |
| -------------- | ---------------------------------------------------------- | ------------- |
| η = 1          | Causal limit: all integration time consumed by propagation | Boundary      |
| 0.01 < η < 0.5 | Propagation comparable to integration                      | Transition    |
| η ≪ 0.01       | Propagation negligible                                     | Deep interior |

Causal efficiency is not an optimization target by default. Different architectures may exhibit optimal noise performance at different values of η, determined by their dominant noise sources and comparison geometries.

#### 3.2 The η\_opt Hypothesis

**Hypothesis 3.1 (Optimal Causal Efficiency).**\
Each clock architecture exhibits a noise-regime transition at some characteristic efficiency η\_opt, determined by comparison geometry and dominant noise sources.

**Firewall:** The framework's core (the causal boundary and η as a geometry descriptor) remains valid regardless of whether η\_opt is confirmed for a given architecture. η\_opt strengthens predictive power if validated, but falsification does not weaken the boundary-condition analysis.

This hypothesis is testable: for a given architecture, measure stability as a function of integration time while holding L\_comparison fixed. If a transition in noise scaling correlates with a characteristic value of η, the hypothesis is supported. If no such correlation exists, the hypothesis is falsified for that architecture.

The experimental protocol is specified in §10.1.

***

#### Table 3 — Causal Efficiency by Architecture

| Architecture              | L\_comparison | τ (typical) | η = L/(cτ) | Regime        | Source     |
| ------------------------- | ------------- | ----------- | ---------- | ------------- | ---------- |
| Optical lattice (local)   | 1 m           | 10⁴ s       | 3×10⁻¹³    | Deep interior | Calculated |
| Optical network (1000 km) | 10⁶ m         | 10⁴ s       | 0.033      | Transition    | Calculated |
| VLBI baseline (6000 km)   | 6×10⁶ m       | 10⁴ s       | 0.20       | Transition    | Calculated |
| GNSS (orbital)            | 2×10⁷ m       | 10³ s       | 0.07       | Transition    | Calculated |
| PTA (inter-pulsar)        | 10¹⁶ m        | 10⁸ s       | 3×10⁻⁴     | Deep interior | Calculated |
| PTA (Earth-pulsar)        | 10¹⁹ m        | 10¹¹ s      | 0.3        | Transition    | Calculated |

**Note:** The "transition zone" (η \~ 0.01–0.5) is where comparison geometry may dominate noise budgets. This is where the η\_opt hypothesis makes its strongest predictions.

***

### 4. Clocks as Architectures, Not Devices

A clock, in this framework, is not an atomic transition or a cavity mode. It is a complete architecture comprising:

1. **Oscillator** — the frequency source
2. **Interrogation apparatus** — the local control system
3. **Comparison baseline** — the infrastructure for phase agreement

**No universal clock metric.** Two clocks cannot be ranked by a single figure of merit without specifying the comparison baseline and integration time.

**Comparison is constitutive.** A clock achieves its stated performance only relative to a specified comparison architecture. Stability numbers quoted without comparison context are incomplete.

**Modularity.** Oscillators, apparatus, and comparison links can be designed, characterized, and upgraded independently.

***

### 5. Agreement Requires Causal Closure

#### 5.1 Causal Closure Condition

Two oscillators at separation L achieve causal closure at integration time τ if and only if:

<p align="center"><span class="math">2L \le c \, \tau</span></p>

This is the bidirectional special case of Definition 2.1.

#### 5.2 Closure Requirements by Scale

| Architecture     | L (one-way) | τ for closure | Implication                   |
| ---------------- | ----------- | ------------- | ----------------------------- |
| Lab comparison   | 10 m        | 67 ns         | Instantaneous on human scales |
| City network     | 10 km       | 67 μs         | Sub-ms closure feasible       |
| Continental link | 1000 km     | 6.7 ms        | Limits short-τ comparison     |
| Intercontinental | 10,000 km   | 67 ms         | \~100 ms minimum epoch        |
| Earth-Moon       | 4×10⁸ m     | 2.7 s         | Multi-second epochs required  |
| Earth-pulsar     | 10¹⁹ m      | 10¹¹ s        | Decades for round-trip        |

***

### 6. Strongly-Coupled Clockwork (Operational Synthesis)

Modern precision timekeeping already operates as a coupled system, though this coupling is rarely made explicit.

#### Table 4 — Five-Gear Clockwork: Architecture Coupling

<table><thead><tr><th width="79.4879150390625">Gear</th><th>Systems</th><th width="139.2855224609375">L_comparison</th><th>τ Domain</th><th>Role</th><th>Couples To</th></tr></thead><tbody><tr><td>1</td><td>Optical clocks</td><td>≲10³ km</td><td>10³–10⁵ s</td><td>Highest stability</td><td>Gear 2 (steering)</td></tr><tr><td>2</td><td>Fountains/TAI</td><td>≲10⁴ km</td><td>10⁴–10⁶ s</td><td>SI realization</td><td>Gear 1, 3</td></tr><tr><td>3</td><td>GNSS</td><td>~2×10⁴ km</td><td>1–10⁴ s</td><td>Global distribution</td><td>Gear 2, 4</td></tr><tr><td>4</td><td>VLBI</td><td>~10⁴ km</td><td>10³–10⁵ s</td><td>Earth orientation</td><td>Gear 3, 5</td></tr><tr><td>5</td><td>Pulsar timing</td><td>10¹⁶–10¹⁹ m</td><td>10⁷–10⁹ s</td><td>Decadal stability</td><td>Gear 4, 1</td></tr></tbody></table>

**Coupling principle:** Each gear-train contributes stability in its native regime and accepts constraints from adjacent regimes.

#### 6.1 TA-OPT: Example Optical-Only Timescale (Conceptual)

**TA-OPT** — a timescale realized exclusively from optical clocks, with reliability-weighted steering, serving as a high-stability reference against which Earth-rotation deviations could be tracked.

TA-OPT is included as a design concept illustrating how the "gear" coupling could be expressed in a timescale. Implementation would require NMI coordination and BIPM/partner processes; this framework neither assumes nor prescribes adoption. The concept demonstrates that the framework is compatible with—but does not mandate—institutional innovation.

#### 6.2 Candor Weighting (Principle)

**Candor weighting (principle):** Clocks with statistically significant unexplained deviations are downweighted relative to demonstrated consistency. Specific update laws are implementation-dependent.

***

#### Provisional Example: 3-Node Fiber Network (Migrates to CSP)

_This worked example is provisional and will migrate to the CSP companion document. It is included here for immediate usability._

**Setup:** Three optical clocks (A, B, C) connected by stabilized fiber:

* A–B: 400 km
* B–C: 600 km
* A–C: 800 km (direct fiber, not routed through B)

**Question:** What is L\_path for verifying agreement among all three clocks?

**Analysis:**

| Verification Protocol | Required Paths | L\_path              |
| --------------------- | -------------- | -------------------- |
| Sequential (A→B→C→A)  | A–B, B–C, C–A  | 800 km (max segment) |
| Star via B            | A–B, B–C       | 600 km (max segment) |
| All-pairs direct      | A–B, B–C, A–C  | 800 km (max segment) |

**Compute η at τ = 10⁴ s:**

| Protocol   | L\_path | η     |
| ---------- | ------- | ----- |
| Sequential | 800 km  | 0.027 |
| Star via B | 600 km  | 0.020 |
| All-pairs  | 800 km  | 0.027 |

**Interpretation:** All protocols place this network in the transition zone (η \~ 0.02–0.03). The star topology minimizes L\_path but creates a single point of failure at B. The all-pairs topology provides redundancy at similar η cost.

**Key insight:** Topology choice affects L\_path, which affects η, which determines whether comparison geometry may dominate noise. This is the link between network design and the causal framework.

***

### 7. What This Framework Is — and Is Not

#### What This Framework Is

* A **design language** for reasoning about clock architectures in terms of comparison geometry
* A **boundary condition** (L\_comparison ≤ cτ) that constrains all phase-comparison operations
* An **architectural control parameter** (η) characterizing proximity to the causal limit
* A **synthesis** making explicit the coupling between existing timekeeping gear-trains
* **Orientation and program-shaping** for infrastructure planning

#### What This Framework Is Not

| Exclusion                                     | Clarification                              |
| --------------------------------------------- | ------------------------------------------ |
| Not a new physical theory                     | Causality assumed, not derived             |
| Not a replacement for Allan variance          | Noise characterization remains essential   |
| Not a redefinition of TAI/UTC/SI              | Existing standards retain authority        |
| Not a policy proposal                         | Governance decisions lie outside scope     |
| Not a claim of optimality                     | η\_opt is a hypothesis, not a prescription |
| Not a complete implementation spec            | Algorithms live in CSP companion           |
| Not a substitute for relativistic corrections | IERS conventions assumed                   |
| Not a legal traceability standard             | UTC/TAI/SI remain legal standards          |

***

### 8. Open Design Questions and Near-Term Frontiers

The value of this framework lies not in closing design questions, but in making them explicit, comparable, and discussable across institutions.

#### 8.1 Architecture: Topology and Layering (Explicitly Open)

**The framework does not prescribe a single network topology.** Different layers (local, regional, continental, planetary) may legitimately use different architectures.

The framework specifies boundary conditions for verification, not a canonical architecture. The optimal topology depends on scale, geography, application, and institutional context.

| Scale                 | Candidate Topologies               | Open Questions                      |
| --------------------- | ---------------------------------- | ----------------------------------- |
| Local (lab)           | Point-to-point                     | Comparison protocol optimization    |
| Regional (100 km)     | Star, ring, small-world            | How does topology affect η\_opt?    |
| Continental (1000 km) | Mesh, redundant paths, small-world | Resilience vs. complexity tradeoffs |
| Intercontinental      | Hybrid satellite+fiber             | Cost-performance optimization       |
| Planetary             | Hierarchical federation            | Governance interoperability         |

**Small-world topology as adaptability candidate:**

A promising candidate topology for adaptability is **small-world** (high local clustering with sparse long-range links), which can increase verification resilience while keeping deployment costs and operational complexity bounded. Small-world networks:

* add redundancy with limited added infrastructure,
* improve fault localization and re-routing,
* support gradual scaling from regional to continental networks.

Its performance should be evaluated in η-space and under failure-mode simulations. This framework does not claim small-world optimality; it identifies small-world as a candidate meriting systematic evaluation.

#### 8.2 Steering, Weighting, and Authority (Explicitly Deferred)

The framework separates _how clocks are compared_ from _how a timescale is steered_. Steering remains an institutional decision, informed—but not dictated—by verification geometry.

| Steering Aspect     | Current Practice       | Framework Contribution             |
| ------------------- | ---------------------- | ---------------------------------- |
| Weight assignment   | BIPM Circular T        | Makes comparison geometry explicit |
| Outlier detection   | Statistical thresholds | Candor weighting principle         |
| Authority hierarchy | NMI → BIPM → UTC       | No change proposed                 |

#### 8.3 Compatibility with Future Quantum Enhancements

**The framework does not rely on entanglement or quantum-enhanced links.** It is fully applicable with classical optical links and existing technologies.

Nothing in the framework assumes quantum-entangled links. Its emphasis on causal comparison geometry is compatible with future entanglement-assisted protocols, which may extend verification capabilities but do not remove causal limits.

***

### 9. Near-Term Impact

> **Near-term impact (next 3–5 years)**
>
> * Can be implemented using existing optical clocks, fibre links, satellite transfer, VLBI
> * Requires documentation and coordination, not new physics
> * Improves resilience and trust before performance ceilings are reached
> * Aligns with current funding and infrastructure cycles

***

#### Minimum Viable Adoption (6–12 months)

| Action                                                   | Effort | Output                               |
| -------------------------------------------------------- | ------ | ------------------------------------ |
| Publish η operating points for existing links            | Low    | Annotated comparison reports         |
| Document L\_path and "closure latency" in specifications | Low    | Updated technical documentation      |
| Run one pre-registered η\_opt scan on continental link   | Medium | Technical note (even if null result) |
| Compare ring vs. small-world on existing backbone        | Medium | Topology evaluation report           |

***

#### Table 5 — Implementation Readiness by Component

| Component          | Current Status             | Readiness | Required Action                       |
| ------------------ | -------------------------- | --------- | ------------------------------------- |
| Optical clocks     | Operational at NMIs        | Ready     | Coordinate comparison campaigns       |
| Fiber links        | Continental networks exist | Ready     | Document η at operating points        |
| Satellite transfer | GPS, Galileo, TWSTFT       | Ready     | Characterize geometry-dependent noise |
| VLBI               | Global network operational | Ready     | Cross-correlate with optical          |
| Pulsar timing      | IPTA ongoing               | Ready     | Establish optical-PTA cross-checks    |

#### 9.1 Actors and Entry Points

#### Table 6 — Actor Entry Points

| Actor                       | Entry Point            | Immediate Action                        | Timeline  |
| --------------------------- | ---------------------- | --------------------------------------- | --------- |
| NMIs (PTB, NIST, NPL, etc.) | Optical clock networks | Characterize η for existing links       | 6 months  |
| BIPM                        | Timescale algorithms   | Evaluate candor weighting in Circular T | 12 months |
| Space agencies (ESA, NASA)  | Satellite timing specs | Add L\_path to mission documentation    | 6 months  |
| Geodetic community          | VLBI/IERS              | Cross-validate with optical networks    | 12 months |
| Pulsar timing consortia     | IPTA                   | Report baseline-dependent systematics   | 12 months |

***

### 10. Testable Predictions (Non-Circular)

#### 10.1 Prediction: η\_opt Location for Optical Clock Networks

**Setup:** Optical clock network with fixed baseline L\_comparison = 1000 km.

**Protocol:** Measure modified Allan deviation while scanning τ from 10² s to 10⁵ s, covering η ∈ \[0.01, 0.5].

**Prediction:** A transition in noise scaling will occur at some characteristic η\_opt within this range.

**Falsification criterion:** If no changepoint is observed over the pre-registered interval, the η\_opt hypothesis is not supported for this architecture. (This does not falsify the framework's boundary-condition analysis.)

#### 10.2 Prediction: Architecture-Specific η\_opt

**Setup:** Compare optical network (1000 km) with VLBI (6000 km) at matched η values.

**Prediction:** Different η\_opt values, reflecting different noise sources.

**Falsification criterion:** Identical η\_opt despite different noise environments falsifies architecture-specificity.

#### 10.3 Prediction: PTA Geometry Insensitivity

**Setup:** Pulsar timing array with L\_comparison \~ 10¹⁶ m, τ \~ 10⁸ s.

**Prediction:** At η ≪ 0.01, stability is limited by timing noise, not comparison geometry.

**Falsification criterion:** _Systematic_ baseline dependence at fixed τ would require framework revision for this regime.

#### 10.4 Near-Term Evaluation: Ring vs. Small-World

**Setup:** Existing fiber backbone (e.g., 4-node continental network).

**Protocol:** Compare ring topology vs. small-world augmentation (one additional cross-link).

**Metrics:** Verification latency, fault isolation time, stability in η transition zone.

**Outcome:** Provides empirical data on topology-η interaction; informs §8.1 open questions.

#### 10.5 Non-Circularity Safeguards

* η\_opt values are measured, not assumed
* Noise sources are characterized independently
* Search intervals are pre-registered
* The framework predicts correlations; it does not define observables

***

### References

1. D. W. Allan, _Statistics of atomic frequency standards_, Proc. IEEE **54**, 221–230 (1966).
2. W. M. Itano et al., _Quantum projection noise_, Phys. Rev. A **47**, 3554 (1993).
3. C. W. Chou et al., _Optical clocks and relativity_, Science **329**, 1630–1633 (2010).
4. G. Petit & B. Luzum (Eds.), _IERS Conventions (2010)_, IERS Technical Note 36.
5. C. Lisdat et al., _A clock network for geodesy and fundamental science_, Nat. Commun. **7**, 12443 (2016).
6. P. Delva et al., _Test of special relativity using a fiber network of optical clocks_, PRL **118**, 221102 (2017).
7. S. M. Brewer et al., _²⁷Al⁺ quantum-logic clock_, PRL **123**, 033201 (2019).
8. E. Bothwell et al., _JILA SrI optical lattice clock_, Metrologia **59**, 065009 (2022).
9. W. McGrew et al., _Atomic clock performance enabling geodesy below the centimetre level_, Nature **564**, 87–90 (2018).
10. U. Huntemann et al., _Single-ion atomic clock with 3×10⁻¹⁸ systematic uncertainty_, PRL **116**, 063001 (2016).
11. G. Hobbs et al., _IPTA second data release_, MNRAS **491**, 5951 (2020).
12. NANOGrav Collaboration, _The NANOGrav 15-year gravitational-wave background_, ApJL **951**, L8 (2023).
13. J. Guéna et al., _Progress in atomic fountains at LNE-SYRTE_, IEEE TUFFC **59**, 391 (2012).
14. H. Schuh & D. Behrend, _VLBI: A fascinating technique_, J. Geodyn. **61**, 68 (2012).

***

### Document Metadata

<table><thead><tr><th width="245.8394775390625">Field</th><th>Value</th></tr></thead><tbody><tr><td>Version</td><td>0.6.0</td></tr><tr><td>Status</td><td>Stable conceptual layer; operational companions forthcoming</td></tr><tr><td>Canonical DOI</td><td>[TBD]</td></tr><tr><td>Citation</td><td>Warring, U. (2025). <em>Causal Clock Unification</em>.</td></tr><tr><td>Companion documents</td><td>CSP (Causal Steering Protocols) — in development</td></tr></tbody></table>

#### Relationship to Companion Documents

**Firewall Statement:** This document (CCUF) defines the conceptual framework. CSP and implementation notes may evolve without requiring CCUF revision. If companion development reveals conceptual gaps, those are addressed through explicit CCUF amendments.

***

_The framework is designed to guide near-term infrastructure decisions under existing technical constraints, while remaining compatible with future advances._

***

### Version History

<table><thead><tr><th width="94.89373779296875">Version</th><th width="109.36566162109375">Date</th><th width="103.16363525390625">Format</th><th>Summary</th></tr></thead><tbody><tr><td>v0.0.1</td><td>2025-12-12</td><td>Internal</td><td>Initial formulation of causal boundary concept linking clock period and effective size. Exploratory scope; definitions not yet fixed.</td></tr><tr><td>v0.0.2</td><td>2025-12-12</td><td>GitBook</td><td>Formalized framework as a boundary-condition design theory. Introduced strict separation of L_source, L_apparatus, and L_comparison. Defined causal efficiency parameter η(τ). Demoted Planck scale to dimensional endpoint only. Language tightened for falsifiability and GitBook presentation.</td></tr><tr><td>v0.1.2</td><td>2025-12-14</td><td>GitBook</td><td>Review-ready structural completion. Added: Executive Orientation (§0) with τ-coverage figure; explicit scope exclusions; Five-Gear Clockwork synthesis (§6) with TA-OPT definition; Testable Predictions (§8) with falsification criteria; Appendix A with protective preamble. All section openers standardized. Forward anchor from §3.2 to §8.1 installed.</td></tr><tr><td>v0.1.5</td><td>2025-12-15</td><td>GitBook</td><td>Table 0 added. Definition 2.1 rewritten for topology-safety (L_path, τ notation). η(τ) formula corrected. Hypothesis 3.1 numbered. §5.2 PTA worked example added. §6.3 candor weighting reduced to principle-only with CSP reference. §7 boundary list expanded (implementation, relativistic, legal exclusions). §8.1 falsification reframed as pre-registered interval criterion without numeric η_opt. §8.3 "systematic" qualifier added. Appendix A typo fixed, notation normalized. Document Metadata and firewall statement added.</td></tr><tr><td>v0.5.0</td><td>2025-12-15</td><td>GitBook</td><td>Action-guiding framework with parameter tables, open design questions, near-term impact framing. Figures replaced with comprehensive tables.</td></tr><tr><td>v0.6.0</td><td>2025-12-15</td><td>GitBook</td><td><strong>Trust repairs (version/status, η_opt firewall, TA-OPT reframe). Quickstart box. MVA checklist. Provisional 3-node example. Auditable Table 1 with sources. PTA footnote. Small-world topology. Figure 1 restored. Ring vs. small-world evaluation hook.</strong></td></tr></tbody></table>
