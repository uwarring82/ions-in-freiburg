---
description: An Operator's Handbook – Part of the Ordinans Series
---

# L–Single-Spin–Single-Mode Quantum Dynamics

{% hint style="info" %}
author: _U. Warring_\
affiliation: _Institute of Physics, University of Freiburg_\
_version: 0.2.1_\
last\_updated: _2025-12-17_\
license: _CC BY 4.0_\
\
**Disclaimer** – This handbook is a conceptual and pedagogical synthesis intended to clarify minimal models, regimes, and design principles for single-spin–single-mode quantum dynamics; it does not claim completeness, universality, or direct applicability to all experimental platforms. Any emulation of bath-like or power-law behaviour discussed here is finite, state-dependent, and explicitly bounded by the assumptions and cutoffs stated in the text.<br>
{% endhint %}

### How to Cite This Handbook

**Stable citation format**:

> Warring, U. (2025). _Single-Spin–Single-Mode Quantum Dynamics: An Operator's Handbook_ (Version 0.2.1). Ordinans Series.

**Version-specific**: Always cite the version number. Sections may evolve in subsequent versions; backward compatibility is maintained for numbered sections.

**For specific results**: When citing particular equations or claims, reference the section number (e.g., "Section 4.9, Eq. for IPR").

***

## PART I — INVARIANT CORE

### 1. Scope, Philosophy, and Minimality

#### 1.1 Scope

Single-spin–single-mode quantum dynamics refers to the physics of a single two-level quantum system (a spin-½ or qubit) interacting with a single quantised harmonic oscillator mode. This minimal composite system—essentially the quantum Rabi model—is a cornerstone of quantum optics and quantum information, underlying phenomena from cavity QED to trapped-ion quantum logic.

#### 1.2 Thesis

Even this ostensibly simple system generates complex quantum dynamics. By tuning system parameters, preparing different initial states, or allowing environment coupling, one can explore diverse regimes—from exactly solvable models to chaotic-like behaviour—and gain insight into larger many-body or open quantum systems.

This handbook develops a unified framework for single-spin–single-mode dynamics, organised into six parts:

<table><thead><tr><th width="78.45623779296875">Part</th><th width="224.71875">Title</th><th>Content</th></tr></thead><tbody><tr><td>I</td><td>Invariant Core</td><td>Hamiltonians, symmetries, regime boundaries</td></tr><tr><td>II</td><td>Dynamics from Simplicity</td><td>Manifold-resolved dynamics, initial-state complexity</td></tr><tr><td>III</td><td>From Closed to Open</td><td>Single mode as environment, memory effects, dissipation</td></tr><tr><td>IV</td><td>Analytic Tools</td><td>Solution recipes, approximation validity</td></tr><tr><td>V</td><td>The Trapped-Ion Platform</td><td>Hamiltonian engineering, experimental knobs</td></tr><tr><td>VI</td><td>Horizons</td><td>Open questions, what this handbook enables</td></tr></tbody></table>

#### 1.3 The Minimality Theorem

> **What Makes This Minimal?**
>
> The spin–mode duo is minimal in the information-theoretic sense: it is the smallest Hilbert space that admits (i) non-commuting observables on both subsystems, (ii) entanglement, and (iii) a tunable symmetry-breaking term (the coupling).
>
> Adding spatial degrees of freedom or more modes does not introduce new _classes_ of phenomena—only more parameters. This handbook shows that collapse, revival, effective non-Markovianity, and time-dependent energy renormalisation are already present here; they are not emergent from thermodynamic limits.

#### 1.4 The Exportability Principle

The single-spin–single-mode system serves as a _reference implementation_. Any phenomenon demonstrated here can be exported to larger systems with confidence that the essential physics is understood. Conversely, claims about multi-mode systems should be benchmarked against this minimal case: if the phenomenon requires more than one mode, that is significant; if it does not, the single-mode setting offers cleaner analysis.

***

### 2. Canonical Hamiltonians and Symmetries

#### 2.1 The Quantum Rabi Hamiltonian

The generic Hamiltonian for a spin-½ (two-level atom or qubit) interacting with a single mode is:

$$H = \frac{\hbar \omega_0}{2}\sigma_z + \hbar \omega , a^\dagger a + \hbar g , (\sigma^+ + \sigma^-)( a + a^\dagger)$$

where:

* $$\omega_0$$ is the spin's transition frequency
* $$\omega$$ is the oscillator frequency
* $$a^\dagger$$, $$a$$ are the mode's creation/annihilation operators
* $$g$$ is the coupling strength
* $$\sigma_z$$, $$\sigma^\pm$$ are Pauli operators on the two-level system

This quantum Rabi Hamiltonian is invariant under a $$\mathbb{Z}_2$$ parity transformation (flipping the sign of both spin-$$\sigma_x$$ and oscillator quadrature)—a symmetry that yields a conserved parity operator:

$$\Pi = \sigma_z (-1)^{a^\dagger a}$$

#### 2.2 The Jaynes–Cummings Model

In the rotating-wave approximation (valid when $$g \ll \omega, \omega_0$$ and $$\omega \approx \omega_0$$), one drops the non-energy-conserving terms $$\sigma^+ a^\dagger$$ and $$\sigma^- a$$, recovering:

$$H_{\text{JC}} = \frac{\hbar \omega_0}{2}\sigma_z + \hbar \omega \, a^\dagger a + \hbar g \, (\sigma^+ a + \sigma^- a^\dagger)$$

The Jaynes–Cummings model conserves the total excitation number:

$$N = a^\dagger a + \frac{1}{2}(1 + \sigma_z)$$

This exact invariant simplifies the solution: the Hilbert space decomposes into independent two-dimensional subspaces $${|e, n\rangle, |g, n+1\rangle}$$ for each excitation number.

> **Exactness Disclaimer**
>
> The JC model is analytically diagonalisable but physically approximate. Its exactness is a mathematical property of the truncated Hamiltonian, not a claim about nature. The counter-rotating terms are always present; we are operating in a regime where their effect is emulable by a Lamb shift, not a dynamical process.
>
> This is the first example of the handbook's core principle: _exactness is a function of the question asked, not the Hamiltonian written down_.

#### 2.3 The Operator's Decision Tree (The Navigator)

