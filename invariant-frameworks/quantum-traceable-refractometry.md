---
description: Set of Principles for Quantum-Traceable Refractive Index Metrology
---

# Quantum-Traceable Refractometry

{% hint style="info" %}
**Authors\*:** U. Warring and W. Wu\
**Affiliation:** Institute of Physics, University of Freiburg\
**Framework ID:** IF-QTR\
**Version:** 0.2.1\
**Status:** Constitutional reference document (stewardship phase)\
**Scope:** Precision refractometry architectures claiming traceability to atomic frequency standards\
**Endorsement Marker:** Local framework under stewardship — no parity implied with BIPM standards or established atmospheric models\
**Lineage:** Metrological systems with environmental coupling\
\
&#xNAN;_\*Listed alphabetically. Authors contribute unique perspectives, but commonly share responsibility for the complete text._
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

| Constraint                    | Source                       | Role in IF                                           |
| ----------------------------- | ---------------------------- | ---------------------------------------------------- |
| SI unit definitions           | BIPM SI Brochure (9th ed.)   | Defines "traceability"                               |
| Uncertainty vocabulary        | JCGM 200:2012 (VIM)          | Defines "precision," "accuracy," "Type A/B"          |
| Uncertainty expression        | JCGM 100:2008 (GUM)          | Governs coverage factors and expanded uncertainty    |
| Causality and linear response | Kramers-Kronig relations     | Governs refractive index near absorption features    |
| Spectroscopic data            | HITRAN, GEISA, or equivalent | Provides absorption line positions                   |
| Atmospheric models            | Ciddor, Edlén, Mathar        | Reference models within their stated validity ranges |

***

### III. Six Invariant Principles

#### IF-1 — Operational Traceability

**Statement:** A refractive index value n(λ) may only be called traceable to an atomic frequency standard if there exists an explicit, uninterrupted comparison chain from that standard to the reported value, with quantified uncertainty, stated coverage factor (k), and Type A/B classification at each stage.

**Formal requirement:** The chain must be documentable as:

```
[Atomic reference] → [Frequency transfer] → [Optical transduction] → [Environmental correction] → [Reported n(λ)]
```

Each link requires:

* Stated uncertainty contribution
* Coverage factor (k)
* Classification as Type A or Type B per GUM

The atomic reference may be any species with a documented frequency standard.

**Falsification condition:** Demonstration that a claimed "traceable" measurement lacks documented uncertainty, coverage factor, or Type A/B classification at any stage.

***

#### IF-2 — Layered Uncertainty Accounting

**Statement:** Uncertainty must be reported in three non-fungible layers:

| Layer    | Symbol        | Content                                                         |
| -------- | ------------- | --------------------------------------------------------------- |
| L\_freq  | Frequency     | Atomic reference, frequency transfer, laser stabilisation       |
| L\_trans | Transduction  | Interferometric or spectroscopic conversion to refractive index |
| L\_env   | Environmental | T, H, P, composition sensing; spatial and temporal co-location  |

These layers cannot be collapsed into a single number without displaying their decomposition. Where one layer dominates, this dominance is a permanent architectural fact that must remain visible in all derived work.

**Falsification condition:** Demonstration that the three layers cannot be decomposed without materially altering the inference about n(λ) for a specific measurement architecture.

***

#### IF-3 — Common-Mode Rejection (where applicable)

**Statement:** Where multi-wavelength operation is employed, the architecture must demonstrably suppress shared-mode noise by comparative measurement. The suppression must be quantified as a dimensionless rejection factor at a stated bandwidth and for a stated noise type.

**Formal requirement:** Report:

* CMR = σ\_single / σ\_comparative
* Measurement bandwidth Δf
* Noise type (white, flicker, random walk, or other with justification)

**Scope limitation:** This principle applies only to architectures employing wavelength comparison. Single-wavelength systems must demonstrate noise characterisation by alternative means under IF-2.

**Falsification condition:** Demonstration that comparative measurement fails to yield CMR > 1 at the stated bandwidth and noise type, or that CMR cannot be quantified from available data.

***

#### IF-4 — Environmental Co-location

**Statement:** Environmental sensing must be spatially and temporally co-located with the measurement volume. Where practicable, physical co-location is preferred over model-based correction.

**Definitions:**

