---
description: A Tier-2 Coordination Framework for Audible, Verifiable Failure
---

# Causal Comparison Networks

***

### Metadata

| Field        | Value                                     |
| ------------ | ----------------------------------------- |
| Version      | 1.2.1                                     |
| Status       | Local candidate framework (Harbour entry) |
| Scope        | Tier 0–2 only; Tier-3 handbooks optional  |
| Last revised | January 2026                              |

> **Endorsement Marker (mandatory)**
>
> This framework does not claim parity with domain standards in (i) quantum metrology, (ii) time transfer (PTP/GNSS), or (iii) rail safety regulation. Cross-domain mapping is analogical and handbook-level, not a validated law.

***

### Reader's Map

**What this is:** A minimal coordination framework for distributed systems that depend on comparisons across distance.

**What this is not:** A theory of ions, clocks, or trains. This framework does not define their state spaces, dynamics, or domain-specific physics.

**Core claim:** These systems work not because their nodes are good, but because their comparisons are causally closed, auditable, and forced to fail audibly when geometry or assumptions break.

***

### 1. Coastlines (Tier 0)

Coastlines are falsifiable boundary conditions. They constrain what coordination can mean; they do not prescribe how to achieve it.

#### C1 — Comparison Causality Bound

A comparison over baseline $$L_{\mathrm{comparison}}$$ is coherent within window $$T$$ only if:

<p align="center"><span class="math"> L_{\mathrm{comparison}} \le v_{\mathrm{info}} \cdot T </span></p>

**Effective information velocity.** The term $$v_{\mathrm{info}}$$ is not the medium limit (e.g., $$c$$); it is the effective information velocity including all latencies:

<p align="center"><span class="math"> v_{\mathrm{info}} = \frac{L_{\mathrm{comparison}}}{\tau_{\mathrm{flight}} + \tau_{\mathrm{switch}} + \tau_{\mathrm{proc}} + \tau_{\mathrm{queue}}} </span></p>

**Falsifiable test:** Intentionally operate with $$L_{\mathrm{comparison}} > v_{\mathrm{info}} \cdot T$$.

**Operational failure criterion:** The null hypothesis $$H_0$$: "loop residuals consistent with declared noise model" is rejected at pre-registered significance level $$\alpha$$ for at least $$M$$ consecutive comparison cycles. The values of $$\alpha$$ and $$M$$ must be declared before operation.

#### C2 — No Shared Node Ontology

Node "state" is a domain placeholder only. No commutativity, continuity, or shared dynamics is assumed across domains.

Only edge comparisons are in scope.

**Implication:** The framework cannot assert that "ion phase" and "clock offset" are the same kind of quantity. It can only assert that both participate in comparison graphs subject to C1.

***

### 2. Tier Structure

<table><thead><tr><th width="80.33203125">Tier</th><th width="444.078125">Content</th><th>Authority</th></tr></thead><tbody><tr><td>0</td><td>Causality bound (C1), ontology separation (C2)</td><td>This framework</td></tr><tr><td>1b</td><td>Raw comparison logs, timestamps, calibration metadata</td><td>Domain standards (referenced)</td></tr><tr><td>2</td><td>VCL topology, <span class="math">\eta_{\mathrm{CEP}}</span> metric, I1–I3 interface locks</td><td>This framework</td></tr><tr><td>3</td><td>Bayesian estimators, control heuristics, optimisation</td><td>Handbooks (optional)</td></tr></tbody></table>

***

### 3. Tier-1b Constituents (Referenced, Not Redefined)

This framework does not replicate domain standards. Implementations must cite the relevant specifications directly.

#### Telecom Timing

For PTP-based phase and time distribution, refer to:

* **ITU-T G.8275.1** — Telecom profile for phase/time synchronisation with full timing support from the network

#### High-Precision Synchronisation

For sub-nanosecond time transfer over Ethernet, refer to:

* **White Rabbit** — PTP-based synchronisation protocol developed at CERN; extends IEEE 1588 with synchronous Ethernet

