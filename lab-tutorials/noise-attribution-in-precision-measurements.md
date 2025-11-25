---
description: Statistical Fundamentals for Noise Analysis
icon: scale-unbalanced-flip
---

# Noise Attribution in Precision Measurements

{% hint style="info" %}
_author: U. Warring_\
&#xNAN;_&#x61;ffiliation: Institute of Physics, University of Freiburg_\
&#xNAN;_&#x76;ersion: 1.0_\
&#xNAN;_&#x6C;ast\_updated: 2025-11-25_\
&#xNAN;_&#x72;eview\_status: Internal laboratory documentation; not externally peer-reviewed_\
&#xNAN;_&#x6C;icense: CC BY-SA 4.0_
{% endhint %}

### Introduction

Understanding and controlling noise is central to all precision measurements, from trapped-ion qubits to frequency standards and classical sensors. The practical question is always:

> _Which part of the variation in my data is fundamental statistical noise, and which part is systematic or technical?_

This chapter provides a structured framework for answering that question using frequentist tools:

* basic distribution and variance checks,
* time-domain stability analysis via Allan deviation, and
* frequency-domain analysis via power spectral density (PSD),

tied together by a step-by-step noise attribution workflow and a real-world case study.

#### Scope and Limitations

This tutorial provides a **frequentist statistical framework** for noise attribution in precision measurements, with emphasis on trapped-ion quantum systems.

**What this tutorial covers:**

* Distribution and variance verification (binomial, Poisson, Gaussian)
* Time-domain stability analysis via Allan deviation
* Frequency-domain analysis via power spectral density
* A structured workflow for systematic noise attribution
* A case study from surface-electrode ion trap research

**What this tutorial does not cover:**

* Bayesian inference methods for noise characterization
* Machine learning or automated anomaly detection approaches
* Domain-specific noise models outside trapped-ion physics (e.g., gravitational wave detectors, atomic fountain clocks) — though the general framework may transfer
* Non-stationary noise processes requiring wavelet or time-frequency analysis
* Detailed derivations of Allan variance transfer functions

**When to seek additional guidance:**

* If your noise exhibits strong non-Gaussian features (heavy tails, multimodality)
* If systematic effects dominate and require dedicated experimental campaigns
* If you observe unexplained residuals after completing the workflow
* For publication-level analysis, consult with experienced colleagues or statisticians

Students and researchers should treat this document as a **structured starting point**, not a comprehensive reference. The workflow provides guidance, not certification.

#### Prerequisites

This material assumes familiarity with:

**Mathematics and Statistics**

* Probability distributions (binomial, Poisson, Gaussian)
* Confidence intervals and hypothesis testing
* Basic Fourier analysis (discrete Fourier transform, power spectra)
* Logarithmic plotting and slope interpretation

**Experimental Physics**

* Data acquisition and time series measurements
* Familiarity with laboratory noise sources (thermal, electronic, mechanical)
* Basic understanding of feedback control systems

**Domain Knowledge (for the case study)**

* Trapped-ion physics fundamentals (helpful but not required)
* Concept of motional heating and electric-field noise

If you lack background in any of these areas, consider reviewing:

* _Data Reduction and Error Analysis_ by Bevington & Robinson (statistics)
* _The Art of Electronics_ by Horowitz & Hill, Chapter 8 (noise in electronics)
* Riley (2008), Ref. \[7], Chapters 1–3 (frequency stability fundamentals)

**Recommended group standard practices**

Within our lab, the following conventions are recommended as defaults:

* Use the **Wilson score interval** for binomial proportions (never the simple Wald interval).
* For Poisson-like count data, **check dispersion** (mean vs variance) and report if over-dispersion is found.
* For time series, always combine **Allan deviation** and **PSD** when characterizing noise.
* For thesis and internal reports, include a short **noise budget table** summarizing identified noise sources and their quantitative contributions.

***

### 1. Statistical Fundamentals for Noise Analysis

Noise attribution starts with the simplest question:

> _Does your data behave like the stochastic process you think it does?_

Three common situations, in order of increasing generality:

* **Binomial proportions** (success/failure outcomes),
* **Poisson counts** (rare events per interval),
* **Gaussian (normal) distributions** (continuous measurements, or large-count limits of the above).

Understanding when each applies — and when they converge — is essential for choosing appropriate statistical tools.

#### 1.1 Binomial Proportions and Wilson Score Interval

Suppose you run $$N$$ identical trials and observe $$k$$ “successes” (e.g. ion detected bright vs dark). The natural estimator of the success probability is

<p align="center"><span class="math">\hat p = \frac{k}{N}.</span></p>

The traditional Wald interval (normal approximation) is

<p align="center"><span class="math">\hat p \pm z \sqrt{\frac{\hat p(1-\hat p)}{N}},</span></p>

where $$z$$ is the critical value for the desired confidence (e.g. $$z \approx 1.96$$ for 95%).

However, this interval is known to have poor coverage for small $$N$$ or extreme probabilities (e.g. $$\hat p$$ near 0 or 1): it can be too narrow and even yield limits outside $$[0,1]$$, cp. Ref. \[1]. This is unacceptable in high-stakes precision analysis.

A more robust choice is the Wilson score interval \[1]. For confidence level $$1-\alpha$$ with critical value $$z_{1-\alpha/2}$$, the Wilson interval is

<p align="center"><span class="math">\text{CI}_{\text{Wilson}} = \frac{\hat p + \frac{z^2}{2N} \pm z\sqrt{\frac{\hat p(1-\hat p)}{N} + \frac{z^2}{4N^2}}}{1 + \frac{z^2}{N}}.</span></p>

