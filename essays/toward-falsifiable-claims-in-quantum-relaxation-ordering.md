---
description: An Invitation Draft to Collaborate
---

# Toward Falsifiable Claims in Quantum Relaxation Ordering

{% hint style="info" %}
Ulrich Warring\
Institute of Physics, University of Freiburg\
\
Circulated for comment — January 2026
{% endhint %}

***

### Abstract

The phrase "quantum Mpemba effect" appears increasingly in the literature on quantum thermalization \[5–10], yet the field lacks consensus on operational definitions, falsification criteria, and the relationship between proposed mechanisms. We present a framework that reformulates such claims as falsifiable inequalities governing the competition between geometric distance and relaxation rate under Hamiltonian parameter variation. The framework deliberately abandons temperature-based parameterisation—a feature, not a limitation, for finite engineered systems where temperature is not operationally well-defined.

As a prototype demonstration, the framework is applied to the strong-coupling spin-boson platform of Ref. \[1], for which the author retains full access to raw experimental time-series data. A constraint: only $$\langle\sigma_z(t)\rangle$$ was measured, yielding a lower bound on trace distance. This creates asymmetric falsification logic: satisfaction of the inequality using $$\sigma_z$$-only data confirms the effect (sufficient condition); failure is inconclusive and cannot falsify without full Bloch-sphere tomography. Definitive adjudication therefore requires numerical simulation—numerics are not auxiliary but decisive. We invite collaboration from experts in open-system thermalization theory and numerical spin-boson modelling to complete the triangulation.

***

### 1. The Problem: Semantic Drift Without Falsification

The classical Mpemba effect—hot water freezing faster than cold under certain conditions—remains contested \[2–4]. Its quantum descendants inherit this contestation whilst adding new ambiguity.

A survey of recent literature reveals at least three distinct operational definitions:

**Definition 1 (Distance crossing):** A higher-energy initial state's trace distance to equilibrium crosses below that of a lower-energy state at finite time and remains below thereafter \[5, 6].

**Definition 2 (Spectral gap anomaly):** The dominant decay mode of the Lindbladian has a larger gap for higher-energy initial states \[6, 9].

**Definition 3 (Coherence shortcut):** Initial quantum coherences accelerate approach to a diagonal ensemble faster than incoherent states of the same energy \[7].

These definitions are not equivalent. A system may satisfy one whilst violating another. Yet papers routinely claim or refute "the quantum Mpemba effect" without specifying which definition is operative.

More problematic: many claims lack explicit falsification criteria. Without pre-registered answers to what would constitute disconfirmation, the literature risks accumulating unfalsifiable assertions.

***

### 2. A Reframing: Quench-Controlled Relaxation Ordering

#### 2.1 Motivation

In finite quantum systems with engineered environments, "temperature" is often undefined or misleading. We focus instead on what experimentalists control: Hamiltonian parameters.

Let $$b$$ denote a control parameter (detuning, bias field, coupling strength). Varying $$b$$ generically changes:

1. **The target state:** The system's long-time reduced state $$\rho_{S,\mathrm{target}}(b)$$ shifts in Hilbert space.
2. **The relaxation dynamics:** The rate $$R(b)$$ at which the system approaches that target changes.

The question becomes: _Can increasing_ $$b$$ _increase the initial distance to target whilst simultaneously increasing the relaxation rate sufficiently that equilibration time decreases?_

#### 2.2 The Core Question (Plain Statement)

We change a control knob $$b$$. Two things happen: (i) the system's long-time reduced state shifts, so the starting point may be farther from this new target; (ii) the relaxation speed may change. We ask whether the speedup can overcompensate the extra distance, so that the time to reach a fixed closeness threshold becomes _shorter_ despite starting _farther away_. This is the only sense of "Mpemba-like" used here.

#### 2.3 Definitions (Full Trace Distance)

Let $$\rho_S(t;b)$$ denote the reduced state of the subsystem at time $$t$$ under parameter value $$b$$.

**Definition (Target state, Option A):** For a pre-revival plateau window $$[t_1, t_2]$$,&#x20;

<p align="center"><span class="math">\rho_{S,\mathrm{target}}(b) = \frac{1}{t_2 - t_1}\int_{t_1}^{t_2}\rho_S(t;b),\mathrm{d}t.</span></p>

