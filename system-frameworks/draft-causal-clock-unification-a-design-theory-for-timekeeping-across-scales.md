---
description: Timekeeping as Causal Geometry
---

# \[Draft] Causal Clock Unification: A Design Theory for Timekeeping Across Scales

{% hint style="info" %}
**Author:** U. Warring\
**Affiliation:** Institute of Physics, University of Freiburg\
**Version:** 0.0.2\
**Last updated:** 2025-12-12\
**License:** CC BY-SA 4.0\
\
**Disclaimer** — _This document reflects an ongoing effort to clarify how causality constrains timekeeping architectures. Its authority derives from transparency, not finality._<br>
{% endhint %}

### Abstract

Precise timekeeping spans more than fifteen orders of magnitude in period, from atomic optical clocks to planetary rotation and pulsar timing arrays. These systems are typically classified by oscillator mechanism, physical size, or measurement technique, resulting in fragmented treatments across metrology, relativity, and astrophysics.<br>

Here we introduce a boundary-condition framework that unifies clocks by the _causal geometry of phase comparison_, rather than by oscillator physics. Any physically realizable clock satisfies:

<p align="center"><span class="math">L_{\text{comparison}} \le cT</span>,</p>

where $$L_{\text{comparison}}$$ is the largest spatial separation over which phase must be actively compared to define a tick on an averaging time $$\tau$$, and $$T$$ is the corresponding tick period. This inequality is a fundamental design constraint, not a law of nature; its physical content lies in the noise penalties incurred as different clock architectures approach the boundary.

To remove longstanding ambiguities, we explicitly distinguish three non-interchangeable length scales: the oscillation source scale ($$L_{\text{source}}$$), the interrogation or stabilization scale ($$L_{\text{apparatus}}$$), and the comparison baseline ($$L_{\text{comparison}}$$). Only the latter enters the causal constraint. Building on this separation, we define a dimensionless causal efficiency parameter:

<p align="center"><span class="math">\eta(\tau) = \frac{L_{\text{comparison}}(\tau)}{c\,\tau}</span>,</p>

where $$\tau$$ is the averaging time over which phase comparison is active.

This framework yields a falsifiable design principle: for each clock architecture, stability improves with increasing $$\eta$$ up to an architecture-specific optimum $$\eta_{\text{opt}}$$, beyond which propagation noise, model error, or spatial decoherence dominate. Deviations from predicted $$\eta_{\text{opt}}$$ provide a direct empirical test. The framework makes no claims about Planck-scale clocks; the Planck point appears only as a dimensional endpoint of the causal boundary. Instead, the contribution is a unifying design theory that connects laboratory clocks, global navigation systems, very long baseline interferometry, and pulsar timing through the geometry of phase comparison.

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
