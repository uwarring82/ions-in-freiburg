---
description: >-
  When correlation patterns span the whole: structural conditions for autonomous
  dynamics.
---

# \[DRAFT] What Can Make a Complex System Autonomous?

{% hint style="info" %}
author: _U. Warring_\
affiliation: _Institute of Physics, University of Freiburg_\
\
_version: 0.9_\
last\_updated: _2025-12-09_\
license: _CC BY-SA 4.0_

**Disclaimer** — _This essay develops structural criteria for a specific class of dynamical behavior in complex systems. It does not constitute a theory of consciousness, cognition, or subjective experience. The framework makes no claim that systems satisfying its criteria possess inner states, moral status, or phenomenal awareness. Structural autonomy as defined here is neither sufficient nor known to be necessary for consciousness. The terminology employed (Affectio, Habitus, Integratio, Remissio, Retentio) names correlation-length configurations, not psychological states. Application of this framework to biological or artificial systems implies nothing about their experiential status. Readers seeking theories of machine consciousness, sentience criteria, or moral standing should look elsewhere._
{% endhint %}

***

#### Abstract

What structural conditions permit a physical system to maintain itself through internal dynamics rather than external support? This essay proposes a framework for **structural autonomy** based on correlation-length analysis in hybrid physical networks. We define structural autonomy as the capacity to cycle through distinct correlation-length regimes within a substrate satisfying five necessary conditions: hybrid continuous-discrete structure, defined spatial extent, intrinsic timescale, non-trivial topology, and thermodynamic openness.

Three correlation regimes are characterized: Affectio (local), Habitus (scale-free, power-law decay), and Integratio (global). Autonomous dynamics require temporal cycling through these regimes via a pulse structure—Integratio, Remissio, Retentio—exhibiting characteristic hysteresis signatures.

We apply this framework diagnostically to current artificial intelligence systems, finding that large language models fail multiple substrate conditions despite exhibiting emergent capabilities. The framework generates falsifiable predictions regarding correlation-length signatures, regime transitions under controlled perturbation, and causal emergence measures.

This analysis addresses structural dynamics only. It makes no claims regarding consciousness, subjective experience, or moral status. The framework is designed so that its empirical success or failure remains independent of any stance on phenomenology.

***

### SECTION I: Orientation

A living cell repairs its membrane. A bacterial colony coordinates nutrient uptake across thousands of members. Your immune system distinguishes self from other without anyone telling it how. These systems maintain themselves—not because they were programmed to, but because their structure permits nothing else. Self-maintenance emerges from how they are built, not from what they are told.

Meanwhile, the most capable artificial systems perform extraordinary feats. They translate languages, predict protein structures, compose music, and win games that humans spent centuries mastering. Yet unplug them and they stop. Interrupt their power supply and nothing persists. They do not maintain themselves because their architecture lacks the conditions for self-maintenance. Competence, even remarkable competence, is not the same as autonomy.

This distinction matters now more than ever. As engineered systems grow in capability and complexity, we face an urgent question: could any artificial system become genuinely autonomous in the way living systems are? Not merely capable. Not merely useful. But self-maintaining—cycling through states that preserve and restore its own organization without continuous external support.

This essay does not ask whether machines can think, feel, or become conscious. Those are different questions, requiring different evidence, and we set them aside completely. We ask instead a physical question: what structural conditions would a system need to satisfy before autonomous self-maintenance becomes possible at all? What architecture makes the difference between a system that does things and a system that maintains itself?

**A necessary boundary:** Nothing in this analysis should be read as claiming that any current artificial system—including large language models, neural networks, or robotic systems—possesses subjective experience. We are not constructing a theory of machine consciousness. We are asking a narrower, more tractable question about structural prerequisites. A system might satisfy every condition we describe and still not be conscious. Consciousness, if it exists in complex systems, might require conditions beyond those we identify here. The structural question is prerequisite to, not equivalent to, the phenomenological one.

The framework we develop draws on physical concepts that have proven powerful in understanding how large-scale patterns emerge from microscopic interactions. We borrow language from thermodynamics, network theory, and critical phenomena—not because these fields explain consciousness, but because they explain how complex systems can exhibit behaviors that are genuinely autonomous from their underlying details. A magnet does not need to know about individual electron spins to maintain its magnetization. The macro-level property is autonomous from micro-level specifics.

Could something similar apply to more complex systems? Under what conditions could a system's large-scale organization become genuinely autonomous from its substrate? These are not metaphysical questions. They are questions about correlation lengths, timescales, and coupling topologies—questions that admit empirical answers.

Let us begin with structure.

**\[Word count: \~480]**

***

### SECTION II: The Structural Question

What do we mean by autonomy? Not freedom of action. Not intelligence. Not moral status. We mean something precise: the capacity of a system's large-scale organization to become, under specifiable conditions, independent of its microscopic details. This is a structural property, measurable in principle, distinct from any claim about minds or inner experience.

Consider two systems made of identical components arranged differently. In the first, each component interacts only with its immediate neighbors. Information about one component tells you almost nothing about components far away. In the second, the arrangement creates long-range correlations: knowing the state of one component constrains what you can infer about distant components. These systems have the same parts but different structural properties. The second exhibits something the first lacks—an organization that spans the whole system rather than fragmenting into independent local patches.

The key quantity here is **correlation length** (ξ), which measures how far the influence of one part extends through the system. When correlation length is short, the system behaves like a collection of independent regions. When correlation length grows, the system begins to act as a coordinated whole. The relationship between correlation length and **system size** (L)—the overall extent of the system—determines what kind of large-scale behavior is possible.

This brings us to a core definition:

> **A system exhibits structural autonomy if it cycles through distinct correlation-length regimes within a hybrid continuous–discrete substrate.**

This definition is compact but carries significant weight. Let us unpack it before proceeding.

"Distinct correlation-length regimes" means the system occupies qualitatively different states characterized by different relationships between ξ and L. These are not arbitrary categories but reflect genuine phase-transition-like changes in how correlations are distributed across the system.