* _Measurement volume_: The spatial region through which the optical path traverses during the integration period of a single data point.
* _Co-location_: Sensor placement within a stated distance of the measurement volume boundary.

**Formal requirements:**

* Spatial bound: State maximum separation between sensor and measurement volume boundary, with justification (e.g., gradient estimate or prior measurement).
* Temporal bound: State synchronisation method and maximum latency.
* If correction is used instead of co-location, its uncertainty must be shown to be subdominant to sensor uncertainty.

**Falsification condition:** Demonstration that spatial or temporal mismatch introduces systematic error exceeding the stated environmental sensor uncertainty.

***

#### IF-5 — Model Transparency and Scope

**Statement:** Any model mapping environmental parameters to refractive index must state:

1. Functional form
2. Input variables and their units
3. Training domain (parameter ranges)
4. Validation domain (if different)
5. Effective sample size N\_eff after autocorrelation correction (for empirical models)
6. Diagnostic tests confirming residuals are consistent with the stated noise model

Outside the stated domain, model-derived claims are invalid. The IF does not prescribe functional form; it requires demonstrated adequacy within scope.

**Soft expectation:** Where multiple environmental parameters are used, model identifiability should be assessed (e.g., via variance inflation factor or equivalent).

**Falsification condition:** Demonstration that the model materially fails within its stated domain, or requires ad hoc adjustment to function outside it without explicit re-validation.

***

#### IF-6 — Precision–Accuracy Separation

**Statement:** Two quantities must always be reported separately:

| Quantity              | Definition                                      | GUM classification |
| --------------------- | ----------------------------------------------- | ------------------ |
| Residual precision    | Repeatability of measurement or fit (σ)         | Type A             |
| Metrological accuracy | Dominant Type B contribution (systematic floor) | Type B             |

These may only be combined via stated coverage factor (k) to yield expanded uncertainty U = k × u\_c per GUM.

**Falsification condition:** Demonstration that for a specific measurement class, Type A and Type B contributions cannot be meaningfully separated.

***

### IV. Framework Instances

The general IF-QTR is implemented through wavelength-specific _framework instances_ that inherit all six principles and add wavelength-specific constraints.

**Inheritance rule:** Instances must satisfy all IF-QTR principles without weakening, relaxing, or overriding any of them. Instances may only add constraints, never remove them.

**Correction rule:** If an instance invokes corrections beyond standard atmospheric models, those corrections must themselves be falsifiable, uncertainty-quantified, and documented with stated validity range.

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
│ Required corrections: [with uncertainty]                │
│ Temporal validation: [reproducibility timescale]        │
└─────────────────────────────────────────────────────────┘
```

#### Instance-Specific Requirements

1. Proximity to molecular absorption features (H₂O, CO₂, O₂, etc.) — assess and document
2. Validity range of standard atmospheric models at the wavelength
3. Required corrections beyond standard models, with uncertainty
4. Wavelength-specific systematic effects
5. Temporal validation: Demonstrated reproducibility over stated operational timescale (minimum: one diurnal cycle; recommended: multiple environmental regimes)

***

### V. Constructive Frictions

The IF acknowledges the following structural tensions:

#### 1. Frequency-layer excellence vs. environmental-layer limitations

Current architectures routinely achieve L\_freq ≲ 10⁻¹² but L\_env \~ 10⁻⁷ with commercial sensors. The IF requires this mismatch to remain visible.

#### 2. Model form agnosticism vs. demonstrated adequacy

The IF does not prescribe functional forms. It requires demonstrated adequacy within stated scope.

#### 3. Generality vs. wavelength specificity

Standard atmospheric models have stated validity ranges. Operation near molecular absorption features, or outside model validity, requires wavelength-specific framework instances with explicit corrections. Silent extrapolation is prohibited.

#### 4. Local excellence vs. inter-laboratory comparability

A system may achieve excellent internal consistency while remaining difficult to compare across laboratories. Strict adherence to IF-2 decomposition and IF-5 diagnostics is the mechanism for ensuring comparability.

#### 5. Single-species vs. multi-species traceability

Different atomic references have different systematic effects. The IF requires explicit documentation but does not privilege any species.

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
│ Departures: [with quantified impact on n(λ)]            │
│ Evidence: [by principle]                                │
└─────────────────────────────────────────────────────────┘
```

