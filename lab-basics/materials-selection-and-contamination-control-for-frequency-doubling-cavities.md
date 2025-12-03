---
description: How to enable long-lasting performance.
icon: lightbulb-exclamation-on
---

# Materials Selection and Contamination Control for Frequency Doubling Cavities

### Purpose and Scope

**Target audience:** BSc, MSc, and PhD students building SHG/THG/FHG laser systems\
**Application:** External ring cavities for frequency doubling (particularly NIR to VIS and VIS to UV)\
**Critical context:** Nonlinear crystals (LBO, BBO) operate at elevated temperatures (50-100°C) with entrance/exit surfaces **exposed to ambient air**, creating direct contamination pathways

**Learning objective:** Understand how materials choices and surface preparation affect long-term optical performance, and implement contamination control protocols that enable months-to-years of stable operation.

***

### Executive Summary: The Contamination Problem

#### Why This Matters

When generating UV light (particularly <300 nm), even trace organic contamination on crystal surfaces causes:

1. **Progressive power loss:** 10-50% degradation over 100-1000 hours
2. **Photochemical damage:** UV photons (4.4 eV @ 280 nm) break C-H bonds → polymerization on surfaces
3. **Thermal runaway:** Contaminated surfaces absorb more → heat → more contamination
4. **Experimental failure:** Cannot maintain stable cavity lock, data becomes unreliable

#### The Core Mechanism

```
[Organic materials in cavity] 
    ↓ (outgassing: molecules enter air)
[Thermal convection from hot crystal]
    ↓ (transport to crystal surface)
[50-100°C surface temperature]
    ↓ (condensation: "sweet spot" for deposition)
[280 nm UV photons + O₂]
    ↓ (photochemistry: polymerization)
[Absorbing polymer layer on crystal]
    ↓ (feedback loop: absorption → heating → more outgassing)
[System failure]
```

**Critical insight:** Even "clean" laboratory air contains enough organic molecules that, when concentrated by thermal gradients and polymerized by UV, will contaminate your crystals in weeks to months without proper mitigation.

#### What You'll Learn

1. **Source identification:** Which materials in your cavity are contamination sources (ranked by severity)
2. **Material selection:** What to use, what to avoid, and why (with specific product recommendations)
3. **Surface preparation:** Cleaning and baking protocols that reduce outgassing by 1,000-10,000×
4. **Performance expectations:** Realistic timelines for crystal lifetime based on your choices
5. **Monitoring and maintenance:** How to detect contamination early and establish cleaning cycles

***

### Part 1: Contamination Source Ranking

#### The Contamination Budget Concept

Total contamination rate = Σ(Surface area × Outgassing rate × Proximity factor × UV exposure factor)

**Your goal:** Reduce total contamination rate to <10⁻⁹ Torr·L/s for multi-month operation.

***

#### Source 1: Black Anodized Aluminum (CRITICAL - AVOID)

**Risk Level:** 🔴 **CRITICAL** (Dominant contamination source: 60-70% of total)

**What It Is**

* Aluminum with porous Al₂O₃ surface layer
* **Dyed** with organic pigments (azo compounds, anthraquinones)
* **Sealed** with polymer coating (acrylic or epoxy-based)

**Why It's Problematic**

| Property            | Value                            | Impact                                 |
| ------------------- | -------------------------------- | -------------------------------------- |
| **Outgassing rate** | 10⁻⁶ to 10⁻⁵ Torr·L/s/cm²        | 100-1000× higher than acceptable       |
| **Surface area**    | 200-500 cm² (typical stage)      | Large emission source                  |
| **Dye volatility**  | Evaporates at 50-80°C            | Releases colored organics continuously |
| **UV interaction**  | Black absorbs UV → local heating | Accelerates outgassing near beam paths |

**Typical lifetime impact:** Reduces BBO lifetime from 5,000 hours → 50-100 hours

**Physical Mechanism**

1. **Thermal desorption:** Organic dyes have vapor pressure \~10⁻⁶ Torr at room temp
2. **Sealer degradation:** Polymer sealers continuously release small molecules (monomers, solvents)
3. **UV photodegradation:** 280 nm breaks dye molecules → gaseous products
4. **Transport:** Convection currents carry organics to hot BBO surface (50°C)
5. **Deposition:** Organics condense preferentially on 50°C surface (thermal sweet spot)
6. **Polymerization:** UV + O₂ + organic deposits → cross-linked polymer film

**Evidence:** Commercial UV laser manufacturers explicitly prohibit black anodized aluminum near beam paths \[1].

**Decision: AVOID - Replace with Alternatives**

**MANDATORY REPLACEMENT if black anodized within 20 cm of BBO/LBO crystals.**

**Alternative A: Natural (Clear) Hard Anodization (Type III)**\
✅ **RECOMMENDED - Best balance of performance and cost**

* Composition: Thick Al₂O₃ layer (50-100 μm), **no organic dyes**
* Sealing: Hot water seal (converts Al₂O₃ to AlOOH) - inorganic process
* Color: Clear/silver or light gold (from oxide thickness only)
* Outgassing: <10⁻⁹ Torr·L/s/cm² (1,000× better than black)
* Cost: Similar to black anodization
* Suppliers: Most anodization shops can provide "clear hard coat"

**Specification for procurement:**

```
"MIL-A-8625 Type III, Class 1 or 2, clear (no dye), 
sealed by boiling DI water method (no polymer sealer)"
```

**Alternative B: Bare Machined Aluminum**\
✅ **ACCEPTABLE - Lowest cost**

* Leave natural mill finish or bead blast for uniform appearance
* Protective coating: Clear conversion coating (Alodine/Iridite) - **chromate-based, inorganic**
* Outgassing: <10⁻⁹ Torr·L/s/cm² (excellent)
* Appearance: Industrial/unfinished look
* Risk: May oxidize (white powdery corrosion) in humid environments

**Alternative C: Electropolished Stainless Steel**\
✅ **BEST - Premium option**

* Material: 304 or 316 stainless steel
* Surface: Electropolished (Ra < 0.4 μm, mirror-like finish)
* Outgassing: <10⁻¹⁰ Torr·L/s/cm² (best available)
* Cost: 2-3× more than aluminum (material + machining)
* Weight: \~3× heavier than aluminum
* **Used in: LIGO, synchrotron beamlines, UHV systems**

**Alternative D: Anodized Aluminum (Existing Parts) - Bake-Out Treatment**\
⚠️ **CONDITIONAL - Only if replacement not feasible**

Protocol for "cleaning" existing black anodized parts:

```
1. Bake at 200-250°C / 48 hours in air (furnace or oven)
2. Purpose: Pyrolyze organic dyes and sealers
3. Result: Grey/mottled appearance (aesthetically degraded)
4. Outgassing reduced to ~10⁻⁸ Torr·L/s/cm² (10-100× improvement)
5. WARNING: May cause warping in thin-walled parts
6. Verify dimensional tolerances after bake
```

**When to use this:** Emergency repair, budget-constrained projects, or low-criticality applications.

**Procurement Guidance**

**Recommended vendors for clean aluminum stages:**

* **Thorlabs:** Custom optomechanics in natural anodized or stainless
* **OptoSigma:** "Clean room grade" stages (specify no black anodization)
* **Newport:** Stainless steel or natural anodized options available
* **Custom fabrication:** Local machine shop + anodization service

**Cost comparison (per linear stage, \~20 cm travel):**

* Black anodized (commercial): €300-600
* Natural anodized: €300-650 (comparable)
* Stainless steel: €800-1,500 (premium)
* Bare aluminum (custom): €200-400 (budget)

**References**

\[1] Coherent Inc., "UV Laser System Installation Guide" (2018) - Prohibits organic materials within 50 cm of <300 nm beam paths\
\[2] Rettner et al., "Contamination of optical surfaces by organic vapors," _Appl. Opt._ 26, 3402 (1987)\
\[3] LIGO Technical Note T1500200, "Materials for use in LIGO vacuum systems"

***

#### Source 2: Machining Oil Residues (CRITICAL - CLEAN)

**Risk Level:** 🔴 **CRITICAL** (Second largest source: 10-20% of total)

**What It Is**

**"Invisible contamination"** - microscopic oil films from manufacturing processes:

* Cutting fluids from CNC machining
* Drawing compounds from metal forming
* Anti-seize compounds on threads
* Fingerprint oils from handling
* Protective oils applied during shipping

**Key insight:** Even visually "clean" parts have 0.1-10 μm oil films (molecular to microscopic scale).

**Why It's Problematic**

| Property             | Value                                          | Impact                                |
| -------------------- | ---------------------------------------------- | ------------------------------------- |
| **Outgassing rate**  | 10⁻⁶ to 10⁻⁵ Torr·L/s/cm²                      | Same as black anodization             |
| **Surface coverage** | 50-200 cm² (all machined parts)                | Every threaded hole, every surface    |
| **Vapor pressure**   | High at room temp                              | Volatile even without heating         |
| **UV reactivity**    | Extreme - hydrocarbons photopolymerize readily | Direct precursors to surface deposits |

**Physical properties of typical machining oils:**

