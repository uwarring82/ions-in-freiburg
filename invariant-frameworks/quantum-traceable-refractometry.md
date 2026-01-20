---
description: Set of Principles for Quantum-Traceable Refractive Index Metrology
---

# Quantum-Traceable Refractometry

{% hint style="info" %}
**Authors\*:** Ulrich Warring and Wei Wu\
**Framework ID:** IF-QTR\
**Version:** 0.2.3\
**Status:** Constitutional reference document (stewardship phase)\
**Scope:** Precision refractometry architectures claiming traceability to atomic frequency standards\
**Endorsement Marker:** Local framework under stewardship — no parity implied with BIPM standards or established atmospheric models\
**Lineage:** Metrological systems with environmental coupling\
\
\*_Listed alphabetically. Authors contribute unique perspectives but share responsibility for the complete text._
{% endhint %}

***

### I. Constitutional Status

This document defines boundary conditions for precision refractometry traceable to atomic frequency standards. It is wavelength-agnostic and species-agnostic. It is not a methods paper, protocol, or standard.

#### Binding Rules

1. Every handbook claim affecting traceability, uncertainty, or comparability must cite at least one IF principle by identifier.
2. No handbook procedure may contradict an IF principle.
3. Handbooks must cite IF; IF must never cite handbooks.
4. Wavelength-specific implementations constitute _framework instances_ that inherit all IF-QTR principles.
5. No instance may weaken, relax, or override any IF-QTR principle.

#### Layer Separation

| Layer      | Governs                            | Inheritance                        |
| ---------- | ---------------------------------- | ---------------------------------- |
| IF-QTR     | Constitutional boundary conditions | —                                  |
| IF-QTR-λ   | Wavelength-specific constraints    | Must satisfy all IF-QTR principles |
| Handbook   | Implementation                     | Must satisfy parent instance       |
| Governance | Decisions in context               | Outside IF scope                   |

**Rationale:** Prevents conflation of metrological requirements with engineering choices or wavelength-specific physics (cf. JCGM 200:2012 VIM §2.39–2.41).

***

### II. External Constraints (Citation-Only)

This framework operates within boundaries established elsewhere. These are referenced, not replicated:

| Constraint                    | Source                                     | Role in IF                                           |
| ----------------------------- | ------------------------------------------ | ---------------------------------------------------- |
| SI unit definitions           | BIPM SI Brochure (9th ed.)                 | Defines SI base units and their realisation          |
| Metrological traceability     | JCGM 200:2012 (VIM) §2.41                  | Defines traceability; governs chain requirements     |
| Uncertainty vocabulary        | JCGM 200:2012 (VIM)                        | Defines "precision," "accuracy," "Type A/B"          |
| Uncertainty expression        | JCGM 100:2008 (GUM)                        | Governs coverage factors and expanded uncertainty    |
| Causality and linear response | Kramers-Kronig relations                   | Governs refractive index near absorption features    |
| Spectroscopic data            | HITRAN 2020 (Gordon et al. 2022)           | Provides absorption line positions and intensities   |
| Atmospheric models            | Ciddor (1996), Edlén (1966), Mathar (2007) | Reference models within their stated validity ranges |

**Constraint on constraints:** External constraints are immutable from the perspective of this framework. Any apparent conflict between IF-QTR principles and external constraints shall be resolved in favour of the external constraint, with the conflict documented as a framework limitation.

**Version pinning:** Spectroscopic databases evolve. Instances should pin to a specific database version (e.g., "HITRAN 2020") and document any sensitivity to database updates.

***

### III. Seven Invariant Principles

#### IF-1 — Operational Traceability

**Statement:** A refractive index value n(λ) may only be called traceable to an atomic frequency standard if there exists an explicit, uninterrupted comparison chain from that standard to the reported value, with quantified uncertainty and Type A/B classification at each stage.

**Formal requirement:** The chain must be documentable as:

```
[Atomic reference] → [Frequency transfer] → [Optical transduction] → [Environmental correction] → [Reported n(λ)]
```

Each link requires:

* Standard uncertainty (k = 1), expressed in consistent units (δn or δf/f with documented conversion)
* Classification as Type A or Type B per GUM
* Explicit statement of correlations with adjacent links (independence must be justified, not assumed)

The final reported value must state:

* Combined standard uncertainty (u\_c)
* Coverage factor (k)
* Expanded uncertainty (U = k × u\_c)

The atomic reference may be any species with a documented frequency standard.

**Falsification condition:** Demonstration that a claimed "traceable" measurement lacks documented uncertainty or Type A/B classification at any stage, or that correlations between links are neither stated nor justified.

***

#### IF-2 — Layered Uncertainty Accounting

**Statement:** Uncertainty must be reported in three non-fungible layers:

<table><thead><tr><th width="155.75">Layer</th><th>Symbol</th><th>Content</th><th>Typical sources</th></tr></thead><tbody><tr><td>Frequency</td><td>L_freq</td><td>Atomic reference, frequency transfer, laser stabilisation</td><td>Ion/atom stability, cavity drift, lock bandwidth</td></tr><tr><td>Transduction</td><td>L_trans</td><td>Interferometric or spectroscopic conversion to refractive index</td><td>OPD measurement, fringe counting, ratio determination</td></tr><tr><td>Environmental</td><td>L_env</td><td>T, H, P, composition sensing; spatial and temporal co-location</td><td>Sensor accuracy, calibration drift, gradient effects</td></tr></tbody></table>

