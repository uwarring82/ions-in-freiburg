---
description: Timekeeping as Causal Geometry
---

# Causal Clock Unification — A Design Framework for Unified Timekeeping Across Scales

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

<table><thead><tr><th width="148.50634765625">Step</th><th>Action</th></tr></thead><tbody><tr><td>1. Inputs</td><td>Determine L_comparison (or L_path for complex topologies) and operating τ</td></tr><tr><td>2. Compute</td><td>η = L_comparison / (c × τ)</td></tr><tr><td>3. Classify</td><td>Deep interior (η ≪ 0.01) · Transition (0.01–0.5) · Boundary (η ~ 1)</td></tr><tr><td>4. Interpret</td><td>See recommended focus below</td></tr></tbody></table>

<table><thead><tr><th width="113.31390380859375">η Range</th><th width="123.32952880859375">Regime</th><th width="196.5447998046875">Primary Constraint</th><th>Recommended Focus</th></tr></thead><tbody><tr><td>η ~ 1</td><td>Boundary</td><td>Comparison geometry</td><td>Topology, L_path optimization</td></tr><tr><td>0.01–0.5</td><td>Transition</td><td>Mixed</td><td>η_opt characterization (§9.1)</td></tr><tr><td>η ≪ 0.01</td><td>Deep interior</td><td>Oscillator/systematics</td><td>Not comparison-limited</td></tr></tbody></table>

***

## CORE FRAMEWORK (Citation-Stable)

**The following four sections constitute the immutable core of CCUF. They are frozen for citation and will not change in future versions.**

***

### 1. The Causal Boundary as a Design Constraint

Every comparison of two oscillators requires information exchange. The propagation time along the longest required signal path sets an irreducible lower bound on the timescale at which their phases can be correlated.

#### 1.1 The Realisability Horizon

**Definition 1.1 (Realisability Horizon).**\
For any phase comparison operation requiring causal information exchange over a longest required signal path L\_path, the integration time must satisfy:

<p align="center"><span class="math">\tau \ge \frac{L_{\text{path}}}{c}</span></p>

For mutual verification (bidirectional / round-trip causal closure):

<p align="center"><span class="math">\tau \ge \frac{2 L_{\text{path}}}{c}</span></p>

L\_path reduces to L\_comparison in direct two-node comparisons; for star/mesh topologies, L\_path is the maximum required path for the chosen protocol.

This inequality is a **boundary condition**, not a dynamical law. It does not describe how clocks evolve; it describes which comparisons are possible. Any architecture proposing agreement over baseline L in time τ < L/c violates causality. No oscillator improvement, no signal processing technique, and no statistical method can circumvent this bound.

#### 1.2 Three Orthogonal Length Scales

Clocks involve three distinct spatial scales that must not be conflated:

<table><thead><tr><th width="122.5823974609375">Scale</th><th width="134.360107421875">Symbol</th><th width="208.639892578125">Definition</th><th>Examples</th></tr></thead><tbody><tr><td>Source</td><td>L_source</td><td>Spatial extent of oscillator</td><td>Ion trap: ~1 mm; Lattice: ~1 cm; Pulsar magnetosphere: ~10 km</td></tr><tr><td>Apparatus</td><td>L_apparatus</td><td>Interrogation/control region</td><td>Vacuum chamber: ~1 m; Radio antenna: ~10 m</td></tr><tr><td>Comparison</td><td>L_comparison</td><td>Baseline for phase agreement</td><td>Lab: ~1 m; Continental: ~10³ km; Galactic: ~10¹⁹ m</td></tr></tbody></table>

Only L\_comparison enters the causal constraint. Advances in L\_source (better oscillators) or L\_apparatus (better interrogation) do not relax the realisability horizon.

***

### 2. Causal Efficiency as an Architectural Control Parameter

#### 2.1 Definition

For any clock architecture operating at integration time τ with comparison baseline L\_comparison, define the **causal efficiency**:

<p align="center"><span class="math">\eta(\tau) = \frac{L_{\text{comparison}}}{c \, \tau}</span></p>