Key properties:

* It never produces limits outside $$[0,1]$$.
* It maintains much more accurate coverage even when $$N$$ is small or $$p$$ is close to 0 or 1 \[1].
* It smoothly reduces to the normal approximation for large $$N$$.

For example, with $$N=10$$ and $$\hat p = 0$$, the Wald interval would give $$[0,0]$$, but the Wilson interval yields a non-zero upper bound (≈0.26 at 95% confidence), which honestly reflects our uncertainty \[1].

For binary experimental outcomes (e.g. qubit state readout, survival probability), this is the interval students should use by default.

**Worked example (Wilson interval)**

Suppose you perform ($$N = 10$$) bright/dark state detections and observe ($$k = 0$$) bright outcomes.

* $$\hat p = k/N = 0$$.
* For 95% confidence, ($$z \approx 1.96$$).

Plugging into the Wilson formula gives approximately

$$\text{CI}_{\text{Wilson}} \approx [0, 0.26].$$

The Wald interval would have given \[0,0], which clearly underestimates our uncertainty. This is a typical regime in trapped-ion experiments where the Wilson interval is strongly preferred.

***

#### 1.2 Poisson Counts and Over-Dispersion

For count data (e.g. number of detected photons in a fixed time, number of quantum jumps), the Poisson distribution is often the baseline model:

* Parameter: $$\lambda$$ (mean rate)
* Mean: $$\mathbb{E}[X] = \lambda$$
* Variance: $$\mathrm{Var}(X) = \lambda$$

If you have $$N$$ independent measurements $$x_1,\dots,x_N$$ (counts per interval), the sample mean and variance are

<p align="center"><span class="math">\bar{x} = \frac{1}{N} \sum_{i=1}^N x_i, \qquad s^2 = \frac{1}{N-1} \sum_{i=1}^N (x_i - \bar{x})^2.</span></p>

For a truly Poisson process, you expect $$s^2 \approx \bar{x}$$. A deviation from this equality is called over-dispersion ($$s^2 > \bar{x}$$) or under-dispersion ($$s^2 < \bar{x}$$).

A quantitative test: under the null hypothesis of a Poisson model with mean $$\lambda = \bar{x}$$, the statistic

<p align="center"><span class="math">(N-1)\frac{s^2}{\bar{x}} \sim \chi^2_{N-1}</span></p>

approximately follows a chi-square distribution with $$n-1$$ degrees of freedom \[4].

**Interpretation procedure:**

1. Compute the test statistic $$\chi^2 = \sum_i (x_i - \bar{x})^2 / \bar{x}$$
2. Compare to the critical value $$\chi^2_{0.95}(n-1)$$ from chi-square tables (or use software)
3. If $$\chi^2 > \chi^2_{0.95}(n-1)$$, reject the null hypothesis of Poisson statistics at the 5% significance level

_Example:_ For $$n = 20$$ measurements, $$\chi^2_{0.95}(19) \approx 30.1$$. If your computed statistic exceeds 30.1, the variance is significantly larger than the Poisson expectation.

A significant result signals **over-dispersion**: extra noise beyond simple Poisson counting statistics. Common causes include fluctuating rates, unresolved mixture of sources, detector gain variations, or additional technical noise.

_Caution:_ A non-significant result does not prove the data are Poisson — it only means you lack evidence to reject the Poisson model. With small $$n$$, power to detect over-dispersion is limited.

_Rule of thumb:_ For the chi-square approximation to be reliable, expected counts should not be too small. A common criterion is that each expected count should be at least 5; Cochran (1952) provides the foundational analysis of this requirement \[5, 5a]. If many bins have expected counts below this threshold, either combine categories or use exact methods (e.g., exact Poisson confidence intervals via the Garwood method).

**Worked example (Poisson dispersion test)**

Assume you record $$N = 20$$ photon-count measurements (counts per fixed time bin) with

<p align="center"><span class="math">\bar{x} = 12.3, \qquad s^2 = 22.5.</span></p>

Under the Poisson hypothesis, you expect (s^2 \approx \bar{x}). Compute

<p align="center"><span class="math">\chi^2 = (N-1)\frac{s^2}{\bar{x}} \approx 19 \times \frac{22.5}{12.3} \approx 34.8.</span></p>

For $$N-1 = 19$$ degrees of freedom and 95% confidence, ($$\chi^2_{0.95}(19) \approx 30.1$$. Since $$34.8 > 30.1$$, you would **reject** the pure Poisson model at the 5% level and conclude that the data are over-dispersed (extra technical or systematic noise).

**Exact confidence intervals for low counts**

When expected counts are small $$< 10$$ or when higher accuracy is required, exact confidence intervals should be used instead of the chi-square approximation. For Poisson data, the **Garwood method** provides exact confidence intervals based on the relationship between Poisson and chi-square distributions.

For an observed count $$k$$, the exact $$100(1−α)$$% confidence interval for the true rate λ is

<p align="center"><span class="math">\left[ \frac{1}{2}\chi^2_{\alpha/2}(2k), \quad \frac{1}{2}\chi^2_{1-\alpha/2}(2k+2) \right]</span></p>

where χ²\_p(ν) is the p-th quantile of the chi-square distribution with ν degrees of freedom.

This is the Poisson analog of the Wilson interval for binomial data: it maintains accurate coverage even for $$k = 0$$ and never produces negative lower bounds.

***

#### 1.3 Gaussian Distributions and Their Limits of Applicability

Many precision measurements produce continuous-valued data: voltages, frequencies, positions, phase differences. The Gaussian (normal) distribution is often the default model:

$$
p(x) = \frac{1}{\sqrt{2\pi\sigma^2}} \exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right)
$$

