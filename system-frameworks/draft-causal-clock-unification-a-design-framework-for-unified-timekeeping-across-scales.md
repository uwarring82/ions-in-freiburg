---
description: Timekeeping as Causal Geometry
---

# \[DRAFT] Causal Clock Unification — A Design Framework for Unified Timekeeping Across Scales

{% hint style="info" %}
**Author:** U. Warring\
**Affiliation:** Institute of Physics, University of Freiburg\
**Version:** 1.0-rc\
**Last updated:** 2025-12-16\
**License:** CC BY 4.0\
\
**Status:** Citation-stable conceptual layer\
**Companion:** CSP (Causal Steering Protocols) — operational details forthcoming\
\
**Disclaimer** — _This document defines a boundary-condition design framework. Its authority derives from transparency, not finality._
{% endhint %}

***

### 0. Orientation

Modern timekeeping operates across integration times spanning more than fifteen orders of magnitude. No single oscillator covers this range. Clocks that agree at one timescale may diverge at another, not because they fail, but because their comparison geometries impose different causal constraints.

This framework introduces a single architectural lens: the causal boundary condition governing phase comparison. It does not replace existing metrology tools, redefine time standards, or propose new physics. It offers a design language for reasoning about why different clock architectures exhibit different stability regimes.

**How to read this document.** Figure 1 provides visual orientation across architectures. Table 1 provides quantitative parameters with sources. Each section states its structural contribution. Hypotheses are labeled; predictions are testable. Open questions are marked as such.

**Document structure.** Sections 1–4 constitute the citation-stable core. Sections 5–9 address synthesis, open questions, and near-term applications; these may evolve in future versions.

***

### Figure 1 — Five-Gear Clockwork Across τ and η

```
                                    CAUSAL EFFICIENCY η = L/(cτ)
                    ←— Deep Interior (η≪0.01) —|— Transition (0.01–0.5) —|— Moderate (η~1) —→

    10⁻² s  ┤                                   
            │  ┌─────────────┐                  
    10⁰ s   ┤  │   OPTICAL   │←————————————————————————————————————┐
            │  │   CLOCKS    │  steering                           │
    10² s   ┤  │  (Gear 1)   │————————┐                            │
            │  └─────────────┘        │                            │
    10³ s   ┤         ↑               ↓                            │
            │         │        ┌─────────────┐    ┌─────────────┐  │
τ   10⁴ s   ┤    frequency     │  FOUNTAINS  │    │    GNSS     │  │ decadal
            │    comparison    │   + TAI     │←——→│  (Gear 3)   │  │ stability
    10⁵ s   ┤          │       │  (Gear 2)   │    └──────┬──────┘  │ check
            │          │       └──────┬──────┘           │         │
    10⁶ s   ┤          │              │                  │         │
            │          │              │  Earth           ↓         │
    10⁷ s   ┤          │              │  orient.  ┌─────────────┐  │
            │          │              └——————————→│    VLBI     │  │
    10⁸ s   ┤          │                          │  (Gear 4)   │  │
            │          │                          └──────┬──────┘  │
    10⁹ s   ┤          │                                 │         │
            │          │           long-baseline         ↓         │
    10¹⁰ s  ┤          │           correlation    ┌─────────────┐  │
            │          └←—————————————————————————│   PULSAR    │——┘
    10¹¹ s  ┤                                     │   TIMING    │
            │                                     │  (Gear 5)   │
                                                  └─────────────┘

            ├─────────────────┼─────────────────┼─────────────────┤
           10⁰              10³               10⁶              10⁹   L_comparison (km)
```

**Caption:** The five gear-trains of precision timekeeping across integration time (τ) and comparison baseline (L\_comparison), with causal efficiency regimes indicated. Arrows show phase-information coupling. **This is a design lens for reasoning about comparison geometry, not an architecture mandate.** VLBI and PTA are included to demonstrate that the causal constraint spans the full range; this structural inclusion does not imply that operational integration is necessary or beneficial. Data ranges correspond to Table 1.

***

### Quickstart: Compute η and Classify

