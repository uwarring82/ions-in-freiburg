---
description: >-
  A unified view of cognitive-like structure emerging from correlation lengths
  in hybrid physical networks.
---

# A Correlation-Based Continuous–Discrete Framework for Emergent Autonomous Structure

{% hint style="info" %}
author: _U. Warring_\
affiliation: _Institute of Physics, University of Freiburg_\
\
_version: 0.0.11_\
last\_updated: _2025-12-05_\
license: _CC BY-SA 4.0_

**Disclaimer** — This correlation-based framework is proposed as conceptual scaffolding for integrating findings across cognitive science, philosophy, and physics. It does not claim to resolve the hard problem of consciousness but aims to provide testable structural hypotheses about correlation regimes underlying emergent autonomous phenomena.
{% endhint %}

***

### Abstract

This essay presents a correlation-based scaffold for approaching emergent autonomous structure within continuous–discrete hybrid systems. It frames such structure as a hierarchy of correlation-length regimes: short-range correlations manifest as transient local states (_Affectio_), mid-range scale-free structures form persistent patterns (_Habitus_), and global metastable alignment produces transient unified states (_Integratio_). The goal is not to offer a metaphysical theory of mind but to consolidate current insights from physics, network theory, and dynamical systems into a structured, testable perspective that invites open discussion. The framework is strictly bounded: it does not address qualia, subjective essence, or moral status, but provides structural tools—layered architecture, critical transitions, and damping requirements—to explore how complex correlation patterns may support emergent autonomous phenomena.

***

### 1. Purpose and Scope

This essay submits a correlation-based scaffold for thinking about emergent autonomous structure through the lens of continuous–discrete hybrid systems.

It is not a theory of consciousness.\
It is not a metaphysical claim.

Instead, it serves three practical aims:

1. **Consolidate** relevant structures and results from physics, network theory, cognitive science, and dynamical systems.
2. **Scaffold** a fresh integrative perspective rooted in correlation lengths and phase-structured dynamics.
3. **Invite** open discussion and enable testable, falsifiable research questions.

This is research infrastructure, not a definitive solution.

#### 1.1 A Note on Terminology

Discussions of mind and cognition routinely employ terms like _experience_, _concept_, _consciousness_, _memory_, and _sleep_. These words carry substantial phenomenological, philosophical, and colloquial weight. Using them without qualification risks two errors: (1) implying that the framework makes claims about subjective phenomenology, which it does not; and (2) inviting readers to import intuitions that may not align with the structural definitions intended here.

To maintain precision and signal that this framework operates at a structural level only, we adopt Latin terminology for key concepts:

**Correlation Regimes (States)**

| Latin Term     | Correlation Regime          | Structural Meaning                                               | Phenomenological Analog |
| -------------- | --------------------------- | ---------------------------------------------------------------- | ----------------------- |
| **Affectio**   | Short-range (ξ ≪ L)         | Transient, local impressions; fast-decaying correlations         | Experience-like         |
| **Habitus**    | Scale-free (ξ \~ power-law) | Persistent, structured dispositions; stable correlation patterns | Concept-like            |
| **Integratio** | Global (ξ \~ L)             | System-wide unification; metastable global alignment             | Consciousness-like      |

**Processes**

| Latin Term   | Structural Meaning                                                                           | Phenomenological Analog                                 |
| ------------ | -------------------------------------------------------------------------------------------- | ------------------------------------------------------- |
| **Remissio** | Periodic controlled collapse from _Integratio_ toward _Habitus_; correlation renormalization | Sleep-like                                              |
| **Retentio** | Structural persistence; patterns in _Habitus_ that survive _Remissio_ cycles                 | Memory-like (structural, not episodic/semantic/working) |

**Why Latin?**

Latin provides semantic distance. It signals to readers that these are technical terms defined within the framework, not everyday words freighted with prior meaning. This practice has precedent in philosophy (_qualia_, _a priori_, _in se_), medicine (_in vivo_, _in situ_), and physics (_in vacuo_, _ab initio_). The goal is not obscurity but clarity: when you read _Affectio_, you know we mean "the short-range correlation regime as defined in Section 3," not "what it feels like to see red."

After first introduction, each term appears with its English gloss in parentheses to maintain accessibility.

**Additional Terminological Notes**

