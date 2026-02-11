---
description: A Clean Mapping and Its Limits
---

# Active Phase Grating vs. Standard Ramsey

**Stewardship:** U. Warring.\
**Version:** 0.2 (draft) — February 2026\
**External constraints:** Dick (1987); Santarelli et al. (1998); Yudin et al. (2010); Huntemann et al. (2012); Hasse et al. (2024, PRA 109, 053105)

***

### 1. Purpose and Scope

This essay establishes the **active phase grating** as a pedagogical and operational framework for understanding multi-pulse analysis trains in stroboscopic trapped-ion spectroscopy. It maps the analogy to spatial diffraction gratings, locates where the mapping is safe, identifies where it breaks, and defines the quantitative figures of merit required to compare the grating approach against standard Ramsey interferometry on metrological ground.

The intended audience is the experimental crew working on FH24-derived stroboscopic protocols (Hasse et al. 2024, PRA 109, 053105), including new doctoral researchers. The essay should be read alongside the qubit-only simulation code, which provides numerical ground truth for the claims made here.

> **Harbour Policy.** This document is a Sail (working essay), not a Coastline (stable framework). It may be revised as experimental data accumulates. The Lock is the metrological comparison methodology; the Keys are the specific parameter choices, which remain free.

***

### 2. The Safe Part of the Analogy

#### 2.1 Ramsey as a Double Slit in Time

Standard Ramsey interferometry maps directly onto a two-path interferometer in time. A first π/2 pulse creates a superposition of internal states (two "paths" in phase space). Free evolution for duration τ accumulates a relative phase Δτ, where Δ is the detuning. A second π/2 pulse recombines the paths. The output signal ⟨σ\_z⟩ = −cos(Δτ) produces fringes with width ∼ 1/τ. This is the double-slit limit: two coherent contributions, resolution set by the total interrogation time.

#### 2.2 The N-Pulse Train as a Diffraction Grating

Replace the second π/2 pulse with N weak pulses of individual area (π/2)/N, separated by gaps Δt. Each pulse generates a time-separated coherent contribution to the transition amplitude. As detuning is scanned, these contributions acquire relative phases ∼ Δ·Δt and interfere. The resulting amplitude has the structure:

> A(Δ) ∝ Σ\_{j=0}^{N−1} w\_j exp(i Δ t\_j)

For equal weights and spacing t\_j = jΔt, this reduces to the standard N-slit grating factor:

> A(Δ) ∝ sin(NΔ·Δt/2) / sin(Δ·Δt/2)

The main-lobe width scales as 1/(NΔt), so increasing N sharpens spectral selectivity. Side lobes appear at multiples of 2π/Δt, producing the universal grating tradeoff: resolution against ambiguity.

#### 2.3 The Mapping Table

| Spatial Grating        | Stroboscopic Train         | Role                                     |
| ---------------------- | -------------------------- | ---------------------------------------- |
| Slit spacing d         | Pulse spacing Δt           | Sets fringe period / free spectral range |
| Number of slits N      | Number of pulses N         | Sets resolving power                     |
| Field superposition    | Quantum amplitude addition | Interference mechanism                   |
| Phase plate at slit    | Per-pulse phase φ          | Steers / blazes the pattern              |
| Slit-width apodisation | Pulse-area shaping         | Side-lobe suppression                    |
| Total aperture Nd      | Total aperture NΔt         | Resolution limit                         |

***

### 3. The Critical Caveat: Active vs. Passive

> **⚠ Guardian Flag.** The grating analogy is safe only when the distinction between passive apertures and active SU(2) rotations is made explicit. Without this caveat, users will be misled about the behaviour under phase manipulation, finite detuning, and error accumulation.

In a passive spatial grating, amplitudes superpose without back-action: the grating does not alter the field it diffracts. In the stroboscopic train, each "slit" is an **active SU(2) rotation** interleaved with detuning-driven z-precession. Pulses and free-precession generally **do not commute**. This has three immediate consequences.