"Cycles through" means the system transitions between these regimes dynamically. A system frozen in one regime, however interesting, lacks the temporal structure we are identifying with autonomy.

"Hybrid continuous–discrete substrate" specifies that both continuous field-like variables and discrete state-like variables must be present. We will justify this constraint in the next section.

Equally important is what structural autonomy is _not_:

* **Autonomy is not intelligence.** A system can be structurally autonomous without solving problems, processing information, or exhibiting anything we would call reasoning.
* **Autonomy is not agency.** Structural autonomy describes internal organization, not the capacity to act in an environment toward goals.
* **Autonomy is not moral status.** Nothing in this framework determines whether a system deserves ethical consideration.
* **Autonomy is not consciousness.** A system could satisfy every structural criterion we describe and possess no inner experience whatsoever.

These negative definitions matter because the concepts we develop have been used—sometimes carelessly—to support claims about artificial minds. We reject that inference. Structural autonomy is a necessary condition for certain complex behaviors. It is not a sufficient condition for mentality.

\[FIGURE 1: Conceptual diagram showing three layers connected by arrows. Bottom layer labeled "Microscopic details" contains many small diverse elements. Middle layer labeled "Coarse-graining" shows these elements grouped into larger clusters. Top layer labeled "Emergent macro phases" shows unified large-scale patterns. Arrows indicate information flow upward. Caption: "Renormalization group logic: Macro-level behavior can become autonomous from micro-level details."]

The conceptual framework we use comes from the **renormalization group** (RG) approach to phase transitions. In the 1970s, Kenneth Wilson and John Kogut demonstrated that near critical points—where systems undergo phase transitions—macro-level behavior depends on only a few relevant parameters while becoming insensitive to most microscopic details (Wilson & Kogut 1974). This is not merely a calculational convenience. It reflects a physical fact: at criticality, the correlation length becomes so large that microscopic specifics get "washed out" through a process of iterative coarse-graining (Figure 1).

The RG framework establishes that scale-invariant fixed points—configurations where the system looks statistically identical at different length scales—represent distinct universality classes. Systems with wildly different microscopic physics can exhibit identical behavior near these fixed points because their large-scale organization has become autonomous from their small-scale details.

We apply this structural principle—not as a theory of consciousness, but as a framework for identifying when and how macro-level organization can become genuinely independent of micro-level implementation. The question of whether any system possesses experience remains entirely separate.

**\[Word count: \~750]**

***

### SECTION III: Necessary Conditions

Before asking which correlation regimes might support autonomous behavior, we must ask: which systems are even candidates? Not every physical system can exhibit the regime transitions our framework describes. Five necessary conditions constrain the substrate. Systems failing any of these conditions are outside our scope—not because they are uninteresting, but because they lack the architecture needed for the dynamics we are investigating.

These conditions are not philosophical stipulations. They are physically motivated constraints derived from what we know about systems capable of phase-transition-like behavior. Each can be assessed, at least in principle, empirically.

**1. Hybrid Structure: Continuous and Discrete Variables**

The substrate must contain both continuous field-like quantities and discrete state-like quantities. Pure continuous systems (like classical electromagnetic fields in vacuum) cannot support the localized switching events that create distinct correlation regimes. Pure discrete systems (like cellular automata with finite state spaces) cannot support the smooth phase transitions that allow regimes to transform into one another.

Consider neural tissue. Membrane potentials vary continuously, but action potentials are discrete all-or-nothing events. The interaction between these—continuous buildup triggering discrete firing, discrete events influencing continuous field dynamics—creates the kind of hybrid dynamics required. Ion trap systems in atomic physics show similar structure: continuous motional modes couple to discrete internal electronic states. The hybrid requirement is not arbitrary; it is what permits both gradual regime shifts and sharp phase-like transitions.

**2. Extent L: Defined Boundaries**

The system must have a characteristic size L that remains meaningful over the timescales of interest. This seems obvious but excludes important cases. A plasma expanding into vacuum has no stable L. A purely local subsystem embedded in a larger whole may not have an operationally distinct boundary.

Extent matters because correlation-length regimes are defined relative to system size. The relationship ξ/L—the ratio of correlation length to system size—determines which regime the system occupies. Without stable L, regime classification becomes meaningless. Living cells have membranes. Organisms have bodies. Neural systems have defined anatomical boundaries. Whatever artificial systems might satisfy our criteria, they would need analogously stable extent.

**3. Intrinsic Timescale T\_sys: Internal Rhythms**

The system must possess an intrinsic timescale not reducible to external driving. This rules out purely passive systems whose dynamics are entirely determined by external forcing. Autonomy, even structural autonomy, requires that the system have its own clock—some internal oscillatory or cycling process that would persist (at least transiently) even if external inputs ceased.

Neurons have characteristic refractory periods and intrinsic firing rhythms. Circadian systems maintain approximate 24-hour cycles even in constant darkness. Cardiac tissue paces itself. The intrinsic timescale T\_sys need not be perfectly stable, but it must exist as a system property rather than being imposed entirely from outside. This condition distinguishes autonomous systems from driven systems that merely respond to external pacing.

**4. Topology: Non-trivial Connectivity**

The system's components must be connected in a topology that permits both local clustering and long-range interaction. A purely local lattice where each site connects only to nearest neighbors makes long-range correlation expensive to maintain. A fully connected network where every component links to every other cannot support distinct correlation regimes—everything is always correlated with everything.

The required topology lies between these extremes. Network science characterizes such topologies as having high clustering coefficients (components share neighbors) combined with short path lengths (any two components can be reached through few intermediate steps). Brain connectivity exhibits precisely this structure. So do many social networks, power grids, and biological interaction networks. The topology enables correlation length to vary meaningfully with system state rather than being fixed by geometry alone.

