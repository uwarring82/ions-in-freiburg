---
description: A Clean Mapping and Its Limits
---

# Active Phase Grating vs. Standard Ramsey

**Stewardship:** U. Warring.\
**Version:** 0.4 (draft) — February 2026\
**External constraints:** Dick (1987); Santarelli et al. (1998); Yudin et al. (2010); Huntemann et al. (2012); Hasse et al. (2024, PRA 109, 053105)

***

## Revision History

|Version|Date    |Changes                                                                                                                                                                                                                                                                                                                        |
|-------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|0.1    |Feb 2026|Initial Guardian-reviewed draft                                                                                                                                                                                                                                                                                                |
|0.2    |Feb 2026|Added development roadmap (T1–T4, N1–N5, E1–E5), publication trajectory                                                                                                                                                                                                                                                        |
|0.3    |Feb 2026|Integrated Scout flags (CCUF mapping, tier boundaries, quantum limits), Architect review (FIR framing, apodisation), Supervisor phrasing corrections                                                                                                                                                                           |
|0.4    |Feb 2026|**Major structural revision.** Fixed-cycle-time framing replaces variable-time comparison. Two-use distinction (composite replacement vs. stroboscopic selector) made explicit. Three-family simulation architecture defined. Duty-cycle penalty absorbed into Dick-effect analysis. Costs revised under equal-time constraint.|

-----

## 1. Purpose and Scope

This essay establishes the **active phase grating** as a pedagogical and operational framework for understanding multi-pulse analysis trains in stroboscopic trapped-ion spectroscopy. It maps the analogy to spatial diffraction gratings, locates where the mapping is safe, identifies where it breaks, and defines the quantitative figures of merit required to compare the grating approach against standard Ramsey interferometry on metrological ground.

The intended audience is the experimental crew working on FH24-derived stroboscopic protocols (Hasse et al. 2024, PRA 109, 053105), including new doctoral researchers. The essay should be read alongside the qubit-only simulation code, which provides numerical ground truth for the claims made here.

> **Harbour Policy.** This document is a Sail (working essay), not a Coastline (stable framework). It may be revised as experimental data accumulates. The Lock is the metrological comparison methodology; the Keys are the specific parameter choices, which remain free.

### 1.1 Tier Classification

This document operates across two Harbour tiers. The boundary is architecturally significant.

- **Tier 1b (Metrological Clocks / Measurement):** The grating response function, sensitivity function g(t), Dick-effect analysis, and all figures of merit that characterise the measurement operator.
- **Tier 2 (Coordination / Feedback):** Capture-range constraints, side-lobe false-lock analysis, discriminator lock stability, and closed-loop Allan deviation.

Sections are labelled [T1b] or [T2] where the distinction matters.

-----

## 2. Two Distinct Uses of a Pulse Train in Ramsey Spectroscopy

Before developing the grating framework, we must distinguish two fundamentally different reasons for replacing a single π/2 pulse with a train of sub-pulses. Conflating them leads to incorrect assessments of when the technique is powerful and when it is not.

### 2.1 Use A: Composite π/2 Replacement (Robustness Engineering)

Replace a single π/2 with a train of sub-pulses summing to π/2, all at the same detuning, to gain robustness against pulse imperfections. The gains are entirely in the error model:

- **Filter-function engineering:** The train modifies the experiment’s sensitivity function g(t) and can place notches at frequencies where LO phase noise or technical lines dominate.
- **Amplitude/detuning robustness:** Intelligent choice of phases and timings (BB1, SK1, WALTZ, Hyper-Ramsey) can make the effective π/2 less sensitive to Ω miscalibration and static detuning.
- **Transient suppression:** Distributing area over several weaker pulses can average or cancel AOM rise-time, chirp, Stark-shift transients, and AM-to-PM conversion.

**When Use A helps:** If the dominant limitation is pulse imperfections, light-shift transients, or spectrally structured decoherence during the Ramsey zones.