**First**, "flipping the phase of every second slit" does not simply "shift the pattern." In a passive grating, alternating phase shifts produce a predictable blazed profile. In the active case, a phase flip can partially cancel, reshape, or generate qualitatively different responses depending on the detuning Δ and the timing gaps. Cancellation can be exact only in the limit Δ ≈ 0 with negligible gap-induced z-rotation; otherwise the gap rotations break the symmetry and a modified pattern re-emerges. This is exactly what the simulation diagnostics show.

**Second**, the "weights" w\_j in the grating sum are not fixed amplitudes. They depend on the accumulated unitary evolution up to pulse j, which includes all prior pulse areas, phases, and detuning-driven rotations. The grating formula A(Δ) ∝ Σ w\_j exp(iΔ t\_j) is therefore a linearised approximation valid for small pulse areas and small detunings, not an exact decomposition.

**Third**, error accumulation scales differently. In a passive grating, fabrication errors in individual slits contribute independently. In the active train, pulse-area errors, phase errors, and timing errors propagate through the unitary chain. Correlated errors can scale as N (not √N), because the same systematic shifts compound multiplicatively through sequential SU(2) operations.

***

### 4. What Is Being Engineered

In the FH24 regime (Hasse et al. 2024), the pulse spacing Δt is matched to a motional mode period. The train therefore acts as a **spectral selector**: it builds sensitivity to a specific Fourier component of the ion's motion. The design intent is not composite-pulse robustness (that becomes relevant only when shaping φ across pulses to cancel systematic shifts). The design intent is:

> _**Engineer the frequency response of the measurement operator.**_

This is precisely the role of the sensitivity function g(t) in Dick-effect methodology. The pulse train defines a time-domain window; its Fourier transform determines which detuning (or motional-frequency) components couple to the readout. The grating picture is a pedagogical handle on these Fourier properties, nothing more and nothing less.

***

### 5. How to Compare Fairly: Discriminator at the Working Point

To compare standard Ramsey against the active grating on metrological ground, one must use the same operational strategy for both. The strategy is: operate as a **frequency discriminator at a chosen working point**.

In standard Ramsey, one picks an analysis phase (typically ±π/2 quadrature) so that the fringe's steepest slope sits at Δ = 0. The error signal is extracted from this slope. In the grating picture, the analogue is: choose a global train phase φ₀ so the composite analysis operation places the discriminator at the working point. The comparison then proceeds identically for both:

1. **Set the working point** by adjusting the analysis phase φ\_ana so that ⟨σ\_z⟩ = 0 at Δ = 0.
2. **Compute the local slope** S\_N = ∂⟨σ\_z⟩/∂Δ evaluated at Δ = 0.
3. **Measure the linear capture range**: the width of the monotonic region around the working point.
4. **Quantify the side-lobe ratio**: the largest parasitic slope relative to the main-lobe slope.
5. **Normalise by total sequence time** (or equivalently, duty cycle) to obtain a per-unit-time metric.

This gives an apples-to-apples comparison. Without step 5, a train that simply extends the total interrogation time will appear to win trivially.

***

### 6. What Do You Gain: The Steeper Slope

In the idealised case (unit contrast, negligible pulse-area error, perfect timing), the discriminator slope scales as:

> S(N) ∼ N · Δt

This is the intuitive "higher resolving power" of the grating: a narrower main lobe produces a steeper zero-crossing. The slope grows roughly linearly with the effective grating length T\_ap = NΔt.

> **⚠ Guardian Flag.** This scaling assumes unit contrast, negligible pulse-area error, and operation at the exact working point. Realistic corrections are treated in Section 7. Do not cite this scaling without its conditions.

***

### 7. What Is the Price: Five Costs

The costs mirror classical grating tradeoffs, plus quantum-control penalties unique to the active case.

#### 7.1 Reduced Capture Range

A narrower main lobe means a smaller monotonic region for locking. The linear capture range shrinks as ∼ 1/(NΔt). In practice, this demands tighter pre-stabilisation of the local oscillator before the discriminator lock can acquire. The classic resolution–dynamic-range tradeoff is unavoidable.

#### 7.2 Side-Lobe Ambiguity

