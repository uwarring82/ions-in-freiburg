---
description: >-
  Parent scaffold with space and time siblings: inheritance, symmetry, necessary
  asymmetry, and cross-disciplinary structural templates
---

# Spacetime Architecture — Unified Scaffold

{% hint style="info" %}
**Author:** U. Warring\
**Affiliation:** Institute of Physics, University of Freiburg\
**Domain:** Spacetime parent and its space/time sibling projections\
**Epistemic status:** Unified structural scaffold\
**Version:** 0.4.4\
**Last updated:** 2026-01-09\
**License:** CC BY 4.0\
**Status:** Constitutional invariant framework\
**Domain:** Epistemic governance (human-bound, tool-mediated)\
**Non-status:** ❌ Not a curriculum · ❌ Not pedagogy · ❌ Not tool-specific
{% endhint %}

{% hint style="warning" %}
**\[ENDORSEMENT MARKER]**\
**Parent scaffold (metric, causality, comparison envelope):** The metric structure and causal ordering carry broad community endorsement in relativistic physics. The comparison envelope `L_comparison ≤ cτ` is a candidate boundary (v1.0, falsifiable); no parity implied with externally validated laws.\
**Sibling projections:** Structural framework; inherits endorsement status from parent and from cited external constraints.\
**Cross-disciplinary applications:** Foundational disciplines define or stress-test scaffold tiers. Applied disciplines inherit structure without modifying it. Domain authority remains with domain experts. \
\
&#xNAN;**\[COUNCIL ACTION REQUIRED]**\
Registry naming convention requires ratification before coastline drafting proceeds. See §13 Open Items. Guardian recommendation: Option A (parent-first) with alias stub for backward compatibility.&#x20;
{% endhint %}

***

### 1. Purpose and Scope

This document specifies a **single architectural scaffold** from which spatial and temporal frameworks project. It proceeds parent-first: the shared causal-metric structure is established before either sibling is introduced. Both siblings then appear together, permitting direct inspection of what they share and where they necessarily differ.

The scaffold is designed to serve two audiences:

1. **Specialists in foundational disciplines** requiring precise structural definitions for metrology, relativistic physics, distributed systems, and quantum information
2. **Researchers in applied disciplines** seeking a rigorous structural template for reasoning about events, ordering, and comparison (entry point: §10.2)

Both audiences share a common problem: how to establish **when** something happened, **where** it happened, and **how to compare** observations made at different times and places.

**In scope:**

* Parent scaffold: metric neighbourhoods, causal structure, comparison envelope
* Sibling projections: space ("where") and time ("when")
* Tier structure for each sibling
* Explicit symmetry and asymmetry analysis
* Foundational and applied discipline mappings

**Out of scope:**

* Detailed coastline content (deferred to tier documents)
* Metrological procedures, apparatus specifications (external constraints, citation-only)
* Metaphysical interpretation of spacetime ontology
* Domain-specific applications (deferred to discipline handbooks)

**Note on terminology:** This document uses a deliberative Council framework (Guardian, Architect, Integrator stances) as a governance structure for epistemic quality control. These terms map to standard roles: Guardian ≈ ethics/clarity editor; Architect ≈ structural reviewer; Integrator ≈ process coordinator. The framework ensures balanced, auditable deliberation but does not affect the technical content of the scaffold.

***

### 2. Parent Scaffold

#### 2.1 The spacetime stage

Events in the universe are located by specifying **where** and **when** they occur. The collection of all events forms a four-dimensional manifold: three dimensions answer "where"; one dimension answers "when." This manifold is the **spacetime stage** on which all physical processes unfold.

**Structural note:** In any domain, reasoning involves event claims (what/where/when) and comparison procedures. The physics scaffold provides the most explicit template for separating causal constraints from conventions. Cross-disciplinary applications use this template structurally; they do not require that domain events be redescribed as relativistic world-points.

#### 2.2 Metric structure

The **metric** `g_{μν}` is the rule for measuring separation between nearby events. It encodes:

* how spatial distances combine with temporal intervals
* how "nearness" is defined in each neighbourhood
* the local geometry that physical apparatus must respect

The metric is governed by General Relativity (external constraint, citation-only). This scaffold presupposes but does not re-derive relativistic field equations.

**Open frontier:** Approaches seeking to unify quantum field theory with gravity (string theory, loop quantum gravity, causal set theory, asymptotic safety) may modify or replace the smooth metric at extreme scales. This scaffold remains agnostic: it specifies structure at scales where the metric description is empirically validated. Future refinements would enter as updated external constraints, not as changes to scaffold architecture. See §11.1 for further discussion.

#### 2.3 Causal structure

**Light cones** partition all events relative to any given event P into three classes:

<table><thead><tr><th width="180.7265625">Class</th><th>Relation to P</th><th>Causal status</th></tr></thead><tbody><tr><td>Causal past</td><td>Can send signal to P</td><td>May influence P</td></tr><tr><td>Causal future</td><td>Can receive signal from P</td><td>May be influenced by P</td></tr><tr><td>Spacelike separated</td><td>Cannot exchange signals with P</td><td>Causally disconnected from P</td></tr></tbody></table>

Causal cones are defined **locally** by the metric. Global causal accessibility can be constrained by curvature and horizons (e.g., black hole event horizons, cosmological horizons), but the local light-cone structure never permits superluminal signalling. This constraint does not depend on observer, coordinate choice, or apparatus.