```
START: Define System Parameters
           │
           ▼
    ┌──────────────────┐
    │  Calculate g/ω   │
    └──────────────────┘
           │
     ┌─────┴─────┬──────────────┐
     ▼           ▼              ▼
  g/ω ≪ 1    0.1 < g/ω < 1   g/ω > 1
     │           │              │
     ▼           ▼              ▼
┌─────────┐ ┌─────────┐    ┌─────────┐
│ Weak/   │ │   USC   │    │   DSC   │
│Resonant │ │         │    │         │
└────┬────┘ └────┬────┘    └────┬────┘
     │           │              │
     ▼           ▼              ▼
┌─────────┐ ┌─────────┐    ┌─────────────┐
│Is Δ≈0?  │ │  QRM    │    │ Adiabatic/  │
└──┬───┬──┘ │Z₂ Parity│    │ Polaron     │
   │   │    │(Braak)  │    │ Frames      │
   ▼   ▼    └────┬────┘    └─────────────┘
 Yes   No        │
  │    │         │
  ▼    ▼         │
┌───┐ ┌────┐     │
│JC │ │Disp│     │
│U(1)│ │σ_z │    │
└─┬─┘ └────┘     │
  │              │
  └──────┬───────┘
         ▼
┌─────────────────────┐
│SELECT INITIAL STATE │
│Complexity Generator │
└─────────┬───────────┘
    ┌─────┴─────┬─────────┬──────────┐
    ▼           ▼         ▼          ▼
 |n⟩ Fock   |α⟩ Coh.  |ξ⟩ Sqz.  Thermal
    │           │         │          │
    ▼           ▼         ▼          ▼
 Single     Collapse   Anomalous  Power-law
 Freq Ω_n  & Revival   Revival    Emulation
```

#### 2.4 Regimes of Interaction

| Regime      | Condition                                       | Symmetry         | Hamiltonian         | Approximation |
| ----------- | ----------------------------------------------- | ---------------- | ------------------- | ------------- |
| Dispersive  |  $$g \ll |\Delta|$$, $$g \ll \omega, \omega_0$$ | Eff. $$U(1)$$    |                     |               |
| Resonant JC | $$g \ll \omega$$, $$\Delta \approx 0$$          | $$U(1)$$         | $$H_{\text{JC}}$$   | RWA valid     |
| Ultrastrong | $$0.1 < g/\omega < 1$$                          | $$\mathbb{Z}_2$$ | $$H_{\text{Rabi}}$$ | Braak exact   |
| Deep Strong | $$g/\omega > 1$$                                | $$\mathbb{Z}_2$$ | $$H_{\text{Rabi}}$$ | Polaron frame |

where $$\Delta = \omega - \omega_0$$ is the spin-mode detuning.

**Dispersive Regime** ($$g \ll |\Delta|$$): The spin and oscillator exchange virtual excitations, leading to energy shifts (Lamb/AC Stark) but not real energy exchange. The effective Hamiltonian is:

$$H_{\text{disp}} \approx \hbar \omega \, a^\dagger a + \frac{\hbar}{2}\left(\omega_0 + \frac{g^2}{\Delta}(2 a^\dagger a + 1)\right)\sigma_z$$

> **Validity Condition (Complete)**
>
> The dispersive approximation requires _both_ $$g \ll |\Delta|$$ _and_ $$g \ll \omega, \omega_0$$. The first ensures the perturbation expansion converges; the second ensures the RWA remains valid as a precursor step.

**Resonant Strong Coupling** ($$g$$ moderate, $$\omega \approx \omega_0$$): The dynamics feature Rabi oscillations. If the oscillator has $$n$$ quanta, the spin flips at the Rabi frequency $$\Omega_n = 2g\sqrt{n+1}$$. The energy spectrum splits into doublets separated by the vacuum Rabi splitting $$2g$$.

**Ultrastrong Coupling** ($$0.1 < g/\omega < 1$$): The counter-rotating terms $$\sigma^+ a^\dagger$$ and $$\sigma^- a$$ cannot be neglected. The ground state is no longer the spin-down vacuum $$|g, 0\rangle$$ but a squeezed entangled state containing virtual excitations. The Bloch–Siegert shift becomes appreciable.

> **Common Misconception Alert**
>
> "Ultrastrong coupling means non-perturbative." _False._ The Rabi model is analytically solvable at any $$g/\omega$$ (Braak 2011). The challenge is not solvability but _interpretation_: as $$g \to \omega$$, the notion of separate spin and mode excitations becomes a bad basis choice, not a physical mystery.

**Deep Strong Coupling** ($$g/\omega > 1$$): This extreme regime pushes the interaction beyond perturbative expansions. Even basic notions of separate "spin" and "oscillator" excitations become blurred.

#### 2.5 Key Point: Symmetry as Signpost

The single-spin–single-mode system is governed by a simple Hamiltonian with symmetries that depend on coupling regime:

* **JC limit**: Approximate $$U(1)$$ symmetry (conservation of $$N$$) makes the problem exactly solvable via independent 2×2 blocks.
* **Full Rabi**: Only $$\mathbb{Z}_2$$ parity remains, yet the model is still integrable (Braak 2011).

> **Integrability Clarification**
>
> The Rabi model is integrable in Braak's sense: the spectrum can be determined by transcendental equations involving confluent Heun functions. This is _not_ Liouville integrability (which requires $$N$$ independent constants of motion for $$N$$ degrees of freedom). The discrete parity symmetry suffices for exact solvability but does not simplify dynamics to independent one-dimensional motions.

***

## PART II — DYNAMICS FROM SIMPLICITY

### 3. Manifold-Resolved Dynamics

Within the Jaynes–Cummings approximation, the Hilbert space decomposes into independent manifolds:

$$\mathcal{H} = \mathcal{M}_0 \oplus \mathcal{M}_1 \oplus \mathcal{M}_2 \oplus \cdots$$

where $$\mathcal{M}n = \text{span}{|e, n\rangle, |g, n+1\rangle}$$ _for_ $$n \geq 0$$_, and_ $$\mathcal{M}{-1} = \text{span}{|g, 0\rangle}$$ is the ground state (decoupled).

Within each manifold $$\mathcal{M}_n$$, the Hamiltonian acts as a 2×2 matrix:

$$H_n = \hbar \begin{pmatrix} (n+\tfrac{1}{2})\omega + \tfrac{\Delta}{2} & g\sqrt{n+1} \ g\sqrt{n+1} & (n+\tfrac{1}{2})\omega - \tfrac{\Delta}{2} \end{pmatrix}$$