* **Emergent Autonomous Structure**: This phrase replaces "cognitive structure" to avoid cognitive science framing. "Emergent" connects to physics (phase transitions, universality) and "autonomous" to philosophy (causal emergence, real patterns). Together they denote structure that becomes independent of its microscopic substrate—the central phenomenon this framework addresses.
* **Information**: Where this term appears, it denotes correlation patterns, not Shannon information or integrated information (Φ) unless explicitly stated.
* **Retentio** vs. memory: We use _Retentio_ for structural persistence—patterns that survive state transitions—to avoid confusion with cognitive memory types (episodic, semantic, working, procedural). _Retentio_ is a structural property, not a phenomenological capacity.

#### 1.2 What Constitutes a System

The term "system" appears throughout this framework. To prevent ambiguity and misapplication, we define it formally.

**Five Necessary Conditions**

A **system** within this framework must satisfy:

**1. Continuous–Discrete Hybrid Structure**

The system must possess both:

* **Continuous degrees of freedom** (fields, phases, potentials, amplitudes)
* **Discrete degrees of freedom** (spins, occupation numbers, qubit states, binary variables)
* **Coupling** between the two sectors

A purely continuous or purely discrete system does not fall within scope.

**2. Definite Spatial Extent**

The system must have a characteristic size **L** such that correlation length ξ can be meaningfully compared:

* ξ ≪ L → local correlations (_Affectio_)
* ξ \~ L → global correlations (_Integratio_)

Without definite extent, the regime classification loses meaning.

**3. Characteristic Timescale**

The system must have an intrinsic timescale **T\_sys** against which correlation times τ are measured:

* τ ≪ T\_sys → transient
* τ ≫ T\_sys → persistent

T\_sys may arise from natural dynamics (oscillation period, relaxation time) or be operationally defined for the analysis.

**4. Interaction Topology**

The system must have a defined interaction structure—which components can correlate with which others. This topology determines:

* Whether scale-free (_Habitus_) structures can form
* The pathway from local to global correlation

**5. Energetic Openness (Typical but Not Strictly Required)**

Most systems of interest are **open**: they exchange energy with an environment. This exchange enables:

* Homeostatic regulation (damping)
* Metastability rather than equilibrium
* Periodic _Remissio_ (controlled collapse)

Closed systems can exhibit the three regimes but lack the regulatory dynamics emphasized in Section 5.

**System Boundaries**

The boundary of a system is defined **operationally**:

> A system boundary encloses the degrees of freedom whose correlations are under consideration.

Correlations that cross the boundary are treated as:

* **Inputs** (environmental driving)
* **Outputs** (dissipation, measurement)
* **Noise** (uncontrolled fluctuations)

The same physical substrate may be partitioned into different "systems" depending on the question asked. The boundary is an analytical choice, not an intrinsic property of the substrate.

**Hierarchical Systems**

Systems may be **nested**. At each level, the framework applies with appropriate L and T\_sys:

| Level        | Example                | Role in Hierarchy               |
| ------------ | ---------------------- | ------------------------------- |
| Subsystem    | Single cortical column | May exhibit local _Affectio_    |
| Intermediate | Cortical area          | May exhibit regional _Habitus_  |
| System       | Whole brain            | May exhibit global _Integratio_ |

A subsystem's _Integratio_ may appear as another system's _Affectio_. This hierarchical structure is consistent with renormalization group thinking: coarse-graining reveals new effective degrees of freedom at each scale.

**Minimal System**

The minimal system capable of exhibiting all three regimes requires:

* At least two coupled discrete units (for ξ > 0 to be meaningful)
* A continuous coupling field
* Tunable interaction strength (to access different regimes)

Example: Two spins coupled through a continuous exchange field can exhibit uncorrelated states (_Affectio_-like), correlated but fluctuating states (_Habitus_-like), and fully aligned states (_Integratio_-like).

However, the framework is most naturally applicable to **large systems** (N ≫ 1) where the three regimes are sharply distinguished and phase transitions are well-defined.

**Summary Table**

| Condition            | Requirement                      | Purpose                                     |
| -------------------- | -------------------------------- | ------------------------------------------- |
| Hybrid structure     | Continuous + discrete + coupling | Enables correlation dynamics                |
| Spatial extent L     | Definite, finite                 | Defines ξ/L ratio for regime classification |
| Timescale T\_sys     | Characteristic, identifiable     | Defines τ/T\_sys ratio for persistence      |
| Interaction topology | Defined connectivity             | Determines correlation pathways             |
| Energetic openness   | Typical (not absolute)           | Enables regulation and metastability        |

