-----

## description: Set of Principles for Quantum-Traceable Refractive Index Metrology

# Quantum-Traceable Refractometry

{% hint style=“info” %}
**Authors*:** Ulrich Warring and Wei Wu  
**Framework ID:** IF-QTR  
**Version:** 0.3.0

**License:** CC BY 4.0  
**Status:** Constitutional reference document (stewardship phase)  
**Scope:** Precision refractometry architectures claiming traceability to atomic frequency standards  
**Endorsement Marker:** Local framework under stewardship — no parity implied with BIPM standards or established atmospheric models  
**Lineage:** Metrological systems with environmental coupling  
**Validation status:** Constitutional principles (IF-1 through IF-7) are wavelength-agnostic by design. Validation occurs through framework instances documented in external handbooks. No instance-specific content resides in this document.  
  
**Listed alphabetically. Authors contribute unique perspectives but share responsibility for the complete text.*
{% endhint %}

-----

### I. Constitutional Status

This document defines boundary conditions for precision refractometry traceable to atomic frequency standards. It is wavelength-agnostic and species-agnostic. It is not a methods paper, protocol, or standard.

#### Binding Rules

1. Every handbook claim affecting traceability, uncertainty, or comparability must cite at least one IF principle by identifier.
1. No handbook procedure may contradict an IF principle.
1. Handbooks must cite IF; IF must never cite handbooks.
1. Wavelength-specific implementations constitute *framework instances* that inherit all IF-QTR principles.
1. No instance may weaken, relax, or override any IF-QTR principle.

#### Layer Separation

|Layer     |Governs                           |Inheritance                       |
|----------|----------------------------------|----------------------------------|
|IF-QTR    |Constitutional boundary conditions|—                                 |
|IF-QTR-λ  |Wavelength-specific constraints   |Must satisfy all IF-QTR principles|
|Handbook  |Implementation                    |Must satisfy parent instance      |
|Governance|Decisions in context              |Outside IF scope                  |

**Rationale:** Prevents conflation of metrological requirements with engineering choices or wavelength-specific physics (cf. JCGM 200:2012 VIM §2.39–2.41).

-----

### II. External Constraints (Citation-Only)

This framework operates within boundaries established elsewhere. These are referenced, not replicated:

|Constraint                   |Source                                    |Role in IF                                          |
|-----------------------------|------------------------------------------|----------------------------------------------------|
|SI unit definitions          |BIPM SI Brochure (9th ed.)                |Defines SI base units and their realisation         |
|Metrological traceability    |JCGM 200:2012 (VIM) §2.41                 |Defines traceability; governs chain requirements    |
|Uncertainty vocabulary       |JCGM 200:2012 (VIM)                       |Defines “precision,” “accuracy,” “Type A/B”         |
|Uncertainty expression       |JCGM 100:2008 (GUM)                       |Governs coverage factors and expanded uncertainty   |
|Causality and linear response|Kramers-Kronig relations                  |Governs refractive index near absorption features   |
|Spectroscopic data           |HITRAN 2020 (Gordon et al. 2022)          |Provides absorption line positions and intensities  |
|Atmospheric models           |Ciddor (1996), Edlén (1966), Mathar (2007)|Reference models within their stated validity ranges|

**Constraint on constraints:** External constraints are immutable from the perspective of this framework. Any apparent conflict between IF-QTR principles and external constraints shall be resolved in favour of the external constraint, with the conflict documented as a framework limitation.

**Version pinning:** Spectroscopic databases evolve. Instances should pin to a specific database version (e.g., “HITRAN 2020”) and document any sensitivity to database updates.

-----

### III. Seven Invariant Principles

#### IF-1 — Operational Traceability

**Statement:** A refractive index value n(λ) may only be called traceable to an atomic frequency standard if there exists an explicit, uninterrupted comparison chain from that standard to the reported value, with quantified uncertainty and Type A/B classification at each stage.

**Formal requirement:** The chain must be documentable as:

```
[Atomic reference] → [Frequency transfer] → [Optical transduction] → [Environmental correction] → [Reported n(λ)]
```

Each link requires:

- Standard uncertainty (k = 1), expressed in consistent units (δn or δf/f with documented conversion)
- Classification as Type A or Type B per GUM
- Explicit statement of correlations with adjacent links (independence must be justified, not assumed)

The final reported value must state:

- Combined standard uncertainty (u_c)
- Coverage factor (k)
- Expanded uncertainty (U = k × u_c)

The atomic reference may be any species with a documented frequency standard.

**Falsification condition:** Demonstration that a claimed “traceable” measurement lacks documented uncertainty or Type A/B classification at any stage, or that correlations between links are neither stated nor justified.

-----

#### IF-2 — Layered Uncertainty Accounting

**Statement:** Uncertainty must be reported in three non-fungible layers:

<table><thead><tr><th width="155.75">Layer</th><th>Symbol</th><th>Content</th><th>Typical sources</th></tr></thead><tbody><tr><td>Frequency</td><td>L_freq</td><td>Atomic reference, frequency transfer, laser stabilisation</td><td>Ion/atom stability, cavity drift, lock bandwidth</td></tr><tr><td>Transduction</td><td>L_trans</td><td>Interferometric or spectroscopic conversion to refractive index</td><td>OPD measurement, fringe counting, ratio determination</td></tr><tr><td>Environmental</td><td>L_env</td><td>T, H, P, composition sensing; spatial and temporal co-location</td><td>Sensor accuracy, calibration drift, gradient effects</td></tr></tbody></table>

**Non-fungibility:** These layers cannot be collapsed into a single number without displaying their decomposition. The layers represent physically distinct contributions that may improve independently as technology advances.

**Cross-layer covariance rule:** Cross-layer cancellation or partial cancellation is not permitted unless covariance terms are explicitly modelled, quantified, and justified. Assumed independence between layers must be stated and defended.

**Dominance transparency:** Where one layer dominates (e.g., L_env in sensor-limited systems), this dominance is a permanent architectural fact that must remain visible in all derived work. Specifically, dominance must be stated in: (a) the abstract or summary, (b) the results section, and (c) any conclusions regarding achievable accuracy. Reporting only the best-performing layer is a violation.

**Falsification condition:** Demonstration that the three layers cannot be decomposed without materially altering the inference about n(λ), or that cross-layer correlations were assumed away without justification.

-----

#### IF-3 — Common-Mode Rejection (where applicable)

**Statement:** Where multi-wavelength operation is employed, the architecture must demonstrably suppress shared-mode noise by comparative measurement. The suppression must be quantified as a dimensionless rejection factor at a stated bandwidth and for a stated noise type.

**Applicability condition:** Multi-wavelength operation is subject to IF-3 if and only if the wavelengths share a common physical path and noise source such that a legitimate ratio-metric comparison is possible. Systems using multiple wavelengths with independent paths or uncorrelated noise sources are not subject to IF-3 but must characterise noise independently under IF-2.

**Formal requirement:** For applicable systems, report:

- CMR = σ_single / σ_comparative (dimensionless)
- Measurement bandwidth Δf (Hz) or averaging time τ (s)
- Noise type (white, flicker, random walk, or other with physical justification)
- Estimator used (e.g., Allan deviation, power spectral density, time-domain standard deviation)

**Comparability requirement:** σ_single and σ_comparative must be computed using the same estimator, the same bandwidth or averaging time, the same preprocessing, and on datasets of comparable duration and conditions. Cherry-picking favourable conditions for one but not the other invalidates the CMR claim.

**Interpretive guidance (non-binding):**

- CMR < 1 (indicating that dual-wavelength operation increases noise) is implausible for well-designed systems and requires independent verification or explanation.
- CMR > 100 at audio frequencies (1–10 Hz) suggests measurement of a single dominant noise mode rather than broadband system characterisation; the autocorrelation structure or power spectral density should be shown.

**Falsification condition:** Demonstration that comparative measurement fails to yield CMR > 1 at the stated bandwidth and noise type, or that CMR was computed using incompatible methods for single vs. comparative measurements.

-----

#### IF-4 — Environmental Co-location

**Statement:** Environmental sensing must be spatially and temporally co-located with the measurement volume. Where practicable, physical co-location is preferred over model-based correction.

**Definitions:**