The eigenstates (dressed states) are:

$$|n, \pm\rangle = \cos\theta_n |e, n\rangle \pm \sin\theta_n |g, n+1\rangle$$

with $$\tan(2\theta_n) = 2g\sqrt{n+1}/\Delta$$, and eigenfrequencies:

$$E_{n,\pm} = \hbar\left[(n+\tfrac{1}{2})\omega \pm \tfrac{1}{2}\sqrt{\Delta^2 + 4g^2(n+1)}\right]$$

***

### 4. Motional Initial States as Complexity Generators

The oscillator's initial state acts as a generator of complexity by controlling the distribution of interaction frequencies and quantum phases in the spin–mode evolution.

#### 4.1 The Distribution Function

Define the Fock-state distribution:

$$p_n = |\langle n | \psi_{\text{mode}}(0) \rangle|^2$$

This distribution $${p_n}$$ plays the role of a _spectral weight_ in excitation space. The spin coherence evolves as:

$$\langle \sigma_+(t) \rangle \approx \sum_{n=0}^{\infty} p_n , e^{-i \Omega_n t} \cdot (\text{amplitude factors})$$

where $$\Omega_n = 2g\sqrt{n+1}$$. The statistics of $$p_n$$ determine the interference pattern.

#### 4.2 Fock States: The Single-Frequency Benchmark

If the mode starts in a Fock state $$|n\rangle$$, the spin undergoes simple Rabi oscillations at a single frequency $$\Omega_n = 2g\sqrt{n+1}$$:

$$P_e(t) = \cos^2\left(g\sqrt{n+1} , t\right)$$

This is the _reference case_: predictable, oscillatory, and non-complex.

#### 4.3 Coherent States: Collapse and Revival

A coherent state $$|\alpha\rangle$$ has Poisson-distributed Fock components:

$$p_n = e^{-|\alpha|^2} \frac{|\alpha|^{2n}}{n!}$$

The spin excitation probability becomes:

$$P_e(t) = \frac{1}{2}\left[1 + \sum_{n=0}^\infty p_n \cos(2g\sqrt{n+1} , t)\right]$$

**Collapse**: The spread of frequencies $${\Omega_n}$$ causes dephasing on timescale:

$$t_{\text{collapse}} \sim (g\sqrt{\langle n \rangle})^{-1}$$

**Revival**: The discrete quantisation allows rephasing at:

$$t_{\text{revival}} \sim \frac{2\pi\sqrt{\langle n \rangle}}{g}$$

The discovery of revivals was a seminal demonstration of field quantisation: revivals are a direct consequence of discrete photon number states, absent in classical or continuum fields.

#### 4.4 Squeezed States: Variance Control

A squeezed state has reduced number uncertainty in certain quadratures. This modifies collapse/revival patterns:

* **Narrower** $$p_n$$: Slower collapse (fewer frequencies interfere)
* **Even/odd parity structure**: Frequency-comb dynamics with substructure in revivals

#### 4.5 Displaced-Squeezed States: Tunable Asymmetry

Combining displacement and squeezing allows independent control of:

* Mean excitation $$\langle n \rangle$$ (sets revival timescale)
* Variance $$(\Delta n)^2$$ (sets collapse rate)
* Parity structure (sets revival substructure)

#### 4.6 Engineered Classical Mixtures: The Power-Law Emulator

> **Key Handbook Statement**
>
> In a single mode, power-law-like behaviour is realised in _excitation space_, not frequency space.

**Motivation**: Many-body physics studies power-law spectral densities $$J(\omega) \sim \omega^s$$. In a single mode, we cannot replicate a continuum, but we can engineer $$p_n$$ to _emulate_ the dynamical signatures of non-Markovian baths.

**Recipe**: Prepare a mixed motional state:

$$\rho_{\text{mode}} = \sum_n p_n |n\rangle\langle n|, \quad p_n \propto (n + n_0)^{-\beta}$$

using stochastically applied sideband pulses. The spin coherence then evolves as:

$$\langle \sigma_+(t) \rangle \approx \sum_n p_n , e^{-i 2g\sqrt{n+1} , t}$$

For large $$n$$ and $$\beta > 1$$, the sum yields an envelope $$\sim t^{-(\beta-1)}$$ up to a cutoff time $$t_c \sim n_{\max}/g$$.

> **Guardian Warning: Emulation Boundary**
>
> This is _emulation_. The underlying Hamiltonian is still JC; there is no bath-induced backflow, only frequency mixing. The power-law envelope is a _signature_, not a physical spectral density. The cutoff $$n_{\max}$$ is not a bath bandwidth but a preparation limit.

#### 4.7 Thermal States: The "Bath" Emulator

A thermal state has:

$$p_n = \frac{\bar{n}^n}{(1+\bar{n})^{n+1}}$$

This causes irreversible-looking damping of Rabi oscillations. The uncertain photon number acts like static disorder, washing out coherent oscillations _without_ revival (since a thermal state has no fixed phase relationship to rephase).

This mimics decoherence even in a closed system, purely due to uncertainty in the initial mode state.

#### 4.8 State Class Summary

| Initial State     | Distribution p\_n    | Dynamics                | Complexity Source        |
| ----------------- | -------------------- | ----------------------- | ------------------------ |
| Fock              | $$n\rangle$$         | $$\delta_{n,n_0}$$      | Single-frequency Rabi    |
| Coherent          | $$\alpha\rangle$$    | Poisson                 | Collapse & revival       |
| Squeezed          | $$ξ\rangle$$         | Sub-Poisson             | Modified revival pattern |
| Thermal           | Bose–Einstein        | Irreversible-like decay | No phase correlation     |
| Power-law mixture | $$(n+n_0)^{-\beta}$$ | Algebraic envelope      | Engineered weight        |

***

### 4.9 An Ordering Parameter in Excitation Space

#### 4.9.1 Definition

For a motional state expanded in the Fock basis with probabilities $$p_n = |\langle n | \psi \rangle|^2$$, the **inverse participation ratio** (IPR) is:

$$\text{IPR} = \sum_{n=0}^{n_{\max}} p_n^2$$

The **effective excitation number** provides intuitive interpretation:

$$N_{\text{eff}} = \frac{1}{\text{IPR}}$$

This quantifies how many Fock states (equivalently, how many JC manifolds) actively participate in the dynamics.