<table><thead><tr><th width="133.59521484375">η Value</th><th width="474.43603515625">Interpretation</th><th>Regime</th></tr></thead><tbody><tr><td>η = 1</td><td>Causal limit: all integration time consumed by propagation</td><td>Boundary</td></tr><tr><td>0.01 &#x3C; η &#x3C; 0.5</td><td>Propagation significant relative to integration</td><td>Transition</td></tr><tr><td>η ≪ 0.01</td><td>Propagation negligible</td><td>Deep interior</td></tr></tbody></table>

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

> **Reader orientation.** In this framework, σᵧ(τ) denotes the measured stability of a _complete clock architecture_ at averaging time τ, while η(τ) characterises how close that architecture operates to the causal limit imposed by its comparison geometry.\
> \
> σᵧ(τ) answers _“how stable?”_\
> η(τ) answers _“under what geometric constraints?”_\
> \
> Both are required for architectural reasoning; neither replaces the other.

***

### 4. Agreement Requires Causal Closure

#### 4.1 Closure Condition

Two oscillators at separation L achieve causal closure at integration time τ if and only if:

<p align="center"><span class="math">2L \le c\, \tau</span></p>

This is the bidirectional special case of Definition 1.1.

Without causal closure, clocks may be individually stable but cannot verify mutual agreement. They run independently, not in concert.

#### 4.2 Closure Requirements by Scale

<table><thead><tr><th width="145.116455078125">Scale</th><th width="121.36785888671875">L (one-way)</th><th width="129.4176025390625">τ for closure</th><th>Implication</th></tr></thead><tbody><tr><td>Laboratory</td><td>10 m</td><td>67 ns</td><td>Instantaneous on human scales</td></tr><tr><td>Metropolitan</td><td>10 km</td><td>67 μs</td><td>Sub-ms closure feasible</td></tr><tr><td>Continental</td><td>1000 km</td><td>6.7 ms</td><td>Limits short-τ comparison</td></tr><tr><td>Intercontinental</td><td>10,000 km</td><td>67 ms</td><td>~100 ms minimum epoch</td></tr><tr><td>Earth–Moon</td><td>4×10⁸ m</td><td>2.7 s</td><td>Multi-second epochs</td></tr><tr><td>Earth–pulsar</td><td>10¹⁹ m</td><td>10¹¹ s</td><td>Decades for round-trip</td></tr></tbody></table>

***

## SYNTHESIS AND APPLICATIONS

**The following sections address operational synthesis, open questions, and near-term applications. They may evolve in future versions while the core (§1–4) remains stable.**

***

### 5. Strongly-Coupled Clockwork (Operational Synthesis)

Modern precision timekeeping operates as a coupled system, though this coupling is rarely explicit. The framework identifies five principal gear-trains spanning fifteen orders of magnitude in baseline and integration time.

#### Table 1 — Clock Architectures: Parameters and Sources

