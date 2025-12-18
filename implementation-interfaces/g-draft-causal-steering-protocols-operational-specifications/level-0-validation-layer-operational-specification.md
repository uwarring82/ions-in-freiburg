---
description: Near-Parameter-Free Network Coherence Validation
---

# Level 0 Validation Layer (Operational Specification)

## Level 0 — Parameter-Free Network Coherence Validation

{% hint style="info" %}
author: _U. Warring_\
affiliation: _Institute of Physics, University of Freiburg_\
&#xNAN;_&#x76;ersion: 0.1.0_\
last\_updated: _2025-12-18_\
license: _CC BY 4.0_\
\
**Disclaimer** – This document specifies a statistical validation gate for multi-link timing-network residuals. It is intended as an operational, auditable precondition for downstream inference or control protocols. It does not establish causality, attribution, or steering laws. A positive coherence detection indicates statistically significant shared structure under the stated model class and assumptions; it does not, by itself, imply a physical mechanism or causal direction. A null result is informative and bounds shared processes below detectability at the tested scales.\\
{% endhint %}

#### How to Cite This Specification

**Stable citation format**:

> Warring, U. (2025). _Level 0 — Parameter-Free Network Coherence Validation_ (Version 0.1.0). Ordinans Series.

**Version-specific**: Always cite the version number. Thresholds and schemas are **locked** within a version.

**For specific results**: Reference section numbers (e.g., “Section 5.2, robust noise-floor estimation”).

***

### 0. Summary (Operator View)

**Purpose:** Decide whether observed cross-link correlations are distinguishable from finite-sample noise **before** any causal inference or steering is attempted.

**Inputs:** comparison streams (z(t)) and network topology (H)

**Outputs:** `level0_certificate.json` containing spectral test results, kill flags, and provenance hashes

**Hard stops (“kill conditions”):** autocorrelation, conditioning, block count, and MP-validity regime checks.

***

### 1. Scope and Guardrails

#### 1.1 In scope

* Statistical detection of shared structure in residuals via covariance spectra
* Multi-(\tau) execution contract with trial-factor correction
* A machine-readable certificate binding results to topology and data provenance

#### 1.2 Out of scope (explicit)

* Causality (“who drives whom”), attribution, and physical interpretation
* Feedback laws, feedforward filters, closed-loop control
* Relativistic modelling, oscillator physics, or platform-specific noise models

> **Operational invariant**\
> No downstream protocol may run unless a valid Level 0 certificate exists for the relevant (\tau)-range and topology hash.

***

### 2. System Model

#### 2.1 Topology

A timing network with (N) nodes and (M) comparison links is encoded by the **incidence matrix** \[ H \in \mathbb{R}^{M\times N}. ] Each row corresponds to a signed link measurement.

#### 2.2 Observations

Measured link streams: \[ z(t) = H,x(t) + \eta(t), ] where (x(t)) are latent node states and (\eta(t)) is link-local noise.

Only (z(t)) and (H) are required.

***

### 3. Input/Output Contracts

#### 3.1 Input data format (hard gate)

**File format:** HDF5

**Required structure**

/comparisons/link\_001   (T,)

/comparisons/link\_002   (T,)

…

/comparisons/link\_M     (T,)

**Required HDF5 attributes**

* `sampling_interval` : float (seconds)
* `unit` : one of `seconds`, `phase_cycles`, `fractional_frequency`
* `link_topology_sha256` : hex digest binding data to the topology file

**Kill:** missing any required attribute → `input_nonconformant`

#### 3.2 Topology file format

**File:** `network.incidence_matrix.csv`

Header:

link\_id,node\_i,node\_j,sign\_i,sign\_j

Row convention: a single link between nodes (i) and (j) is represented by a row with (+1) at node (i) and (-1) at node (j). Any equivalent signed convention is admissible **if** it is consistent and hashed.

***

### 4. Residual Formation (Gauge Projection)

#### 4.1 Projection matrix construction (explicit)

Gauge freedom (absolute time) is removed by projection onto the row space of (H): \[ P = H,H^{+}, ] where (H^{+}) is the Moore–Penrose pseudoinverse.

**Implementation note:** use a numerically stable pseudoinverse for rank-deficient matrices.

**Connectivity validation:** for a connected network, \[ \mathrm{rank}(P) = N-1. ]

#### 4.2 Residual definition

Residuals: \[ r(t) = P,z(t). ]

***

### 5. Blocked Covariance Estimation

#### 5.1 Blocking

For a chosen block duration (\tau), segment (r(t)) into (B) non-overlapping blocks, yielding the matrix \[ R(\tau)\in\mathbb{R}^{M\times B}. ]