#### 4.9.2 Interpretation Rule

> **Scope Boundary**
>
> In this handbook, the IPR is _not_ a measure of chaos, ergodicity, or thermalisation. It is an **ordering parameter in excitation space** that quantifies how many JC manifolds actively participate in the dynamics.
>
> * **Large IPR** (small $N\_{\text{eff\}}$) → localisation in excitation space; few manifolds dominate; regular dynamics
> * **Small IPR** (large $N\_{\text{eff\}}$) → delocalisation; many manifolds interfere; complex envelopes

This maps directly onto dynamical signatures:

<table><thead><tr><th width="152.27813720703125">IPR Regime</th><th width="130.0250244140625">N_eff</th><th>Dynamical Character</th></tr></thead><tbody><tr><td><span class="math">\text{IPR} \approx 1</span></td><td><span class="math">\approx 1</span></td><td>Single-frequency Rabi oscillation</td></tr><tr><td><span class="math">\text{IPR} \sim \bar{n}^{-1/2}</span></td><td><span class="math">\sim \sqrt{\bar{n}}</span></td><td>Collapse with clean revivals</td></tr><tr><td><span class="math">\text{IPR} \ll 1</span></td><td><span class="math">\gg 1</span></td><td>Extended collapse, complex envelope</td></tr></tbody></table>

#### 4.9.3 IPR Across State Classes

<table><thead><tr><th width="164.28125">Initial State</th><th width="196.078125">Typical IPR Scaling</th><th width="137.8187255859375">N_eff</th><th>Dynamical Implication</th></tr></thead><tbody><tr><td>Fock <span class="math">|n\rangle</span></td><td><span class="math">\text{IPR} = 1</span></td><td>1</td><td>Single frequency, fully ordered</td></tr><tr><td>Coherent <span class="math">|\alpha\rangle</span></td><td><span class="math">\sim (2\pi\bar{n})^{-1/2}</span></td><td><span class="math">\sim \sqrt{2\pi\bar{n}}</span></td><td>Collapse + revival</td></tr><tr><td>Squeezed <span class="math">|\xi\rangle</span></td><td>Smaller than coherent at same <span class="math">\bar{n}</span></td><td>Larger</td><td>Enhanced interference</td></tr><tr><td>Thermal</td><td><span class="math">\sim (1 + 2\bar{n})^{-1}</span></td><td><span class="math">\sim 1 + 2\bar{n}</span></td><td>Strong dephasing-like decay</td></tr><tr><td>Power-law mixture</td><td>Depends on <span class="math">\beta</span>; may diverge</td><td>Tuneable</td><td>Algebraic envelopes</td></tr></tbody></table>

#### 4.9.4 Connection to Prior Work

Similar participation-based measures have been successfully used to characterise localisation and information spreading in trapped-ion spin–boson and spin–phonon models, where they quantify how strongly dynamics explore the available mode space (Clos, Porras, Warring & Schaetz 2016).

The conceptual move here is consistent but deliberately simpler:

* **There**: Participation across _mode space_ in multi-ion chains
* **Here**: Participation across _excitation space_ of a single mode

This reinforces the minimality thesis: the essential physics of localisation/delocalisation is already present in the single-mode setting.

#### 4.9.5 Relation to Non-Markovianity Measures

The IPR quantifies _static_ delocalisation in excitation space. Non-Markovianity measures quantify _dynamical_ memory effects in the reduced spin dynamics.

In particular, information-backflow measures based on trace-distance revivals (Wittemer, Clos, Breuer, Warring & Schaetz 2018) provide a complementary, operational characterisation of memory that is sensitive to time-dependent correlations rather than initial-state structure.

> **Interface Boundary**
>
> In this handbook, non-Markovianity measures are used only as **diagnostic overlays**: they do not define regimes, but help interpret when excitation-space delocalisation translates into observable memory effects.
>
> A low IPR (high $$N_{\text{eff}}$$) implies many frequencies interfere, which _correlates with_ slower decay of distinguishability and longer memory times—but does not _cause_ non-Markovianity in any formal sense.

#### 4.9.6 Operational Use

The IPR can be:

1. **Computed** from any prepared distribution $$p_n$$
2. **Measured** via motional state tomography
3. **Engineered** by choosing state preparation protocols

This makes it a practical design parameter: before running an experiment, compute the IPR of your target state to predict whether dynamics will be regular (high IPR) or complex (low IPR).

***

## PART III — FROM CLOSED TO OPEN

### 5. The Single Mode as an Environment

#### 5.1 Perspective Shift

The same spin–mode Hamiltonian admits two complementary perspectives:

1. **Closed system**: Track the full state $$|\psi_{SM}(t)\rangle$$; evolution is unitary, information is conserved.
2. **Open system**: Trace out the mode degrees of freedom; the spin's reduced state $$\rho_S(t) = \text{Tr}_M[|\psi\rangle\langle\psi|]$$ follows non-unitary dynamics.

The second perspective reveals phenomena invisible in the first: effective decoherence, relaxation, and—crucially—_energy renormalisation_.

#### 5.2 The Master Equation in Minimal-Dissipation Form

For a thermal initial state of the mode with mean occupation $$\bar{n}$$, the exact time-convolutionless master equation in minimal-dissipation form reads:

$$\dot{\rho}S = -i\left[\frac{\tilde{\omega}(t)}{2}\sigma_z, \rho_S\right] + \gamma_z(t)\mathcal{D}[\sigma_z]\rho_S + \gamma+(t)\mathcal{D}[\sigma_+]\rho_S + \gamma_-(t)\mathcal{D}[\sigma_-]\rho_S$$

where $$\mathcal{D}[O]\rho = O\rho O^\dagger - \frac{1}{2}{O^\dagger O, \rho}$$ is the Lindblad superoperator, and all coefficients $$\tilde{\omega}, \gamma_{\pm,z}$$ are time-dependent.

The emergent Hamiltonian is:

$$K_S(t) = \frac{\tilde{\omega}(t)}{2}\sigma_z$$

with renormalised frequency $$\tilde{\omega}(t) = \omega_0 + \delta\tilde{\omega}(t)$$.

#### 5.3 Time-Dependent Energy Renormalisation

> **This section incorporates results from Colla et al. (2025), Nature Communications 16:2502**