| Step         | Action                                                                      |
| ------------ | --------------------------------------------------------------------------- |
| 1. Inputs    | Determine L\_comparison (or L\_path for complex topologies) and operating τ |
| 2. Compute   | η = L\_comparison / (c × τ)                                                 |
| 3. Classify  | Deep interior (η ≪ 0.01) · Transition (0.01–0.5) · Boundary (η \~ 1)        |
| 4. Interpret | See recommended focus below                                                 |

| η Range  | Regime        | Primary Constraint     | Recommended Focus              |
| -------- | ------------- | ---------------------- | ------------------------------ |
| η \~ 1   | Boundary      | Comparison geometry    | Topology, L\_path optimization |
| 0.01–0.5 | Transition    | Mixed                  | η\_opt characterization (§9.1) |
| η ≪ 0.01 | Deep interior | Oscillator/systematics | Not comparison-limited         |

***

## CORE FRAMEWORK (Citation-Stable)

**The following four sections constitute the immutable core of CCUF. They are frozen for citation and will not change in future versions.**

***

### 1. The Causal Boundary as a Design Constraint

Every comparison of two oscillators requires information exchange. The propagation time along the longest required signal path sets an irreducible lower bound on the timescale at which their phases can be correlated.

#### 1.1 The Realisability Horizon

**Definition 1.1 (Realisability Horizon).**\
For any phase comparison operation requiring causal information exchange over a longest required signal path L\_path, the integration time must satisfy:

\$$\tau \ge \frac{L\_{\text{path\}}}{c}\$$

For mutual verification (bidirectional / round-trip causal closure):

\$$\tau \ge \frac{2 L\_{\text{path\}}}{c}\$$

L\_path reduces to L\_comparison in direct two-node comparisons; for star/mesh topologies, L\_path is the maximum required path for the chosen protocol.

This inequality is a **boundary condition**, not a dynamical law. It does not describe how clocks evolve; it describes which comparisons are possible. Any architecture proposing agreement over baseline L in time τ < L/c violates causality. No oscillator improvement, no signal processing technique, and no statistical method can circumvent this bound.

#### 1.2 Three Orthogonal Length Scales

Clocks involve three distinct spatial scales that must not be conflated:

| Scale      | Symbol        | Definition                   | Examples                                                         |
| ---------- | ------------- | ---------------------------- | ---------------------------------------------------------------- |
| Source     | L\_source     | Spatial extent of oscillator | Ion trap: \~1 mm; Lattice: \~1 cm; Pulsar magnetosphere: \~10 km |
| Apparatus  | L\_apparatus  | Interrogation/control region | Vacuum chamber: \~1 m; Radio antenna: \~10 m                     |
| Comparison | L\_comparison | Baseline for phase agreement | Lab: \~1 m; Continental: \~10³ km; Galactic: \~10¹⁹ m            |

Only L\_comparison enters the causal constraint. Advances in L\_source (better oscillators) or L\_apparatus (better interrogation) do not relax the realisability horizon.

***

### 2. Causal Efficiency as an Architectural Control Parameter

#### 2.1 Definition

For any clock architecture operating at integration time τ with comparison baseline L\_comparison, define the **causal efficiency**:

\$$\eta(\tau) = \frac{L\_{\text{comparison\}}}{c , \tau}\$$

| η Value        | Interpretation                                             | Regime        |
| -------------- | ---------------------------------------------------------- | ------------- |
| η = 1          | Causal limit: all integration time consumed by propagation | Boundary      |
| 0.01 < η < 0.5 | Propagation significant relative to integration            | Transition    |
| η ≪ 0.01       | Propagation negligible                                     | Deep interior |

Causal efficiency is not an optimization target. Different architectures may exhibit optimal noise performance at different values of η, determined by their dominant noise sources and comparison geometries.

#### 2.2 The η\_opt Hypothesis

**Hypothesis 2.1 (Optimal Causal Efficiency).**\
Each clock architecture exhibits a noise-regime transition at some characteristic efficiency η\_opt, determined by comparison geometry and dominant noise sources.

**Firewall:** The causal boundary condition (Definition 1.1) remains valid independent of whether η\_opt is confirmed for any architecture. Confirmation of η\_opt adds predictive resolution; non-confirmation does not invalidate the boundary-condition analysis.

This hypothesis is testable: for a given architecture, measure stability as a function of τ while holding L\_comparison fixed. If a transition in noise scaling correlates with a characteristic η value, the hypothesis is supported. If no such transition is observed, the hypothesis is falsified for that architecture.