Standard Ramsey produces a single sinusoid in detuning. The N-pulse grating develops (N − 1) side lobes between principal maxima. Each side lobe is a potential false-lock point. Without apodisation (non-uniform pulse weighting), the side-lobe amplitude relative to the main lobe is ∼ 1/N for the first side lobe. Engineering mitigation strategies include pulse-area tapering (the grating analogue of apodisation) and multi-step acquisition protocols that first lock with Ramsey, then hand off to the grating.

#### 7.3 Control-Error Accumulation

Because pulses are active SU(2) operations, errors propagate through the unitary chain:

* **Pulse-area errors:** if uncorrelated across pulses, the net effect scales as √N. If correlated (e.g., systematic miscalibration), it scales as N.
* **Phase errors:** same scaling dichotomy. Correlated phase drift produces a systematic shift of the discriminator zero-crossing.
* **Timing jitter:** fluctuations in Δt shift the effective grating spacing, broadening the response and reducing peak slope.

The transition between √N and N scaling — where correlations in control errors shift regimes — is precisely where experimental design decisions live. This is **not a heuristic warning**; it is the quantitative question that the simulation must answer for each specific apparatus.

#### 7.4 Noise Spectral Reshaping (Dick Effect)

The pulse train implements a sensitivity function g(t) in the time domain. Its Fourier transform determines which local-oscillator (or drive) noise frequencies couple to the measurement. This is exactly the Dick effect (Dick 1987; Santarelli et al. 1998): high-frequency phase noise on the LO is aliased to near-DC by the periodic interrogation structure.

For standard Ramsey, the sensitivity function is approximately constant during free evolution and zero during dead time. For the N-pulse train, g(t) has a comb-like structure: it is non-zero during each pulse window and picks up different Fourier weights. The resulting aliased noise can either be suppressed or enhanced relative to Ramsey, depending on the match between the train's spectral sensitivity and the noise spectrum of the LO.

This is not optional engineering. As demonstrated by the zero-dead-time clock work (Schioppo et al. 2017, Nature Photonics 11, 48), the Dick effect is typically the dominant stability limitation for pulsed standards. Any proposal for a multi-pulse interrogation must compute g(t) and its Fourier coefficients g\_n, then evaluate the Dick instability:

> σ\_y²(1s) = (2/g₀²) Σ\_n |g\_n|² S\_y(n/t\_c)

where S\_y is the LO fractional frequency noise spectral density and t\_c is the cycle time.

#### 7.5 Duty-Cycle and Dead-Time Penalty

Even in a qubit-only model, the train occupies a finite time window. If T\_ap = NΔt grows, the measurement bandwidth (rate of frequency corrections) decreases. In a clock, this directly worsens stability if LO noise dominates at low Fourier frequencies. In the trapped-ion motional context, longer trains increase exposure to decoherence mechanisms (heating, dephasing, background-gas collisions).

The fifth figure of merit is the **effective duty cycle** d = T\_interrogation / T\_cycle, and any fair comparison must report sensitivity per unit wall-clock time, not per unit interrogation time.

***

### 8. Literature Anchors

The conceptual territory of the active phase grating sits at the intersection of three well-established lines of work. These are external coastlines in Harbour language: constraints we reference without replicating.

#### 8.1 Sensitivity Function and Dick Effect

The canonical methodology for computing the "price" of pulsed interrogation. Dick (1987, Proc. 19th PTTI) introduced the framework. Santarelli et al. (1998, IEEE Trans. UFFC 45, 887) provided the quantum-mechanical derivation of the sensitivity function and experimentally verified it in the LPTF Cs fountain. Lemonde et al. (1998, IEEE Int. Freq. Control Symp.) clarified the formalism. Quessada et al. (2003, J. Opt. B 5, S150) extended it to optical standards. Any N-pulse train proposal must evaluate its Dick instability using this methodology.

#### 8.2 Multi-Pulse Ramsey Schemes in Clocks and Interferometry

The explicit engineering of interrogation sequences in the time domain has a long history. In the CPT context, Yun et al. (2012, EPL 97, 63004) demonstrated multipulse Ramsey-CPT interference fringes in vapour cells, showing the expected narrowing with N and the associated capture-range concerns. Boudot et al. (2017, arXiv:1703.04720) achieved high-performance pulsed Ramsey-CPT clocks. The "temporal Fabry-Pérot" framing used in some of this work is essentially the same grating picture presented here.