**When Use A does not help:** If pulses are already clean and the system is projection-noise limited, a π/2 is a π/2. Splitting it buys nothing fundamental; it only reshapes technical error couplings. It can actively hurt if extra pulses add light shifts, spontaneous scattering, or convert amplitude noise into phase noise.

This is well-trodden composite-pulse territory. The relevant literature is Yudin et al. (2010), Huntemann et al. (2012), and the comprehensive review by Zanon-Willette et al. (2018).

### 2.2 Use B: Stroboscopic Spectral Selector (Measurement Engineering)

Replace the analysis operation with a train whose inter-pulse spacing Δt is matched to a **physical frequency of interest** — the motional mode period in FH24. The total area is still π/2, but the train’s purpose is not robustness. It is **spectral selectivity**: the train acts as a narrow-band filter centred on 1/Δt, enhancing sensitivity to that frequency component while suppressing others.

**When Use B helps:** When you need frequency-selective readout of a specific motional component, or when you want to engineer the discriminator slope for a known target frequency.

**When Use B does not help:** If the target frequency is already well-resolved by standard Ramsey, or if the additional control complexity introduces errors that exceed the spectral-selectivity gain.

**This Sail addresses Use B.** The FH24 regime — Raman-driven Mg⁺ transitions, Ω/2π in the low-MHz range, pulse durations ∼100 ns, Δt ∼ 770 ns matched to ω_LF ∼ 2π × 1.3 MHz — is not limited by pulse imperfections. It is limited by the need to resolve motional dynamics stroboscopically. The grating framework is the right tool for this regime.

The two uses are **not mutually exclusive**. One could apodise pulse areas for side-lobe suppression (Use B optimisation) while simultaneously phase-stepping for light-shift cancellation (Use A optimisation). But the design intents are distinct and should not be conflated in analysis.

-----

## 3. The Safe Part of the Analogy [T1b]

### 3.1 Ramsey as a Double Slit in Time

Standard Ramsey interferometry maps onto a two-path interferometer in time. A first π/2 pulse creates a superposition. Free evolution for duration τ accumulates relative phase Δτ. A second π/2 pulse recombines the paths. The output ⟨σ_z⟩ = −cos(Δτ) produces fringes with width ∼ 1/τ. Two coherent contributions; resolution set by total interrogation time.

### 3.2 The N-Pulse Train as a Diffraction Grating

Replace the second π/2 with N weak pulses of individual area (π/2)/N, separated by gaps Δt. The amplitude:

> A(Δ) ∝ Σ_{j=0}^{N−1} w_j exp(i Δ t_j)

For equal weights and spacing, this reduces to the N-slit grating factor:

> A(Δ) ∝ sin(NΔ·Δt/2) / sin(Δ·Δt/2)

Main-lobe width scales as 1/(NΔt). Side lobes appear at multiples of 2π/Δt.

**Signal-processing framing:** The train implements a Finite Impulse Response (FIR) filter in quantum state space. The pulse areas are filter coefficients; the inter-pulse gaps set the sampling period. Standard filter-design techniques (windowing, optimal tapering) apply directly to pulse-sequence engineering.

### 3.3 The Mapping Table

|Spatial Grating       |Stroboscopic Train        |Role                                    |
|----------------------|--------------------------|----------------------------------------|
|Slit spacing d        |Pulse spacing Δt          |Sets fringe period / free spectral range|
|Number of slits N     |Number of pulses N        |Sets resolving power                    |
|Field superposition   |Quantum amplitude addition|Interference mechanism                  |
|Phase plate at slit   |Per-pulse phase φ         |Steers / blazes the pattern             |
|Slit-width apodisation|Pulse-area shaping        |Side-lobe suppression                   |
|Total aperture Nd     |Total aperture NΔt        |Resolution limit                        |

-----

## 4. The Critical Caveat: Active vs. Passive

> **⚠ Guardian Flag.** The grating analogy is safe only when the distinction between passive apertures and active SU(2) rotations is made explicit.

In a passive grating, amplitudes superpose without back-action. In the stroboscopic train, each “slit” is an **active SU(2) rotation** interleaved with detuning-driven z-precession. Pulses and free-precession generally **do not commute**. Three consequences:

