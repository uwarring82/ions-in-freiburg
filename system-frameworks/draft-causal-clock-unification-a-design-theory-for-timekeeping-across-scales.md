---
description: Timekeeping as Causal Geometry
---

# \[Draft] Causal Clock Unification: A Design Theory for Timekeeping Across Scales

{% hint style="info" %}
**Author:** U. Warring\
**Affiliation:** Institute of Physics, University of Freiburg\
**Version:** 0.0.3\
**Last updated:** 2025-12-13\
**License:** CC BY-SA 4.0\
\
**Disclaimer** — _This document reflects an ongoing effort to clarify how causality constrains timekeeping architectures. Its authority derives from transparency, not finality._<br>
{% endhint %}

### Abstract

Modern timekeeping spans laboratory-scale atomic clocks, global clock networks, and astrophysical timing systems such as VLBI and pulsar timing arrays. While these systems differ widely in mechanism and scale, they share a common operational requirement: a tick is defined only through phase comparison across space.

We introduce a boundary-condition framework that unifies clocks by the causal geometry of phase comparison rather than by oscillator physics. Any physically realizable clock satisfies the constraint that the largest spatial separation over which phase must be actively compared to define a tick on averaging time tau cannot exceed the corresponding light-crossing distance. This relation is not proposed as a new law of nature, but as a fundamental design constraint whose physical content lies in how real clock architectures operate at different depths below the causal boundary.

To prevent definitional ambiguity, we explicitly distinguish three non-interchangeable length scales: the spatial extent of the oscillating process, the region of stabilization and interrogation, and the comparison baseline. Only the comparison baseline enters the causal constraint.

This formulation motivates a dimensionless causal efficiency, defined as the ratio between the comparison baseline and the product of the speed of light and the averaging time, which quantifies how aggressively a clock architecture exploits its causal allowance on a given timescale. We argue that clock stability improves with increasing causal efficiency up to an architecture-specific optimum, beyond which propagation noise, model error, or spatial decoherence dominate.

The framework makes no claims about Planck-scale clocks or new physics. Its value lies in providing a unifying design perspective and a falsifiable optimization principle for timekeeping systems spanning more than fifteen orders of magnitude in period.

***

## Introduction

### Timekeeping as Causal Geometry

#### 1. Context: Why unifying clocks is nontrivial

Over the last decades, precision timekeeping has expanded far beyond the laboratory. Optical atomic clocks now reach fractional instabilities below 10^{-18}, satellite constellations distribute time across planetary scales, Earth rotation is inferred via very long baseline interferometry (VLBI), and pulsar timing arrays (PTAs) probe galactic-scale regularities in spacetime. These systems differ enormously in physical realization, scale, and scientific purpose, yet all are routinely referred to as “clocks.”

Despite this shared label, there is no common framework that places such systems on equal conceptual footing. Atomic clock research emphasizes oscillator physics and quantum noise; satellite and network clocks emphasize synchronization and distribution; VLBI and PTAs are typically framed as astronomical or geodetic techniques rather than as timekeeping architectures. As a result, comparisons across these domains are often qualitative, metaphorical, or reduced to performance tables without a shared structural interpretation.

This fragmentation motivates a simple but foundational question: What, if anything, structurally unifies clocks operating across vastly different physical scales?

#### 2. What is already well established

The physical ingredients relevant to this question are not new.

Relativistic causality constrains the transmission of signals and underlies all synchronization procedures. Time–frequency metrology provides a rigorous statistical language—via Allan variance, phase noise spectra, and related tools—for quantifying clock stability. Relativistic geodesy has demonstrated that clocks can act as sensitive probes of gravitational potential. VLBI and pulsar timing have developed sophisticated models for long-baseline timing and propagation effects.

Each of these fields is internally mature and successful. However, they typically address how clocks operate within a given architecture, not how architectures themselves compare when the spatial scale of phase comparison becomes a dominant variable.

#### 3. The missing perspective: comparison geometry as a primary variable

A recurring difficulty in cross-domain discussions is ambiguity about what constitutes the “size” of a clock. Physical size, apparatus footprint, network extent, and comparison baseline are often conflated, even though they play fundamentally different roles.

To avoid this ambiguity, we explicitly distinguish three length scales:

* $$L_{\text{source}}$$ — the spatial extent of the oscillating process (oscillator physics)
* $$L_{\text{apparatus}}$$ — the region over which the oscillator is stabilized and interrogated (engineering)
* $$L_{\text{comparison}}$$ — the spatial separation over which phase information must be compared to define a tick (architecture)

Only the third scale, $$L_{\text{comparison}}$$, determines how far phase information must propagate to produce a usable time reference.