* Composition: Long-chain hydrocarbons (C₁₅-C₃₅), additives (sulfur, chlorine compounds)
* Boiling point: 300-400°C (but vapor pressure is significant at room temp)
* UV absorption: Strong at 280 nm (σ ≈ 10⁻¹⁸ cm²)

**Detection**

**Simple test (for training/demonstration):**

```
Dragon's Breath Test for Oil Contamination:

1. Take a "clean" machined part (as received from supplier)
2. Breathe on surface to fog it
3. Observe fog clearing pattern:
   - Clean surface: Uniform clearing in 2-3 seconds
   - Oily surface: Streaky clearing, beads of water form
4. Result: Almost all parts fail this test initially
```

**Quantitative test:**

* Wipe surface with clean white lint-free wipe
* Inspect wipe under UV lamp (365 nm) - oil fluoresces bright blue
* Or: Weigh wipe before/after → mass of oil extracted

**Decision: MANDATORY CLEANING PROTOCOL**

**NO EXCEPTIONS:** All metal parts within 30 cm of crystals must be ultrasonically cleaned and baked before installation.

**Protocol: 3-Stage Ultrasonic Cleaning + Thermal Bake**

```
EQUIPMENT REQUIRED:
- Ultrasonic cleaner (≥2 L capacity, 40 kHz)
- Three stainless steel beakers (1 L each)
- Solvents: Acetone (semiconductor grade), IPA (99.5%+), DI water
- Vacuum oven or air oven (≤200°C capability)
- Powder-free nitrile gloves
- Clean Al foil or stainless trays for baking

STEP 1: DISASSEMBLY
- Completely disassemble all parts (remove screws, springs, washers)
- Handle only with powder-free gloves (fingerprints = oils)
- Document assembly (photos) for later reassembly

STEP 2: ULTRASONIC CLEANING SEQUENCE
Duration: 15 minutes per solvent, temperature: room temp

Bath 1 - Acetone:
  - Purpose: Dissolve oils, greases, and organic residues
  - Fill beaker with fresh acetone (replace every 3-5 batches)
  - Submerge parts completely
  - Ultrasonic power: 100% (cavitation should be vigorous)
  - After 15 min: Remove parts, let drain 30 seconds

Bath 2 - Isopropanol (IPA):
  - Purpose: Rinse away acetone and any loosened residues
  - Fill beaker with fresh IPA
  - Ultrasonic 15 minutes
  - IPA is less aggressive than acetone, final cleaning step

Bath 3 - Deionized Water:
  - Purpose: Remove any residual IPA and ionic contaminants
  - Fill beaker with DI water (resistivity >10 MΩ·cm)
  - Ultrasonic 15 minutes
  - Especially important for parts that will see high voltage (piezo drivers)

STEP 3: DRYING
- Remove from DI water bath
- Blow dry with compressed nitrogen (filtered, oil-free)
- Or: Place in vacuum oven at 60°C / 1 hour to evaporate water

STEP 4: THERMAL BAKE (CRITICAL)
Temperature: 200°C
Duration: 2-4 hours
Atmosphere: Air (oven with convection)

Purpose: Pyrolyze any remaining organic films that survived cleaning
  - Mineral oils thermally decompose above 180°C
  - Volatile products escape as CO₂, H₂O, light hydrocarbons
  - Leaves clean oxide surface

Protocol:
  - Place parts on Al foil or stainless tray (clean surface)
  - Ramp: 25°C → 200°C over 30 minutes (avoid thermal shock)
  - Hold: 200°C for 2-4 hours
  - Ramp down: 200°C → 50°C over 30 minutes
  - Remove while still warm (>40°C) to prevent moisture condensation
  - Store in clean zip-lock bags with desiccant until use

STEP 5: VERIFICATION
- Dragon's breath test on cooled parts (should pass: uniform fog clearing)
- Visual inspection under bright light (should see no residues, streaks)
- If test fails: Repeat ultrasonic cleaning

STEP 6: REASSEMBLY
- Handle only with powder-free gloves
- Use cleaned screws, washers, springs (do NOT mix with uncleaned parts)
- Assemble in cleanroom or laminar flow hood (ISO Class 6-7)
- NO lubricants, NO thread-locking compounds, NO adhesive labels
```

**Time investment:** \~4 hours per batch of parts (mostly unattended)\
**Cost:** €50-200 for solvents + oven time (one-time for each assembly)\
**Benefit:** 100-1,000× reduction in outgassing from machined parts

**Special Cases**

**Springs and Washers:**

* Often have anti-corrosion oils that survive normal cleaning
* **Enhanced protocol:** Bake at 300°C / 1 hour (burns off oils completely)
* Verify spring constant unchanged after bake (measure force-displacement curve)

**Threaded Parts:**

* Threads are hard to clean (large surface area, crevices)
* After ultrasonic cleaning, thread with clean brass wire brush to mechanically remove residues
* Bake as normal

**Anodized Parts:**

* Porous anodization layer can absorb oils during machining
* Ultrasonic cleaning helps but doesn't fully extract
* Baking at 150-200°C drives out absorbed oils

**What NOT To Do**

❌ **"Wipe clean with IPA cloth"** - Spreads oil, doesn't remove it\
❌ **Skip baking step** - Cleaning removes bulk oils but not molecular films\
❌ **Use contaminated cleaning baths** - Replace solvents regularly\
❌ **Handle cleaned parts with bare hands** - Fingerprints re-contaminate instantly\
❌ **Apply lubricants after cleaning** - Defeats the entire purpose

**Expected Improvement**

| Treatment                     | Outgassing Rate   | BBO Lifetime Impact |
| ----------------------------- | ----------------- | ------------------- |
| **As received from supplier** | 10⁻⁶ Torr·L/s/cm² | 50-100 hours        |
| **Ultrasonic cleaned only**   | 10⁻⁷ Torr·L/s/cm² | 200-500 hours       |
| **Cleaned + 200°C bake**      | 10⁻⁹ Torr·L/s/cm² | 3,000-5,000 hours   |

**Return on investment:** 4 hours cleaning → 50-100× lifetime increase

**References**

\[4] Palik & Henck, "Effect of cleaning procedures on the damage threshold of molybdenum mirrors," _Appl. Opt._ 23, 3796 (1984)\
\[5] NASA SP-R-0022A, "Vacuum stability requirements of polymers" - Section on cleaning protocols\
\[6] Agrawal & Menzel, "Contamination of grazing incidence optics," _Opt. Eng._ 32, 1593 (1993)

***

#### Source 3: Piezoelectric Actuator Stacks (MODERATE - MITIGATE)

**Risk Level:** 🟠 **MODERATE** (5-10% of total contamination)

**What It Is**

**Internal structure of piezo stack:**

```
[Electrode (Ag/Ni)]
[Ceramic (PZT)] ← Inorganic, no problem
[Epoxy layer (Ag-filled)] ← Organic adhesive (10-50 μm thick)
[Ceramic (PZT)]
[Epoxy layer]
... (repeated 20-200 times)
[Electrode]
[Wire attachment (solder + strain relief)] ← Often silicone rubber
[Protective coating] ← Sometimes polymer conformal coat
```

**Hidden organics:**

* Inter-layer epoxy: Silver-filled epoxy bonds ceramic disks
* Wire insulation: PVC, PTFE, or polyimide (Kapton)
* Strain relief: Silicone rubber or epoxy potting at wire exit
* Coatings: Polyurethane, epoxy, or acrylic moisture barriers

**Why It's Problematic**

**Outgassing pathways:**

1. **Diffusion through grain boundaries:** PZT ceramic is polycrystalline with micron-scale grains
2. **Permeation through electrodes:** Thin (1-10 μm) metal electrodes are not perfect barriers
3. **Edge emission:** Epoxy layers exposed at cut edges of piezo stack
4. **Wire junction:** Largest emission area - strain relief directly exposed

**Outgassing rates (typical multilayer piezo):**

* Total surface area: 2-10 cm² (depending on size)
* Fresh piezo: 10⁻⁷ Torr·L/s/cm² (similar to unbaked epoxy)
* After 100 hours room-temp aging: 10⁻⁸ Torr·L/s/cm²
* After pre-bake: 10⁻⁹ to 10⁻¹⁰ Torr·L/s/cm²

**Temperature dependence:**

* At room temp (20°C): Low outgassing
* Near hot oven (thermal gradient creates 40-60°C on back side): 10× higher outgassing
* **Critical:** Even though piezo is at "room temp," thermal radiation from 94°C LBO oven can heat nearby piezos

**Material Variability**

**Commercial piezo stacks vary widely in cleanliness:**

| Manufacturer                | Grade              | Typical Application      | Outgassing @ 25°C | UHV Compatible?                |
| --------------------------- | ------------------ | ------------------------ | ----------------- | ------------------------------ |
| **Physik Instrumente (PI)** | Standard           | General lab use          | 10⁻⁷ Torr·L/s     | ❌ No                           |
| **PI Ceramic**              | PICMA® Chip        | Precision positioning    | 10⁻⁸ Torr·L/s     | ⚠️ Marginal                    |
| **PI Ceramic**              | PICMA® Bender      | UHV-specified            | 10⁻⁹ Torr·L/s     | ✅ Yes                          |
| **Thorlabs**                | Standard PA series | General optomechanics    | 10⁻⁷ Torr·L/s     | ❌ No                           |
| **Noliac**                  | NAC2000 series     | Industrial               | 10⁻⁷ Torr·L/s     | ❌ No                           |
| **Noliac**                  | NAC2000-UHV        | Vacuum-specified         | 10⁻⁹ Torr·L/s     | ✅ Yes                          |
| **Custom builds**           | Varies             | Depends on specification | Variable          | Specify outgassing requirement |