**First**, phase manipulation **reshapes** the response, not merely shifts it. Exact cancellation under phase-flipping is a special symmetry point (Δ ≈ 0, negligible gap rotation); away from it, the pattern reappears in modified form. Interference does not disappear generically — it is restructured by the active dynamics.

**Second**, the weights w_j depend on the accumulated unitary evolution up to pulse j. The grating formula is a linearised approximation valid for small pulse areas and small detunings, not an exact decomposition.

**Third**, error accumulation in the active train can scale as N for correlated errors (multiplicative compounding through sequential SU(2) operations), unlike passive gratings where fabrication errors contribute independently.

-----

## 5. The Fixed-Cycle-Time Fairness Constraint

### 5.1 The Principle

Previous versions of this document compared Ramsey and grating sequences that could differ in total cycle time, making the comparison vulnerable to a trivial confound: longer interrogation always wins if time is not controlled for.

The correct comparison **fixes the total cycle time**:

> T_cyc = T_prep + T_free + T_ana = constant

In standard Ramsey, T_free is a contiguous block where g(t) ≈ 1 (idealised), and the π/2 pulses are short boundary operations.

In the active phase grating sequence, the free evolution is **not removed — it is distributed into the gaps** between pulses within the prep and/or analysis trains. The total available detuning phase accumulation Δ × (time with Ω = 0) can be kept the same as Ramsey.

**What changes is the temporal weighting of phase sensitivity:** g(t) becomes a structured (comb-like) waveform instead of a flat plateau.

### 5.2 The High-Ground Statement

Under fixed T_cyc, the grating’s claim is not “we used longer interrogation.” It is:

> ***We engineered g(t), and therefore engineered the frequency response and the noise aliasing of the discriminator, under the same time budget.***

This is the only honest metrological claim. Everything that follows must be evaluated under this constraint.

### 5.3 The Fairness Protocol

Use fixed T_cyc and fixed pulse durations δt (FH24-like), and enforce the same net beam-splitter action:

- Prep train total area: Σ θ_j = π/2
- Analysis train total area: Σ θ_j = π/2
- All additional “waiting” is realised as gaps where Ω = 0

The only knobs being compared are: how the π/2 actions are distributed in time, where the free evolution is placed, and phase conventions (working-point setting via φ_ana, plus any per-pulse phase pattern).

-----

## 6. What You Gain Under Fixed Cycle Time [T1b]

### 6.1 Higher Discriminator Slope Without Longer Cycles

For equal T_cyc, a multi-pulse structure can produce a steeper local slope around the working point because the response can develop a narrower central feature through temporal multi-path interference (the grating effect). This narrowing comes from the structured g(t), not from extended interrogation.

This is most effective when pulses are weak enough that the “sum of contributions” picture remains approximately valid, and the gap structure creates a strong comb factor in the response.

In the idealised case (unit contrast, negligible pulse-area error):

> S(N) ∼ N · Δt

> **⚠ Guardian Flag.** This scaling assumes unit contrast, negligible pulse-area error, and operation at the exact working point. It does not account for the costs enumerated in Section 7.

### 6.2 Engineered LO-Noise Coupling (Dick Engineering)

Because g(t) changes shape, the Dick weighting changes. Under equal T_cyc, this is the **central metrological reason** to use a grating sequence. Depending on the LO noise spectrum:

- The grating can **suppress** aliasing at harmful Fourier components (place zeros of g_n where S_y is large), or
- It can **catastrophically enhance** aliasing (if large g_n coincide with noisy harmonics).

The question that determines whether the grating wins is:

> Does the reshaped g(t) improve the ratio (slope) / (noise floor at discriminator output) under the actual LO and control-noise spectra?

### 6.3 CCUF Parameter Mapping