According to the minimal-dissipation Ansatz, the splitting between coherent (Hamiltonian) and incoherent (dissipator) evolution is uniquely determined by minimising the dissipator's action.

For the mode initially in vacuum ($$\bar{n} = 0$$), the energy shift has an explicit analytic form:

$$\delta\tilde{\omega}(t) = -\frac{2g^2}{\Delta} \cdot \frac{1}{1 + \left(1 + \frac{4g^2}{\Delta^2}\right)\cot^2\left(\frac{\pi t}{T}\right)}$$

where $$T(\Delta) = 2\pi/\sqrt{\Delta^2 + 4g^2}$$ is the JC oscillation period.

**Key features**:

* The shift is _periodic_ in coupling duration with period $$T$$
* Maximum shift: $$\delta\tilde{\omega}(T/2) = -2g^2/\Delta$$
* Near resonance ($$\Delta \to 0$$), the effect is resonantly enhanced

**Time-averaged shift**:

$$\langle \delta\tilde{\omega}(t) \rangle_T = \frac{-2g^2 \, \text{sgn}(\Delta)}{|\Delta| + 2\pi/T}$$

This equals the dressed-state energy shift—the conventional Lamb shift emerges as a _time average_ of fundamentally time-dependent dynamics.

#### 5.4 Experimental Observation (Freiburg 2025)

Recent trapped-ion experiments observed these time-dependent shifts directly:

<table><thead><tr><th width="192.7437744140625">Parameter</th><th>Value</th></tr></thead><tbody><tr><td>Mode frequency <span class="math">\omega_m</span></td><td><span class="math">2\pi \times 1.30</span> MHz</td></tr><tr><td>Coupling <span class="math">g/\omega</span></td><td><span class="math">\approx 0.05</span> (near USC threshold)</td></tr><tr><td>Detuning <span class="math">\Delta/g</span></td><td><span class="math">\approx 0.8</span></td></tr><tr><td>Maximum shift <span class="math">\delta\tilde{\omega}/\omega</span></td><td><span class="math">\approx 15\%</span></td></tr><tr><td>Mean shift</td><td><span class="math">\approx 4\%</span></td></tr></tbody></table>

The observed modulation matches the minimal-dissipation prediction (Eq. above), providing direct evidence for time-dependent energy renormalisation in the JC model.

#### 5.5 The Generalised Lamb Shift

> **Conceptual Reframing**
>
> The Lamb shift and AC Stark shift—traditionally viewed as static energy corrections—are time-averaged manifestations of fundamentally dynamic phenomena. They arise from correlation buildup between system and environment, appearing only constant when the environment is traced out and time-averaged.

In the dispersive limit ($$|\Delta| \gg g$$):

$$\langle \delta\tilde{\omega} \rangle_T \to -\frac{g^2}{\Delta}$$

recovering the standard Lamb shift formula. But this is a limiting case of a more general time-dependent structure.

***

### 6. Mode Damping and Memory

#### 6.1 Closed vs Open: The Fundamental Distinction

<table><thead><tr><th width="115.06561279296875">Property</th><th width="197.83746337890625">Closed (single mode)</th><th>Open (continuum bath)</th></tr></thead><tbody><tr><td>Spectrum</td><td>Discrete</td><td>Continuous</td></tr><tr><td>Collapse</td><td>Temporary (dephasing)</td><td>Permanent (decoherence)</td></tr><tr><td>Information</td><td>Preserved (entangled)</td><td>Lost (to environment)</td></tr><tr><td>Entropy</td><td>Constant</td><td>Increases</td></tr><tr><td>Revivals</td><td>Yes</td><td>No</td></tr></tbody></table>

In a closed system, the "collapse" of spin coherence is temporary—the full state remains pure, but the spin's reduced state loses coherence due to entanglement with the mode. Given sufficient time, coherence returns (revival).

In an open system coupled to many modes, collapse is permanent—information leaks into uncontrollable degrees of freedom.

#### 6.2 Adding True Dissipation

When the mode leaks photons (rate $$\kappa$$) or the spin has spontaneous emission (rate $$\gamma$$):

$$\dot{\rho} = -\frac{i}{\hbar}[H, \rho] + \kappa \mathcal{D}[a]\rho + \gamma \mathcal{D}[\sigma^-]\rho$$

The competition between coherent dynamics and dissipation yields:

* **Strong damping** ($$\kappa, \gamma \gg g$$): Quantum coherence constantly "monitored," no entanglement buildup
* **Moderate damping**: Damped revivals—each revival smaller than the last
* **Weak damping** ($$\kappa, \gamma \ll g$$): Near-ideal JC dynamics with slow decay envelope

> **Overclaim Protection**
>
> The Lindblad master equation is Markovian _by construction_. It cannot capture non-Markovian backflow. However, a single damped mode with $$\kappa \sim g$$ can _emulate_ memory effects on timescales $$t \lesssim \kappa^{-1}$$. Do not confuse this with true system-bath memory.

***

### 7. Emulating Power-Law Baths: What Is and Is Not Possible

#### 7.1 The Spin–Boson Benchmark

The full spin–boson model couples a two-level system to a _continuum_ of oscillators characterised by spectral density $$J(\omega) \sim \omega^s$$:

* $$s < 1$$: Sub-Ohmic (strong low-frequency coupling)
* $$s = 1$$: Ohmic
* $$s > 1$$: Super-Ohmic

#### 7.2 Single-Mode Emulation

A single mode cannot reproduce a continuum. However, the _dynamical signatures_ can be emulated:

<table><thead><tr><th width="253.953125">True Bath Property</th><th>Single-Mode Emulation</th></tr></thead><tbody><tr><td>Spectral density <span class="math">J(\omega)</span></td><td>Distribution <span class="math">p_n</span> in excitation space</td></tr><tr><td>Power-law decay envelope</td><td>Power-law <span class="math">p_n</span> yields <span class="math">t^{-(\beta-1)}</span></td></tr><tr><td>Bath bandwidth</td><td>Preparation cutoff <span class="math">n_{\max}</span></td></tr><tr><td>Non-Markovian backflow</td><td>Mode recurrences (different mechanism)</td></tr></tbody></table>

#### 7.3 The Emulation Boundary

What _cannot_ be emulated:

* True information loss (single mode always recurs)
* Bath-induced localisation (requires continuum)
* Arbitrary correlation functions (limited by $$H_{\text{JC}}$$ structure)