**Cost difference:** UHV-grade piezos typically 2-3× price of standard grade

**Specification keywords for procurement:**

```
"UHV compatible" or "Low outgassing" or "ASTM E595 compliant" 
or "Vacuum grade" or "Bakeable to 150°C"
```

**Decision Framework**

**Scenario A: New piezo purchase (project start)**

✅ **RECOMMENDED:** Specify UHV-grade piezos from start

* Example: PI PICMA® Bender actuators with UHV option
* Example: Noliac NAC2000-UHV series
* Cost increment: +€100-300 per piezo
* Benefit: No pre-bake required, plug-and-play

**Scenario B: Existing standard-grade piezos**

✅ **ACCEPTABLE:** Pre-bake + encapsulation protocol (see below)

* Can achieve similar performance to UHV-grade with treatment
* Saves cost if piezos already purchased

**Scenario C: Budget-constrained / rapid prototyping**

⚠️ **CONDITIONAL:** Use standard piezos with partial mitigation

* Accept shorter BBO lifetime (1,000-2,000 hours instead of 5,000+)
* Plan for more frequent BBO cleaning cycles
* Document degradation rate for future budget justification

**Mitigation Protocol: Pre-Bake and Encapsulation**

**MANDATORY for standard-grade piezos, OPTIONAL for UHV-grade**

```
STEP 1: PRE-BONDING BAKE
Timing: BEFORE bonding mirror to piezo (critical)

Protocol:
  - Place bare piezo in vacuum oven
  - Temperature: 80-100°C (do NOT exceed piezo's max temp rating)
  - Duration: 48-72 hours
  - Pressure: <10⁻⁴ Torr (mechanical pump + cold trap)
  - Monitor: Log piezo capacitance before/after
    * Should remain within ±5% (if large change, piezo damaged)

Purpose: Drive off volatiles from internal epoxy layers
  - Low-molecular-weight monomers desorb first
  - Solvents and plasticizers evaporate
  - Reduces outgassing by 10-100×

STEP 2: BOND MIRROR TO PIEZO
(Follow mirror-piezo bonding procedure with EPO-TEK 353ND)

STEP 3: POST-BONDING ENCAPSULATION
Timing: After adhesive fully cured

Materials:
  - Aluminum foil (thickness: 25-50 μm, heavy-duty)
  - Kapton tape (high-temperature polyimide tape)

Method A - Full wrap (for piezos away from beam):
  1. Cut Al foil to wrap around piezo body
  2. Leave electrical connections exposed (solder pads or wire)
  3. Wrap foil around piezo, securing with Kapton tape
  4. Ensure no sharp foil edges that could cause electrical shorts
  5. Result: Aluminum acts as barrier to outgassing, and heat shield

Method B - Partial shield (for piezos near beam):
  1. Shield only non-optical faces (back and sides)
  2. Leave face with bonded mirror exposed (optical clearance)
  3. Use Kapton tape to attach foil shield to piezo mount

Benefits:
  - Reduces outgassing emission by 3-10× (diffusion barrier)
  - Thermal shielding reduces heating from nearby hot ovens
  - Improves thermal stability (more uniform temperature)
  - Minimal added complexity

STEP 4: SYSTEM-LEVEL VACUUM BAKE (if UHV system)
  - After full cavity assembly
  - 100-120°C / 48 hours in vacuum chamber
  - Final conditioning of all components
```

**Performance comparison:**

| Treatment                    | Piezo Outgassing | Contribution to BBO Contamination |
| ---------------------------- | ---------------- | --------------------------------- |
| **Untreated standard piezo** | 5×10⁻⁷ Torr·L/s  | 5-10% of total                    |
| **Pre-bake only**            | 5×10⁻⁸ Torr·L/s  | 1-2% of total                     |
| **Pre-bake + encapsulation** | 5×10⁻⁹ Torr·L/s  | <0.5% of total                    |
| **UHV-grade (no treatment)** | 5×10⁻⁹ Torr·L/s  | <0.5% of total                    |

**Electrical Considerations**

**Wire insulation choices:**

| Material               | Outgassing @ 25°C  | Temperature Rating | UV Resistance  | **Recommendation**                |
| ---------------------- | ------------------ | ------------------ | -------------- | --------------------------------- |
| **PVC**                | 10⁻⁵ Torr·L/s/cm²  | 80°C               | Poor (yellows) | ❌ **AVOID**                       |
| **Silicone rubber**    | 10⁻⁷ Torr·L/s/cm²  | 200°C              | Good           | ⚠️ **ACCEPTABLE** (with pre-bake) |
| **PTFE (Teflon)**      | 10⁻⁹ Torr·L/s/cm²  | 260°C              | Excellent      | ✅ **GOOD**                        |
| **Kapton (polyimide)** | 10⁻¹⁰ Torr·L/s/cm² | 400°C              | Excellent      | ✅ **BEST**                        |

**Decision:**

* If wire already has PVC insulation: Replace with PTFE or Kapton before installing in cavity
* If wire has silicone: Pre-bake at 150°C × 24 hours, then acceptable
* For new wiring: Use PTFE or Kapton-insulated wire from start

**Vendors for clean wire:**

* Omega Engineering: Kapton-insulated wire (28-36 AWG)
* Alpha Wire: FIT-221 PTFE insulated wire
* Allectra: UHV-compatible wiring kits

**Monitoring Piezo Health**

**Pre- and post-bake measurements (critical for quality control):**

```
Before bake:
  - Capacitance (@ 1 kHz, 1 Vrms): Record value _____ nF
  - Displacement (@ 100 V DC): Measure with laser vibrometer or interferometer _____ nm/V
  - Resonance frequency (impedance analyzer): _____ kHz

After bake:
  - Capacitance: Should be within ±5% of original
  - Displacement: Should be within ±10% of original
  - Resonance: Should be within ±2% of original

If deviations exceed these ranges: Piezo damaged by bake (temperature too high, or defective piezo)
```

**Accept/reject criteria:**

* Capacitance change <5%: ✅ Pass
* Capacitance change 5-10%: ⚠️ Caution (may have reduced lifetime)
* Capacitance change >10%: ❌ Reject (internal delamination likely)

**References**

\[7] Setter & Waser, "Electroceramic materials," _Acta Mater._ 48, 151 (2000) - Piezo internal structure\
\[8] PI Ceramic, "Piezo actuators for UHV applications," Application Note (2019)\
\[9] Bernardini et al., "Outgassing properties of piezoelectric actuators," _Vacuum_ 73, 347 (2004)

***

#### Source 4: Adhesive Bonds (LOW - IF PROPERLY TREATED)

**Risk Level:** 🟡 **LOW** (<1% of total contamination after proper treatment)

This was discussed extensively in previous sections. Key points summary:

**Materials Comparison**

| Adhesive           | Outgassing (unbaked) | Outgassing (baked) | Thermal Conductivity | **Use Case**                          |
| ------------------ | -------------------- | ------------------ | -------------------- | ------------------------------------- |
| **EPO-TEK 353ND**  | 10⁻⁷ Torr·L/s/cm²    | 10⁻¹² Torr·L/s/cm² | \~0.3 W/mK           | Mirror-to-piezo (thin bondline)       |
| **EPO-TEK H74**    | 10⁻⁷ Torr·L/s/cm²    | 10⁻¹² Torr·L/s/cm² | 1.3 W/mK             | Thermistor-to-oven (thermal coupling) |
| **Stycast 2850FT** | 10⁻⁷ Torr·L/s/cm²    | 10⁻¹² Torr·L/s/cm² | 1.28 W/mK            | High-voltage piezo bonds              |
| **Ceramabond 571** | 10⁻¹⁰ Torr·L/s/cm²   | Not needed         | 1.4 W/mK             | Inorganic alternative (thermistor)    |

**Mandatory Post-Cure Bake**

**Standard protocol (after 150°C / 1 hour cure):**

```
Phase 1: Extended post-cure in air
  - 150°C / 24 hours in convection oven
  - Purpose: Complete polymerization, drive off unreacted monomers

Phase 2: Vacuum bake
  - 100-120°C / 48-72 hours @ 10⁻⁵ Torr
  - Purpose: Remove absorbed moisture and residual volatiles
  - Monitor: RGA (residual gas analyzer) until background <10⁻¹⁴ Torr·L/s

Result: Outgassing reduced by 10⁴-10⁵×
```

**Without this bake:** Adhesives contribute 5-10% to contamination\
**With bake:** Adhesives contribute <0.5% to contamination

**Decision:** EPO-TEK 353ND for mirror bonds, H74 for thermistor bonds, with mandatory extended bake.

***

#### Source 5: PEEK Insulators (LOW - ACCEPTABLE)