#### 8.3 Tailored Composite Pulse Schemes (Hyper-Ramsey and Generalisations)

When the goal shifts from spectral selectivity to systematic-shift suppression, one shapes pulse phases, durations, and frequencies across the train. Yudin et al. (2010, PRA 82, 011804(R)) proposed Hyper-Ramsey spectroscopy: a three-pulse sequence with phase-inverted central pulse that cancels probe-induced light shifts by two to four orders of magnitude. Huntemann et al. (2012, PRL 109, 213002) demonstrated this experimentally on the ¹⁷¹Yb⁺ E3 transition, achieving 10⁴-fold light-shift suppression. Zanon-Willette et al. (2018, Rep. Prog. Phys. 81, 094401) reviewed the composite-pulse landscape comprehensively.

In grating language, these correspond to "blazing" and "phase-plate engineering." They are conceptually adjacent to our framework but serve a different design intent: shift cancellation rather than spectral selectivity. The two intents can coexist in a single sequence, but they should not be conflated.

***

### 9. The Pedagogical Safeguard

> **Teaching rule.** When presenting the grating analogy to students or collaborators, always state both halves: (1) the mathematical structure is identical to N-slit diffraction; (2) the slits are active SU(2) rotations, not passive apertures, so the weights depend on the control Hamiltonian and the analogy breaks under phase manipulation at finite detuning.

The cancellation diagnostic in the simulation demonstrates this concretely. When the phase of every second pulse is flipped: at Δ = 0 with negligible gap rotation, the contributions cancel exactly (as in a passive grating with alternating phase). At finite Δ, the gap rotations break the symmetry and the pattern reappears in modified form. Interference survives — but it is modified by active dynamics. This is the sharpest illustration of the difference between passive and active gratings.

***

### 10. The Complete Figure-of-Merit Set

The meaningful comparison between standard Ramsey and the active phase grating is **not** fringe width. It is the following set of five quantities, evaluated at the working point:

| Figure of Merit                | Symbol            | Ramsey Baseline       | Grating Scaling (Ideal)      |
| ------------------------------ | ----------------- | --------------------- | ---------------------------- |
| Discriminator slope            | S = ∂⟨σ\_z⟩/∂Δ    | ∼ τ                   | ∼ NΔt                        |
| Linear capture range           | Δ\_cap            | ∼ 1/τ                 | ∼ 1/(NΔt)                    |
| Side-lobe ratio                | r\_SL             | 0 (single sinusoid)   | ∼ 1/N (first side lobe)      |
| Control-noise-equivalent error | δΔ\_ctrl          | Two-pulse errors only | Depends on √N vs N scaling   |
| Effective duty cycle           | d = T\_int/T\_cyc | Set by dead time      | Longer train, more dead time |

A sixth quantity — the **projection-noise-normalised sensitivity** — can be derived from these five when the atom number and contrast are specified. For a single trapped ion, the projection noise is fixed at 1/2, so the relevant comparison reduces to S/√(T\_cycle).

***

### 11. Development Roadmap: Theory, Numerics, Experiment

#### 11.1 Theory Programme

The theoretical work proceeds in three layers, each extending the grating framework toward a falsifiable experimental prediction.

**Layer T1: Exact sensitivity function for the N-pulse train.** Derive g(t) analytically for the stroboscopic train with arbitrary pulse areas, spacings, and phases. The starting point is the Santarelli–Lemonde formalism: g(t) is defined as the response of the transition probability to an infinitesimal phase step at time t. For standard Ramsey with two ideal pulses, g(t) is piecewise constant and the derivation is textbook. For N interleaved pulses, g(t) acquires a comb-like structure whose Fourier coefficients g\_n encode the grating's spectral selectivity. The key deliverable is a closed-form (or semi-analytic) expression for g\_n(N, Δt, θ\_pulse), where θ\_pulse is the individual pulse area, valid beyond the linearised (small-area) limit. This extends the grating picture from a pedagogical handle to a quantitative tool.