**Structural note:** Causal structure is the most portable element of this framework. Any domain concerned with cause and effect—tracing influence, establishing liability, reasoning about consequences—implicitly invokes causal ordering. The light-cone formalism provides the physics-grounded version; domain-specific causal models are approximations or projections suited to their evidence base.

#### 2.4 Comparison envelope (candidate boundary, v1.0)

When any two readings—whether clock ticks or ruler markings—are to be **compared**, the comparison process itself is bounded by causality. A reading at location A can only be meaningfully compared with a reading at location B if a signal can traverse the separation within the comparison interval.

**Candidate boundary statement:**

> During a comparator interval τ, the region over which comparison is causally possible satisfies:
>
> `L_comparison ≤ cτ`
>
> where c is the speed of light and τ is proper time along the comparator's worldline.

**Operational anchor:** A **comparison event** is a protocol that outputs a decision variable D (e.g., phase difference estimate, baseline ratio, synchronisation verdict) whose computation requires classical communication during τ (including local wiring or internal signal paths for co-located comparisons). The envelope bounds the spatial support of that communication graph. This definition excludes inferential use of pre-established correlations, which do not require communication during the comparison interval.

**Delayed comparison:** If readings are recorded now but compared later, τ refers to the later comparison interval—not the interval during which the readings were taken. The envelope then applies to that later interval's communication graph. This prevents the envelope from being trivially satisfied by delaying comparison indefinitely; the constraint binds whenever comparison actually occurs.

**Status:** This is a design boundary for comparison geometry—a constraint on what can be coherently compared, not a claim about what exists. It is Council-cleared, version-tagged (v1.0), and falsifiable.

**Falsifiable by:** Any verified experiment demonstrating a comparison event (as defined above) beyond this envelope without violating causal order.

**Clarification on quantum-assisted protocols:** Entanglement-based synchronisation and similar protocols do not violate the envelope. Correlations are established within causal access (during state preparation) and later exploited (during measurement); no classical information is transmitted faster than light during the comparison interval. A future handbook will specify a **syndrome set** defining operationally what constitutes a comparison event, including quantum-assisted cases.

#### 2.5 What the parent scaffold provides

<table><thead><tr><th width="198.11328125">Element</th><th>Character</th><th>Epistemic status</th></tr></thead><tbody><tr><td>4-D manifold</td><td>Structural container</td><td>Endorsed (standard relativity)</td></tr><tr><td>Metric <code>g_{μν}</code></td><td>Neighbourhood geometry</td><td>Endorsed (GR, citation-only)</td></tr><tr><td>Light cones</td><td>Causal partitioning</td><td>Endorsed (SR/GR, citation-only)</td></tr><tr><td>Comparison envelope</td><td>Causal access boundary</td><td>Candidate (v1.0, falsifiable)</td></tr></tbody></table>

Both siblings inherit all four elements. Neither sibling may contradict the parent.

***

### 3. Sibling Projections: Introduction

The parent scaffold answers: "What is the causal-geometric stage?"

The siblings answer: "How do we separately address the 'where' and the 'when'?"

A **projection** extracts one aspect of spacetime while presupposing the full parent structure. Projections are not reductions; the parent is not discarded when a sibling is invoked.

#### 3.1 Why two siblings?

Operationally, "where" and "when" are addressed by distinct apparatus:

* **Clocks** accumulate phase or count oscillations → answer "when"
* **Rulers** compare lengths or baselines → answer "where"

The distinction is not ontological (spacetime is unified) but **operational** (measurement protocols differ).

#### 3.2 Sibling inheritance rule

Every spatial or temporal tier inherits the parent scaffold in full. No tier may:

* violate causal ordering
* contradict metric structure
* exceed the comparison envelope without causal justification

***

### 4. Sibling Tier Structure

Both siblings share a **three-layer architecture**:

<table><thead><tr><th width="97.25390625">Layer</th><th width="234.1015625">Function</th><th>Epistemic character</th></tr></thead><tbody><tr><td><strong>Tier 1a</strong></td><td>Logical labels</td><td>Conventional (no metric content)</td></tr><tr><td><strong>Tier 1b</strong></td><td>Physical measurement</td><td>External constraints (metrology)</td></tr><tr><td><strong>Tier 2</strong></td><td>Coordination lock</td><td>Conventional (naming, organisation)</td></tr></tbody></table>

The comparison envelope resides at the **parent**, not at Tier 1. Both siblings inherit it; neither re-derives it.

***

### 5. Time Sibling ("When")

#### 5.1 Tier T1a — Logical temporal ordering

**Purpose:** Establish "before" and "after" without metric duration.

**Realisation:** Lamport clocks, vector clocks, happened-before relations, logical timestamps in distributed systems.

**Lamport clocks** provide a single scalar counter incremented on local events and updated on message receipt. They establish a partial order: if event A causally precedes event B, then the Lamport timestamp of A is less than that of B (but not conversely).

**Vector clocks** extend Lamport clocks by maintaining a vector of counters (one per process). They capture the full causal history: two events are causally ordered if and only if their vector timestamps are comparable. Vector clocks detect concurrency (when neither event causally precedes the other).

**Properties:**

* Provides partial order over events (Lamport) or full causal history (vector clocks)
* No seconds, no oscillator, no proper time
* Sufficient for sequencing and concurrency detection; insufficient for duration

**Boundary with T1b:** Logical order does not determine how much time elapses. Transition to T1b requires physical clocks.

**Foundational discipline:** Distributed systems and computer science provide the mathematical proofs that Lamport and vector clocks prevent causal violations in non-metric environments. These are not approximations of physical clocks; they are the canonical solution to ordering without duration.