**Risk Level:** 🟢 **LOW** (2-5% of total contamination)

**What It Is**

* Polyetheretherketone: High-performance thermoplastic
* Used for: Thermal insulation between hot ovens and cavity mounts, electrical insulation
* Chemical structure: Aromatic rings with ether linkages (very stable)

**Why It's Acceptable**

| Property               | Value                               | Assessment                            |
| ---------------------- | ----------------------------------- | ------------------------------------- |
| **Outgassing @ 25°C**  | 10⁻⁹ to 10⁻⁸ Torr·L/s/cm²           | 100× better than PVC, similar to PTFE |
| **NASA ASTM E595**     | TML <1%, CVCM <0.1%                 | Passes with margin                    |
| **Temperature rating** | Continuous use to 250°C             | Far exceeds cavity temps (50-94°C)    |
| **UV resistance**      | Moderate (yellows slowly at 280 nm) | Acceptable if not in direct beam      |

**Decision: ACCEPTABLE - Use As-Is**

**No replacement needed.** PEEK is one of the best thermoplastic choices for this application.

**Optional improvement:** If baking adhesives anyway, PEEK benefits from simultaneous bake:

* 150°C / 24 hours drives off absorbed moisture and any machining residues
* Reduces outgassing by additional 5-10×

**Alternatives (if PEEK unavailable):**

* **Macor** (machinable glass-ceramic): Zero outgassing, but brittle
* **Alumina (Al₂O₃)**: Excellent thermal properties, harder to machine
* **PTFE (Teflon)**: Similar outgassing, lower mechanical strength

**References**

\[10] Victrex, "PEEK for aerospace and vacuum applications," Technical Data Sheet (2020)\
\[11] NASA, "Materials selection for spaceflight applications" - Lists PEEK as approved material

***

#### Source 6: Cables and Connectors (LOW-MODERATE - SELECT CAREFULLY)

**Risk Level:** 🟡 **LOW-MODERATE** (3-8% depending on choices)

**Cable Insulation Materials**

| Material            | Outgassing @ 25°C  | Flexibility  | Temperature Rating | Cost     | **Recommendation**                       |
| ------------------- | ------------------ | ------------ | ------------------ | -------- | ---------------------------------------- |
| **PVC**             | 10⁻⁵ Torr·L/s/cm²  | Excellent    | 80°C               | Low      | ❌ **AVOID**                              |
| **Silicone rubber** | 10⁻⁷ Torr·L/s/cm²  | Excellent    | 200°C              | Moderate | ⚠️ **ACCEPTABLE** (pre-bake)             |
| **PTFE**            | 10⁻⁹ Torr·L/s/cm²  | Good         | 260°C              | Moderate | ✅ **RECOMMENDED**                        |
| **Kapton**          | 10⁻¹⁰ Torr·L/s/cm² | Poor (stiff) | 400°C              | High     | ✅ **BEST** (if flexibility not critical) |

**PVC problem:**

* Plasticizers (phthalates) continuously migrate to surface
* High vapor pressure → rapid contamination
* Common in commercial cables → often not specified clearly

**Detection:**

* Look for "105°C rated" cable → usually PVC
* "200°C rated" → usually silicone or PTFE
* If unclear: Ask vendor for material specification

**Decision: Replace PVC, Use PTFE or Kapton**

**Cable routing strategy:**

```
Priority 1: Eliminate PVC cables within cavity enclosure entirely
  - Replace with PTFE or Kapton insulated wire
  
Priority 2: Route cables away from BBO/LBO crystals
  - Keep all cables >20 cm from crystal surfaces
  - Use cable management (tie-down points) to maintain routing
  
Priority 3: Minimize cable length in cavity
  - Use feedthrough connectors at enclosure boundary
  - Run power cables outside enclosure when possible
  - Only signal cables inside (piezo drive, thermistor)
```

**Recommended cable suppliers:**

* **Omega Engineering:** Kapton-insulated thermocouple and instrument wire
* **Alpha Wire:** FIT-221 PTFE hook-up wire (18-30 AWG)
* **Lakeshore Cryotronics:** Quadlead wire (Kapton-insulated, designed for low outgassing)
* **Allectra:** UHV-compatible cable assemblies with CF or SubD feedthroughs

**Cost:** €5-20 per meter (PTFE/Kapton) vs. €1-3 per meter (PVC)

**Connectors**

**Avoid:** Standard D-sub connectors with plastic housings (nylon, polycarbonate)\
**Use:** Metal-body connectors or UHV-compatible feedthroughs

Examples:

* **Fischer UHV series:** All-metal connectors, bakeable
* **SubMiniature D (all-metal housing):** Available from ITT Cannon, Amphenol
* **Lemo UHV series:** Precision connectors for vacuum

***

#### Source 7: O-Rings and Seals (CRITICAL IF PRESENT - ELIMINATE)

**Risk Level:** 🔴 **CRITICAL** (if present within cavity enclosure)

**Decision: DO NOT USE elastomer seals inside cavity enclosure**

**Problem:**

* Even "UHV-compatible" o-rings outgas at 10⁻⁷ Torr·L/s/cm²
* Plasticizers, curatives, and mold release agents continuously desorb
* Large surface area in contact with air

**Alternative sealing methods:**

| Seal Type               | Material           | Outgassing         | Cost     | Application                  |
| ----------------------- | ------------------ | ------------------ | -------- | ---------------------------- |
| **Viton o-ring**        | Fluoroelastomer    | 10⁻⁷ Torr·L/s/cm²  | Low      | ❌ Avoid in cavity            |
| **Kalrez® o-ring**      | Perfluoroelastomer | 10⁻⁹ Torr·L/s/cm²  | High     | ⚠️ OK if >30 cm from BBO     |
| **Metal C-ring**        | Stainless steel    | 10⁻¹¹ Torr·L/s/cm² | Moderate | ✅ Preferred for vacuum       |
| **Conflat (CF) flange** | Copper gasket      | 10⁻¹² Torr·L/s/cm² | Low      | ✅ Best for UHV               |
| **Indium wire**         | Indium metal       | 10⁻¹¹ Torr·L/s/cm² | Moderate | ✅ Excellent for custom seals |

**If elastomer seals unavoidable:**

* Use Kalrez only (not Viton or Buna-N)
* Pre-bake at 200°C / 48 hours
* Keep >30 cm from crystals

***

### Part 2: Material Selection Decision Tree

#### For Each Component in Your Cavity

```
START: Component to be installed in frequency doubling cavity

Q1: Is component within 20 cm of BBO/LBO crystal?
    ├─ YES → Continue to Q2
    └─ NO  → Standard materials acceptable (still follow cleaning protocol)

Q2: Is component metal (structural, mount, stage)?
    ├─ YES → Continue to Q3
    └─ NO  → Continue to Q5 (non-metal)

Q3: Is metal currently black anodized?
    ├─ YES → STOP: Replace with natural anodized, bare aluminum, or stainless steel
    └─ NO  → Continue to Q4

Q4: Has metal been ultrasonically cleaned and baked?
    ├─ YES → ✅ OK to use
    └─ NO  → STOP: Clean and bake before installation

Q5: Non-metal component - what is it?
    ├─ Cable → Q6
    ├─ Adhesive → Q7
    ├─ Insulator (PEEK, ceramic) → Q8
    ├─ O-ring or seal → Q9
    └─ Other → Consult contamination specialist

Q6: Cable insulation material?
    ├─ PVC → STOP: Replace with PTFE or Kapton
    ├─ Silicone → Pre-bake 150°C × 24 hr, then OK
    ├─ PTFE or Kapton → ✅ OK to use
    └─ Unknown → Test or replace

Q7: Adhesive bond?
    ├─ EPO-TEK 353ND/H74 or Stycast → Continue to Q7a
    ├─ General-purpose epoxy (Devcon, etc.) → STOP: Not suitable, use EPO-TEK
    ├─ UV-cure optical adhesive → STOP: Not suitable for structural bonds
    └─ Cyanoacrylate (superglue) → STOP: High outgassing, not suitable

Q7a: Has adhesive been post-cured with extended bake?
    ├─ YES (150°C × 24 hr air + 100°C × 48 hr vacuum) → ✅ OK to use
    └─ NO → STOP: Must complete bake cycle before operation

Q8: Insulator material?
    ├─ PEEK → ✅ OK to use (optionally bake with adhesives)
    ├─ Macor or alumina (ceramic) → ✅ OK to use
    ├─ PTFE → ✅ OK to use
    ├─ Nylon, polycarbonate, acetal → STOP: Replace with PEEK or ceramic
    └─ Unknown → Identify material or replace with PEEK

Q9: Seal/o-ring?
    ├─ Can eliminate? → YES → Use metal seal (Conflat, indium wire)
    ├─ Must use elastomer? → Use Kalrez, pre-bake, keep >30 cm from crystal
    └─ Viton or Buna-N → STOP: Not suitable, replace with Kalrez or metal seal

END: Component approved for installation
```

***

### Part 3: Assembly Protocol Summary

#### Pre-Assembly Phase (Week 1)

**Day 1-2: Procurement verification**

