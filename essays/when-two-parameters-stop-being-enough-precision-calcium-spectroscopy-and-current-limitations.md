---
description: >-
  A commentary on Wilzewski et al., "Nonlinear Calcium King Plot Constrains New
  Bosons and Nuclear Properties," Phys. Rev. Lett. 134, 233002 (2025)
---

# When Two Parameters Stop Being Enough — Precision Calcium Spectroscopy and the Limits of Effective I

{% hint style="info" %}
**Stewardship:** U. Warring\
**Status:** Provisional reading · v2.2 · February 2026 \
**Endorsement Marker:** Commentary (Sails layer) — not a Ledger classification\
\
**A note on this document.** This commentary reflects my current reading of Wilzewski et al. (2025) and may contain misunderstandings. The authors are warmly invited to respond, correct, or disagree; updates will incorporate clarifications as they arise. This is a living discussion document, not a fixed evaluation.
{% endhint %}

***

### The Setup: A Convenient Truncation

Isotope shift spectroscopy rests on an effective description. To leading order, the frequency shift of an electronic transition between two isotopes of the same element decomposes into two terms: a mass shift, proportional to the reduced nuclear mass difference, and a field shift, proportional to the difference in mean-squared nuclear charge radii. Each term factorises cleanly into an electronic coefficient and a nuclear parameter. This two-parameter structure — essentially an effective field theory truncated at the lowest-order nuclear moments — is the foundation of the King plot, introduced in 1963: plot the isotope shifts of one transition against those of another, and the result is a straight line, because the two nuclear parameters (mass difference and charge-radius difference) can be algebraically eliminated.

The linearity of the King plot was never a prediction of fundamental physics. It was a consequence of truncation — the decision to keep only the two leading terms in what is, in principle, an infinite series of electronic-nuclear coupling contributions. For decades, this truncation was experimentally adequate: no measurement was precise enough to see the higher-order terms. The calcium King plot, in particular, appeared stubbornly linear, its low nuclear mass and spherical nuclear shape suppressing finite-size effects by three orders of magnitude relative to heavier systems like ytterbium.

Wilzewski et al. have now broken through this floor. Their combined measurements yield a King plot nonlinearity significant at the level of order 10³σ (the collaboration quotes \~900σ) — not a subtle hint but an unambiguous departure from the two-parameter effective theory. The central question is not whether the nonlinearity is real, but what it tells us about the physics beyond the truncation. This work is best read as a precision test of the factorisation and truncation assumptions underlying effective isotope-shift theory, with BSM sensitivity as a corollary.

### What the Collaboration Measured

The result emerges from the convergence of three independent measurement campaigns across major European metrology facilities, spanning all five stable, even calcium isotopes (⁴⁰Ca, ⁴²Ca, ⁴⁴Ca, ⁴⁶Ca, ⁴⁸Ca).

At the Physikalisch-Technische Bundesanstalt in Braunschweig, the team measured isotope shifts of the ³P₀ → ³P₁ fine-structure transition in Ca¹⁴⁺ — calcium stripped of fourteen electrons. Since highly charged ions lack fast-cycling transitions suitable for direct laser cooling, the Ca¹⁴⁺ ions were sympathetically cooled and interrogated via quantum-logic spectroscopy using a co-trapped Be⁺ logic ion. The interrogation laser was referenced to an ultrastable silicon cavity and calibrated against PTB's ytterbium ion optical clock, yielding isotope shift uncertainties below 150 millihertz.

At ETH Zürich, correlation spectroscopy of the ²S₁/₂ → ²D₅/₂ transition in singly-charged Ca⁺ exploited a decoherence-free entangled state of two co-trapped isotopes to achieve common-mode rejection of laser phase noise. By preparing the two-ion state in the subspace that precesses at the isotope shift frequency while remaining insensitive to shared noise sources, the team pushed isotope shift uncertainties below 70 millihertz.