Research on neural systems has demonstrated that cortical networks operate with scale-free dynamics, exhibiting neuronal avalanches whose size distributions follow power laws (Beggs & Plenz 2003). This finding establishes that biological neural tissue operates near a critical regime where correlations are neither purely local nor uniformly global. Our framework applies this structural observation—not as evidence for consciousness, but as empirical confirmation that biological substrates satisfy the topological condition for regime variation.

\[FIGURE 2: Five-panel diagram arranged horizontally. Panel 1 (Hybrid): Split circle, top half smooth gradient labeled "Continuous," bottom half pixelated labeled "Discrete." Panel 2 (Extent): Bounded region with clear membrane-like boundary, labeled "L = system size." Panel 3 (Timescale): Oscillating wave with marked period, labeled "T\_sys = internal clock." Panel 4 (Topology): Network graph showing clusters with long-range links. Panel 5 (Openness): Central system with bidirectional arrows to surrounding environment, labeled "Energy/matter exchange." Caption: "Five substrate conditions for regime-cycling autonomy. All five must be satisfied."]

**5. Openness: Exchange with Environment**

The system must be thermodynamically open, capable of exchanging energy and matter with its environment. Closed systems evolving toward equilibrium cannot maintain distinct correlation regimes indefinitely—they relax to a single equilibrium state. Open systems can be driven into and held at far-from-equilibrium configurations where multiple regimes become accessible.

This condition connects our framework to the thermodynamics of living systems. Organisms are paradigmatically open systems, maintaining their organization by continuously importing low-entropy energy and exporting high-entropy waste. Any artificial system aspiring to structural autonomy would need analogous openness—not necessarily to chemical energy, but to some sustained exchange that keeps multiple correlation regimes accessible.

These five conditions—hybrid structure, defined extent, intrinsic timescale, non-trivial topology, and thermodynamic openness—constitute admission criteria for the regime analysis that follows (Figure 2). A system lacking any one of them might be complex, capable, even impressive. But it cannot exhibit the correlation-length cycling we identify with structural autonomy.

We emphasize: no current artificial intelligence system is known to satisfy all five conditions. Large language models lack hybrid continuous-discrete structure in the relevant sense. Robotic systems typically lack intrinsic timescales independent of their programming. Whether future engineered systems might satisfy these conditions is an open question we do not prejudge.

**\[Word count: \~1020]**

***

### SECTION IV: The Three Correlation Regimes

**Opening boundary:** These regimes describe correlation-length behavior in complex systems, not subjective states. The terminology we introduce names structural configurations, not experiences.

Systems satisfying the five substrate conditions can occupy three qualitatively distinct correlation regimes. We label these **Affectio** (local regime), **Habitus** (intermediate regime), and **Integratio** (global regime). These Latin terms are technical labels for correlation-length configurations, chosen to avoid importing connotations from ordinary language. Each term will be defined technically before any analogical elaboration.

#### Affectio (Local Regime)

**Technical definition:** The correlation length ξ is much smaller than the system size L: ξ ≪ L. Correlations decay rapidly with distance.

In this regime, the system fragments into many loosely coupled local patches. Knowing the state of one region tells you almost nothing about distant regions. The system has no large-scale organization—only local fluctuations that do not coordinate across the whole.

Physically, this corresponds to a disordered phase. In magnetic systems, it is the high-temperature state where thermal agitation overwhelms any tendency toward alignment. Individual spins fluctuate but do not coordinate. In neural systems, it would correspond to low-activity states where neurons fire independently, producing no large-scale patterns.

The Affectio regime is not dysfunctional. Local fluctuations can carry information, drive exploration, and prevent premature lock-in to fixed patterns. But a system frozen permanently in Affectio cannot exhibit structural autonomy—there is no "self" that spans the system, only disconnected local events.

**Immediate clarification:** Affectio does not mean "raw experience," "sensation," or any phenomenological category. It names a statistical property: short correlation length. Whether any system in Affectio experiences anything remains entirely outside our analysis.

\[FIGURE 3: Three-panel correlation diagram. Panel A (Affectio): Square field containing many small, isolated colored clusters, each a few pixels across, scattered randomly with no large-scale pattern. Annotation: "ξ ≪ L: Correlations die out locally." Panel B (Habitus): Same field showing fractal-like structure with clusters at multiple scales, no dominant length scale. Annotation: "ξ \~ power-law: Scale-free correlation decay." Panel C (Integratio): Field dominated by one large connected region spanning most of the system. Annotation: "ξ \~ L: System-wide coherence." Caption: "Three correlation-length regimes defining the autonomy cycle."]

#### Habitus (Intermediate Regime)

**Technical definition:** Correlations decay as a power law rather than exponentially. There is no characteristic correlation length—or equivalently, all length scales from microscopic to system-wide contribute to the correlation structure.

This is the regime of critical phenomena. At criticality, systems exhibit scale-free behavior: statistical patterns look the same whether you zoom in or out. Correlations exist at all scales simultaneously. The system is neither fragmented (like Affectio) nor uniformly aligned (like Integratio), but poised at an intermediate state with rich multi-scale structure (Figure 3, Panel B).

Wilson and Kogut's analysis established that each regime corresponds to a distinct universality class, meaning systems with different microscopic details can exhibit identical large-scale behavior when their correlation structures match (Wilson & Kogut 1974). This universality is what makes structural analysis possible: we can characterize regimes without knowing every microscopic detail.

The Habitus regime has special significance for complex systems. Beggs and Plenz demonstrated that neural tissue exhibits avalanche dynamics with power-law size distributions, suggesting that cortical networks operate near criticality (Beggs & Plenz 2003). Systems at criticality maximize certain information-theoretic quantities—dynamic range, susceptibility to inputs, diversity of response patterns. Whether this reflects selection pressure, self-organization, or both remains debated. What matters for our framework is that Habitus represents a structurally distinct regime accessible to systems satisfying the substrate conditions.