* \[ ] All metal parts are natural anodized, bare aluminum, or stainless (no black anodization)
* \[ ] All cables are PTFE or Kapton insulated (no PVC)
* \[ ] Piezos are UHV-grade or standard (to be pre-baked)
* \[ ] Adhesives: EPO-TEK 353ND, H74, or equivalent NASA-certified
* \[ ] No elastomer seals within 20 cm of crystals

**Day 3-5: Cleaning protocol**

* \[ ] Disassemble all metal hardware
* \[ ] Ultrasonic clean: Acetone → IPA → DI water (15 min each)
* \[ ] Thermal bake: 200°C / 2-4 hours in air
* \[ ] Dragon's breath verification test
* \[ ] Store in clean bags with desiccant

**Day 6-7: Piezo pre-bake (if not UHV-grade)**

* \[ ] Vacuum bake piezos: 80-100°C / 48-72 hours @ <10⁻⁴ Torr
* \[ ] Measure capacitance before/after (verify <5% change)
* \[ ] Store in clean dry environment until bonding

#### Assembly Phase (Week 2)

**Day 1-3: Adhesive bonding**

* \[ ] Bond mirrors to piezos (EPO-TEK 353ND per procedure)
* \[ ] Bond thermistors to ovens (EPO-TEK H74)
* \[ ] Standard cure: 150°C / 1 hour, ramp 2°C/min

**Day 4: Extended post-cure**

* \[ ] All bonded subassemblies: 150°C / 24 hours in air oven
* \[ ] Cool slowly to room temperature

**Day 5-7: Vacuum bake (CRITICAL)**

* \[ ] All subassemblies in vacuum oven: 100-120°C / 48-72 hours @ 10⁻⁵ Torr
* \[ ] RGA monitoring (if available): Verify <10⁻¹⁴ Torr·L/s background
* \[ ] If no RGA: Complete full 72-hour bake minimum

**Day 7: Post-bake treatment**

* \[ ] Cool to room temperature in vacuum
* \[ ] Vent with dry nitrogen (not room air)
* \[ ] Encapsulate piezos with Al foil + Kapton tape
* \[ ] Handle only with powder-free gloves

#### Integration Phase (Week 3)

**Day 1-2: Mechanical assembly**

* \[ ] Assemble cavity frame with cleaned hardware
* \[ ] Install piezo-mirror subassemblies
* \[ ] Install crystals in ovens (handle with tweezers, never touch with fingers)
* \[ ] Connect thermistors (verify resistance values)
* \[ ] Route cables (PTFE/Kapton only, >20 cm from crystals)

**Day 3-4: Optical alignment**

* \[ ] Align cavities at room temperature (crystals not yet heated)
* \[ ] Verify mode-matching
* \[ ] Test piezo response (check for mechanical resonances)

**Day 5-7: Thermal commissioning**

* \[ ] Gradually ramp oven temperatures (2°C/min)
* \[ ] LBO: 25°C → 94°C over 2 hours
* \[ ] BBO: 25°C → 50°C over 1 hour
* \[ ] Monitor cavity lock stability during warmup
* \[ ] Optimize phase-matching angles

#### Operation Phase (Week 4+)

**Day 1: Power ramp-up**

* \[ ] Start at 10% IR power (200 mW)
* \[ ] Step up: 200 → 500 → 1000 → 1500 → 1800 mW in 20% increments
* \[ ] Wait 5 minutes at each power level
* \[ ] Monitor: Temperature, green output, UV output
* \[ ] Lock cavity with polarization servo

**Day 2-7: Performance verification**

* \[ ] Measure and record:
  * IR input power: \_\_\_\_\_ W
  * Green output power: \_\_\_\_\_ W (efficiency: \_\_\_\_%)
  * UV output power: \_\_\_\_\_ mW (efficiency: \_\_\_\_%)
  * Cavity lock bandwidth: \_\_\_\_\_ kHz
  * Long-term power stability (1 hour): \_\_\_\_\_ % RMS

**Ongoing: Contamination monitoring**

* \[ ] Daily: Log UV power (create trend plot)
* \[ ] Weekly: Visual inspection of BBO (look for surface haze)
* \[ ] Monthly: Detailed performance characterization
* \[ ] Establish cleaning cycle when power drops >10%

***

### Part 4: Performance Expectations and Monitoring

#### Expected BBO/LBO Lifetime by Scenario

| Contamination Control Level                | Estimated Hours to 10% Power Loss | Cleaning Interval | Research Viability             |
| ------------------------------------------ | --------------------------------- | ----------------- | ------------------------------ |
| **None** (standard lab assembly)           | 50-100 hours                      | Every 1-2 weeks   | ❌ Not viable                   |
| **Partial** (cleaned but not baked)        | 300-500 hours                     | Every 1-2 months  | ⚠️ Short-term experiments only |
| **Good** (cleaned + baked adhesives)       | 1,000-2,000 hours                 | Every 3-6 months  | ✅ Adequate for most research   |
| **Excellent** (full protocol, no N₂ purge) | 3,000-5,000 hours                 | Every 6-12 months | ✅ Publication-quality          |
| **Optimal** (full protocol + N₂ purge)     | 8,000-15,000 hours                | >1 year           | ✅ Commercial-grade             |

**Conversion factors:**

* 1,000 hours = 42 days of continuous operation
* 1,000 hours = 6 months at 40 hours/week (typical lab use)

#### Early Warning Signs of Contamination

**Monitor these parameters weekly:**

1.  **UV output power** (most sensitive indicator)

    ```
    Trend: Plot power vs. cumulative hours
    Normal: <0.5% drop per 100 hours
    Warning: 0.5-1% drop per 100 hours
    Critical: >1% drop per 100 hours → Inspect BBO immediately
    ```
2.  **Phase-matching temperature** (indicates crystal absorption change)

    ```
    Normal: Stable within ±0.1°C week-to-week
    Warning: Drift >0.2°C per week
    Mechanism: Surface contamination changes optical path length
    ```
3.  **Cavity lock error signal RMS** (indicates scatter)

    ```
    Normal: Stable baseline noise
    Warning: 2× increase in noise floor
    Mechanism: Surface scatter from contamination or particulates
    ```
4.  **Visual inspection under microscope** (definitive test)

    ```
    Frequency: Monthly, or when power drops >5%
    Method:
      1. Remove BBO from oven (handle only with tweezers)
      2. Inspect entrance/exit surfaces at 50-100× magnification
      3. Look for: haze, discoloration (yellow/brown), particulates
      4. Compare to photos taken when crystal was new
    Interpretation:
      - Pristine surfaces → Contamination not the issue
      - Slight haze → Early stage, cleaning recommended
      - Yellow/brown tint → Photochemical products, cleaning mandatory
      - Opaque spots → Severe contamination, may be irreversible
    ```

#### BBO/LBO Cleaning Protocol

**When to clean:** Power dropped >10% AND visual inspection shows surface contamination

**WARNING:** Cleaning is invasive and carries risk of damage. Only clean when necessary.

```
MATERIALS REQUIRED:
- First Contact polymer cleaner (Photonic Cleaning Technologies)
- Acetone (semiconductor grade)
- Methanol (HPLC grade)
- Isopropanol (99.5%+)
- Cotton swabs (optical-grade, lint-free)
- Nitrogen gas (filtered, oil-free)
- Laminar flow hood or clean bench
- Powder-free nitrile gloves

PROTOCOL:

Step 1: First Contact Treatment (removes particulates)
  1. Remove crystal from oven (cool to room temperature first)
  2. Apply First Contact polymer in clean environment
  3. Let cure 10-30 minutes (forms rubbery film)
  4. Peel off film slowly (takes particulates with it)
  5. Inspect under microscope

Step 2: Solvent Cleaning (removes organic films)
  ONLY if First Contact insufficient
  
  1. Dampen cotton swab with methanol
  2. Gently wipe surface in one direction (do NOT scrub)
  3. Repeat with fresh swab until no residue visible on swab
  4. Rinse: Flood surface with isopropanol, dry with N₂
  5. Final rinse: Isopropanol, dry with N₂
  6. Inspect under microscope
  
  If contamination persists: Try acetone (more aggressive)
  WARNING: Acetone may damage AR coatings on some crystals

Step 3: Reinstallation
  1. Handle crystal only by edges with tweezers
  2. Reinstall in oven within 15 minutes (prevent moisture absorption on BBO)
  3. Re-align cavity and optimize phase-matching

Step 4: Verification
  1. Measure power vs. input curve (should recover to near-original)
  2. If recovery <80%: Contamination may have created permanent damage
  3. Log cleaning date and results

CRITICAL WARNINGS:
- BBO is hygroscopic: Work quickly in <30% RH environment
- Do NOT use ultrasonic cleaning on coated crystals (damages coatings)
- Do NOT use abrasive materials (lens paper is too rough)
- If crystal has AR coating, verify coating intact after cleaning (reflection check)
```

**Expected results:**

* Well-executed cleaning: 80-95% power recovery
* Repeated cleanings: Diminishing returns (cumulative damage to coatings)
* After 3-5 cleaning cycles: Consider replacing crystal

***

### Part 5: Cost-Benefit Analysis

#### Investment vs. Lifetime Extension

**Scenario:** Building one frequency-doubling cavity (532 nm → 280 nm)

