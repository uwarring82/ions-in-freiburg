# L–ORDINANS-L3-TMP — Engineered World Submission Template

{% hint style="info" %}
**Author:** U. Warring\
**Affiliation:** Institute of Physics, University of Freiburg\
**Version:** 0.1.1\
**Last updated:** 2025-12-19\
**License:** CC BY 4.0\
\
**Disclaimer** — _This document defines a boundary-condition design framework. Its authority derives from transparency, not finality._
{% endhint %}

***

### Introduction

#### What This Template Does

This template enforces **system–environment separation** for all Layer-3 "Engineered World" submissions in the Ordinans framework. It ensures that claimed emergent phenomena—irreversibility, scaling behaviour, decoherence, measurement-induced effects—are:

* **Falsifiable:** Testable against a defined Null Environment
* **Reproducible:** With explicit environment specifications and algorithmic standards
* **Properly attributed:** To engineered environments, not hidden system assumptions

#### The Core Principle

> **If the Null Environment reproduces the effect, the physics is not in the system.**

This is the **Margin Principle**, invariant across all template versions. It prevents claims of "emergent complexity" that actually arise from uncontrolled or poorly documented experimental conditions.

#### Why It Exists

In quantum simulation and open-system research, it is easy to attribute complexity to "the system" when it actually originates from:

* Uncontrolled environmental couplings
* Measurement back-action
* Finite-size recurrence effects
* Undocumented algorithmic choices in numerical simulations

This template forces authors to make these influences **explicit, documented, and testable**.

#### Who Uses This Template

Anyone documenting:

* Quantum simulations with engineered baths or noise sources
* Open-system experiments (trapped ions, cavity QED, circuit QED)
* Measurement-induced phenomena (quantum trajectories, adaptive protocols)
* Environment-contingent universality classes

...where the **Spin⊗Mode Ordinans** ($$\mathcal{H}{\text{spin}} \otimes \mathcal{H}{\text{mode}}$$) serves as the invariant system core.

#### Relationship to Other Frameworks

**This template is a Map of Coastlines** (invariant procedural framework), not an Implementation Interface:

* **Maps of Coastlines** (Invariant Frameworks) — Define boundaries, constraints, and falsification criteria. Stable, citation-bearing, slow-changing.
* **Implementation Interfaces** — Operational protocols for specific tasks (e.g., Causal Steering Protocols).
* **Sails and Repair Kits** (Essays) — Interpretive, motivational perspectives. Non-normative.

**Related pages:**

* What Can Make a Complex System an Ordinans? — Conceptual foundation for system–environment separation
* Causal Clock Unification Framework — Example of an invariant framework in timing metrology

***

### Methodological Foundation

This template enforces the **system–environment separation principle** central to the Ordinans perspective: all irreversible, stochastic, or scaling behaviour arises from explicitly coupled environments, not from the isolated system itself.

**Methodological precedents:**

* **Leggett et al. (1987)**: Dynamics of the dissipative two-state system — established environment-coupling formalism for open quantum systems (_Rev. Mod. Phys._ 59, 1–85)
* **Breuer & Petruccione (2002)**: _The Theory of Open Quantum Systems_ — systematic framework for Kraus operators and environmental certification
* **Lock-Key Rule (Warring, 2025)**: Architectural separation between invariant structure (template) and interpretive context (World instantiations)

***

### Template Structure

The template consists of 8 mandatory sections plus change log:

<table><thead><tr><th width="111.16796875">Section</th><th>Purpose</th></tr></thead><tbody><tr><td>§0</td><td>Identity &#x26; Genealogy</td></tr><tr><td>§1</td><td>World Assumption (hypothesis)</td></tr><tr><td>§2</td><td>Environmental Construction</td></tr><tr><td>§3</td><td>Environment Certification</td></tr><tr><td>§4</td><td>Null Environment (falsification suite)</td></tr><tr><td>§5</td><td>Stability Boundary</td></tr><tr><td>§6</td><td>Emergent Laws</td></tr><tr><td>§7</td><td>Interpretation Boundary</td></tr><tr><td>§8</td><td>Version &#x26; Provenance (including waiver/versioning policies)</td></tr></tbody></table>

***

### §0. Identity & Genealogy