**Layer T2: Optimal N under realistic noise.** Given g\_n(N) from T1 and a measured or modelled LO noise spectrum S\_y(f), compute the Dick-limited instability σ\_y(N) as a function of N. Simultaneously compute the discriminator slope S(N) and capture range Δ\_cap(N). The theoretically optimal N\* is defined by:

> N\* = argmax\_N \[ S(N) / √(σ\_y²(N) + σ\_proj²) ]

where σ\_proj is the projection noise contribution. This is a genuine prediction: the optimal grating order depends on the apparatus noise floor, not on the analogy. The theory must also determine whether N\* is robust (broad optimum) or fragile (sharp peak), as this dictates experimental tolerance.

**Layer T3: Extension to motional coupling.** Promote the qubit-only model to a spin-motion coupled system. In the Lamb-Dicke regime, the motional sidebands introduce a second frequency scale ω\_mode alongside the detuning Δ. When Δt is matched to 2π/ω\_mode (the FH24 stroboscopic condition), the grating's spectral selectivity is directed at the motional frequency rather than the LO detuning. The theory must derive the modified sensitivity function g(t; η, n̄) including the Lamb-Dicke parameter η and mean phonon number n̄, and determine how motional heating during the train degrades the grating contrast. The key question is whether the grating resolving power can separate closely spaced motional modes (e.g., distinguish the LF mode from a nearby parametric resonance) — this would be a qualitatively new capability.

**Layer T4 (speculative): Connection to force sensing.** A frequency discriminator with enhanced slope is, by the equivalence Δω = F/(mω\_mode · x\_zpf), also a force sensor with enhanced transduction gain. Derive the force sensitivity δF(N) of the grating protocol and compare against the standard quantum limit for a harmonically bound ion. If the grating protocol approaches or restructures the SQL in a non-trivial way (e.g., by concentrating sensitivity into a narrow frequency band), this becomes a result with implications beyond trapped-ion spectroscopy.

#### 11.2 Numerical Programme

The simulations validate the theory at each layer and generate the quantitative predictions that experiments will test.

**Step N1: Working-point finder (qubit-only).** Extend the existing simulation with an analysis phase parameter φ\_ana. For each N from 1 to 20: automatically find φ\_ana such that ⟨σ\_z⟩ = 0 at Δ = 0, then extract slope S\_N, capture range (width of monotonic region), and side-lobe ratio. Plot all five figures of merit as functions of N. Deliverable: a single summary figure showing the Ramsey-vs-grating comparison.

**Step N2: Control-noise injection.** Add Gaussian noise to pulse areas (δθ/θ at the 10⁻³ to 10⁻¹ level), timing jitter (δ(Δt)/Δt at the 10⁻⁴ to 10⁻² level), and phase drift (random walk in φ). For each noise level, repeat the N-sweep from N1. Determine the crossover point where the noise-equivalent detuning error δΔ\_ctrl exceeds the slope gain, yielding the realistic optimum N\*(noise). Map the √N-to-N transition in error scaling by varying the correlation length of the noise.

**Step N3: Dick-effect evaluation.** Compute g(t) numerically for each N by applying infinitesimal phase steps at each time point in the sequence and recording the transition-probability response. Extract Fourier coefficients g\_n. Given a representative LO noise model (white frequency noise + flicker floor), compute σ\_y(N) and overlay it on the slope-vs-N plot from N1. Verify that the theoretical N\* from T2 matches the numerical optimum.

**Step N4: Spin-motion simulation.** Implement a truncated Fock-space simulation (n\_max ∼ 20) for a single ion in a harmonic trap coupled to the qubit via Lamb-Dicke interaction. Reproduce the qubit-only results in the η → 0 limit. Then turn on η = 0.1–0.4 (the FH24 range) and simulate the grating response as a function of motional frequency ω\_mode for fixed Δt = 2π/ω\_mode,design. This produces the grating's "spectral transfer function" for motional excitation — the core experimental observable. Include thermal occupation (n̄ = 0 to 10) and heating rate (dn̄/dt) to quantify contrast degradation.

**Step N5: Two-mode resolution test.** Introduce a second motional mode at ω₂ = ω₁ + δω. Simulate the grating response as a function of N and determine the minimum resolvable splitting δω\_min(N). Compare against the Ramsey limit δω\_min(N=1). If the grating resolves splittings that Ramsey cannot at the same total interrogation time, this is the quantitative basis for a "qualitatively new capability" claim.