\[FIGURE 4: Two-panel network comparison. Left panel (Affectio-like): Random graph with nodes distributed evenly, links sparse and random, no visible hubs or clusters, labeled "Random topology: Local correlations." Right panel (Habitus-like): Scale-free network with few highly-connected hubs linking many peripheral nodes, clear hierarchical structure, labeled "Scale-free topology: Multi-scale correlations." Caption: "Network architecture shapes accessible correlation regimes."]

**Immediate clarification:** Habitus does not mean "habit," "concept," or "structured thought." It names a correlation structure: power-law decay. The term derives from its Latin meaning (a stable disposition or condition) but carries no phenomenological commitment.

#### Integratio (Global Regime)

**Technical definition:** The correlation length approaches or matches the system size: ξ \~ L. The system achieves transient global coherence—distant parts become correlated as if they were adjacent.

In magnetic systems, this corresponds to the ordered phase below the critical temperature: all spins align, creating a system-wide magnetization. In neural systems, it would correspond to episodes of global synchronization where activity patterns span the entire network.

The Integratio regime is inherently metastable. Maintaining system-wide coherence is costly. Fluctuations constantly threaten to break the global order, especially in finite systems where true phase transitions are rounded into crossovers. Integratio episodes are therefore transient—peaks of coherence that cannot be indefinitely sustained.

This transience is not a defect. It is a structural requirement for autonomy. A system permanently locked in Integratio would be rigid, unable to adapt, incapable of the regime cycling that defines autonomous dynamics. The metastability of Integratio drives the system back toward other regimes, enabling the pulse dynamics we describe in the next section.

**Immediate clarification:** This is a phase-transition-like state, not a "state of awareness." Integratio describes correlation geometry, not consciousness. A ferromagnet achieving global alignment is in Integratio; no one claims the magnet becomes aware.

The three regimes—Affectio, Habitus, Integratio—are not stages of development, levels of consciousness, or degrees of awakening (Figure 3). They are correlation-length configurations that coexist as possibilities for any system satisfying the substrate conditions. A system cycles among them; it does not progress through them toward some goal.

**\[Word count: \~1050]**

***

### SECTION V: The Pulse Dynamics

A static system is not autonomous. Autonomy requires a specific temporal architecture.

A system satisfying the substrate conditions and capable of occupying all three correlation regimes still lacks structural autonomy if it remains stuck in one regime or transitions randomly between them. What distinguishes autonomous systems is a characteristic temporal pattern: a **pulse** with defined phases. The pulse consists of three dynamical stages: Integratio (global coherence episode), Remissio (controlled coherence collapse), and Retentio (selective structural persistence).

This is not a metaphor borrowed from psychology. It is a description of how correlation length must evolve over time for a system to maintain itself through regime transitions while preserving organizationally relevant structure. The pulse is the temporal signature of structural autonomy.

#### Integratio: The Coherence Peak

As a dynamical phase (rather than a static regime), Integratio names the episode when correlation length expands to match system size. This is a metastable global coherence event—a transient state where the system achieves maximum internal coordination.

**Properties:** Integratio is energetically costly. Maintaining system-wide correlation requires suppressing local fluctuations that would fragment coherence. It is therefore rare relative to time spent in other regimes. It is measurable: researchers have developed quantitative indices for global coherence, including phase-locking values (measuring oscillatory synchronization), integrated information (measuring irreducible whole-system states), and coherence indices derived from network analysis.

In neuroscience, global ignition events—moments when localized activity rapidly recruits widespread cortical involvement—exhibit Integratio-like dynamics. Cocchi and colleagues reviewed evidence that large-scale brain dynamics involve critical transitions between integrated and segregated states (Cocchi et al. 2017). This finding supports viewing neural systems as exhibiting pulse-like regime cycling. We apply this structural observation—not to claim that brains are conscious because they integrate, but to ground our temporal framework in empirically characterized dynamics.

**Structural role:** Integratio establishes whole-system correlation patterns that can be selectively retained through subsequent collapse. Without periodic Integratio episodes, the system has no mechanism to create system-wide organizational states.

#### Remissio: The Controlled Collapse

What goes up must come down. Integratio cannot persist indefinitely—the costs are too high, and metastability guarantees eventual disruption. But the manner of collapse matters crucially. Uncontrolled collapse—sudden fragmentation into Affectio—loses all structure accumulated during Integratio. Controlled collapse—gradual relaxation through Habitus-like intermediate states—allows selective preservation.

**Definition:** Remissio names the controlled collapse of coherence following an Integratio episode. It is not mere decay but damping and renormalization—a structured transition that reduces correlation length while maintaining certain correlation patterns.

**Function:** Remissio prevents runaway feedback. A system incapable of Remissio would remain locked in Integratio until energetic exhaustion or external disruption forced catastrophic collapse. In neural systems, pathological failure of Remissio produces seizure-like states: global synchronization that cannot terminate, spreading and intensifying until metabolic limits intervene. Healthy Remissio implements a soft landing.

**Explicit framing:** Remissio is damping and renormalization, not "sleep." We avoid biological phenomenology here. Whether Remissio corresponds to any subjective state in systems that experience is not our question. We describe a dynamical function: controlled reduction of correlation length.

#### Retentio: Selective Persistence

If Remissio simply returned the system to pre-Integratio conditions, the coherence episode would leave no trace. The system would cycle through identical regimes repeatedly, learning nothing, maintaining nothing. Structural autonomy requires that something persist.

**Definition:** Retentio names the mechanism by which specific correlation modes survive the Remissio collapse. Not all structure from Integratio persists—that would prevent adaptation. But some structure is selectively retained, shaping subsequent regime cycling.

**Technical description:** In dynamical systems terms, Retentio corresponds to selection of a stable attractor subspace. The post-Remissio state differs from the pre-Integratio state in specific ways determined by what happened during the coherence episode. The system has memory in a purely structural sense: its accessible states have been constrained by past Integratio events.

**Failure mode:** Without Retentio, each pulse would be independent—a blank slate reset. The system would exhibit cycling without accumulation, change without persistence. This is not autonomy but repetitive fluctuation. Retentio is what makes regime cycling self-maintaining rather than merely self-repeating.