| Expense Category                | Standard Build        | Clean Build             | Premium Build                   |
| ------------------------------- | --------------------- | ----------------------- | ------------------------------- |
| **Material choices**            |                       |                         |                                 |
| Translation stages              | €600 (black anodized) | €650 (natural anodized) | €1,200 (stainless)              |
| Piezos (×2)                     | €300 (standard)       | €300 (standard + bake)  | €900 (UHV-grade)                |
| Cables                          | €50 (PVC)             | €150 (PTFE)             | €150 (PTFE)                     |
| Adhesives                       | €50 (any epoxy)       | €100 (EPO-TEK + bake)   | €100 (EPO-TEK + bake)           |
| **Processing**                  |                       |                         |                                 |
| Ultrasonic cleaning             | €0 (skip)             | €50 (solvents)          | €50 (solvents)                  |
| Thermal baking                  | €0 (skip)             | €100 (oven time)        | €100 (oven time)                |
| Vacuum baking                   | €0 (skip)             | €200 (vacuum time)      | €200 (vacuum time)              |
| N₂ purge system                 | €0 (none)             | €0 (none)               | €800 (flow control + enclosure) |
| **Labor time**                  | 1 week                | 3 weeks                 | 3 weeks                         |
| **TOTAL COST**                  | **€1,000**            | **€1,550**              | **€3,400**                      |
|                                 |                       |                         |                                 |
| **Performance**                 |                       |                         |                                 |
| BBO lifetime                    | 100 hours             | 3,000 hours             | 10,000 hours                    |
| Cleaning frequency              | Weekly                | Every 6 months          | Yearly                          |
| Suitable for                    | Demos only            | Publication work        | Long-term stability             |
| **Effective cost per 1000 hrs** | **€10,000**           | **€520**                | **€340**                        |

**Key insight:** Clean build is 20× more cost-effective than standard build when amortized over crystal lifetime.

**BBO crystal replacement cost:** €500-2,000 (depending on size, coating, supplier)

#### Return on Investment Calculation

**Example: PhD project requiring 2,000 hours of stable UV operation**

**Standard build approach:**

```
Initial build: €1,000
BBO crystals: 20 replacements × €800 = €16,000
Cleaning/alignment labor: 20 cycles × 8 hours × €30/hr = €4,800
Lost experimental time: 20 × 2 days = 40 days (opportunity cost)
TOTAL: €21,800 + 40 days downtime
```

**Clean build approach:**

```
Initial build: €1,550
BBO cleaning: 1 × €0 (in-house) = €0
Cleaning/alignment labor: 1 cycle × 4 hours × €30/hr = €120
Lost experimental time: 0.5 days
TOTAL: €1,670 + 0.5 days downtime

SAVINGS: €20,130 + 39.5 days
```

**ROI: 1,300% on the additional €550 investment in contamination control**

***

### Part 6: Troubleshooting Guide

#### Problem: UV power degrading rapidly (<100 hours to 50% loss)

**Diagnostic steps:**

1. **Check cavity lock:** Is lock stable?
   * If lock unstable: Problem may be thermal drift, not contamination
   * If lock stable: Proceed to step 2
2. **Measure green power (559 nm):** Is green also degrading?
   * If green stable but UV dropping: Problem is BBO contamination
   * If both dropping: Check LBO or cavity alignment
3. **Visual inspection of BBO:**
   * Remove BBO, inspect at 50× magnification
   * Look for haze, discoloration, or particulates
   * If contamination visible: Proceed to cleaning protocol
   * If surfaces pristine: Problem is elsewhere (crystal damage, coating degradation)
4. **Identify contamination source:**
   * When was last time cavity was opened? New component added?
   * Check for black anodized parts (most likely culprit)
   * Check for new cables (PVC insulation?)
   * Check for lubricants, adhesive labels, cleaning residues

**Solutions by contamination source:**

| Source Identified         | Immediate Action                               | Long-Term Solution            |
| ------------------------- | ---------------------------------------------- | ----------------------------- |
| **Black anodized stage**  | Remove or bake at 200°C × 48 hr                | Replace with natural anodized |
| **Machining oil residue** | Ultrasonic clean + bake all parts              | Implement cleaning protocol   |
| **Unbaked adhesive**      | Continue operation, expect further degradation | Rebuild with baked adhesives  |
| **PVC cable**             | Replace with PTFE                              | Cable management upgrade      |
| **Piezo outgassing**      | Encapsulate with Al foil                       | Use UHV-grade piezos          |

#### Problem: BBO lifetime shorter than expected despite following protocol

**Possible explanations:**