#### 11.3 Experimental Programme

The experiments are ordered by increasing difficulty and decreasing overlap with existing demonstrations.

**Experiment E1: Qubit-only grating spectroscopy (validation).** Implement the N-pulse analysis train on a single trapped Ba⁺ (or Mg⁺) ion using microwave or Raman pulses. Scan detuning and record ⟨σ\_z⟩(Δ) for N = 1, 2, 5, 10, 20. Verify the predicted narrowing of the central feature. Extract discriminator slope and capture range; compare against simulation (N1). This is a straightforward validation experiment with no new physics — its role is to confirm that the simulation chain is trustworthy before proceeding to motional coupling. Estimated effort: one doctoral researcher, two to four weeks of beam time.

**Experiment E2: Working-point discriminator operation.** Lock the LO to the grating discriminator at the working point. Measure the closed-loop stability (Allan deviation) as a function of N. Compare against standard Ramsey lock at the same total interrogation time. This tests the Dick-effect prediction from N3: does the grating lock achieve better or worse stability than Ramsey, and at which N does the crossover occur? Estimated effort: extends E1 by two to four weeks for closed-loop implementation and stability characterisation.

**Experiment E3: Stroboscopic motional spectroscopy.** This is the FH24 core experiment, now informed by the grating framework. Set Δt = 2π/ω\_LF (matched to the low-frequency motional mode). Apply the N-pulse train after state preparation and free evolution. Measure ⟨σ\_z⟩ as a function of motional excitation (prepared by displacement pulses or heating). Extract the motional-frequency transfer function and compare against simulation (N4). The key test is whether the grating resolving power reveals structure in the motional spectrum (mode splittings, anomalous heating spectral features) that standard Ramsey does not resolve.

**Experiment E4: Anomalous heating-rate spectroscopy (the PRL target).** If E3 demonstrates grating-enhanced motional-frequency resolution, use it to measure the spectral density of electric field noise S\_E(ω) near ω\_mode with resolution δω set by the grating. Standard heating-rate measurements integrate over a broad frequency band; the grating protocol could, in principle, spectrally resolve the noise — distinguishing between 1/f, white, and structured (e.g., resonance-induced) contributions. A spectrally resolved heating-rate measurement at the single-trapped-ion level would be a new experimental capability. If the spectral shape reveals a feature (a resonance, a cutoff, a deviation from 1/f), that is a result with implications for surface-science models of anomalous heating and for the design of quantum processors.

**Experiment E5: Force sensitivity benchmark (the long shot).** Operate the grating discriminator as a narrow-band force sensor. Apply a known oscillating electric field at frequency ω\_mode and measure the minimum detectable force as a function of N. Compare against the SQL for a single harmonically bound ion. If the grating protocol restructures the sensitivity bandwidth in a metrologically useful way (concentrating sensitivity into a narrow band at the cost of bandwidth, analogous to a lock-in amplifier), characterise the force-sensitivity–bandwidth product and compare against existing single-ion force-sensing records. This experiment is speculative but has the broadest implications if successful.

***

### 12. Realistic Publication Trajectory

| Milestone                        | Content                                                                            | Target Venue                                           | Estimated Timeline |
| -------------------------------- | ---------------------------------------------------------------------------------- | ------------------------------------------------------ | ------------------ |
| Sail + simulation (T1–T2, N1–N3) | Methods paper: grating framework, figure-of-merit comparison, Dick-effect analysis | PRA or NJP                                             | 2026 Q3–Q4         |
| E1 + E2 validation               | Experimental verification of grating narrowing and discriminator lock              | Included in methods paper or standalone PRA(R)         | 2026 Q4–2027 Q1    |
| E3 stroboscopic spectroscopy     | Motional-frequency transfer function with grating-enhanced resolution              | PRA or PRL (if mode splitting resolved)                | 2027 Q1–Q2         |
| E4 heating-rate spectroscopy     | Spectrally resolved S\_E(ω) near trap frequency                                    | PRL                                                    | 2027 Q2–Q4         |
| E5 force sensing                 | Grating-enhanced force sensitivity benchmark                                       | PRL or Nature Physics (if SQL connection demonstrated) | 2028+              |