with mean $$\mu$$ and variance $$\sigma^2$$.

**When Gaussian Models Apply**

**Direct physical justification:**\
Thermal noise (Johnson-Nyquist), quantum shot noise in the large-photon limit, and many detection systems produce approximately Gaussian fluctuations by construction.

**Central Limit Theorem (CLT):**\
Sums or averages of many independent random variables converge to Gaussian distributions, regardless of the underlying distribution. This is why:

* Binomial distributions approach Gaussian for large $$n$$ (typically $$np > 10$$ and $$n(1-p) > 10$$)
* Poisson distributions approach Gaussian for large $$\lambda$$ (typically $$\lambda > 20$$)
* Averaged time series data often appears Gaussian even when individual samples are not

**Practical criterion:** If your data arise from averaging or summing many independent contributions, Gaussian assumptions are often reasonable.

**Diagnostic Tools**

Before assuming Gaussianity, verify:

1. **Histogram inspection:** Does the distribution appear symmetric and bell-shaped? Look for skewness, heavy tails, or multimodality.
2. **Q–Q plot (quantile-quantile):** Plot observed quantiles against theoretical Gaussian quantiles. Deviations from a straight line indicate:
   * S-shaped curve → heavy tails (more outliers than Gaussian predicts)
   * Curved ends → skewness
   * Steps or clusters → discrete subpopulations or rounding
3. **Formal tests:**
   * Shapiro-Wilk (best power for $$n < 50$$)
   * Anderson-Darling (sensitive to tails)
   * Jarque-Bera (tests skewness and kurtosis)

**Common Pitfalls**

**Applying Gaussian statistics to small counts:**\
For Poisson data with $$\lambda < 20$$ or binomial data with small $$np$$, Gaussian approximations can yield confidence intervals that miss the true value more often than advertised, or even extend below zero. Use exact methods or appropriate approximations (Wilson, Garwood) instead.

**Ignoring heavy tails:**\
Some noise processes (e.g., certain types of electronic interference, surface noise with Lévy-flight character) produce distributions with heavier tails than Gaussian. Standard confidence intervals and significance tests assume Gaussian tails; heavy-tailed data will have more "outliers" than expected, and trimmed or robust estimators may be needed.

**Over-reliance on normality tests:**\
With large $$n$$, normality tests reject even trivial deviations. With small $$n$$, they lack power to detect meaningful non-Gaussianity. Use tests as one input alongside visual diagnostics and physical reasoning.

**Worked example (Gaussian diagnostics)**

Consider 1000 measurements of a stabilized voltage:

* The histogram looks symmetric, but the Q–Q plot against a Gaussian shows clear S-shaped deviations in the tails.
* A Shapiro–Wilk test returns $$p \approx 10^{-4}$$.

Conclusion: the data are **not exactly Gaussian**—there are heavier tails than expected. For many analyses (mean estimates, rough confidence intervals), the Gaussian model may still be acceptable, but you should:

* use robust estimators (e.g. median and MAD) when outliers matter, and
* avoid relying on Gaussian tail probabilities for rare-event claims.

**Relationship to Sections 1.1 and 1.2**

The three distributions form a hierarchy:

| Situation                     | Appropriate model | Gaussian approximation valid when...            |
| ----------------------------- | ----------------- | ----------------------------------------------- |
| Binary outcomes (bright/dark) | Binomial          | $$np > 10$$ and $$n(1-p) > 10$$                 |
| Count data (photons, events)  | Poisson           | $$\lambda > 20$$                                |
| Continuous measurements       | Gaussian          | CLT conditions met, or by physical construction |

When in doubt, start with the more specific model (binomial or Poisson) and verify whether Gaussian approximations are justified for your sample sizes and parameters. The specific models provide exact results; the Gaussian is an approximation whose accuracy depends on being in the appropriate limit.

***

### 2. Time-Domain Stability: Allan Deviation

Many precision systems (clocks, oscillators, qubit phases) are characterized by time-dependent noise: not just how big fluctuations are, but how they evolve over different averaging times. The standard tool here is the Allan variance (and its square root, Allan deviation) \[3].

#### 2.1 Definition and Interpretation

Consider a time series $$y(t)$$ representing, for example, the fractional frequency deviation of a clock or the normalized deviation of some measured quantity. Suppose we sample it at regular intervals and define time-averaged values $$\bar{y}_i(\tau)$$ over non-overlapping blocks of duration $$\tau$$:

* Split the full data set of duration $$T$$ into $$M$$ contiguous blocks of length $$\tau$$.
* In each block, compute the average $$\bar{y}_i(\tau)$$.

The Allan variance for averaging time $$\tau$$ is \[3,7]

<p align="center"><span class="math">\sigma_y^2(\tau) = \frac{1}{2(M-1)} \sum_{i=1}^{M-1} \big(\bar{y}_{i+1}(\tau) - \bar{y}_i(\tau)\big)^2.</span></p>

The Allan deviation is $$\sigma_y(\tau) = \sqrt{\sigma_y^2(\tau)}$$.

Qualitative meaning: $$\sigma_y(\tau)$$ measures how much the system’s average value changes from one interval of length $$\tau$$ to the next. Plotting $$\sigma_y(\tau)$$ vs. $$\tau$$ on log–log axes reveals different noise processes as distinct slopes \[3,7]:

* White (uncorrelated) noise: $$\sigma_y(\tau) \propto \tau^{-1/2}$$ (averaging suppresses noise like $$1/\sqrt{\tau}$$).
* Flicker noise (1/f): $$\sigma_y(\tau)$$ approximately flat (slope ≈ 0).
* Random walk / drift: $$\sigma_y(\tau) \propto \tau^{+1/2}$$ or steeper (noise grows with averaging time).

A typical pattern: at short $$\tau$$, white measurement noise dominates; as $$\tau$$ increases, flicker noise or drift takes over, and stability no longer improves.

#### 2.2 Overlapping Allan Deviation

Non-overlapping Allan variance only uses one pair of neighboring averages per $$2\tau$$ span. To better exploit data, one introduces the overlapping Allan variance, which uses all possible adjacent $$\tau$$-spaced averages \[6,7]. This yields many more terms in the sum and significantly reduces estimator variance at each $$\tau$$.

Qualitatively:

* Non-overlapping ADEV: fewer, more independent samples; higher scatter.
* Overlapping ADEV: many more samples; lower scatter; slightly more complex correlation structure.

For most experimental applications, overlapping Allan deviation is preferred because it provides smoother, more reliable stability estimates with limited data \[6,7].

#### 2.3 Confidence Intervals

Like any estimator, $$\sigma_y(\tau)$$ has uncertainty. The effective number of degrees of freedom depends on how many independent averages contribute at each $$\tau$$. Reference \[7] provides formulas and tables for confidence intervals of Allan deviation. When plotting $$\sigma_y(\tau)$$, especially for publication, you should:

* include error bars or bands for each $$\tau$$, and
* be cautious when interpreting features at $$\tau$$ where the number of independent samples is small.

***

### 3. Frequency-Domain Analysis: Power Spectral Density

Time-domain stability gives a good overview of noise vs. averaging time, but it does not directly reveal which frequencies are problematic. For that, we use the power spectral density (PSD) $$S_x(f)$$.

#### 3.1 Practical Estimation: Welch’s Method

Given a time series $$x(t)$$ (e.g. a voltage, position, or frequency deviation) sampled at rate $$f_s$$, the theoretical PSD is

<p align="center"><span class="math">S_x(f) = \lim_{T \to \infty} \frac{1}{T} \left| \int_0^T x(t) e^{-2\pi i f t} dt \right|^2.</span></p>

In practice, we have a finite time series and compute discrete Fourier transforms. A single FFT-based periodogram is often very noisy as an estimator. Welch’s method \[8] improves the estimate by averaging over multiple segments:

1. Divide the time series into overlapping segments (e.g. 50% overlap).
2. Apply a window (e.g. Hanning) to each segment to reduce edge discontinuities.
3. Compute the FFT and periodogram of each windowed segment.
4. Average these periodograms to obtain the final PSD estimate \[8].

This approach greatly reduces the variance of the PSD estimate, at the cost of lower frequency resolution (due to shorter segments). Typical choices:

* Segment length: $$2^{10}–2^{14}$$ samples, depending on data length.
* Overlap: 50 % (standard compromise between resolution and variance).
* Window: Hanning or similar, to manage spectral leakage \[8].

The result is a smooth PSD estimate, suitable for identifying broadband slopes and narrow peaks.

#### 3.2 Reading the PSD

On a log–log plot of PSD vs frequency, different noise types appear as characteristic slopes:

* White noise: flat spectrum.
* $$1/f$$ noise: PSD $$\propto f^{-1}$$ (slope −1).
* $$1/f^2$$ noise: PSD $$\propto f^{-2}$$ (random walk, slope −2).

Superimposed narrow peaks indicate coherent or quasi-periodic noise sources, such as:

* Mains power (e.g. 50/60 Hz and harmonics),
* Mechanical resonances (e.g. vacuum pump or fan frequencies),
* Servo oscillations or control-loop artifacts.

By associating peaks with known hardware or environmental frequencies, we can quickly identify specific offenders.

#### 3.3 Link Between PSD and Allan Deviation

The PSD and Allan deviation are mathematically related: Allan deviation can be expressed as a weighted integral over $$S_y(f)$$ \[7]. Practically:

* Integrating PSD over a given frequency band gives the contribution to time-domain variance from that band.
* Features in the ADEV plot (e.g. a “bump” at a certain $$\tau$$) can be mapped to features in the PSD (e.g. a $$1/f$$ regime or a resonance).

This consistency check is valuable: it ensures that time-domain and frequency-domain analyses tell a coherent story about the same noise processes.

***

### 4. Step-by-Step Noise Attribution Workflow

To move from “I see noise” to “I know its sources and magnitudes,” it helps to follow a structured workflow. Figure 1 sketches this as a flowchart.

<figure><img src="../.gitbook/assets/noise_attribution_flowchart (1).png" alt="Flowchart showing nine-step noise attribution workflow from raw data through statistical checks, ADEV and PSD analysis, cross-validation, iteration, and final documentation"><figcaption></figcaption></figure>

_Figure 1: Noise attribution workflow._ Starting from raw data, we first check simple statistical assumptions (distribution and variance), then use time- and frequency-domain tools, and finally iterate with physical hypotheses until the noise budget closes.

#### 4.1 Step 1: Define Objectives and Noise Hypotheses

Clarify what “noise” means for your system:

* Is it the instability of a frequency?
* The scatter of a measurement around a calibration curve?
* The heating rate of an ion’s motional mode?