- *Measurement volume*: The minimum convex hull enclosing the optical path during the integration period of a single data point. For systems with folded or multi-pass geometries, this is the union of convex hulls for each distinct path segment.
- *Measurement volume boundary*: The surface of the measurement volume as defined above.
- *Co-location*: Sensor placement within a stated distance of the measurement volume boundary.

**Operational proxy for complex geometries:** Where the measurement path cannot be uniquely described by a simple volume bounding box (e.g., folded optics, multi-segment interferometers, resonator modes, or stratified environments), an explicit mapping to the relevant optical path segments and their associated environmental gradients must be provided. This mapping must demonstrate that the stated co-location bound applies to each segment, or that segment-specific corrections with quantified uncertainty are applied.

**Formal requirements:**

- Spatial bound: State maximum separation between sensor and measurement volume boundary, with justification (e.g., gradient estimate, prior measurement, or fluid dynamics argument).
- Temporal bound: State synchronisation method and maximum latency.
- If correction is used instead of co-location, its uncertainty must be shown to be subdominant to sensor uncertainty.

**Falsification condition:** Demonstration that spatial or temporal mismatch introduces systematic error exceeding the stated environmental sensor uncertainty, or that the measurement volume definition is ambiguous for the stated geometry.

-----

#### IF-5 — Model Transparency and Scope

**Statement:** Any model mapping environmental parameters to refractive index must state:

1. Functional form (e.g., linear, polynomial, physics-based)
1. Input variables and their units
1. Training domain (parameter ranges with explicit bounds)
1. Validation domain (if different from training)
1. Effective sample size N_eff after autocorrelation correction (for empirical models)
1. Diagnostic tests confirming residuals are consistent with the stated noise model

Outside the stated domain, model-derived claims are invalid. The IF does not prescribe functional form; it requires demonstrated adequacy within scope.

**Required diagnostics:** At minimum, one of the following must be reported:

- Autocorrelation function of residuals, or
- Durbin-Watson statistic, or
- Ljung-Box Q-statistic

with interpretation relative to white-noise null hypothesis. Significant autocorrelation (e.g., Durbin-Watson substantially below 2, or Breusch-Godfrey p < 0.01) must be addressed via HAC standard errors, AR modelling, or equivalent; the chosen remedy must be stated.

**Collinearity diagnostics:** Where multiple environmental parameters are used, variance inflation factor (VIF) or equivalent must be reported. VIF > 10 for any predictor indicates problematic collinearity requiring attention (variable transformation, regularisation, or explicit acknowledgment as a limitation).

**Falsification condition:** Demonstration that the model materially fails within its stated domain, that required diagnostics are absent, or that the model requires ad hoc adjustment to function outside its domain without explicit re-validation.

-----

#### IF-6 — Precision–Accuracy Separation

**Statement:** Two quantities must always be reported separately:

|Quantity             |Definition                                     |GUM classification|Typical evaluation method                                                             |
|---------------------|-----------------------------------------------|------------------|--------------------------------------------------------------------------------------|
|Residual precision   |Repeatability of measurement or model fit (σ)  |Type A            |Statistical analysis of repeated measurements or fit residuals                        |
|Metrological accuracy|Dominant Type B contribution (systematic floor)|Type B            |Calibration certificates, manufacturer specifications, or independent characterisation|

**Combination rule:** These may only be combined via stated coverage factor (k) to yield expanded uncertainty U = k × u_c per GUM, where:

u_c = √(u_A² + u_B² + 2·r·u_A·u_B)

The correlation coefficient r between Type A and Type B components must be stated. If independence is assumed (r = 0), this must be justified.

**Systematic precision:** Where repeatability is limited by a systematic effect (e.g., drift), this component should be classified as Type B if it arises from a known physical mechanism with bounded magnitude, or Type A if it is measured empirically from repeated measurement cycles. Mixed cases require explicit decomposition.

**Falsification condition:** Demonstration that for a specific measurement class, Type A and Type B contributions cannot be meaningfully separated, or that correlations were assumed away without justification.

-----

#### IF-7 — Cross-Instance Correlation (where applicable)

**Statement:** Where multiple framework instances are applied to the same measurement volume during overlapping time intervals (e.g., simultaneous n(λ₁) and n(λ₂) measurements for dispersion characterisation), shared uncertainty contributions must be identified and their correlation structure documented.

