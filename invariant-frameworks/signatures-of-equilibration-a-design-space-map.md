---
description: Mapping Mpemba-like effects in aqueous solutions
---

# Signatures of Equilibration – A Design-Space Map

{% hint style="info" %}
**Version:** 0.4\
**Stewardship:** Ulrich Warring, University of Freiburg\
**Status:** Teaching and Research framework, not peer-reviewed. Use for experimental design and discussion.
{% endhint %}

***

### What This Document Is

This is a structured guide for exploring an Mpemba–like effect—the counterintuitive observation that hot water can sometimes freeze faster than cold water. Rather than claiming to explain the effect, this document maps out:

* What you can control in an experiment (parameters)
* What mechanisms might dominate under different conditions
* What claims are testable (falsifiable boundaries)
* What remains unknown (open questions)

The framework helps you design experiments that can distinguish between competing explanations.

***

### Background Physics

#### Why might hot water freeze faster?

At first glance, this seems impossible: hot water has more thermal energy to lose. But "freezing" involves two distinct processes:

1. **Cooling** — removing heat until the water approaches 0 °C
2. **Nucleation** — forming the first stable ice crystal

Water often _supercools_ below 0 °C before freezing begins. The nucleation step is probabilistic: it depends on impurities, container surfaces, and random molecular fluctuations.

**Key insight:** If preheating changes the nucleation landscape (e.g., by modifying container surfaces or redistributing impurities), it might reduce supercooling and trigger earlier freezing—even though cooling takes longer.

#### Classical nucleation theory (the essential idea)

Ice doesn't form spontaneously in pure water at 0 °C. A small ice cluster must overcome an energy barrier to grow. This barrier depends on:

* **Temperature:** Deeper supercooling lowers the barrier
* **Surface properties:** Rough or chemically active surfaces provide "nucleation sites" where ice can form more easily
* **Impurities:** Particles in the water can seed ice formation

The nucleation rate (how quickly ice appears) increases dramatically with supercooling depth and nucleation site density.

***

### Established Physics (External Constraints)

These are well-tested principles we take as given:

| Principle                   | What it tells us                                                                                |
| --------------------------- | ----------------------------------------------------------------------------------------------- |
| Classical nucleation theory | Ice formation requires overcoming an energy barrier; surfaces and impurities lower this barrier |
| Newton's law of cooling     | Cooling rate is proportional to temperature difference with surroundings                        |
| Thermodynamics              | Energy is conserved; phase changes require latent heat removal                                  |
| Stochastic nucleation       | Freezing time = (deterministic cooling) + (random nucleation delay)                             |

We don't re-derive these; we use them as constraints on any proposed explanation.

***

### 1. What You Can Control (Experimental Parameters)

| Parameter                 | What it means                                                         | How to measure/set it                                                                    | Symbol |
| ------------------------- | --------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- | ------ |
| **Bulk impurities**       | Dissolved substances, particles, or gas bubbles in the water          | Conductivity meter (μS/cm); particle counter; use ultrapure or deliberately seeded water | _P\_b_ |
| **Wall nucleation state** | How "rough" or chemically active the container surface is             | Surface roughness Ra (μm) via profilometer; contact angle θ (°) via goniometer           | _P\_w_ |
| **Container material**    | Glass type, plastic, metal—affects surface chemistry and ion leaching | Categorical choice: borosilicate glass (best), soda-lime glass, HDPE, PTFE               | _M_    |
| **Thermal history**       | Has the container been heated before? How many times?                 | Protocol: specify number of heat-cool cycles, maximum temperature, hold time             | _H_    |
| **Cooling rate**          | How fast heat leaves the sample                                       | Bath temperature; stirring speed; sample geometry                                        | _κ_    |
| **Sample volume**         | Larger volumes have more thermal inertia and internal gradients       | Direct measurement (mL); recommend 5–20 mL for statistical studies                       | _V_    |
| **Initial temperature**   | How hot is the "hot" sample?                                          | Temperature difference from cooling bath: ΔT₀ (K)                                        | _ΔT₀_  |
| **System openness**       | Can water evaporate?                                                  | Sealed (lid) vs. open; if open, weigh before and after                                   | _σ_    |
| **Freeze criterion**      | What counts as "frozen"?                                              | See below—this matters enormously                                                        | _F_    |

