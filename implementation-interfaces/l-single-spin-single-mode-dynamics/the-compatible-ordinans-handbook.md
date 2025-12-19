---
description: Single Spin ⊗ Single Mode as the Minimal Ordinan
icon: lightbulb-exclamation-on
---

# The Compatible Ordinans Handbook

Version: v0.0.1 (Draft)

Status: Internally consistent, Council-aligned

Perspective: Ordinans (compatible with the Common View)

***

### Foreword

#### The Common View and the Ordinans Perspective

This handbook presents the Common View of single-spin–single-mode quantum dynamics while introducing a new organising perspective: the Ordinans perspective.

The Common View describes _what happens_ in experimentally realised quantum systems: canonical Hamiltonians, control protocols, noise mechanisms, and measurement schemes developed across cavity QED, trapped ions, circuit QED, and optomechanics. This body of knowledge is mature, successful, and indispensable.

The Ordinans perspective does not revise this physics. Instead, it re-organises it according to a strict architectural separation between:

* a context-independent quantum system, and
* explicitly coupled environments.

This separation enables falsifiable statements about complex quantum behaviour even when full numerical prediction is impossible.

***

### Introduction

#### The Minimal Ordinans: Spin ⊗ Mode

We introduce the Ordinans perspective through the simplest non-trivial quantum system: a single two-level system (spin-½) coupled to a single harmonic oscillator mode.

The system is defined as

$$\mathcal{H}_{\mathrm{sys}} = \mathcal{H}_{\mathrm{spin}} \otimes \mathcal{H}_{\mathrm{mode}}$$,

with no additional structure.

This system appears universally across quantum platforms:

* atoms or superconducting qubits coupled to cavity modes,
* trapped ions with internal states coupled to motional modes,
* optomechanical systems coupling two-level defects to vibrational motion.

Nothing in this handbook alters the established physics of this system.

What changes is the scientific question:

> Not _“What happens?”,_\
> but _“What must be coupled for this to happen?”_

***

#### From Description to Structure

In the Common View, decoherence, dissipation, stochasticity, and measurement backaction are often introduced as secondary or parasitic effects.

In the Ordinans perspective:

* the system is frozen (context-independent definition),
* all complexity is traced to explicit couplings.

Noise, dissipation, measurement, clocks, and feedback are treated as physically real environments, modelled as subsystems coupled through designed interfaces.

What is designed is the coupling geometry, not reality itself.

***

#### Falsifiability without Predictability

As quantum systems grow in complexity, full numerical prediction becomes infeasible. This creates a verification problem in quantum simulation.

The Ordinans perspective does not solve computational complexity.

Instead, it restores scientific falsifiability by requiring:

* explicit environment specification,
* switchable interfaces,
* null-environment tests.

A claim is admissible only if the predicted behaviour disappears when the coupling is removed.

***

#### Falsification Criterion (Explicit)

The Ordinans perspective fails if:

1. Removing a specified environment does not remove the claimed effect, or
2. Two systems with identical system definitions but different environment couplings behave identically when they should not, or
3. Observed behaviour cannot be traced to any explicit coupling.

The spin ⊗ mode system serves as a calibration point: if the framework fails here, it cannot succeed at larger scales.

***

## PART I — LAYER 0

### The Core (Context-Independent System)

> _No irreversibility. No scaling. No interpretation._

***

### Chapter 1 — The Spin ⊗ Mode System

Content

* Hilbert spaces: \mathbb{C}^2 \otimes \ell^2(\mathbb{N})
* Jaynes–Cummings and Rabi Hamiltonians
* Rotating-wave and ultrastrong-coupling regimes
* Physical implementations across platforms

References

* E. T. Jaynes and F. W. Cummings, _Proc. IEEE_ 51, 89 (1963)
* I. I. Rabi, _Phys. Rev._ 49, 324 (1936)
* S. Haroche and J.-M. Raimond, _Exploring the Quantum_ (Oxford, 2006)
* A. Blais et al., _Phys. Rev. A_ 69, 062320 (2004)

***

### Chapter 2 — Reachability and Ideal Control

Content

* Ideal unitary control
* Reachable sets and controllability
* State preparation as initial-condition engineering (not dynamics)

References

* S. Lloyd, _Phys. Rev. Lett._ 75, 346 (1995)
* D. J. Wineland et al., _J. Res. NIST_ 103, 259 (1998)
* C. Law and J. Eberly, _Phys. Rev. Lett._ 76, 1055 (1996)

