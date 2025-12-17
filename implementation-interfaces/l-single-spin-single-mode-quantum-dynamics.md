---
description: An Operator's Handbook – Part of the Ordinans Series
---

# L–Single-Spin–Single-Mode Quantum Dynamics

{% hint style="info" %}
author: _U. Warring_\
affiliation: _Institute of Physics, University of Freiburg_\
_version: 0.2_\
last\_updated: _2025-12-17_\
license: _CC BY 4.0_\
\
**Disclaimer** – This handbook is a conceptual and pedagogical synthesis intended to clarify minimal models, regimes, and design principles for single-spin–single-mode quantum dynamics; it does not claim completeness, universality, or direct applicability to all experimental platforms. Any emulation of bath-like or power-law behaviour discussed here is finite, state-dependent, and explicitly bounded by the assumptions and cutoffs stated in the text.<br>
{% endhint %}

## PART I — INVARIANT CORE

### 1. Scope, Philosophy, and Minimality

#### 1.1 Scope

Single-spin–single-mode quantum dynamics refers to the physics of a single two-level quantum system (a spin-½ or qubit) interacting with a single quantised harmonic oscillator mode. This minimal composite system—essentially the quantum Rabi model—is a cornerstone of quantum optics and quantum information, underlying phenomena from cavity QED to trapped-ion quantum logic.

#### 1.2 Thesis

Even this ostensibly simple system generates complex quantum dynamics. By tuning system parameters, preparing different initial states, or allowing environment coupling, one can explore diverse regimes—from exactly solvable models to chaotic-like behaviour—and gain insight into larger many-body or open quantum systems.

This handbook develops a unified framework for single-spin–single-mode dynamics, organised into six parts:

| Part | Title                    | Content                                                 |
| ---- | ------------------------ | ------------------------------------------------------- |
| I    | Invariant Core           | Hamiltonians, symmetries, regime boundaries             |
| II   | Dynamics from Simplicity | Manifold-resolved dynamics, initial-state complexity    |
| III  | From Closed to Open      | Single mode as environment, memory effects, dissipation |
| IV   | Analytic Tools           | Solution recipes, approximation validity                |
| V    | The Trapped-Ion Platform | Hamiltonian engineering, experimental knobs             |
| VI   | Horizons                 | Open questions, what this handbook enables              |

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

\$$H = \frac{\hbar \omega\_0}{2}\sigma\_z + \hbar \omega , a^\dagger a + \hbar g , (\sigma^+ + \sigma^-)( a + a^\dagger)\$$

where:

* $\omega\_0$ is the spin's transition frequency
* $\omega$ is the oscillator frequency
* $a^\dagger$, $a$ are the mode's creation/annihilation operators
* $g$ is the coupling strength
* $\sigma\_z$, $\sigma^\pm$ are Pauli operators on the two-level system

This quantum Rabi Hamiltonian is invariant under a $\mathbb{Z}\_2$ parity transformation (flipping the sign of both spin-$\sigma\_x$ and oscillator quadrature)—a symmetry that yields a conserved parity operator:

\$$\Pi = \sigma\_z (-1)^{a^\dagger a}\$$

#### 2.2 The Jaynes–Cummings Model

In the rotating-wave approximation (valid when $g \ll \omega, \omega\_0$ and $\omega \approx \omega\_0$), one drops the non-energy-conserving terms $\sigma^+ a^\dagger$ and $\sigma^- a$, recovering:

\$$H\_{\text{JC\}} = \hbar \omega , a^\dagger a + \frac{\hbar \omega\_0}{2}\sigma\_z + \hbar g , (\sigma^+ a + \sigma^- a^\dagger)\$$

The Jaynes–Cummings model conserves the total excitation number:

\$$N = a^\dagger a + \frac{1}{2}(1 + \sigma\_z)\$$

This exact invariant simplifies the solution: the Hilbert space decomposes into independent two-dimensional subspaces ${|e, n\rangle, |g, n+1\rangle}$ for each excitation number.

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
    │ Calculate g/ω    │
    └──────────────────┘
           │
     ┌─────┴─────┬──────────────┐
     ▼           ▼              ▼
  g/ω ≪ 1    0.1 < g/ω < 1   g/ω > 1
     │           │              │
     ▼           ▼              ▼