- **T_ap = NΔt** is the comparison length L_comparison, now embedded within the fixed cycle time rather than extending it.
- **Causal efficiency** η = L_comparison / cτ_total measures how the fixed cycle budget is distributed between sensing and driving.
- **Correlation length** ξ of the noise source imposes: N_max ≈ ξ/Δt. Beyond this, additional pulses add noise sensitivity without adding signal. Under fixed T_cyc, this constraint also means: if N > N_max, the time budget would be better spent on longer contiguous free evolution (i.e., revert to Ramsey).

-----

## 7. What You Pay Under Fixed Cycle Time: Revised Costs

With interleaved wait, the cost structure changes. **You have not paid time; you have paid actuation count and structural complexity.** The previous duty-cycle penalty (v0.3 §7.5) is absorbed into the Dick analysis — it is not an independent cost under fixed T_cyc.

### 7.1 Control-Noise Accumulation: The Dominant New Price [T1b]

Under fixed T_cyc, this becomes the primary cost. You have introduced many more opportunities for amplitude, phase, and timing error:

- **Uncorrelated errors** → net effect scales as √N
- **Correlated errors** (common in real labs: systematic miscalibration, thermal drift, AOM response) → effective detuning offset and contrast loss scale as N

The √N-to-N transition depends on the correlation length of the control noise relative to the train duration. Determining this transition for a specific apparatus is the single most important task for the numerical programme.

### 7.2 Reduced Capture Range [T2]

The narrower central feature means a smaller monotonic region for locking. Under fixed T_cyc, this is no longer masked by different total times. If the LO has excursions exceeding ∼ 1/(NΔt), the discriminator cannot track. Mitigation: apodisation (Blackman-Harris or Kaiser window pulse-area weighting), or multi-step acquisition (Ramsey lock → grating handoff).

**Tier boundary note:** This is a T1b → T2 degradation pathway. The measurement’s resolution exceeds the control system’s ability to exploit it.

### 7.3 Side-Lobe Ambiguity [T2]

N − 1 side lobes between principal maxima. Each a potential false-lock point. Under fixed T_cyc, the side-lobe structure is a feature of the g(t) comb, not of extended interrogation. Apodisation and multi-step protocols apply as before.

### 7.4 Model Dependence [T1b]

Standard Ramsey’s mapping between Δ and output is simple and robust: ⟨σ_z⟩ = −cos(Δτ). The grating sequence’s mapping depends sensitively on pulse timing, phases, and the full unitary chain. This raises calibration demands: the crew must measure the actual transfer function, not merely predict it from ideal parameters. Any deviation between the model and the apparatus produces systematic errors in the extracted detuning.

### 7.5 Dick-Effect Reshaping [T1b + T2, coupled]

Under fixed T_cyc, this replaces the old “duty-cycle penalty” as the noise-budget cost. The sensitivity function g(t) for the N-pulse train has a comb-like structure with Fourier coefficients g_n that determine aliased noise:

> σ_y²(1s) = (2/g₀²) Σ_n |g_n|² S_y(n/t_c)

Whether this is better or worse than Ramsey depends entirely on the match between {g_n} and S_y(f). The Dick computation is mandatory and apparatus-specific.

-----

## 8. How to Compare Fairly: The Working-Point Protocol

### 8.1 The Five-Step Protocol

1. **Set the working point** [T1b] by adjusting φ_ana so that ⟨σ_z⟩ = 0 at Δ = 0.
1. **Compute the local slope** [T1b] S_N = ∂⟨σ_z⟩/∂Δ at Δ = 0.
1. **Measure the linear capture range** [T2]: width of monotonic region around working point.
1. **Quantify the side-lobe ratio** [T2]: largest parasitic slope relative to main-lobe slope.
1. **Compute the Dick-limited noise floor** [T1b + T2]: σ_y(N) under the actual LO noise model.

The combined figure of merit is:

> FoM(N) = S(N) / √(σ_y²(N) + σ_proj²)

evaluated at fixed T_cyc. This is the quantity that determines whether the grating wins.

### 8.2 The Three-Family Comparison

All families share the same T_cyc, the same total beam-splitter area (π/2 + π/2 = π), and the same working-point protocol.

