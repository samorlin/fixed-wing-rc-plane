# ✈️ Project Daedalus | Fixed-Wing Trainer RC Aircraft

> **A lightweight, 3D-printable fixed-wing RC aircraft designed, analyzed, and optimized for low-cost aerodynamic performance and structural resilience.**

---

## 📌 Project Overview

**Project Daedalus** is an aerospace engineering project documenting the end-to-end aero-structural design, numerical simulation, and manufacturing layout of a 1.0 m wingspan fixed-wing trainer aircraft[cite: 1]. Built under a strict £100 budget target, the airframe combines a 3D-printed PLA structure with continuous carbon-fiber reinforcement[cite: 1].

<p align="center">
  <img src="daedulus media/daedulusrender2.png" width="800" alt="Project Daedalus CAD Assembly">
  <br>
  <em>Figure 1: Full CAD assembly view in Autodesk Fusion showing ground stance and airframe layout[cite: 1].</em>
</p>

---

## 📊 Key Aircraft Specifications

| Parameter | Value | Rationale / Notes |
| :--- | :--- | :--- |
| **All-Up Weight (AUW)** | 1.0 kg (≈ 9.81 N)[cite: 1] | Target operating weight for 3D-printed RC class[cite: 1] |
| **Wingspan ($b$)** | 1000 mm (1.0 m)[cite: 1] | Optimized for transportability and smooth visibility[cite: 1] |
| **Mean Aerodynamic Chord ($\bar{c}$)** | 150 mm[cite: 1] | Total Wing Area $S = 0.15\text{ m}^2$ (Aspect Ratio $AR = 6.67$)[cite: 1] |
| **Aerofoil Section** | NACA 2412[cite: 1] | High lift-to-drag ratio, gentle stall characteristics[cite: 1] |
| **Wing Wingform** | Tapered ($\lambda = 0.67$)[cite: 1] | Tapered from $180\text{ mm}$ root chord to $120\text{ mm}$ tip chord[cite: 1] |
| **Design Load Factor ($n$)** | $3g$ maneuver limit[cite: 1] | $29.43\text{ N}$ maximum pull-up total lift[cite: 1] |
| **Main Spar Sizing** | $6\text{ mm}$ OD / $4\text{ mm}$ ID[cite: 1] | Continuous carbon fiber tube with Safety Factor $\approx 6.3$[cite: 1] |
| **Total Build Cost** | £85.19[cite: 1] | Under the target £100 budget limit[cite: 1] |

---

## 🛠️ Key Architectural & Design Decisions

* **Zero Dihedral (Flat Wing Architecture):** Eliminates complex 3D-printed angled structural joiners at the wing root[cite: 1]. A single continuous $750\text{ mm}$ carbon tube passes directly through the fuselage[cite: 1]. Pendulum stability is maintained via high-wing mounting[cite: 1].
* **Flat Trailing Edge Reference:** Orthogonal alignment datum provides a straight reference for manufacturing and control surface mounting[cite: 1].
* **Elastic Wing Attachment:** Utilizes rubber band wing mounting to absorb ground strike impacts and prevent fuselage damage during hard landings[cite: 1].

---

## 🧮 Structural Analysis: Spar Sizing (Euler-Bernoulli Beam)

To verify that a lightweight $6\text{ mm}$ outer-diameter carbon spar withstands a $3g$ pull-up maneuver[cite: 1], bending stress ($\sigma_{\text{max}}$) was computed using Euler-Bernoulli beam theory[cite: 1]:

<p align="center">
  <img src="assets/beam_loading_fbd.png" width="600" alt="3g Pull-Up Beam Free Body Diagram">
  <br>
  <em>Figure 2: Beam loading free body diagram for a 3g maneuver load of 29.43 N total lift[cite: 1].</em>
</p>

### Stress & Safety Factor Calculation

1. **Root Bending Moment ($M_{\text{root}}$):**
   $$M_{\text{root}} = L_{\text{panel}} \cdot \bar{y} = 14.72\text{ N} \times 0.22\text{ m} = 3.24\text{ N}\cdot\text{m}$$[cite: 1]

2. **Second Moment of Area ($I$):**
   $$I = \frac{\pi}{64} \left( D_{\text{outer}}^4 - D_{\text{inner}}^4 \right) = \frac{\pi}{64} \left( 0.006^4 - 0.004^4 \right) \approx 5.105 \times 10^{-11}\text{ m}^4$$[cite: 1]

3. **Maximum Bending Stress ($\sigma_{\text{max}}$):**
   $$\sigma_{\text{max}} = \frac{M_{\text{root}} \cdot y_{\text{max}}}{I} = \frac{3.24 \times 0.003}{5.105 \times 10^{-11}} \approx 190.4\text{ MPa}$$[cite: 1]

4. **Safety Factor (SF):**
   $$\text{SF} = \frac{\sigma_{\text{ult}}}{\sigma_{\text{max}}} = \frac{1200\text{ MPa}}{190.4\text{ MPa}} \approx 6.3$$[cite: 1]

---