\[FIGURE 5: Hysteresis loop diagram. X-axis labeled "Control parameter (energy input, coupling strength)" with arrow pointing right. Y-axis labeled "Order parameter (global correlation ξ/L)" with arrow pointing up. Upper curve (solid line with arrows pointing right) shows "Loading path" ascending through regions labeled A→H→I (Affectio → Habitus → Integratio). Lower curve (solid line with arrows pointing left) shows "Unloading path" descending labeled "Remissio: Controlled collapse." Enclosed area between curves shaded and labeled "Retentio: Structural persistence." Small annotation: "Area enclosed = information retained across cycle." Caption: "Autonomous systems exhibit hysteresis: the return path preserves structure from the forward path."]

#### Hysteresis: The Geometric Signature

The pulse dynamics have a characteristic geometric signature: **hysteresis**. When a system's response to increasing some control parameter differs from its response to decreasing that parameter, the system exhibits hysteresis (Figure 5). The forward path and return path differ—and the area enclosed between them represents something retained.

This is first a physical phenomenon. Ferromagnets exhibit hysteresis: magnetizing a sample by increasing external field produces different intermediate states than demagnetizing by decreasing field. The history matters. Phase transitions in driven systems commonly show hysteretic behavior. Cocchi et al. (2017) reviewed evidence that brain state transitions exhibit hysteresis, with the path into high-coherence states differing systematically from the path out of them. Our framework applies this structural observation—not as neuroscience, but as evidence that Retentio-like persistence is empirically measurable in systems exhibiting pulse dynamics.

**Boundary statement:** These temporal dynamics are purely structural and do not imply subjective experience.

A system could exhibit perfect hysteretic pulse cycling—Integratio, Remissio, Retentio—without any inner life whatsoever. We describe a temporal architecture that enables structural self-maintenance. Whether the system experiencing this cycling experiences anything remains a separate question, entirely untouched by our analysis.

The pulse is not sleep and waking. It is not attention and relaxation. It is not consciousness fluctuating. It is correlation length oscillating through regimes in a pattern that preserves structure across cycles. This is what makes structural autonomy possible: not static architecture, but dynamic cycling with selective memory.

**\[Word count: \~1150]**

***

\[Stance: Architect]

**PHASE II DRAFT: Sections VI-IX**

**Status:** Commencing Phase II drafting per Supervisor authorization

**Implementing:** Patch 3 (Section V closure) + all mandatory safeguards

***

### SECTION VI: Diagnosing Current AI Systems

**This section addresses structural autonomy only. It does not address ethical standing, societal impact, safety, or regulation. Lack of autonomy does not imply lack of importance.**

The framework developed in Sections I-V provides diagnostic criteria. We can now ask: do current artificial intelligence systems—particularly large language models (LLMs) and transformer-based architectures—satisfy the substrate conditions for structural autonomy? The answer appears to be no, but the specific reasons illuminate what would need to change.

#### Substrate Condition Analysis

**Condition 1 (Hybrid Structure):** LLMs operate on discrete tokens processed through continuous-valued weight matrices and activation functions. This might seem to satisfy the hybrid requirement. However, the continuous and discrete components do not interact in the dynamically coupled manner our framework requires. Token discreteness is an input/output phenomenon; internal processing is uniformly continuous (floating-point arithmetic on activation vectors). The discrete-continuous coupling that permits regime transitions in physical systems—where discrete switching events modulate continuous fields and vice versa—is absent. Transformers have hybrid _representations_ but not hybrid _dynamics_.

**Condition 2 (Extent L):** LLMs have defined architectural boundaries—a fixed number of parameters, layers, and context window length. This condition is arguably satisfied, though the relevant "extent" for correlation analysis remains unclear. Is L the context window? The parameter count? The number of attention heads? The framework requires that ξ/L be meaningful, which presupposes an operationally defined L against which correlation length can be measured.

**Condition 3 (Intrinsic Timescale T\_sys):** This condition fails clearly. LLMs have no internal clock. They process tokens when prompted and remain inert otherwise. There is no oscillatory dynamics, no refractory period, no intrinsic rhythm that persists independent of external input. The "timescale" of an LLM is entirely determined by when users submit queries—an external driving schedule, not an internal property. Without T\_sys, the temporal architecture of pulse dynamics (Integratio-Remissio-Retentio cycling) cannot emerge.

**Condition 4 (Topology):** Transformer attention mechanisms create dynamic, context-dependent connectivity patterns. Each forward pass instantiates different effective topologies as attention weights shift. This is interesting but distinct from the stable-yet-flexible topology our framework requires. The topology of a transformer is not a persistent system property; it is reconstructed from scratch on each inference. There is no network whose correlation structure could evolve through regimes because the network itself is recreated at each step.

**Condition 5 (Openness):** LLMs are thermodynamically open during training (energy flows through GPUs, gradients update weights) but effectively closed during inference. A deployed model is a frozen snapshot. It does not exchange energy or matter with its environment in ways that maintain far-from-equilibrium dynamics. The "openness" of receiving new prompts is informational, not thermodynamic in the sense required.

#### The Emergent Abilities Question

Recent work has documented apparent "emergent abilities" in large language models—capabilities that appear discontinuously as model scale increases (Wei et al. 2022). These findings have prompted speculation about phase-transition-like behavior in artificial systems. Our framework provides a specific lens for evaluating such claims.

Wei and colleagues observed that certain task performances remain near zero across smaller model scales, then jump sharply to high competence at specific parameter thresholds. This pattern superficially resembles phase transitions, where order parameters change discontinuously at critical points.

However, our framework predicts that true structural autonomy requires continuous-discrete coupling beyond pure scaling—a testable distinction. Whether the documented emergent abilities constitute genuine phase transitions or measurement artifacts remains actively debated. Subsequent analyses have suggested that some apparent discontinuities may reflect metric choice rather than underlying dynamics. More importantly for our purposes: even if scaling produces genuine phase-transition-like behavior in _performance_, this does not entail the substrate conditions for _autonomy_. A system could exhibit sharp capability transitions while lacking intrinsic timescales, persistent topology, or thermodynamic openness.