This run-specific target is intentionally dynamics-dependent. In finite closed systems with no external bath, no operationally superior notion exists; ETH-based approaches \[11–14] similarly rely on long-time averages. Option A does _not_ invoke a canonical Gibbs state, and comparisons across different $$b$$ are comparisons of "time to reach one's own long-time reduced state," not "time to reach a shared equilibrium." This is a weaker but operationally cleaner claim.

**Definition (Trace distance):** For a qubit with Bloch vectors $$\vec{r}(t)$$ and $$\vec{r}{\mathrm{target}}$$_,_&#x20;

<p align="center"><span class="math">D(t;b) = \tfrac{1}{2}\lVert\rho_S(t;b) - \rho{S,\mathrm{target}}(b)\rVert_1 = \tfrac{1}{2}\lVert\vec{r}(t;b) - \vec{r}_{\mathrm{target}}(b)\rVert_2,</span></p>

with initial distance $$D_0(b) \equiv D(0;b)$$. The second equality holds for qubits only.

**Definition (Relaxation rate):** Under an exponential-envelope approximation on the pre-revival transient, $$D_{\mathrm{env}}(t;b) \approx D_0(b),e^{-R(b)t},$$ where $$R(b) = \tau(b)^{-1}$$ is extracted by fitting.

**Definition (Equilibration time):** $$t_\varepsilon(b)$$ is the first time $$D_{\mathrm{env}}(t;b) < \varepsilon$$ and remains below for a dwell time $$\Delta t_{\mathrm{dwell}}$$. Under the envelope model: $$t_\varepsilon(b) = \frac{1}{R(b)}\ln\left(\frac{D_0(b)}{\varepsilon}\right).$$

#### 2.4 Experimental Surrogate: σ\_z-Only Measurement

When only $$\langle\sigma_z(t)\rangle$$ is measured (as in Ref. \[1]), we define:

**Definition (σ\_z proxy):** $$d_z(t;b) = |\langle\sigma_z(t)\rangle - \langle\sigma_z\rangle_{\mathrm{target}}|,$$ with initial value $$d_{z,0}(b) \equiv d_z(0;b)$$.

**Relation to trace distance:** $$d_z(t;b) \leq 2D(t;b)$$, with equality iff $$\langle\sigma_x\rangle = \langle\sigma_y\rangle = 0$$ for both states.

_Geometric interpretation:_ The trace distance is half the Euclidean length of the Bloch-vector difference (the full 3D displacement); $$d_z$$ is the projection onto the $$z$$-axis. Transverse coherences ($$\sigma_x$$, $$\sigma_y$$ components) contribute to $$D$$ but are invisible to $$d_z$$. Hence $$d_z$$ is a **lower bound** on $$2D$$.

**Surrogate rate:** $$R_z(b)$$ extracted from $$d_{z,\mathrm{env}}(t;b) \approx d_{z,0}(b),e^{-R_z(b)t}$$.

#### 2.5 The Governing Inequality

**Proposition.** Under the exponential-envelope approximation, the condition for decreasing equilibration time with increasing $$b$$ is:

$$\frac{\mathrm{d}t_\varepsilon}{\mathrm{d}b} < 0 \iff \frac{R'(b)}{R(b)} > \frac{D_0'(b)/D_0(b)}{\ln(D_0(b)/\varepsilon)}. \tag{1}$$

_Interpretation:_ The fractional gain in relaxation rate must exceed the fractional distance penalty, attenuated by the logarithmic depth to threshold.

**Separating phenomenon from analytic convenience.** Inequality (1) is one sufficient condition under exponential decay. Failure of exponentiality invalidates this closed-form inequality but does not invalidate the ordering question itself. The phenomenon—whether increasing $$b$$ can reduce equilibration time despite increasing initial distance—is independent of envelope shape. Alternative decay forms (algebraic, oscillatory-damped) admit analogous but more complex conditions.

**Applying Inequality (1) to the σ\_z surrogate.** When only $$d_z$$ is available, substitute $$d_{z,0}(b)$$ and $$R_z(b)$$. Satisfaction implies proxy-ordering is present. Because $$d_z \leq 2D$$, proxy-ordering is _consistent with_ true ordering but does not prove it; failure is _inconclusive_ for true ordering (see Table 1).

***

**Glossary of terms used here:**

