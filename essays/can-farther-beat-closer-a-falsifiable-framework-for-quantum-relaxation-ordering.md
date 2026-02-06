---
description: A collaboration invitation
---

# Can "Farther" Beat "Closer"? A Falsifiable Framework for Quantum Relaxation Ordering

{% hint style="info" %}
**Authors:** Ulrich Warring\
**Last updated:** 2026-02-06\
**Status:** Community Narrative (Sail)\
**License:** CC BY 4.0
{% endhint %}

***

The quantum Mpemba effect has a problem:&#x20;

<p align="center"><em>Nobody agrees what it means.</em></p>

At least four distinct definitions circulate in recent literature. Some invoke trace-distance crossings. Others focus on Lindbladian spectral gaps. Others still require quantum coherences. And the newest class—non-Markovian anomalies—identifies effects that vanish entirely in the Markovian limit. A system can satisfy one definition whilst violating another. Papers claim or refute "the quantum Mpemba effect" without specifying which definition applies, or whether their dynamical regime even permits comparison.

Worse: most claims lack falsification criteria. Without pre-registered answers to what would count as disconfirmation, the literature risks accumulating unfalsifiable assertions dressed in quantum language.

### The reframing

We propose stripping the phenomenon to its operational core. In trapped-ion systems, temperature is well-defined—as ensemble averages over repeated runs with identical parameters—and is controllable via cooling parameters that set initial motional state occupations. But temperature is one control parameter among several: detuning, coupling strength, drive amplitude, initial motional temperature. None is privileged.

The classical Mpemba question ("does hot beat cold?") becomes a special case of a more general question. When you turn any control knob, two things change: (i) the system's long-time state shifts, so you may start farther from the new target; (ii) the relaxation speed changes. The question becomes sharp:

> **Can the speedup overcompensate the extra distance, so that equilibration time decreases despite starting farther away?**

If yes, we call it _quench-controlled relaxation ordering_. The classical temperature-based effect is one instance; our framework handles any control axis uniformly.

This thread belongs to a broader programme we are pursuing: defining and understanding complex phenomena as a topology of causal connections. Where others treat relaxation as a kinetic race along a single axis, we read it as geometry—the structure of causal pathways linking an initial state to its equilibrium through the space of accessible controls. Relaxation ordering, on this view, is a topological feature of that landscape: a region where the causal connection between "farther start" and "later arrival" inverts. Making that geometric structure explicit is what turns a curiosity into a falsifiable claim.

### What makes this framework different

Three features distinguish it from existing approaches:

**A primary test without derivatives.** We compare equilibration times directly for parameter pairs. No numerical differentiation, no noise amplification. An interpretive inequality decomposes why ordering occurred, but the pairwise comparison is the adjudicator.

**An explicit validity boundary.** The bath memory time—the timescale over which environment correlations persist—separates non-Markovian transients from the regime where exponential fitting makes sense. If your analysis window overlaps with the memory time, the test is void. This prevents the most common failure mode: fitting Markovian models to non-Markovian data. In the language of our causal-topology programme, the memory time marks the boundary where the causal geometry of the bath itself becomes non-trivial—where simple arrow-of-time reasoning breaks down and the full connection structure must be respected.

**Asymmetric adjudication logic.** Our prototype platform measured only one spin component. That is a lower bound on the full state-space distance. Satisfaction confirms ordering in the measured sector. Failure is inconclusive—transverse coherences could still produce ordering invisibly. Full adjudication requires numerics. This asymmetry is stated upfront, not buried.

### What we are offering

Our group participated in a 2016 trapped-ion experiment that observed thermalisation in an isolated quantum system. We retain full access to the raw time-series data—including runs not in the publication. The platform: a single spin coupled to 1–5 engineered phonon modes in the strong-coupling regime. Every parameter is documented. Theory and numerics can engage without guesswork.

The experimental data validate methodology and provide proxy-ordering constraints. But only one spin component was measured. Definitive adjudication—confirming or falsifying ordering in the full state space—requires numerical collaborators who can simulate the Hamiltonian with complete state output and extract the memory time from the discrete phonon spectrum.

### The ask

We seek collaborators in:

**Open-systems theory:** bounds on relaxation rates, memory-time extraction for few-mode baths, conditions for exponential vs non-exponential envelopes.

**Numerical spin-boson modelling:** hierarchical equations of motion, reaction-coordinate methods, matrix product states—whatever reaches this regime with full state output.

**Foundations:** positioning relative to eigenstate thermalisation, prethermalization, shortcuts to adiabaticity—and, where it connects, to the causal-geometric perspective we are developing across several parallel threads.

The goal is to make the question answerable, not to advocate for a particular answer. Null results are publishable. Critical responses are more valuable than enthusiastic ones.

**Contact:** ulrich.warring@physik.uni-freiburg.de\
**Full invitation document:** [GitHub](https://github.com/uwarring82/deep-spaces/blob/main/call/Toward%20Falsifiable%20Claims%20in%20Quantum%20Relaxation%20Ordering.md)