<table><thead><tr><th width="128.10296630859375">Architecture</th><th width="138.91973876953125">L_comparison</th><th width="100.546142578125">τ_min</th><th width="106.18896484375">Typical τ</th><th width="102.7442626953125">η Range</th><th width="150.03125">Dominant Noise</th><th width="140.9189453125">σ_y(τ)</th><th>Source</th></tr></thead><tbody><tr><td>Optical lattice (local)</td><td>~1 m</td><td>~3 ns</td><td>1–10⁴ s</td><td>10⁻¹²–10⁻⁸</td><td>Quantum projection</td><td>~1×10⁻¹⁸ @ 10⁴ s</td><td>[1]</td></tr><tr><td>Optical ion (local)</td><td>~1 mm</td><td>~3 ps</td><td>1–10⁴ s</td><td>10⁻¹⁵–10⁻¹¹</td><td>Quantum projection</td><td>~1×10⁻¹⁸ @ 10⁴ s</td><td>[2]</td></tr><tr><td>Optical network</td><td>10²–10³ km</td><td>0.3–3 ms</td><td>10³–10⁵ s</td><td>10⁻²–10⁻¹</td><td>Fiber phase noise</td><td>~1×10⁻¹⁸ @ 10⁴ s</td><td>[3]</td></tr><tr><td>Microwave fountain</td><td>~10⁴ km</td><td>~30 ms</td><td>10⁴–10⁶ s</td><td>10⁻³–10⁻²</td><td>Dick effect</td><td>~1×10⁻¹⁶ @ 10⁵ s</td><td>[4]</td></tr><tr><td>Hydrogen maser</td><td>~10⁴ km</td><td>~30 ms</td><td>10²–10⁵ s</td><td>10⁻³–10⁻¹</td><td>Cavity drift</td><td>~1×10⁻¹⁵ @ 10⁴ s</td><td>[5]</td></tr><tr><td>GNSS</td><td>~2×10⁴ km</td><td>~70 ms</td><td>1–10⁴ s</td><td>10⁻²–10⁰</td><td>Ionosphere</td><td>~1×10⁻¹⁴ @ 10³ s</td><td>[6]</td></tr><tr><td>TWSTFT</td><td>~10⁴ km</td><td>~30 ms</td><td>10²–10⁵ s</td><td>10⁻³–10⁻¹</td><td>Troposphere</td><td>~5×10⁻¹⁶ @ 10⁴ s</td><td>[7]</td></tr><tr><td>VLBI</td><td>6–10×10³ km</td><td>20–30 ms</td><td>10³–10⁵ s</td><td>10⁻²–10⁻¹</td><td>Troposphere</td><td>~1×10⁻¹⁵ @ 10⁴ s</td><td>[8]</td></tr><tr><td>Pulsar timing†</td><td>~10¹⁹ m</td><td>~10¹¹ s</td><td>10⁷–10⁹ s</td><td>≪10⁻²</td><td>Timing noise, ISM</td><td>~1×10⁻¹⁵ @ 10⁸ s</td><td>[9]</td></tr><tr><td>PTA correlation†</td><td>~10¹⁶ m</td><td>~10⁸ s</td><td>10⁸–10⁹ s</td><td>0.03–0.3</td><td>Red noise</td><td>~1×10⁻¹⁵ @ 10⁸ s</td><td>[10]</td></tr></tbody></table>

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

<table><thead><tr><th width="82.0589599609375">Gear</th><th width="129.65484619140625">Systems</th><th width="138.2720947265625">L_comparison</th><th width="110.3026123046875">τ Domain</th><th width="159.8359375">Role</th><th>Couples To</th></tr></thead><tbody><tr><td>1</td><td>Optical clocks</td><td>≲10³ km</td><td>10³–10⁵ s</td><td>Highest stability</td><td>Gear 2</td></tr><tr><td>2</td><td>Fountains/TAI</td><td>≲10⁴ km</td><td>10⁴–10⁶ s</td><td>SI realization</td><td>Gear 1, 3</td></tr><tr><td>3</td><td>GNSS</td><td>~2×10⁴ km</td><td>1–10⁴ s</td><td>Global distribution</td><td>Gear 2, 4</td></tr><tr><td>4</td><td>VLBI</td><td>~10⁴ km</td><td>10³–10⁵ s</td><td>Earth orientation</td><td>Gear 3, 5</td></tr><tr><td>5</td><td>Pulsar timing</td><td>10¹⁶–10¹⁹ m</td><td>10⁷–10⁹ s</td><td>Decadal stability</td><td>Gear 4, 1</td></tr></tbody></table>

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

<table><thead><tr><th width="332.9027099609375">Exclusion</th><th>Clarification</th></tr></thead><tbody><tr><td>Not a new physical theory</td><td>Causality assumed, not derived</td></tr><tr><td>Not a replacement for Allan variance</td><td>Noise characterization remains essential</td></tr><tr><td>Not a redefinition of TAI/UTC/SI</td><td>Existing standards retain authority</td></tr><tr><td>Not a policy proposal</td><td>Governance decisions lie outside scope</td></tr><tr><td>Not a claim of optimality</td><td>η_opt is a hypothesis, not a prescription</td></tr><tr><td>Not an implementation specification</td><td>Algorithms belong in CSP</td></tr><tr><td>Not a substitute for relativistic corrections</td><td>IERS conventions assumed</td></tr></tbody></table>

***

### 7. Open Design Questions

The framework's value lies in making questions explicit and comparable, not in closing them.

#### 7.1 Architecture: Topology and Layering

The framework does not prescribe a single network topology. Different scales may legitimately use different architectures.