> **Guardian Warning**
>
> Do not claim that a single-mode experiment demonstrates "non-Markovian dynamics" without qualifying: the recurrences arise from mode finiteness, not from structured bath memory. The physics is different even if signatures overlap.

***

## PART IV — ANALYTIC TOOLS

### 8. Solution Recipes

#### 8.1 Decision Framework

```
CHOOSE YOUR TOOL

Question: What regime?
├── Dispersive (g ≪ |Δ|, g ≪ ω)
│   └── USE: Perturbation theory / Schrieffer-Wolff
│       ├── Output: H_eff with Lamb shifts
│       └── Validity: Check g²/Δ² ≪ 1
│
├── Resonant JC (g ≪ ω, Δ ≈ 0)  
│   └── USE: Exact JC diagonalisation
│       ├── Output: Dressed states, Rabi formula
│       └── Validity: Check g/ω ≪ 1
│
├── Ultrastrong (0.1 < g/ω < 1)
│   └── USE: Braak exact / Numerical
│       ├── Output: Spectrum via transcendental eq.
│       └── Validity: Check counter-rotating effects
│
└── Deep Strong (g/ω > 1)
    └── USE: Polaron frame / Numerical
        ├── Output: Transformed Hamiltonian
        └── Validity: Strong-coupling expansion
```

#### 8.2 The Rotating-Wave Approximation

**Procedure**: Drop $$\sigma^+ a^\dagger$$ and $$\sigma^- a$$ terms.

**When valid**: $$g \ll \omega, \omega_0$$ _and_ timescales $$\gg 1/\omega$$.

**What it yields**: The JC Hamiltonian decomposes into 2×2 blocks with exact eigenstates:

$$|n, \pm\rangle = \cos\theta_n |e,n\rangle \pm \sin\theta_n |g, n+1\rangle$$

**What it misses**: Bloch–Siegert shifts, virtual-photon physics, ground-state entanglement.

#### 8.3 The Braak Solution

For the full Rabi Hamiltonian, Braak (2011) showed integrability via:

1. Parity decomposition: $$H = H_+ \oplus H_-$$
2. Bargmann representation: Map to differential equations
3. Transcendental eigenvalue equation: Zeros of confluent Heun functions

**When to use**: USC regime where RWA fails but numerical truncation is uncertain.

**Practical note**: The solution is implicit (eigenvalues via root-finding), not closed-form. For dynamics, numerical methods are often more practical.

#### 8.4 Perturbative Expansions

**Dispersive regime** ($$g/\Delta$$ expansion):

$$H_{\text{eff}} = H_0 + \frac{g^2}{\Delta}\sigma_z a^\dagger a + \frac{g^2}{2\Delta}\sigma_z + O(g^4/\Delta^3)$$

**Bloch–Siegert regime** ($$g/(\omega_0 + \omega)$$ expansion):

$$\delta_{\text{BS}} \approx \frac{g^2}{2(\omega_0 + \omega)}$$

**Strong-coupling regime** (treat $$\omega$$ as perturbation on $$g$$-dominated interaction).

#### 8.5 Numerical Methods

**Truncated diagonalisation**: Truncate oscillator space to $$n \leq N_{\max}$$, diagonalise numerically.

* **Rule of thumb**: $$N_{\max} > \langle n \rangle + 5\sqrt{\langle n \rangle}$$
* **Check**: Verify eigenvalues converge as $$N_{\max}$$ increases

**Time-domain simulation**: Integrate Schrödinger/master equation directly.

* **For pure states**: Fourth-order Runge-Kutta on state vector
* **For mixed states**: Lindblad equation or quantum trajectories

#### 8.6 Open-System Tools

**Markov limit**: Standard Lindblad equation with constant rates.

**Non-Markov (single mode)**: Exact TCL master equation (see Section 5.2).