**World ID:** SW-\[Number]\
**Title:** \[Concise phenomenological description]

**Parent Interface (Layer 2):**\
→ §\[X] \[Interface name]

**Ordinans Core (Layer 1):**

$$
\mathcal{H}_{\text{sys}} = \mathcal{H}_{\text{spin}} \otimes \mathcal{H}_{\text{mode}}
$$

**Invariant Statement (Required):**\
The Ordinans Core is referenced but not modified. All irreversible, stochastic, or scaling behaviour arises exclusively from the environment defined below.

***

### §1. World Assumption

**Hypothesis:**\
Describe in one paragraph what kind of environment is being simulated or engineered.

**Examples:**

* "A clock environment with infinite memory"
* "A continuously monitored environment with finite information extraction rate"
* "A structured bosonic bath with a sub-Ohmic spectral density"

**Scope Declaration:**\
The laws described in this World apply to the coupled system + environment, not to the isolated Ordinans system.

***

### §2. Environmental Construction

#### §2.1 Environment Class

☐ Classical stochastic environment\
☐ Quantum bath (unmonitored)\
☐ Measurement channel (monitored)\
☐ Feedback / controller environment\
☐ Hybrid (specify)

#### §2.2 Coupling Axiom (Mandatory)

All couplings must be specified in the form:

$$
\mathcal{H}_{\text{int}} = \sum_k S_k \otimes E_k(t)
$$

* **System operator(s)** $$S_k$$**:**\
  \[e.g. $$\sigma_x$$, $$a+a^\dagger$$, parity, etc.]
* **Environment operator(s)** $$E_k(t)$$**:**\
  \[stochastic process, bath operator, measurement record, etc.]

{% hint style="warning" %}
**Guardian Rule — No Ghost Environments:**\
Any effect attributed to "noise", "drift", or "imperfections" must be represented here as an explicit $$E_k(t)$$.
{% endhint %}

#### §2.3 Environment Generator (Reproducibility)

**Generator Type:**\
☐ Probability distribution\
☐ Noise spectrum\
☐ Kraus map / POVM\
☐ Algorithmic controller

**Specification (required):**

\[Provide the explicit algorithm, distribution, or update rule. Vague descriptions are not acceptable.]

{% hint style="info" %}
**v1.1 Enhancement — Algorithmic Controller Standards:**

If "Algorithmic controller" is selected, the following fields are **mandatory**:

* **Version:** \[Software/algorithm version identifier]
* **Seed policy:** \[Fixed seed / randomized / time-based / hardware RNG]
* **Determinism:**\
  ☐ **Yes** — Algorithm produces identical output for identical input\
  ☐ **No** — Algorithm contains stochastic elements (specify layer: \[e.g., Monte Carlo sampling, thermal noise injection, measurement back-action])

**Rationale:** Algorithmic environments must be reproducible by independent groups. Without version control and seed documentation, certification becomes impossible. _(Precedent: Open Science Framework pre-registration protocols; Simmons et al., Psych. Sci. 2011)_
{% endhint %}

***

### §3. Environment Certification (Required)

Before claiming emergent physics, the environment must be validated.

**Certification checklist:**

* ☐ Target statistics measured (e.g. $$\psi_{\text{exp}}(t)$$ vs. $$\psi(t)$$)
* ☐ Agreement verified over ≥ 2 decades (if scale-free) **\[see note below]**
* ☐ Renewal / independence test passed (if applicable)
* ☐ Environment parameters logged and archived

{% hint style="info" %}
**v1.1 Clarification — Scale-Free Status:**

_Scale-free status is itself a testable hypothesis, not an input assumption._ Before invoking the "≥ 2 decades" criterion, provide independent justification that the phenomenon exhibits power-law or scale-invariant behaviour.

**Acceptable justifications include:**

* Collapse of data onto a master curve under rescaling
* Log-log linearity with $$R^2 > 0.95$$ over the claimed range
* Dimensional analysis predicting scale invariance
* Explicit removal of characteristic scales from the coupling operators

**Failure mode prevented:** Circular reasoning where "we assume scale-free" → "2 decades verified" → "therefore scale-free". _(Precedent: Bak et al., Phys. Rev. Lett. 1987 — self-organized criticality requires independent scaling evidence)_
{% endhint %}

