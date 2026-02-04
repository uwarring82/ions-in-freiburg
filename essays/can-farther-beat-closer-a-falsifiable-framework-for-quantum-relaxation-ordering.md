---
description: A collaboration invitation
---

# Can "Farther" Beat "Closer"? A Falsifiable Framework for Quantum Relaxation Ordering

{% hint style="info" %}
**Authors:** Ulrich Warring\
**Last updated:** 2026-02-04\
**Status:** Community Narrative (Sail)\
**License:** CC BY 4.0
{% endhint %}

***

The quantum Mpemba effect has a problem: nobody agrees what it means.

At least four distinct definitions circulate in recent literature. Some invoke trace-distance crossings. Others focus on Lindbladian spectral gaps. Others still require quantum coherences. And the newest class—non-Markovian anomalies—identifies effects that vanish entirely in the Markovian limit. A system can satisfy one definition whilst violating another. Papers claim or refute "the quantum Mpemba effect" without specifying which definition applies, or whether their dynamical regime even permits comparison.

Worse: most claims lack falsification criteria. Without pre-registered answers to _what would count as disconfirmation_, the literature risks accumulating unfalsifiable assertions dressed in quantum language.

***

**The reframing**

We propose stripping the phenomenon to its operational core. Forget temperature—it's often undefined in finite engineered systems anyway. Focus instead on what experimentalists actually control: a Hamiltonian parameter.

When you turn a knob, two things change: (i) the system's long-time state shifts, so you may start _farther_ from the new target; (ii) the relaxation speed changes. The question becomes sharp:

> _Can the speedup overcompensate the extra distance, so that equilibration time decreases despite starting farther away?_

If yes, we call it **quench-controlled relaxation ordering**. No thermal baths required. No ambiguous "hot" and "cold." Just a falsifiable comparison: did the farther state arrive first?

***

**What makes this framework different**

Three features distinguish it from existing approaches:

1. **A primary test without derivatives.** We compare equilibration times directly for parameter pairs. No numerical differentiation, no noise amplification. An interpretive inequality decomposes _why_ ordering occurred, but the pairwise comparison is the adjudicator.
2. **An explicit validity boundary.** The bath memory time—the timescale over which environment correlations persist—separates non-Markovian transients from the regime where exponential fitting makes sense. If your analysis window overlaps with the memory time, the test is void. This prevents the most common failure mode: fitting Markovian models to non-Markovian data.
3. **Asymmetric adjudication logic.** Our prototype platform measured only one spin component. That's a lower bound on the full state-space distance. Satisfaction confirms ordering _in the measured sector_. Failure is _inconclusive_—transverse coherences could still produce ordering invisibly. Full adjudication requires numerics. This asymmetry is stated upfront, not buried.

***

**What we're offering**

I participated in a 2016 trapped-ion experiment that observed thermalisation in an isolated quantum system. I retain full access to the raw time-series data—including runs not in the publication. The platform: a single spin coupled to 1–5 engineered phonon modes in the strong-coupling regime. Every parameter is documented. Theory and numerics can engage without guesswork.

The experimental data validate methodology and provide proxy-ordering constraints. But only one spin component was measured. Definitive adjudication—confirming or falsifying ordering in the full state space—requires numerical collaborators who can simulate the Hamiltonian with complete state output and extract the memory time from the discrete phonon spectrum.

***

**The ask**

We seek collaborators in:

* **Open-systems theory:** bounds on relaxation rates, memory-time extraction for few-mode baths, conditions for exponential vs non-exponential envelopes.
* **Numerical spin-boson modelling:** hierarchical equations of motion, reaction-coordinate methods, matrix product states—whatever reaches this regime with full state output.
* **Foundations:** positioning relative to eigenstate thermalisation, prethermalization, shortcuts to adiabaticity.

The goal is to make the question _answerable_, not to advocate for a particular answer. Null results are publishable. Critical responses are more valuable than enthusiastic ones.

Full framework document available online: [https://github.com/uwarring82/deep-spaces/blob/main/call/Toward%20Falsifiable%20Claims%20in%20Quantum%20Relaxation%20Ordering.md](https://github.com/uwarring82/deep-spaces/blob/main/call/Toward%20Falsifiable%20Claims%20in%20Quantum%20Relaxation%20Ordering.md)

***

**Contact:** ulrich.warring@physik.uni-freiburg.de