<table><thead><tr><th width="190.71875">Scale</th><th width="194.0511474609375">Candidate Topologies</th><th>Open Questions</th></tr></thead><tbody><tr><td>Local (lab)</td><td>Point-to-point</td><td>Protocol optimization</td></tr><tr><td>Regional (100 km)</td><td>Star, ring</td><td>Topology effect on η_opt?</td></tr><tr><td>Continental (1000 km)</td><td>Mesh, small-world</td><td>Resilience vs. complexity</td></tr><tr><td>Intercontinental</td><td>Hybrid satellite+fiber</td><td>Cost-performance tradeoffs</td></tr><tr><td>Planetary</td><td>Hierarchical federation</td><td>Governance interoperability</td></tr></tbody></table>

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

<table><thead><tr><th width="282.17474365234375">Action</th><th width="89.21588134765625">Effort</th><th>Output</th></tr></thead><tbody><tr><td>Publish η for existing links</td><td>Low</td><td>Annotated comparison reports</td></tr><tr><td>Document L_path in specifications</td><td>Low</td><td>Updated technical documentation</td></tr><tr><td>Run one pre-registered η_opt scan</td><td>Medium</td><td>Technical note (even null result)</td></tr></tbody></table>

#### Table 3 — Actor Entry Points

<table><thead><tr><th width="227.97723388671875">Actor</th><th width="184.7833251953125">Entry Point</th><th>Immediate Action</th></tr></thead><tbody><tr><td>NMIs (PTB, NIST, NPL, etc.)</td><td>Optical networks</td><td>Document η at operating points</td></tr><tr><td>BIPM</td><td>Timescale algorithms</td><td>Evaluate candor weighting principle</td></tr><tr><td>Space agencies</td><td>Satellite timing</td><td>Add L_path to mission specs</td></tr><tr><td>VLBI community</td><td>IVS/IERS</td><td>Cross-validate with optical links</td></tr><tr><td>PTA consortia</td><td>IPTA/NANOGrav</td><td>Report baseline-dependent systematics</td></tr></tbody></table>

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

> Special thanks to the intellectual and institutional environments that shaped this work.

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

<table><thead><tr><th width="186.883544921875">Field</th><th>Value</th></tr></thead><tbody><tr><td>Version</td><td>1.0-rc</td></tr><tr><td>Status</td><td>Citation-stable conceptual layer</td></tr><tr><td>Core sections</td><td>§1–4 (frozen)</td></tr><tr><td>Evolving sections</td><td>§5–9 (may be revised)</td></tr><tr><td>Canonical DOI</td><td>[TBD]</td></tr><tr><td>Citation</td><td>Warring, U. (2025). <em>Causal Clock Unification</em> (v1.0-rc).</td></tr><tr><td>Companion</td><td>CSP (Causal Steering Protocols) — operational details separate</td></tr></tbody></table>

#### Relationship to Companion Documents

**Firewall Statement:** This document (CCUF) defines the conceptual framework. The core (§1–4) is frozen for citation. CSP and implementation notes may evolve without requiring core revision. If companion development reveals gaps in the core, amendments require a new major version.

***

### Version History

<table><thead><tr><th width="110.03338623046875">Version</th><th width="136.52630615234375">Date</th><th>Summary</th></tr></thead><tbody><tr><td>0.1–0.3</td><td>2025-12–14</td><td>Initial formulation through Five-Gear synthesis</td></tr><tr><td>0.5</td><td>2025-12-15</td><td>Parameter tables, open questions, near-term impact</td></tr><tr><td>0.6</td><td>2025-12-15</td><td>Trust repairs, quickstart, provisional example, small-world</td></tr><tr><td><strong>1.0-rc</strong></td><td><strong>2025-12-16</strong></td><td><strong>Merged structure: citation-stable core (§1–4) separated from evolving synthesis (§5–9). Restrained VLBI/PTA framing. Auditable Table 1 with sources. TA-OPT as architectural example only. Retained actionability elements (Quickstart, MVA, actor entry points).</strong></td></tr></tbody></table>

***

_This framework defines a conceptual design layer. Algorithms, operational protocols, and governance mechanisms are explicitly out of scope._