This distinction reveals a common constraint that applies to all clocks, regardless of mechanism:

<p align="center"><span class="math">L_{\text{comparison}} \le cT</span>,</p>

where T is the tick period relevant to the comparison. This inequality is a direct consequence of relativistic causality: phase information used to define a tick must lie within (or on) the light cone of the comparison process.

Crucially, this relation is not introduced as a new law of nature. It is a fundamental design constraint that all realizable clocks must satisfy. Its physical content lies not in the inequality itself—which is unavoidable—but in how real clock architectures operate at different distances below this causal boundary.

#### 4. Operational definition and causal efficiency

To prevent post-hoc or semantic interpretations, we adopt a strictly operational definition:

$$L_{\text{comparison}}$$ is the maximum spatial separation between phase measurements that must be combined within a single active feedback cycle to define or stabilize a tick on the averaging timescale of interest. Passive post-processing steps that do not participate in the feedback defining the tick are excluded.

This allows us to introduce a dimensionless control parameter, the causal efficiency,

<p align="center"><span class="math">\eta(\tau) \equiv \frac{L_{\text{comparison}}(\tau)}{c\,\tau}</span>,</p>

where $$\tau$$ is the averaging time over which phase comparison is active.

$$\eta(\tau)$$ measures how aggressively a given architecture exploits its causal allowance on timescale \tau.

* $$\eta \ll 1$$: deeply sub-causal architectures (e.g. laboratory atomic clocks prioritizing quantum coherence)
* $$\eta \to 1$$: near-saturated architectures (e.g. VLBI or PTAs), where propagation and medium effects dominate

This framing shifts attention from oscillator mechanism to comparison geometry, enabling clocks of radically different kinds to be placed on a common architectural plane.

#### 5. Research gap and guiding question

While causality, synchronization, and stability are individually well studied, no existing framework explicitly treats the causal geometry of phase comparison as the unifying variable across clock architectures. In particular, the literature lacks:

1. A clear separation between oscillator physics and comparison geometry
2. A way to compare clocks across laboratory, planetary, and astrophysical scales using a common metric
3. A design-level principle describing how performance changes as architectures approach their causal limit

This gap motivates the central guiding question of this work:

Does each clock architecture admit an optimal causal efficiency \eta\_{\text{opt\}}(\tau), beyond which extending the comparison baseline no longer improves stability because propagation noise, model error, or spatial decoherence dominate?

If such optima exist and can be predicted, the framework has falsifiable content and practical design relevance.

#### 6. Aim and scope of this work

The aim of this work is to formalize a boundary-condition framework for timekeeping that unifies clocks by the causal geometry of phase comparison rather than by oscillator physics.

Specifically, we:

* Treat $$L_{\text{comparison}} \le cT$$ as a fundamental design constraint
* Introduce $$\eta(\tau)$$ as a load-bearing architectural parameter
* Map diverse clock systems onto a common ($$L_{\text{comparison}}, \tau$$) plane
* Argue that clock performance reflects distance to the causal boundary, not proximity to any fundamental scale

This framework is intended as a guide for analysis and design, not as a replacement for existing theories. It makes no claims about Planck-scale clocks, quantum gravity, or biological rhythms. The Planck scale appears only as a dimensional endpoint of the causal envelope.

#### 7. Roadmap

The next section situates this framework relative to established bodies of work in relativistic synchronization, time–frequency metrology, relativistic geodesy, VLBI, and pulsar timing. By explicitly mapping where these approaches succeed—and where they stop—we identify the precise conceptual space occupied by the present contribution.

### Design Claim

> For any physically realizable clock or timing system operating on averaging time \tau, there exists an architecture-specific optimal causal efficiency
>
> <p align="center"><span class="math">\eta(\tau) \equiv \frac{L_{\mathrm{comparison}}(\tau)}{c\,\tau}</span>,</p>
>
> where $$L_{\mathrm{comparison}}(\tau)$$ is the maximum spatial separation between phase measurements that must be combined within a single feedback cycle to define a tick on that timescale.
>
> Below this optimum, increasing $$L_{\mathrm{comparison}}$$ improves stability by averaging over local oscillator noise. Above it, propagation noise, model error, or spatial decoherence dominate, and stability degrades. The empirical content of the framework lies in predicting and testing the location of $$\eta_{\mathrm{opt}}(\tau)$$for specific clock architectures. Failure to observe such an optimum in real systems would falsify the framework’s predictive core.

***

## Relation to Prior Work

### Differential Diagnosis Across Disciplines

The framework developed here does not introduce new physical laws. It synthesizes well-established results from several mature fields by re-organizing them around a different primary variable: the causal geometry of phase comparison. This section delineates how existing approaches treat clocks and timing, where their natural scope ends, and where the present framework extends the conceptual structure.

