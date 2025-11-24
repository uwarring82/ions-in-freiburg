---
description: Statistical Fundamentals for Noise Analysis
icon: scale-unbalanced-flip
---

Understanding and controlling noise is central to all precision
measurements, from trapped-ion qubits to frequency standards and
classical sensors. The practical question is always:

**Which part of the variation in my data is fundamental statistical
noise, and which part is systematic or technical?**

This chapter provides a structured framework using: - basic distribution
and variance checks, - time-domain stability analysis via Allan
deviation, - frequency-domain analysis via power spectral density (PSD),

tied together by a step-by-step noise attribution workflow and a
real-world case study.

------------------------------------------------------------------------

## 1. Statistical Fundamentals for Noise Analysis

Noise attribution starts with the simplest question:

**Does your data behave like the stochastic process you think it does?**

Two common situations: - Binomial proportions, - Poisson counts.

### 1.1 Binomial Proportions and Wilson Score Interval

Suppose you run $$N$$ identical trials with $$k$$ successes. The estimator
is:

$$ 
`\hat `{=tex}p = rac{k}{N}. 
$$

The Wald interval is:

$$ 
`\hat `{=tex}p `\pm `{=tex}z
`\sqrt{rac{\hat p(1-\hat p)}{N}}`{=tex}. 
$$

This is unreliable for small (N) or extreme (p) $$1$$.

**Wilson interval** $$1$$:

$$ ext{CI}\_ ext{Wilson} = rac{`\hat `{=tex}p + rac{z\^2}{2N}
`\pm `{=tex}z`\sqrt{ rac{\hat p(1-\hat p)}{N} + rac{z^2}{4N^2}}`{=tex}}{1 +
rac{z\^2}{N}}. $$

Properties: - Never gives bounds outside ($$0,1$$), - Accurate coverage
for small (N), - Reduces to normal approximation for large (N).

### 1.2 Poisson Counts and Over-Dispersion

Poisson baseline: - Mean = (`\lambda`{=tex}), - Variance =
(`\lambda`{=tex}).

Test dispersion using:

$$ (N-1)rac{s\^2}{ar{x}} `\sim `{=tex}`\chi`{=tex}\^2\_{N-1} $$

if expected counts ≥ 5 $$4,5$$.

------------------------------------------------------------------------

## 2. Time-Domain Stability: Allan Deviation

Allan variance measures how fluctuations evolve with averaging time (
au) $$3$$.

### 2.1 Definition

$$ `\sigma`{=tex}*y\^2( au) = rac{1}{2(M-1)}`\sum`{=tex}*{i=1}\^{M-1}
`\left`{=tex}(ar y\_{i+1}( au)-ar y_i( au)ight)\^2. $$

Characteristic slopes: - White noise: (`\propto    `{=tex}au\^{-1/2}), -
Flicker: flat, - Random walk: (`\propto    `{=tex}au\^{+1/2}).

### 2.2 Overlapping Allan Deviation

Uses all possible adjacent averages → lower variance than
non-overlapping $$6,7$$.

### 2.3 Confidence Intervals

Uncertainty depends on number of independent samples. See $$7$$.

------------------------------------------------------------------------

## 3. Frequency-Domain Analysis: Power Spectral Density

PSD reveals frequency-dependent noise.

### 3.1 Welch's Method

Steps $$8$$: 1. Segment data (typically 50% overlap), 2. Window each
segment, 3. FFT, 4. Average periodograms.

### 3.2 Reading the PSD

Slopes: - White: flat, - (1/f): slope --1, - (1/f\^2): slope --2.

Narrow peaks → coherent sources (50/60 Hz, mechanical, servo
instabilities).

### 3.3 Relation to ADEV

Allan deviation is a weighted integral over the PSD $$7$$.

------------------------------------------------------------------------

## 4. Step-by-Step Noise Attribution Workflow

### Step 1: Define Noise Hypotheses

List plausible noise sources.

### Step 2: Collect Data with an Analysis Plan

Avoid p-hacking; log conditions.

### Step 3: Data Integrity Checks

Inspect raw time series, histograms.

### Step 4: Distribution Analysis

Use binomial, Poisson, or Gaussian tests as appropriate.

### Step 5: Allan Deviation

Identify slopes and regimes.

### Step 6: PSD

Identify broadband slopes and discrete peaks.

### Step 7: Build Noise Budget

Assign variance contributions.

### Step 8: Iterate

Refine hypotheses and experiments.

### Step 9: Document

Archive raw data and scripts.

------------------------------------------------------------------------

## 5. Case Study: Electric-Field Noise in Surface-Electrode Ion Traps

### 5.1 Background

Heating rate (`\dot{ar n}`{=tex}) linked to electric-field noise.

Candidate mechanisms: - Johnson noise, - Technical noise, - Surface
patch potentials, - Microscopic surface processes.

### 5.2 Measurements

Heating rate vs trap distance (d) at room and cryogenic temperatures
$$2,9,10$$.

### 5.3 Statistical Checks

Stable, stationary distributions.

### 5.4 Scaling

Observed:

$$ S_E `\propto `{=tex}d\^{-4}, $$

inconsistent with Johnson noise; cryogenic cooling reduces amplitude
drastically.

### 5.5 Frequency Dependence

White + (1/f\^lpha) ((lpha pprox 1)) noise $$2,10$$, consistent with
surface fluctuation models.

### 5.6 Attribution

Surface noise is dominant; models include fluctuating dipoles, two-level
systems, adsorbate dynamics.

------------------------------------------------------------------------

## 6. Reproducibility and Integrity

Principles: - Predefine analysis plans, - Avoid p-hacking, - Document
exclusions, - Report statistical + systematic uncertainties, - Archive
data + code.

------------------------------------------------------------------------

## References

1.  L. D. Brown, T. T. Cai, A. DasGupta (2001). *Interval estimation for
    a binomial proportion*. Statistical Science 16, 101--133.\
2.  J. A. Sedlacek et al. (2018). *Evidence for multiple mechanisms
    underlying surface electric-field noise in ion traps*. PRA 98,
    063430.\
3.  D. W. Allan (1966). *Statistics of atomic frequency standards*.
    Proc. IEEE 54, 221--230.\
4.  NIST/SEMATECH e-Handbook (2012), Section 1.3.5.15.\
5.  Statistics LibreTexts (2019). *Chi-Square Goodness-of-Fit Test*.\
6.  D. W. Howe et al. (1981). *Properties of oscillator signals and
    measurement methods*.\
7.  W. J. Riley (2008). *Handbook of Frequency Stability Analysis*. NIST
    SP 1065.\
8.  P. D. Welch (1967). *The use of FFT for the estimation of power
    spectra*. IEEE Trans. Audio Electroacoustics 15, 70--73.