List plausible noise sources: thermal noise, $$1/f$$ electronics noise, mechanical vibrations, electromagnetic pick-up, drift in environmental parameters, quantum projection noise, etc. This top-down hypothesis list will guide your tests.

#### 4.2 Step 2: Collect Data with an Analysis Plan

Before taking data, sketch a plan:

* What signals and auxiliary channels will you record?
* Over what timescale and at what sampling rate?
* Which statistical tools will you apply?

Pre-defining the analysis reduces the temptation to “fish” for effects (p-hacking). During data taking, log:

* environmental conditions (temperature, humidity, lab activity),
* instrument settings,
* timestamps and any interventions.

#### 4.3 Step 3: Data Integrity Checks

Start with simple plots:

* Raw data vs time,
* Histograms,
* Scatter plots vs environmental parameters.

Look for:

* Obvious outliers (instrument glitches, saturations),
* Jumps or steps (configuration changes),
* Missing data segments.

If you exclude data, record why (e.g. “laser unlocked between 13:05–13:07, excluded this interval”). Integrity checks prevent you from analyzing artefacts as if they were physical noise.

#### 4.4 Step 4: Statistical Distribution Analysis

Now test whether your data behave as expected under their _assumed_ distribution.

* **Poisson:** Are mean and variance comparable? Use the dispersion test with $$(N-1)\frac{s^2}{\bar{x}} \sim \chi^2_{N-1}$$ and check if the result is within a reasonable range of the chi-square distribution \[4]. A significantly larger value indicates over-dispersion (extra noise beyond simple Poisson). Check that expected counts are ≥5 to justify the approximate test \[5].
*   **Gaussian:** Does a histogram look approximately bell-shaped? Produce a Q–Q plot (quantile–quantile against a normal distribution) to visually assess departures from normality.

    For formal testing, common choices include:

    * **Shapiro-Wilk test:** Preferred for smaller samples ($$n < 50$$); high power against a broad range of alternatives.
    * **Anderson-Darling test:** Good sensitivity to tail deviations; appropriate for moderate sample sizes.
    * **D'Agostino-Pearson test:** Tests skewness and kurtosis jointly; useful for larger samples.

    _Caution:_ With large $$n$$, even small, practically negligible deviations from normality will register as statistically significant. In such cases, rely more heavily on Q–Q plots and assess whether deviations are large enough to affect your downstream analysis (e.g., confidence interval coverage, ADEV interpretation). If QQ-plot deviations are within ±0.5σ across most of the range, Gaussian approximations are typically adequate for confidence intervals.
* **Binomial:** For repeated success/failure runs, estimate $$\hat p$$ and construct Wilson intervals \[1]. Check if repeated blocks of trials are mutually consistent with a single $$p$$ (homogeneity test). Strong discrepancies between blocks indicate time-varying $$p(t)$$ or systematic biases (e.g. detector threshold drift).

If the data strongly deviate from the expected distribution, revisit either your model (maybe it isn’t purely Poisson or binomial) or your assumptions (hidden drifts, unaccounted correlations, etc.).

#### 4.5 Step 5: Time-Domain Analysis (Allan Deviation)

For time series, compute $$\sigma_y(\tau)$$ over a range of averaging times:

* Identify noise regimes by slope: white noise, flicker, random walk, drift \[3,7].
* Locate crossover points where one mechanism yields to another.
* Use overlapping Allan deviation to reduce estimator noise \[6,7].
* Consider drift-insensitive variants (Hadamard variance) if linear drift contaminates the ADEV at long $$\tau$$.

Compare the observed stability with theoretical predictions or device specs. If the short-term regime is worse than shot-noise limits, you likely have technical noise; if long-term stability tanks at a certain $$\tau$$, suspect drift in environmental or technical parameters.

#### 4.6 Step 6: Frequency-Domain Analysis (PSD)

Compute the PSD using Welch’s method \[8]:

* Look for narrow spectral lines (e.g. 50/60 Hz mains, mechanical resonances).
* Characterize the broadband slope (white, $$1/f$$, $$1/f^2$$).
* Compare measurements under different conditions (e.g. pumps on/off, equipment moved) to see which features change.

Link PSD features to physical noise sources:

* Peaks at line frequencies → electromagnetic pick-up.
* Peaks at rotation frequencies → mechanical vibrations.
* Broad $$1/f$$ region → flicker noise in electronics or surfaces.

#### 4.7 Step 7: Cross-Analysis and Noise Budget

Combine insights:

* Do the Allan deviation regimes correspond to integrated contributions from parts of the PSD spectrum \[7]?
* Can you assign each segment of $$\sigma_y(\tau)$$ to an identifiable mechanism?
* Build a noise budget: a table listing each noise source, its estimated variance/power, and its contribution to the total.

If the sum of identified contributions explains the observed noise within uncertainties, your model is consistent. If there is a substantial unexplained residual, you have a missing noise source – formulate new hypotheses.

#### Validation Strategies

Beyond internal consistency (PSD–ADEV agreement), consider these validation approaches:

**Bootstrap resampling**\
Resample your time series (using block bootstrap to preserve correlations) and recompute ADEV or PSD. The spread of bootstrap estimates provides uncertainty bounds that account for data structure, not just sample size.

**Split-half validation**\
Divide your data into two halves (e.g., first half vs. second half, or interleaved). Perform the full noise attribution independently on each half. Consistent results strengthen confidence; discrepancies reveal non-stationarity or overfitting to noise.

**Sensitivity analysis**\
Vary analysis parameters (PSD segment length, ADEV τ spacing, outlier thresholds) and observe how conclusions change. Robust conclusions should not depend critically on arbitrary choices.