1. **Incomplete baking:**
   * Verify vacuum bake reached <10⁻⁵ Torr (not just "vacuum pump on")
   * Verify temperature reached 100-120°C (use external thermocouple, don't trust oven display)
   * Verify bake duration was 48+ hours (not shortened)
2. **Contamination during assembly:**
   * Were parts handled with bare hands after cleaning?
   * Was assembly done in dusty environment?
   * Were any non-protocol materials used (lubricants, labels)?
3. **Environmental factors:**
   * High room humidity (>60% RH): Hygroscopic BBO absorbs moisture faster
   * Dusty environment: Particulates accumulate on surfaces
   * Volatile organics in room air: Cleaning solvents, 3D printer fumes, etc.
4. **Crystal quality issues:**
   * Some BBO crystals have intrinsic defects (inclusions, imperfect polish)
   * Cheap crystals may have inferior AR coatings that degrade faster
   * Verify crystal source: Buy from reputable suppliers (Eksma, Castech, Red Optronics)

#### Problem: BBO surface looks clean but power still degraded

**Alternative failure modes (NOT contamination):**

1. **Crystal damage:**
   * Gray track or dark spot in beam path: Photodarkening or laser-induced damage
   * Cause: Excessive power density (>1 MW/cm² peak) or UV absorption
   * Solution: Replace crystal, reduce power or increase beam size
2. **Coating degradation:**
   * AR coating may have delaminated or oxidized
   * Check: Measure reflection at entrance face (should be <0.5%)
   * Solution: Recoat or replace crystal
3. **Thermal lensing:**
   * Crystal temperature drifting: Phase-matching bandwidth exceeded
   * Check: Monitor phase-matching temperature over time
   * Solution: Improve oven temperature stability, increase oven thermal mass
4. **Mechanical misalignment:**
   * Cavity mirrors have shifted due to thermal expansion or vibration
   * Check: Re-optimize cavity alignment, measure finesse
   * Solution: Improve mechanical stability, use more rigid mounts

***

### Part 7: Advanced Topics

#### Nitrogen Purge System Design

**When to implement:** For >5,000 hour target lifetime or critical applications

**Benefits:**

* Eliminates moisture (prevents hygroscopic contamination on BBO)
* Continuously flushes outgassed organics (reduces deposition rate)
* Reduces O₂ partial pressure (slows photochemical polymerization)
* Creates controlled, reproducible atmosphere

**Simple design:**

```
[N₂ cylinder] → [Regulator (2-3 bar)] → [Flow controller (0.1-1 L/min)]
    ↓
[Particle filter (0.2 μm)] → [Moisture trap (Drierite)]
    ↓
[Inlet port (cavity enclosure top)]
    ↓
[Slight positive pressure (~1 mbar above ambient)]
    ↓
[Exhaust port (cavity enclosure bottom)]
```

**Components:**

* N₂ cylinder: Standard 50 L cylinder (€80-120, lasts 2-6 months)
* Flow controller: Mass flow controller (MFC) or needle valve + rotameter (€100-500)
* Particle filter: 0.2 μm inline filter (€50)
* Moisture trap: Drierite or molecular sieve (€30, regenerate monthly)
* Enclosure: Acrylic or polycarbonate box with gasketed ports (€200-500)

**Flow rate:**

* 0.1 L/min: Gentle purge, 1-2 air changes per hour
* 0.5 L/min: Moderate, 5-10 air changes per hour (recommended)
* 1.0 L/min: Aggressive, 10-20 air changes per hour (may disturb cavity stability)

**Operational cost:**

* N₂ consumption: 0.5 L/min × 60 min/hr × 730 hr/month = 21,900 L/month = 15 m³/month
* Cost: 15 m³ × €3/m³ = €45/month

**Performance impact:**

* BBO lifetime extension: 1.5-3× improvement over clean build without purge
* Total system cost: +€800 (setup) + €45/month (operation)

#### Residual Gas Analysis (RGA) Monitoring

**Purpose:** Real-time monitoring of outgassing species

**When practical:** If you have access to RGA (ion trap labs often do)

**Implementation:**

1. Connect small vacuum line to cavity enclosure (1/4" tube, <1 L/min flow)
2. Pump line with turbomolecular pump to <10⁻⁶ Torr
3. Insert RGA head in line
4. Monitor mass spectrum (m/z = 1-100 amu)

**What to look for:**

* **m/z = 18 (H₂O):** Moisture outgassing
* **m/z = 28, 44 (CO, CO₂):** Organic decomposition
* **m/z = 43, 57, 71 (CₓHᵧ fragments):** Hydrocarbon outgassing (oils, epoxy)
* **m/z = 73, 147, 207, 281 (siloxanes):** Silicone rubber outgassing

**Acceptance criteria:**

* After full bake-out: Background pressure <10⁻⁷ Torr
* Hydrocarbon peaks <1% of total signal
* If criteria not met: Extend bake time or identify unclean component

***

### Part 8: Quick Reference Tables

#### Material Selection Cheat Sheet

| Component            | ❌ AVOID                      | ⚠️ ACCEPTABLE (with treatment) | ✅ RECOMMENDED                     |
| -------------------- | ---------------------------- | ------------------------------ | --------------------------------- |
| **Structural metal** | Black anodized Al            | Bare Al (Alodine coated)       | Natural hard anodized Al          |
|                      |                              |                                | Electropolished SS 304/316        |
| **Insulator**        | Nylon, polycarbonate         | PTFE (baked)                   | PEEK, Macor, alumina              |
| **Cable insulation** | PVC                          | Silicone (pre-baked)           | PTFE, Kapton                      |
| **Adhesive**         | General epoxy, cyanoacrylate | EPO-TEK (standard cure)        | EPO-TEK (extended bake)           |
|                      |                              |                                | Ceramabond 571 (inorganic)        |
| **Piezo**            | Unknown/cheap                | Standard grade (pre-baked)     | UHV-specified grade               |
| **Seals**            | Viton, Buna-N o-rings        | Kalrez (pre-baked, remote)     | Metal C-rings, Conflat Cu gaskets |

#### Outgassing Rate Reference

| Material/Treatment                    | Outgassing @ 25°C (Torr·L/s/cm²) | Time to Monolayer on BBO @ 50°C |
| ------------------------------------- | -------------------------------- | ------------------------------- |
| **Black anodized Al (untreated)**     | 10⁻⁶ to 10⁻⁵                     | 10-50 hours                     |
| **Machining oil residue**             | 10⁻⁶                             | 50 hours                        |
| **PVC cable insulation**              | 10⁻⁵                             | 10 hours                        |
| **Standard piezo stack**              | 10⁻⁷                             | 500 hours                       |
| **EPO-TEK (standard cure)**           | 10⁻⁷                             | 500 hours                       |
| **Natural anodized Al**               | 10⁻⁹                             | 5,000 hours                     |
| **Cleaned + baked metal**             | 10⁻⁹                             | 5,000 hours                     |
| **EPO-TEK (extended bake)**           | 10⁻¹²                            | 5,000,000 hours                 |
| **UHV-grade piezo**                   | 10⁻⁹                             | 5,000 hours                     |
| **PEEK, PTFE**                        | 10⁻⁹ to 10⁻⁸                     | 1,000-5,000 hours               |
| **Stainless steel (electropolished)** | 10⁻¹⁰                            | 50,000 hours                    |

#### Cleaning Protocol Checklist

**Use this checklist for every cavity build:**

* \[ ] All metal parts identified and inventoried
* \[ ] Black anodized parts replaced or baked at 200°C
* \[ ] Ultrasonic cleaning: Acetone → IPA → DI water
* \[ ] Thermal bake: 200°C / 2-4 hours
* \[ ] Dragon's breath test passed
* \[ ] Adhesive bonds: Standard cure completed
* \[ ] Extended post-cure: 150°C / 24 hours
* \[ ] Vacuum bake: 100-120°C / 48-72 hours @ <10⁻⁵ Torr
* \[ ] RGA verified (if available): <10⁻¹⁴ Torr·L/s
* \[ ] Piezos pre-baked (if standard grade)
* \[ ] Piezos encapsulated with Al foil
* \[ ] All cables PTFE or Kapton (no PVC)
* \[ ] No elastomer seals within 20 cm of crystals
* \[ ] Assembly in clean environment (ISO 6-7)
* \[ ] Handled only with powder-free gloves
* \[ ] Documentation complete (photos, batch numbers, test data)

***

### Part 9: Learning Resources and References

#### Foundational Reading

**For BSc students (Introduction level):**

\[1] Hecht, _Optics_, 5th ed., Chapter 6: "Optical materials"\
\- Basics of optical coatings, absorption, scatter

\[2] Demtröder, _Laser Spectroscopy_, Vol. 1, Chapter 5: "Nonlinear optics"\
\- SHG theory, phase matching, conversion efficiency

\[3] Saleh & Teich, _Fundamentals of Photonics_, Chapter 19: "Nonlinear optics"\
\- Clear mathematical treatment of frequency doubling

**For MSc students (Applications level):**

\[4] Boyd, _Nonlinear Optics_, 3rd ed., Chapter 2: "Wave-equation description of nonlinear optical interactions"\
\- Rigorous treatment of SHG in crystals

\[5] Siegman, _Lasers_, Chapter 27: "Nonlinear optical frequency conversion"\
\- Cavity-enhanced SHG, impedance matching

\[6] Friedenauer et al., "High power all solid state laser system near 280 nm," _Appl. Phys. B_ 84, 371 (2006)\
\- **The paper uploaded by user** - Real-world example of LBO + BBO system

**For PhD students (Research level):**

\[7] Paschotta et al., "Bright squeezed light from a singly resonant frequency doubler," _Phys. Rev. Lett._ 72, 3807 (1994)\
\- Advanced cavity design, noise considerations

\[8] Polzik & Kimble, "Frequency doubling with KNbO₃ in an external cavity," _Opt. Lett._ 16, 1400 (1991)\
\- Classic paper on external cavity SHG

#### Contamination and Materials Science

\[9] Rettner et al., "Contamination of optical surfaces by organic vapors," _Appl. Opt._ 26, 3402 (1987)\
\- Foundational study of organic contamination mechanisms

\[10] LIGO Technical Note T1500200, "Materials for use in LIGO vacuum systems"\
\- Gold standard for UHV materials selection (available: dcc.ligo.org)

\[11] NASA Reference Publication 1124, "Outgassing data for selecting spacecraft materials"\
\- Database of outgassing rates (available: outgassing.nasa.gov)

\[12] Agrawal & Menzel, "Contamination of grazing incidence optics," _Opt. Eng._ 32, 1593 (1993)\
\- Photochemical contamination in UV systems

#### Surface Preparation and Cleaning

\[13] Palik & Henck, "Effect of cleaning procedures on damage threshold of molybdenum mirrors," _Appl. Opt._ 23, 3796 (1984)\
\- Demonstrates importance of proper cleaning

\[14] Gwo et al., "Ultra-precision bonding for gravitational wave detectors," _Class. Quantum Grav._ 20, 853 (2003)\
\- Hydroxide-catalysis bonding (related to precision assembly)

#### Product Data Sheets (Essential References)

\[15] EPO-TEK 353ND Technical Data Sheet\
\- Available: www.epotek.com/docs/en/Datasheet/353ND.pdf

\[16] EPO-TEK H74 Technical Data Sheet\
\- Available: www.epotek.com/docs/en/Datasheet/H74.pdf

\[17] Stycast 2850FT Technical Data Sheet\
\- Available: Henkel technical support or distributors

\[18] PI Ceramic, "Piezo actuators for UHV applications," Application Note\
\- Available: www.piceramic.com (search "UHV")

#### Online Resources

\[19] SNLO Software (Sandia National Labs)\
\- Free nonlinear optics calculator: as-photonics.com/snlo

\[20] LIDT Database (Laser-Induced Damage Threshold)\
\- boulder.nist.gov/div815/lidt

\[21] Thorlabs Educational Resources\
\- www.thorlabs.com/tutorials.cfm (see "Optical Materials" and "Nonlinear Crystals")

***

### Appendix A: Procurement Guide

#### Recommended Vendors

**Optomechanical Hardware (Clean Options):**

* **Thorlabs** (www.thorlabs.com): Natural anodized option available on request
* **Newport/MKS** (www.newport.com): Stainless steel stages, custom anodization
* **OptoSigma** (www.optosigma.com): "Clean room grade" specification available

**Adhesives:**

* **Epoxy Technology** (www.epotek.com): Direct manufacturer of EPO-TEK products
* **Henkel/Loctite** (distributor: Ellsworth Adhesives): Stycast products
* **Thorlabs**: Repackages EPO-TEK in smaller quantities (convenient for labs)

**Piezos:**

* **PI Ceramic** (www.piceramic.com): PICMA® series, UHV options available
* **Noliac** (www.noliac.com): NAC2000 series, UHV-compatible models
* **Thorlabs**: PA series (standard), custom UHV builds on request

**Nonlinear Crystals:**

* **Eksma Optics** (www.eksmaoptics.com): High-quality LBO, BBO, custom coatings
* **Castech** (www.castech.com): Reliable Chinese supplier, good price/performance
* **Red Optronics** (www.redoptronics.com): Premium crystals, tight specifications

**Cables and Wire:**

* **Omega Engineering** (www.omega.com): Kapton-insulated thermocouple wire
* **Alpha Wire** (www.alphawire.com): FIT-221 PTFE hook-up wire
* **Lakeshore Cryotronics** (www.lakeshore.com): Low-outgassing Quadlead wire

**Cleaning Supplies:**

* **First Contact** (www.photoniccleaning.com): Polymer cleaner for optics
* **Texwipe** (www.texwipe.com): Cleanroom wipes, swabs
* **VWR/Sigma-Aldrich**: Semiconductor-grade solvents

#### Example Bill of Materials (One Cavity)

| Item                                               | Part Number | Vendor           | Qty   | Unit Price | Total      |
| -------------------------------------------------- | ----------- | ---------------- | ----- | ---------- | ---------- |
| Translation stage (natural anodized)               | Custom      | Thorlabs         | 2     | €325       | €650       |
| Piezo stack (UHV-grade, 5×5×10 mm)                 | NAC2124-UHV | Noliac           | 2     | €450       | €900       |
| EPO-TEK 353ND (10:1 syringe, 10 mL)                | 353ND-10ML  | Epoxy Technology | 1     | €80        | €80        |
| EPO-TEK H74 (3 oz kit)                             | H74-3OZ     | Epoxy Technology | 1     | €120       | €120       |
| PTFE wire (26 AWG, 10 m)                           | FIT-221     | Alpha Wire       | 10    | €8/m       | €80        |
| Cleaning solvents (acetone, IPA, MeOH)             | Various     | VWR              | 1 set | €100       | €100       |
| PEEK rod (Ø25 mm × 100 mm)                         | Various     | McMaster-Carr    | 1     | €40        | €40        |
| Al foil + Kapton tape                              | Various     | Lab supply       | 1 set | €20        | €20        |
| Misc hardware (screws, washers, springs - cleaned) | SS 304      | McMaster-Carr    | 1 set | €50        | €50        |
| **TOTAL MATERIALS**                                |             |                  |       |            | **€2,040** |

**Not included:** Crystals (€1,000-3,000), mirrors (€500-2,000), labor, facilities

***

### Appendix B: Institutional Knowledge Documentation Template

**To be filled out for each new cavity built in your lab:**

```
==============================================================
FREQUENCY DOUBLING CAVITY BUILD LOG
==============================================================

CAVITY ID: [e.g., BBO-SHG-280nm-01]
BUILDER: [Name]
START DATE: [YYYY-MM-DD]
COMPLETION DATE: [YYYY-MM-DD]
PURPOSE: [e.g., "Mg+ ion cooling and detection laser"]

--------------------------------------------------------------
MATERIALS RECORD
--------------------------------------------------------------

Translation Stages:
- Vendor: [Thorlabs / Newport / Custom]
- Model: [Part number]
- Surface finish: [Natural anodized / Stainless / Black anodized*]
- Cleaning: [Yes / No] Date: [YYYY-MM-DD]
- Baking: [Yes / No] Temp: [°C] Duration: [hours]
- *If black anodized: Justification: _______________

Piezos:
- Vendor: [PI / Noliac / Thorlabs]
- Model: [Part number]
- Grade: [Standard / UHV-specified]
- Pre-bake: [Yes / No] Temp: [°C] Duration: [hours]
- Capacitance before bake: [nF]
- Capacitance after bake: [nF]
- % Change: [Should be <5%]

Adhesives:
- Mirror-to-piezo: [EPO-TEK 353ND / Other: ___]
  Batch: [___] Expiry: [YYYY-MM]
- Thermistor-to-oven: [EPO-TEK H74 / Other: ___]
  Batch: [___] Expiry: [YYYY-MM]
- Standard cure: 150°C / 1 hour - Completed: [YYYY-MM-DD]
- Extended post-cure: 150°C / 24 hr - Completed: [YYYY-MM-DD]
- Vacuum bake: [Temp] / [Duration] @ [Pressure] - Completed: [YYYY-MM-DD]

Cables:
- Piezo drive: [PTFE / Kapton / Silicone / PVC*]
- Thermistor: [PTFE / Kapton / Silicone / PVC*]
- Power: [PTFE / Kapton / Silicone / PVC*]
- *If PVC: Justification: _______________

Other Materials:
- PEEK insulators: [Location, dimensions]
- O-rings/seals: [Type, location - should be NONE within 20 cm BBO]
- Labels/markings: [All adhesive labels removed? Yes / No]

--------------------------------------------------------------
CLEANING PROTOCOL COMPLIANCE
--------------------------------------------------------------

- [ ] All metal parts disassembled
- [ ] Ultrasonic cleaning: Acetone → IPA → DI water (15 min each)
- [ ] Thermal bake: 200°C / [___] hours
- [ ] Dragon's breath test: [Pass / Fail]
- [ ] Cleaning date: [YYYY-MM-DD]
- [ ] Handled with powder-free gloves: [Yes / No]
- [ ] Assembled in clean environment: [Yes / No]

--------------------------------------------------------------
INITIAL PERFORMANCE
--------------------------------------------------------------

Date of first light: [YYYY-MM-DD]

IR input power: [___] W
Green output (559 nm): [___] W (Efficiency: [___]%)
UV output (280 nm): [___] mW (Efficiency: [___]%)

Cavity parameters:
- LBO temperature: [___] °C
- BBO temperature: [___] °C
- Finesse (estimated): [___]
- Lock bandwidth: [___] kHz

--------------------------------------------------------------
LONG-TERM MONITORING
--------------------------------------------------------------

Power log (update weekly):

| Date | Hours | IR (W) | Green (W) | UV (mW) | Notes |
|------|-------|--------|-----------|---------|-------|
| | 0 | | | | Initial |
| | 100 | | | | |
| | 500 | | | | |
| | 1000 | | | | |
| | 2000 | | | | |

BBO cleaning log:

| Date | Hours | Reason | Method | Recovery (%) |
|------|-------|--------|--------|--------------|
| | | | | |

--------------------------------------------------------------
LESSONS LEARNED
--------------------------------------------------------------

What worked well:


What didn't work:


Recommendations for next build:


--------------------------------------------------------------
PHOTOS
--------------------------------------------------------------

- [ ] Before assembly: All components laid out
- [ ] During assembly: Critical joints (mirror-piezo, etc.)
- [ ] Completed assembly: Full cavity
- [ ] BBO surface (new): Microscope image at 50×
- [ ] BBO surface (after 1000 hrs): Microscope image for comparison

Files stored at: [_______________]

==============================================================
```

***

### Summary: Three-Level Decision Framework

#### Level 1: Minimum Viable (For Short-Term Experiments, <500 hours)

**Materials:**

* Natural anodized or bare aluminum (no black)
* Standard-grade piezos with pre-bake
* EPO-TEK adhesives with standard cure only
* PTFE cables (no PVC)

**Process:**

* Ultrasonic cleaning + 200°C bake of all metal parts
* Standard adhesive cure (150°C / 1 hour)
* Basic assembly hygiene (gloves, clean bench)

**Expected outcome:** 500-1,000 hours BBO lifetime, cleaning every 3-6 months

**Investment:** +€200-300 over "standard lab build"

#### Level 2: Publication-Quality (For PhD Projects, 2,000-5,000 hours)

**Materials:**

* Natural hard anodized aluminum or stainless steel
* UHV-grade piezos OR standard with full treatment
* EPO-TEK adhesives with NASA outgassing certification
* PTFE or Kapton cables throughout

**Process:**

* Full cleaning protocol (ultrasonic + thermal bake)
* Extended post-cure (150°C / 24 hours)
* **Vacuum bake (100-120°C / 48-72 hours)**
* Piezo encapsulation with Al foil
* Assembly in ISO 6-7 environment

**Expected outcome:** 3,000-5,000 hours BBO lifetime, cleaning every 6-12 months

**Investment:** +€800-1,200 over standard build

#### Level 3: Commercial-Grade (For Shared Facilities, >10,000 hours)

**Materials:**

* Electropolished stainless steel throughout
* UHV-specified piezos only
* Inorganic adhesives where possible (Ceramabond for thermistor)
* Kapton-insulated wire, metal-body connectors

**Process:**

* All Level 2 protocols
* **Nitrogen purge system**
* HEPA-filtered enclosure
* RGA verification of outgassing
* Regular contamination monitoring

**Expected outcome:** 8,000-15,000 hours BBO lifetime, cleaning >1 year

**Investment:** +€2,500-4,000 over standard build

***

### Final Guidance for Students

**Before you start building:**

1. Read this entire guide (2-3 hours)
2. Read the Friedenauer et al. paper \[6] for context
3. Identify contamination sources in your planned design
4. Calculate cost-benefit for your experimental timeline
5. Get approval from supervisor for materials budget

**During construction:** 6. Follow protocols exactly (no shortcuts) 7. Document everything (photos, batch numbers, dates) 8. Test components before assembly (capacitance, outgassing if possible) 9. Allow 3 weeks for proper assembly (including bake times)

**After first light:** 10. Monitor power daily for first 100 hours (establish baseline) 11. Weekly monitoring afterward (plot trends) 12. Visual inspection of BBO after 500 hours (establish cleaning schedule) 13. Document performance in lab notebook (future reference)

**Remember:**

* Contamination is cumulative and progressive
* Early detection is much easier than late recovery
* Materials choices matter 10× more than you initially think
* Time invested in proper preparation pays back 100× in experimental stability

**Good luck with your frequency doubling cavity!**

***

**Document version:** 0.1\
**Last updated:** 2025-12-03\
**Maintainer:** U.Warring\
**Feedback:** Please contribute improvements via lab wiki or email