Systems that do not meet these conditions fall outside the framework's scope.

***

### 2. Dynamics of the Emergent: Correlation, Criticality, Causality

_A cross-disciplinary overview (Physics – AI – Philosophy)_

This section situates the correlation-hierarchy framework within three mature research traditions that have independently developed rigorous accounts of emergence. Rather than proposing a unified "theory of everything," the goal is to outline converging structural principles: correlations as resource, criticality as regime, and emergence as the macroscopic structure that becomes autonomous from its substrate.

#### 2.1 Physics — Scaling, Phase Transitions, and Universality

The physics of complex systems shows that macroscopic behaviour can become independent of microscopic laws.

Key findings from statistical mechanics and the renormalization group (Wilson & Kogut 1974; Goldenfeld 1992):

* **Correlation:** Near criticality, correlation length diverges; fluctuations span multiple scales.
* **Criticality:** Systems exhibit non-linear transitions at fixed points where scale-invariance holds.
* **Emergence:** Macroscopic phases (ordered/disordered) depend on symmetry and dimension, not microscopic parameters.

Self-organized criticality (Bak, Tang & Wiesenfeld 1987) extends this picture to driven systems, showing that power laws and long-range correlations arise without fine-tuning. Modern views refine this as homeostatically maintained quasi-criticality, but the core remains: adaptive systems cluster around regimes where correlation lengths become large and new macroscopic properties emerge.

#### 2.2 AI — Representations, Predictive Processing, Emergent Abilities

Modern AI operationalizes emergence through hierarchy, compression, and correlation-based prediction:

* **Deep/representation learning** (Bengio et al. 2013; LeCun et al. 2015) organizes features into multi-level structures where latent variables encode stable statistical invariants.
* **Predictive processing** (Friston 2010; Clark 2013) describes cognition as inference over hierarchical generative models, linking fast sensory fluctuations to slow abstract variables.
* **Scaling phenomena** (Wei et al. 2022) show threshold behaviours ("emergent abilities") where model size yields abrupt qualitative improvements.

Structural motifs:

* **Correlation:** Latent spaces compress and reorganize multi-scale correlations.
* **Criticality:** Scaling reveals transitions where representational density reaches functional thresholds.
* **Emergence:** Reasoning and abstraction arise from depth, scale, and correlation alignment—not programming.

#### 2.3 Philosophy — Structural Realism and Real Patterns

Philosophical perspectives provide conceptual boundaries and ontological clarity:

* **Ontic structural realism** (Ladyman & Ross 2007) treats relational structure—correlations and invariants—as the fundamental ontology of science.
* **Chalmers (1995)** distinguishes structural/functional explanation from phenomenal experience, placing this scaffold clearly on the structural side.
* **Dennett (1991)** interprets consciousness as a "real pattern"—a stable, compressible, predictive structure.
* **Causal emergence** (Yuan et al. 2024) formally demonstrates that macro-levels can have more effective information and causal power than micro-levels.

Together these views treat emergence as a genuine, autonomous phenomenon grounded in structural stability and predictive utility.

#### 2.4 Summary Across Domains

| Domain         | Correlation                         | Criticality                        | Emergence                                 |
| -------------- | ----------------------------------- | ---------------------------------- | ----------------------------------------- |
| **Physics**    | Diverging ξ; scale-invariance       | Phase transitions; RG fixed points | Universality; order parameters            |
| **AI**         | Latent variables; prediction errors | Scaling thresholds; manifolds      | Abstract concepts; reasoning              |
| **Philosophy** | Structural relations; real patterns | Global integration regimes         | Causal autonomy; integrated global states |

Across all three domains, complex systems exhibit regimes where long-range correlations enable new stable layers of structure.