**Non-fungibility:** These layers cannot be collapsed into a single number without displaying their decomposition. The layers represent physically distinct contributions that may improve independently as technology advances.

**Cross-layer covariance rule:** Cross-layer cancellation or partial cancellation is not permitted unless covariance terms are explicitly modelled, quantified, and justified. Assumed independence between layers must be stated and defended.

**Dominance transparency:** Where one layer dominates (e.g., L\_env in sensor-limited systems), this dominance is a permanent architectural fact that must remain visible in all derived work. Specifically, dominance must be stated in: (a) the abstract or summary, (b) the results section, and (c) any conclusions regarding achievable accuracy. Reporting only the best-performing layer is a violation.

**Falsification condition:** Demonstration that the three layers cannot be decomposed without materially altering the inference about n(λ), or that cross-layer correlations were assumed away without justification.

***

#### IF-3 — Common-Mode Rejection (where applicable)

**Statement:** Where multi-wavelength operation is employed, the architecture must demonstrably suppress shared-mode noise by comparative measurement. The suppression must be quantified as a dimensionless rejection factor at a stated bandwidth and for a stated noise type.

**Applicability condition:** Multi-wavelength operation is subject to IF-3 if and only if the wavelengths share a common physical path and noise source such that a legitimate ratio-metric comparison is possible. Systems using multiple wavelengths with independent paths or uncorrelated noise sources are not subject to IF-3 but must characterise noise independently under IF-2.

**Formal requirement:** For applicable systems, report:

* CMR = σ\_single / σ\_comparative (dimensionless)
* Measurement bandwidth Δf (Hz) or averaging time τ (s)
* Noise type (white, flicker, random walk, or other with physical justification)
* Estimator used (e.g., Allan deviation, power spectral density, time-domain standard deviation)

**Comparability requirement:** σ\_single and σ\_comparative must be computed using the same estimator, the same bandwidth or averaging time, the same preprocessing, and on datasets of comparable duration and conditions. Cherry-picking favourable conditions for one but not the other invalidates the CMR claim.

**Interpretive guidance (non-binding):**

* CMR < 1 (indicating that dual-wavelength operation increases noise) is implausible for well-designed systems and requires independent verification or explanation.
* CMR > 100 at audio frequencies (1–10 Hz) suggests measurement of a single dominant noise mode rather than broadband system characterisation; the autocorrelation structure or power spectral density should be shown.

**Falsification condition:** Demonstration that comparative measurement fails to yield CMR > 1 at the stated bandwidth and noise type, or that CMR was computed using incompatible methods for single vs. comparative measurements.

***

#### IF-4 — Environmental Co-location

**Statement:** Environmental sensing must be spatially and temporally co-located with the measurement volume. Where practicable, physical co-location is preferred over model-based correction.

**Definitions:**

* _Measurement volume_: The minimum convex hull enclosing the optical path during the integration period of a single data point. For systems with folded or multi-pass geometries, this is the union of convex hulls for each distinct path segment.
* _Measurement volume boundary_: The surface of the measurement volume as defined above.
* _Co-location_: Sensor placement within a stated distance of the measurement volume boundary.

**Operational proxy for complex geometries:** Where the measurement path cannot be uniquely described by a simple volume bounding box (e.g., folded optics, multi-segment interferometers, resonator modes, or stratified environments), an explicit mapping to the relevant optical path segments and their associated environmental gradients must be provided. This mapping must demonstrate that the stated co-location bound applies to each segment, or that segment-specific corrections with quantified uncertainty are applied.

**Formal requirements:**

* Spatial bound: State maximum separation between sensor and measurement volume boundary, with justification (e.g., gradient estimate, prior measurement, or fluid dynamics argument).
* Temporal bound: State synchronisation method and maximum latency.
* If correction is used instead of co-location, its uncertainty must be shown to be subdominant to sensor uncertainty.

**Falsification condition:** Demonstration that spatial or temporal mismatch introduces systematic error exceeding the stated environmental sensor uncertainty, or that the measurement volume definition is ambiguous for the stated geometry.

***

#### IF-5 — Model Transparency and Scope

**Statement:** Any model mapping environmental parameters to refractive index must state:

1. Functional form (e.g., linear, polynomial, physics-based)
2. Input variables and their units
3. Training domain (parameter ranges with explicit bounds)
4. Validation domain (if different from training)
5. Effective sample size N\_eff after autocorrelation correction (for empirical models)
6. Diagnostic tests confirming residuals are consistent with the stated noise model

Outside the stated domain, model-derived claims are invalid. The IF does not prescribe functional form; it requires demonstrated adequacy within scope.

**Required diagnostics:** At minimum, one of the following must be reported:

* Autocorrelation function of residuals, or
* Durbin-Watson statistic, or
* Ljung-Box Q-statistic

with interpretation relative to white-noise null hypothesis. Significant autocorrelation (e.g., Durbin-Watson substantially below 2, or Breusch-Godfrey p < 0.01) must be addressed via HAC standard errors, AR modelling, or equivalent; the chosen remedy must be stated.