<table><thead><tr><th width="176.3828125">Term</th><th>Meaning</th></tr></thead><tbody><tr><td>Target state</td><td>Plateau-averaged reduced state used as reference</td></tr><tr><td>Trace distance <span class="math">D</span></td><td>Half the 1-norm difference between density matrices (= half Bloch-vector Euclidean distance for qubits)</td></tr><tr><td>σ_z proxy <span class="math">d_z</span></td><td><span class="math">z</span>-component projection of Bloch-vector difference; lower bound on <span class="math">2D</span></td></tr><tr><td>Relaxation rate <span class="math">R</span></td><td>Fitted decay rate of distance envelope in pre-revival window</td></tr><tr><td>Equilibration time <span class="math">t_\varepsilon</span></td><td>First time distance stays below threshold <span class="math">\varepsilon</span> for a dwell time</td></tr><tr><td>Causal coherence</td><td>Same mechanism explains both initial distance and relaxation rate across theory, numerics, and experiment</td></tr></tbody></table>

***

**Operational definitions for claim adjudication.**

A claim of quench-controlled relaxation ordering is _falsifiable_ if it specifies a metric, target definition, and threshold such that violation of Inequality (1) rules it out within stated uncertainties, _conditional on the envelope model being adequate on the specified window_.

A claim is _confirmed_ if Inequality (1) is satisfied using a metric that upper-bounds or equals the true trace distance.

A claim is _causally coherent_ if a single mechanism consistently explains the dependence of both initial distance and relaxation rate across theory, numerics, and experiment.

Failure at any evidence level is classified as _falsification_, _inconclusive_, or _mechanism mismatch_—not as partial support.

**Table 1: Logical Status of Quench-Controlled Relaxation Ordering Claims**

<table><thead><tr><th width="102.98046875">Data</th><th width="111.36328125">Ineq. (1)</th><th width="152.83203125">Ordering Claim</th><th width="109.953125">Status</th><th>Coherence</th><th>Next Step</th></tr></thead><tbody><tr><td>Full <span class="math">D</span></td><td>Satisfied</td><td>Present</td><td>Confirmed</td><td>Coherent if one mechanism explains both <span class="math">D_0(b)</span> and <span class="math">R(b)</span></td><td>Identify mechanism; propose tomographic verification</td></tr><tr><td>Full <span class="math">D</span></td><td>Violated</td><td>Absent</td><td>Falsified (in scanned regime)</td><td>Coherent null result</td><td>Publish null + boundary of validity</td></tr><tr><td>σ_z proxy <span class="math">d_z</span></td><td>Satisfied</td><td>Proxy-ordering confirmed; true ordering not falsified</td><td>Confirmed (proxy)</td><td>Partially coherent (z-sector only)</td><td>Proceed to numerics for full <span class="math">D</span></td></tr><tr><td>σ_z proxy <span class="math">d_z</span></td><td>Violated</td><td>Inconclusive</td><td>Not falsified</td><td>Undetermined</td><td>Proceed to numerics; cannot falsify from <span class="math">d_z</span> alone</td></tr><tr><td>Any</td><td>Oscillations only cross threshold</td><td>Artefact (no faster decay)</td><td>Rejected</td><td>Mechanism mismatch</td><td>Re-examine envelope extraction</td></tr><tr><td>Any</td><td>Target drifts / non-stationary</td><td>Undefined</td><td>Ill-posed</td><td>Assumptions broken</td><td>Revise target definition or window</td></tr></tbody></table>

Any claim not mappable onto this table is not well-defined operationally.

#### 2.6 Terminology and Scope

We call the phenomenon, when observed, **quench-controlled relaxation ordering**. This phrase makes no claims about temperature, thermalization in a bath sense, or equivalence to classical Mpemba phenomenology. It is not new physics; it is a reparameterisation designed to make existing claims mutually testable.

**Scope limitation.** The framework applies to finite, engineered systems where "temperature" is not operationally well-defined. Claims of thermodynamic universality or requiring a canonical Gibbs target are outside scope.

**Relation to spectral-gap definitions.** Some formulations of quantum Mpemba-like effects \[6, 9] characterise the phenomenon via anomalous Lindbladian spectral gaps. Spectral-gap anomalies _can be_ sufficient for ordering under common assumptions (Markovianity, fixed stationary state), but they are neither necessary nor guaranteed to map one-to-one onto the present operationalisation. Our framework:

* does not assume Markovianity,
* does not assume a Lindbladian spectrum,
* and allows ordering to arise from geometry (distance structure) alone.

***

### 3. Test Platform: The Strong-Coupling Spin-Boson System of Ref. \[1]

#### 3.1 System Specification

The platform couples a single effective spin (two hyperfine states of $${}^{25}\mathrm{Mg}^+$$) to an engineered bosonic environment of $$N = 1\ldots 5$$ axial phonon modes in a hybrid Coulomb crystal. The Hamiltonian is: $$H = \frac{\hbar\omega_z}{2}\sigma_z + \frac{\hbar\Omega}{2}\sigma_x + \sum_{j=1}^{N}\hbar\omega_j a_j^\dagger a_j + \frac{\hbar\Omega}{2}\bigl(\sigma_+ C + \sigma_- C^\dagger\bigr),$$ where $$C = \exp\bigl[i\sum_j \eta_j(a_j^\dagger + a_j)\bigr] - 1$$ and $$\eta_j \approx 1$$ (strong coupling).

The control parameter is $$b \equiv \omega_z$$, the effective magnetic field.

#### 3.2 Platform Strengths

* **Strong coupling:** Higher-order terms in $$C$$ contribute; the system explores highly entangled spin-phonon states. This is the regime where counterintuitive relaxation ordering might emerge.
* **Complete parameter specification:** All experimental parameters—trap frequencies, Rabi frequencies, detunings, Lamb–Dicke parameters, mode occupations, timing sequences—are documented in the Supplementary Material of Ref. \[1]. Theory and numerics can engage without undocumented experimental details.
* **Finite closed system:** "Equilibrium" is a local stationary marginal induced by entanglement, not a bath-defined thermal state. This forces operational clarity.
* **Raw data access:** The author participated in Ref. \[1] and retains the complete raw time-series data, including runs not shown in the publication.

#### 3.3 Platform Constraint

**Observable limitation:** The experimental data consist of $$\langle\sigma_z(t)\rangle$$ measurements only. Full Bloch-sphere tomography ($$\langle\sigma_x\rangle$$, $$\langle\sigma_y\rangle$$, $$\langle\sigma_z\rangle$$) was not performed.

This means the experimental analysis provides:

* A validated methodology for target construction, envelope extraction, and rate fitting.
* A **lower bound** on the trace distance via $$d_z \leq 2D$$.
* Conservative inequality tests: satisfaction implies the effect is real; failure is inconclusive.

Definitive inequality adjudication requires numerical simulations providing full Bloch-sphere dynamics under matched Hamiltonian parameters.

Ref. \[1] focuses on ETH-style time averages and fluctuation measures \[11–14]. It does not test Mpemba-like hypotheses. However, it provides the platform specification and methodological template for such a test.

***

### 4. Required Expertise

#### 4.1 Thermalization Theory

The exponential-envelope approximation is a convenience (see §2.5). Strong-coupling dynamics may exhibit non-Markovian backflow, oscillatory decay, or algebraic tails \[15–17]. The target state may drift due to finite-size effects \[18–20].

**Key terms for non-specialists:**

* _Non-Markovian_: memory effects where the environment's past state influences current dynamics; information can flow back from environment to system.
* _Revivals_: quasi-periodic partial returns toward the initial state due to finite environment size.
* _ETH (Eigenstate Thermalization Hypothesis)_: the conjecture that individual energy eigenstates of chaotic systems encode thermal expectation values \[11–14].

We seek collaborators who can:

* Derive or bound $$R(b)$$ from Hamiltonian structure in specific limits.
* Identify regimes where the envelope approximation fails and propose alternatives (e.g., stretched exponential, power-law with cutoff).
* Connect quench-controlled relaxation ordering to established equilibration bounds and typicality arguments \[18–20].

#### 4.2 Numerical Spin-Boson Modelling

**Numerics are not auxiliary but decisive.** Given the σ\_z-only constraint on experimental data, numerical simulation is the only path to definitive inequality adjudication. Without numerical collaborators providing full Bloch-sphere dynamics, the framework remains a validated methodology with lower-bound constraints—valuable, but incomplete.

We seek collaborators who can:

* Simulate the Hamiltonian of Ref. \[1] across systematic $$\omega_z$$-scans with full spin-state output.
* Validate against the experimental $$\langle\sigma_z(t)\rangle$$ traces to confirm simulation fidelity.
* Compute the true trace distance $$D(t;b)$$ and compare with the $$d_z$$ lower bound.
* Test sensitivity of $$R(b)$$ extraction to envelope method (Hilbert transform, running minimum, low-pass filtering).
* Explore parameter regimes beyond Ref. \[1].
* Determine whether quench-controlled relaxation ordering is generic, fine-tuned, or absent in this model class.

#### 4.3 Conceptual Positioning

We seek input on:

* Whether "quench-controlled relaxation ordering" is distinct from related concepts (shortcuts to adiabaticity, prethermalization, dynamical phase transitions).
* How to position the framework relative to Refs. \[5–10] without overclaiming or underclaiming.
* Whether the Option A / Option B distinction (run-specific vs canonical target) maps onto existing debates.

This collaboration is not aimed at reinterpreting published results post hoc without time-resolved data. Contributions that relabel findings without new constraints fall outside scope.

#### 4.4 Triangulation Requirement

Claims about relaxation ordering often rely on a single evidence level: theory alone, numerics alone, or experiment alone. Each is insufficient.

We treat triangulation—mutually constraining cross-check of theory, numerics, and experiment—as a necessary condition for causal coherence (see Glossary, §2.5).

* **Theory** must predict which quantities control relaxation ordering and under which assumptions those predictions hold.
* **Numerics** must test these predictions where analytic control is limited. Crucially, numerics provide the full Bloch-sphere data that experiment lacks (see Table 1, "Next Step" column).
* **Experiment** provides $$\langle\sigma_z(t)\rangle$$ data for methodology validation, lower-bound constraints, and real measurement noise.

In this prototype, the division of labour is: experiment validates methodology and constrains $$d_z$$; numerics provide full $$D$$ and enable definitive Inequality (1) tests; theory provides mechanistic predictions. The full parameter set is public \[1, Supplement].

***

### 5. Methodological Commitments

#### 5.1 Falsification Parity

Any accepted framework states falsification criteria with the same precision as confirmation criteria. "Parameters were wrong" is not acceptable post hoc.

#### 5.2 Pre-Registration

For any test, we pre-register:

* Metric (trace distance or surrogate).
* Envelope extraction method.
* Temporal windows for fitting and plateau averaging.
* Threshold values $$\varepsilon$$.

#### 5.3 Scope Limitation

We claim only that this framework provides a falsifiable operationalisation for finite, closed, strong-coupling systems with tuneable Hamiltonians. Extensions to open systems with true baths or to many-body thermodynamic limits require separate treatment.

#### 5.4 Null Results

Null results (monotonic $$t_\varepsilon(b)$$) are informative and publishable, not failures.

***

### 6. Collaboration Structure

All phases enforce triangulation, ensuring any claimed ordering admits causally coherent explanation across theory, numerics, and experiment.

#### Phase 0: Retrospective Re-analysis (Months 1–3)

**Objective:** Validate analysis pipeline on real $$\langle\sigma_z(t)\rangle$$ data; extract lower-bound constraints.

**0.1 Primary Dataset: Ref. \[1], Full Raw Data**

Goals:

* Validate pipeline (target construction, envelope extraction, windowing, uncertainty propagation) on experimental $$\langle\sigma_z(t)\rangle$$ traces.
* Determine which parameter scans exist in the raw dataset.
* Compute $$d_z(t;b)$$ and extract $$R_z(b)$$ across available parameter variation.
* Assess whether existing data permit conservative evaluation of Inequality (1) or methodology validation only.

Pre-registered outcomes (per Table 1):

1. _Pipeline validated; data insufficient for Inequality (1) test._
2. _Pipeline validated; lower-bound constraints on_ $$d_{z,0}(b)$$ _and_ $$R_z(b)$$ _extracted._
3. _Pipeline validated; Inequality (1) satisfied using_ $$d_z$$ → proxy-ordering confirmed; proceed to Phase 2.
4. _Pipeline validated; Inequality (1) violated using_ $$d_z$$ → inconclusive; proceed to Phase 2.

Even without definitive adjudication, Phase 0 may constrain interpretations by showing that assumed preconditions (monotonic target distance, stable envelope, absence of revival dominance) are not satisfied in these data.

**0.2 Secondary Datasets**

Identify other publications providing:

* Time-resolved data (not steady-state only).
* Systematic Hamiltonian parameter scans.
* Sufficient methodological detail.