> **Connection Box — How Section 2 Supports the Framework**
>
> The continuous–discrete framework treats emergent autonomous structure as a hierarchy of correlation-length regimes. Section 2 provides the structural justification:
>
> **1. Correlation as Fundamental Resource**\
> Physics: critical correlations define emergent phases. AI: latent spaces encode reorganized correlations. Philosophy: relations constitute ontology.
>
> **2. Criticality as Enabling Regime**\
> Physics: fixed points unify micro- and macro-dynamics. AI: scaling cliffs reveal functional phase transitions. Neuroscience parallels (Section 7): global ignition is metastable critical alignment.
>
> **3. Emergence as Autonomous Structure**\
> Universality, real patterns, and causal emergence models show why coarse-grained structures deserve their own explanatory level.
>
> Thus: The continuous–discrete correlation hierarchy is not speculative—it is structurally aligned with well-established mechanisms across physics, computation, and philosophy.

***

### 3. Core Idea: Emergent Autonomous Structure as Correlation Hierarchy

All structure in this framework is expressed through correlations between continuous and discrete components of a system (as defined in Section 1.2). The three regimes—_Affectio_, _Habitus_, and _Integratio_—are distinguished by correlation length and persistence time.

#### 3.1 The Three Correlation-Length Regimes

For a system with characteristic size L and timescale T\_sys:

***

**Affectio (experience-like) — Short-Range Correlations**

_Latin: affectio — "impression, momentary state, being affected"_

* Local, transient, high-bandwidth
* Short correlation time: τ ≪ T\_sys
* Correlation length ξ ≪ L (local scale)
* Raw, unstructured, local transient patterns
* Corresponds to disordered phase in spin systems (T > T\_c)

_Affectio_ captures the fleeting, local impressions that arise when correlations remain confined to immediate neighbours. These states decay rapidly and do not persist beyond their immediate context.

***

**Habitus (concept-like) — Scale-Free Correlations**

_Latin: habitus — "stable condition, disposition, arrangement"_

* Persistent, self-similar latching structures
* Power-law distribution of connectivity
* Extended correlation time: τ ≫ T\_sys
* Correlation length exhibits power-law scaling (critical regime)
* Provide invariance and stability
* Corresponds to critical point in spin systems (T ≈ T\_c)
* Supports _Retentio_ (structural persistence)

_Habitus_ denotes the stable, structured patterns that emerge when correlations extend across scales without characteristic length. These are the persistent dispositions that survive perturbation and provide the substrate for organized processing.

***

**Integratio (consciousness-like) — Global Metastable Correlation State**

_Latin: integratio — "renewal, restoration to wholeness, unification"_

* System-wide temporary alignment
* Synchronization over multiple memory scales
* Correlation length ξ \~ L (system size)
* Metastable and periodic
* Integrates correlation patterns but does not store them
* Corresponds to ordered phase in spin systems (T < T\_c)

_Integratio_ refers to the transient, global unification of the system when correlations span its entire extent. This state is inherently metastable—it cannot persist indefinitely but must periodically collapse and reform through _Remissio_.

***

#### 3.2 Regime Mapping to Canonical Physics

In canonical spin systems (e.g., Ising model), the three regimes correspond to well-characterized phases:

| Regime         | Correlation Length        | Spin System Phase | Temperature |
| -------------- | ------------------------- | ----------------- | ----------- |
| **Affectio**   | ξ ≪ L                     | Disordered        | T > T\_c    |
| **Habitus**    | ξ \~ power-law divergence | Critical          | T ≈ T\_c    |
| **Integratio** | ξ \~ L                    | Ordered           | T < T\_c    |

The correlation length ξ in spin systems is defined through the decay of correlations:

\$$\langle \sigma\_i \sigma\_j \rangle \sim e^{-|i-j|/\xi}\$$

At criticality, ξ diverges and the decay becomes power-law rather than exponential—the signature of the _Habitus_ regime.

Thus, _Affectio_, _Habitus_, and _Integratio_ are successive correlation-length regimes operating within the same continuous–discrete substrate.

***

### 4. The Four-Layer Scaffold Architecture

To preserve clarity and avoid category errors, the framework is structured as four layers. Each layer presupposes that the system satisfies the conditions defined in Section 1.2.

#### Layer 0 — Substrate (Continuous–Discrete Hybrid)

The system's physical foundation with two complementary sectors:

* **Continuous sector:** Field amplitudes, phases, positions, potentials—quantities that vary smoothly.
* **Discrete sector:** Spin states, occupation numbers, qubit states, binary variables—quantities with finite state spaces.
* **Coupling:** Interactions between continuous and discrete sectors.