#### GNSS Integrity

For satellite-based timing and integrity monitoring, refer to:

* **RAIM (Receiver Autonomous Integrity Monitoring)** — consistency-based fault detection using redundant pseudorange measurements

#### Railway Safety

For functional safety lifecycle and integrity requirements, refer to:

* **EN 50126 / 50128 / 50129** — CENELEC standards for railway RAMS (Reliability, Availability, Maintainability, Safety)

***

### 4. Verifiable Closure Loops (VCL)

VCL is the primary Tier-2 coordination primitive. It converts the abstract causality bound (C1) into testable topology constraints.

#### Definition

A VCL is a closed cycle of directed comparisons. The aggregate residual must be statistically compatible with zero under a pre-registered test:

<p align="center"><span class="math"> \Delta_{\mathrm{loop}} = \sum_{\text{edges in loop}} y_{ij} </span></p>

#### Mandatory Constraints

Every VCL used for integrity claims must satisfy:

1. **Cardinality:** Loop length ≥ 3 nodes (avoids degenerate two-node ambiguity)
2. **Causality:** Each edge satisfies C1 for the same comparison window
3. **Directedness:** Comparisons are directed unless symmetry is explicitly validated; reversal is not assumed
4. **Heterogeneity:** At least one node or link class with orthogonal failure modes (different technology, supplier, physics channel, or trust boundary)
5. **Pre-registration:** Before operation, declare for each loop:
   * Test statistic
   * Noise model assumption class
   * Significance level $$\alpha$$
   * Decision threshold

**Scope of heterogeneity requirement:** Heterogeneity is mandatory for every loop that supports an integrity claim (i.e., any loop whose residual is used to generate alarms, certify system state, or publish to external parties). Loops used solely for internal diagnostics or optimisation may be homogeneous but cannot support integrity claims.

#### Rationale for Heterogeneity

A homogeneous loop can suffer common-mode failures invisible to residual checks. Orthogonal failure modes ensure that at least one comparison channel remains informative when others fail systematically.

#### Falsifiable Tests

* **Bias injection:** Inject a known bias on one edge. Prediction: $$\Delta_{\mathrm{loop}}$$ shifts with predicted sign and magnitude.
* **Heterogeneity removal:** Remove one node class. Prediction: false-negative rate increases measurably.

***

### 5. Causal Efficiency Protocol (CEP)

CEP quantifies how close the system operates to its causal boundary. It is an in-domain operating dial, not a cross-domain comparison metric.

#### Notation

Use $$\eta_{\mathrm{CEP}}$$ to distinguish from other efficiency parameters.

#### Operational Definition

<p align="center"><span class="math"> \eta_{\mathrm{CEP}}(\tau) = \frac{\text{achieved comparison precision}}{\text{architecture-limited precision}} </span></p>

Both numerator and denominator must be stated in the same in-domain units (e.g., fractional time error, phase variance, or decision uncertainty).

**Denominator constraints:** The architecture-limited precision must be derived from declared geometry and latency bounds (C1) and the pre-registered noise class. It must not be derived from retrospective fit to observed data.

**No cross-domain normalisation is implied.** The value of $$\eta_{\mathrm{CEP}}$$ in an ion array cannot be compared directly to $$\eta_{\mathrm{CEP}}$$ in a clock network without separate validation.

#### Mandatory Alarm S1 (Fragmentation)

If correlation length $$\xi < L_{\mathrm{comparison}}$$, the system has fragmented. CEP must flag: **"collective sensing invalid"**.

**Falsifiable test:** Deliberately reduce correlation (add controlled decoherence, induce packet-delay chaos, break timetable coupling). Prediction: S1 triggers prior to performance collapse, with published false-alarm rate.

***

### 6. Inference Stack (Tier-3 Boundary)

The inference stack is a Tier-3 handbook concern. Only the interface between layers is defined at Tier 2.

#### Layer A — Estimator (Bayesian)

* **Purpose:** State fusion, gap filling, prediction
* **Permitted:** Adaptive; may be complex
* **Required outputs:** Residuals and uncertainty estimates