#### 5.2 Sample covariance with regularisation

\[ \widehat{C}(\tau) = \frac{1}{B}R(\tau),R(\tau)^{\mathsf T} + \varepsilon\_{\mathrm{reg\}} I, \qquad \varepsilon\_{\mathrm{reg\}} = 10^{-12},\mathrm{Tr}!\left(\frac{1}{B}R R^{\mathsf T}\right). ]

***

### 6. Spectral Decision Logic (RMT Gate)

Let ({\lambda\_k}\_{k=1}^{M}) denote eigenvalues of (\widehat{C}(\tau)), sorted descending.

#### 6.1 MP boundary

Define the aspect ratio \[ q = \frac{M}{B}. ] The upper Marčenko–Pastur edge is \[ \lambda\_{\mathrm{MP\}} = \sigma^2(1+\sqrt{q})^2, ] where (\sigma^2) is the noise-floor variance.

#### 6.2 Noise-floor estimation (robust)

**Iterative median clipping (max 3 iterations)**

1. Initialise (\hat{\sigma}^2 \leftarrow \mathrm{median}({\lambda\_k}))
2. Compute (\lambda\_{\mathrm{MP\}}(\hat{\sigma}^2))
3. Remove all (\lambda\_k > \lambda\_{\mathrm{MP\}})
4. Recompute (\hat{\sigma}^2) on remaining eigenvalues
5. Repeat until convergence or iteration limit

**Kill:** if more than (M/2) eigenvalues are clipped → `noise_floor_contaminated`

***

### 7. Coherence Metrics

#### 7.1 Effective rank