**Applicability condition:** IF-7 applies whenever:

- Two or more IF-QTR instances are used on the same physical apparatus, AND
- Measurements occur within temporal windows where environmental conditions are correlated, AND
- Results are combined or compared (e.g., for dispersion, wavelength-dependent systematics, or cross-validation).

**Formal requirement:** For applicable cases, identify:

- Shared components (e.g., common environmental sensors, shared optical geometry, common timing reference)
- Correlation coefficient or covariance for each shared component
- Impact on combined uncertainty when results from multiple instances are used together

**Falsification condition:** Demonstration that cross-instance correlations materially affect combined results but were not documented.

-----

### IV. Framework Instances

The general IF-QTR is implemented through wavelength-specific *framework instances* documented in external handbooks.

#### Architectural Separation

|Document Type         |Contains                                                                                  |Does Not Contain                                   |
|----------------------|------------------------------------------------------------------------------------------|---------------------------------------------------|
|IF-QTR (this document)|Principles, templates, constraints, upgrade criteria                                      |Numerical values, coefficients, measured quantities|
|Framework Instance    |Declaration block, wavelength-specific constraints, absorption notes                      |Implementation data, compliance evidence           |
|Implementing Handbook |All numerical values, coefficients, uncertainties, validation data, compliance declaration|Constitutional principles (cites IF-QTR instead)   |

**Separation rule:** The IF-QTR contains no wavelength-specific numerical values. All such values reside exclusively in implementing handbooks. This separation ensures that the constitutional document remains stable while implementations evolve.

#### Inheritance Rule

Instances must satisfy all IF-QTR principles without weakening, relaxing, or overriding any of them. Instances may only add constraints, never remove them.

#### Correction Rule

If an instance invokes corrections beyond standard atmospheric models, those corrections must themselves be:

- Falsifiable (with stated test)
- Uncertainty-quantified (with coverage factor)
- Documented with stated validity range

All correction values reside in the implementing handbook, not in the instance declaration.

#### Instance Declaration Template

```
┌─────────────────────────────────────────────────────────┐
│ FRAMEWORK INSTANCE DECLARATION                          │
│                                                         │
│ Instance ID: IF-QTR-[identifier]                        │
│ Parent: IF-QTR v[version]                               │
│ Wavelength scope: [range with units]                    │
│ Atomic reference: [species and transition]              │
│ Absorption proximity: [relevant features or "none"]     │
│ Standard model validity: [applicable models and limits] │
│ Gas composition: [assumptions and measured quantities]  │
│ Required corrections: [with uncertainty]                │
│ Temporal validation: [minimum requirement]              │
│ Spectroscopic database: [name and version]              │
└─────────────────────────────────────────────────────────┘
```

#### Instance-Specific Requirements

Each implementing handbook must address:

1. Proximity to molecular absorption features (H₂O, CO₂, O₂, etc.)
1. Validity range of standard atmospheric models at the operational wavelength
1. Required corrections beyond standard models, with uncertainty
1. Wavelength-specific systematic effects
1. Gas composition assumptions
1. Environmental validation ranges (T, H, P bounds)
1. Temporal validation (minimum: one diurnal cycle; document duration achieved)
1. Spectroscopic database version

These requirements specify *what must be documented*, not *what values to use*. Values belong in handbooks.

-----

### V. Constructive Frictions

The IF acknowledges the following structural tensions. These are diagnostic, not prescriptive; navigation is left to implementers.

#### 1. Frequency-layer excellence vs. environmental-layer limitations

Current architectures routinely achieve L_freq many orders of magnitude below L_env when using commercial environmental sensors. The IF requires this mismatch to remain visible regardless of its magnitude. This raises strategic questions about system design: why invest in quantum-grade frequency references when environmental sensors dominate? Possible answers include: future sensor upgrades, stability vs. accuracy trade-offs, or applications where traceability matters more than absolute accuracy.

#### 2. Model form agnosticism vs. demonstrated adequacy

The IF does not prescribe functional forms. It requires demonstrated adequacy within stated scope. This permits innovation but creates comparability challenges across implementations using different model forms.