#### The freeze criterion problem

Many contradictory results in the literature come from different definitions of "freezing":

| Criterion               | What you measure         | Best method                                                |
| ----------------------- | ------------------------ | ---------------------------------------------------------- |
| **Nucleation onset**    | First ice crystal forms  | Temperature spike (latent heat release); video observation |
| **Surface ice**         | Visible ice layer on top | Visual/camera                                              |
| **Full solidification** | Entire sample is solid   | Temperature plateau ends; physical probing                 |

**Important:** The nucleation-redistribution hypothesis (that preheating changes where ice starts forming) should show up most clearly at _F_ = nucleation onset. It may not persist to _F_ = full solidification, where total heat removal dominates.

***

### 2. Which Mechanism Dominates Where?

Different experimental conditions favour different mechanisms. This table shows likely primary drivers—not certainties.

| Experimental regime                                                 | Likely primary mechanism    | Likely secondary               | What you'd observe                                                |
| ------------------------------------------------------------------- | --------------------------- | ------------------------------ | ----------------------------------------------------------------- |
| Very pure water, smooth new container, sealed                       | Random convection patterns  | Stochastic supercooling        | High variability between trials; no consistent Mpemba-like effect |
| Controlled impurities, roughened container, thermal cycling, sealed | **Wall nucleation changes** | Reduced supercooling           | Earlier nucleation in preheated samples; lower variance           |
| Open container, large ΔT₀                                           | Evaporative mass loss       | Enhanced convection            | Shorter total freeze time, but confounded—you've lost water mass  |
| Large volume, slow cooling                                          | Convection currents         | Internal temperature gradients | Results depend on container shape; variable                       |
| **Small volume, controlled nucleation, sealed**                     | **Nucleation timing**       | Minimal confounders            | **Cleanest test of nucleation hypothesis**                        |

#### How regimes connect (transition arrows)

* Increasing volume (_V_ ↑) while decreasing cooling rate (_κ_ ↓) → shifts from nucleation-dominated to convection-dominated
* Opening the system (_σ_: sealed → open) → introduces evaporation; mass loss confounds all other effects
* Smoothing container walls (_P\_w_ ↓) → reduces nucleation site density; increases supercooling depth and variance
* Switching from borosilicate to soda-lime glass (_M_ change) → may introduce ion leaching into _P\_b_

***

### 3. Testable Claims (Falsifiable Boundaries)

A good scientific framework makes claims that could be proven wrong. Here are four:

#### Boundary 1: Nucleation site threshold

**Claim:** If the container is very smooth (Ra < 0.05 μm) and the water is ultrapure, preheating won't produce a Mpemba-like effect at nucleation onset.

**Test:** Compare supercooling distributions in polished borosilicate with different thermal histories.

**Current status:** Supported in some careful experiments; results vary with protocol.

***

#### Boundary 2: Thermal history matters independently

**Claim:** The effect of preheating comes from changing the container surface (_P\_w_), not just from starting hotter. Two samples at the same temperature but with different thermal histories should behave differently.

**Test:** Heat one sample slowly to 80 °C then cool to 40 °C; rapidly heat another directly to 40 °C. Compare their supercooling distributions.

**How might thermal history change the surface?**

* Gas bubbles desorbing from surface cracks (timescale: minutes)
* Chemical changes to surface oxides (timescale: minutes to hours)
* Micro-crack formation or healing (timescale: hours)

**Current status:** Plausible but under-tested. Timescales are estimates.

**Uncertainty note:** If the timescales are wrong, the test protocols may not capture the relevant changes. Future work should systematically vary heating duration.

***

#### Boundary 3: Evaporation can be ruled out

**Claim:** In sealed containers with controlled purity and surface state, evaporation cannot explain observed nucleation-timing differences.

**Test:** Seal containers; weigh before and after; verify mass loss < 0.1%.

**Current status:** Established for sealed systems. Open systems remain confounded.

***

#### Boundary 4: Container material matters

**Claim:** Changing container material shifts which mechanism dominates, mainly through effects on surface nucleation (_P\_w_) and ion leaching (_P\_b_).

**Test:** Run identical protocols with borosilicate, soda-lime glass, and PTFE containers; compare supercooling statistics.

