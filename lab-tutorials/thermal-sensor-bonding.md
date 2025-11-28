---
description: Lab Guide & Certification Protocol
---

# Thermal Sensor Bonding

{% hint style="info" %}
author: U._Warring_\
&#xNAN;_&#x61;ffiliation: Institute of Physics, University of Freiburg_\
&#xNAN;_&#x76;ersion: 0.7_\
&#xNAN;_&#x6C;ast\_updated: 2025-11-28_\
&#xNAN;_&#x72;eview\_status: Internal laboratory documentation; not externally peer-reviewed_\
&#xNAN;_&#x6C;icense: CC BY-SA 4.0_
{% endhint %}

### 1. Overview

For attaching for example mm-scale thermistors to copper or other substrates under 0–200 °C conditions, three adhesive classes cover all recurring scenarios:

1. Industrial thermal epoxies — for external components, housings, and non-optical mounts.
2. Optics-grade, low-outgassing epoxies — for _internal_ laser/SHG environments.
3. High-temperature sensor-grade epoxies — for occasional >150 °C or structural bonding.

> ⚠️ Laser Safety Reminder: All adhesive work inside laser cavities must only begin once the laser is powered down, locked out, and beam paths secured. Wavelength-specific eyewear is mandatory whenever the enclosure is open.

***

### 1.5 Safety Prerequisites & Protocols

A. Training & Authorization

* Completed institutional chemical safety training.
* Cavity Work: LSO authorization + laser safety certification required.
* Must review SDS for: Stycast 2850FT, EPO-TEK H74, WEICON HT 250, MG 8329TCS.

B. Personal Protective Equipment (PPE)

* Standard (All Jobs): Nitrile gloves (6 mil+), Safety glasses (side shields), Lab coat.
* Cavity/Laser Work: Laser safety eyewear (OD 7+ @ 1064 nm / OD 5+ @ 532 nm).
* Thermal Work: Heat-resistant gloves (for bake-out handling >60°C).

C. Ventilation & Surface Prep

* Mixing: Fume hood required for Stycast/EPO-TEK (amine hardeners).
* Abrasion Hazards:
  * _Metals:_ Standard ventilation.
  * _Ceramics/Glass/FR-4:_ N95/P95 dust mask or respirator required. Perform in fume hood or use wet-abrasion to control hazardous dust (silica/glass fibers).
  * _AlN (Aluminum Nitride):_ hydrolysis risk (ammonia release) if abrading aged AlN in humid air—use fume hood.

D. Chemical & Thermal Response

* Skin Contact: Wash with soap + water ≥15 min. NEVER use solvents on skin.
* Thermal: Cool-down time ≥30 min before touching with thermal gloves; ≥60 min for bare hands.
* Waste: Uncured epoxy $$\to$$ Chemical Waste. Solvents $$\to$$ Organic Waste.

***

### 2. Adhesive Comparison Table

| **Adhesive**   | **Thermal Cond. (k)**  | **Service Temp**     | **Strength / Properties**                                            | **Best Use**                                        |
| -------------- | ---------------------- | -------------------- | -------------------------------------------------------------------- | --------------------------------------------------- |
| MG 8329TCS     | $$\approx 1.4$$ W/m·K  | $$-40 \dots 150$$ °C | <p>Lap shear ~7.7 MPa (Al)</p><p><br></p><p>Moderate rigidity</p>    | Low-waste, occasional external thermistor bonding.  |
| WEICON HT 250  | $$\approx 1.4$$ W/m·K  | $$-50 \dots 200$$ °C | <p>Shore D > 90 (Very High)</p><p><br></p><p>Structural standard</p> | Structural, batch bonding on external copper parts. |
| OMEGABOND 200  | $$\approx 0.8$$ W/m·K  | Up to 260 °C         | <p>High Shear (~18.6 MPa)</p><p><br></p><p>Requires Heat Cure</p>    | High-T external mounting (reserve option).          |
| Stycast 2850FT | $$\approx 1.25$$ W/m·K | $$130 \dots 155$$ °C | <p>CTE matched to Copper</p><p><br></p><p>Low Outgassing</p>         | Internal SHG/Laser Cavity bonding near optics.      |
| EPO-TEK H74    | $$\approx 1.3$$ W/m·K  | > 200 °C             | <p>High Shear</p><p><br></p><p>Optical Grade</p>                     | Alternative for vacuum/cavity work.                 |

***

### 3. Use-Case Mapping

A. Internal to Laser/SHG Cavity (Critical Zone)

* Use: Stycast 2850FT (Cat 9 or 11) _or_ EPO-TEK H74.
* Why: Low outgassing (ASTM E595), CTE match protects optics from stress.