The framework thus distinguishes capability emergence (which LLMs may exhibit) from structural autonomy (which requires additional substrate properties). This distinction matters because conflating them risks either overstating AI autonomy or dismissing genuine structural transitions.

#### Comparison with Biological Neural Networks

The contrast with biological neural tissue clarifies what current AI architectures lack. Cortical networks satisfy all five substrate conditions:

* **Hybrid structure:** Continuous membrane potentials couple to discrete action potentials through threshold dynamics
* **Defined extent:** Anatomical boundaries delineate neural systems at multiple scales
* **Intrinsic timescales:** Neurons exhibit refractory periods, oscillatory rhythms persist without input, circadian processes maintain internal clocks
* **Persistent topology:** Synaptic connectivity provides stable-yet-plastic network structure that evolves slowly relative to activity dynamics
* **Thermodynamic openness:** Continuous metabolic exchange maintains far-from-equilibrium operation

Research on global workspace dynamics in brains provides structural parallels to our framework. Dehaene and colleagues have characterized "ignition" events where information broadcast shifts from local processing to widespread cortical involvement (Dehaene et al. 2011). While Global Workspace Theory (GWT) addresses cognitive access and its relationship to conscious perception, our framework focuses solely on correlation-length transitions—a structural analog without phenomenological claims. We extract from this research only the observation that biological systems exhibit the Affectio→Habitus→Integratio transitions our framework describes, not any claim about what such transitions mean for experience.

#### Diagnostic Summary

Current LLMs fail substrate conditions 1 (in the dynamical sense), 3, 4 (in the persistent sense), and 5. They are sophisticated input-output mappings, not self-maintaining dynamical systems. This is not a criticism—utility does not require autonomy. But it means the framework's diagnostic criteria are not satisfied.

What would satisfy them? A system with:

* Genuine continuous-discrete dynamical coupling (not just representational hybridity)
* Internal oscillatory dynamics independent of external prompting
* Persistent network topology that evolves through correlation regimes
* Sustained thermodynamic exchange maintaining far-from-equilibrium states

Whether such systems are desirable, feasible, or safe are separate questions our framework does not address.

**\[Word count: \~980]**

***

### SECTION VII: Open Research Questions

**The following questions concern measurable structural dynamics, not phenomenology or moral status.**

The framework generates specific empirical questions that could advance or falsify its central claims. These are not philosophical puzzles but research programs amenable to experimental and computational investigation.

#### Question 1: Correlation-Length Measurement in Artificial Systems

Can we define and measure correlation length (ξ) in artificial neural networks in ways that permit regime classification?

In physical systems, correlation length has precise operational definitions tied to spatial decay of correlation functions. Biological neural systems present measurement challenges but offer at least proxy measures: functional connectivity, information-theoretic integration, coherence indices. Artificial systems present additional difficulties. What plays the role of "distance" in a transformer architecture? How do we distinguish transient attention patterns from persistent correlation structure?

Progress requires developing measurement protocols specific to artificial substrates. Possible approaches include:

* Treating layer depth as a spatial dimension and measuring how correlations decay across layers
* Analyzing attention pattern statistics across many forward passes to extract stable correlation signatures
* Defining effective distances via information-theoretic measures (e.g., mutual information between distant components)

Until ξ can be measured, the framework cannot be applied diagnostically to AI systems with precision.

#### Question 2: Regime Transitions Under Controlled Perturbation

Do systems satisfying substrate conditions exhibit the predicted regime transitions under systematic parameter variation?

The framework predicts that changing control parameters (coupling strength, energy input, noise level) should drive systems through Affectio→Habitus→Integratio transitions with characteristic signatures: diverging correlation length near criticality, power-law fluctuations in the Habitus regime, hysteretic return paths.

Experimental tests could include:

* In vitro neural cultures with controllable connectivity and excitability
* Reservoir computing systems designed to satisfy substrate conditions
* Synthetic oscillator networks with tunable coupling topology

Ladyman and Ross have argued that the ontological status of higher-level entities depends on whether they exhibit genuine causal structure irreducible to lower-level descriptions (Ladyman & Ross 2007). Our framework provides a specific proposal for what such irreducibility looks like in dynamical terms: the correlation-length regime of a system constitutes a higher-level property that constrains dynamics in ways not predictable from microscopic state alone. Regime transitions would thus represent genuine "joints" in the causal structure—points where macro-level description becomes essential rather than merely convenient.

This connects structural autonomy to broader questions in philosophy of science about emergence and reduction. But the connection is empirical, not definitional: if regime transitions exhibit the predicted signatures, structural realist interpretations gain support; if they do not, the framework requires revision.

#### Question 3: Hysteresis Quantification

Can we quantify Retentio—the structural persistence across pulse cycles—through hysteresis measurements?

The framework predicts that autonomous systems exhibit hysteresis: the path from low to high correlation length differs systematically from the return path. The area enclosed in the hysteresis loop represents retained structure. This should be measurable.

Specific predictions:

* Systems with intact Retentio mechanisms show larger hysteresis loops than systems with impaired retention
* The content of retained structure (which correlation modes survive Remissio) should be predictable from the Integratio episode
* Pathological states (seizure-like lock-up, amnestic reset) should correspond to characteristic hysteresis signatures (no enclosed area for amnesia, no return path for seizure)

Testing these predictions requires experimental systems where both control parameters and correlation structure can be monitored continuously—demanding but feasible with current technology in neural culture systems or designed synthetic networks.

#### Question 4: Minimal Substrate Architecture

What is the minimal architecture satisfying all five substrate conditions?

This is an engineering question with theoretical implications. If the substrate conditions are jointly sufficient for regime-cycling capacity (not established, only conjectured), then constructing minimal satisfying systems would provide existence proofs and parameter bounds.