#### Layer B — Auditor (Frequentist)

* **Purpose:** Invariant verification only
* **Constraint:** Must not learn; checks are pre-registered
* **Inputs:** Raw comparisons and estimator residuals
* **Required outputs:** Binary alarms and recorded $$p$$-values/thresholds

#### Design Principle

Auditors remain interpretable even if estimators are opaque. The Auditor layer is the external trust surface; the Estimator layer is permitted to be a black box.

***

### 7. Interface Locks (Tier 2)

Interface locks define explicit causal actions when layers conflict. They are mandatory; no implementation may bypass them.

#### I1 — Hard Conflict (Audible Failure)

**Trigger:** Auditor alarm fires.

**Required actions:**

1. Freeze Estimator adaptation
2. Enter HOLD state
3. Require human or supervisory review to resume

**No automatic override permitted.**

#### I2 — Soft Conflict

**Trigger:** Residuals are marginal but sub-threshold.

**Required actions:**

1. Continue operation
2. Increase logging frequency and test cadence
3. Do not suppress either signal

#### I3 — Nonstationarity Gate (Explicit Degradation)

**Trigger:** Frequentist test power falls below declared minimum.

**Computable criterion:** Test power is computed under the pre-registered effect size $\delta$ and noise class. Trigger when power $$< p_{\min}$$. The values of $$\delta$$ and $$p_{\min}$$ must be declared before operation.

**Required actions:**

1. Degrade to a simpler coordination mode (e.g., logical ordering, reduced claims)
2. Maintain audit logging
3. Resume full operation only after stationarity is re-established

**Re-establishment criterion:** Return to full tier requires:

* (a) Frequentist test power $$\ge p_{\min}$$, and
* (b) Posterior variance within declared envelope for $$\ge N$$ consecutive comparison cycles

The value of $$N$$ must be declared before operation.

***

### 8. Degradation Modes and Minimum Viable Topology

Graceful degradation is mandatory. Systems must define behaviour under partial failure.

#### Minimum Integrity Topology

At least one heterogeneous VCL loop must remain closed for integrity claims to be valid.

#### Degradation Sequence

<table><thead><tr><th width="262.796875">Condition</th><th width="335.046875">Capability</th><th>Auditability</th></tr></thead><tbody><tr><td>All loops closed</td><td>Full sensing + coordination</td><td>Full</td></tr><tr><td>Some loops broken</td><td>Reduced sensing; coordination continues</td><td>Full</td></tr><tr><td>All loops broken</td><td>Sensing disabled; coordination only</td><td>Full</td></tr><tr><td>Heterogeneity lost (all remaining loops homogeneous)</td><td>Safe mode</td><td>Full</td></tr></tbody></table>

#### Safe Mode Semantics

* Reduced capability
* No sensing or optimisation claims
* No integrity claims (heterogeneity requirement not satisfied)
* Audit logging continues
* Explicit flag to external systems

***

### 9. Domain Linkages

The following linkages are explicit, narrow, and defensible. They do not assert equivalence of domain physics.

#### Ion Arrays (Perturbation Sensing)

* **Comparisons:** Phase or frequency estimates across sites
* **VCL interpretation:** Closed transport or interrogation cycles
* **CEP use:** Monitors when correlation length falls below baseline (fragmentation → sensing invalid)
* **Tier-3 note:** Quantum specifics (non-commuting observables, QFI) belong in domain handbooks; they are not asserted here

#### Global Timing Systems (Clock Networks)

* **Comparisons:** Time or phase transfer measurements
* **VCL interpretation:** Closure across triangles or multi-hop paths
* **Reference constituents:** ITU-T G.8275.1, White Rabbit, RAIM

#### Train Networks (Schedule Integrity)

* **Comparisons:** Event timestamps, occupancy states, interlocking transitions
* **VCL interpretation:** Loop closures in schedule and route constraints
* **Reference constituents:** EN 50126/50128/50129 RAMS framework