**Failure Rule:**\
If the environment cannot be independently certified, all emergent claims are invalid.

***

### §4. Null Environment (Falsification Suite)

**Null Environment Definition:**\
Specify the control environment that should produce trivial dynamics.

**Examples:**

* Gaussian timing jitter with finite variance
* White phase noise
* Measurement strength → 0

{% hint style="danger" %}
**Null Condition:**

_If the Null Environment produces the same phenomenology as the Engineered Environment, the World is rejected._

**Methodological precedent:** Falsification requires a testable alternative hypothesis (Popper, _Logic of Scientific Discovery_, 1959). The Null Environment serves as the $$H_0$$ hypothesis against which the Engineered World is tested.
{% endhint %}

***

### §5. Stability Boundary

Define the validity window:

$$
t \ll \tau_{\text{stab}}
$$

with:

$$
\tau_{\text{stab}} = \min(\tau_{\text{heating}},\;\tau_{\text{phase drift}},\;\tau_{\text{recurrence}})
$$

**Cross-references (Layer 2):**

* ☐ Phase stability baseline
* ☐ Heating / loss rates
* ☐ Finite-size recurrence

{% hint style="warning" %}
**Guardian Rule:**\
Data taken outside this window may not be interpreted as physical scaling.

**Rationale:** Finite-size quantum systems exhibit Poincaré recurrence on timescale $$\tau_{\text{rec}} \sim \exp(S)$$ where $$S$$ is entropy. Claims of "irreversibility" or "thermalization" valid only for $$t \ll \tau_{\text{rec}}$$. _(Precedent: Bocchieri & Loinger, Phys. Rev. 1957)_
{% endhint %}

***

### §6. Emergent Laws (World-Specific)

**Phenomenology (equations required):**

\[Insert scaling laws, distributions, or asymptotics]

**Guardian Statement (Mandatory):**\
These laws describe the Engineered World, not the isolated Ordinans system. They are contingent on the specified environment and disappear when the coupling is removed.

***

### §7. Interpretation Boundary

**This Engineered World:**

* ☐ Does not define a new Hamiltonian
* ☐ Does not extend the Ordinans Core
* ☐ Does not constitute a control primitive

{% hint style="success" %}
**v1.1 Enhancement — Positive Affirmation:**

**This Engineered World&#x20;**_**does**_**&#x20;establish:**\
A falsifiable, reproducible demonstration of environment-contingent phenomenology within the stated validity window (§5).

**Its value lies in:**

* Falsifiable emergence
* Stress-testing system–environment separation
* Classifying environment-induced universality

**Rationale:** Negative constraints alone risk misreading as "this proves nothing". Explicit positive statement clarifies what is scientifically established without overclaiming. _(Precedent: Meehl, Psych. Rep. 1967 — scientific theories must state both what they predict and what they forbid)_
{% endhint %}

***

### §8. Version & Provenance

**World Version:** v\[ ]\
**Template Version:** ORDINANS-L3-TMP v1.1\
**Status:** ☐ Exploratory ☐ Certified ☐ Deprecated

**Council Review:** ☐ Yes ☐ Pending\
**Notes:** \[optional]

#### §8.1 Waiver Policy (v1.1)

{% hint style="info" %}
**v1.1 Enhancement — Explicit Waiver Criteria:**

Waivers of specific template sections are permitted under the following conditions:

**(a) Written justification** citing which section is inapplicable and why\
&#xNAN;**(b) Guardian review** confirming the waiver does not compromise falsifiability\
&#xNAN;**(c) Archival in Divergent log** with expiry date (≤ 2 years)

**Critical constraint:** Waivers do not modify this template. They acknowledge context-specific inapplicability, not template revision.

**Rationale:** Prevents erosion of discipline through accumulation of informal exceptions. Waiver = documented exception, not precedent. _(Precedent: Lock-Key Rule — keys (waivers) never modify locks (template structure) without re-ratification)_
{% endhint %}

#### §8.2 Template Versioning Policy (v1.1)

{% hint style="info" %}
**v1.1 Enhancement — Backwards Compatibility:**

Worlds certified under earlier template versions retain validity. Re-certification against updated templates is voluntary unless structural incompatibility is declared by Council.