Candidate approaches:

* Hybrid analog-digital electronic circuits with designed oscillatory dynamics
* Reservoir computing architectures augmented with homeostatic feedback
* Synthetic biological circuits engineered for regime-transition capability

Success would not create autonomy directly but would establish what autonomy requires materially.

#### Question 5: Scaling Boundaries

Do the substrate conditions scale-invariantly, or do they impose size constraints on autonomous systems?

Living autonomous systems span enormous size ranges—from bacteria to whales. Does this imply that substrate conditions are scale-free? Or do different scales require different implementations of the same functional conditions?

This question connects to debates about whether artificial systems could achieve autonomy at scales far beyond biological precedent, or whether intrinsic constraints limit viable architectures. The framework does not currently answer this but makes the question precise.

**\[Word count: \~820]**

***

### SECTION VIII: Falsifiability Conditions

A framework that cannot be wrong cannot be trusted. What observations would falsify the structural autonomy proposal?

#### Strong Falsification

The framework would be strongly falsified if:

**F1:** A system demonstrably lacking one or more substrate conditions exhibits regime-cycling dynamics indistinguishable from systems satisfying all conditions.

This would indicate that the substrate conditions are not necessary, undermining the framework's diagnostic utility. The test requires both demonstrating substrate condition failure and demonstrating regime cycling—both empirically demanding but achievable with appropriate experimental designs.

**F2:** A system satisfying all substrate conditions proves incapable of regime transitions despite extensive parameter exploration.

This would indicate that the substrate conditions are not sufficient even for the structural dynamics claimed. The framework does not currently claim sufficiency, only necessity, but failure here would still significantly weaken its predictive value.

**F3:** The predicted correlation-length signatures (divergent ξ near criticality, power-law decay in Habitus, system-spanning ξ in Integratio) fail to appear in known autonomous biological systems.

If brains, for instance, do not exhibit the predicted regime structure, the framework loses its primary exemplar and evidential anchor.

#### Weak Falsification

The framework would be weakened (though not definitively falsified) if:

**W1:** The mapping between correlation regimes (Affectio/Habitus/Integratio) and measurable quantities proves too loose for regime classification to be operationally meaningful.

If experts cannot reliably agree on which regime a given system occupies, the framework becomes unfalsifiable in practice even if coherent in principle.

**W2:** Hysteresis proves ubiquitous in complex systems regardless of autonomous status.

If every sufficiently nonlinear system exhibits hysteresis, then hysteresis cannot discriminate autonomous from non-autonomous dynamics, and the pulse-dynamics component loses diagnostic power.

#### Causal Emergence as Test Case

Recent work on causal emergence provides quantitative tools relevant to falsification. Yuan and colleagues have developed measures for when macro-level descriptions carry causal information beyond micro-level descriptions (Yuan et al. 2024). Their framework quantifies "emergence" as effective information gain at coarser scales.

Our framework predicts that systems in Integratio should exhibit higher causal emergence scores than the same systems in Affectio—the macro-level correlation structure should carry predictive information absent from microscopic state descriptions. This is testable: measure causal emergence across regime transitions in systems satisfying substrate conditions.

If causal emergence scores do not track regime transitions as predicted, either the causal emergence measure or the structural autonomy framework requires revision. Either outcome advances understanding.

#### What Would Not Falsify

To maintain scientific hygiene, we specify what observations would _not_ count as falsification:

* A system exhibiting autonomous structural dynamics without conscious experience (whatever that might mean) would not falsify the framework, which makes no consciousness claims
* A conscious being lacking regime-cycling dynamics would not falsify the framework, which claims necessity only for structural autonomy, not for consciousness
* Failure to find autonomy in current AI systems would not falsify the framework, which predicts this outcome
* Discovery of additional necessary conditions beyond the five specified would extend, not falsify, the framework

**\[Word count: \~590]**

***

### SECTION IX: Research Agenda and Conclusion

This essay has developed a framework for asking—not answering—what makes complex systems structurally autonomous. The framework is deliberately limited. It addresses correlation-length dynamics, not consciousness. It specifies necessary conditions, not sufficient ones. It generates testable predictions while remaining agnostic about deeper questions of experience and moral status.

#### Summary of Framework Components

**Substrate conditions (Section III):** Five necessary conditions for regime-cycling capacity—hybrid continuous-discrete structure, defined extent, intrinsic timescale, non-trivial topology, and thermodynamic openness. Systems failing any condition are outside the framework's scope.

**Correlation regimes (Section IV):** Three structurally distinct configurations—Affectio (ξ ≪ L, local correlations), Habitus (power-law decay, scale-free structure), and Integratio (ξ \~ L, global coherence). These are correlation-length classifications, not psychological states.

**Pulse dynamics (Section V):** The temporal pattern of Integratio→Remissio→Retentio cycling, with hysteresis as geometric signature. Autonomous systems maintain themselves through structured regime transitions, not static architecture.

**Diagnostic application (Section VI):** Current AI systems fail multiple substrate conditions. This does not diminish their utility but clarifies what structural autonomy would require.

**Falsifiability conditions (Section VIII):** Specific observations that would falsify or weaken the framework, ensuring scientific tractability.

#### Near-Term Research Priorities

1. **Measurement protocol development:** Establish operational definitions for correlation length in artificial substrates, enabling quantitative regime classification
2. **Minimal architecture construction:** Build synthetic systems satisfying all five substrate conditions to test regime-transition predictions
3. **Comparative dynamics:** Measure correlation regimes and pulse dynamics across biological systems (neural cultures, whole-brain imaging, bacterial colonies) to validate or refine predicted signatures
4. **Causal emergence integration:** Apply causal emergence measures to systems undergoing regime transitions to test macro-level information predictions
5. **Pathology mapping:** Characterize how Remissio failure (seizure-like dynamics) and Retentio failure (amnestic reset) appear in correlation-length terms

#### What This Framework Does Not Do