The experimental protocol is specified in §9.1.

***

### 3. Clocks as Architectures, Not Devices

A clock, in this framework, is not an atomic transition or a cavity mode. It is a complete architecture comprising:

1. **Oscillator** — the frequency source
2. **Interrogation apparatus** — the local control system
3. **Comparison baseline** — the infrastructure for phase agreement

**No universal clock metric.** Two clocks cannot be ranked by a single figure of merit without specifying L\_comparison and τ.

**Comparison is constitutive.** A clock achieves its stated performance only relative to a specified comparison architecture. Stability numbers quoted without comparison context are incomplete.

**Modularity.** Oscillators, apparatus, and comparison links can be designed and upgraded independently. Improvement in one component improves the architecture only if no other component becomes limiting.

***

### 4. Agreement Requires Causal Closure

#### 4.1 Closure Condition

Two oscillators at separation L achieve causal closure at integration time τ if and only if:

\$$2L \le c , \tau\$$

This is the bidirectional special case of Definition 1.1.

Without causal closure, clocks may be individually stable but cannot verify mutual agreement. They run independently, not in concert.

#### 4.2 Closure Requirements by Scale

| Scale            | L (one-way) | τ for closure | Implication                   |
| ---------------- | ----------- | ------------- | ----------------------------- |
| Laboratory       | 10 m        | 67 ns         | Instantaneous on human scales |
| Metropolitan     | 10 km       | 67 μs         | Sub-ms closure feasible       |
| Continental      | 1000 km     | 6.7 ms        | Limits short-τ comparison     |
| Intercontinental | 10,000 km   | 67 ms         | \~100 ms minimum epoch        |
| Earth–Moon       | 4×10⁸ m     | 2.7 s         | Multi-second epochs           |
| Earth–pulsar     | 10¹⁹ m      | 10¹¹ s        | Decades for round-trip        |

***

## SYNTHESIS AND APPLICATIONS

**The following sections address operational synthesis, open questions, and near-term applications. They may evolve in future versions while the core (§1–4) remains stable.**

***

### 5. Strongly-Coupled Clockwork (Operational Synthesis)

Modern precision timekeeping operates as a coupled system, though this coupling is rarely explicit. The framework identifies five principal gear-trains spanning fifteen orders of magnitude in baseline and integration time.

#### Table 1 — Clock Architectures: Parameters and Sources

| Architecture            | L\_comparison | τ\_min   | Typical τ | η Range     | Dominant Noise     | σ\_y(τ)           | Source |
| ----------------------- | ------------- | -------- | --------- | ----------- | ------------------ | ----------------- | ------ |
| Optical lattice (local) | \~1 m         | \~3 ns   | 1–10⁴ s   | 10⁻¹²–10⁻⁸  | Quantum projection | \~1×10⁻¹⁸ @ 10⁴ s | \[1]   |
| Optical ion (local)     | \~1 mm        | \~3 ps   | 1–10⁴ s   | 10⁻¹⁵–10⁻¹¹ | Quantum projection | \~1×10⁻¹⁸ @ 10⁴ s | \[2]   |
| Optical network         | 10²–10³ km    | 0.3–3 ms | 10³–10⁵ s | 10⁻²–10⁻¹   | Fiber phase noise  | \~1×10⁻¹⁸ @ 10⁴ s | \[3]   |
| Microwave fountain      | \~10⁴ km      | \~30 ms  | 10⁴–10⁶ s | 10⁻³–10⁻²   | Dick effect        | \~1×10⁻¹⁶ @ 10⁵ s | \[4]   |
| Hydrogen maser          | \~10⁴ km      | \~30 ms  | 10²–10⁵ s | 10⁻³–10⁻¹   | Cavity drift       | \~1×10⁻¹⁵ @ 10⁴ s | \[5]   |
| GNSS                    | \~2×10⁴ km    | \~70 ms  | 1–10⁴ s   | 10⁻²–10⁰    | Ionosphere         | \~1×10⁻¹⁴ @ 10³ s | \[6]   |
| TWSTFT                  | \~10⁴ km      | \~30 ms  | 10²–10⁵ s | 10⁻³–10⁻¹   | Troposphere        | \~5×10⁻¹⁶ @ 10⁴ s | \[7]   |
| VLBI                    | 6–10×10³ km   | 20–30 ms | 10³–10⁵ s | 10⁻²–10⁻¹   | Troposphere        | \~1×10⁻¹⁵ @ 10⁴ s | \[8]   |
| Pulsar timing†          | \~10¹⁹ m      | \~10¹¹ s | 10⁷–10⁹ s | ≪10⁻²       | Timing noise, ISM  | \~1×10⁻¹⁵ @ 10⁸ s | \[9]   |
| PTA correlation†        | \~10¹⁶ m      | \~10⁸ s  | 10⁸–10⁹ s | 0.03–0.3    | Red noise          | \~1×10⁻¹⁵ @ 10⁸ s | \[10]  |