┌─────────┐ ┌─────────┐    ┌─────────┐
│ Weak/   │ │  USC    │    │  DSC    │
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
│ SELECT INITIAL STATE │
│ (Complexity Generator)│
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

| Regime      | Condition                          | Symmetry        | Hamiltonian         | Approximation |
| ----------- | ---------------------------------- | --------------- | ------------------- | ------------- |
| Dispersive  | $g \ll                             | \Delta          | $, $g \ll \omega$   | Eff. $U(1)$   |
| Resonant JC | $g \ll \omega$, $\Delta \approx 0$ | $U(1)$          | $H\_{\text{JC\}}$   | RWA valid     |
| Ultrastrong | $0.1 < g/\omega < 1$               | $\mathbb{Z}\_2$ | $H\_{\text{Rabi\}}$ | Braak exact   |
| Deep Strong | $g/\omega > 1$                     | $\mathbb{Z}\_2$ | $H\_{\text{Rabi\}}$ | Polaron frame |

where $\Delta = \omega - \omega\_0$ is the spin-mode detuning.

**Dispersive Regime** ($g \ll |\Delta|$): The spin and oscillator exchange virtual excitations, leading to energy shifts (Lamb/AC Stark) but not real energy exchange. The effective Hamiltonian is:

\$$H\_{\text{disp\}} \approx \hbar \omega , a^\dagger a + \frac{\hbar}{2}\left(\omega\_0 + \frac{g^2}{\Delta}(2 a^\dagger a + 1)\right)\sigma\_z\$$

> **Validity Condition (Complete)**
>
> The dispersive approximation requires _both_ $g \ll |\Delta|$ _and_ $g \ll \omega, \omega\_0$. The first ensures the perturbation expansion converges; the second ensures the RWA remains valid as a precursor step.

**Resonant Strong Coupling** ($g$ moderate, $\omega \approx \omega\_0$): The dynamics feature Rabi oscillations. If the oscillator has $n$ quanta, the spin flips at the Rabi frequency $\Omega\_n = 2g\sqrt{n+1}$. The energy spectrum splits into doublets separated by the vacuum Rabi splitting $2g$.

**Ultrastrong Coupling** ($0.1 < g/\omega < 1$): The counter-rotating terms $\sigma^+ a^\dagger$ and $\sigma^- a$ cannot be neglected. The ground state is no longer the spin-down vacuum $|g, 0\rangle$ but a squeezed entangled state containing virtual excitations. The Bloch–Siegert shift becomes appreciable.

> **Common Misconception Alert**
>
> "Ultrastrong coupling means non-perturbative." _False._ The Rabi model is analytically solvable at any $g/\omega$ (Braak 2011). The challenge is not solvability but _interpretation_: as $g \to \omega$, the notion of separate spin and mode excitations becomes a bad basis choice, not a physical mystery.

**Deep Strong Coupling** ($g/\omega > 1$): This extreme regime pushes the interaction beyond perturbative expansions. Even basic notions of separate "spin" and "oscillator" excitations become blurred.

#### 2.5 Key Point: Symmetry as Signpost

The single-spin–single-mode system is governed by a simple Hamiltonian with symmetries that depend on coupling regime:

* **JC limit**: Approximate $U(1)$ symmetry (conservation of $N$) makes the problem exactly solvable via independent 2×2 blocks.
* **Full Rabi**: Only $\mathbb{Z}\_2$ parity remains, yet the model is still integrable (Braak 2011).

> **Integrability Clarification**
>
> The Rabi model is integrable in Braak's sense: the spectrum can be determined by transcendental equations involving confluent Heun functions. This is _not_ Liouville integrability (which requires $N$ independent constants of motion for $N$ degrees of freedom). The discrete parity symmetry suffices for exact solvability but does not simplify dynamics to independent one-dimensional motions.

***

## PART II — DYNAMICS FROM SIMPLICITY

### 3. Manifold-Resolved Dynamics

Within the Jaynes–Cummings approximation, the Hilbert space decomposes into independent manifolds:

\$$\mathcal{H} = \mathcal{M}\_0 \oplus \mathcal{M}\_1 \oplus \mathcal{M}\_2 \oplus \cdots\$$

where $\mathcal{M}_n = \text{span}{|e, n\rangle, |g, n+1\rangle}$ for $n \geq 0$, and $\mathcal{M}_{-1} = \text{span}{|g, 0\rangle}$ is the ground state (decoupled).

Within each manifold $\mathcal{M}\_n$, the Hamiltonian acts as a 2×2 matrix:

\$$H\_n = \hbar \begin{pmatrix} (n+\tfrac{1}{2})\omega + \tfrac{\Delta}{2} & g\sqrt{n+1} \ g\sqrt{n+1} & (n+\tfrac{1}{2})\omega - \tfrac{\Delta}{2} \end{pmatrix}\$$

The eigenstates (dressed states) are:

\$$|n, \pm\rangle = \cos\theta\_n |e, n\rangle \pm \sin\theta\_n |g, n+1\rangle\$$

with $\tan(2\theta\_n) = 2g\sqrt{n+1}/\Delta$, and eigenfrequencies:

\$$E\_{n,\pm} = \hbar\left\[(n+\tfrac{1}{2})\omega \pm \tfrac{1}{2}\sqrt{\Delta^2 + 4g^2(n+1)}\right]\$$

***

### 4. Motional Initial States as Complexity Generators

The oscillator's initial state acts as a generator of complexity by controlling the distribution of interaction frequencies and quantum phases in the spin–mode evolution.

#### 4.1 The Distribution Function

Define the Fock-state distribution:

\$$p\_n = |\langle n | \psi\_{\text{mode\}}(0) \rangle|^2\$$

This distribution ${p\_n}$ plays the role of a _spectral weight_ in excitation space. The spin coherence evolves as:

\$$\langle \sigma\_+(t) \rangle \approx \sum\_{n=0}^{\infty} p\_n , e^{-i \Omega\_n t} \cdot (\text{amplitude factors})\$$

where $\Omega\_n = 2g\sqrt{n+1}$. The statistics of $p\_n$ determine the interference pattern.

#### 4.2 Fock States: The Single-Frequency Benchmark

If the mode starts in a Fock state $|n\rangle$, the spin undergoes simple Rabi oscillations at a single frequency $\Omega\_n = 2g\sqrt{n+1}$:

\$$P\_e(t) = \cos^2\left(g\sqrt{n+1} , t\right)\$$

This is the _reference case_: predictable, oscillatory, and non-complex.

#### 4.3 Coherent States: Collapse and Revival

A coherent state $|\alpha\rangle$ has Poisson-distributed Fock components:

\$$p\_n = e^{-|\alpha|^2} \frac{|\alpha|^{2n\}}{n!}\$$

The spin excitation probability becomes:

\$$P\_e(t) = \frac{1}{2}\left\[1 + \sum\_{n=0}^\infty p\_n \cos(2g\sqrt{n+1} , t)\right]\$$

**Collapse**: The spread of frequencies ${\Omega\_n}$ causes dephasing on timescale:

\$$t\_{\text{collapse\}} \sim (g\sqrt{\langle n \rangle})^{-1}\$$

**Revival**: The discrete quantisation allows rephasing at:

\$$t\_{\text{revival\}} \sim \frac{2\pi\sqrt{\langle n \rangle\}}{g}\$$

The discovery of revivals was a seminal demonstration of field quantisation: revivals are a direct consequence of discrete photon number states, absent in classical or continuum fields.

#### 4.4 Squeezed States: Variance Control

A squeezed state has reduced number uncertainty in certain quadratures. This modifies collapse/revival patterns:

* **Narrower $p\_n$**: Slower collapse (fewer frequencies interfere)
* **Even/odd parity structure**: Frequency-comb dynamics with substructure in revivals

#### 4.5 Displaced-Squeezed States: Tunable Asymmetry

Combining displacement and squeezing allows independent control of:

* Mean excitation $\langle n \rangle$ (sets revival timescale)
* Variance $(\Delta n)^2$ (sets collapse rate)
* Parity structure (sets revival substructure)