**Current status:** Expected from surface chemistry; systematic Mpemba-like studies limited.

***

### 4. Recommended Experimental Protocol

To test whether preheating affects nucleation timing:

| Parameter              | Recommended setting                                                                    | Why                                                        |
| ---------------------- | -------------------------------------------------------------------------------------- | ---------------------------------------------------------- |
| Water purity (_P\_b_)  | Ultrapure (< 1 μS/cm) OR deliberately seeded with known nucleant (e.g., silver iodide) | Separates bulk from surface effects                        |
| Surface state (_P\_w_) | Measure Ra and θ; compare polished vs. roughened containers                            | This is your main variable                                 |
| Container (_M_)        | Borosilicate glass; keep constant within experiment                                    | Minimises ion leaching; stable surface                     |
| Thermal history (_H_)  | Define protocol: e.g., "heat to 80 °C, hold 5 min, cool to start temperature"          | Enables history-dependence test                            |
| Cooling rate (_κ_)     | Stirred water bath at −10 °C                                                           | Fast enough to observe nucleation before deep supercooling |
| Volume (_V_)           | 5–20 mL; at least 30 replicates per condition                                          | Statistical power; manageable gradients                    |
| System (_σ_)           | Sealed; verify Δm < 0.1%                                                               | Eliminates evaporation                                     |
| Freeze criterion (_F_) | Nucleation onset (temperature spike)                                                   | Direct test of nucleation hypothesis                       |

**What to measure:**

* Primary: Temperature at which nucleation occurs (_T\_nucleation_) for each trial
* Secondary: Variance across trials; correlation with surface roughness

***

### 5. What We Don't Know Yet

1. **Can we predict nucleation from surface measurements?** If we measure Ra and θ, can we calculate the expected supercooling distribution? What's the functional relationship?
2. **How fast does thermal history act?** If you heat a container for 1 minute vs. 10 minutes, does _P\_w_ change differently? At what point do returns diminish?
3. **Does material choice matter beyond surface roughness?** Does glass chemistry affect nucleation independently of roughness?
4. **When does nucleation advantage persist to full freezing?** Under what conditions does faster nucleation translate to faster complete solidification?
5. **Can we model this quantitatively?** Stochastic thermodynamics provides mathematical frameworks for random processes. Can these predict Mpemba-like statistics from measured parameters?

***

### 6. Key References

For further reading, organised by topic:

**Nucleation theory (foundations):**

* Turnbull (1950) "Kinetics of heterogeneous nucleation" — the classic paper
* Kelton & Greer (2010) _Nucleation in Condensed Matter_ — comprehensive textbook

**Mpemba-like effect experiments:**

* Burridge & Linden (2016) — careful study questioning reproducibility
* Burridge & Hallstadius (2020) — protocol standardisation; addresses endpoint confusion

**Theoretical approaches:**

* Lu & Raz (2017) — stochastic thermodynamics of Mpemba-like effects
* Kumar & Bechhoefer (2020) — experimental Mpemba effect in colloidal system (not water)

**Molecular simulations:**

* Huang et al. (2015) — MD simulations suggesting structural changes in preheated water

***

### Document History

| Version | Date       | Changes                                                                                                |
| ------- | ---------- | ------------------------------------------------------------------------------------------------------ |
| 0.1     | 2026-01-23 | Initial draft                                                                                          |
| 0.2     | 2026-01-23 | Added freeze criterion; split purity parameters                                                        |
| 0.3     | 2026-01-23 | Operationalised surface measurements; added material parameter; references                             |
| 0.4     | 2026-01-23 | Simplified language; added background physics; regime transition arrows; uncertainty propagation notes |

***

### How to Use This Document

**For lab work:** Use §4 (Recommended Protocol) as your starting point. Vary one parameter at a time.

**For understanding the literature:** Use §2 (Regime Map) to classify which conditions a paper used, then assess whether their conclusions apply to other regimes.

**For discussion:** Use §5 (Open Questions) to identify genuine unknowns vs. questions that careful experiments could resolve.

**For writing reports:** Cite specific boundaries (§3) when making claims; acknowledge which regime your experiment falls into.

***

_This framework follows Open-Science Harbour conventions: established physics is referenced but not re-derived; claims are testable; uncertainties are flagged; versions are tracked._