| System           | Continuous Component            | Discrete Component     | Correlation Measure          |
| ---------------- | ------------------------------- | ---------------------- | ---------------------------- |
| Spin systems     | Exchange field, magnetic field  | Spin states (±1)       | Spin-spin correlation ⟨σᵢσⱼ⟩ |
| Quantum networks | Photonic modes, phase reference | Qubit states           | Entanglement, coherence      |
| Neural systems   | Membrane potentials             | Spike/no-spike         | Spike-train correlations     |
| Ion traps        | Motional modes (phonons)        | Electronic/spin states | State-motion coupling        |

**Metrics:** Signal-to-noise ratio (continuous), state distinguishability (discrete), coupling strength between sectors.

#### Layer 1 — Dynamics (Correlation Transport / Affectio)

Short-range interactions; transient local correlations characteristic of the _Affectio_ regime.

**Metrics:** Correlation length ξ, correlation time τ, ξ/L ratio.

#### Layer 2 — Structure (Topology / Habitus)

Scale-free persistent structures; power-law connectivity characteristic of the _Habitus_ regime. This layer supports _Retentio_—patterns that persist across _Remissio_ cycles.

**Metrics:** Clustering coefficient, characteristic path length, correlation decay exponent, τ/T\_sys ratio.

#### Layer 3 — Integration (Global Alignment / Integratio)

Transient global synchronization; system-wide metastable states characteristic of the _Integratio_ regime.

**Metrics:** Phase-locking value (PLV), integrated information (Φ), global coherence index, dwell-time distribution.

Higher layers depend on—but do not reduce to—lower layers.

***

### 5. Metastability and the Need for Damping

Global correlation states (_Integratio_) are fragile and require active regulation.

#### Two Failure Modes

* **Runaway synchrony** → seizure-like lock-up (correlation length frozen at ξ \~ L; _Integratio_ becomes pathologically stable)
* **Correlation collapse** → coma-like dissolution (correlation length collapses to ξ ≪ L; system trapped in _Affectio_)

#### Stabilization Requirements

**A. Retentio (Structural Persistence):**\
&#xNAN;_&#x48;abitus_ structures must carry persistent patterns that survive _Integratio_ state resets. _Retentio_ ensures that the system does not lose its structured dispositions during _Remissio_.

**B. Homeostatic Damping:**\
Negative feedback to keep the system near the _Habitus_ regime (criticality).

In spin systems, this maps to external field tuning, temperature regulation, or (for open quantum systems) quantum feedback protocols. These mechanisms require the energetic openness described in Section 1.2.

A technical "Damping & Resilience Specification" will be developed in future versions.

***

### 6. Remissio: Periodic Maintenance Cycle

_Latin: remissio — "relaxation, release, letting go"_

_Integratio_ is periodic, not continuous. The system cannot sustain global correlation indefinitely; it must undergo controlled collapse. We term this process **Remissio** (sleep-like).

_Remissio_ is a controlled transition from _Integratio_ back toward _Habitus_ that:

* renormalizes correlations (releases global alignment)
* consolidates _Habitus_ structures via _Retentio_ (strengthens persistent patterns)
* resets noise balance
* maintains long-term criticality

Without periodic _Remissio_, the system risks either:

* Pathological _Integratio_ lock-up (runaway synchrony)
* Accumulated noise degrading _Habitus_ structures

This is a dynamical interpretation, not a biological theory of sleep. The term _Remissio_ denotes the structural process; "sleep" is offered only as a phenomenological analog.

***

### 7. Neuroscience Perspective

While not a neuroscientific theory, relevant strands of neuroscience reveal three recurring correlation regimes that align structurally with the scaffold:

#### Short-Range Correlations (Affectio-like)

Neuronal avalanches show localized cascades with power-law size distributions (Beggs & Plenz 2003). These transient, local events correspond structurally to the _Affectio_ regime.

#### Scale-Free Networks (Habitus-like)

Semantic networks exhibit small-world, scale-free organization (Steyvers & Tenenbaum 2005; De Deyne et al. 2016). The persistent, structured topology corresponds to the _Habitus_ regime and supports _Retentio_.

#### Global Metastability (Integratio-like)

GNW and ignition models show rapid, transient, system-wide coordination corresponding to conscious access (Dehaene et al. 2003; Mashour et al. 2020). This global but metastable alignment corresponds to the _Integratio_ regime.