#### 4.6 Engineered Classical Mixtures: The Power-Law Emulator

> **Key Handbook Statement**
>
> In a single mode, power-law-like behaviour is realised in _excitation space_, not frequency space.

**Motivation**: Many-body physics studies power-law spectral densities $J(\omega) \sim \omega^s$. In a single mode, we cannot replicate a continuum, but we can engineer $p\_n$ to _emulate_ the dynamical signatures of non-Markovian baths.

**Recipe**: Prepare a mixed motional state:

\$$\rho\_{\text{mode\}} = \sum\_n p\_n |n\rangle\langle n|, \quad p\_n \propto (n + n\_0)^{-\beta}\$$

using stochastically applied sideband pulses. The spin coherence then evolves as:

\$$\langle \sigma\_+(t) \rangle \approx \sum\_n p\_n , e^{-i 2g\sqrt{n+1} , t}\$$

For large $n$ and $\beta > 1$, the sum yields an envelope $\sim t^{-(\beta-1)}$ up to a cutoff time $t\_c \sim n\_{\max}/g$.

> **Guardian Warning: Emulation Boundary**
>
> This is _emulation_. The underlying Hamiltonian is still JC; there is no bath-induced backflow, only frequency mixing. The power-law envelope is a _signature_, not a physical spectral density. The cutoff $n\_{\max}$ is not a bath bandwidth but a preparation limit.

#### 4.7 Thermal States: The "Bath" Emulator

A thermal state has:

\$$p\_n = \frac{\bar{n}^n}{(1+\bar{n})^{n+1\}}\$$

This causes irreversible-looking damping of Rabi oscillations. The uncertain photon number acts like static disorder, washing out coherent oscillations _without_ revival (since a thermal state has no fixed phase relationship to rephase).

This mimics decoherence even in a closed system, purely due to uncertainty in the initial mode state.

#### 4.8 State Class Summary

| Initial State     | Distribution $p\_n$ | Dynamics                | Complexity Source        |
| ----------------- | ------------------- | ----------------------- | ------------------------ |
| Fock $            | n\rangle$           | $\delta\_{n,n\_0}$      | Single-frequency Rabi    |
| Coherent $        | \alpha\rangle$      | Poisson                 | Collapse & revival       |
| Squeezed $        | ξ\rangle$           | Sub-Poisson             | Modified revival pattern |
| Thermal           | Bose–Einstein       | Irreversible-like decay | No phase correlation     |
| Power-law mixture | $(n+n\_0)^{-\beta}$ | Algebraic envelope      | Engineered weight        |

***

## PART III — FROM CLOSED TO OPEN

### 5. The Single Mode as an Environment

#### 5.1 Perspective Shift

The same spin–mode Hamiltonian admits two complementary perspectives:

1. **Closed system**: Track the full state $|\psi\_{SM}(t)\rangle$; evolution is unitary, information is conserved.
2. **Open system**: Trace out the mode degrees of freedom; the spin's reduced state $\rho\_S(t) = \text{Tr}\_M\[|\psi\rangle\langle\psi|]$ follows non-unitary dynamics.

The second perspective reveals phenomena invisible in the first: effective decoherence, relaxation, and—crucially—_energy renormalisation_.

#### 5.2 The Master Equation in Minimal-Dissipation Form

For a thermal initial state of the mode with mean occupation $\bar{n}$, the exact time-convolutionless master equation in minimal-dissipation form reads:

\$$\dot{\rho}_S = -i\left\[\frac{\tilde{\omega}(t)}{2}\sigma\_z, \rho\_S\right] + \gamma\_z(t)\mathcal{D}\[\sigma\_z]\rho\_S + \gamma_+(t)\mathcal{D}\[\sigma\_+]\rho\_S + \gamma\_-(t)\mathcal{D}\[\sigma\_-]\rho\_S\$$

where $\mathcal{D}\[O]\rho = O\rho O^\dagger - \frac{1}{2}{O^\dagger O, \rho}$ is the Lindblad superoperator, and all coefficients $\tilde{\omega}, \gamma\_{\pm,z}$ are time-dependent.

The emergent Hamiltonian is:

\$$K\_S(t) = \frac{\tilde{\omega}(t)}{2}\sigma\_z\$$

with renormalised frequency $\tilde{\omega}(t) = \omega\_0 + \delta\tilde{\omega}(t)$.

#### 5.3 Time-Dependent Energy Renormalisation

> **This section incorporates results from Colla et al. (2025), Nature Communications 16:2502**

According to the minimal-dissipation Ansatz, the splitting between coherent (Hamiltonian) and incoherent (dissipator) evolution is uniquely determined by minimising the dissipator's action.

For the mode initially in vacuum ($\bar{n} = 0$), the energy shift has an explicit analytic form:

\$$\delta\tilde{\omega}(t) = -\frac{2g^2}{\Delta} \cdot \frac{1}{1 + \left(1 + \frac{4g^2}{\Delta^2}\right)\cot^2\left(\frac{\pi t}{T}\right)}\$$

where $T(\Delta) = 2\pi/\sqrt{\Delta^2 + 4g^2}$ is the JC oscillation period.

**Key features**:

* The shift is _periodic_ in coupling duration with period $T$
* Maximum shift: $\delta\tilde{\omega}(T/2) = -2g^2/\Delta$
* Near resonance ($\Delta \to 0$), the effect is resonantly enhanced

**Time-averaged shift**:

\$$\langle \delta\tilde{\omega}(t) \rangle\_T = \frac{-2g^2 , \text{sgn}(\Delta)}{|\Delta| + 2\pi/T}\$$

This equals the dressed-state energy shift—the conventional Lamb shift emerges as a _time average_ of fundamentally time-dependent dynamics.

#### 5.4 Experimental Observation (Freiburg 2025)

Recent trapped-ion experiments observed these time-dependent shifts directly:

| Parameter                                   | Value                               |
| ------------------------------------------- | ----------------------------------- |
| Mode frequency $\omega\_m$                  | $2\pi \times 1.30$ MHz              |
| Coupling $g/\omega$                         | $\approx 0.05$ (near USC threshold) |
| Detuning $\Delta/g$                         | $\approx 0.8$                       |
| Maximum shift $\delta\tilde{\omega}/\omega$ | $\approx 15%$                       |
| Mean shift                                  | $\approx 4%$                        |

The observed modulation matches the minimal-dissipation prediction (Eq. above), providing direct evidence for time-dependent energy renormalisation in the JC model.

#### 5.5 The Generalised Lamb Shift

> **Conceptual Reframing**
>
> The Lamb shift and AC Stark shift—traditionally viewed as static energy corrections—are time-averaged manifestations of fundamentally dynamic phenomena. They arise from correlation buildup between system and environment, appearing only constant when the environment is traced out and time-averaged.

In the dispersive limit ($|\Delta| \gg g$):

\$$\langle \delta\tilde{\omega} \rangle\_T \to -\frac{g^2}{\Delta}\$$

recovering the standard Lamb shift formula. But this is a limiting case of a more general time-dependent structure.

***

### 6. Mode Damping and Memory

#### 6.1 Closed vs Open: The Fundamental Distinction

| Property    | Closed (single mode)  | Open (continuum bath)   |
| ----------- | --------------------- | ----------------------- |
| Spectrum    | Discrete              | Continuous              |
| Collapse    | Temporary (dephasing) | Permanent (decoherence) |
| Information | Preserved (entangled) | Lost (to environment)   |
| Entropy     | Constant              | Increases               |
| Revivals    | Yes                   | No                      |

In a closed system, the "collapse" of spin coherence is temporary—the full state remains pure, but the spin's reduced state loses coherence due to entanglement with the mode. Given sufficient time, coherence returns (revival).

In an open system coupled to many modes, collapse is permanent—information leaks into uncontrollable degrees of freedom.

#### 6.2 Adding True Dissipation

When the mode leaks photons (rate $\kappa$) or the spin has spontaneous emission (rate $\gamma$):

\$$\dot{\rho} = -\frac{i}{\hbar}\[H, \rho] + \kappa \mathcal{D}\[a]\rho + \gamma \mathcal{D}\[\sigma^-]\rho\$$

The competition between coherent dynamics and dissipation yields:

* **Strong damping** ($\kappa, \gamma \gg g$): Quantum coherence constantly "monitored," no entanglement buildup
* **Moderate damping**: Damped revivals—each revival smaller than the last
* **Weak damping** ($\kappa, \gamma \ll g$): Near-ideal JC dynamics with slow decay envelope

> **Overclaim Protection**
>
> The Lindblad master equation is Markovian _by construction_. It cannot capture non-Markovian backflow. However, a single damped mode with $\kappa \sim g$ can _emulate_ memory effects on timescales $t \lesssim \kappa^{-1}$. Do not confuse this with true system-bath memory.

***

### 7. Emulating Power-Law Baths: What Is and Is Not Possible

#### 7.1 The Spin–Boson Benchmark

The full spin–boson model couples a two-level system to a _continuum_ of oscillators characterised by spectral density $J(\omega) \sim \omega^s$:

* $s < 1$: Sub-Ohmic (strong low-frequency coupling)
* $s = 1$: Ohmic
* $s > 1$: Super-Ohmic

#### 7.2 Single-Mode Emulation

A single mode cannot reproduce a continuum. However, the _dynamical signatures_ can be emulated:

| True Bath Property           | Single-Mode Emulation                    |
| ---------------------------- | ---------------------------------------- |
| Spectral density $J(\omega)$ | Distribution $p\_n$ in excitation space  |
| Power-law decay envelope     | Power-law $p\_n$ yields $t^{-(\beta-1)}$ |
| Bath bandwidth               | Preparation cutoff $n\_{\max}$           |
| Non-Markovian backflow       | Mode recurrences (different mechanism)   |

#### 7.3 The Emulation Boundary

What _cannot_ be emulated:

* True information loss (single mode always recurs)
* Bath-induced localisation (requires continuum)
* Arbitrary correlation functions (limited by $H\_{\text{JC\}}$ structure)

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

**Procedure**: Drop $\sigma^+ a^\dagger$ and $\sigma^- a$ terms.

**When valid**: $g \ll \omega, \omega\_0$ _and_ timescales $\gg 1/\omega$.

**What it yields**: The JC Hamiltonian decomposes into 2×2 blocks with exact eigenstates:

\$$|n, \pm\rangle = \cos\theta\_n |e,n\rangle \pm \sin\theta\_n |g, n+1\rangle\$$

**What it misses**: Bloch–Siegert shifts, virtual-photon physics, ground-state entanglement.

#### 8.3 The Braak Solution

For the full Rabi Hamiltonian, Braak (2011) showed integrability via:

1. Parity decomposition: $H = H\_+ \oplus H\_-$
2. Bargmann representation: Map to differential equations
3. Transcendental eigenvalue equation: Zeros of confluent Heun functions

**When to use**: USC regime where RWA fails but numerical truncation is uncertain.

**Practical note**: The solution is implicit (eigenvalues via root-finding), not closed-form. For dynamics, numerical methods are often more practical.

#### 8.4 Perturbative Expansions

**Dispersive regime** ($g/\Delta$ expansion):

\$$H\_{\text{eff\}} = H\_0 + \frac{g^2}{\Delta}\sigma\_z a^\dagger a + \frac{g^2}{2\Delta}\sigma\_z + O(g^4/\Delta^3)\$$

**Bloch–Siegert regime** ($g/(\omega\_0 + \omega)$ expansion):

\$$\delta\_{\text{BS\}} \approx \frac{g^2}{2(\omega\_0 + \omega)}\$$

**Strong-coupling regime** (treat $\omega$ as perturbation on $g$-dominated interaction).

#### 8.5 Numerical Methods

**Truncated diagonalisation**: Truncate oscillator space to $n \leq N\_{\max}$, diagonalise numerically.

* **Rule of thumb**: $N\_{\max} > \langle n \rangle + 5\sqrt{\langle n \rangle}$
* **Check**: Verify eigenvalues converge as $N\_{\max}$ increases

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