The path to a high-impact result runs through E4: spectrally resolved anomalous-heating-rate measurements. This is where the grating framework stops being a pedagogical convenience and becomes an enabling tool for a measurement that was previously inaccessible. If the spectral shape of S\_E(ω) near ω\_mode contains structure — and there are theoretical reasons to expect this from patch-potential models and adsorbate dynamics — then the grating protocol is the right instrument to reveal it.

***

### 13. High-Ground Summary

**Standard Ramsey** is a two-path interferometer in time. Resolution is set by τ. It is simple, has a single sinusoidal fringe (no ambiguity), and imposes minimal control demands.

**The active phase grating** is a multi-path interferometer in time. Resolution is set by NΔt. It acts as a spectral filter on detuning (or motional frequency), and can operate as a high-gain discriminator. But:

> _**Steeper slope is purchased with reduced capture range, increased structural complexity, enhanced sensitivity to control imperfections, and compulsory sensitivity-function engineering.**_

The optimum N is finite in any realistic setting. Finding it requires computing all five figures of merit, not just the fringe width. The development roadmap (theory layers T1–T4, numerical steps N1–N5, experiments E1–E5) defines a path from the pedagogical framework through validated simulation to experimental demonstration, with spectrally resolved heating-rate spectroscopy as the milestone that transforms the grating from a method into a measurement.

***

### References

* Dick, G. J. (1987). Local oscillator induced instabilities in trapped ion frequency standards. _Proc. 19th PTTI_, pp. 133–147.
* Hasse, F., Palani, D., Thomm, R., Warring, U., & Schaetz, T. (2024). Phase-stable travelling waves stroboscopically matched for super-resolved observation of trapped-ion dynamics. _Phys. Rev. A_, 109, 053105.
* Huntemann, N., Lipphardt, B., Okhapkin, M., Tamm, Chr., Peik, E., Taichenachev, A. V., & Yudin, V. I. (2012). Generalized Ramsey excitation scheme with suppressed light shift. _Phys. Rev. Lett._, 109, 213002.
* Lemonde, P., Santarelli, G., Laurent, P., Pereira Dos Santos, F., Clairon, A., & Salomon, C. (1998). Sensitivity function approach for frequency standards. _Proc. IEEE Int. Freq. Control Symp._, pp. 110–115.
* Quessada, A., Kovacich, R. P., Courtillot, I., Clairon, A., Santarelli, G., & Lemonde, P. (2003). The Dick effect for an optical frequency standard. _J. Opt. B: Quantum Semiclass. Opt._, 5, S150–S154.
* Santarelli, G., Audoin, C., Makdissi, A., Laurent, P., Dick, G. J., & Clairon, A. (1998). Frequency stability degradation of an oscillator slaved to a periodically interrogated atomic resonator. _IEEE Trans. UFFC_, 45(4), 887–894.
* Schioppo, M., et al. (2017). Ultrastable optical clock with two cold-atom ensembles. _Nature Photon._, 11, 48–52.
* Yun, P., Zhang, Y., Liu, G., et al. (2012). Multipulse Ramsey-CPT interference fringes for the ⁸⁷Rb clock transition. _EPL_, 97, 63004.
* Yudin, V. I., Taichenachev, A. V., Oates, C. W., Barber, Z. W., Lemke, N. D., Ludlow, A. D., Sterr, U., Lisdat, Ch., & Riehle, F. (2010). Hyper-Ramsey spectroscopy of optical clock transitions. _Phys. Rev. A_, 82, 011804(R).
* Zanon-Willette, T., et al. (2018). Composite laser-pulses spectroscopy for high-accuracy optical clocks: a review of recent progress and perspectives. _Rep. Prog. Phys._, 81, 094401.

***

**Council Review Status**

* **Guardian:** Cleared. No veto. Three flags raised (Sections 6, 7.3, 7.5) and incorporated as corrections.
* **Architect:** Awaiting review on implementability of simulation protocol (Section 11) and experimental feasibility estimates.
* **Integrator:** Awaiting synthesis into Harbour documentation.