#### 5.2 Tier T1b — Physical clocks

**Purpose:** Read **proper time** τ from the spacetime metric using physical apparatus.

**Realisation:** Atomic clocks (caesium, optical), Earth rotation (UT1 via VLBI), pulsar timing.

**Properties:**

* Proper time is a path integral: τ = ∫ ds along the clock's worldline
* Clocks measure τ, not coordinate time
* Drift between clocks reveals relative spacetime geometry

**External constraints (citation-only):**

* SI second (BIPM)
* TAI/UTC conventions (IERS)
* Pulsar timing models

**Inheritance from parent:** Physical clocks operate within the comparison envelope. Comparing tick N at clock A with tick N at clock B requires causal access within one period.

**Foundational discipline:** Metrology and relativistic physics provide the SI standards and the operational definition of the second that anchor this tier to the metric g\_{μν}. If the SI second were redefined, Tier T1b would update accordingly.

#### 5.3 Tier T2 — Calendar Lock (coordination)

**Purpose:** Convert proper-time readings into named intervals for human coordination.

**Lock structure:**

| Stage         | Function                                               |
| ------------- | ------------------------------------------------------ |
| Partition     | Divide time into days, months, years                   |
| Hierarchy     | Nest intervals (second → minute → hour → day → year)   |
| Epoch         | Anchor to reference event (e.g., CE epoch, Unix epoch) |
| Enumeration   | Assign names and numbers to intervals                  |
| Intercalation | Insert leap seconds, leap days as convention updates   |

**Properties:**

* Calendars are conventions, not physics
* Intercalation corrects drift between Tier 1b readings and Tier 2 labels
* Calendar changes do not alter proper time

**Foundational discipline:** Timekeeping authorities (IERS, BIPM) and astronomical conventions define the Calendar Lock's reference points and update rules. These are the "memory" layer that converts physical measurements into coordination tools.

***

### 6. Space Sibling ("Where")

#### 6.1 Tier S1a — Logical spatial labels

**Purpose:** Assign coordinate indices without metric distance.

**Realisation:** Grid coordinates, simulation meshes, address systems, graph-node identifiers, spatial adjacency vectors.

**Properties:**

* Labels provide identity and adjacency (topology) without scale
* "Node 7 is adjacent to Node 8" does not imply any physical distance
* Sufficient for addressing; insufficient for length

**Topology note:** S1a may encode metric topology (which points are neighbours) without encoding metric scale (how far apart neighbours are). Purely combinatorial graphs are a permitted special case.

**Structural parallel to vector clocks:** Just as vector clocks capture a process's complete causal history relative to all other processes, **spatial adjacency vectors** (SAVs) capture a topological signature of a node relative to a chosen reference structure (all nodes, a landmark set, or a neighbourhood), sufficient for connectivity and routing tasks. This enables concurrency detection in time (vector clocks) and connectivity analysis in space (adjacency vectors). Where vector clocks answer "what is my causal relationship to every other process?", SAVs answer "what is my topological relationship to my reference structure?"

Key realisations of SAVs include:

* **Vivaldi coordinates:** Self-organising coordinate systems where nodes estimate positions based on round-trip latencies (Dabek et al. 2004). Note: Vivaldi uses RTT as a physical proxy but without SI calibration; it is a hybrid structure sitting at the S1a/S1b boundary. Treat as approximate/heuristic until calibrated.
* **Graph embeddings:** Mapping graph nodes to coordinate spaces preserving adjacency structure
* **Landmark-based routing vectors:** Node distances to a fixed set of reference nodes enabling greedy routing

These structures operate entirely within Tier S1a: they encode topology and connectivity, not metric distance. The transition to physical distance (S1b) requires calibration against a metric observable (e.g., light travel time with SI traceability).

**Note on formal guarantees:** Vector clocks provide provably minimal causal history: they are the canonical, mathematically complete solution to distributed ordering. SAVs vary in formal strength. Some implementations (graph embeddings with bounded distortion, exact distance oracles) offer provable guarantees on topological fidelity. Others (Vivaldi coordinates, heuristic embeddings) are statistical approximations that converge under assumptions but do not guarantee uniqueness or minimality. The `tier-s1a-logical-grids.md` coastline will specify which SAV classes satisfy S1a requirements for different application contexts, distinguishing between:

* **Exact SAVs:** provably complete topological representation (e.g., full distance matrix, exact graph embedding)
* **Approximate SAVs:** statistically accurate under specified conditions (e.g., Vivaldi with convergence bounds)
* **Heuristic SAVs:** useful for routing/addressing but without formal guarantees

**Boundary with S1b:** Logical labels and adjacency vectors do not determine physical separation. Transition to S1b requires physical rulers. Logical topology cannot claim proximity that would exceed causal reach (comparison envelope) when validated at S1b.

**Calibration criterion:** Transition from S1a to S1b is achieved when logical coordinates map to metric observables with documented SI traceability and stated measurement uncertainty. Until this criterion is satisfied, coordinates remain S1a structures regardless of whether they use physical proxies (e.g., RTT).

**Foundational discipline:** Graph theory and network science provide the mathematical structures for logical spatial labelling and adjacency vectors. Database indexing, memory addressing, and overlay network routing in computer science are direct applications of S1a structure.

#### 6.2 Tier S1b — Physical rulers

**Purpose:** Read **proper length** from the spacetime metric using physical apparatus.

