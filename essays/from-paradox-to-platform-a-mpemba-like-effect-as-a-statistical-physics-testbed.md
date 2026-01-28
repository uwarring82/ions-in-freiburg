# From Paradox to Platform: A Mpemba-like Effect as a Statistical Physics Testbed

{% hint style="info" %}
**Authors:** Ulrich Warring\
**Draft version:** 0.2\
**Date:** January 2026
{% endhint %}

***

### 1. A Question Worth Taking Seriously

In 1963, a Tanzanian secondary school student named Erasto Mpemba noticed something odd while making ice cream. The hot mixture he placed in the freezer solidified before his classmates' cooled mixtures did. When he asked his teacher why, he was told he must be mistaken. Hot things cool slower than cold things—everyone knows that.

Mpemba persisted. Years later, he posed the question to Denis Osborne, a visiting physics professor, who had the scientific humility to say: "I don't know, but let's find out." Their subsequent experiments, published in 1969, gave the phenomenon its name and launched decades of controversy.

The Mpemba effect—the observation that hot water can sometimes freeze faster than cold water—has been rediscovered, debated, dismissed, and revived more times than almost any other simple physical phenomenon. It appears in Aristotle. It shows up in Francis Bacon. It has been declared solved and declared mythical, sometimes in the same year.

This essay argues that the Mpemba effect is neither a solved problem nor a myth. It is something more interesting: a well-posed question that was historically asked poorly. The tools to ask it properly now exist. More importantly, the question itself—once properly framed—becomes a gateway into statistical physics, nucleation theory, experimental design, and the practice of doing science collectively across communities and continents.