**Prediction testing**\
If your noise model is correct, it should predict behavior in new conditions. For example, if you attribute noise to a 50 Hz pickup, inserting a notch filter should reduce that contribution predictably.

#### 4.8 Step 8: Iterate and Refine

Noise attribution is rarely one-shot. Use residuals to guide the next iteration:

* Form a more detailed or alternative hypothesis (e.g. add a $$1/f$$ component or an environment-coupled term).
* Design targeted experiments: change materials, temperatures, shielding, or geometry to perturb suspected sources.
* Repeat the workflow with updated data and models.

Each iteration should ideally shrink the unexplained residual and refine your physical understanding.

#### 4.9 Step 9: Document and Archive

Finally, record:

* Which noise sources were identified and how.
* Quantitative contributions (with uncertainties).
* Mitigation steps taken and their effect.
* Any anomalous or unexplained features.

Archive raw data and analysis scripts whenever possible. Future students (and your future self) will benefit immensely from this transparency.

***

### 5. Case Study: Electric-Field Noise and Heating in Surface-Electrode Ion Traps

To see the workflow in action, consider a canonical problem in trapped-ion physics: anomalous motional heating in surface-electrode traps.

#### 5.1 Background and Hypotheses

When an ion is trapped at distance $$d$$ above an electrode surface, it experiences fluctuating electric fields. These fields drive motional heating: the mean phonon number $$\bar{n}$$ increases over time, limiting gate fidelity and coherence.

Standard thermal (Johnson) noise in the electrodes predicts an electric-field noise spectral density roughly scaling as

* $$S_E \propto d^{-2}$$, and
* linear in temperature $$T$$.

However, numerous experiments have observed much stronger distance dependence and higher amplitude than Johnson noise would suggest. A set of candidate mechanisms includes:

* Johnson noise in the electrodes (baseline),
* technical noise from electronics (RF drive, DACs),
* fluctuating patch potentials on the surface (e.g. from adsorbates, defects),
* other microscopic surface processes.

#### 5.2 Measurements

We consider a **pedagogically simplified** version of the measurements in \[2,9,10]. The following aspects are omitted or idealized for clarity:

* **Micromotion effects:** Real measurements require careful minimization and characterization of excess micromotion, which contributes to heating through mechanisms distinct from surface noise.
* **Trap geometry corrections:** The simple $$d^{-4}$$ scaling assumes a semi-infinite planar electrode; real trap geometries require numerical modeling.
* **Secular frequency dependence:** Heating rate measurements at different trap frequencies probe different parts of the noise spectrum; this dependence is averaged over here.
* **Surface treatment protocols:** The referenced experiments involve specific cleaning, annealing, and in-situ treatment procedures not detailed here.
* **Statistical analysis of heating rate extraction:** Converting Rabi flop or sideband ratio data to phonon numbers involves additional statistical machinery.

For complete experimental methodology, consult the original references \[2,9,10] and the reviews therein.

**Simplified measurement protocol:**

* Single ions are trapped at various distances $$d$$ above a surface-electrode trap.
* At each $$d$$, the heating rate $$\dot{\bar{n}}$$ is measured by preparing the ion near the motional ground state and measuring its energy after a delay.
* Measurements are performed at both room temperature (≈300 K) and cryogenic temperatures (e.g. 4 K).
* For each condition, multiple runs are taken to estimate mean and variance of $$\dot{\bar{n}}$$.

#### 5.3 Statistical and Stability Checks

At fixed $$d$$ and temperature:

* The distribution of measured heating rates per run is approximately log-normal; taking logarithms yields near-Gaussian distributions.
* Variance between runs is moderate; no strong evidence for Poisson-like event statistics within a fixed $$d$$.
* Over time, heating rates are stable; Allan deviation does not show large drifts over the timescale of the measurement. The process appears stationary (within resolution).

Thus, basic statistical assumptions (stationarity, well-defined mean) are satisfied; no hard evidence for time-varying rates during a run.

#### 5.4 Distance and Temperature Scaling

The decisive evidence emerges from distance scaling:

*   The measured electric-field noise (inferred from heating rate) scales approximately as $$S_E \propto d^{-4},$$

    across the accessible range of distances \[2,10].
* This $$d^{-4}$$ scaling holds both at 300 K and at 4 K \[2].

This scaling is much steeper than the $$d^{-2}$$ scaling predicted for uniform Johnson noise from the electrode bulk. It suggests that the dominant noise originates in localized surface patches or microscopic structures whose fields decay more rapidly with distance.

Cooling the trap to 4 K has two main effects \[2,9]:

* The overall noise amplitude drops by orders of magnitude (often ≳100× reduction in heating rate).
* The functional form (e.g. $$d^{-4}$$) remains roughly the same.

This behaviour is inconsistent with pure Johnson noise (which would be proportional to $$T$$ and have a different spatial scaling), and strongly indicates an additional surface-related mechanism \[2,9,10].

#### 5.5 Frequency Dependence

Measurements of the noise PSD show:

* At intermediate frequencies, the spectrum is roughly flat (white noise),
* At lower frequencies, it shows a $$1/f^\alpha$$ tail with $$\alpha \approx 1$$ \[2,10],
* No dominant narrow peaks from technical noise (after careful filtering and shielding).

A $$1/f$$-like spectrum is consistent with many models of surface fluctuation noise, e.g. fluctuating dipoles, two-level systems, or adsorbate dynamics \[10]. By contrast, Johnson noise would be white over the relevant band.