| Theoretical Object                             | Ion Trap Realisation                                 |
| ---------------------------------------------- | ---------------------------------------------------- |
| Spin-½                                         | Two hyperfine/Zeeman states                          |
| $\|{\downarrow}\rangle$, $\|{\uparrow}\rangle$ | e.g., $\|F=3, m\_F=3\rangle$, $\|F=2, m\_F=2\rangle$ |
| Mode $a, a^\dagger$                            | Quantised motion (axial COM mode)                    |
| $\omega$                                       | Trap frequency ($\sim 2\pi \times 1$ MHz)            |
| $\omega\_0$                                    | Zeeman/hyperfine splitting (tunable via $B$-field)   |
| $g$                                            | $\eta \Omega$ (Lamb-Dicke × laser Rabi rate)         |

#### 9.2 Sideband Transitions as JC/AJC Engineering

Laser-ion interaction in the Lamb-Dicke regime:

**Carrier** ($\delta = 0$): \$$H\_{\text{car\}} = \frac{\hbar \Omega}{2}(\sigma^+ + \sigma^-)\$$ Flips spin without changing motion.

**Red sideband** ($\delta = -\omega$): \$$H\_{\text{RSB\}} = \hbar \eta \Omega (\sigma^+ a + \sigma^- a^\dagger)\$$ JC interaction: spin flip ↔ phonon annihilation.

**Blue sideband** ($\delta = +\omega$): \$$H\_{\text{BSB\}} = \hbar \eta \Omega (\sigma^+ a^\dagger + \sigma^- a)\$$ Anti-JC interaction: spin flip ↔ phonon creation.

**Bichromatic drive** (both sidebands): \$$H\_{\text{bi\}} \approx \hbar g\_{\text{eff\}} (\sigma^+ + \sigma^-)(a + a^\dagger)\$$ Approximates the full Rabi Hamiltonian.

> **Operational Boundary**
>
> The Lamb-Dicke regime ($\eta \ll 1$) is not a fundamental limit—it is a convenience that linearises the coupling. Stronger coupling (large $\eta$) introduces higher-order terms $\sim \eta^2 (a + a^\dagger)^2 \sigma\_z$, which can be accounted for but invalidate the simple mapping.
>
> This handbook assumes $\eta \leq 0.2$ unless otherwise stated.

#### 9.3 Lamb-Dicke Validity

The Lamb-Dicke parameter:

\$$\eta = k \sqrt{\frac{\hbar}{2 m \omega\}} = k , x\_0\$$

where $k$ is the laser wavevector component along the mode, and $x\_0$ is the ground-state wavepacket size.

**Lamb-Dicke regime**: $\eta \sqrt{\langle n \rangle + 1} \ll 1$

This ensures the motional wavefunction samples only the linear part of the laser's spatial phase.

***

### 10. Engineering Initial States

#### 10.1 Ground-State Cooling

**Resolved sideband cooling**: Drive red sideband repeatedly. \$$|{\downarrow}, n\rangle \xrightarrow{\text{RSB\}} |{\uparrow}, n-1\rangle \xrightarrow{\text{decay\}} |{\downarrow}, n-1\rangle\$$

Achieves $\bar{n} \lesssim 0.1$ routinely.

#### 10.2 State Preparation Protocols

| Target State               | Preparation Method                            | Typical Fidelity |
| -------------------------- | --------------------------------------------- | ---------------- |
| $\|n\rangle$ Fock          | Sequential BSB $\pi$-pulses from $\|0\rangle$ | $>95%$           |
| $\|\alpha\rangle$ Coherent | Classical drive (displacement)                | $>99%$           |
| $\|\xi\rangle$ Squeezed    | Parametric modulation / pulse sequence        | $>90%$           |
| Cat state                  | Conditional displacement + measurement        | $>85%$           |
| Power-law mixture          | Stochastic sideband pulses                    | Tuneable         |

#### 10.3 Cat State Generation

Protocol (Monroe et al. 1996):

1. Prepare $|{\downarrow}, 0\rangle$
2. Apply carrier $\pi/2$ to create $(|{\downarrow}\rangle + |{\uparrow}\rangle)/\sqrt{2}$
3. Apply state-dependent displacement: $|{\downarrow}\rangle \to |{\downarrow}, \alpha\rangle$, $|{\uparrow}\rangle \to |{\uparrow}, -\alpha\rangle$
4. Result: $(|{\downarrow}, \alpha\rangle + |{\uparrow}, -\alpha\rangle)/\sqrt{2}$