**Collinearity diagnostics:** Where multiple environmental parameters are used, variance inflation factor (VIF) or equivalent must be reported. VIF > 10 for any predictor indicates problematic collinearity requiring attention (variable transformation, regularisation, or explicit acknowledgment as a limitation).

**Falsification condition:** Demonstration that the model materially fails within its stated domain, that required diagnostics are absent, or that the model requires ad hoc adjustment to function outside its domain without explicit re-validation.

***

#### IF-6 — Precision–Accuracy Separation

**Statement:** Two quantities must always be reported separately:

| Quantity              | Definition                                      | GUM classification | Typical evaluation method                                                              |
| --------------------- | ----------------------------------------------- | ------------------ | -------------------------------------------------------------------------------------- |
| Residual precision    | Repeatability of measurement or model fit (σ)   | Type A             | Statistical analysis of repeated measurements or fit residuals                         |
| Metrological accuracy | Dominant Type B contribution (systematic floor) | Type B             | Calibration certificates, manufacturer specifications, or independent characterisation |

**Combination rule:** These may only be combined via stated coverage factor (k) to yield expanded uncertainty U = k × u\_c per GUM, where:

u\_c = √(u\_A² + u\_B² + 2·r·u\_A·u\_B)

The correlation coefficient r between Type A and Type B components must be stated. If independence is assumed (r = 0), this must be justified.

**Systematic precision:** Where repeatability is limited by a systematic effect (e.g., drift), this component should be classified as Type B if it arises from a known physical mechanism with bounded magnitude, or Type A if it is measured empirically from repeated measurement cycles. Mixed cases require explicit decomposition.

**Falsification condition:** Demonstration that for a specific measurement class, Type A and Type B contributions cannot be meaningfully separated, or that correlations were assumed away without justification.

***

#### IF-7 — Cross-Instance Correlation (where applicable)

**Statement:** Where multiple framework instances are applied to the same measurement volume during overlapping time intervals (e.g., simultaneous n(λ₁) and n(λ₂) measurements for dispersion characterisation), shared uncertainty contributions must be identified and their correlation structure documented.

**Applicability condition:** IF-7 applies whenever:

* Two or more IF-QTR instances are used on the same physical apparatus, AND
* Measurements occur within temporal windows where environmental conditions are correlated, AND
* Results are combined or compared (e.g., for dispersion, wavelength-dependent systematics, or cross-validation).

**Formal requirement:** For applicable cases, identify:

* Shared components (e.g., common environmental sensors, shared optical geometry, common timing reference)
* Correlation coefficient or covariance for each shared component
* Impact on combined uncertainty when results from multiple instances are used together

**Falsification condition:** Demonstration that cross-instance correlations materially affect combined results but were not documented.

***

### IV. Framework Instances

The general IF-QTR is implemented through wavelength-specific _framework instances_ that inherit all seven principles and add wavelength-specific constraints.

**Inheritance rule:** Instances must satisfy all IF-QTR principles without weakening, relaxing, or overriding any of them. Instances may only add constraints, never remove them.

**Correction rule:** If an instance invokes corrections beyond standard atmospheric models, those corrections must themselves be:

* Falsifiable (with stated test)
* Uncertainty-quantified (with coverage factor)
* Documented with stated validity range

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

1. Proximity to molecular absorption features (H₂O, CO₂, O₂, etc.) — assess and document
2. Validity range of standard atmospheric models at the wavelength
3. Required corrections beyond standard models, with uncertainty
4. Wavelength-specific systematic effects
5. Gas composition assumptions (e.g., CO₂ fixed at 420 ppm, or measured, or modelled from location/season)
6. **Temporal validation requirement:** Demonstrated reproducibility over stated operational timescale (minimum: one diurnal cycle; recommended: multiple environmental regimes). _Note: This is an instance-level validation requirement, not a constitutional gate. Instances may document shorter validation periods with explicit justification._

***

### V. Constructive Frictions

The IF acknowledges the following structural tensions. These are diagnostic, not prescriptive; navigation is left to implementers.

#### 1. Frequency-layer excellence vs. environmental-layer limitations

Current architectures routinely achieve L\_freq ≲ 10⁻¹² but L\_env \~ 10⁻⁷ with commercial sensors. The IF requires this mismatch to remain visible. This raises strategic questions about system design: why invest in quantum-grade frequency references when environmental sensors dominate? Possible answers include: future sensor upgrades, stability vs. accuracy trade-offs, or applications where traceability matters more than absolute accuracy.

#### 2. Model form agnosticism vs. demonstrated adequacy

The IF does not prescribe functional forms. It requires demonstrated adequacy within stated scope. This permits innovation but creates comparability challenges across implementations using different model forms.

#### 3. Generality vs. wavelength specificity

Standard atmospheric models have stated validity ranges. Operation near molecular absorption features, or outside model validity, requires wavelength-specific framework instances with explicit corrections. Silent extrapolation is prohibited.

#### 4. Local excellence vs. inter-laboratory comparability

A system may achieve excellent internal consistency while remaining difficult to compare across laboratories. Strict adherence to IF-2 decomposition and IF-5 diagnostics is the mechanism for ensuring comparability.

#### 5. Single-species vs. multi-species traceability