**Version upgrade triggers:**

* **Patch (X.Y.Z → X.Y.Z+1):** Editorial clarifications, no re-certification required
* **Minor (X.Y → X.Y+1):** New optional fields, re-certification recommended
* **Major (X → X+1):** Breaking changes, re-certification required within 1 year

**Structural incompatibility:** Declared when a fundamental assumption of the earlier template is invalidated (e.g., discovery that Ordinans Core is non-unitary, violation of system–environment separation).

**Rationale:** Protects scientific investment in certified Worlds while allowing template evolution. Analogous to semantic versioning in software (Preston-Werner, _SemVer 2.0.0_, 2013).
{% endhint %}

***

### Margin Principle (Non-Negotiable)

{% hint style="danger" %}
**If the Null Environment reproduces the effect, the physics is not in the system.**

This principle is invariant across all template versions.
{% endhint %}

***

### Usage Notes

#### For Authors

* Complete all mandatory sections before submission
* Guardian review triggered automatically for waivers
* Certification status updated in central registry

#### For Reviewers

* Verify Null Environment is genuinely distinct from Engineered Environment
* Check coupling operators $$S_k \otimes E_k(t)$$ are explicit, not schematic
* Confirm stability boundary $$\tau_{\text{stab}}$$ is justified by cross-references

#### For Replicators

* Algorithmic controllers must specify version, seed policy, determinism
* Environment parameters archived in machine-readable format (JSON/HDF5)
* Null Environment data available alongside Engineered World data

***

### References

#### Methodological Foundations

* Leggett, A. J., Chakravarty, S., Dorsey, A. T., Fisher, M. P. A., Garg, A., & Zwerger, W. (1987). Dynamics of the dissipative two-state system. _Reviews of Modern Physics_, 59(1), 1–85.
* Breuer, H.-P., & Petruccione, F. (2002). _The Theory of Open Quantum Systems_. Oxford University Press.
* Popper, K. R. (1959). _The Logic of Scientific Discovery_. Hutchinson.

#### Precedents for Template Design

* Bak, P., Tang, C., & Wiesenfeld, K. (1987). Self-organized criticality. _Physical Review Letters_, 59(4), 381–384.
* Bocchieri, P., & Loinger, A. (1957). Quantum Recurrence Theorem. _Physical Review_, 107(2), 337–338.
* Meehl, P. E. (1967). Theory-testing in psychology and physics: A methodological paradox. _Philosophy of Science_, 34(2), 103–115.
* Simmons, J. P., Nelson, L. D., & Simonsohn, U. (2011). False-positive psychology. _Psychological Science_, 22(11), 1359–1366.

#### Open Science Infrastructure

* Preston-Werner, T. (2013). Semantic Versioning 2.0.0. Retrieved from [https://semver.org](https://semver.org)
* Warring, U. (2025). The Lock-Key Rule of Open Science. _Open Science Harbour Framework_.

***

### Change Log (v1.0 → v1.1)

| Section    | Enhancement                                                                                |
| ---------- | ------------------------------------------------------------------------------------------ |
| §2.3       | Algorithmic Reproducibility: Added mandatory fields (Version, Seed policy, Determinism)    |
| §3         | Scale-Free Clarification: Independent justification required before 2-decade criterion     |
| §7         | Positive Affirmation: Explicit statement of what Engineered Worlds establish               |
| §8.1       | Waiver Policy: Structured criteria (a-b-c) replacing informal language                     |
| §8.2       | Versioning Policy: Backwards compatibility rules and structural incompatibility definition |
| References | Expanded to include methodological precedents and versioning standards                     |

***

**Status:** This template is the canonical submission format for all Layer-3 entries.

Any Horizons content not conforming to ORDINANS-L3-TMP v1.1 is out of scope unless explicitly waived under §8.1.

***

### Version History

**v0.1.1 (2025-12-19)** — Guardian-cleared revision incorporating:

* §3: Scale-free hypothesis clarification
* §2.3: Algorithmic reproducibility standards
* §8: Explicit waiver criteria and template versioning policy
* §7: Positive affirmation of established claims

**v0.1.0 (2025-12-18)** — Initial template structure (Internal)