> **Normalisation Note**
>
> The cat state $(|\alpha\rangle + |-\alpha\rangle)/\sqrt{2}$ is properly normalised only for $|\alpha| \gg 1$ (where $\langle \alpha | -\alpha \rangle = e^{-2|\alpha|^2} \approx 0$). For small $\alpha$, include the overlap correction.

***

### 11. Experimental Knob Map

| Theoretical Parameter         | Ion Trap Realisation     | Typical Range             | Calibration Method            |
| ----------------------------- | ------------------------ | ------------------------- | ----------------------------- |
| $g$                           | $\eta \Omega$            | $2\pi \times (1-100)$ kHz | Rabi flopping on sideband     |
| $\omega$                      | Trap frequency           | $2\pi \times (0.5-5)$ MHz | Secular frequency measurement |
| $\omega\_0$                   | Zeeman shift             | Tunable via $B$-field     | Microwave spectroscopy        |
| $\Delta = \omega - \omega\_0$ | Laser detuning           | $2\pi \times (0-1)$ MHz   | Ramsey spectroscopy           |
| $\kappa$ (damping)            | Sympathetic cooling      | $10-10^4$ s$^{-1}$        | Sideband asymmetry            |
| $\gamma\_\phi$ (dephasing)    | Engineered noise         | Tuneable                  | Ramsey decay                  |
| $\bar{n}$                     | Cooling quality          | $0.01-10$                 | Sideband ratio                |
| $p\_n$ distribution           | Squeeze + displace + mix | Engineered                | Motional tomography           |

#### 11.1 Accessing Different Regimes

| Regime                 | How to Access                                                           |
| ---------------------- | ----------------------------------------------------------------------- |
| Dispersive             | Large detuning $\Delta \gg g$ (detune laser far from sideband)          |
| Resonant JC            | $\Delta \approx 0$, moderate $\eta \Omega$                              |
| Near-USC               | Small $\Delta$, large $\eta \Omega$ (typical: $g/\omega \sim 0.05-0.1$) |
| Engineered dissipation | Add sympathetic cooling or electrode noise                              |

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

1. **Non-thermal initial states**: How does $K\_S(t)$ depend on squeezed, Fock, or cat initial states of the mode?
2. **Beyond JC**: Full characterisation of time-dependent renormalisation in the Rabi model.
3. **Quantum thermodynamics**: Connecting $K\_S(t)$ to work and heat definitions at strong coupling.

#### 14.2 Extensions

1. **Multi-mode environments**: How do signatures change with 2, 3, ..., $N$ modes?
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

***

## Appendix A: Notation Summary

| Symbol                            | Meaning                                    |
| --------------------------------- | ------------------------------------------ |
| $\omega\_0$                       | Bare spin transition frequency             |
| $\omega$                          | Oscillator/mode frequency                  |
| $g$                               | Spin-mode coupling strength                |
| $\Delta = \omega - \omega\_0$     | Detuning                                   |
| $\eta$                            | Lamb-Dicke parameter                       |
| $\Omega$                          | Laser Rabi frequency                       |
| $\bar{n}$                         | Mean thermal occupation                    |
| $p\_n$                            | Fock-state probability distribution        |
| $\Omega\_n = 2g\sqrt{n+1}$        | $n$-photon Rabi frequency                  |
| $T = 2\pi/\sqrt{\Delta^2 + 4g^2}$ | JC oscillation period                      |
| $K\_S(t)$                         | Emergent (renormalised) system Hamiltonian |
| $\tilde{\omega}(t)$               | Renormalised spin frequency                |

***

## Appendix B: Version History

| Version | Date       | Changes                                                                                                                         |
| ------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------- |
| 0.1     | 2025-12-17 | Initial draft (review format)                                                                                                   |
| 0.2     | 2025-12-17 | Modular restructure; Guardian protections; Navigator; minimal-dissipation Ansatz; power-law emulator; trapped-ion axis elevated |

***

_End of Handbook v0.2_