## 🌪️ Aerodynamic Simulation (OpenVSP / VSPAERO)

Aerodynamic evaluations were executed using Vortex Lattice Method (VLM) solvers at cruise speed $V = 15\text{ m/s}$ ($Re = 1.5 \times 10^5$)[cite: 1].

### Built-in $+3.8^\circ$ Incidence Angle
To generate the required cruise lift coefficient ($C_{L,\text{target}} = 0.475$) without pitching the fuselage upward[cite: 1]:
* **Drag Reduction:** The fuselage body sits at $\alpha \approx 0^\circ$ during level cruise, minimizing frontal parasite drag ($C_{D0}$)[cite: 1].
* **Thrust Alignment:** Keeps motor thrust parallel to flight path, eliminating power-pitch coupling[cite: 1].

<p align="center">
  <img src="assets/vspaero_lift_curve.png" width="700" alt="VSPAERO CL vs Alpha Curve">
  <br>
  <em>Figure 3: VSPAERO lift coefficient sweep showing required incidence optimization[cite: 1].</em>
</p>

### Spanwise Load Distribution & Static Stability
* **Elliptical Lift Distribution:** The $180\text{ mm} \rightarrow 120\text{ mm}$ wing taper rounds the spanwise lift curve toward an ideal elliptical distribution, minimizing induced drag ($C_{Di}$)[cite: 1].
* **Longitudinal Stability:** $X_{\text{cg}}$ set at $31\%$ MAC ($226.5\text{ mm}$ from LE)[cite: 1], achieving a $10\%$ Static Margin[cite: 1] with negative pitching moment slope ($\frac{d C_m}{d\alpha} < 0$)[cite: 1].

<p align="center">
  <img src="assets/vspaero_spanwise_lift.png" width="45%" alt="Spanwise Circulation">
  <img src="assets/vspaero_cm_alpha.png" width="45%" alt="Cm vs Alpha Stability Curve">
  <br>
  <em>Figure 4: Spanwise circulation distribution (Left)[cite: 1] and Pitching Moment ($C_m$ vs $\alpha$) curve confirming static longitudinal stability (Right)[cite: 1].</em>
</p>

---

## 📐 Detailed CAD Integration & Internal Layout

The airframe was modeled in **Autodesk Fusion** to integrate structural hardware, internal electronics, and aerodynamic shaping[cite: 1]:

<p align="center">
  <img src="assets/cad_fuselage_bay.png" width="30%" alt="Internal Bay">
  <img src="assets/cad_servo_pocket.png" width="30%" alt="Servo Bay">
  <img src="assets/cad_motor_cowl.png" width="30%" alt="Nose Cowl">
  <br>
  <em>Figure 5: Internal equipment bay (Left)[cite: 1], flush servo mounting pockets (Center)[cite: 1], and detachable motor cowl with $2^\circ$ right/down thrust offset (Right)[cite: 1].</em>
</p>

* **Internal Equipment Bay:** Central hollow housing for $3\text{S Lipo}$ battery, ESC, and receiver with sliding range for CG tuning[cite: 1].
* **Flush Servo Recesses:** Recessed pockets for $9\text{g}$ metal-gear servos to reduce aerodynamic drag[cite: 1].
* **Integrated Thrust Vector Offset:** $2^\circ$ right yaw and $2^\circ$ down pitch modeled directly into motor firewall to counter motor torque effects[cite: 1].

---

## 💵 Bill of Materials (BOM)

| Component | Description | Qty | Cost (£) |
| :--- | :--- | :--- | :--- |
| **PLA Filament** | 1.75mm Spool (In-house 3D printing) | 800 g | £11.99[cite: 1] |
| **3S LiPo Battery** | 11.1V Pack | 1 | £13.00[cite: 1] |
| **Brushless Motor** | XXD A2212 1000KV Motor | 1 | £4.40[cite: 1] |
| **ESC** | Hobbywing Skywalker 40A ESC | 1 | £13.59[cite: 1] |
| **Servos** | MG90D Metal-Gear Servos | 4 | £9.60[cite: 1] |
| **Receiver** | HappyModel EPW6 ELRS Receiver | 1 | £11.39[cite: 1] |
| **Propeller** | APC 9x6 Precision Propellers | 2-Pack | £3.06[cite: 1] |
| **Carbon Spars** | 6mm OD Carbon Fiber Tubes (500mm) | 2 | £8.69[cite: 1] |
| **Landing Gear** | Aluminum Strut + 65mm Wheels | 1 Set | £5.65[cite: 1] |
| **Tail Wheel / Hardware** | Tail Assembly & CA Hinges | 1 Set | £3.82[cite: 1] |
| **Total Outlay** | | | **£85.19**[cite: 1] |

---

## 🚀 Future Work

- [ ] Initial Maiden Flight & Manual Trim Validation[cite: 1]
- [ ] Configure Electronic Aileron Differential & Flaperon Mixing in EdgeTX[cite: 1]
- [ ] Onboard Telemetry Payload Integration (Airspeed, Altitude, Attitude sensors)[cite: 1]