#### 1. Relativistic Synchronization and Causality

Established results.

Einstein’s formulation of special relativity established the operational meaning of simultaneity and the requirement that synchronization protocols respect the invariant speed of light. Subsequent analyses by Reichenbach and Malament clarified the conventional and causal aspects of synchronization, grounding clock comparison firmly within spacetime structure.

Limit of the approach.

In this tradition, causality enters primarily as a binary feasibility condition: synchronization procedures must not violate light-cone structure. The geometry of the clock network itself is typically taken as given, not as a variable influencing performance.

Extension introduced here.

We treat causality not only as a feasibility test but as a continuous architectural constraint: clock performance depends on how closely a system operates to its causal limit. The comparison baseline becomes a design variable whose scale shapes stability.

***

#### 2. Time–Frequency Metrology and Oscillator Stability

Established results.

The statistical foundations of time–frequency metrology—most notably Allan variance—provide a rigorous language for characterizing oscillator stability across averaging times. Modern optical clocks build on this tradition, incorporating quantum projection noise, laser phase noise, and advanced interrogation schemes to approach fundamental limits.

Limit of the approach.

Standard metrology focuses primarily on the local oscillator and apparatus ($$L_{\text{source}}$$, $$L_{\text{apparatus}}$$). Propagation and distribution are typically modeled as “link noise” to be minimized or corrected, rather than as intrinsic elements of the clock’s architecture.

Extension introduced here.

We elevate the comparison baseline $$L_{\text{comparison}}$$ to a first-class system parameter. For distributed or long-baseline systems, the link is not ancillary—it is the clock. The framework complements, rather than replaces, oscillator-centric analyses by clarifying when spatial extent becomes performance-limiting.

***

#### 3. Relativistic Geodesy and Clocks as Sensors

Established results.

Relativistic geodesy has demonstrated that frequency comparisons between clocks are sensitive to gravitational potential differences. Experiments using optical clocks have confirmed relativistic redshift predictions with unprecedented precision, establishing clocks as probes of spacetime geometry.

Limit of the approach.

In geodesy, spacetime variation is treated as signal, while clock instability is noise. The optimization objective is external field reconstruction, not the construction of a universal or maximally stable time scale.

Extension introduced here.

We explicitly invert this perspective. When the goal is timekeeping, gravitational and spacetime variability become noise sources. This inversion reveals a functional limit: beyond a certain comparison scale, improving clocks transforms them into spacetime sensors. This transition can be quantified through the causal efficiency $$\eta(\tau)$$.

_(Functional note: the distinction is not operational but objective-dependent—the same hardware supports both roles.)_

***

#### 4. VLBI, Earth Rotation, and Planetary-Scale Timing

Established results.

VLBI provides exquisitely precise measurements of Earth orientation, reference frames, and baseline geometry using distant radio sources. These techniques rely on highly stable frequency standards and sophisticated relativistic delay models.

Limit of the approach.

VLBI is usually framed as an astronomical and geodetic technique, with its clock-like aspects treated as a subordinate operational requirement rather than as the defining architectural feature.

Extension introduced here.

By focusing on the phase comparison baseline—Earth to quasar—we reinterpret VLBI-based Earth rotation as a timing system operating extremely close to the causal boundary. Its stability is limited not by oscillator physics, but by propagation effects and spacetime variability across the baseline.

***

#### 5. Pulsar Timing Arrays and Astrophysical Timekeeping

Established results.

Pulsar timing arrays exploit the extraordinary rotational stability of millisecond pulsars to study gravitational waves and long-term spacetime perturbations. Timing models incorporate dispersion, solar-system ephemerides, and clock corrections with great sophistication.

Limit of the approach.

PTAs are commonly described as detectors or observatories, rather than as clocks. Individual pulsars are treated as the clocks; the Earth-based comparison is viewed as readout infrastructure.

Extension introduced here.

In the present framework, the entire PTA—pulsars, propagation medium, and Earth-term comparison—constitutes a composite timing system. Individual pulsars function as oscillator components, while the galactic-scale comparison baseline drives the system toward \eta \to 1, where spacetime noise dominates stability.

***

#### 6. Summary of the Gap

Across these domains, causality, synchronization, stability analysis, and long-baseline timing are all well understood. However:

* The comparison geometry of clocks is rarely treated as the primary organizing variable.
* No framework explicitly separates $$L_{\text{source}}$$, $$L_{\text{apparatus}}$$, and $$L_{\text{comparison}}$$ across all scales.
* No dimensionless parameter is commonly used to characterize how clock architectures approach their causal limit.