**Table 1 Sources:**\
\[1] Bothwell et al. 2022, Metrologia 59:065009\
\[2] Brewer et al. 2019, PRL 123:033201\
\[3] Lisdat et al. 2016, Nat. Commun. 7:12443\
\[4] Guéna et al. 2012, IEEE TUFFC 59:391\
\[5] Parker 2012, Metrologia 49:S86\
\[6] Petit & Jiang 2008, Metrologia 45:S35\
\[7] Fujieda et al. 2014, Metrologia 51:253\
\[8] Schuh & Behrend 2012, J. Geodyn. 61:68\
\[9] Hobbs et al. 2020, MNRAS 491:5951\
\[10] NANOGrav 2023, ApJL 951:L8

**Notes:**

* σ\_y(τ) values are representative of demonstrated performance; actual values vary by implementation
* ISM = interstellar medium scattering/dispersion

†**PTA semantics:** For single-pulsar timing, L\_comparison is Earth–pulsar distance. For array correlation (gravitational-wave detection), L\_comparison represents inter-pulsar angular separation projected onto the gravitational-wave wavelength; \~10¹⁶ m is representative for nHz-frequency spatial correlations. See §9.3 for baseline-dependence predictions.

***

#### Table 2 — Five-Gear Clockwork: Coupling Structure

| Gear | Systems        | L\_comparison | τ Domain  | Role                | Couples To |
| ---- | -------------- | ------------- | --------- | ------------------- | ---------- |
| 1    | Optical clocks | ≲10³ km       | 10³–10⁵ s | Highest stability   | Gear 2     |
| 2    | Fountains/TAI  | ≲10⁴ km       | 10⁴–10⁶ s | SI realization      | Gear 1, 3  |
| 3    | GNSS           | \~2×10⁴ km    | 1–10⁴ s   | Global distribution | Gear 2, 4  |
| 4    | VLBI           | \~10⁴ km      | 10³–10⁵ s | Earth orientation   | Gear 3, 5  |
| 5    | Pulsar timing  | 10¹⁶–10¹⁹ m   | 10⁷–10⁹ s | Decadal stability   | Gear 4, 1  |

**Structural note:** VLBI and PTA systems are included to demonstrate that the causal constraint spans the full range of baselines and integration times. This structural inclusion does not imply that operational integration across all gears is necessary or beneficial for any particular application.

#### 5.1 TA-OPT: Architectural Example

**TA-OPT** — a timescale realized exclusively from optical clocks, serving as a high-stability reference.

TA-OPT is introduced solely to illustrate how gear coupling could be expressed in a timescale architecture. No operational recommendation or institutional implication is intended or implied. Implementation would require NMI coordination and BIPM processes that lie outside this framework's scope.

#### 5.2 Candor Weighting (Principle)

**Candor weighting:** Clocks with statistically significant unexplained deviations are downweighted relative to demonstrated consistency.

This is a design principle. Specific update laws are implementation-dependent and belong in CSP.

***

### 6. What This Framework Is — and Is Not

This framework defines a conceptual design layer. Algorithms, operational protocols, and governance mechanisms are explicitly out of scope.

#### What This Framework Is

* A **design language** for reasoning about clock architectures in terms of comparison geometry
* A **boundary condition** (L\_comparison ≤ cτ) constraining all phase-comparison operations
* An **architectural control parameter** (η) characterizing proximity to the causal limit
* A **synthesis** making explicit the coupling between existing timekeeping systems