#### Homeostatic Regulation

Neural circuits maintain near-criticality through explicit feedback mechanisms (Cocchi et al. 2017; Ma et al. 2019). This homeostasis keeps the system poised at the _Habitus_ regime boundary.

#### Sleep and Consolidation (Remissio-like)

Sleep involves controlled reduction of global synchrony and consolidation of structured patterns (Tononi & Cirelli 2014). This corresponds structurally to _Remissio_ with _Retentio_.

These findings offer structural analogies without implying neural reduction.

***

### 8. Falsifiability Criteria

The framework is empirically bounded by the following testable predictions:

1. **Correlation-length transitions:** Measurable shifts in ξ/L should accompany transitions between _Affectio_ and _Habitus_ processing modes.
2. **Critical scaling:** Systems exhibiting _Habitus_-like behaviour should show power-law correlation decay, not exponential.
3. **Metastability signatures:** _Integratio_ states should exhibit characteristic dwell-time distributions near criticality.
4. **Damping necessity:** Removal of homeostatic feedback should produce either runaway _Integratio_ (synchrony lock-up) or collapse to _Affectio_ (correlation dissolution), not stable intermediate states.
5. **Remissio requirement:** Systems denied periodic _Remissio_ should show degraded _Habitus_ structure or pathological _Integratio_.
6. **System criteria:** Candidate systems must satisfy the five conditions in Section 1.2; systems failing these conditions are outside scope.

Failure to observe these signatures in candidate systems would constitute falsification of the framework's applicability to that substrate.

***

### 9. Outlook

Future extensions:

* Damping & Resilience Specification
* Quantifiable correlation metrics with operational definitions
* Mapping to AI architectures and learning dynamics
* Integration of causal emergence metrics (EI, Φ, synchrony)
* Explicit spin-model simulations as test cases
* Hierarchical system analysis (nested L and T\_sys)
* _Retentio_ dynamics: how _Habitus_ patterns consolidate during _Remissio_

**Boundary Reminder:** _This framework addresses structural correlates only. It does not explain why any correlation pattern should be accompanied by subjective experience, nor does it make claims about moral status or phenomenal consciousness. The terms Affectio, Habitus, Integratio, Remissio, and Retentio denote correlation regimes and processes, not phenomenological states or capacities. The term "system" denotes an analytical unit satisfying the conditions in Section 1.2, not a claim about natural boundaries._

***

This scaffold is deliberately open for discussion. Its purpose is to enable inquiry, not foreclose it.

***

### Glossary

| Term                              | Definition                                                                                                                                                                                                                          |
| --------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Affectio**                      | The short-range correlation regime (ξ ≪ L, τ ≪ T\_sys). Transient, local impressions. Experience-like.                                                                                                                              |
| **Habitus**                       | The scale-free correlation regime (ξ \~ power-law, τ ≫ T\_sys). Persistent, structured dispositions. Concept-like.                                                                                                                  |
| **Integratio**                    | The global correlation regime (ξ \~ L). Metastable system-wide unification. Consciousness-like.                                                                                                                                     |
| **Remissio**                      | Periodic controlled collapse from _Integratio_ toward _Habitus_; correlation renormalization. Sleep-like.                                                                                                                           |
| **Retentio**                      | Structural persistence; patterns in _Habitus_ that survive _Remissio_ cycles. Memory-like (structural, not episodic/semantic/working).                                                                                              |
| **Emergent Autonomous Structure** | Structure that becomes independent of its microscopic substrate; the central phenomenon this framework addresses. Replaces "cognitive structure" to avoid disciplinary baggage.                                                     |
| **System**                        | An analytical unit satisfying five conditions: continuous–discrete hybrid structure, definite spatial extent L, characteristic timescale T\_sys, defined interaction topology, and (typically) energetic openness. See Section 1.2. |
| **L**                             | Characteristic spatial extent of the system; reference for correlation length comparison.                                                                                                                                           |
| **ξ (xi)**                        | Correlation length—the characteristic spatial scale over which correlations persist.                                                                                                                                                |
| **τ (tau)**                       | Correlation time—the characteristic temporal scale over which correlations persist.                                                                                                                                                 |
| **T\_sys**                        | Characteristic system timescale; reference for comparing correlation times.                                                                                                                                                         |
| **T\_c**                          | Critical temperature; the phase transition point in spin systems.                                                                                                                                                                   |