To our knowledge, no prior work unifies atomic clocks, clock networks, VLBI, and pulsar timing by treating the causal geometry of phase comparison as the central architectural principle, nor introduces a causal efficiency parameter \eta(\tau) to quantify this structure.

We welcome identification of prior formulations that address this question.

***

### References

1. A. Einstein, _Zur Elektrodynamik bewegter Körper_, Ann. Phys. 17, 891–921 (1905).
2. H. Reichenbach, _Axiomatik der relativistischen Raum-Zeit-Lehre_, Vieweg (1924).
3. D. Malament, _Causal theories of time and the conventionality of simultaneity_, Noûs 11, 293–300 (1977).
4. D. W. Allan, _Statistics of atomic frequency standards_, Proc. IEEE 54, 221–230 (1966).
5. W. M. Itano et al., _Quantum projection noise: Population fluctuations in two-level systems_, Phys. Rev. A 47, 3554 (1993).
6. D. J. Wineland et al., _Experimental issues in coherent quantum-state manipulation of trapped atomic ions_, J. Res. NIST 103, 259–328 (1998).
7. C. W. Chou et al., _Optical clocks and relativity_, Science 329, 1630–1633 (2010).
8. S. Kopeikin et al., _Relativistic Reference Frames for Astrometry and Geodesy_, Springer (2011); see also ISSI Spacetime Metrology program (2015–).
9. J. E. Sovers, C. S. Jacobs, and G. S. Lanyi, _Astrometry and geodesy with radio interferometry_, Rev. Mod. Phys. 70, 1393 (1998).
10. S. Lambert and C. Le Poncin-Lafitte, _Improved determination of VLBI delays_, A\&A 529, A70 (2011).
11. R. N. Manchester et al., _The International Pulsar Timing Array_, PASA 30, e017 (2013).
12. L. Verbiest et al., _The International Pulsar Timing Array: First data release_, MNRAS 458, 1267–1288 (2016).

***

_Special thanks to all my past, current, and future environments._

***

### Disclaimer

| Item                       | Statement                                                                                                                                                                                                                                                                            |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Scope                      | This document proposes a design-theoretic framework for comparing and optimizing clock architectures. It does not introduce new physical laws, modify established relativity, or claim experimental discovery.                                                                       |
| Status                     | This page presents a working draft intended for  discussion, critical review, and iterative refinement. Concepts, definitions, and terminology may evolve as the framework is tested against data and prior art.                                                                     |
| Relationship to Prior Work | All underlying physical principles—relativistic causality, clock synchronization, noise theory, and time–frequency metrology—are well established. The contribution here is a structural synthesis and formalization of these elements into a unified comparison-geometry framework. |
| Novelty Claim              | To the best of our knowledge, the explicit separation of comparison geometry from oscillator physics, and the formulation of causal efficiency as a design parameter, has not been previously formalized. This claim is made cautiously and remains open to correction.              |
| Non-Claims                 | The framework makes no claims about Planck-scale clocks, quantum gravity, superluminal signaling, or the ultimate nature of time. The Planck point appears only as a dimensional reference, not an empirical target.                                                                 |
| Intended Use               | The framework is intended as a conceptual and architectural guide for analyzing existing clocks and designing distributed timekeeping systems. It should be read as a tool for reasoning, not as a prescription or constraint on future physics.                                     |
| Feedback & Corrections     | Constructive criticism, references to overlooked prior work, and counterexamples are explicitly welcomed. Any demonstrated errors or anticipations will be acknowledged and incorporated in subsequent versions.                                                                     |

***

### Version History

<table><thead><tr><th width="96.37890625">Version</th><th width="107.32421875">Date</th><th width="93.87890625">Status</th><th>Summary of Changes</th></tr></thead><tbody><tr><td>v0.0.1</td><td>2025-12-12</td><td>Internal</td><td>Initial formulation of causal boundary concept linking clock period and effective size. Exploratory scope; definitions not yet fixed.</td></tr><tr><td>v0.0.2</td><td>2025-12-12</td><td>GitBook</td><td>Formalized framework as a boundary-condition design theory. Introduced strict separation of <span class="math">L_{\text{source}}</span>, <span class="math">L_{\text{apparatus}}</span>, and <span class="math">L_{\text{comparison}}</span>. Defined causal efficiency parameter <span class="math">\eta(\tau)</span>. Demoted Planck scale to dimensional endpoint only. Language tightened for falsifiability and GitBook presentation.</td></tr><tr><td>v0.0.x (planned)</td><td>—</td><td>Planned</td><td>Addition of “Relation to Prior Work” section; explicit Design Claim box; causal envelope figure and caption; first worked example estimating <span class="math">\eta_{\text{opt}}</span> for a concrete clock architecture.</td></tr></tbody></table>