Different atomic references have different systematic effects (e.g., sensitivity to electric/magnetic fields, blackbody radiation shifts). The IF requires explicit documentation but does not privilege any species. Future instances may need to become species-specific (e.g., IF-QTR-1762nm-Ba⁺) if species-dependent systematics prove significant.

***

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

* Principle identifier (e.g., IF-3)
* Nature of departure (what requirement is not met)
* Justification (why departure is necessary or acceptable)
* **Quantified impact:** Signed uncertainty contribution to final n(λ) with stated coverage factor (k), expressed in the same units as the reported uncertainty. If impact cannot be quantified, state "impact unknown; treated as uncharacterised contribution to \[layer]" and bound conservatively.

#### Failure Mode Checklist

For stewards and reviewers, the following constitute principle violations:

| Principle | Failure Mode                                                                                                                           |
| --------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| IF-1      | Missing uncertainty or Type A/B classification at any chain link; undocumented correlations between links                              |
| IF-2      | Collapsed uncertainty layers without decomposition; unreported dominant layer; cross-layer cancellation without covariance modelling   |
| IF-3      | CMR claimed without bandwidth, noise type, or estimator; incompatible methods for σ\_single vs. σ\_comparative                         |
| IF-4      | Environmental sensor placed outside stated bound without gradient characterisation; undefined measurement volume for complex geometry  |
| IF-5      | Model used outside stated domain without re-validation; missing autocorrelation diagnostics; unreported VIF for multi-predictor models |
| IF-6      | Type A and Type B combined without stating correlation; systematic precision misclassified                                             |
| IF-7      | Cross-instance correlations ignored when combining multi-wavelength results                                                            |

***

### VII. Upgrade Path

**Current status:** Stewardship (v0.2.3)

#### Requirements for v1.0.0

1. At least two independent framework instances validated at spectrally non-adjacent wavelengths (separation > 200 nm)
2. Cross-instance comparison demonstrating IF-2 layer decomposition consistency
3. At least one published, reproducible CMR metric with stated bandwidth, noise type, and estimator (IF-3)
4. External review with no unresolved objections

#### Review Panel Composition (for v1.0.0)

* Minimum two independent metrologists
* At least one reviewer from outside the authorship institution(s)
* Decision rule: Unanimous consent required; if consensus cannot be reached, unresolved objections must be documented and addressed in a subsequent revision before v1.0.0 designation

#### Instance Validation Requirements

* Independent replication demonstrating IF-1 through IF-7 compliance
* Documentation of absorption proximity effects
* Comparison with standard atmospheric models within their validity range
* Temporal reproducibility over at least one diurnal cycle (recommended; shorter periods acceptable with justification)

#### Definition of "Independent Replication"

For v1.0.0 purposes, "independent" means:

* Different apparatus (not merely different measurement runs on the same system), OR
* Same apparatus operated by different personnel with independent data analysis, OR
* Third-party validation of published data using independent analysis code

Same-group measurements on different days or under different conditions do not constitute independent replication unless analysis independence is demonstrated.

***

### VIII. Terminology (GUM-aligned)

| Term                      | Definition                                                                 | Reference            |
| ------------------------- | -------------------------------------------------------------------------- | -------------------- |
| Coverage factor           | Numerical factor k multiplying combined standard uncertainty               | GUM §2.3.6           |
| Expanded uncertainty      | U = k × u\_c                                                               | GUM §2.3.5           |
| Type A evaluation         | Uncertainty from statistical analysis                                      | GUM §2.3.2           |
| Type B evaluation         | Uncertainty from other means                                               | GUM §2.3.3           |
| Metrological traceability | Property relating measurement to reference through documented chain        | VIM §2.41            |
| Framework instance        | Wavelength-specific implementation inheriting all IF-QTR principles        | This document        |
| Measurement volume        | Minimum convex hull enclosing optical path during integration period       | This document (IF-4) |
| Non-fungible (layers)     | Cannot be substituted, exchanged, or collapsed without loss of information | This document (IF-2) |
| CMR                       | Common-mode rejection ratio: σ\_single / σ\_comparative                    | This document (IF-3) |

***

### IX. Version History

| Version | Date       | Change                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | Authors           |
| ------- | ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------- |
| 0.1.0   | 2026-01-20 | Initial scaffolding (1762 nm specific)                                                                                                                                                                                                                                                                                                                                                                                                                                              | U. Warring, W. Wu |
| 0.1.1   | 2026-01-20 | Feedback integration; GUM alignment                                                                                                                                                                                                                                                                                                                                                                                                                                                 | U. Warring, W. Wu |
| 0.2.0   | 2026-01-20 | Generalised to IF-QTR; instance architecture                                                                                                                                                                                                                                                                                                                                                                                                                                        | U. Warring, W. Wu |
| 0.2.1   | 2026-01-20 | Added: hierarchy rule, Type A/B at links, noise type in IF-3, measurement volume definition, temporal validation, non-adjacent wavelength requirement                                                                                                                                                                                                                                                                                                                               | U. Warring, W. Wu |
| 0.2.2   | 2026-01-20 | Added: external constraints table, complete IF-2/IF-6 tables, IF-3 applicability condition, IF-4 operational proxy, environmental parameter ranges in instance, CMR as mandate, tightened departure language                                                                                                                                                                                                                                                                        | U. Warring, W. Wu |
| 0.2.3   | 2026-01-20 | Added: IF-7 (cross-instance correlation), IF-1 correlation requirement, IF-2 covariance rule and dominance visibility locations, IF-3 comparability clause and interpretive guidance, IF-4 convex hull definition, IF-5 required diagnostics and VIF threshold, IF-6 correlation term and systematic precision guidance, failure mode checklist, review panel composition, independent replication definition, gas composition in instance template, spectroscopic database pinning | U. Warring, W. Wu |