#### What This Framework Is Not

| Exclusion                                     | Clarification                              |
| --------------------------------------------- | ------------------------------------------ |
| Not a new physical theory                     | Causality assumed, not derived             |
| Not a replacement for Allan variance          | Noise characterization remains essential   |
| Not a redefinition of TAI/UTC/SI              | Existing standards retain authority        |
| Not a policy proposal                         | Governance decisions lie outside scope     |
| Not a claim of optimality                     | η\_opt is a hypothesis, not a prescription |
| Not an implementation specification           | Algorithms belong in CSP                   |
| Not a substitute for relativistic corrections | IERS conventions assumed                   |

***

### 7. Open Design Questions

The framework's value lies in making questions explicit and comparable, not in closing them.

#### 7.1 Architecture: Topology and Layering

The framework does not prescribe a single network topology. Different scales may legitimately use different architectures.

| Scale                 | Candidate Topologies    | Open Questions              |
| --------------------- | ----------------------- | --------------------------- |
| Local (lab)           | Point-to-point          | Protocol optimization       |
| Regional (100 km)     | Star, ring              | Topology effect on η\_opt?  |
| Continental (1000 km) | Mesh, small-world       | Resilience vs. complexity   |
| Intercontinental      | Hybrid satellite+fiber  | Cost-performance tradeoffs  |
| Planetary             | Hierarchical federation | Governance interoperability |

**Small-world topology** (high local clustering with sparse long-range links) is one candidate meriting systematic evaluation for continental-scale networks: it may offer resilience with bounded complexity. This framework identifies it as a candidate for testing, not as an optimal solution.

#### 7.2 Steering, Weighting, and Authority

The framework separates _how clocks are compared_ from _how a timescale is steered_. Steering remains an institutional decision, informed—but not dictated—by verification geometry.

#### 7.3 Compatibility with Future Quantum Enhancements

This framework does not rely on entanglement or quantum-enhanced links. It is fully applicable with classical optical links and existing technologies.

Quantum correlations may modify comparison strategies without violating causal bounds; such effects are deferred to future work.

***

### 8. Near-Term Impact

> **Near-term impact (next 3–5 years)**
>
> * Can be implemented using existing clocks, fiber links, satellite transfer, VLBI
> * Requires documentation and coordination, not new physics
> * Aligns with current funding and infrastructure cycles

#### Minimum Viable Adoption (6–12 months)

| Action                             | Effort | Output                            |
| ---------------------------------- | ------ | --------------------------------- |
| Publish η for existing links       | Low    | Annotated comparison reports      |
| Document L\_path in specifications | Low    | Updated technical documentation   |
| Run one pre-registered η\_opt scan | Medium | Technical note (even null result) |

#### Table 3 — Actor Entry Points

| Actor                       | Entry Point          | Immediate Action                      |
| --------------------------- | -------------------- | ------------------------------------- |
| NMIs (PTB, NIST, NPL, etc.) | Optical networks     | Document η at operating points        |
| BIPM                        | Timescale algorithms | Evaluate candor weighting principle   |
| Space agencies              | Satellite timing     | Add L\_path to mission specs          |
| VLBI community              | IVS/IERS             | Cross-validate with optical links     |
| PTA consortia               | IPTA/NANOGrav        | Report baseline-dependent systematics |

***

### 9. Testable Predictions (Non-Circular)

#### 9.1 Prediction: η\_opt Location for Optical Clock Networks

**Setup:** Fixed baseline L\_comparison = 1000 km.

**Protocol:** Measure modified Allan deviation while scanning τ from 10² s to 10⁵ s, covering η ∈ \[0.01, 0.5].

**Prediction:** A transition in noise scaling occurs at some characteristic η\_opt within this range.

**Falsification criterion:** No changepoint observed over the pre-registered interval. (This does not invalidate the boundary-condition core; see Firewall in §2.2.)

#### 9.2 Prediction: Architecture-Specific η\_opt

**Setup:** Optical network (1000 km baseline) vs. VLBI (6000 km baseline) at matched η values.

**Prediction:** Different η\_opt values reflecting different dominant noise sources (fiber phase noise vs. tropospheric delay).