|Family               |Prep                    |Free Evolution              |Analysis                |
|---------------------|------------------------|----------------------------|------------------------|
|**Ramsey baseline**  |Single π/2 pulse        |Contiguous wait             |Single π/2 pulse        |
|**One-sided grating**|Single π/2 pulse        |Distributed in analysis gaps|N-pulse train (Σθ = π/2)|
|**Two-sided grating**|N-pulse train (Σθ = π/2)|Distributed in both gap sets|N-pulse train (Σθ = π/2)|

The simulation sweeps N from 1 to 20 for each family, extracting all five quantities at each point. The comparison reveals whether one-sided or two-sided gratings outperform Ramsey, and whether the two-sided variant gains over one-sided or merely multiplies control sensitivity.

-----

## 9. The Pedagogical Safeguard

> **Teaching rule.** When presenting the grating analogy, always state both halves: (1) the mathematical structure is identical to N-slit diffraction; (2) the slits are active SU(2) rotations, not passive apertures, so the weights depend on the control Hamiltonian and the analogy breaks under phase manipulation at finite detuning.

-----

## 10. The Complete Figure-of-Merit Set

|Figure of Merit               |Symbol             |Tier  |Ramsey Baseline    |Grating (Ideal, Fixed T_cyc)           |
|------------------------------|-------------------|------|-------------------|---------------------------------------|
|Discriminator slope           |S = ∂⟨σ_z⟩/∂Δ      |T1b   |∼ τ_free           |∼ NΔt (if N contributes)               |
|Linear capture range          |Δ_cap              |T2    |∼ 1/τ_free         |∼ 1/(NΔt)                              |
|Side-lobe ratio               |r_SL               |T2    |0 (single sinusoid)|∼ 1/N (first side lobe)                |
|Control-noise-equivalent error|δΔ_ctrl            |T1b   |Two-pulse errors   |√N or N scaling                        |
|Dick-limited noise floor      |σ_y(Dick)          |T1b+T2|g(t) ≈ flat plateau|g(t) comb-like; apparatus-specific     |
|Combined FoM                  |S/√(σ_y² + σ_proj²)|T1b+T2|Baseline           |Must exceed baseline to justify grating|

### 10.1 Quantum Limits

- **SQL:** δΔ_SQL = 1/(S · √N_rep). The grating increases S but does not increase N_rep under fixed T_cyc. Net gain only if S grows relative to noise.
- **Heisenberg Limit:** Not approached. The N-path structure improves classical resolving power, not quantum-enhanced sensitivity. The grating is a SQL-level instrument with engineered spectral selectivity.
- **Measurement back-action:** In motional coupling (E3–E5), N pulses impart cumulative momentum kicks. Theory Layer T3 must quantify this.

-----

## 11. Development Roadmap

### 11.1 Theory Programme

**T1: Exact sensitivity function g(t) for the N-pulse train** under fixed T_cyc. Derive Fourier coefficients g_n(N, Δt, θ_pulse) via the Santarelli–Lemonde formalism. Deliverable: semi-analytic expression valid beyond the small-area limit.

**T2: Optimal N under realistic noise.** Given g_n(N) and measured S_y(f), compute:

> N* = argmax_N [ S(N) / √(σ_y²(N) + σ_proj²) ]

Include the CCUF ceiling N_max ≈ ξ/Δt. Determine whether N* is robust or fragile.

**T3: Spin-motion coupling.** Derive g(t; η, n̄) in the Lamb-Dicke regime. Quantify contrast degradation from motional heating during the train. Key question: can the grating resolve closely spaced motional modes? Quantify measurement back-action.

**T4 (speculative): Force sensing.** Derive δF(N) and compare against SQL. Characterise sensitivity–bandwidth product.

### 11.2 Numerical Programme

**N1: Three-family working-point comparison (qubit-only).** Fixed T_cyc. For each family (Ramsey, one-sided, two-sided) and N = 1–20: find φ_ana, extract all six figures of merit. Include uniform-weight and apodised (Blackman-Harris) variants. Deliverable: single summary figure, six panels, three families overlaid.