***

### X. References

1. BIPM, _The International System of Units (SI)_, 9th edition (2019)
2. JCGM 100:2008, _Evaluation of measurement data — Guide to the expression of uncertainty in measurement_ (GUM)
3. JCGM 200:2012, _International vocabulary of metrology — Basic and general concepts and associated terms_ (VIM)
4. P. E. Ciddor, "Refractive index of air: new equations for the visible and near infrared," _Appl. Opt._ **35**, 1566–1573 (1996)
5. B. Edlén, "The refractive index of air," _Metrologia_ **2**, 71 (1966)
6. R. J. Mathar, "Refractive index of humid air in the infrared: model fits," _J. Opt. A_ **9**, 470 (2007)
7. I. E. Gordon et al., "The HITRAN2020 molecular spectroscopic database," _JQSRT_ **277**, 107949 (2022)

***

## Appendix A: Framework Instance IF-QTR-1762nm

**Instance ID:** IF-QTR-1762nm\
**Version:** 0.1.2\
**Parent Framework:** IF-QTR v0.2.3\
**Status:** Reference implementation (stewardship phase)

***

### A.1 Instance Declaration

```
┌─────────────────────────────────────────────────────────┐
│ FRAMEWORK INSTANCE DECLARATION                          │
│                                                         │
│ Instance ID: IF-QTR-1762nm                              │
│ Parent: IF-QTR v0.2.3                                   │
│ Wavelength scope: 1762 ± 1 nm                           │
│ Atomic reference: ¹³⁸Ba⁺ (S₁/₂ → D₅/₂, 1762.115 nm)    │
│ Absorption proximity: H₂O at 1761.04 nm, 1762.49 nm    │
│ Standard model validity: Outside Ciddor/Edlén range    │
│   (> 1760 nm); Mathar partially applicable             │
│ Gas composition: CO₂ assumed fixed at 420 ppm;         │
│   H₂O measured via RH sensor                           │
│ Required corrections: Kramers-Kronig humidity          │
│   enhancement relative to standard models              │
│ Temporal validation: ≥ 1 diurnal cycle required        │
│ Spectroscopic database: HITRAN 2020                    │
└─────────────────────────────────────────────────────────┘
```

***

### A.2 Wavelength-Specific Context

#### A.2.1 Atomic Reference

The ¹³⁸Ba⁺ ion provides a frequency reference via the S₁/₂ → D₅/₂ electric quadrupole transition at 1762.115 nm. This transition is:

* Narrow linewidth (< 1 Hz natural linewidth)
* Suitable for optical frequency standards
* Directly relevant to barium-ion quantum network architectures

**Species-specific considerations:** The electric quadrupole transition has different systematic sensitivities than dipole-allowed transitions (e.g., different tensor polarisabilities, different sensitivity to electric field gradients). These effects are subdominant to L\_env in the current implementation but may become relevant if environmental sensing improves.

#### A.2.2 Absorption Proximity

The 1762 nm wavelength lies between two H₂O absorption lines (HITRAN 2020):

* 1761.0405 nm
* 1762.4852 nm

This proximity induces anomalous dispersion via Kramers-Kronig relations, resulting in enhanced humidity sensitivity compared to standard atmospheric models.

#### A.2.3 Standard Model Limitations

| Model         | Stated validity range      | Status at 1762 nm                          |
| ------------- | -------------------------- | ------------------------------------------ |
| Ciddor (1996) | 300–1700 nm                | Outside stated range                       |
| Edlén (1966)  | Visible (\~400–700 nm)     | Outside stated range                       |
| Mathar (2007) | Extended IR (to \~2000 nm) | Within range; requires humidity correction |

***

### A.3 Instance-Specific Constraints

#### A.3.1 Humidity Coefficient Correction

**Measured values:**

| Source                    | ∂n/∂H (× 10⁻⁸ %⁻¹) | Notes                            |
| ------------------------- | ------------------ | -------------------------------- |
| This work (observed)      | −1.780 ± 0.004     | Empirical fit, HAC SE            |
| Kramers-Kronig prediction | −1.772             | First-principles calculation     |
| Mathar (2007)             | −1.653             | Model value at 1762 nm           |
| Ciddor (1996)             | −1.537             | Extrapolated beyond stated range |
| Edlén (1966)              | −1.526             | Extrapolated beyond stated range |

**Enhancement relative to standard models:**

| Reference model | Enhancement   | Calculation                    |
| --------------- | ------------- | ------------------------------ |
| Ciddor          | (15.8 ± 0.3)% | (1.780 − 1.537) / 1.537 × 100% |
| Edlén           | (16.6 ± 0.3)% | (1.780 − 1.526) / 1.526 × 100% |
| Mathar          | (7.7 ± 0.3)%  | (1.780 − 1.653) / 1.653 × 100% |