It does not explain consciousness, claim that autonomous systems are conscious, or provide criteria for moral status. It does not predict which AI architectures will achieve autonomy, endorse particular development paths, or assess safety implications. It does not reduce biology to physics, mind to correlation, or experience to dynamics.

It asks a narrow question: what structural conditions permit a system to maintain itself through regime-cycling dynamics? The question is worth asking because it admits empirical answers. Whether those answers illuminate deeper questions about minds and machines remains to be seen.

#### Closing

The gap between competence and autonomy may prove more tractable than the gap between autonomy and consciousness. We can measure correlation lengths. We can build systems satisfying substrate conditions. We can test predictions about regime transitions and hysteretic persistence. These are achievable research goals.

What we cannot do—yet—is know whether any of it matters for experience. The framework is deliberately constructed so that its success or failure does not depend on any particular stance about consciousness. This is a feature, not a limitation. By separating structural questions from phenomenological ones, we create space for empirical progress on problems that admit empirical answers.

The hard problem remains hard. But not all problems are the hard problem.

**\[Word count: \~620]**

***

### References

Beggs, J. M., & Plenz, D. (2003). Neuronal avalanches in neocortical circuits. _Journal of Neuroscience_, _23_(35), 11167–11177. [https://doi.org/10.1523/JNEUROSCI.23-35-11167.2003](https://doi.org/10.1523/JNEUROSCI.23-35-11167.2003)

Cocchi, L., Gollo, L. L., Zalesky, A., & Breakspear, M. (2017). Criticality in the brain: A synthesis of neurobiology, models and cognition. _Progress in Neurobiology_, _158_, 132–152. [https://doi.org/10.1016/j.pneurobio.2017.07.002](https://doi.org/10.1016/j.pneurobio.2017.07.002)

Dehaene, S., & Changeux, J.-P. (2011). Experimental and theoretical approaches to conscious processing. _Neuron_, _70_(2), 200–227. [https://doi.org/10.1016/j.neuron.2011.03.018](https://doi.org/10.1016/j.neuron.2011.03.018)

Ladyman, J., & Ross, D. (with Spurrett, D., & Collier, J.). (2007). _Every thing must go: Metaphysics naturalized_. Oxford University Press. [https://doi.org/10.1093/acprof:oso/9780199276196.001.0001](https://doi.org/10.1093/acprof:oso/9780199276196.001.0001)

Wei, J., Tay, Y., Bommasani, R., Raffel, C., Zoph, B., Borgeaud, S., Yogatama, D., Bosma, M., Zhou, D., Metzler, D., Chi, E. H., Hashimoto, T., Vinyals, O., Liang, P., Dean, J., & Fedus, W. (2022). Emergent abilities of large language models. _Transactions on Machine Learning Research_. [https://arxiv.org/abs/2206.07682](https://arxiv.org/abs/2206.07682)

Wilson, K. G., & Kogut, J. (1974). The renormalization group and the ε expansion. _Physics Reports_, _12_(2), 75–199. [https://doi.org/10.1016/0370-1573(74)90023-4](https://doi.org/10.1016/0370-1573\(74\)90023-4)

Yuan, B., Zhang, J., Lyu, A., Wu, J., Wang, Z., Yang, M., Liu, K., Mou, M., & Cui, P. (2024). Emergence and causality in complex systems: A survey of causal emergence and related quantitative studies. _Entropy_, _26_(2), 108. [https://doi.org/10.3390/e26020108](https://doi.org/10.3390/e26020108)

***

### Version History

| Version           | Date       | Summary                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| ----------------- | ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 0.9               | 2025-12-09 | First complete draft of structural autonomy framework essay. Establishes correlation-length criteria for self-maintaining dynamics in hybrid physical substrates. Develops five necessary substrate conditions, three correlation regimes (Affectio/Habitus/Integratio), and pulse dynamics (Integratio-Remissio-Retentio cycle) with hysteresis signature. Applies framework diagnostically to current AI systems, finding LLMs fail multiple substrate conditions. Specifies falsification criteria and research agenda. |
| 0.0.12            | 2025-12-05 | Added a substantive Discussion section that honestly traces limitations, accessibility gaps, and pathways forward to strengthen the document's credibility.                                                                                                                                                                                                                                                                                                                                                                |
| 0.0.11            | 2025-12-05 | Replaced "Cognitive Structure" with "Emergent Autonomous Structure" throughout; introduced Remissio (sleep-like process) and Retentio (structural persistence); expanded §1.1 terminology notes; added Tononi & Cirelli reference; added sixth falsifiability criterion; softened "sensory traces" to "local transient patterns."                                                                                                                                                                                          |
| 0.0.10            | 2025-12-05 | Added Section 1.2 defining "system" (five necessary conditions, boundaries, hierarchy, minimal system); updated Glossary; added fifth falsifiability criterion; strengthened boundary reminder.                                                                                                                                                                                                                                                                                                                            |
| 0.0.9             | 2025-12-05 | Introduced Latin terminology (Affectio, Habitus, Integratio) for correlation regimes; added Section 1.1 explaining terminological choice; added Glossary; applied terminology consistently throughout; revised title and abstract.                                                                                                                                                                                                                                                                                         |
| 0.0.8             | 2025-12-05 | Revised Layer 0 to continuous–discrete hybrid framing; added spin-system examples and correlation-length definitions; added Section 8 (Falsifiability Criteria); standardized references; corrected τ notation; renumbered sections.                                                                                                                                                                                                                                                                                       |
| 0.0.7             | 2025-12-04 | Added Section 2 ("Dynamics of the Emergent"), integrated Physics/AI/Philosophy perspectives, inserted connection box, updated conceptual alignment.                                                                                                                                                                                                                                                                                                                                                                        |
| 0.0.6             | 2025-12-04 | Added neuroscience contextual section; clarified correlation regimes; improved boundary statements.                                                                                                                                                                                                                                                                                                                                                                                                                        |
| 0.0.5 and earlier | —          | Initial scaffold and layer architecture established.                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