**Falsification criterion:** Identical η\_opt despite different noise environments falsifies architecture-specificity.

#### 9.3 Prediction: PTA Geometry Insensitivity

**Setup:** Pulsar timing array with L\_comparison \~ 10¹⁶ m, τ \~ 10⁸ s (η ≪ 0.01 for some configurations).

**Prediction:** At deep-interior η values, stability is limited by intrinsic timing noise and ISM effects, not comparison geometry.

**Falsification criterion:** _Systematic_ baseline dependence at fixed τ would require revision of the geometry-insensitivity prediction for this regime.

#### 9.4 Non-Circularity Safeguards

* η\_opt values are measured, not assumed
* Noise sources are characterized independently of the framework
* Search intervals are pre-registered to prevent post-hoc adjustment
* The framework predicts correlations; it does not define the observables

***

### References

1. D. W. Allan, _Statistics of atomic frequency standards_, Proc. IEEE **54**, 221–230 (1966).
2. C. Lisdat et al., _A clock network for geodesy and fundamental science_, Nat. Commun. **7**, 12443 (2016).
3. P. Delva et al., _Test of special relativity using a fiber network of optical clocks_, PRL **118**, 221102 (2017).
4. G. Petit & B. Luzum (Eds.), _IERS Conventions (2010)_, IERS Technical Note 36.
5. S. M. Brewer et al., _²⁷Al⁺ quantum-logic clock_, PRL **123**, 033201 (2019).
6. E. Bothwell et al., _JILA SrI optical lattice clock_, Metrologia **59**, 065009 (2022).
7. W. McGrew et al., _Atomic clock performance enabling geodesy below the centimetre level_, Nature **564**, 87–90 (2018).
8. G. Hobbs et al., _The International Pulsar Timing Array: second data release_, MNRAS **491**, 5951 (2020).
9. NANOGrav Collaboration, _The NANOGrav 15-year gravitational-wave background_, ApJL **951**, L8 (2023).
10. H. Schuh & D. Behrend, _VLBI: A fascinating technique for geodesy and astrometry_, J. Geodyn. **61**, 68 (2012).
11. J. Guéna et al., _Progress in atomic fountains at LNE-SYRTE_, IEEE TUFFC **59**, 391 (2012).
12. M. Fujieda et al., _Carrier-phase two-way satellite frequency transfer_, Metrologia **51**, 253 (2014).

***

### Document Metadata

| Field             | Value                                                          |
| ----------------- | -------------------------------------------------------------- |
| Version           | 1.0-rc                                                         |
| Status            | Citation-stable conceptual layer                               |
| Core sections     | §1–4 (frozen)                                                  |
| Evolving sections | §5–9 (may be revised)                                          |
| Canonical DOI     | \[TBD]                                                         |
| Citation          | Warring, U. (2025). _Causal Clock Unification_ (v1.0-rc).      |
| Companion         | CSP (Causal Steering Protocols) — operational details separate |

#### Relationship to Companion Documents

**Firewall Statement:** This document (CCUF) defines the conceptual framework. The core (§1–4) is frozen for citation. CSP and implementation notes may evolve without requiring core revision. If companion development reveals gaps in the core, amendments require a new major version.

***

### Version History

<table><thead><tr><th width="110.03338623046875">Version</th><th width="136.52630615234375">Date</th><th>Summary</th></tr></thead><tbody><tr><td>0.1–0.3</td><td>2025-12–14</td><td>Initial formulation through Five-Gear synthesis</td></tr><tr><td>0.5</td><td>2025-12-15</td><td>Parameter tables, open questions, near-term impact</td></tr><tr><td>0.6</td><td>2025-12-15</td><td>Trust repairs, quickstart, provisional example, small-world</td></tr><tr><td><strong>1.0-rc</strong></td><td><strong>2025-12-16</strong></td><td><strong>Merged structure: citation-stable core (§1–4) separated from evolving synthesis (§5–9). Restrained VLBI/PTA framing. Auditable Table 1 with sources. TA-OPT as architectural example only. Retained actionability elements (Quickstart, MVA, actor entry points).</strong></td></tr></tbody></table>

***

_This framework defines a conceptual design layer. Algorithms, operational protocols, and governance mechanisms are explicitly out of scope._