**Summary:** The observed humidity coefficient shows \~16% enhancement relative to Ciddor/Edlén (which are extrapolated beyond their validity range) and \~8% enhancement relative to Mathar (which is within its stated range but does not fully account for Kramers-Kronig effects near H₂O absorption).

**Required action:** Any handbook implementing IF-QTR-1762nm must apply a humidity coefficient correction. The recommended approach is to use the Kramers-Kronig-derived value (−1.772 × 10⁻⁸ %⁻¹) or the empirically measured value (−1.780 × 10⁻⁸ %⁻¹). Use of uncorrected Ciddor, Edlén, or Mathar values constitutes a departure requiring documentation under Section VI of the parent framework, with quantified impact on final n(λ).

#### A.3.2 Environmental Parameter Ranges

The empirical model underlying this instance was validated over the following ranges:

| Parameter         | Symbol | Training range | Validation range | Unit |
| ----------------- | ------ | -------------- | ---------------- | ---- |
| Temperature       | T      | 15–35          | 15–35            | °C   |
| Relative humidity | H      | 20–45          | 20–45            | %RH  |
| Pressure          | P      | 965–1000       | 965–1000         | hPa  |

**Justification:** These ranges represent typical laboratory conditions in a temperate climate with seasonal variation. The training and validation domains are identical, indicating that model performance has been assessed across the full stated range.

**Constraint:** Claims of n(1762 nm) accuracy outside these ranges require re-validation with appropriate data or explicit departure documentation with quantified impact.

#### A.3.3 Temporal Validation

**Instance requirement:** Demonstrated reproducibility over ≥ 1 diurnal cycle, with data spanning at least two distinct environmental regimes (e.g., day/night, or different weather conditions).

**Observed campaign results (reference implementation):**

| Metric                                | Value   |
| ------------------------------------- | ------- |
| Campaign duration                     | 15 days |
| Training measurements                 | 89,106  |
| Validation measurements               | 46,999  |
| Effective sample size (N\_eff)        | 35,100  |
| Autocorrelation coefficient (AR(1) ρ) | 0.435   |
| Diurnal cycles covered                | > 10    |
| Distinct weather regimes              | ≥ 3     |

**Note:** The 15-day campaign exceeds the minimum instance requirement. Future implementations need only demonstrate ≥ 1 diurnal cycle with ≥ 2 environmental regimes, though longer campaigns increase confidence in model stability.

***

### A.4 Compliance with Parent Principles

#### IF-1 Compliance: Operational Traceability

**Traceability chain:**

All uncertainties expressed as standard uncertainties (k = 1). Conversions between δf/f and δn use the relation δn ≈ (n−1) × δf/f, documented in the implementing handbook.

| Link | Component                      | Uncertainty (δn)        | Type  | Correlation with adjacent                           |
| ---- | ------------------------------ | ----------------------- | ----- | --------------------------------------------------- |
| 1    | ¹³⁸Ba⁺ ion frequency           | \~10⁻¹⁵ × (n−1) ≈ 10⁻¹⁹ | B     | Independent (atomic property)                       |
| 2    | ULE cavity transfer            | \~10⁻¹²                 | B     | Correlated with Link 3 (shared thermal environment) |
| 3    | 1762 nm laser lock             | \~10⁻¹²                 | B     | Correlated with Link 2                              |
| 4    | Dual-λ interferometer          | \~10⁻¹⁰                 | A + B | Independent (different physical mechanism)          |
| 5    | Environmental sensing (BME280) | 2.12 × 10⁻⁷             | B     | Independent                                         |
| 6    | Statistical model              | 1.2 × 10⁻⁹              | A     | Independent                                         |

**Final reported uncertainty:**

* Combined standard uncertainty: u\_c ≈ 2.12 × 10⁻⁷ (dominated by Link 5)
* Coverage factor: k = 2
* Expanded uncertainty: U = 4.24 × 10⁻⁷

**Chain completeness:** All links documented with uncertainty, Type classification, and correlation status. ✓

#### IF-2 Compliance: Layered Uncertainty

| Layer         | Symbol   | Value       | Dominant? | Primary source               |
| ------------- | -------- | ----------- | --------- | ---------------------------- |
| Frequency     | L\_freq  | \~10⁻¹²     | No        | ULE cavity drift             |
| Transduction  | L\_trans | \~10⁻¹⁰     | No        | Fringe counting resolution   |
| Environmental | L\_env   | 2.12 × 10⁻⁷ | **Yes**   | BME280 sensor specifications |

**Cross-layer correlations:** Layers are treated as independent. Justification: L\_freq and L\_trans arise from optical/electronic systems; L\_env arises from atmospheric sensing with separate transduction pathway. No physical mechanism for correlation identified.

**Dominance visibility:**

* Abstract: "accuracy limited by environmental sensing (δn \~ 2 × 10⁻⁷)"
* Results: Table III shows layered decomposition
* Conclusions: "BME280 uncertainty dominates error budget"

✓ IF-2 satisfied.

#### IF-3 Compliance: Common-Mode Rejection

**Applicability assessment:** This implementation uses dual-wavelength operation (780 nm reference, 1762 nm probe) with a shared 4.2 m optical path. The wavelengths traverse identical mechanical and atmospheric perturbations, satisfying the IF-3 applicability condition.

