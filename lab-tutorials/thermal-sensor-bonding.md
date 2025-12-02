---
description: Lab Guide & Certification Protocol
icon: lightbulb-exclamation-on
---

# Thermal Sensor Bonding

{% hint style="info" %}
author: U._Warring_\
&#xNAN;_&#x61;ffiliation: Institute of Physics, University of Freiburg_\
&#xNAN;_&#x76;ersion: 0.8_\
&#xNAN;_&#x6C;ast\_updated: 2025-11-28_\
&#xNAN;_&#x72;eview\_status: Internal laboratory documentation; not externally peer-reviewed_\
&#xNAN;_&#x6C;icense: CC BY-SA 4.0_
{% endhint %}

### 1. Overview

For attaching mm-scale thermistors to copper or other substrates under 0–200 °C conditions, three adhesive classes cover many recurring scenarios (under ambient conditions):

1. **Industrial thermal epoxies** — for external components, housings, and non-optical mounts
2. **Optics-grade, low-outgassing epoxies** — for internal laser/SHG environments
3. **High-temperature sensor-grade epoxies** — for occasional >150 °C or structural bonding

> ⚠️ **Laser Safety Reminder:** All adhesive work inside laser cavities must only begin once the laser is powered down, locked out, and beam paths secured. Wavelength-specific eyewear is mandatory whenever the enclosure is open.\
> See: [Bonding of Optical Components in High-Power Laser Beam Paths](https://claude.ai/chat/bonding-of-optical-components-in-high-power-laser-beam-paths) for cavity-specific protocols.

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

| Adhesive                   | Thermal Cond. (k) | Service Temp      | Strength / Properties                                | Best Use                                          | Ref                                                                   |
| -------------------------- | ----------------- | ----------------- | ---------------------------------------------------- | ------------------------------------------------- | --------------------------------------------------------------------- |
| **MG Chemicals 8329TCS**   | 0.67 W/m·K        | –55 to 130 °C     | Lap shear \~7.7 MPa (Al)\<br>Moderate rigidity       | Low-waste, occasional external thermistor bonding | [¹](https://claude.ai/chat/49682465-322d-43ea-857a-5d533d7097ad#ref1) |
| **WEICON Easy-Mix HT 250** | 0.74 W/m·K        | –60 to 200 °C     | Shore D > 90 (Very High)\<br>Structural standard     | Structural, batch bonding on external parts       | [²](https://claude.ai/chat/49682465-322d-43ea-857a-5d533d7097ad#ref2) |
| **OMEGABOND 200**          | 1.52 W/m·K        | Up to 260 °C      | High Shear (\~18.6 MPa)\<br>Requires Heat Cure       | High-T external mounting (reserve option)         | [³](https://claude.ai/chat/49682465-322d-43ea-857a-5d533d7097ad#ref3) |
| **Stycast 2850FT**         | 1.04 W/m·K        | –65 to 130/155 °C | CTE matched to Copper\<br>Low Outgassing (ASTM E595) | Internal SHG/Laser Cavity bonding near optics     | [⁴](https://claude.ai/chat/49682465-322d-43ea-857a-5d533d7097ad#ref4) |
| **EPO-TEK H74**            | 1.89 W/m·K        | > 200 °C          | High Shear\<br>Optical Grade                         | Alternative for vacuum/cavity work                | [⁵](https://claude.ai/chat/49682465-322d-43ea-857a-5d533d7097ad#ref5) |

#### Reference Documentation

\<a name="ref1">\</a>**\[1] MG Chemicals 8329TCS Technical Data Sheet**\
https://www.mgchemicals.com/products/adhesives/thermal-conductive-epoxies/8329tcs-thermally-conductive-epoxy

\<a name="ref2">\</a>**\[2] WEICON Easy-Mix HT 250 Technical Data Sheet**\
https://www.weicon.de/en/products/adhesives-and-sealants/structural-adhesives/easy-mix-ht-250

\<a name="ref3">\</a>**\[3] OMEGABOND 200 Technical Specifications**\
https://www.omega.com/en-us/industrial-heaters-and-heating-elements/p/OB-200

\<a name="ref4">\</a>**\[4] Stycast 2850FT Technical Data Sheet (Henkel/Loctite)**\
https://dm.henkel-dam.com/is/content/henkel/stycast-2850ft-blue-with-catalyst-9-en-tds\
&#xNAN;_&#x4E;ote:_ Properties depend on catalyst choice (Cat 9 vs Cat 11) — see Appendix B

\<a name="ref5">\</a>**\[5] EPO-TEK H74 Technical Data Sheet (Epoxy Technology)**\
https://www.epotek.com/site/administrator/components/com\_products/assets/files/Style\_Uploads/H74.pdf

#### Standards Referenced

* **ASTM E595:** Standard Test Method for Total Mass Loss and Collected Volatile Condensable Materials from Outgassing in a Vacuum Environment\
  https://www.astm.org/e0595-15r21.html

***

### 3. Use-Case Mapping

#### A. Internal to Laser/SHG Cavity (Critical Zone)

**Use:** Stycast 2850FT (Cat 9 or 11) **or** EPO-TEK H74\
**Why:** Low outgassing (ASTM E595 compliant), CTE match protects optics from stress\
**See also:** [Bonding of Optical Components in High-Power Laser Beam Paths](https://claude.ai/chat/bonding-of-optical-components-in-high-power-laser-beam-paths) for surface preparation protocols specific to cavity environments

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
   **See:** [Cleaning Components After Manufacturing](https://claude.ai/chat/cleaning-components-after-manufacturing) for detailed solvent protocols
3. **Dry:** Ensure full evaporation before applying glue (≥5 min air dry)

#### 4.3 Bake-Out (Optics-Grade Only)

**Temp/Time:** 80–100 °C for 4–12 hours\
**Atmosphere:** Vacuum (preferred) or flowing dry N₂\
**Goal:** Drive off volatiles before the part enters the laser cavity

**Verification:** Visual inspection under magnification (20×) for micro-cracks or haze after cooldown

#### 4.4 Strain Relief

**Crucial:** Always anchor the cable jacket separately from the sensor head using a cable clamp or secondary glue dot. Do not rely on the thermistor bead to hold the cable weight.

#### 4.5 Substrate Compatibility

| Substrate Type            | Adhesion Quality       | Special Notes                                            | Ref                                                                   |
| ------------------------- | ---------------------- | -------------------------------------------------------- | --------------------------------------------------------------------- |
| **Metals** (Cu, Al, SS)   | Excellent              | Bond Aluminium within 1h of abrasion (oxide reformation) | [⁶](https://claude.ai/chat/49682465-322d-43ea-857a-5d533d7097ad#ref6) |
| **Ceramics** (Al₂O₃, AlN) | Good (Stycast matched) | **Safety:** Dust mask mandatory during abrasion          | [⁴](https://claude.ai/chat/49682465-322d-43ea-857a-5d533d7097ad#ref4) |
| **Glass**                 | Good                   | Low CTE mismatch with Stycast                            | [⁴](https://claude.ai/chat/49682465-322d-43ea-857a-5d533d7097ad#ref4) |
| **Plastics** (FR-4, G-10) | Good                   | **Safety:** Mask required for fiberglass dust            | -                                                                     |
| **Difficult** (PTFE, PP)  | Poor                   | Require primers (avoid if possible)                      | -                                                                     |

\<a name="ref6">\</a>**\[6] Surface Preparation Guidelines**\
Parker, T. C., et al. "Surface preparation for structural adhesive bonding of aluminum alloys." _International Journal of Adhesion and Adhesives_ 15.4 (1995): 233-238.

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

| Item                      | Purpose                           | Supplier Link                                                            |
| ------------------------- | --------------------------------- | ------------------------------------------------------------------------ |
| MG 8329TCS                | Drawer essential (occasional use) | [Link](https://claude.ai/chat/49682465-322d-43ea-857a-5d533d7097ad#ref1) |
| WEICON HT 250             | Structural standard               | [Link](https://claude.ai/chat/49682465-322d-43ea-857a-5d533d7097ad#ref2) |
| Stycast 2850FT + Cat 9/11 | Cavity standard                   | [Link](https://claude.ai/chat/49682465-322d-43ea-857a-5d533d7097ad#ref4) |
| Precision Scale (0.01g)   | Catalyst weighing                 | Generic lab supplier                                                     |
| Heat-Resistant Gloves     | Bake-out handling                 | Generic lab supplier                                                     |
| Scotch-Brite Pads (7447)  | Surface prep                      | 3M                                                                       |
| Loupe (10–20×)            | Bond inspection                   | Edmund Optics                                                            |

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

**Source:** [Stycast 2850FT TDS](https://claude.ai/chat/49682465-322d-43ea-857a-5d533d7097ad#ref4)

***

### Safety Data Sheets (SDS)

All users must review the following before handling:

1. **Stycast 2850FT (Base + Catalyst 9/11):**\
   Available from Henkel/Loctite (request from supplier or institutional EHS)
2. **EPO-TEK H74:**\
   https://www.epotek.com (SDS section)
3. **WEICON Easy-Mix HT 250:**\
   https://www.weicon.de/en/downloads/safety-data-sheets
4. **MG Chemicals 8329TCS:**\
   https://www.mgchemicals.com/downloads/sds

***

### Related Tutorials

* [**Bonding of Optical Components in High-Power Laser Beam Paths**](https://claude.ai/chat/bonding-of-optical-components-in-high-power-laser-beam-paths)\
  &#xNAN;_&#x45;ssential reading for cavity work — covers low-scatter bonding, surface contamination control, and beam-path safety protocols_
* [**Cleaning Components After Manufacturing**](https://claude.ai/chat/cleaning-components-after-manufacturing)\
  &#xNAN;_&#x53;olvent selection, ultrasonic cleaning, and particulate control for sensor preparation_

***

**Document Version:** 2.0 (Enhanced with References)\
**Last Updated:** December 2025\
**Maintained by:** Experimental Quantum & Atomic Physics Group, University of Freiburg

***