#### Departure Protocol

Any departure must include:

* Principle identifier
* Nature of departure
* Justification
* Quantified impact on final n(λ) (order of magnitude minimum)

***

### VII. Upgrade Path

**Current status:** Stewardship (v0.2.1)

#### Requirements for v1.0.0

1. At least two independent framework instances validated at spectrally non-adjacent wavelengths (separation > 200 nm)
2. Cross-instance comparison demonstrating IF-2 layer decomposition consistency
3. At least one published, reproducible CMR metric with stated bandwidth and noise model (IF-3)
4. External review with no unresolved objections

#### Instance Validation Requirements

* Independent replication demonstrating IF-1 through IF-6 compliance
* Documentation of absorption proximity effects
* Comparison with standard atmospheric models within their validity range
* Temporal reproducibility over at least one diurnal cycle

***

### VIII. Terminology (GUM-aligned)

| Term                      | Definition                                                          | Reference            |
| ------------------------- | ------------------------------------------------------------------- | -------------------- |
| Coverage factor           | Numerical factor k multiplying combined standard uncertainty        | GUM §2.3.6           |
| Expanded uncertainty      | U = k × u\_c                                                        | GUM §2.3.5           |
| Type A evaluation         | Uncertainty from statistical analysis                               | GUM §2.3.2           |
| Type B evaluation         | Uncertainty from other means                                        | GUM §2.3.3           |
| Metrological traceability | Property relating measurement to reference through documented chain | VIM §2.41            |
| Framework instance        | Wavelength-specific implementation inheriting all IF-QTR principles | This document        |
| Measurement volume        | Spatial region traversed by optical path during integration period  | This document (IF-4) |

***

### IX. Version History

| Version | Date       | Change                                                                                                                                                    | Authors           |
| ------- | ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------- |
| 0.1.0   | 2026-01-20 | Initial scaffolding (1762 nm specific)                                                                                                                    | U. Warring, W. Wu |
| 0.1.1   | 2026-01-20 | Feedback integration; GUM alignment                                                                                                                       | U. Warring, W. Wu |
| 0.2.0   | 2026-01-20 | Generalised to IF-QTR; instance architecture                                                                                                              | U. Warring, W. Wu |
| 0.2.1   | 2026-01-20 | Synthesis: hierarchy rule, Type A/B at links, noise type in IF-3, measurement volume definition, temporal validation, non-adjacent wavelength requirement | U. Warring, W. Wu |

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
**Version:** 0.1.0\
**Parent Framework:** IF-QTR v0.2.1\
**Status:** Reference implementation (stewardship phase)

***

### A.1 Instance Declaration

```
┌─────────────────────────────────────────────────────────┐
│ FRAMEWORK INSTANCE DECLARATION                          │
│                                                         │
│ Instance ID: IF-QTR-1762nm                              │
│ Parent: IF-QTR v0.2.1                                   │
│ Wavelength scope: 1762 ± 1 nm                           │
│ Atomic reference: ¹³⁸Ba⁺ (S₁/₂ → D₅/₂, 1762.115 nm)    │
│ Absorption proximity: H₂O at 1761.04 nm, 1762.49 nm    │
│ Standard model validity: Outside Ciddor/Edlén range    │
│   (> 1760 nm); Mathar partially applicable             │
│ Required corrections: Kramers-Kronig humidity          │
│   enhancement (15.3 ± 1.5)% relative to Mathar         │
│ Temporal validation: 15-day campaign demonstrated      │
└─────────────────────────────────────────────────────────┘
```

***

### A.2 Wavelength-Specific Context

#### A.2.1 Atomic Reference

The ¹³⁸Ba⁺ ion provides a frequency reference via the S₁/₂ → D₅/₂ electric quadrupole transition at 1762.115 nm. This transition is:

* Narrow linewidth (< 1 Hz natural linewidth)
* Suitable for optical frequency standards
* Directly relevant to barium-ion quantum network architectures

#### A.2.2 Absorption Proximity

The 1762 nm wavelength lies between two H₂O absorption lines:

* 1761.0405 nm (HITRAN)
* 1762.4852 nm (HITRAN)

This proximity induces anomalous dispersion via Kramers-Kronig relations, resulting in enhanced humidity sensitivity compared to standard atmospheric models.