#### 5.6 Attribution and Open Questions

Combining:

* Distance scaling $$S_E \propto d^{-4}$$,
* Temperature behaviour (dramatic reduction at cryogenic temperatures),
* Frequency dependence (white plus $$1/f$$ tail), and
* Cross-checks to rule out technical noise,

we can confidently attribute most of the observed noise to surface electric-field noise associated with microscopic processes at or near the electrode surface \[2,9,10].

Within this class, several microscopic models are still under investigation \[10]:

* Fluctuating adsorbate dipoles,
* Two-level systems in oxides or contamination layers,
* Motion or rearrangement of surface charges.

Experiments that modify the surface (e.g. argon-ion cleaning, changing materials, varying temperature) further support these interpretations. For example, Sedlacek _et al._ \[2] observed that after argon-ion milling, the temperature dependence of the noise changed from a power law to a thermally activated (Arrhenius-like) form, consistent with activation of specific surface processes.

Remaining open questions include \[2,9,10]:

* What is the dominant microscopic noise mechanism for a given material and treatment?
* How do different electrode materials or coatings compare in long-term stability?
* Can we design and maintain surfaces with sufficiently low electric-field noise that no longer limit trapped-ion performance?

This case study illustrates the full workflow:

1. Basic variance and distribution checks (statistical sanity).
2. Time-domain stability analysis (no large drifts).
3. Frequency-domain PSD analysis (1/f plus white noise, no obvious technical peaks).
4. Systematic scaling experiments (distance, temperature, surface treatment).
5. Cross-checking against theoretical models and prior literature \[2,9,10].

The result is a compelling attribution of a complex noise source, guiding both mitigation strategies (e.g. cryogenic operation, surface cleaning) and future research directions.

***

### 6. Reproducibility and Integrity

Finally, a few meta-principles:

* Predefine analysis plans wherever possible: specify which tests and metrics you will use before examining the data.
* Avoid p-hacking: don’t iteratively tweak thresholds or exclude points until you get “nice” Allan deviation or PSD curves. If you explore many variants, be explicit that these are exploratory.
* Document data exclusions: every time you discard a data point or segment, record the physical reason (e.g. “laser unlocked here”).
* Report both statistical and systematic uncertainties: if systematics dominate, say so.
* Archive data and code: aim for the standard that another researcher can reproduce your plots and noise budget from your raw data and scripts.

These practices ensure that your noise attribution is not only technically sound but also scientifically trustworthy.

***

### 7. Common Pitfalls in Noise Attribution

Experience suggests several recurring errors in noise analysis. Being aware of these can save significant time and prevent incorrect conclusions.

#### 7.1 Statistical Pitfalls

**Over-interpreting long-τ Allan deviation**\
At large averaging times, the number of independent samples becomes small (sometimes < 5), and ADEV estimates become unreliable. A "bump" or "upturn" at long τ may be a statistical fluctuation rather than a real drift mechanism. Always check confidence intervals and be skeptical of features where degrees of freedom are low.

**Confusing statistical significance with physical significance**\
A statistically significant deviation from a Poisson or Gaussian model does not necessarily indicate a problem. With sufficient data, you will _always_ find deviations. Ask: Is this deviation large enough to matter for my measurement goals?

**Applying Gaussian statistics to count data**\
For small counts (< 20–30), Gaussian approximations to Poisson or binomial distributions can be poor. Use exact methods or appropriate approximations (Wilson interval for binomial, Garwood interval for Poisson).

**Neglecting correlations in time series**\
Standard error estimates assume independent samples. If your data have temporal correlations (which noise analysis often reveals!), naive uncertainty estimates will be too small. Consider block bootstrap or HAC (heteroskedasticity and autocorrelation consistent) estimators.

#### 7.2 Measurement Pitfalls

**Forgetting to log environmental conditions**\
Temperature, humidity, vibration levels, and lab activity often correlate with noise. If you don't record them, you cannot test these hypotheses later. Log continuously if possible.

**Changing multiple variables simultaneously**\
When investigating noise sources, change one thing at a time. If you modify the trap drive frequency _and_ the detection threshold _and_ the ion species, you cannot attribute any observed change.

**Insufficient baseline measurements**\
Before investigating a suspected noise source, establish a reliable baseline. Otherwise, you cannot quantify improvement.

#### 7.3 Analysis Pitfalls

**Choosing analysis parameters post hoc**\
Selecting PSD segment length, ADEV τ range, or histogram bin width _after_ seeing the data — especially to make features appear or disappear — is a form of p-hacking. Pre-specify reasonable choices or report results for multiple parameter values.

**Ignoring the PSD–ADEV consistency check**\
If your ADEV shows white noise but your PSD shows strong 1/f behavior (or vice versa), something is wrong. These representations must be consistent; discrepancies indicate analysis errors or non-stationary data.

**Attributing residuals without physical evidence**\
It is tempting to label unexplained noise as "technical noise" or "surface noise." Such attributions require supporting evidence (e.g., scaling with a controllable parameter, correlation with an auxiliary measurement). Unexplained residuals should be honestly labeled as such.

#### 7.4 Documentation Pitfalls

**Undocumented data exclusions**\
Every excluded data point or segment should have a recorded justification written _before_ seeing its effect on the final result. "Excluded because it made the fit worse" is not acceptable.

**Non-reproducible analysis**\
If you cannot regenerate your plots from archived raw data and scripts, your analysis is not reproducible. This is the minimum standard for trustworthy science.

***

### Appendix A: Glossary of Terms