At the Max Planck Institute for Nuclear Physics in Heidelberg, the PENTATRAP facility determined nuclear mass ratios by measuring cyclotron frequency ratios of highly charged calcium ions shuttled between stacked Penning traps, achieving relative uncertainties below 4 × 10⁻¹¹.

Each campaign, independently, represents a state-of-the-art measurement. Combined, they expose a nonlinearity that the two-parameter effective isotope-shift theory cannot accommodate.

### Decomposing the Nonlinearity

The collaboration's analysis of the nonlinearity is built on a geometric framework that deserves careful attention, both for what it reveals and for the assumptions it encodes.

With five isotopes forming four isotope pairs relative to ⁴⁰Ca (a convenient choice that fixes a basis in the full pair space), the modified isotope shifts of two transitions define a four-dimensional space. King linearity corresponds to confinement to a two-dimensional plane spanned by the unit vector and the modified shifts of the first transition. Any nonlinearity has a finite projection onto the two out-of-plane basis vectors, labelled Λ₊ and Λ₋ — specific linear combinations of the isotope-shift vectors chosen to diagonalise the dominant SM contributions — which together span all possible patterns of residuals around a straight-line King fit. The decomposition analysis, developed in prior work by several of the co-authors, maps each physical source of nonlinearity (under the standard factorizable ansatz) onto a specific direction in the (λ₊, λ₋) plane, determined by the isotope-dependence of the underlying nuclear parameter. The collaboration assumes factorizability for the decomposition — an assumption that is well justified for some contributions but, as discussed below, structurally uncertain for others. The electronic coefficient of each effect then sets the magnitude of its vector contribution. A hypothetical new boson coupling electrons and neutrons, for instance, would contribute along a direction fixed by the neutron-number differences (A − A') of the isotope pairs — the cyan line in the paper's Figure 2 — making it immediately visible whether the measured residual is geometrically compatible with a BSM origin.

This geometric approach makes the reasoning visually auditable. One can read directly from the plot why the second-order mass shift — the largest expected higher-order Standard Model contribution — fails to explain the data: its predicted contribution (the red dot) points in the wrong direction in the (λ₊, λ₋) plane to reach the measured nonlinearity (the black cross). The discrepancy is not merely one of magnitude but of geometric signature.

After subtracting the calculated second-order mass shift, a residual nonlinearity remains. The team identifies nuclear polarisation as the only remaining Standard Model contribution known to be potentially large enough to account for it. Nuclear polarisation arises from virtual excitations of the nucleus induced by the atomic electrons, effectively entangling the electronic and nuclear subsystems. The collaboration computed this effect using a nuclear model incorporating rotational transitions and giant resonances up to octupole order, drawing on recent detailed calculations for Ca⁺ by Viatkina, Yerokhin, and Surzhykov and performing new calculations for Ca¹⁴⁺. It is worth noting that the identification of nuclear polarisation as the plausible remaining source rests not merely on the general physical existence of this effect but on the specific quantitative modelling in these calculations — a distinction that matters when assessing how robust the SM interpretation is. Within a 50% author-estimated theoretical uncertainty, the nuclear polarisation contribution overlaps with the measured residual, making the data compatible with the Standard Model.

### The Deeper Issue: Model Identifiability

The 50% theoretical uncertainty on nuclear polarisation is widely noted and deserves attention, but it is not the most fundamental concern. The deeper issue is structural.

The decomposition framework assumes that each source of nonlinearity contributes an additive, factorizable term — a product of an isotope-independent electronic coefficient and an isotope-dependent nuclear parameter. For the second-order mass shift, this factorisation is well established. For nuclear polarisation, it is not. Nuclear polarisation generically induces state-dependent operator mixing: the effective atomic Hamiltonian acquires a nuclear self-energy correction that depends on the electronic state energy, coupling the electronic and nuclear degrees of freedom in a way that cannot be cleanly separated into independent factors. In the language of many-body theory, the effective Hamiltonian becomes

H\_eff = H\_atomic + Σ\_nuclear(E)

where the nuclear self-energy Σ is energy-dependent and non-separable.

This has a direct consequence for the geometric decomposition. The (λ₊, λ₋) basis is meaningful only if the contributing effects correspond to independent physical operators. If nuclear polarisation violates factorizability, it does not contribute along a single fixed direction in the decomposition plane — its "direction" becomes state-dependent and potentially isotope-pair-dependent. The geometric argument that nuclear polarisation "points in the right direction" is therefore informative but not strictly decisive: it demonstrates compatibility within the factorizable approximation, but cannot confirm compatibility outside it.

The real ambiguity, then, is not parameter uncertainty within a model. It is model identifiability: can the data distinguish between (a) a factorizable nuclear polarisation contribution with large but bounded uncertainty, (b) a non-factorizable nuclear polarisation contribution with a different effective operator structure, and (c) a combination of nuclear polarisation and a small BSM contribution that happen to mimic the observed residual pattern? With the current data and theoretical framework, these alternatives are not fully separable. Operationally, the discriminant is whether a single additional operator (or response kernel) fitted across transitions can account for all residual patterns without requiring transition-dependent redefinition — a test that demands both richer nuclear-structure calculations and additional precisely measured transitions.

This is what makes the result scientifically interesting at a level beyond the BSM search. The King plot was always an effective-theory tool, and the calcium measurement is among the first clear cases where the effective theory's structural assumptions — not just its parameters — are being tested at the precision frontier. The collaboration's data do not merely constrain a new boson; they probe whether the factorisation

(electron physics) ⊗ (nuclear physics)

is itself an adequate description at the sub-hertz scale.

### Constraints on New Physics

Despite the observed nonlinearity and the interpretive ambiguities it introduces, the collaboration extracts improved bounds on hypothetical new bosons through a generalised King plot analysis.

The method is conceptually analogous to the original King plot's elimination of nuclear charge radii: by incorporating a third transition (the ²D₃/₂ → ²D₅/₂ fine-structure interval in Ca⁺, measured in earlier work by Solaro et al. and Chang et al.), one additional source of nonlinearity can be algebraically eliminated. The collaboration assigns the two nonlinearity sources as follows: the second-order mass shift is subtracted using calculated coefficients (K₅₇₀⁽²⁾ calculated to 10% uncertainty in this work; K₇₂₉⁽²⁾ and K\_DD⁽²⁾ from prior calculations with an assigned 100% uncertainty), and a second source — attributed to nuclear polarisation — is eliminated through the generalised King plot construction.

The resulting generalised King plot is linear to within one standard deviation, implying that no further significant sources of nonlinearity contribute beyond the two accounted for. This linearity, combined with the assumption that a new boson would contribute an additional nonlinearity beyond these SM effects, yields an exclusion curve for the Yukawa coupling strength y\_e y\_n that improves on all prior King-plot-derived bounds for most boson masses between 10 eV/c² and 10⁷ eV/c².

Two factors currently limit the bound: the theoretical uncertainty on the Ca⁺ second-order mass shift coefficients, and the approximately 20 Hz measurement precision of the ²D₃/₂ → ²D₅/₂ transition from the earlier experiments. The authors note that reducing the nuclear polarisation uncertainty to approximately 10% and achieving sub-hertz precision on the third transition would push BSM sensitivity into parameter space not yet probed by any other laboratory method.

It is worth being explicit that the BSM bound is conditional on the parameterisation adopted in the generalised King plot — specifically, on the assumption that the eliminated nonlinearity sources are correctly identified and that their operator structure is factorizable. This conditionality does not invalidate the bound but defines its scope of applicability.

### What Could Be Done Better

The preceding analysis has been largely appreciative of the collaboration's scientific conduct, and deservedly so. But a careful commentary owes the work — and the field — an honest account of where current practice falls short and where methodological advances could sharpen both the result and its interpretation.

#### Data Accessibility

The paper states that the supporting data "are not publicly available upon publication because it is not technically feasible and/or the cost of preparing, depositing, and hosting the data would be prohibitive within the terms of this research project." The data are available from the authors upon reasonable request.

This warrants closer discussion. The core reduced data — isotope shift frequencies, mass ratios, covariance matrices — fit comfortably in a single table, and Table I of the paper already contains most of it. What would add genuine reproducibility value is the release of a minimal bundle: the reduced isotope shift values with full covariance matrices, the systematic uncertainty breakdowns for each facility, the intermediate quantities entering the decomposition and generalised King plot analyses (including the calculated electronic coefficients and their uncertainties), and the code required to reproduce Figures 2 and 3. Beyond this, the underlying measurement records — individual spectroscopic scans, cyclotron frequency ratio time series — would enable deeper methodological scrutiny.

It is fair to acknowledge that multi-platform collaborations face genuine practical challenges in data curation: heterogeneous formats across facilities, internal metadata conventions, and the fact that some intermediate products (detailed theory calculations, decomposition code) reside in theory groups with their own norms. These are real obstacles. But in 2025, multiple discipline-appropriate repositories exist (Zenodo, Dryad, institutional data archives) that would host such data at negligible cost. The FAIR principles — findable, accessible, interoperable, reusable — are now a condition of funding for many of the agencies acknowledged in the paper, including the Deutsche Forschungsgemeinschaft and the European Research Council.

The three-facility structure of this collaboration makes the case stronger, not weaker. Independent reanalysis by groups outside the collaboration — testing alternative decomposition methods, different uncertainty models, richer operator bases — is precisely the kind of scientific cross-check that open data enables. The community should regard comprehensive data release as part of the experimental deliverable, and funding agencies should support that view. A PRL publication carrying the "Featured in Physics" designation could help catalyse this norm.

#### Blinding and Analyst Bias

The paper does not mention whether any blinding protocol was applied during data collection or analysis. This is not unusual in precision atomic physics, where blinding has historically been less common than in particle physics or gravitational-wave astronomy. The question is worth raising, though its significance here should not be overstated.

The dominant ambiguity in this result is theoretical, not procedural. No plausible analyst choice could move a thousand-sigma nonlinearity into or out of existence. The analysis freedom lies in how the nonlinearity is _distributed_ among contributing effects — which corrections to subtract, which uncertainties to assign, which model assumptions to adopt. Blinding would improve sociological credibility but would not materially change the physics conclusion. The limiting systematic is ontological (model structure), not procedural (analyst tuning).

That said, as isotope shift measurements enter the regime where Standard Model higher-order effects and BSM signals are of comparable magnitude, the distinction between procedural and ontological limitations will narrow. Future experiments targeting the residual nonlinearity after subtraction of known SM contributions will face exactly the conditions where blinding pays its largest dividends: small residuals, multi-step inference chains, and analysis choices that can shift results by amounts comparable to the signal of interest.

A staged blinding protocol could be implemented at multiple levels. Within each facility, systematic corrections and uncertainty budgets could be finalised before seeing the other groups' results, with combination performed by a designated analyst working from sealed inputs. Alternatively, salted offsets could be applied at the level of King-plot coordinates or even (λ₊, λ₋) components, preserving the analysts' ability to perform quality checks while preventing outcome-dependent tuning. The LIGO/Virgo collaboration's experience is instructive: blinding was initially resisted as unnecessary overhead but is now regarded as essential to detection credibility. Precision atomic physics would benefit from beginning this transition before the need becomes acute.

#### Towards Richer Inference: Model Expansion and Hierarchical Bayesian Methods

The statistical framework of the paper is predominantly frequentist: the nonlinearity is quantified by a deterministic volume in isotope-pair space, uncertainties are propagated through standard error analysis, and the BSM exclusion curve represents a 95% confidence bound. This is conventional and competently executed, but the problem's structure invites a more expressive framework.

However, the most impactful methodological improvement would not be a change of statistical paradigm alone. Bayesian methods propagate uncertainty within a model class; they do not correct a misspecified model class. If nuclear polarisation breaks factorisation, the likelihood function itself is wrong, and a posterior computed over incorrect models becomes a well-quantified wrong answer. The strongest advance would therefore be _model expansion_: enriching the operator basis before refining the inference.

Concretely, this could mean including transition-dependent effective operators that allow for non-factorizable nuclear response kernels, fitting atomic and nuclear coefficients simultaneously rather than in a sequential subtract-then-fit procedure, and treating factorizability itself as a model-comparison question rather than a fixed assumption. Only within an expanded model space does probabilistic inference become decisive.

A hierarchical Bayesian framework is naturally suited to this enriched problem. At the lowest level, it would model the individual measurements with their facility-specific error structures, maintaining the crucial separation between epistemic (theory) and aleatory (measurement) uncertainties — a distinction that is very difficult to preserve in chained frequentist error propagation but emerges naturally in a hierarchical model. At the next level, theoretical coefficients (second-order mass shift, nuclear polarisation parameters) would enter as latent variables with priors reflecting the current state of calculations — perhaps log-normal or half-Cauchy distributions on the ratio functions, with hyperparameters informed by the spread of existing nuclear model results. It should be acknowledged that these nuclear-theory inputs are themselves outputs of complex many-body calculations with their own internal priors and model assumptions; treating their uncertainties as simple parametric priors is already an approximation, though a tractable one that captures the dominant variance. At the highest level, BSM coupling strength and the choice between factorizable and non-factorizable nuclear polarisation models could be handled through joint posterior inference and Bayes factors.

Several concrete advantages would follow. The 50% uncertainty on nuclear polarisation, currently treated as a hard bound on an uncertainty ellipse, would be replaced by a continuous prior that can be updated as improved calculations become available. The correlation structure between different sources of uncertainty would be propagated consistently through to the final BSM bound, rather than handled through a sequence of independent approximations. And the analysis would become incrementally updatable: as the anticipated sub-hertz ²D₃/₂ → ²D₅/₂ measurement, improved second-order mass shift theory, and reduced nuclear polarisation uncertainties arrive, each could be incorporated without re-deriving the entire analysis chain.

The computational cost of such an analysis is no longer prohibitive. Modern probabilistic programming tools (Stan, NumPyro, PyMC) handle models of this complexity with Hamiltonian Monte Carlo sampling in minutes to hours. Similar hierarchical approaches are already standard in cosmological parameter inference and global parton distribution function fits in particle physics. The principal barrier in precision metrology is cultural rather than technical: the shift to fully probabilistic inference requires making prior assumptions explicit, which — somewhat paradoxically — makes the analysis more transparent, not less.

One tension is worth acknowledging. The geometric decomposition plot (Figure 2) achieves its explanatory power through visual, deterministic reasoning: one can see directly why the second-order mass shift fails and where nuclear polarisation must land. Bayesian posteriors, while statistically optimal for nested uncertainties, risk obscuring this directional legibility behind posterior integrations. The field may face a genuine trade-off between statistical rigour and epistemic accessibility. The ideal framework would preserve the geometric transparency of the decomposition while embedding it within a probabilistic structure that correctly handles the nested, correlated, and partially structural uncertainties. Achieving this synthesis is a methodological challenge worth pursuing.

### The Broader Lesson

The calcium King plot result illustrates something important about where the precision frontier now stands. The experiments are working. The tools — quantum-logic spectroscopy of highly charged ions, correlation spectroscopy of entangled ion pairs, Penning-trap mass spectrometry — have matured to the point where they probe physics that was previously invisible. But what they have made visible is not (yet) new fundamental interactions. It is the next layer of the atomic-nuclear interface: the regime where the convenient factorisation of electronic and nuclear contributions breaks down, where non-factorizable nuclear response — exemplified here by nuclear polarisation — becomes the dominant interpretive challenge.

This is a deeper kind of result than a bound on a new boson, though it produces that too. Collider physics tests coupling constants within a fixed field-theoretic framework. Precision isotope-shift spectroscopy, at the level now achieved, tests whether the effective-theory _structure_ — the separation of electron physics from nuclear physics — is itself adequate. That is a qualitatively different probe, and it is one that only becomes available when experimental precision outpaces the truncation order of the effective description.

The field has always been nuclear-limited in principle. What has changed is that experimentalists have now reached the scale where this limitation is empirically manifest. The thousand-sigma nonlinearity is not a surprise that required explanation so much as the first direct observation of what was always expected to appear once measurements crossed the threshold of higher-order electronic-nuclear coupling. The novelty lies not in the appearance of nuclear physics but in the breakdown of a historically convenient truncation — and in the fact that the collaboration had both the precision to see it and the integrity to characterise it honestly.

Maturity, however, brings obligations beyond measurement. When the interpretive chain runs through multi-source decomposition analyses with phenomenological uncertainty estimates and structural assumptions about operator factorizability, the field's methodological infrastructure must keep pace. Open data practices enable the independent reanalysis that credibility demands. Blinding protocols, while secondary to the theoretical challenges in this specific result, will become essential as residuals shrink toward the BSM-sensitive regime. And a richer statistical and operator-theoretic framework — combining model expansion with hierarchical Bayesian inference — offers the language naturally suited to problems where the question is not just "what are the parameters?" but "is the model itself correct?"

The paper is a quiet demonstration of what large-scale collaborative precision science looks like when it works well: three major European facilities contributing independent, complementary measurements; theorists from multiple groups providing the calculations needed for interpretation; an analysis framework developed incrementally over prior publications by several of the co-authors. The result is not the product of a single brilliant insight but of carefully built infrastructure — experimental, theoretical, and analytical — converging on a problem that no single group could have addressed alone.

In a field often drawn to heroic narratives, this paper offers a different model: systematic, transparent, self-critical, and quietly ambitious. The thousand-sigma nonlinearity does not require new physics to explain within present modelling. It is the first precision-frontier observation of the breakdown of the effective two-parameter isotope-shift theory — and the infrastructure that found it, characterised it, and honestly adjudicated it is precisely what will be needed when new physics does appear. The question for the field is whether it will also build the methodological infrastructure — open data, blinding, model expansion, probabilistic inference — that will make such a discovery not merely announced but believed.

***

### Update Log

<table><thead><tr><th width="100.55078125">Date</th><th width="102.06640625">Version</th><th>Change</th></tr></thead><tbody><tr><td>Feb 2026</td><td>v1.0</td><td>Initial commentary drafted</td></tr><tr><td>Feb 2026</td><td>v2.0</td><td>Major revision: reframed around effective-theory breakdown; added model identifiability section; recalibrated blinding discussion; prioritised model expansion over inference refinement</td></tr><tr><td>Feb 2026</td><td>v2.1</td><td>Targeted edits: thesis-locking sentence; factorizable ansatz qualifier; operational discriminant; minimal reproducibility bundle; nested theory complexity acknowledgement; ~900σ precision on first mention</td></tr><tr><td>Feb 2026</td><td>v2.2</td><td>Final calibration: softened historical uniqueness claim; "does not require new physics" replaces "is not new physics"; nuclear polarisation reframed as exemplar of non-factorizable response; author notification line added</td></tr></tbody></table>

### Invitation to Dialogue

This commentary was written in the spirit of engaged reading, not adjudication. I would welcome responses, corrections, or disagreements from the authors of the original work or from anyone in the precision metrology and isotope-shift community. Substantive responses will be incorporated into future versions with full attribution, and any errors of understanding on my part will be corrected transparently.

If you wish to contribute, please reach out directly or open a discussion on this page.

_The authors of Wilzewski et al. (2025) were notified of this commentary upon publication and invited to respond._

***

_Commentary prepared February 2026. The author declares no competing interests with respect to the work discussed._