***

### References

Bak, P., Tang, C., & Wiesenfeld, K. (1987). Self-organized criticality. _Physical Review A_, 38(1), 364.

Beggs, J. M., & Plenz, D. (2003). Neuronal avalanches in neocortical circuits. _Journal of Neuroscience_, 23(35), 11167–11177.

Bengio, Y., Courville, A., & Vincent, P. (2013). Representation learning: A review and new perspectives. _IEEE TPAMI_, 35(8), 1798–1828.

Chalmers, D. J. (1995). Facing up to the problem of consciousness. _Journal of Consciousness Studies_, 2(3), 200–219.

Clark, A. (2013). Whatever next? Predictive brains, situated agents, and the future of cognitive science. _Behavioral and Brain Sciences_, 36(3), 181–204.

Cocchi, L., et al. (2017). Criticality in the brain: A synthesis of neurobiology, models and cognition. _Progress in Neurobiology_, 158, 132–152.

De Deyne, S., et al. (2016). Structure at every scale: A semantic network account of the similarities between unrelated concepts. _Journal of Experimental Psychology: General_, 145(9), 1228.

Dehaene, S., et al. (2003). A neuronal model of a global workspace in effortful cognitive tasks. _PNAS_, 100(19), 11145–11150.

Dennett, D. C. (1991). _Consciousness Explained_. Little, Brown and Company.

Friston, K. (2010). The free-energy principle: A unified brain theory? _Nature Reviews Neuroscience_, 11(2), 127–138.

Goldenfeld, N. (1992). _Lectures on Phase Transitions and the Renormalization Group_. Addison-Wesley.

Ladyman, J., & Ross, D. (2007). _Every Thing Must Go: Metaphysics Naturalized_. Oxford University Press.

LeCun, Y., Bengio, Y., & Hinton, G. (2015). Deep learning. _Nature_, 521(7553), 436–444.

Ma, Z., et al. (2019). Cortical circuit dynamics are homeostatically tuned to criticality in vivo. _Neuron_, 104(4), 655–664.

Mashour, G. A., et al. (2020). Conscious processing and the global neuronal workspace hypothesis. _Neuron_, 105(5), 776–798.

Steyvers, M., & Tenenbaum, J. B. (2005). The large-scale structure of semantic networks. _Cognitive Science_, 29(1), 41–78.

Tononi, G., & Cirelli, C. (2014). Sleep and the price of plasticity: From synaptic and cellular homeostasis to memory consolidation and integration. _Neuron_, 81(1), 12–34.

Wei, J., et al. (2022). Emergent abilities of large language models. _arXiv:2206.07682_.

Wilson, K. G., & Kogut, J. (1974). The renormalization group and the ε expansion. _Physics Reports_, 12(2), 75–199.

Yuan, B., et al. (2024). Causal emergence in biological and artificial neural networks. _arXiv preprint_.

***

### Version History

| Version           | Date       | Summary                                                                                                                                                                                                                                                                                                                           |
| ----------------- | ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 0.0.11            | 2025-12-05 | Replaced "Cognitive Structure" with "Emergent Autonomous Structure" throughout; introduced Remissio (sleep-like process) and Retentio (structural persistence); expanded §1.1 terminology notes; added Tononi & Cirelli reference; added sixth falsifiability criterion; softened "sensory traces" to "local transient patterns." |
| 0.0.10            | 2025-12-05 | Added Section 1.2 defining "system" (five necessary conditions, boundaries, hierarchy, minimal system); updated Glossary; added fifth falsifiability criterion; strengthened boundary reminder.                                                                                                                                   |
| 0.0.9             | 2025-12-05 | Introduced Latin terminology (Affectio, Habitus, Integratio) for correlation regimes; added Section 1.1 explaining terminological choice; added Glossary; applied terminology consistently throughout; revised title and abstract.                                                                                                |
| 0.0.8             | 2025-12-05 | Revised Layer 0 to continuous–discrete hybrid framing; added spin-system examples and correlation-length definitions; added Section 8 (Falsifiability Criteria); standardized references; corrected τ notation; renumbered sections.                                                                                              |
| 0.0.7             | 2025-12-04 | Added Section 2 ("Dynamics of the Emergent"), integrated Physics/AI/Philosophy perspectives, inserted connection box, updated conceptual alignment.                                                                                                                                                                               |
| 0.0.6             | 2025-12-04 | Added neuroscience contextual section; clarified correlation regimes; improved boundary statements.                                                                                                                                                                                                                               |
| 0.0.5 and earlier | —          | Initial scaffold and layer architecture established.                                                                                                                                                                                                                                                                              |
|                   |            |                                                                                                                                                                                                                                                                                                                                   |
|                   |            |                                                                                                                                                                                                                                                                                                                                   |