Admissibility criteria:

<table><thead><tr><th width="196.61328125">Criterion</th><th>Requirement</th></tr></thead><tbody><tr><td>Control parameter</td><td>Clear mapping to tuneable <span class="math">b</span></td></tr><tr><td>Temporal resolution</td><td>Sufficient for envelope extraction</td></tr><tr><td>Target definition</td><td>Compatible with Option A or B</td></tr><tr><td>Uncertainty</td><td>Documented</td></tr></tbody></table>

Non-admissible datasets are logged as illustrative only.

#### Phase 1: Framework Critique (Months 2–4, overlapping)

Circulate the protocol to collaborators. Collect responses on:

* Logical gaps or unstated assumptions.
* Superior alternative operationalisations.
* Theoretical results that constrain or extend the framework.
* Additional admissible datasets.

#### Phase 2: Numerical Exploration (Months 5–8)

Systematic $$\omega_z$$-scans on the Hamiltonian of Ref. \[1] or agreed variants, with **full Bloch-sphere output**.

Deliverables:

* Full spin-state dynamics: $$\langle\sigma_x(t)\rangle$$, $$\langle\sigma_y(t)\rangle$$, $$\langle\sigma_z(t)\rangle$$ across parameter grid.
* Validation: numerical $$\langle\sigma_z(t)\rangle$$ compared with experimental traces to confirm simulation fidelity.
* True trace distance $$D(t;b)$$ and rate $$R(b)$$ with uncertainties.
* Comparison: $$D$$ vs $$d_z$$ lower bound to quantify transverse-coherence contribution.
* **Definitive evaluation of Inequality (1)** using full $$D_0(b)$$ and $$R(b)$$.
* Sensitivity analysis for envelope method and windows.

#### Phase 3: Synthesis (Months 9–12)

Joint publication reporting:

* Whether quench-controlled relaxation ordering occurs (Inequality (1) status per Table 1, based on numerical $$D$$, constrained by experimental $$d_z$$).
* If satisfied: parameter regime characterisation; proposed experimental verification with full tomography.
* If violated: null result documented with full $$D$$; implications discussed.
* If inconclusive (σ\_z-only): constraints reported; numerical follow-up specified.
* Pre-registered choices and any deviations.

**Causal Coherence Report:** Structured table linking (a) hypothesised mechanisms → predicted signatures in $$D_0(b)$$, $$R(b)$$, revival structure, (b) numerical reproduction with full Bloch-sphere data, (c) experimental $$d_z$$ constraints and their consistency with numerical $$D$$. Disagreements logged as coherence breaks with attributed cause (model assumption, analysis choice, experimental confound, or transverse-coherence contribution).

***

### 7. Falsification Signatures

The hypothesis is killed for the scanned range if any of the following hold (see Table 1). Using full trace distance $$D$$ from numerics:

**Kill A (Strict nesting):** For all $$b_i < b_j$$, $$D_{\mathrm{env}}(t; b_j) > D_{\mathrm{env}}(t; b_i) \quad \forall, t \in (0, t_{\mathrm{rev}}]$$ with non-overlapping confidence bands.

**Kill B (Monotone equilibration time):** $$t_\varepsilon(b)$$ increases monotonically for all threshold values within uncertainties.

**Kill C (Inequality (1) fails everywhere):** $$\frac{R'(b)}{R(b)} \leq \frac{D_0'(b)/D_0(b)}{\ln(D_0(b)/\varepsilon)}$$ for all $$b$$, beyond $$2\sigma$$.

**Kill D (Oscillation artefact):** Only oscillations cross threshold; envelope rate does not increase with $$b$$.

**Asymmetric falsification with σ\_z-only data (Table 1, rows 3–4):**

* Inequality (1) satisfied using $$d_z$$ → proxy-ordering confirmed; proceed to numerics.
* Inequality (1) violated using $$d_z$$ → inconclusive; cannot falsify without full $$D$$.

Definitive falsification requires numerical $$D$$.

***

### 8. Invitation

This is a prototype demonstration. The experimental data validate methodology and provide lower-bound constraints; definitive adjudication requires numerical collaborators who can provide full Bloch-sphere dynamics.

We seek to make the question answerable, not to advocate for a particular answer.

If you work on open-system thermalization, quantum relaxation dynamics, spin-boson models, trapped-ion physics, or foundations of quantum statistical mechanics, and share concern that sharper definitions would benefit the field, we welcome your participation.