\[ \widehat{R}_{\mathrm{eff\}}(\tau) = #{k : \lambda\_k > \lambda_{\mathrm{MP\}}}. ]

#### 7.2 Coherence index

\[ \widehat{\kappa}(\tau) = \frac{\sum\_{k=1}^{\widehat{R}_{\mathrm{eff\}}}\lambda\_k}{\sum_{k=1}^{M}\lambda\_k}. ]

#### 7.3 Uncertainty on (\widehat{\kappa}) (explicit)

Estimate (\Delta\widehat{\kappa}) via **block bootstrap**:

* resample blocks of (R(\tau)) with replacement
* (L=50) blocks per replicate
* (10^{4}) replicates

\[ \Delta\widehat{\kappa} = \mathrm{std}\left({\widehat{\kappa}^{(b)\}}\right). ]

***

### 8. Hypothesis Test

#### 8.1 Hypotheses

* (\mathcal{H}\_0): residuals consistent with finite-sample noise (no detectable shared mode)
* (\mathcal{H}\_1): at least one shared mode exceeds the noise bulk

#### 8.2 Decision rule (hard)

Reject (\mathcal{H}_0) at scale (\tau) if \[ \widehat{R}_{\mathrm{eff\}}(\tau)\ge 1 \quad\land\quad \lambda\_1(\tau) > \lambda\_{\mathrm{MP\}}(\tau). ]

***

### 9. Kill Conditions (Hard Stops)

<table><thead><tr><th width="190">Condition</th><th width="170">Threshold</th><th>Meaning</th></tr></thead><tbody><tr><td>Autocorrelation</td><td>\(|\rho_1| &#x3C; 0.1\)</td><td>Blocks sufficiently independent</td></tr><tr><td>Conditioning</td><td>\(\mathrm{cond}(\widehat{C}) &#x3C; 10^8\)</td><td>Numerical stability (no near-singularity)</td></tr><tr><td>Block count</td><td>\(B \ge 200\)</td><td>RMT convergence regime</td></tr><tr><td>MP validity</td><td>\(M/B \le 0.1\)</td><td>Do not apply MP threshold outside regime</td></tr><tr><td>Noise-floor contamination</td><td>\(>\!M/2\) clipped eigenvalues</td><td>Median estimator invalid (dense signal)</td></tr><tr><td>Input conformant</td><td>Required HDF5 attrs present</td><td>Provenance and schema integrity</td></tr></tbody></table>

***

### 10. Multi-Scale Execution Contract (Multi-(\tau))

#### 10.1 Sweep definition

Choose (\tau)-grid: \[ \tau \in {\tau\_{\min}, 2\tau\_{\min}, 4\tau\_{\min}, \dots, \tau\_{\max\}}. ]

#### 10.2 Trial-factor correction

If testing (N\_\tau) scales, apply Bonferroni correction: \[ \alpha \rightarrow \alpha/N\_\tau. ]

#### 10.3 Integration rule

Report \[ \widehat{R}_{\mathrm{eff\}} = \max_{\tau}\widehat{R}\_{\mathrm{eff\}}(\tau), ] and store all per-(\tau) results in the certificate under `"multi_tau_results"`.

***

### 11. Certificate Artifact (Machine-Readable Output)

#### 11.1 Required fields

```json
{
  "protocol_version": "0.1.0",
  "execution_timestamp": "2025-12-18T00:00:00Z",
  "topology_hash": "sha256:…",
  "data_provenance": {
    "source_file": "…",
    "link_topology_sha256": "…",
    "preprocessing_hash": "sha256:…"
  },
  "parameters": {
    "M": 12,
    "tau_grid": [1000, 2000, 4000, 8000, 16000],
    "B_min": 200,
    "alpha": 0.01,
    "bonferroni_alpha": 0.002
  },
  "results": {
    "R_eff_max": 1,
    "tau_at_R_eff_max": 8000,
    "multi_tau_results": [
      {
        "tau": 8000,
        "B": 500,
        "lambda_MP": 1.23,
        "top_eigenvalues": [2.45, 1.18, 1.12],
        "R_eff": 1,
        "kappa": 0.034,
        "dkappa": 0.008,
        "decision": "reject_H0"
      }
    ]
  },
  "kill_flags": {
    "input_nonconformant": false,
    "autocorr_violation": false,
    "condition_violation": false,
    "block_count_violation": false,
    "mp_validity_violation": false,
    "noise_floor_contaminated": false
  }
}
```

#### 11.2 Contract with higher levels

* If any kill\_flags.\* == true → downstream modules must not run
* If R\_eff\_max == 0 → downstream modules must not run
* If decision == "reject\_H0" → downstream modules may proceed only on certified subspace

***

### 12. Figures

#### Figure 0-A — Validation Flow (Mermaid)

graph LR\
subgraph L0\[Level 0: Validation Loop]\
direction LR\
Z\[z(t)] -->|Projection P| R\[r(t)]\
R -->|Block into B| B1\[Blocks]\
B1 -->|Covariance Ĉ(τ)| C\[Ĉ]\
C -->|Eigenvalues| L\[λ\_k]\
L -->|MP Threshold| MP\[λ\_MP]\
L -->|Compute| K\[κ̂, R̂\_eff]\
K --> D{Valid?}\
D -- Yes --> Cert\[Issue Certificate]\
D -- No --> Kill((Kill Stop))\
end

#### Figure 0-B — Spectral Gate Intuition (Operator Schematic)

> Interpretation: in (\mathcal{H}\_0), all eigenvalues remain within the MP bulk. A detectable shared mode produces a top eigenvalue (\lambda\_1) separating from the bulk.

eigenvalue density ^ | \* | \* \* signal spike (λ1) | \* \* | \* \* \* \* \* \* \* \* \* noise bulk (MP) +----------------------------------------------> λ λ\_MP

### 13. Interpretation Rules (Guardian)

* (\widehat{\kappa} > 0) does not imply causality or a specific mechanism
* A null result ((\widehat{R}\_{\mathrm{eff\}}=0)) is informative and bounds shared coupling below detectability
* MP threshold use is void outside (M/B \le 0.1)
* Any post-hoc threshold modification requires a new version

***

### References

1. Marčenko, V. A. & Pastur, L. A. (1967). Distribution of eigenvalues for some sets of random matrices. _Math. USSR-Sb._ 1, 457–483.
2. Baik, J., Ben Arous, G. & Péché, S. (2005). Phase transition of the largest eigenvalue for nonnull complex sample covariance matrices. _Ann. Probab._ 33, 1643–1697.
3. Johnstone, I. M. (2001). On the distribution of the largest eigenvalue in principal components analysis. _Ann. Stat._ 29, 295–327.
4. Anderson, T. W. (2003). _An Introduction to Multivariate Statistical Analysis_ (3rd ed.). Wiley.
5. Efron, B. & Tibshirani, R. (1993). _An Introduction to the Bootstrap_. Chapman & Hall/CRC.
6. Ledoit, O. & Wolf, M. (2004). A well-conditioned estimator for large-dimensional covariance matrices. _J. Multivar. Anal._ 88, 365–411.

***

### Version History

<table><thead><tr><th width="120">Version</th><th width="140">Date</th><th>Changes</th></tr></thead><tbody><tr><td>0.1.0</td><td>2025-12-18</td><td>Initial operational specification: explicit projection, robust noise-floor estimation, multi-\(\tau\) contract, schema + certificate, Mermaid figures, locked kill conditions</td></tr></tbody></table>

\`\`\`