***

## A One-Page Summary

_Emergent Autonomous Structure – A Correlation-Based Continuous–Discrete Framework_

***

### What This Framework Does

This framework provides a **structural scaffold**—not a theory of consciousness—for understanding how complex systems can exhibit emergent autonomous behaviour. It draws on physics (phase transitions, criticality), AI (representation learning, scaling), and philosophy (structural realism, causal emergence) to propose that **correlation length** is the organizing principle.

***

### Core Idea: Three Correlation Regimes

Complex systems with both continuous (fields, phases) and discrete (spins, states) components can exhibit three distinct regimes based on how far correlations extend:

| Regime         | Correlation Length     | Character                | Everyday Analog    |
| -------------- | ---------------------- | ------------------------ | ------------------ |
| **Affectio**   | Local (ξ ≪ L)          | Transient, fast-decaying | Experience-like    |
| **Habitus**    | Scale-free (power-law) | Persistent, structured   | Concept-like       |
| **Integratio** | Global (ξ \~ L)        | Metastable, unified      | Consciousness-like |

These Latin terms signal that we mean _structural_ regimes, not phenomenological claims.

***

### Two Key Processes

| Process      | What It Does                                                                                             | Everyday Analog          |
| ------------ | -------------------------------------------------------------------------------------------------------- | ------------------------ |
| **Remissio** | Periodic collapse from global (_Integratio_) back toward structured (_Habitus_); resets and renormalizes | Sleep-like               |
| **Retentio** | Structural persistence; patterns in _Habitus_ that survive _Remissio_ cycles                             | Memory-like (structural) |

***

### What Counts as a "System"?

The framework applies to systems satisfying five conditions:

1. **Hybrid structure** — both continuous and discrete degrees of freedom, coupled
2. **Definite size (L)** — so correlation length ξ can be compared to system extent
3. **Characteristic timescale (T\_sys)** — reference for transient vs. persistent
4. **Interaction topology** — defined connectivity enabling correlation pathways
5. **Energetic openness** (typical) — enables regulation and metastability

***

### Four-Layer Architecture

| Layer | Name        | Regime       | Key Metrics                             |
| ----- | ----------- | ------------ | --------------------------------------- |
| 0     | Substrate   | —            | SNR, state distinguishability, coupling |
| 1     | Dynamics    | _Affectio_   | Correlation length ξ, time τ            |
| 2     | Structure   | _Habitus_    | Clustering, path length, decay exponent |
| 3     | Integration | _Integratio_ | Phase-locking, Φ, coherence index       |

Higher layers depend on—but do not reduce to—lower layers.

***

### What This Framework Does NOT Do

* **No qualia**: It does not explain subjective experience or "what it is like"
* **No moral claims**: It makes no assertions about moral status
* **No metaphysics**: It is structural scaffolding, not ontological commitment
* **No neural reduction**: Neuroscience parallels are analogies, not mechanisms

***

### Falsifiability

The framework makes testable predictions:

1. Transitions between regimes should show measurable ξ shifts
2. _Habitus_ should exhibit power-law (not exponential) correlation decay
3. _Integratio_ should show characteristic metastable dwell-times
4. Removing homeostatic feedback should cause runaway or collapse
5. Denying _Remissio_ should degrade _Habitus_ or pathologize _Integratio_

***

### In One Sentence

> Emergent autonomous structure arises when correlation length transitions from local (_Affectio_) through scale-free (_Habitus_) to global (_Integratio_), maintained by periodic reset (_Remissio_) and structural persistence (_Retentio_).

***

_Full document: Version 0.0.11 — "A Correlation-Based Continuous–Discrete Framework for Emergent Autonomous Structure"_