***

### Chapter 3 — Symmetries and Constraints

Content

* Parity symmetry
* Energy conservation in the closed system
* What no environment may violate silently

References

* C. Cohen-Tannoudji et al., _Atom–Photon Interactions_ (Wiley, 1992)
* W. H. Zurek, _Rev. Mod. Phys._ 75, 715 (2003)

***

## PART II — LAYER 1

### Interfaces (Coupling Geometries)

> _Mathematical couplings only. No records. No observers._

***

### Chapter 4 — Unitary Interfaces

Content

* Time-dependent Hamiltonians
* Sideband and parametric couplings
* Tunable interaction strengths
* “Valves” between system and environment

References

* D. Leibfried et al., _Rev. Mod. Phys._ 75, 281 (2003)
* A. Wallraff et al., _Nature_ 431, 162 (2004)

***

### Chapter 5 — Measurement as Interface

Content

* Completely positive maps
* Kraus operators and POVMs
* Measurement strength as coupling parameter
* Information–disturbance tradeoff

Explicit exclusions

* No “outcomes”
* No “collapse”
* No observer language

References

* K. Kraus, _States, Effects, and Operations_ (Springer, 1983)
* H. Wiseman and G. Milburn, _Quantum Measurement and Control_ (Cambridge, 2010)
* K. Jacobs, _Stochastic Processes for Physicists_ (Cambridge, 2010)

***

### Chapter 6 — The Canonical Null Test

Content

* Zero-Interface limit
* Switchability as axiom
* Parametric null tests
* Substitute null environments
* Goodhart-style failure modes

References

* H.-P. Breuer and F. Petruccione, _The Theory of Open Quantum Systems_ (Oxford, 2002)
* H.-P. Breuer et al., _Rev. Mod. Phys._ 88, 021002 (2016)

***

## PART III — LAYER 2

### Ordinans (Engineered Worlds)

> _Interpretation and emergence live here._

***

### Chapter 7 — The Dissipative World

Content

* Thermal baths
* Lindblad dynamics
* T\_1, T\_2 as world properties
* Dissipation as design tool

References

* G. Lindblad, _Commun. Math. Phys._ 48, 119 (1976)
* C. Gardiner and P. Zoller, _Quantum Noise_ (Springer, 2004)
* J. Barreiro et al., _Nature_ 470, 486 (2011)

***

### Chapter 8 — The Monitored World

Content

* Designation of interface outputs as records
* Conditional dynamics
* Feedback as world logic
* Measurement ≠ thermal bath (operational distinction)

References

* H. Wiseman and G. Milburn, _Phys. Rev. Lett._ 70, 548 (1993)
* J. Atalaya et al., _Phys. Rev. A_ 97, 020104 (2018)
* Y. Li et al., _Phys. Rev. Lett._ 121, 010601 (2018)

***

### Chapter 9 — The Protected World (Soft Coastline)

Content

* Error correction as environment engineering
* Bosonic and cat codes
* Logical vs physical decay
* Protection claims and null tests

References

* Z. Leghtas et al., _Science_ 347, 853 (2015)
* M. Mirrahimi et al., _New J. Phys._ 16, 045014 (2014)
* B. Terhal, _Rev. Mod. Phys._ 87, 307 (2015)

***

## PART IV — EVALUATION SUITE

***

### Chapter 10 — Scaling Laws

Content

* Exponential vs algebraic decay
* Environment statistics → scaling
* Breakdown of perturbative intuition

References

* J.-P. Bouchaud and A. Georges, _Phys. Rep._ 195, 127 (1990)
* Á. Rivas et al., _Rep. Prog. Phys._ 77, 094001 (2014)

***

### Chapter 11 — Falsification Protocols

Content

* Cross-world comparison
* Platform-independent tests
* Reporting standards
* What constitutes rejection

References

* K. Popper, _The Logic of Scientific Discovery_ (Routledge, 1959)
* R. Blatt and C. Roos, _Nat. Phys._ 8, 277 (2012)

***

### Appendices

A. Mathematical Conventions

B. Environment Modelling Examples

C. Terminology and Forbidden Language

***

### Closing Statement

> _This handbook does not claim to predict complex quantum worlds. It claims to make them falsifiable._

***