**Realisation:** Interferometers, optical cavities, VLBI baselines, satellite laser ranging (SLR).

**Properties:**

* Proper length is defined with respect to a specified simultaneity slice (typically the ruler's instantaneous rest frame in flat spacetime); the slice choice is part of the measurement protocol (details deferred to coastline)
* Rulers measure metric separation, not coordinate distance
* Baseline comparisons reveal spatial geometry

**External constraints (citation-only):**

* SI metre (BIPM, defined via c and second)
* ITRF realisations (IERS)
* Geodetic reference ellipsoids

**Inheritance from parent:** When comparing baselines using any probe (light-based, clock-based, or other), the comparison is bounded by `L_comparison ≤ cτ`. The envelope is inherited, not re-derived.

**Foundational discipline:** Geodesy and space geodetic techniques (VLBI, SLR, GNSS) provide the operational infrastructure for Tier S1b. These disciplines define how the SI metre is realised on planetary scales.

#### 6.3 Tier S2 — Map Lock (coordination)

**Purpose:** Convert spatial measurements into named regions for human coordination.

**Lock structure:**

| Stage           | Function                                                       |
| --------------- | -------------------------------------------------------------- |
| Partition       | Divide space into nameable regions                             |
| Hierarchy       | Nest regions (continent → country → city → address)            |
| Reference point | Anchor to datum (meridian, reference ellipsoid, origin marker) |
| Enumeration     | Assign names, codes, postal identifiers                        |
| Updates         | Revise for datum shifts, boundary changes, tectonic motion     |

**Properties:**

* Maps are conventions, not physics
* Reference-frame realisations (e.g., ITRF2020) are external constraints, citation-only
* Administrative boundary changes do not alter metric structure

**Foundational discipline:** Geodesy and navigation provide the ITRF and geodetic datums that anchor the Map Lock to physical measurements. Cartographic conventions and administrative geography then build coordination layers on this foundation.

***

### 7. Symmetry and Asymmetry

#### 7.1 Structural symmetries

| Aspect              | Time sibling                | Space sibling    | Symmetry                                           |
| ------------------- | --------------------------- | ---------------- | -------------------------------------------------- |
| Logical layer       | T1a (Lamport/vector clocks) | S1a (grids/SAVs) | ✔ both provide relational structure without metric |
| Physical layer      | T1b (clocks)                | S1b (rulers)     | ✔ both read metric via apparatus                   |
| Coordination lock   | T2 (Calendar)               | S2 (Map)         | ✔ both use identical lock structure                |
| Comparison envelope | inherited                   | inherited        | ✔ both bounded by parent envelope                  |

#### 7.2 Necessary asymmetries

| Aspect                | Time sibling                                      | Space sibling                                            | Asymmetry                                                    |
| --------------------- | ------------------------------------------------- | -------------------------------------------------------- | ------------------------------------------------------------ |
| **Dimensionality**    | 1 dimension                                       | 3 dimensions                                             | Space admits direction; time does not branch                 |
| **Proper quantity**   | Proper time τ (path integral along worldline)     | Proper length (rest-frame, slice-specified)              | τ accumulates along path; length requires simultaneity slice |
| **Causal role**       | Time orders cause and effect                      | Space separates simultaneous events                      | Causal precedence is temporal, not spatial                   |
| **Reversibility**     | Thermodynamic arrow (out of scope)                | Spatial isotropy (no preferred direction)                | Time has an arrow; space (locally) does not                  |
| **Apparatus**         | Oscillators accumulate phase                      | Interferometers compare paths                            | Fundamentally different measurement operations               |
| **Logical structure** | Causal history (vector clocks) — provably minimal | Topological signature (SAVs) — varies in formal strength | Both metric-free; differ in guarantee level                  |

#### 7.3 Asymmetry implications

The asymmetries are **not defects** in the architecture; they reflect genuine physical differences between temporal and spatial aspects of spacetime:

1. **Clocks integrate; rulers compare.** A clock accumulates proper time along its worldline. A ruler compares two endpoints at (approximately) the same coordinate time. These operations are not interchangeable.
2. **Causal order is temporal.** The statement "A caused B" implies A is in B's past light cone—a temporal relation. Spatial separation alone cannot establish causation.
3. **Dimensionality affects coordination.** Calendar Lock manages one-dimensional enumeration (past → future). Map Lock manages three-dimensional hierarchy (nested regions). The lock structure is identical; the dimensionality of the partitioned space differs.
4. **Logical structures serve different purposes with different guarantees.** Vector clocks answer "what happened before what?" with provable minimality. SAVs answer "what is adjacent to what?" with varying formal strength depending on implementation. Both are metric-free but address distinct organisational needs with distinct rigour profiles.
5. **Proper quantities differ in character.** Proper time τ is a path integral—it accumulates along a worldline and is observer-independent once the path is specified. Proper length requires specifying a simultaneity slice (which events count as "simultaneous" endpoints); in curved spacetime or under relativistic motion, this slice choice is part of the measurement protocol. This asymmetry is fundamental, not merely procedural.

**Cross-disciplinary implication:** These asymmetries persist in structural analogues. Causal ordering is always temporal in character; spatial adjacency cannot substitute for temporal priority. Domain frameworks that conflate the two lose the structure this scaffold provides.

***

### 8. Degradation Pathways

Both siblings degrade toward the parent scaffold, not away from it:

```
        TIME SIBLING                         SPACE SIBLING
        
        T2 (Calendar)                        S2 (Maps)
             │                                    │
             ▼                                    ▼
        T1b (Clocks)                         S1b (Rulers)
             │                                    │
             ▼                                    ▼
        T1a (Lamport/vector)                 S1a (Grids/SAVs)
             │                                    │
             └──────────────┬─────────────────────┘
                            ▼
                    PARENT SCAFFOLD
              (metric + causality + envelope)
```

**Degradation rule:** Loss of a higher tier does not invalidate lower tiers or the parent. An agent who loses calendar conventions retains clock readings; losing clock access retains logical ordering; losing all temporal coordination retains local causal structure.

The same applies spatially: losing maps retains measurement; losing measurement retains SAVs and logical labels; losing all spatial coordination retains local causal structure.

**Terminal state:** An agent reduced to parent-only access can still distinguish causal past from causal future and recognise local metric neighbourhoods. This is the irreducible minimum.

**Structural template for epistemic reliability:** The degradation pathway models fallback under uncertainty:

* When calendar dating is disputed, fall back to relative chronology (T1a)
* When timestamps are contested, fall back to causal sequence (vector clocks detect what is concurrent vs ordered)
* When synchronised systems fail, fall back to Lamport ordering
* When maps are unavailable, fall back to physical measurement or SAV-based topology
* When metric distance is unknown, fall back to adjacency vectors for connectivity

***

### 9. Architectural Control Parameter

The parameter:

> η(τ) = L\_comparison / cτ

measures the fraction of the causal envelope utilised during **any comparison process**. It applies equally to temporal comparisons (clock-to-clock) and spatial comparisons (baseline-to-baseline), since both are bounded by the same parent envelope.

* η near 1: comparison approaches the causal limit (maximum reach, highest noise susceptibility)
* η near 0: comparison well within causal access (shorter reach, lower noise susceptibility)

**Dual status of η:**

* **As derived observable:** Given a comparison protocol, η can be measured empirically. It characterises where within the comparison envelope a given protocol operates.
* **As design coordinate:** Protocols can be designed to target specific η values, trading reach against noise susceptibility.

The **comparison envelope** (`L_comparison ≤ cτ`) is the falsifiable constraint. η is not itself a candidate boundary but a parameter that describes protocol behaviour within that boundary. The scaffold takes no position on whether any particular η value is "optimal"—this depends on apparatus, noise environment, and application requirements.

**Domain of validity:** η's optimal value depends on the dominant noise sources (oscillator instability, channel noise, latency jitter) and on whether the protocol is communication-limited or oscillator-limited. Different apparatus classes and comparison strategies will have different η\_opt values.

**Deferred to handbooks:** Optimisation of η for specific apparatus (optical clocks, VLBI, interferometers) and determination of η\_opt under various noise models belongs in comparison-protocol handbooks, not in this structural scaffold.

***

### 10. Cross-Disciplinary Structural Templates

This section distinguishes between **foundational disciplines** that define or stress-test scaffold tiers and **applied disciplines** that inherit the structure without modifying it. This prevents the scaffold from becoming a "theory of everything" while preserving its utility as a "theory of measurement and comparison."

#### 10.1 Foundational disciplines (explicit anchors)

Foundational disciplines are **custodians of registry constraints** for one or more scaffold tiers. They maintain the standards, proofs, and reference-frame realisations that the scaffold cites. If the scaffold's constraints were violated, these disciplines would lose their primary methodology.

| Discipline                                 | Tier anchored   | Registry custodianship                                                                         |
| ------------------------------------------ | --------------- | ---------------------------------------------------------------------------------------------- |
| **Distributed systems / Computer science** | T1a, S1a        | Custodian of Lamport clock proofs, vector clock correctness, graph-embedding guarantees        |
| **Metrology / Relativistic physics**       | T1b, S1b        | Custodian of SI second, SI metre, and operational definitions anchoring measurement to g\_{μν} |
| **Geodesy / Navigation**                   | S1b, S2         | Custodian of ITRF realisations, VLBI/SLR infrastructure, geodetic datums                       |
| **Quantum information theory**             | Parent scaffold | Custodian of no-signalling theorem; clarifies entanglement/envelope interaction                |
| **Timekeeping authorities (IERS, BIPM)**   | T2              | Custodian of Calendar Lock reference points (epochs, leap seconds) and update rules            |

These disciplines are **first responders**: changes to their standards propagate through the scaffold via the external constraints registry (§12). A redefinition of the SI second would update Tier T1b; a new ITRF realisation would update Tier S2.

#### 10.2 Applied disciplines (downstream consumers)

Applied disciplines **inherit** the scaffold's structure without modifying it. They stress-test consistency within their evidentiary regimes but do not revise the registry. Their domain authority does not extend to redefining scaffold tiers.

<table><thead><tr><th width="192.90234375">Discipline</th><th width="367.3125">Scaffold usage</th><th>Tiers consumed</th></tr></thead><tbody><tr><td><strong>History / Archaeology</strong></td><td>Use Calendar Lock and causal structure to organise timelines. Consumers of "when" but do not define the second.</td><td>T1a (sequence), T2 (periodisation)</td></tr><tr><td><strong>Archival sciences / Provenance</strong></td><td>Use causal chain of custody for documentary evidence. Apply T1a ordering to records.</td><td>T1a, T2, S1a, S2</td></tr><tr><td><strong>Law / Jurisprudence</strong></td><td>Use Map Lock and Calendar Lock for jurisdiction and evidence. Consume "where/when" for social order but do not define the metre.</td><td>T2, S2</td></tr><tr><td><strong>Neuroscience</strong></td><td>Use causal partitioning to map neural information flow. Operate within the parent scaffold's causal structure.</td><td>Parent (causality), T1a (spike ordering)</td></tr><tr><td><strong>Sociology / Politics</strong></td><td>Use coordination locks for administrative partitioning. Tier 2 consumers of the architecture.</td><td>T2, S2</td></tr><tr><td><strong>Economics</strong></td><td>Use Calendar Lock for fiscal periods and Map Lock for market boundaries.</td><td>T2, S2</td></tr></tbody></table>

**Applied disciplines retain full domain authority** over their evidence standards, interpretive frameworks, and explanatory models. The scaffold offers structure, not jurisdiction. A historian judges what counts as adequate dating evidence; a lawyer determines legal standards of proof; a neuroscientist decides what constitutes neural causation.

#### 10.3 The shared problem

Every discipline that reasons about events faces three questions:

1. **When** did it happen? (temporal location)
2. **Where** did it happen? (spatial location)
3. **How do we compare** observations made at different times and places? (comparison procedure)

Foundational disciplines provide the most rigorous answers at their respective tiers. Applied disciplines inherit these answers and adapt them to domain-specific evidence bases.

#### 10.4 What the scaffold provides as template

**Tier separation:** Distinguish logical ordering/labelling (Tier 1a) from physical measurement (Tier 1b) from coordination conventions (Tier 2). This prevents conflation of what is observed with how it is named.

**Lock patterns:** The five-stage lock (Partition → Hierarchy → Reference → Enumeration → Updates) applies wherever raw observations are converted into named, sharable categories.

**Degradation logic:** When higher-tier conventions fail or are disputed, fall back to lower tiers. This models epistemic reliability under uncertainty.

**Inheritance:** Domain frameworks can be checked for consistency with more fundamental layers. A legal timeline that violates causal ordering is internally incoherent; a historical chronology that ignores physical dating constraints is epistemically weaker.

#### 10.5 Caution on cross-disciplinary mapping

Domain-specific applications are **structural analogues**, not identity claims. The scaffold provides:

* a template for tier separation
* a model for inheritance and fallback
* a pattern for coordination locks

It does **not** claim that historical chronology _is_ relativistic proper time, that legal jurisdiction _is_ spacetime localisation, or that neural spike ordering _is_ Lamport timestamping. The mapping is structural: the same organisational pattern applied to different evidence bases with different authority structures.

**Domain authority remains with domain experts.** Foundational disciplines are custodians of registry constraints; applied disciplines stress-test consistency within their domains. Neither subsumes the other.

***

### 11. Open Frontiers

#### 11.1 Physics frontiers

| Frontier                                     | Scaffold relation                                                                              |
| -------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| Quantum field theory + gravity               | Parent scaffold specifies classical limit; emergent proposals must recover metric + causality  |
| Discrete spacetime (causal sets, spin foams) | Comparison envelope may require reformulation if continuum assumption fails                    |
| Quantum reference frames                     | Sibling projections may require superposition of frames; parent scaffold remains backdrop      |
| Relativistic quantum information             | Comparison envelope interpretation must accommodate entanglement-assisted protocols (see §2.4) |

#### 11.2 Cross-disciplinary frontiers

| Frontier                    | Scaffold relation                                                                             |
| --------------------------- | --------------------------------------------------------------------------------------------- |
| AI temporal reasoning       | Extend Lamport/vector clock ordering to continuous time; integrate with physical clock access |
| Distributed spatial systems | Extend SAV frameworks to dynamic topologies; integrate with physical distance calibration     |
| Neural causality            | Map spike-timing windows onto comparison envelope analogues                                   |
| Computational history       | Formalise chronological reasoning using tier structure                                        |
| Legal AI                    | Automate jurisdiction determination using Map Lock / Calendar Lock patterns                   |
| Multi-agent coordination    | Generalise comparison envelope to distributed consensus bounds                                |

***

### 12. External Constraints Registry

| Domain              | Constraint                           | Citation                      |
| ------------------- | ------------------------------------ | ----------------------------- |
| Relativity          | Special relativity, causal structure | Einstein 1905; Minkowski 1908 |
| Relativity          | General relativity, metric dynamics  | Einstein 1915; standard texts |
| Time metrology      | SI second                            | BIPM SI Brochure              |
| Time metrology      | TAI/UTC, leap seconds                | IERS Conventions              |
| Time metrology      | Pulsar timing                        | IPTA data releases            |
| Space metrology     | SI metre                             | BIPM SI Brochure              |
| Space metrology     | ITRF realisations                    | IERS Conventions              |
| Space metrology     | VLBI, SLR techniques                 | IERS Technical Notes          |
| Geodesy             | Reference ellipsoids, datums         | IAG resolutions               |
| Distributed systems | Lamport clocks                       | Lamport 1978                  |
| Distributed systems | Vector clocks                        | Fidge 1988; Mattern 1989      |
| Distributed systems | Vivaldi coordinates                  | Dabek et al. 2004             |
| Graph theory        | Graph embeddings, landmark routing   | Standard texts                |
| Quantum information | No-signalling theorem                | Standard QIT texts            |

All entries are **citation-only**: this scaffold presupposes them but does not govern, re-derive, or modify them.

***

### 13. Open Items

| Item                                        | Target                                                    | Status                    | Priority     |
| ------------------------------------------- | --------------------------------------------------------- | ------------------------- | ------------ |
| **Registry naming convention**              | Council ratification                                      | **BLOCKING**              | **Critical** |
| Tier T1a coastline (Lamport/vector clocks)  | `tier-t1a-logical-clocks.md`                              | Drafted                   | —            |
| **Tier S1a coastline (logical grids/SAVs)** | `tier-s1a-logical-grids.md`                               | **Not drafted**           | **High**     |
| Tier T1b coastline (physical clocks)        | `tier-t1b-physical-clocks.md`                             | Not drafted               | Medium       |
| Tier T2 coastline (Calendar)                | `tier-t2-calendar.md`                                     | Drafted                   | —            |
| Tier S1b coastline (physical rulers)        | `tier-s1b-physical-rulers.md`                             | Not drafted               | Medium       |
| Tier S2 coastline (Maps)                    | `tier-s2-maps.md`                                         | Not drafted               | Medium       |
| Comparison-envelope falsifiability          | Research note                                             | Deferred                  | Low          |
| Syndrome set: "meaningful comparison"       | Handbook (incl. quantum-assisted protocols)               | Deferred                  | Medium       |
| SAV syndrome set                            | Handbook (minimum graph data for topological position)    | Deferred                  | Medium       |
| SAV formal classification                   | Coastline specification (exact/approximate/heuristic)     | Deferred to S1a coastline | High         |
| η optimisation protocols                    | Handbook                                                  | Deferred                  | Low          |
| Applied-discipline handbooks                | Domain-specific applications (history, law, neuro)        | Not drafted               | Low          |
| Foundational-discipline liaison             | Coordinate with IERS, BIPM, distributed systems community | Ongoing                   | Medium       |

**Registry naming convention — Council decision required:**

The navigation footer implements `parent-scaffold-causal-structure.md` (parent-first naming), while legacy documents use `tier-0-causal-structure.md` (tier-only naming). Council must ratify one convention before coastline drafting proceeds:

<table><thead><tr><th width="155.9921875">Option</th><th>Pattern</th><th>Implication</th></tr></thead><tbody><tr><td>A (parent-first)</td><td><code>parent-scaffold-...</code>, <code>tier-t1a-...</code>, <code>tier-s1a-...</code></td><td>Reflects parent-first architecture; legacy Tier 0 superseded</td></tr><tr><td>B (tier-only)</td><td><code>tier-0-...</code>, <code>tier-t1a-...</code>, <code>tier-s1a-...</code></td><td>Maintains backward compatibility; parent = Tier 0</td></tr><tr><td>C (hybrid)</td><td><code>spacetime-parent-scaffold.md</code> + <code>tier-...</code></td><td>Compromise naming</td></tr></tbody></table>

**Guardian recommendation:** Option A with alias stub. Ratify parent-first naming; retain `tier-0-causal-structure.md` as a thin redirect/alias stub that forwards to `parent-scaffold-causal-structure.md`. This preserves backward compatibility without compromising parent-first semantics.

**Note on document types:** Overviews and summaries are **handbooks** (navigation documents). Coastlines are **boundary-defining documents** with falsifiability targets. The two are complementary but not interchangeable.

**Note on tier naming:** This document uses T1a/T1b/T2 for temporal tiers and S1a/S1b/S2 for spatial tiers. All coastline filenames should follow this convention.

***

### 14. Risk Register

<table><thead><tr><th width="210.140625">Risk</th><th width="436.7421875">Mitigation</th><th>Status</th></tr></thead><tbody><tr><td>Cross-disciplinary layer misread as physics claim</td><td>§10.5 caution; endorsement marker distinguishes interpretive mappings; foundational/applied split clarifies authority</td><td>Mitigated</td></tr><tr><td>Foundational disciplines not consulted</td><td>§13 includes liaison item; external constraints registry cites authoritative sources</td><td>Ongoing</td></tr><tr><td>Applied disciplines feel subsumed</td><td>§10.2 explicitly preserves domain authority; scaffold offers structure, not jurisdiction</td><td>Mitigated</td></tr><tr><td>"Foundational" criterion read as gatekeeping</td><td>§10.1 reframed as registry custodianship; operationally checkable</td><td>Mitigated</td></tr><tr><td>Comparison envelope falsifiability underspecified</td><td>§2.4 operational anchor defines comparison event; delayed-comparison clause added; syndrome set deferred to handbook</td><td>Mitigated</td></tr><tr><td>"True by definition" attack on envelope</td><td>§2.4 delayed-comparison clause shows envelope binds whenever comparison occurs</td><td>Mitigated</td></tr><tr><td>Co-located comparison misreading</td><td>§2.4 parenthetical clarifies "classical communication" includes local wiring</td><td>Mitigated</td></tr><tr><td>Proper length definition contested in curved spacetime</td><td>§6.2 notes slice-dependence; §7.2 updated; details deferred to coastline</td><td>Mitigated</td></tr><tr><td>η parameter appears tautological</td><td>§9 clarifies dual status (observable + design coordinate) and cost-function dependence</td><td>Mitigated</td></tr><tr><td>Registry evolution creates version confusion</td><td>§13 flags Council decision as BLOCKING; recommends Option A + alias stub</td><td><strong>Active</strong></td></tr><tr><td>S1a lacks formal depth relative to T1a</td><td>SAV framework explicit in §6.1 with formal-guarantee classification; detailed specification deferred to coastline</td><td>Mitigated</td></tr><tr><td>SAV "complete topological position" overstates rigour</td><td>§6.1 reframed as "topological signature relative to chosen reference structure"</td><td>Mitigated</td></tr><tr><td>Vivaldi coordinates boundary ambiguity</td><td>§6.1 explicitly marks Vivaldi as hybrid proxy at S1a/S1b boundary</td><td>Mitigated</td></tr><tr><td>S1a→S1b transition criterion unclear</td><td>§6.1 calibration criterion added: SI traceability + stated uncertainty</td><td>Mitigated</td></tr><tr><td>"Ruler" terminology collision</td><td>"Ruler" reserved for S1b (physical measurement); SAV terminology adopted for S1a</td><td>Monitored</td></tr><tr><td>Council/Guardian idioms unfamiliar to external readers</td><td>§1 note added mapping idioms to standard roles</td><td>Mitigated</td></tr></tbody></table>

***

### 15. Council Sufficiency

<table><thead><tr><th width="453.46484375">Criterion</th><th>Status</th></tr></thead><tbody><tr><td>Parent scaffold established before siblings</td><td>✔</td></tr><tr><td>Both siblings introduced together</td><td>✔</td></tr><tr><td>Tier boundaries explicit for both siblings</td><td>✔</td></tr><tr><td>Symmetries enumerated</td><td>✔</td></tr><tr><td>Asymmetries enumerated and justified</td><td>✔</td></tr><tr><td>Comparison envelope at parent level</td><td>✔</td></tr><tr><td>Comparison event operationally defined</td><td>✔</td></tr><tr><td>Co-located comparison clarified</td><td>✔</td></tr><tr><td>Delayed-comparison clause included</td><td>✔</td></tr><tr><td>η parameter dual status clarified</td><td>✔</td></tr><tr><td>Quantum-assisted protocols clarified</td><td>✔</td></tr><tr><td>Proper length slice-dependence explicit</td><td>✔</td></tr><tr><td>Vector clocks explicitly included (T1a)</td><td>✔</td></tr><tr><td>Spatial adjacency vectors explicitly included (S1a)</td><td>✔</td></tr><tr><td>SAV "topological signature" phrasing (no overclaim)</td><td>✔</td></tr><tr><td>SAV formal-guarantee classification introduced</td><td>✔</td></tr><tr><td>S1a→S1b calibration criterion explicit</td><td>✔</td></tr><tr><td>T1a/S1a structural parallel established</td><td>✔</td></tr><tr><td>T1a/S1a formal-rigour asymmetry acknowledged</td><td>✔</td></tr><tr><td>Foundational disciplines as registry custodians</td><td>✔</td></tr><tr><td>Applied disciplines' domain authority preserved</td><td>✔</td></tr><tr><td>External constraints citation-only</td><td>✔</td></tr><tr><td>Degradation pathways parent-consistent</td><td>✔</td></tr><tr><td>Cross-disciplinary caution prominent</td><td>✔</td></tr><tr><td>Risk register included and updated</td><td>✔</td></tr><tr><td>No metaphysical overreach</td><td>✔</td></tr><tr><td>Tier naming standardised</td><td>✔</td></tr><tr><td>Registry naming flagged for Council ratification</td><td>✔</td></tr><tr><td>Option A + alias stub recommended</td><td>✔</td></tr><tr><td>Council/Guardian idioms glossed for external readers</td><td>✔</td></tr></tbody></table>

***

### 16. How to Use This Document

#### For foundational-discipline specialists

Your discipline is a custodian of registry constraints for one or more scaffold tiers. Sections 5–6 specify the tier structure; §10.1 identifies your custodianship role. Changes to your standards (e.g., SI redefinition, new ITRF realisation, updated vector-clock proofs) propagate through the scaffold via the external constraints registry (§12).

#### For physicists and metrologists

Begin with Sections 2–7. The comparison envelope (§2.4) and architectural control parameter (§9) are the novel contributions requiring scrutiny. Tier T1b and S1b coastlines will specify apparatus-level detail.

#### For quantum gravity researchers

Section 2.2 (metric structure) and Section 11.1 (physics frontiers) frame the scaffold as a classical benchmark. The scaffold does not prejudge emergence vs. fundamentality; it specifies what must be recovered at scales where classical structure is observed.

#### For distributed systems researchers

Sections 5.1 (Lamport and vector clocks), 6.1 (SAVs and logical grids), and 10.1 (foundational disciplines) show how your work anchors Tier 1a for both siblings. The scaffold formalises the relationship between logical ordering/topology and physical measurement. Note the formal-guarantee classification in §6.1—your input on SAV rigour requirements is welcome.

#### For applied-discipline researchers

Section 10.2 is your entry point. Identify which tiers your discipline consumes. The tier structure (logical → physical → conventional) and lock patterns (Calendar, Map) offer organisational templates. Section 8 (degradation) models epistemic reliability under uncertainty. Your domain authority is preserved; the scaffold offers structure, not jurisdiction.

#### For historians, archivists, and legal scholars

You are applied-discipline consumers (§10.2). The Calendar Lock and Map Lock patterns (§5.3, §6.3) provide templates for organising temporal and spatial evidence. Section 8 (degradation) models what to do when dating or localisation is contested.

#### For everyone

The scaffold answers: "What is the most rigorous available framework for locating events in time and space, and for comparing observations across separation?" Foundational disciplines are custodians of the registry; applied disciplines stress-test consistency within their domains. Whatever your domain, if you reason about when, where, and how to compare, this scaffold provides structural templates. Adapt them to your evidence base and standards of proof.

***

_Spacetime Architecture — Unified Scaffold | Open-Science Harbour_