#### A.2.3 Standard Model Limitations

| Model         | Stated validity | Status at 1762 nm                         |
| ------------- | --------------- | ----------------------------------------- |
| Ciddor (1996) | 300–1700 nm     | Outside range                             |
| Edlén (1966)  | Visible         | Outside range                             |
| Mathar (2007) | Extended IR     | Partially applicable; requires correction |

***

### A.3 Instance-Specific Constraints

#### A.3.1 Humidity Coefficient Correction

**Observed:** ∂n/∂H = −1.780 × 10⁻⁸ %⁻¹\
**Mathar prediction:** ∂n/∂H = −1.653 × 10⁻⁸ %⁻¹\
**Kramers-Kronig prediction:** ∂n/∂H = −1.772 × 10⁻⁸ %⁻¹

**Enhancement factor:** (15.3 ± 1.5)% relative to Mathar

**Required action:** Any handbook implementing IF-QTR-1762nm must apply the Kramers-Kronig correction to humidity coefficients. Use of uncorrected Mathar values is a departure requiring documentation under Section VI of the parent framework.

#### A.3.2 Environmental Parameter Ranges

The empirical model underlying this instance was validated over:

| Parameter         | Training range | Validation range |
| ----------------- | -------------- | ---------------- |
| Temperature       | 15–35 °C       | 15–35 °C         |
| Relative humidity | 20–45 %RH      | 20–45 %RH        |
| Pressure          | 965–1000 hPa   | 965–1000 hPa     |

**Constraint:** Claims outside these ranges require re-validation or explicit departure documentation.

#### A.3.3 Temporal Validation

Demonstrated reproducibility:

* Campaign duration: 15 days
* Training measurements: 89,106
* Validation measurements: 46,999
* Effective sample size (N\_eff): 35,100 (after AR(1) correction)
* Diurnal cycles covered: > 10

***

### A.4 Compliance with Parent Principles

#### IF-1 Compliance: Operational Traceability

**Traceability chain:**

| Link | Component                      | Uncertainty       | Coverage | Type  |
| ---- | ------------------------------ | ----------------- | -------- | ----- |
| 1    | ¹³⁸Ba⁺ ion frequency           | δf/f \~ 10⁻¹⁵     | k = 1    | B     |
| 2    | ULE cavity transfer            | δn \~ 10⁻¹²       | k = 1    | B     |
| 3    | 1762 nm laser lock             | < 1 kHz linewidth | k = 1    | B     |
| 4    | Dual-λ interferometer          | δn \~ 10⁻¹⁰       | k = 1    | A + B |
| 5    | Environmental sensing (BME280) | δn \~ 2.12 × 10⁻⁷ | k = 1    | B     |
| 6    | Statistical model              | δn \~ 1.2 × 10⁻⁹  | k = 1    | A     |

#### IF-2 Compliance: Layered Uncertainty

| Layer         | Symbol   | Value       | Dominant? |
| ------------- | -------- | ----------- | --------- |
| Frequency     | L\_freq  | 10⁻¹²       | No        |
| Transduction  | L\_trans | 10⁻¹⁰       | No        |
| Environmental | L\_env   | 2.12 × 10⁻⁷ | **Yes**   |

**Architectural fact:** Environmental sensing limits accuracy. This is documented and visible.

#### IF-3 Compliance: Common-Mode Rejection

| Parameter               | Value                           |
| ----------------------- | ------------------------------- |
| Reference wavelength    | 780 nm (⁸⁷Rb)                   |
| Probe wavelength        | 1762 nm (¹³⁸Ba⁺)                |
| Optical path difference | 4.2 m                           |
| CMR metric              | To be quantified in handbook    |
| Bandwidth               | To be stated in handbook        |
| Noise type              | To be characterised in handbook |

**Note:** Full CMR characterisation is deferred to the implementing handbook. This instance establishes the requirement; the handbook must provide the measurement.

#### IF-4 Compliance: Environmental Co-location

| Parameter                | Value                          |
| ------------------------ | ------------------------------ |
| Sensor type              | BME280                         |
| Spatial bound            | < 10 cm from beam path         |
| Temporal synchronisation | GPS-disciplined, 1 Hz sampling |
| Maximum latency          | < 1 s                          |

