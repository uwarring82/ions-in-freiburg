---
description: Lab Guide & Certification Protocol
icon: lightbulb-exclamation-on
---

# L–Thermal Sensor Bonding

{% hint style="info" %}
author: U._Warring_\
&#xNAN;_&#x61;ffiliation: Institute of Physics, University of Freiburg_\
&#xNAN;_&#x76;ersion: 0.85_\
&#xNAN;_&#x6C;ast\_updated: 2025-12-02_\
&#xNAN;_&#x72;eview\_status: Internal laboratory documentation; not externally peer-reviewed_\
&#xNAN;_&#x6C;icense: CC BY-SA 4.0_
{% endhint %}

### 1. Overview

For attaching mm-scale thermistors to copper or other substrates under 0–200 °C conditions, three adhesive classes cover many recurring scenarios (under ambient conditions):

1. **Industrial thermal epoxies** — for external components, housings, and non-optical mounts
2. **Optics-grade, low-outgassing epoxies** — for internal laser/SHG environments
3. **High-temperature sensor-grade epoxies** — for occasional >150 °C or structural bonding

> ⚠️ **Laser Safety Reminder:** All adhesive work inside laser cavities must only begin once the laser is powered down, locked out, and beam paths secured. Wavelength-specific eyewear is mandatory whenever the enclosure is open.\
> See: [Bonding of Optical Components in High-Power Laser Beam Paths ](l-bonding-of-optical-components-in-high-power-laser-beam-paths.md)for cavity-specific protocols.

***

### 1.5 Safety Prerequisites & Protocols

#### A. Training & Authorization

* ✓ Completed institutional chemical safety training
* ✓ **Cavity Work:** LSO authorization + laser safety certification required
* ✓ Must review SDS for all adhesives listed in Section 2 (links provided below)

#### B. Personal Protective Equipment (PPE)

**Standard (All Jobs):**

* Nitrile gloves (6 mil+)
* Safety glasses (side shields)
* Lab coat

**Cavity/Laser Work:**

* Laser safety eyewear (OD 7+ @ 1064 nm / OD 5+ @ 532 nm)

**Thermal Work:**

* Heat-resistant gloves (for bake-out handling >60°C)

#### C. Ventilation & Surface Prep

**Mixing:**\
Fume hood required for Stycast/EPO-TEK (amine hardeners)

**Abrasion Hazards:**

* **Metals:** Standard ventilation
* **Ceramics/Glass/FR-4:** N95/P95 dust mask or respirator required. Perform in fume hood or use wet-abrasion to control hazardous dust (silica/glass fibers)
* **AlN (Aluminum Nitride):** Hydrolysis risk (ammonia release) if abrading aged AlN in humid air—use fume hood

#### D. Chemical & Thermal Response

* **Skin Contact:** Wash with soap + water ≥15 min. **NEVER** use solvents on skin
* **Thermal:** Cool-down time ≥30 min before touching with thermal gloves; ≥60 min for bare hands
* **Waste:**
  * Uncured epoxy → Chemical Waste
  * Solvents → Organic Waste

***

### 2. Adhesive Comparison Table

<table><thead><tr><th>Adhesive</th><th width="167.0859375">Thermal Cond. (k)</th><th width="99.36328125">Service Temp</th><th>Strength / Properties</th><th width="195.78125">Best Use</th></tr></thead><tbody><tr><td><a href="https://mgchemicals.com/products/adhesives/thermally-conductive-adhesives/high-thermal-conductivity-adhesive/"><strong>MG Chemicals 8329TCS</strong></a></td><td>0.67 W/m·K</td><td>–55 to 130 °C</td><td>Lap shear ~7.7 MPa (Al)&#x3C;br>Moderate rigidity</td><td>Low-waste, occasional external thermistor bonding</td></tr><tr><td><a href="https://www.weicon.de/easy-mix-ht-250-epoxid-klebstoff-hochtemperaturbestaendig-bis-2500c/10056568"><strong>WEICON Easy-Mix HT 250</strong></a></td><td>0.74 W/m·K</td><td>–60 to 200 °C</td><td>Shore D > 90 (Very High)&#x3C;br>Structural standard</td><td>Structural, batch bonding on external parts</td></tr><tr><td><a href="https://www.omega.de/pptst/OB-100_OB-200_OT-200.html"><strong>OMEGABOND 200</strong></a></td><td>1.52 W/m·K</td><td>Up to 260 °C</td><td>High Shear (~18.6 MPa)&#x3C;br>Requires Heat Cure</td><td>High-T external mounting (reserve option)</td></tr><tr><td><a href="https://www.henkel-adhesives.com/ch/de/produkt/potting-compounds/loctite_stycast_2850ftblk.html"><strong>Stycast 2850FT</strong></a></td><td>1.04 W/m·K</td><td>–65 to 130/155 °C</td><td>CTE matched to Copper&#x3C;br>Low Outgassing (ASTM E595)</td><td>Internal SHG/Laser Cavity bonding near optics</td></tr><tr><td><a href="https://www.epotek.com/docs/en/Datasheet/H74.pdf"><strong>EPO-TEK H74</strong></a></td><td>1.3 W/m·K</td><td>> 200 °C</td><td>High Shear&#x3C;br>Optical Grade</td><td>Alternative for vacuum/cavity work</td></tr></tbody></table>