#### 3. Generality vs. wavelength specificity

Standard atmospheric models have stated validity ranges. Operation near molecular absorption features, or outside model validity, requires wavelength-specific framework instances with explicit corrections. Silent extrapolation is prohibited.

#### 4. Local excellence vs. inter-laboratory comparability

A system may achieve excellent internal consistency while remaining difficult to compare across laboratories. Strict adherence to IF-2 decomposition and IF-5 diagnostics is the mechanism for ensuring comparability.

#### 5. Single-species vs. multi-species traceability

Different atomic references have different systematic effects (e.g., sensitivity to electric/magnetic fields, blackbody radiation shifts). The IF requires explicit documentation but does not privilege any species. Future instances may need to become species-specific (e.g., IF-QTR-1762nm-Ba⁺) if species-dependent systematics prove significant.

-----

### VI. Contributor Interface

#### Compliance Declaration (Mandatory)

```
┌─────────────────────────────────────────────────────────┐
│ IF-QTR COMPLIANCE DECLARATION                           │
│                                                         │
│ Framework: IF-QTR v[version]                            │
│ Instance: [IF-QTR-λ or "general"]                       │
│ Principles implemented: [list by IF-n]                  │
│ Principles not applicable: [with justification]         │
│ Departures: [with quantified impact]                    │
│ Evidence: [by principle]                                │
└─────────────────────────────────────────────────────────┘
```

#### Departure Protocol

Any departure from an IF principle must include:

- Principle identifier (e.g., IF-3)
- Nature of departure (what requirement is not met)
- Justification (why departure is necessary or acceptable)
- **Quantified impact:** Signed uncertainty contribution to final n(λ) with stated coverage factor (k), expressed in the same units as the reported uncertainty. If impact cannot be quantified, state “impact unknown; treated as uncharacterised contribution to [layer]” and bound conservatively.

#### Failure Mode Checklist

For stewards and reviewers, the following constitute principle violations:

|Principle|Failure Mode                                                                                                                          |
|---------|--------------------------------------------------------------------------------------------------------------------------------------|
|IF-1     |Missing uncertainty or Type A/B classification at any chain link; undocumented correlations between links                             |
|IF-2     |Collapsed uncertainty layers without decomposition; unreported dominant layer; cross-layer cancellation without covariance modelling  |
|IF-3     |CMR claimed without bandwidth, noise type, or estimator; incompatible methods for σ_single vs. σ_comparative                          |
|IF-4     |Environmental sensor placed outside stated bound without gradient characterisation; undefined measurement volume for complex geometry |
|IF-5     |Model used outside stated domain without re-validation; missing autocorrelation diagnostics; unreported VIF for multi-predictor models|
|IF-6     |Type A and Type B combined without stating correlation; systematic precision misclassified                                            |
|IF-7     |Cross-instance correlations ignored when combining multi-wavelength results                                                           |

-----

### VII. Upgrade Path

**Current status:** Stewardship (v0.3.0)

#### Requirements for v1.0.0

1. At least two independent framework instances validated at spectrally non-adjacent wavelengths (separation > 200 nm)
1. Cross-instance comparison demonstrating IF-2 layer decomposition consistency
1. At least one published, reproducible CMR metric with stated bandwidth, noise type, and estimator (IF-3)
1. External review with no unresolved objections

**Documentation location:** Evidence for upgrade criteria (e.g., cross-instance comparisons, CMR metrics) resides in implementing handbooks and is cited by reference during upgrade review. The IF-QTR itself does not incorporate this evidence.

#### Review Panel Composition (for v1.0.0)

- Minimum two independent metrologists
- At least one reviewer from outside the authorship institution(s)
- Decision rule: Unanimous consent required; if consensus cannot be reached, unresolved objections must be documented and addressed in a subsequent revision before v1.0.0 designation

#### Instance Validation Requirements

- Independent replication demonstrating IF-1 through IF-7 compliance
- Documentation of absorption proximity effects
- Comparison with standard atmospheric models within their validity range
- Temporal reproducibility over at least one diurnal cycle (recommended; shorter periods acceptable with justification)

#### Definition of “Independent Replication”

For v1.0.0 purposes, “independent” means:

- Different apparatus (not merely different measurement runs on the same system), OR
- Same apparatus operated by different personnel with independent data analysis, OR
- Third-party validation of published data using independent analysis code

Same-group measurements on different days or under different conditions do not constitute independent replication unless analysis independence is demonstrated.

-----

### VIII. Terminology (GUM-aligned)

|Term                     |Definition                                                                |Reference           |
|-------------------------|--------------------------------------------------------------------------|--------------------|
|Coverage factor          |Numerical factor k multiplying combined standard uncertainty              |GUM §2.3.6          |
|Expanded uncertainty     |U = k × u_c                                                               |GUM §2.3.5          |
|Type A evaluation        |Uncertainty from statistical analysis                                     |GUM §2.3.2          |
|Type B evaluation        |Uncertainty from other means                                              |GUM §2.3.3          |
|Metrological traceability|Property relating measurement to reference through documented chain       |VIM §2.41           |
|Framework instance       |Wavelength-specific implementation inheriting all IF-QTR principles       |This document       |
|Measurement volume       |Minimum convex hull enclosing optical path during integration period      |This document (IF-4)|
|Non-fungible (layers)    |Cannot be substituted, exchanged, or collapsed without loss of information|This document (IF-2)|
|CMR                      |Common-mode rejection ratio: σ_single / σ_comparative                     |This document (IF-3)|

-----

### IX. Version History

|Version|Date      |Change                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |Authors          |
|-------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|
|0.1.0  |2026-01-20|Initial scaffolding (1762 nm specific)                                                                                                                                                                                                                                                                                                                                                                                                                                             |U. Warring, W. Wu|
|0.1.1  |2026-01-20|Feedback integration; GUM alignment                                                                                                                                                                                                                                                                                                                                                                                                                                                |U. Warring, W. Wu|
|0.2.0  |2026-01-20|Generalised to IF-QTR; instance architecture                                                                                                                                                                                                                                                                                                                                                                                                                                       |U. Warring, W. Wu|
|0.2.1  |2026-01-20|Added: hierarchy rule, Type A/B at links, noise type in IF-3, measurement volume definition, temporal validation, non-adjacent wavelength requirement                                                                                                                                                                                                                                                                                                                              |U. Warring, W. Wu|
|0.2.2  |2026-01-20|Added: external constraints table, complete IF-2/IF-6 tables, IF-3 applicability condition, IF-4 operational proxy, environmental parameter ranges in instance, CMR as mandate, tightened departure language                                                                                                                                                                                                                                                                       |U. Warring, W. Wu|
|0.2.3  |2026-01-20|Added: IF-7 (cross-instance correlation), IF-1 correlation requirement, IF-2 covariance rule and dominance visibility locations, IF-3 comparability clause and interpretive guidance, IF-4 convex hull definition, IF-5 required diagnostics and VIF threshold, IF-6 correlation term and systematic precision guidance, failure mode checklist, review panel composition, independent replication definition, gas composition in instance template, spectroscopic database pinning|U. Warring, W. Wu|
|0.3.0  |2026-02-16|Architectural elevation: removed Appendix A (all numerical values now reside exclusively in implementing handbooks); added architectural separation table and separation rule in Section IV; revised Section V Friction 1 to remove illustrative numerical values; added validation status to info box; added documentation location clause to Section VII                                                                                                                         |U. Warring, W. Wu|

-----

### X. References

1. BIPM, *The International System of Units (SI)*, 9th edition (2019)
1. JCGM 100:2008, *Evaluation of measurement data — Guide to the expression of uncertainty in measurement* (GUM)
1. JCGM 200:2012, *International vocabulary of metrology — Basic and general concepts and associated terms* (VIM)
1. P. E. Ciddor, “Refractive index of air: new equations for the visible and near infrared,” *Appl. Opt.* **35**, 1566–1573 (1996)
1. B. Edlén, “The refractive index of air,” *Metrologia* **2**, 71 (1966)
1. R. J. Mathar, “Refractive index of humid air in the infrared: model fits,” *J. Opt. A* **9**, 470 (2007)
1. I. E. Gordon et al., “The HITRAN2020 molecular spectroscopic database,” *JQSRT* **277**, 107949 (2022)

-----

**End of Document**