**Justification for spatial bound:** Laboratory environment with forced-air circulation; gradients estimated < 0.1 °C/m under operating conditions.

#### IF-5 Compliance: Model Transparency

| Requirement       | Status                                           |
| ----------------- | ------------------------------------------------ |
| Functional form   | Linear: n = α₀ + α\_T T + α\_H H + α\_P P        |
| Input variables   | T (°C), H (%RH), P (hPa)                         |
| Training domain   | T: 15–35 °C, H: 20–45 %RH, P: 965–1000 hPa       |
| Validation domain | Same as training                                 |
| N\_eff            | 35,100 (AR(1) ρ = 0.435)                         |
| Diagnostics       | DW = 1.13, BG LM = 29,735 (p < 0.001), VIF < 2.1 |

**Linearity justification:** Higher-order terms tested; contribution to residual variance < 10⁻⁹. Linear form adequate within stated domain.

#### IF-6 Compliance: Precision–Accuracy Separation

| Metric                       | Value       | GUM type |
| ---------------------------- | ----------- | -------- |
| Residual precision           | 1.2 × 10⁻⁹  | A        |
| Metrological accuracy        | 2.12 × 10⁻⁷ | B        |
| Expanded uncertainty (k = 2) | 4.24 × 10⁻⁷ | Combined |

***

### A.5 Refractive Index Coefficients

Empirically determined coefficients for n(T, H, P) at 1762 nm:

| Coefficient        | Value         | HAC SE       | Unit  |
| ------------------ | ------------- | ------------ | ----- |
| α₀ (constant)      | 1.000027      | 3.03 × 10⁻⁷  | —     |
| α\_T (temperature) | −8.940 × 10⁻⁷ | 4.47 × 10⁻¹⁰ | °C⁻¹  |
| α\_H (humidity)    | −1.780 × 10⁻⁸ | 4.13 × 10⁻¹⁰ | %⁻¹   |
| α\_P (pressure)    | +2.569 × 10⁻⁷ | 2.99 × 10⁻¹² | hPa⁻¹ |

**Model fit:** R² = 0.996

***

### A.6 Limitations and Improvement Pathways

#### Current Limitations

1. **Environmental sensing:** BME280 uncertainty (2.12 × 10⁻⁷) dominates error budget. This is a permanent architectural constraint at current sensor technology.
2. **Calibration:** Initial functionality verification performed; comprehensive metrological calibration not implemented.
3. **Environmental range:** Model validated over limited range; extrapolation prohibited without re-validation.

#### Improvement Pathways

1. **Sensor upgrade:** Metrology-grade hygrometry could reduce L\_env to 10⁻⁸ regime.
2. **Extended validation:** Broader environmental range (outdoor conditions, seasonal variation) would strengthen model confidence.
3. **CMR characterisation:** Full common-mode rejection measurement at multiple bandwidths.

***

### A.7 Instance Version History

| Version | Date       | Change                                               | Authors           |
| ------- | ---------- | ---------------------------------------------------- | ----------------- |
| 0.1.0   | 2026-01-20 | Initial instance based on 15-day validation campaign | U. Warring, W. Wu |

***

### A.8 Reference Handbook

The implementing handbook for this instance is:

> W. Wu et al. "Precision Refractive Index Measurement at 1762 nm," IN PREPERATION

**Compliance declaration for reference handbook:**

```
┌─────────────────────────────────────────────────────────┐
│ IF-QTR COMPLIANCE DECLARATION                           │
│                                                         │
│ Framework: IF-QTR v0.2.1                                │
│ Instance: IF-QTR-1762nm v0.1.0                          │
│ Principles implemented: IF-1, IF-2, IF-4, IF-5, IF-6    │
│ Principles not applicable: None                         │
│ Principles with deferred evidence: IF-3 (CMR metric)    │
│ Departures: None                                        │
│ Evidence:                                               │
│   IF-1: Fig. 4 (traceability chain)                     │
│   IF-2: Tables I–III (layered uncertainty)              │
│   IF-4: Section II.C (co-location statement)            │
│   IF-5: Section III.C, V.C (model diagnostics)          │
│   IF-6: Table III (precision vs. accuracy)              │
└─────────────────────────────────────────────────────────┘
```

***

**End of Document**