We believe the Mpemba effect deserves to be taken seriously, not because hot water always freezes faster (it doesn't), but because understanding _when_ it does and _why_ reveals something genuine about how phase transitions work in the real world.

***

### 2. Why the Mess?

If the Mpemba effect is real, why hasn't it been definitively established? And if it's not real, why does it keep appearing in careful experiments?

The answer lies in three interrelated problems that plagued early work and continue to confuse the literature.

#### The endpoint problem

"Freezing" is not a single event. When we ask whether hot water freezes faster, we might mean:

* **Nucleation onset:** the moment the first ice crystal forms
* **Surface ice:** when a visible layer appears on top
* **Full solidification:** when the entire sample is solid

These are different physical processes occurring on different timescales and governed by different mechanisms. Nucleation is stochastic—it depends on random molecular fluctuations and surface imperfections. Heat removal is deterministic—it follows the laws of thermal conduction and convection. Comparing "freezing times" without specifying which endpoint you measured is like comparing race times without agreeing on the finish line.

A 2020 study by Burridge and Hallstadius at Imperial College London demonstrated that much of the historical confusion stems from this ambiguity. When they controlled for endpoint definition and other variables, they found that the effect could be observed reproducibly under specific conditions—but only when those conditions were actually controlled.

#### The hidden variables problem

A glass of water is not a simple system. Its freezing behaviour depends on what's dissolved in it, what container it's in, how that container was prepared, how the sample is being cooled, and where you place your thermometer. Most early Mpemba experiments controlled few of these variables. Two experimenters running "the same" protocol could easily be measuring different systems. This is why the literature is full of confident contradictions: people were not actually disagreeing about the same phenomenon.

#### The single-trace problem

Perhaps the deepest issue is statistical. Nucleation is inherently probabilistic. Even under identical conditions, the same sample will freeze at different times on different trials. This means that comparing one hot sample to one cold sample tells you almost nothing. You need distributions: many trials, same conditions, statistical analysis.

Most historical Mpemba experiments reported single traces or small numbers of trials. A "positive" result might be a statistical fluctuation; a "negative" result might have missed the effect by bad luck. Without distributions, we cannot distinguish signal from noise.

***

### 3. The Design-Space Reframe

The path out of this confusion is not to abandon the question but to reformulate it. Instead of asking "Does hot water freeze faster?" we should ask: "Under what conditions, and by what mechanism, might preheated water exhibit earlier freezing than initially cooler water?"

This reframing transforms the Mpemba effect from a yes/no paradox into a parameter-exploration problem. The relevant parameters include:

* **Bulk impurities (**_**P\_b**_**):** What's in the water? Ultrapure, tap water, or deliberately seeded with known nucleating agents?
* **Wall nucleation state (**_**P\_w**_**):** How rough or chemically active is the container surface? Measured by surface roughness or water contact angle.
* **Container material (**_**M**_**):** Borosilicate glass, soda-lime glass, plastic? Each has different surface chemistry.
* **Thermal history (**_**H**_**):** Has the container been heated before? How many times, to what temperature, for how long?
* **Cooling rate (**_**κ**_**):** How fast is heat being removed?
* **Sample volume (**_**V**_**):** Small volumes minimise internal gradients; large volumes introduce convection complexity.
* **System openness (**_**σ**_**):** Sealed or open to evaporation?
* **Freeze criterion (**_**F**_**):** Which endpoint are we measuring?

We have developed a design-space map—a structured framework that identifies which mechanisms are likely to dominate under which parameter combinations. The map does not claim to explain the Mpemba effect; it organises the conditions under which different candidate explanations become testable.

Crucially, the map functions as a _coordination device_. Different groups working at different levels of sophistication can contribute comparable data because they share a common language for reporting conditions. Without this shared framework, a hundred independent experiments produce a hundred incomparable anecdotes. With it, they produce a distributed dataset that grows more powerful over time.

The design-space map will be archived on Zenodo as a living document, versioned and open to community refinement.

***

### 4. A Tiered Research Ecosystem

One of the beauties of the Mpemba effect is its accessibility. You do not need a particle accelerator or a cleanroom. But accessibility does not mean lack of depth—it means that meaningful contributions can come from many levels of expertise, each feeding the same scientific framework.

We envision a three-tiered ecosystem where schools, universities, and research laboratories collaborate on the same question, each contributing what they can and learning what they need.

#### Tier 1: Schools and citizen scientists

A secondary school science club can run a valid Mpemba experiment with basic equipment: sealed glass jars, a thermometer, a home freezer, and patience. The key discipline is protocol. Define your endpoint clearly. Control what you can. Record your conditions honestly. Repeat the experiment multiple times.

At this tier, students learn the foundations of experimental science: controlling variables, distinguishing observation from interpretation, accepting that nature might not cooperate with expectations. These lessons transfer far beyond the Mpemba effect.

But here is the critical point: school experiments are not merely pedagogical. If a classroom in Nairobi reports their parameters according to the shared framework—container type, water source, thermal history, endpoint definition, number of trials—their data enters the same scientific pool as university results. They are doing real science at an accessible entry point, not a simulation of science for training purposes.

#### Tier 2: Undergraduate teaching laboratories

University physics and chemistry students can push further. With access to ultrapure water, calibrated thermocouples, continuous temperature logging, and systematic parameter variation, undergraduates can target quantitative questions: What is the distribution of nucleation temperatures across 30 or more trials? How does that distribution shift when we change surface roughness? Does thermal history matter independently of initial temperature?

At this tier, students learn statistical thinking—why reporting a mean without a variance is incomplete, why null results constrain theories, why systematic errors can masquerade as signals. They encounter nucleation theory: the interplay of energy barriers, surface chemistry, and stochastic fluctuations.

A well-designed undergraduate project can do more than confirm or deny the Mpemba effect. It can map which parameter regimes show no effect—itself a scientific contribution that helps focus more advanced efforts.

#### Tier 3: Research frontiers

For research groups with specialised equipment, the Mpemba effect opens onto genuinely sophisticated physics:

**High-throughput micro-capsule arrays.** Imagine thousands of identical micro-capsules, each containing a small water droplet with controlled impurities, monitored in parallel by automated optical detection. This setup generates nucleation statistics at a scale impossible with traditional methods. The capsule walls become a controlled variable; batch-to-batch consistency enables the statistical power that single-sample experiments lack.

**Precision sensors as local probes.** Advanced sensing techniques—including nitrogen-vacancy centres in diamond—can probe local temperature and phase transitions with nanoscale resolution. The possibility of using functionalised nanoparticles as both nucleation sites and sensors could enable direct observation of the nucleation microenvironment, though optical heating and surface chemistry introduce complications that require careful control.

**Microgravity experiments.** On the International Space Station, buoyancy-driven convection is strongly suppressed. Many candidate Mpemba mechanisms invoke convection currents; removing this variable clarifies what remains. Our prediction: in sealed, conduction-dominated samples, any Mpemba-like behaviour that persists in microgravity is primarily attributable to nucleation statistics rather than convection. This is a falsifiable claim waiting for an experiment.

**Theoretical grounding.** Stochastic thermodynamics has identified "Mpemba-like" behaviour in various model systems—situations where a system farther from equilibrium relaxes faster than one closer to equilibrium. Connecting these theoretical frameworks to real water remains challenging, but both theory and experiment now ask about distributions of relaxation times rather than single trajectories. This shared language may eventually enable quantitative comparison.

Each tier feeds the others. School observations raise questions that undergraduates can quantify. Undergraduate null results constrain the parameter space that research groups should explore. Research-grade measurements anchor the distributions that everyone interprets. A student who encounters the Mpemba effect in secondary school, revisits it with better statistics as an undergraduate, and designs a micro-capsule platform as a doctoral researcher has traced a complete scientific arc through a single evolving question.

***

### 5. Science in Public, in Real Time

Most science reaches the public after the fact: cleaned up, narrated in hindsight, stripped of uncertainty. We propose something different. This research campaign should be visible as it unfolds—not as polished retrospective but as live process.

The Mpemba effect is unusually suited to real-time visibility. The experiments are visual: you can watch ice form, see the temperature spike when nucleation releases latent heat, compare traces side by side. The question is intuitive: everyone has encountered freezing; everyone has a freezer. The human story resonates: a student who refused to accept dismissal, a professor who took the question seriously.

#### A platform gradient

Different audiences will engage at different depths, and the campaign should meet them where they are:

**Social media** captures moments: a school in São Paulo posts their first successful nucleation video; a research group shares a surprising null result with a brief explanation. These fragments build collective awareness and recruit new participants.

**YouTube and video platforms** allow for explainers and lab tours. What does a surface roughness measurement actually involve? How do you set up a temperature-controlled bath? What does a micro-capsule array look like under the microscope? This level of detail helps prospective participants understand what's involved and demystifies laboratory work.

**Podcasts and long-form video** support deeper engagement: interviews with teachers and students across tiers, methodological discussions about why certain controls matter, debates about what the accumulating data suggest. This format suits audiences who want to follow the scientific reasoning, not just the highlights.

**Documentary and cinema** synthesise the narrative arc: the history of the question, the launch of the coordinated campaign, the accumulating results, the surprises and setbacks, the eventual (partial?) resolution. A documentary made in three years will tell a different story than one made in one year—and that uncertainty is itself part of what makes the project compelling.

#### The anchor and the sail

Real-time visibility carries risks. Media attention can distort scientific priorities; dramatic results may be overemphasised while informative nulls are ignored; the pressure to produce content can compromise the patience that good science requires.

The design-space map is our anchor. Whatever gets filmed, whatever goes viral, the underlying framework remains stable: where in parameter space are we, what did we observe, how does it constrain our understanding? The media is the sail—it catches attention, it propels participation—but the anchor keeps us from drifting into spectacle.

The commitment must be explicit: a boring null result receives the same visibility as a dramatic confirmation. The audience sees how science actually works—messy, iterative, collective, often inconclusive. This honesty is pedagogically valuable precisely because it is rare.

***

### 6. An Invitation

The Mpemba effect has languished for decades as a curiosity—occasionally investigated, frequently dismissed, never resolved. We believe the time is ripe to change this.

The tools now exist: shared frameworks for coordination, high-throughput platforms for statistics, precision instruments for mechanism identification, theoretical models for interpretation. The communication infrastructure now exists: global visibility, real-time sharing, platforms for every depth of engagement. What remains is the work itself.

We invite participation at every tier:

**If you teach science**, consider the Mpemba effect as a classroom module. The protocol is accessible; the statistical reasoning transfers to any experimental discipline; the connection to ongoing research is genuine, not manufactured. Your students' data, properly reported against the shared framework, contributes to the collective map.

**If you run a teaching laboratory**, design a project around systematic parameter variation. Pick a boundary from the design-space map and test it. Report your distributions, including—especially—your null results.

**If you lead a research group**, consider where your expertise intersects: surface science, microfluidics, cryogenics, optical sensing, stochastic modelling. The open questions are technically demanding and scientifically substantive.

**If you communicate science**, follow the campaign. The story is unfolding in real time; the ending is genuinely unknown. That uncertainty is what makes it worth telling.

We are making the design-space map freely available on Zenodo with version control. We will maintain a registry of participating groups and a repository of reported results, structured so that contributions from any tier can be integrated. The goal is not a single definitive paper but a collective mapping effort that grows over years.

***

### Coda: Why This Matters

The Mpemba effect is, in one sense, a small question. Whether hot water sometimes freezes faster than cold water has no technological stakes, no medical applications, no policy implications.

But small questions, taken seriously, teach large lessons. This one teaches:

* That phenomena dismissed as folklore may contain real physics.
* That reproducibility crises often stem from ambiguous protocols, not fraud or incompetence.
* That statistical thinking transforms noise into signal.
* That collective investigation, properly coordinated, outperforms isolated heroism.
* That science can unfold in public view without becoming spectacle.
* That a secondary school student can contribute to the same question as a research professor—not as outreach theatre, but as genuine collaboration.

Erasto Mpemba was told he must be mistaken. He wasn't—not entirely. The question he asked was genuine; only the methods to answer it were missing. Sixty years later, we have those methods: the frameworks, the instruments, the platforms, the global connectivity.

The question is still open. Let's find out together.

***

### References and Resources

**Design-space map:** \[Zenodo DOI to be added upon publication]

**Key experimental references:**

* Burridge, H.C. & Hallstadius, O. (2020). "Observing the Mpemba effect with minimal bias." _Proc. R. Soc. A_ 476: 20190829.
* Burridge, H.C. & Linden, P.F. (2016). "Questioning the Mpemba effect." _Sci. Rep._ 6: 37665.

**Nucleation theory:**

* Turnbull, D. (1950). "Kinetics of heterogeneous nucleation." _J. Chem. Phys._ 18: 198–203.
* Kelton, K.F. & Greer, A.L. (2010). _Nucleation in Condensed Matter._ Pergamon.

**Theoretical frameworks:**

* Lu, Z. & Raz, O. (2017). "Nonequilibrium thermodynamics of the Markovian Mpemba effect." _PNAS_ 114: 5083–5088.
* Kumar, A. & Bechhoefer, J. (2020). "Exponentially faster cooling in a colloidal system." _Nature_ 584: 64–68.

***

_This essay is released under CC-BY-4.0. We welcome correspondence, critique, and collaboration._