| Parameter               | Value                           | Status          |
| ----------------------- | ------------------------------- | --------------- |
| Reference wavelength    | 780 nm (⁸⁷Rb-stabilised)        | Documented      |
| Probe wavelength        | 1762 nm (¹³⁸Ba⁺/ULE-stabilised) | Documented      |
| Optical path difference | 4.2 m                           | Documented      |
| Shared physical path    | Yes                             | IF-3 applicable |

**Mandate:** This instance requires that any implementing handbook reports a CMR metric computed as follows:

* Estimator: \[to be specified by handbook]
* Bandwidth/averaging time: \[to be specified by handbook]
* Noise type: \[to be characterised by handbook]
* σ\_single and σ\_comparative computed using identical methods

**Current status:** CMR not yet quantified. This is a documented departure (see A.8).

#### IF-4 Compliance: Environmental Co-location

| Parameter                | Value                          | Justification                                                         |
| ------------------------ | ------------------------------ | --------------------------------------------------------------------- |
| Sensor type              | BME280                         | Commercial environmental sensor                                       |
| Spatial bound            | < 10 cm from beam path         | Laboratory with forced-air circulation; gradients < 0.1 °C/m measured |
| Temporal synchronisation | GPS-disciplined, 1 Hz sampling | Common timebase for all measurements                                  |
| Maximum latency          | < 1 s                          | Sensor response time                                                  |

**Geometry:** Single linear beam path (4.2 m); measurement volume is a cylinder of \~1 cm diameter × 4.2 m length. Convex hull is well-defined. No segment-specific corrections required. ✓

#### IF-5 Compliance: Model Transparency

| Requirement                | Status | Value/Evidence                             |
| -------------------------- | ------ | ------------------------------------------ |
| Functional form            | ✓      | Linear: n = α₀ + α\_T T + α\_H H + α\_P P  |
| Input variables            | ✓      | T (°C), H (%RH), P (hPa)                   |
| Training domain            | ✓      | T: 15–35 °C, H: 20–45 %RH, P: 965–1000 hPa |
| Validation domain          | ✓      | Same as training                           |
| N\_eff                     | ✓      | 35,100 (AR(1) ρ = 0.435)                   |
| Autocorrelation diagnostic | ✓      | DW = 1.13; BG LM = 29,735 (p < 0.001)      |
| Collinearity diagnostic    | ✓      | VIF < 2.1 for all predictors               |

**Interpretation of diagnostics:**

* Durbin-Watson = 1.13 (below 2) and Breusch-Godfrey LM = 29,735 with p < 0.001 indicate strong positive autocorrelation in residuals at the raw sample rate (N = 89,106).
* This is expected for environmental time series and is addressed via HAC standard errors with lag selection 18–37, which inflates standard errors appropriately.
* Effective sample size N\_eff ≈ 35,100 (60% reduction from nominal) reflects the autocorrelation structure.
* VIF < 2.1 indicates no problematic collinearity among T, H, P predictors.

**Linearity justification:** Higher-order terms (T², H², TH, etc.) were tested; contribution to residual variance < 10⁻⁹. Linear form adequate within stated domain.

#### IF-6 Compliance: Precision–Accuracy Separation

| Quantity                             | Source         | Value       | Type | Evaluation method                          |
| ------------------------------------ | -------------- | ----------- | ---- | ------------------------------------------ |
| Residual precision (σ)               | Model fit      | 1.2 × 10⁻⁹  | A    | Standard deviation of fit residuals        |
| Metrological accuracy                | BME280 suite   | 2.12 × 10⁻⁷ | B    | Propagated manufacturer specifications     |
| Correlation (r)                      | —              | 0 (assumed) | —    | No mechanism identified; see justification |
| Combined standard uncertainty (u\_c) | Quadrature sum | 2.12 × 10⁻⁷ | —    | √(σ² + u\_B²) ≈ u\_B                       |
| Expanded uncertainty (U, k=2)        | —              | 4.24 × 10⁻⁷ | —    | 2 × u\_c                                   |

**Correlation justification:** Type A (fit residuals) and Type B (sensor specifications) arise from independent sources: fit residuals reflect unmodelled atmospheric variation and measurement noise; sensor specifications reflect calibration uncertainty. No physical mechanism couples these, so r = 0 is assumed.

**Separation demonstrated:** Type A and Type B contributions reported independently with combination method and correlation assumption stated. ✓

#### IF-7 Compliance: Cross-Instance Correlation

**Applicability:** Currently only one instance (IF-QTR-1762nm) is validated. IF-7 will become applicable when a second instance (e.g., IF-QTR-780nm) is developed and measurements are combined.

**Anticipated shared components for future cross-instance work:**

* Environmental sensors (same BME280 unit)
* Optical geometry (same 4.2 m path)
* Timing reference (same GPS-disciplined oscillator)

These will require explicit correlation modelling when IF-7 becomes applicable.

***

### A.5 Refractive Index Coefficients

Empirically determined coefficients for n(T, H, P) at 1762 nm:

| Coefficient        | Value         | HAC SE       | Unit  | Physical interpretation                               |
| ------------------ | ------------- | ------------ | ----- | ----------------------------------------------------- |
| α₀ (constant)      | 1.000027      | 3.03 × 10⁻⁷  | —     | Baseline refractive index                             |
| α\_T (temperature) | −8.940 × 10⁻⁷ | 4.47 × 10⁻¹⁰ | °C⁻¹  | Thermal density effect                                |
| α\_H (humidity)    | −1.780 × 10⁻⁸ | 4.13 × 10⁻¹⁰ | %⁻¹   | Water vapour displacement + Kramers-Kronig dispersion |
| α\_P (pressure)    | +2.569 × 10⁻⁷ | 2.99 × 10⁻¹² | hPa⁻¹ | Pressure-density relationship                         |

**Model fit quality:** R² = 0.996

**Standard errors:** Heteroskedasticity and Autocorrelation Consistent (HAC) with Newey-West kernel, lag selection 18–37 based on sample size and autocorrelation structure.

***

### A.6 Limitations and Improvement Pathways

#### Current Limitations

1. **Environmental sensing (L\_env dominance):** BME280 uncertainty (2.12 × 10⁻⁷) dominates error budget by \~5 orders of magnitude over frequency layer. This is a permanent architectural constraint at current sensor technology.
2. **Sensor calibration:** Initial functionality verification performed; comprehensive metrological calibration against transfer standards not implemented. Drift over 15-day campaign not independently assessed.
3. **Environmental range:** Model validated over limited range (laboratory conditions); extrapolation to outdoor or extreme conditions prohibited without re-validation.
4. **CMR characterisation:** Common-mode rejection metric not yet quantified with stated estimator, bandwidth, and noise type.
5. **CO₂ assumption:** CO₂ concentration assumed fixed at 420 ppm; not measured. Seasonal/diurnal variation in CO₂ (\~20 ppm) contributes \~10⁻⁹ to n uncertainty, subdominant to L\_env but potentially relevant for future higher-accuracy implementations.

#### Improvement Pathways

| Pathway                    | Target                             | Impact on L\_env           | Estimated effort |
| -------------------------- | ---------------------------------- | -------------------------- | ---------------- |
| Metrology-grade hygrometry | Chilled-mirror, δRH < 0.5%         | Reduce to \~10⁻⁸           | Medium           |
| Calibrated thermometry     | Pt100 with δT < 0.1 °C             | Reduce to \~10⁻⁷           | Low              |
| Extended validation        | Outdoor conditions, seasonal range | Broader applicability      | High             |
| CMR measurement            | Allan deviation at multiple τ      | Quantified noise rejection | Low              |
| CO₂ sensing                | NDIR sensor, δCO₂ < 10 ppm         | Remove assumption          | Low              |

***

### A.7 Instance Version History

| Version | Date       | Change                                                                                                                                                                                                                                                                                            | Authors           |
| ------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------- |
| 0.1.0   | 2026-01-20 | Initial instance based on 15-day validation campaign                                                                                                                                                                                                                                              | U. Warring, W. Wu |
| 0.1.1   | 2026-01-20 | Corrected enhancement factor presentation; partitioned temporal validation; populated environmental ranges; CMR expressed as mandate; expanded IF-6 compliance table                                                                                                                              | U. Warring, W. Wu |
| 0.1.2   | 2026-01-20 | Added: IF-1 correlation status for all links; IF-2 cross-layer correlation justification and dominance visibility locations; IF-5 diagnostic interpretation; IF-6 correlation justification; IF-7 anticipated shared components; gas composition assumption; CO₂ limitation; unit conversion note | U. Warring, W. Wu |

***

### A.8 Reference Handbook

The implementing handbook for this instance is:

> W. Wu and U. Warring, "Precision Refractive Index Measurement at 1762 nm," Technical Report, University of Freiburg (IN PREPARATION)

**Compliance declaration for reference handbook:**

```
┌─────────────────────────────────────────────────────────┐
│ IF-QTR COMPLIANCE DECLARATION                           │
│                                                         │
│ Framework: IF-QTR v0.2.3                                │
│ Instance: IF-QTR-1762nm v0.1.2                          │
│ Principles implemented: IF-1, IF-2, IF-4, IF-5, IF-6   │
│ Principles not applicable: IF-7 (single instance)       │
│ Departures:                                             │
│   IF-3: CMR metric not yet reported.                   │
│     Nature: σ_single and σ_comparative not measured.   │
│     Justification: Dual-wavelength operation verified  │
│       functional; quantitative CMR deferred to next    │
│       measurement campaign.                            │
│     Impact: Noise rejection contribution to L_trans    │
│       uncharacterised. Conservative bound: IF CMR = 1  │
│       (no rejection), single-wavelength noise would    │
│       contribute ~10⁻⁹ to L_trans, subdominant to      │
│       L_env by ~2 orders of magnitude. Stated as       │
│       bound, not measurement; k = 1.                   │
│ Evidence:                                               │
│   IF-1: Section A.4, traceability chain table          │
│   IF-2: Section A.4, layered uncertainty table         │
│   IF-4: Section A.4, co-location table                 │
│   IF-5: Section A.4, model transparency table          │
│   IF-6: Section A.4, precision-accuracy table          │
└─────────────────────────────────────────────────────────┘
```

***

**End of Document**