**N2: Control-noise injection.** Sweep amplitude noise (δθ/θ: 10⁻³–10⁻¹), timing jitter (δ(Δt)/Δt: 10⁻⁴–10⁻²), phase drift. Find N*(noise) for each family. Map the √N-to-N transition.

**N3: Dick-effect evaluation.** Compute g(t) numerically for each family and N. Extract g_n. Given representative S_y(f), compute σ_y(N). Verify N* from T2.

**N4: Spin-motion simulation.** Fock-space truncation (n_max ∼ 20), η = 0.1–0.4, n̄ = 0–10, heating rate. Motional-frequency transfer function for each family.

**N5: Two-mode resolution test.** Second mode at ω₂ = ω₁ + δω. Minimum resolvable splitting vs N. Compare families.

### 11.3 Experimental Programme

**E1: Qubit-only validation.** N-pulse train on single Ba⁺. Verify narrowing, slope, capture range vs. simulation. Fixed T_cyc. 2–4 weeks.

**E2: Discriminator lock.** Closed-loop stability (Allan deviation) vs. N, compared against Ramsey at same T_cyc. Tests Dick prediction. 2–4 weeks beyond E1.

**E3: Stroboscopic motional spectroscopy.** FH24 core. Δt matched to ω_LF. Motional-frequency transfer function. Mode-splitting resolution test.

**E4: Heating-rate spectroscopy (PRL target).** Spectrally resolved S_E(ω) near ω_mode. New capability if spectral structure is revealed.

**E5: Force sensitivity (long shot).** Narrow-band force sensor. SQL comparison. Sensitivity–bandwidth product.

-----

## 12. Publication Trajectory

|Milestone                       |Content                                                      |Target                  |Timeline       |
|--------------------------------|-------------------------------------------------------------|------------------------|---------------|
|Sail + simulation (T1–T2, N1–N3)|Methods: fixed-T_cyc framework, three families, Dick analysis|PRA or NJP              |2026 Q3–Q4     |
|E1 + E2 validation              |Experimental grating narrowing + discriminator lock          |PRA(R) or included above|2026 Q4–2027 Q1|
|E3 motional spectroscopy        |Transfer function, mode splitting                            |PRA or PRL              |2027 Q1–Q2     |
|E4 heating-rate spectroscopy    |Spectrally resolved S_E(ω)                                   |PRL                     |2027 Q2–Q4     |
|E5 force sensing                |SQL comparison                                               |PRL or Nat. Phys.       |2028+          |

-----

## 13. High-Ground Summary

**Standard Ramsey** is a two-path interferometer in time. Within a fixed cycle budget, it places free evolution in a contiguous block, producing a flat sensitivity function g(t) and a single sinusoidal fringe.

**The active phase grating** redistributes the same free evolution into gaps between active SU(2) pulses. Under fixed cycle time, the claim is not longer interrogation. It is:

> ***Engineered g(t) — and therefore engineered frequency response and noise aliasing — within the same time budget.***

The gain is a steeper discriminator slope from temporal multi-path interference. The price is:

> ***Increased actuation count (control-noise accumulation), reduced capture range, side-lobe ambiguity, model dependence, and apparatus-specific Dick-effect reshaping.***

Whether the gain outpaces the price depends on the actual LO noise spectrum, the control-error statistics, and the target measurement. The grating wins when the reshaped g(t) suppresses the dominant noise source while the control chain supports the higher actuation count. It loses when it doesn’t.

The optimum N is finite, bounded above by N_max ≈ ξ/Δt (CCUF constraint) and below by the minimum resolving power required. Finding it requires computing the combined figure of merit S(N)/√(σ_y²(N) + σ_proj²) under the fixed-cycle-time protocol, not just the fringe width.

-----

## 14. A Practical Decision Rule

For the crew, a short bottom line:

- **If your limitation is pulse imperfections / light-shift transients / detuning error** → Use A (composite replacement) is the right tool. This Sail does not address that regime; consult the Hyper-Ramsey literature.
- **If your limitation is free-evolution dephasing and you are near ideal Ramsey** → A train inside the Ramsey zones usually gives little, and can cost you via extra light shifts / scattering.
- **If you need frequency-selective readout of a specific motional component (FH24 regime)** → Use B (stroboscopic selector) applies. This Sail provides the framework, and the three-family comparison determines whether the grating outperforms Ramsey for your specific noise environment.
- **In all cases:** the three-family simulation at fixed T_cyc is the arbiter. Run it with your actual parameters before committing to a grating protocol.

-----

## References

- Dick, G. J. (1987). Local oscillator induced instabilities in trapped ion frequency standards. *Proc. 19th PTTI*, pp. 133–147.
- Hasse, F., Palani, D., Thomm, R., Warring, U., & Schaetz, T. (2024). Phase-stable travelling waves stroboscopically matched for super-resolved observation of trapped-ion dynamics. *Phys. Rev. A*, 109, 053105.
- Huntemann, N., Lipphardt, B., Okhapkin, M., Tamm, Chr., Peik, E., Taichenachev, A. V., & Yudin, V. I. (2012). Generalized Ramsey excitation scheme with suppressed light shift. *Phys. Rev. Lett.*, 109, 213002.
- Lemonde, P., Santarelli, G., Laurent, P., Pereira Dos Santos, F., Clairon, A., & Salomon, C. (1998). Sensitivity function approach for frequency standards. *Proc. IEEE Int. Freq. Control Symp.*, pp. 110–115.
- Quessada, A., Kovacich, R. P., Courtillot, I., Clairon, A., Santarelli, G., & Lemonde, P. (2003). The Dick effect for an optical frequency standard. *J. Opt. B: Quantum Semiclass. Opt.*, 5, S150–S154.
- Santarelli, G., Audoin, C., Makdissi, A., Laurent, P., Dick, G. J., & Clairon, A. (1998). Frequency stability degradation of an oscillator slaved to a periodically interrogated atomic resonator. *IEEE Trans. UFFC*, 45(4), 887–894.
- Schioppo, M., et al. (2017). Ultrastable optical clock with two cold-atom ensembles. *Nature Photon.*, 11, 48–52.
- Yun, P., Zhang, Y., Liu, G., et al. (2012). Multipulse Ramsey-CPT interference fringes for the ⁸⁷Rb clock transition. *EPL*, 97, 63004.
- Yudin, V. I., Taichenachev, A. V., Oates, C. W., Barber, Z. W., Lemke, N. D., Ludlow, A. D., Sterr, U., Lisdat, Ch., & Riehle, F. (2010). Hyper-Ramsey spectroscopy of optical clock transitions. *Phys. Rev. A*, 82, 011804(R).
- Zanon-Willette, T., et al. (2018). Composite laser-pulses spectroscopy for high-accuracy optical clocks: a review of recent progress and perspectives. *Rep. Prog. Phys.*, 81, 094401.

-----

## Council-5 Review Status

|Stance        |Status                            |Notes                                                                                                                                          |
|--------------|----------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
|**Guardian**  |Cleared                           |Flags on scaling conditions (§6.1), error accumulation (§7.1), active/passive caveat (§4). All incorporated. No veto.                          |
|**Architect** |Cleared                           |FIR framing (§3.2), apodisation protocol (§7.2), three-family architecture (§8.2). Sensitivity function T1 prioritised.                        |
|**Integrator**|Pending                           |Awaiting synthesis into Harbour documentation.                                                                                                 |
|**Scout**     |Cleared                           |CCUF mapping (§6.3), tier boundaries (§1.1), quantum limits (§10.1), composite territory (§2.1). All addressed.                                |
|**Verifier**  |Pending                           |Scaling claims to be verified against N1 simulation output. Literature anchors spot-checked.                                                   |
|**Supervisor**|Structural correction incorporated|Fixed-T_cyc framing (§5), two-use distinction (§2), three-family comparison (§8.2), revised cost structure (§7), practical decision rule (§14).|