The protocol document is available on request. Critical responses are more valuable than enthusiastic ones.

***

### Contact

ulrich.warring@physik.uni-freiburg.de

***

### References

#### Primary Platform

\[1] G. Clos, D. Porras, U. Warring, and T. Schaetz, "Time-resolved observation of thermalization in an isolated quantum system," _Phys. Rev. Lett._ **117**, 170401 (2016). \[arXiv:1509.07712]

#### Classical Mpemba Effect

\[2] E. B. Mpemba and D. G. Osborne, "Cool?," _Phys. Educ._ **4**, 172 (1969).

\[3] M. Jeng, "The Mpemba effect: When can hot water freeze faster than cold?," _Am. J. Phys._ **74**, 514 (2006).

\[4] H. C. Burridge and P. F. Linden, "Questioning the Mpemba effect: Hot water does not cool more quickly than cold," _Sci. Rep._ **6**, 37665 (2016).

#### Quantum Mpemba-Like Phenomena

\[5] A. Lapolla and A. Godec, "Faster uphill relaxation in thermodynamically equidistant temperature quenches," _Phys. Rev. Lett._ **125**, 110602 (2020).

\[6] F. Carollo, A. Lasanta, and I. Lesanovsky, "Exponentially accelerated approach to stationarity in Markovian open quantum systems through the Mpemba effect," _Phys. Rev. Lett._ **127**, 060401 (2021).

\[7] S. K. Manikandan, "Equidistant quenches in few-level quantum systems," _Phys. Rev. Res._ **3**, 043108 (2021).

\[8] Z. Lu and O. Raz, "Nonequilibrium thermodynamics of the Markovian Mpemba effect and its inverse," _Proc. Natl. Acad. Sci. USA_ **114**, 5083 (2017).

\[9] I. Klich, O. Raz, O. Hirschberg, and M. Vucelja, "Mpemba index and anomalous relaxation," _Phys. Rev. X_ **9**, 021060 (2019).

\[10] J. Zhang _et al._, "Observation of quantum strong Mpemba effect," _Nat. Commun._ **16**, 301 (2025).

#### Quantum Thermalization and ETH

\[11] J. M. Deutsch, "Quantum statistical mechanics in a closed system," _Phys. Rev. A_ **43**, 2046 (1991).

\[12] M. Srednicki, "Chaos and quantum thermalization," _Phys. Rev. E_ **50**, 888 (1994).

\[13] M. Rigol, V. Dunjko, and M. Olshanii, "Thermalization and its mechanism for generic isolated quantum systems," _Nature_ **452**, 854 (2008).

\[14] L. D'Alessio, Y. Kafri, A. Polkovnikov, and M. Rigol, "From quantum chaos and eigenstate thermalization to statistical mechanics and thermodynamics," _Adv. Phys._ **65**, 239 (2016).

#### Open Quantum Systems and Relaxation

\[15] H.-P. Breuer and F. Petruccione, _The Theory of Open Quantum Systems_ (Oxford University Press, 2002).

\[16] Á. Rivas and S. F. Huelga, _Open Quantum Systems: An Introduction_ (Springer, 2012).

\[17] H.-P. Breuer, E.-M. Laine, J. Piilo, and B. Vacchini, "Colloquium: Non-Markovian dynamics in open quantum systems," _Rev. Mod. Phys._ **88**, 021002 (2016).

#### Equilibration in Closed Systems

\[18] P. Reimann, "Foundation of statistical mechanics under experimentally realistic conditions," _Phys. Rev. Lett._ **101**, 190403 (2008).

\[19] N. Linden, S. Popescu, A. J. Short, and A. Winter, "Quantum mechanical evolution towards thermal equilibrium," _Phys. Rev. E_ **79**, 061103 (2009).

\[20] A. J. Short and T. C. Farrelly, "Quantum equilibration in finite time," _New J. Phys._ **14**, 013063 (2012).

#### Trapped-Ion Systems

\[21] R. Blatt and C. F. Roos, "Quantum simulations with trapped ions," _Nat. Phys._ **8**, 277 (2012).

\[22] C. Monroe and J. Kim, "Scaling the ion trap quantum processor," _Science_ **339**, 1164 (2013).

***

_Claims are scoped, assumptions stated, falsification criteria explicit._