**Allan deviation (ADEV)**\
A measure of frequency stability as a function of averaging time τ. Characterizes how much a signal's average value changes between consecutive intervals of duration τ. Units match the quantity being measured.

**Allan variance (AVAR)**\
The square of Allan deviation. Often denoted σ²\_y(τ).

**Flicker noise (1/f noise)**\
Noise whose power spectral density is inversely proportional to frequency. Common in electronic components and many physical systems. In ADEV plots, appears as a flat region (slope ≈ 0).

**Garwood interval**\
An exact confidence interval for Poisson parameters based on the chi-square distribution. Maintains accurate coverage for low counts (including zero), analogous to the Wilson interval for binomial data.

**Johnson noise (thermal noise)**\
Voltage fluctuations in resistors due to thermal agitation of charge carriers. Spectral density is white (flat) and proportional to temperature and resistance.

**Over-dispersion**\
When the variance of count data exceeds the mean, indicating extra variability beyond what a Poisson model predicts.

**Power spectral density (PSD)**\
The distribution of signal power across frequencies. For a random process, S(f) gives the power per unit frequency bandwidth.

**Q–Q plot (quantile-quantile plot)**\
A graphical method comparing the quantiles of observed data against theoretical quantiles (e.g., from a Gaussian distribution). Deviations from a straight line indicate departures from the reference distribution.

**Shot noise (quantum projection noise)**\
Fundamental noise arising from the discrete nature of particles or quanta. For counting experiments, follows Poisson statistics with variance equal to mean.

**Welch's method**\
A technique for estimating power spectral density by averaging periodograms from overlapping, windowed data segments. Reduces variance at the cost of frequency resolution.

**White noise**\
Noise with constant power spectral density across all frequencies. In ADEV plots, appears as slope −1/2 (i.e., σ\_y(τ) ∝ τ^{−1/2}).

**Wilson score interval**\
A confidence interval for binomial proportions that maintains accurate coverage even for small sample sizes or extreme probabilities, unlike the simpler Wald interval.

***

### Appendix B: Minimal Python implementation snippets

Below are compact code examples for typical analyses. They are not a full library, but a starting point.

```python
# Binomial Wilson interval
import statsmodels.stats.proportion as smp

N = 10
k = 0
alpha = 0.05  # 95% confidence
ci_low, ci_high = smp.proportion_confint(count=k, nobs=N, alpha=alpha, method="wilson")
print(ci_low, ci_high)

# Poisson Garwood interval
from statsmodels.stats.proportion import poisson_twosided_confint
k = 3  # observed count
ci_low, ci_high = poisson_twosided_confint(k, alpha=0.05, method='exact')


# Poisson dispersion test
import numpy as np
from scipy.stats import chi2

x = np.array([...])  # counts
N = len(x)
xbar = x.mean()
s2 = x.var(ddof=1)
chi2_stat = (N - 1) * s2 / xbar
p_value = 1 - chi2.cdf(chi2_stat, df=N-1)
print("chi2 =", chi2_stat, "p =", p_value)


# Overlapping Allan deviation (using allantools)
import allantools
import numpy as np

y = np.array([...])  # fractional frequency data
rate = 1.0  # sampling rate in Hz
taus, adevs, errors, ns = allantools.oadev(y, rate=rate, data_type="freq")


# Welch PSD estimate
import numpy as np
from scipy.signal import welch

fs = 1.0  # sampling rate in Hz
x = np.array([...])  # time series
f, Sx = welch(x, fs=fs, nperseg=1024, noverlap=512, window="hann")


# Q–Q plot against Gaussian
import numpy as np
import matplotlib.pyplot as plt
from scipy import stats

x = np.array([...])
stats.probplot(x, dist="norm", plot=plt)
plt.xlabel("Theoretical quantiles")
plt.ylabel("Sample quantiles")
plt.show()
```

***

### References

1. L. D. Brown, T. T. Cai, and A. DasGupta (2001). Interval estimation for a binomial proportion. _Statistical Science_ 16, 101–133.
2. J. A. Sedlacek _et al._ (2018). Evidence for multiple mechanisms underlying surface electric-field noise in ion traps. _Physical Review A_ 98, 063430.
3. D. W. Allan (1966). Statistics of atomic frequency standards. _Proceedings of the IEEE_ 54, 221–230.
4. NIST/SEMATECH (2012). e-Handbook of Statistical Methods. Section 1.3.5.15 (Chi-square test for variance).
5. Statistics LibreTexts (2019). Chi-Square Goodness-of-Fit Test. (Discussion of expected counts ≥5 rule of thumb.), a) W. G. Cochran (1952). The χ² test of goodness of fit. Annals of Mathematical Statistics 23, 315–345.
6. D. W. Howe, D. W. Allan, and J. A. Barnes (1981). Properties of oscillator signals and measurement methods. _Proc. 35th Annual Frequency Control Symposium_, 1–47.
7. W. J. Riley (2008). Handbook of Frequency Stability Analysis. NIST Special Publication 1065.
8. P. D. Welch (1967). The use of fast Fourier transform for the estimation of power spectra: A method based on time averaging over short, modified periodograms. _IEEE Transactions on Audio and Electroacoustics_ 15, 70–73.
9. J. Labaziewicz _et al._ (2008). Suppression of heating rates in cryogenic surface-electrode ion traps. _Physical Review Letters_ 100, 013001.
10. M. Brownnutt, M. Kumph, P. Rabl, and R. Blatt (2015). Ion-trap measurements of electric-field noise near surfaces. _Reviews of Modern Physics_ 87, 1419–1482.