***

### 10. Verification Plan

A conforming implementation must demonstrate the following before claiming CCN compliance.

#### Pre-Deployment

1. **Pre-register VCL tests:** Declare $$\alpha$$, $$M$$, noise class, and test statistic for each loop
2. **Pre-register I3 parameters:** Declare effect size $$\delta$$, minimum power $$p_{\min}$$, and re-entry cycle count $$N$$
3. **Declare CEP parameters:** In-domain precision units, geometry/latency bounds for denominator, fragmentation threshold, false-alarm rate

#### Injection Tests

4. **Bias injection:** Confirm $$\Delta_{\mathrm{loop}}$$ responds with predicted sign and magnitude
5. **Delay injection:** Confirm C1 violation triggers alarm after $$M$$ cycles
6. **Node dropout:** Confirm minimum viable topology holds
7. **Topology break:** Confirm safe mode engages

#### Interface Verification

8. **I1 holds:** Demonstrate freeze under alarm; confirm no automatic override path exists
9. **I3 degradation:** Demonstrate tier downgrade when power $$< p_{\min}$$ and clean re-entry via declared criterion

#### Reporting

10. **Publish:** False-alarm and missed-detection rates for each domain, intra-domain, before any cross-domain narrative

***

### 11. What This Framework Does Not Claim

* No shared ontology across quantum, classical, or operational states
* No universal noise model
* No cross-domain commensurability of $$\eta_{\mathrm{CEP}}$$ or residuals without separate validation
* No replacement of domain safety or regulatory standards
* No optimisation guarantees beyond causal geometry

***

### 12. Reference Anchors

The following are curated entry points for domain-specific detail. This framework references but does not replicate their content.

| Domain              | Standard             | Scope                                |
| ------------------- | -------------------- | ------------------------------------ |
| Telecom timing      | ITU-T G.8275.1       | PTP phase/time distribution profile  |
| High-precision sync | White Rabbit (CERN)  | Sub-ns synchronisation over Ethernet |
| GNSS integrity      | RAIM literature      | Consistency-based fault detection    |
| Railway safety      | EN 50126/50128/50129 | RAMS and functional safety lifecycle |

***

### Appendix A: One-Paragraph Summary

Causal Comparison Networks (CCN) is a Tier-2 coordination framework for distributed systems whose performance depends on comparisons across distance. It defines two coastlines: a causality bound (C1) limiting coherent comparison to $$L_{\mathrm{comparison}} \le v_{\mathrm{info}} \cdot T$$, and an ontology separation (C2) forbidding assumptions about shared node state across domains. The framework introduces Verifiable Closure Loops (VCL) as topology constraints with mandatory heterogeneity and pre-registration, and a Causal Efficiency Protocol ($$\eta_{\mathrm{CEP}}$$) as an in-domain operating dial. Interface locks (I1–I3) enforce audible failure: hard conflicts freeze adaptation, soft conflicts increase vigilance, and nonstationarity triggers explicit degradation. Domain applications (ion arrays, clock networks, train schedules) are linked analogically at the comparison-graph level; domain-specific physics remains in Tier-3 handbooks. The framework does not replace regulatory standards; it provides a common coordination layer that forces systems to fail audibly when causal geometry or assumptions break.

***

### Appendix B: Terminology

**Lock-Key Rule:** Framework concepts are stable (lock); domain interpretations are free (keys); authority derives from use, not endorsement. This principle ensures that the coastlines defined here cannot be captured or redefined by any single implementation or authority.

**Harbour-compatible open-science practice:** A documentation architecture that separates stable scientific principles (coastlines) from interpretive tools (sails and repair kits) and operational procedures (handbooks). Distribution scales; authority does not.

***

### Harbour Index Tags

`coordination-architecture` · `verifiable-loops` · `causal-geometry` · `degradation-pathways` · `tier-2-framework`

***

_Framework maintained under Harbour-compatible open-science practice. Lock-Key Rule applies: concepts stable (lock), interpretations free (keys), authority from use not endorsement._