**Structured bath**: Nakajima–Zwanzig projection, path integrals (beyond this handbook's scope).

***

## PART V — THE TRAPPED-ION PLATFORM

### 9. Hamiltonian Engineering with a Single Ion

#### 9.1 The Physical Mapping

<table><thead><tr><th width="169.153076171875">Theoretical Object</th><th>Ion Trap Realisation</th></tr></thead><tbody><tr><td>Spin-½</td><td>Two hyperfine/Zeeman states (Laser dressed )</td></tr><tr><td><span class="math">|{\downarrow}\rangle</span>, <span class="math">|{\uparrow}\rangle</span></td><td>e.g., <span class="math">|F=3, m_F=3\rangle, |F=2, m_F=2\rangle</span> (Laser dressed)</td></tr><tr><td>Mode <span class="math">a, a^\dagger</span></td><td>Quantised motion (axial COM mode)</td></tr><tr><td><span class="math">\omega</span></td><td>Trap frequency (<span class="math">\sim 2\pi \times 1</span> MHz)</td></tr><tr><td><span class="math">\omega_0</span></td><td>Zeeman-like splitting (tunable via an effective <span class="math">B</span>-field – Laser detuning)</td></tr><tr><td><span class="math">g</span></td><td><span class="math">\eta \Omega</span> (Lamb-Dicke × Laser Rabi rate)</td></tr></tbody></table>

#### 9.2 Sideband Transitions as JC/AJC Engineering

Laser-ion interaction in the Lamb-Dicke regime:

**Carrier** ($$\delta = 0$$):&#x20;

$$H_{\text{car}} = \frac{\hbar \Omega}{2}(\sigma^+ + \sigma^-)$$ Flips spin without changing motion.

**Red sideband** ($$\delta = -\omega$$):&#x20;

$$H_{\text{RSB}} = \hbar \eta \Omega (\sigma^+ a + \sigma^- a^\dagger)$$ JC interaction: spin flip ↔ phonon annihilation.

**Blue sideband** ($$\delta = +\omega$$):&#x20;

$$H_{\text{BSB}} = \hbar \eta \Omega (\sigma^+ a^\dagger + \sigma^- a)$$ Anti-JC interaction: spin flip ↔ phonon creation.

**Bichromatic drive** (both sidebands): $$H_{\text{bi}} \approx \hbar g_{\text{eff}} (\sigma^+ + \sigma^-)(a + a^\dagger)$$ Approximates the full Rabi Hamiltonian.

> **Operational Boundary**
>
> The Lamb-Dicke regime ($$\eta \ll 1$$) is not a fundamental limit—it is a convenience that linearises the coupling. Stronger coupling (large $$\eta$$) introduces higher-order terms $$\sim \eta^2 (a + a^\dagger)^2 \sigma_z$$, which can be accounted for but invalidate the simple mapping.
>
> This handbook assumes $$\eta \leq 0.2$$ unless otherwise stated.

#### 9.3 Lamb-Dicke Validity

The Lamb-Dicke parameter:

$$\eta = k \sqrt{\frac{\hbar}{2 m \omega}} = k , x_0$$

where $$k$$ is the laser wavevector component along the mode, and $$x_0$$ is the ground-state wavepacket size.

**Lamb-Dicke regime**: $$\eta \sqrt{\langle n \rangle + 1} \ll 1$$

This ensures the motional wavefunction samples only the linear part of the laser's spatial phase.

***

### 10. Engineering Initial States

#### 10.1 Ground-State Cooling

**Resolved sideband cooling**: Drive red sideband repeatedly. $$|{\downarrow}, n\rangle \xrightarrow{\text{RSB}} |{\uparrow}, n-1\rangle \xrightarrow{\text{decay}} |{\downarrow}, n-1\rangle$$

Achieves $$\bar{n} \lesssim 0.1$$ routinely.

#### 10.2 State Preparation Protocols

| Target State                 | Preparation Method                               | Typical Fidelity |
| ---------------------------- | ------------------------------------------------ | ---------------- |
| Fock $$|n\rangle$$           | Sequential BSB $$\pi$$-pulses from $$|0\rangle$$ | $$>95\%$$        |
| Coherent $$|\alpha\rangle$$  | Classical drive (displacement)                   | $$>99\%$$        |
| Squeezed $$|\xi\rangle$$     | Parametric modulation / pulse sequence           | $$>90\%$$        |
| Cat state                    | Conditional displacement + measurement           | $$>85\%$$        |
| Power-law mixture            | Stochastic sideband pulses                       | Tuneable         |

#### 10.3 Cat State Generation

Protocol (Monroe et al. 1996):

1. Prepare $$|{\downarrow}, 0\rangle$$
2. Apply carrier $$\pi/2$$ to create $$(|{\downarrow}\rangle + |{\uparrow}\rangle)/\sqrt{2}$$
3. Apply state-dependent displacement: $$|{\downarrow}\rangle \to |{\downarrow}, \alpha\rangle, |{\uparrow}\rangle \to |{\uparrow}, -\alpha\rangle$$
4. Result: $$(|{\downarrow}, \alpha\rangle + |{\uparrow}, -\alpha\rangle)/\sqrt{2}$$

> **Normalisation Note**
>
> The cat state $$(|\alpha\rangle + |-\alpha\rangle)/\sqrt{2}$$ is properly normalised only for $$|\alpha| \gg 1$$ (where $$\langle \alpha | -\alpha \rangle = e^{-2|\alpha|^2} \approx 0$$). For small $$\alpha$$, include the overlap correction.

***

### 11. Experimental Knob Map

<table><thead><tr><th width="189.49066162109375">Theoretical Parameter</th><th width="178.003173828125">Ion Trap Realisation</th><th width="182.9813232421875">Typical Range</th><th>Calibration Method</th></tr></thead><tbody><tr><td><span class="math">g</span></td><td><span class="math">\eta \Omega</span></td><td><span class="math">2\pi \times (1-100)</span> kHz</td><td>Rabi flopping on sideband</td></tr><tr><td><span class="math">\omega</span></td><td>Trap frequency</td><td><span class="math">2\pi \times (0.5-5)</span> MHz</td><td>Secular frequency measurement</td></tr><tr><td><span class="math">\omega_0</span></td><td>Zeeman shift</td><td>Tunable via <span class="math">B</span>-field</td><td>Microwave spectroscopy</td></tr><tr><td><span class="math">\Delta = \omega - \omega_0</span></td><td>Laser detuning</td><td><span class="math">2\pi \times (0-1)</span> MHz</td><td>Ramsey spectroscopy</td></tr><tr><td><span class="math">\kappa</span> (damping)</td><td>Sympathetic cooling</td><td><span class="math">10-10^4\, \text{s}^{-1}</span></td><td>Sideband asymmetry</td></tr><tr><td><span class="math">\gamma_\phi</span> (dephasing)</td><td>Engineered noise</td><td>Tuneable</td><td>Ramsey decay</td></tr><tr><td><span class="math">\bar{n}</span></td><td>Cooling quality</td><td><span class="math">0.01-10</span></td><td>Sideband ratio</td></tr><tr><td><span class="math">p_n</span> distribution</td><td>Squeeze + displace + mix</td><td>Engineered</td><td>Motional tomography</td></tr></tbody></table>

#### 11.1 Accessing Different Regimes

<table><thead><tr><th width="235.2125244140625">Regime</th><th>How to Access</th></tr></thead><tbody><tr><td>Dispersive</td><td>Large detuning <span class="math">\Delta \gg g</span> (detune laser far from sideband)</td></tr><tr><td>Resonant JC</td><td><span class="math">\Delta \approx 0</span>, moderate <span class="math">\eta \Omega</span></td></tr><tr><td>Near-USC</td><td>Small <span class="math">\Delta</span>, large <span class="math">\eta \Omega</span> (typical: <span class="math">g/\omega \sim 0.05-0.1</span>)</td></tr><tr><td>Engineered dissipation</td><td>Add sympathetic cooling or electrode noise</td></tr></tbody></table>

***

## PART VI — HORIZONS

### 12. What Is Already Known

The single-spin–single-mode system is among the most thoroughly characterised quantum systems:

* **JC spectrum and dynamics**: Fully solved analytically (Jaynes & Cummings 1963)
* **Collapse and revival**: Observed in cavity QED and ion traps (1980s-present)
* **Braak integrability**: Full Rabi model solved (2011)
* **USC phenomena**: Observed in superconducting circuits (2010s)
* **Time-dependent Lamb shift**: Observed in trapped ions (Colla et al. 2025)
* **State engineering**: Fock, coherent, squeezed, cat states all demonstrated

### 13. What This Handbook Enables

#### 13.1 For Graduate Students

* **Conceptual bridge**: Connect textbook Hamiltonians to laboratory reality
* **Decision protocols**: Know which approximation applies when
* **Operational fluency**: Translate theoretical parameters to experimental knobs

#### 13.2 For Experimentalists

* **Design guidance**: Engineer specific dynamical signatures via state preparation
* **Regime navigation**: Identify which physics dominates in your parameter range
* **Benchmark protocols**: Test system calibration against exact predictions

#### 13.3 For Theorists

* **Minimal testbed**: Verify new ideas in the simplest non-trivial setting
* **Emulation boundaries**: Know what can and cannot be simulated with one mode
* **Open-system foundations**: Use the minimal-dissipation framework as reference

### 14. Open Questions and Outlook

#### 14.1 Within the Single-Mode Framework

1. **Non-thermal initial states**: How does $$K_S(t)$$ depend on squeezed, Fock, or cat initial states of the mode?
2. **Beyond JC**: Full characterisation of time-dependent renormalisation in the Rabi model.
3. **Quantum thermodynamics**: Connecting $$K_S(t)$$ to work and heat definitions at strong coupling.

#### 14.2 Extensions

1. **Multi-mode environments**: How do signatures change with 2, 3, ..., $$N$$ modes?
2. **Structured baths**: Engineering effective spectral densities with multiple modes.
3. **Autonomous quantum machines**: Using emergent driving for heat engines.

#### 14.3 The Handbook's Continuing Role

This handbook is a _living document_. As the field develops, new sections will address:

* Additional state classes and their dynamics
* Refined experimental protocols
* Connections to quantum error correction and fault tolerance

***

## References

* Braak, D. (2011). Integrability of the Rabi Model. _Physical Review Letters_ 107, 100401.
* Clos, G., Porras, D., Warring, U. & Schaetz, T. (2016). Time-Resolved Observation of Thermalization in an Isolated Quantum System. _Physical Review Letters_ 117, 170401.
* Colla, A. & Breuer, H.-P. (2022). Open-system approach to nonequilibrium quantum thermodynamics at arbitrary coupling. _Physical Review A_ 105, 052216.
* Colla, A., Hasse, F., Palani, D., Schaetz, T., Breuer, H.-P. & Warring, U. (2025). Observing time-dependent energy level renormalisation in an ultrastrongly coupled open system. _Nature Communications_ 16, 2502.
* Forn-Díaz, P., Lamata, L., Rico, E., Kono, J. & Solano, E. (2019). Ultrastrong coupling regimes of light-matter interaction. _Reviews of Modern Physics_ 91, 025005.
* Jaynes, E. T. & Cummings, F. W. (1963). Comparison of quantum and semiclassical radiation theories with application to the beam maser. _Proceedings of the IEEE_ 51, 89–109.
* Leggett, A. J. et al. (1987). Dynamics of the dissipative two-state system. _Reviews of Modern Physics_ 59, 1–85.
* Leibfried, D., Blatt, R., Monroe, C. & Wineland, D. (2003). Quantum dynamics of single trapped ions. _Reviews of Modern Physics_ 75, 281–324.
* Meekhof, D. M., Monroe, C., King, B. E., Itano, W. M. & Wineland, D. J. (1996). Generation of Nonclassical Motional States of a Trapped Atom. _Physical Review Letters_ 76, 1796.
* Monroe, C., Meekhof, D. M., King, B. E. & Wineland, D. J. (1996). A "Schrödinger Cat" Superposition State of an Atom. _Science_ 272, 1131–1136.
* Scully, M. O. & Zubairy, M. S. (1997). _Quantum Optics_. Cambridge University Press.
* Shore, B. W. & Knight, P. L. (1993). The Jaynes–Cummings model. _Journal of Modern Optics_ 40, 1195–1238.
* Smirne, A. & Vacchini, B. (2010). Nakajima-Zwanzig versus time-convolutionless master equation for the non-Markovian dynamics of a two-level system. _Physical Review A_ 82, 022110.
* Wittemer, M., Clos, G., Breuer, H.-P., Warring, U. & Schaetz, T. (2018). Measurement of quantum memory effects and its fundamental limitations. _Physical Review A_ 97, 020102.

***

## Appendix A: Notation Summary

<table><thead><tr><th width="202.918701171875">Symbol</th><th>Meaning</th></tr></thead><tbody><tr><td><span class="math">\omega_0</span></td><td>Bare spin transition frequency</td></tr><tr><td><span class="math">\omega</span></td><td>Oscillator/mode frequency</td></tr><tr><td><span class="math">g</span></td><td>Spin-mode coupling strength</td></tr><tr><td><span class="math">\Delta = \omega - \omega_0</span></td><td>Detuning</td></tr><tr><td><span class="math">\eta</span></td><td>Lamb-Dicke parameter</td></tr><tr><td><span class="math">\Omega</span></td><td>Laser Rabi frequency</td></tr><tr><td><span class="math">\bar{n}</span></td><td>Mean thermal occupation</td></tr><tr><td><span class="math">p_n</span></td><td>Fock-state probability distribution</td></tr><tr><td><span class="math">\Omega_n = 2g\sqrt{n+1}</span></td><td><span class="math">n</span>-photon Rabi frequency</td></tr><tr><td><span class="math">T = 2\pi/\sqrt{\Delta^2 + 4g^2}</span></td><td>JC oscillation period</td></tr><tr><td><span class="math">K_S(t)</span></td><td>Emergent (renormalised) system Hamiltonian</td></tr><tr><td><span class="math">\tilde{\omega}(t)</span></td><td>Renormalised spin frequency</td></tr><tr><td><span class="math">\text{IPR} = \sum_n p_n^2</span></td><td>Inverse participation ratio</td></tr><tr><td><span class="math">N_{\text{eff}} = 1/\text{IPR}</span></td><td>Effective excitation number</td></tr></tbody></table>

***

## Appendix B: Version History

<table><thead><tr><th width="97.75628662109375">Version</th><th width="175.0687255859375">Date</th><th>Changes</th></tr></thead><tbody><tr><td>0.1</td><td>2025–12-17</td><td>Initial draft (review format)</td></tr><tr><td>0.2</td><td>2025–12-17</td><td>Modular restructure; Guardian protections; Navigator; minimal-dissipation Ansatz; power-law emulator; trapped-ion axis elevated</td></tr><tr><td>0.2.1</td><td>2025–12-17</td><td>Added Section 4.9 (IPR ordering parameter); citation apparatus; references for Clos et al. 2016, Wittemer et al. 2018</td></tr></tbody></table>

***

_End of Handbook v0.2_