B. External Copper Parts (Structural)

* Use: WEICON Easy-Mix HT 250.
* Why: Strongest mechanical anchor, reliable to 200 °C, good shelf life.

C. Occasional / Low-Waste Jobs

* Use: MG Chemicals 8329TCS.
* Why: Minimizes waste for single-sensor jobs.

***

### 4. Application Protocol

#### 4.1 Bond Line Thickness

Target: $$< 0.1$$ mm.

* Reason: Thick epoxy layers act as a "thermal expansion jack," lifting the sensor or cracking the joint during heating.

#### 4.2 Surface Preparation

1. Abrade: Light Scotch-Brite or fine sandpaper. (_Wear mask for Ceramic/FR-4_).
2. Clean: IPA or Acetone in Fume Hood.
3. Dry: Ensure full evaporation before applying glue.

#### 4.3 Bake-Out (Optics-Grade Only)

* Temp/Time: 80–100 °C for 4–12 hours.
* Atmosphere: Vacuum (preferred) or flowing dry N₂.
* Goal: Drive off volatiles _before_ the part enters the laser cavity.

#### 4.4 Strain Relief

Crucial: Always anchor the cable jacket separately from the sensor head using a cable clamp or secondary glue dot. Do not rely on the thermistor bead to hold the cable weight.

#### 4.5 Substrate Compatibility

* Metals (Cu, Al, SS): Excellent adhesion. _Note: Bond Aluminium within 1h of abrasion._
* Ceramics (Al₂O₃, AlN) & Glass: Good match for Stycast. Safety: Dust mask mandatory during abrasion.
* Plastics (FR-4, G-10): Good adhesion. Safety: Mask required for fiberglass dust.
* Difficult: PTFE/PP require primers (avoid if possible).

***

### 5. Dry-Run Training Protocol (Mandatory)

_Every user must complete this before their first live cavity installation._

1. Dry Run A (Mixing): Practice weighing Stycast components (0.01g precision) and mixing without introducing bubbles.
2. Dry Run B (Geometry): Bond a dummy slug. Verify $$ $<0.1$ $$ mm thickness and minimal fillet.
3. Dry Run C (Bake-Out): Simulate oven loading and thermal safety (gloves/cooldown).
4. Dry Run D (Inspection): Use a loupe to check cured dummy for micro-cracks or haze.

***

### 6. Recommended Lab Stock

1. MG 8329TCS (Drawer essential).
2. WEICON HT 250 (Structural standard).
3. Stycast 2850FT (Cavity standard).

* Aux: Precision Scale (0.01g), Scrap Copper (for training), Heat-Resistant Gloves.

***

### APPENDIX A: TR-01 Certification Checklist

_Copy/Print for Lab Safety Binder_

Trainee: \_\_\_\_\_\_\_\_\_\_ | Supervisor: \_\_\_\_\_\_\_\_\_\_ | Date: \_\_\_\_\_

PHASE A: Safety & PPE

* \[ ] PPE: Glasses, Gloves, Lab Coat donned?
* \[ ] Hazards: Dust mask used for Ceramic/FR-4? Fume hood used for solvents?
* \[ ] Laser: (If applicable) Lockout and Eyewear protocol demonstrated?

PHASE B: The Mix

* \[ ] Stycast: Bulk container stirred? Ratio calculated by WEIGHT?
* \[ ] WEICON: Nozzle purged? Color uniform?

PHASE C: Application & Process

* \[ ] Prep: Surface abraded & solvent cleaned?
* \[ ] Thickness: Visual check $$<0.1$$ mm?
* \[ ] Thermal: Bake-out temp set correctly? Thermal gloves used?

SIGN-OFF

*   \[ ] Result: Dummy bond is mechanically sound, clean, and safe?

    $$\to$$ PERMISSION GRANTED FOR LIVE CAVITY WORK

***

### APPENDIX B: Stycast 2850FT Data Card

LAB STANDARD: STYCAST 2850FT (Blue/Black)

Internal Optics / High Vacuum Only

| **Parameter**      | **Catalyst 9 (General)** | **Catalyst 11 (High Spec)** |
| ------------------ | ------------------------ | --------------------------- |
| Mix Ratio (Weight) | 100 : 3.5                | 100 : 5.5                   |
| Cure               | 16h @ 25°C               | Heat Only: 2h @ 100°C       |
| Max T              | 130°C                    | 155°C                       |
| Safety             | Fume Hood Recommended    | Fume Hood REQUIRED          |

WARNING: Stir bulk resin before weighing. Filler settles!

***