#### Standards Referenced

* **ASTM E595:** Standard Test Method for Total Mass Loss and Collected Volatile Condensable Materials from Outgassing in a Vacuum Environment – [https://store.astm.org/e0595-15r21.html](https://store.astm.org/e0595-15r21.html)

***

### 3. Use-Case Mapping

#### A. Internal to Laser/SHG Cavity (Critical Zone)

**Use:** Stycast 2850FT (Cat 9 or 11) **or** EPO-TEK H74\
**Why:** Low outgassing (ASTM E595 compliant), CTE match protects optics from stress\
**See also:** [Bonding of Optical Components in High-Power Laser Beam Paths](l-bonding-of-optical-components-in-high-power-laser-beam-paths.md) for surface preparation protocols specific to cavity environments

#### B. External Parts (Structural)

**Use:** WEICON Easy-Mix HT 250\
**Why:** Strongest mechanical anchor, reliable to 200 °C, good shelf life

#### C. Occasional / Low-Waste Jobs

**Use:** MG Chemicals 8329TCS\
**Why:** Minimizes waste for single-sensor jobs

***

### 4. Application Protocol

#### 4.1 Bond Line Thickness

**Target:** 0.05–0.15 mm\
**Reason:** Thick epoxy layers act as a "thermal expansion jack," lifting the sensor or cracking the joint during heating.

#### 4.2 Surface Preparation

1. **Abrade:** Light Scotch-Brite or fine sandpaper (320–600 grit)\
   ⚠️ Wear mask for Ceramic/FR-4 substrates (silica dust hazard)
2. **Clean:** IPA or Acetone in Fume Hood\
   **See:** [Cleaning Components After Manufacturing](cleaning-components-after-manufacturing.md) for detailed solvent protocols
3. **Dry:** Ensure full evaporation before applying glue (≥5 min air dry)

#### 4.3 Bake-Out (Optics-Grade Only)

**Temp/Time:** 80–100 °C for 4–12 hours\
**Atmosphere:** Vacuum (preferred) or flowing dry N₂\
**Goal:** Drive off volatiles before the part enters the laser cavity

**Verification:** Visual inspection under magnification (20×) for micro-cracks or haze after cooldown

#### 4.4 Strain Relief

**Crucial:** Always anchor the cable jacket separately from the sensor head using a cable clamp or secondary glue dot. Do not rely on the thermistor bead to hold the cable weight.

#### 4.5 Substrate Compatibility

| Substrate Type            | Adhesion Quality       | Special Notes                                            |
| ------------------------- | ---------------------- | -------------------------------------------------------- |
| **Metals** (Cu, Al, SS)   | Excellent              | Bond Aluminium within 1h of abrasion (oxide reformation) |
| **Ceramics** (Al₂O₃, AlN) | Good (Stycast matched) | **Safety:** Dust mask mandatory during abrasion          |
| **Glass**                 | Good                   | Low CTE mismatch with Stycast                            |
| **Plastics** (FR-4, G-10) | Good                   | **Safety:** Mask required for fiberglass dust            |
| **Difficult** (PTFE, PP)  | Poor                   | Require primers (avoid if possible)                      |

***

### 5. Dry-Run Training Protocol (Mandatory)

Every user must complete this before their first live cavity installation.

**Dry Run A (Mixing):**\
Practice weighing Stycast components (0.01g precision) and mixing without introducing bubbles

**Dry Run B (Geometry):**\
Bond a dummy slug. Verify 0.05–0.15 mm thickness and minimal fillet

**Dry Run C (Bake-Out):**\
Simulate oven loading and thermal safety (gloves/cooldown)

**Dry Run D (Inspection):**\
Use a loupe (10–20× magnification) to check cured dummy for micro-cracks or haze

***

### 6. Recommended Lab Stock

| Item                      | Purpose                           | Supplier Link |
| ------------------------- | --------------------------------- | ------------- |
| MG 8329TCS                | Drawer essential (occasional use) |               |
| WEICON HT 250             | Structural standard               |               |
| Stycast 2850FT + Cat 9/11 | Cavity standard                   |               |
| Precision Scale (0.01g)   | Catalyst weighing                 |               |
| Heat-Resistant Gloves     | Bake-out handling                 |               |
| Scotch-Brite Pads (7447)  | Surface prep                      |               |
| Loupe (10–20×)            | Bond inspection                   |               |

***

### APPENDIX A: Certification Checklist

**Trainee:** \_\_\_\_\_\_\_\_\_\_ | **Supervisor:** \_\_\_\_\_\_\_\_\_\_ | **Date:** \_\_\_\_\_

#### PHASE A: Safety & PPE

* \[ ] PPE: Glasses, Gloves, Lab Coat donned?
* \[ ] Hazards: Dust mask used for Ceramic/FR-4? Fume hood used for solvents?
* \[ ] Laser: (If applicable) Lockout and Eyewear protocol demonstrated?
* \[ ] SDS Review: All four adhesive SDS reviewed? (Circle: Yes / No)

#### PHASE B: The Mix

* \[ ] **Stycast:** Bulk container stirred? Ratio calculated by **WEIGHT**?
* \[ ] **WEICON:** Nozzle purged? Color uniform?

#### PHASE C: Application & Process

* \[ ] **Prep:** Surface abraded (320–600 grit) & solvent cleaned?
* \[ ] **Thickness:** Visual check 0.05–0.15 mm?
* \[ ] **Thermal:** Bake-out temp set correctly? Thermal gloves used?
* \[ ] **Inspection:** Loupe check for cracks/haze?

#### SIGN-OFF

* \[ ] **Result:** Dummy bond is mechanically sound, clean, and safe?

**✓ PERMISSION GRANTED FOR LIVE CAVITY WORK**

***

### APPENDIX B: Stycast 2850FT Data Card

#### LAB STANDARD: STYCAST 2850FT (Blue/Black)

**Internal Optics / High Vacuum Only**

| Parameter                | Catalyst 9 (General)  | Catalyst 11 (High Spec) |
| ------------------------ | --------------------- | ----------------------- |
| **Mix Ratio (Weight)**   | 100 : 3.5             | 100 : 5.5               |
| **Cure**                 | 16h @ 25°C            | Heat Only: 2h @ 100°C   |
| **Max Service Temp**     | 130°C                 | 155°C                   |
| **ASTM E595 (TML/CVCM)** | Pass (<1.0% / <0.1%)  | Pass (<1.0% / <0.1%)    |
| **CTE (α)**              | \~25 ppm/K            | \~25 ppm/K              |
| **Safety**               | Fume Hood Recommended | Fume Hood **REQUIRED**  |

> ⚠️ **WARNING:** Stir bulk resin before weighing. Filler settles!

**Source:** Stycast 2850FT TDS

***

### Safety Data Sheets (SDS)

All users must review the following before handling:

1. **Stycast 2850FT (Base + Catalyst 9/11):** [**https://api.henkeldx.com/v2/mysds/SafetyDataSheetSet?Appid=%27YPSSW\_SDSUA\_EXT%27\&Matnr=%271188119%27\&Laiso=%27EN%27\&Rvlid=%27US%27\&Dmskey=%27%27\&X-Api-Key=Auy4a2t5e00VU2Ju93GSKHeybHFVjYLX**](https://api.henkeldx.com/v2/mysds/SafetyDataSheetSet?Appid=%27YPSSW_SDSUA_EXT%27\&Matnr=%271188119%27\&Laiso=%27EN%27\&Rvlid=%27US%27\&Dmskey=%27%27\&X-Api-Key=Auy4a2t5e00VU2Ju93GSKHeybHFVjYLX)
2. **EPO-TEK H74:** [**https://www.epotek.com/docs/en/SDS/H74%20SDS.pdf**](https://www.epotek.com/docs/en/SDS/H74%20SDS.pdf)
3. **WEICON Easy-Mix HT 250:** [**https://media.weicon.de/fmds/433287/dld:inline**](https://media.weicon.de/fmds/433287/dld:inline) **and** [**https://media.weicon.de/fmds/433288/dld:inline**](https://media.weicon.de/fmds/433288/dld:inline)
4. **MG Chemicals 8329TCS:** [**https://www.mgchemicals.com/downloads/msds/01%20English%20Can-USA%20SDS/sds-8329tcs-part-a.pdf**](https://www.mgchemicals.com/downloads/msds/01%20English%20Can-USA%20SDS/sds-8329tcs-part-a.pdf)

***
