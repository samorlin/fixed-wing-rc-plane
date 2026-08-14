# 🛩️ Daedalus — 1.0m 3D-Printed RC Trainer Aircraft

> An aero-structurally optimized, 3D-printed $1.0\text{ m}$ wingspan RC trainer designed for low-cost manufacturing, structural resilience, and easy electronics integration.

![Daedalus Aircraft Banner](docs/images/cad_full_assembly.jpg)

---

## 📄 Main Design Report

For the complete aero-structural analysis, Euler-Bernoulli beam calculations, VSPAERO pitching moment simulations, and stability verification, read the full PDF report:

👉 **[Download / View the Full Design Report (PDF)](Daedalus_Aero_Structural_Design_Report.pdf)**

---

## 📌 Key Aircraft Specifications

| Parameter | Value | Design Rationale |
| :--- | :--- | :--- |
| **Wingspan ($b$)** | $1000\text{ mm}$ ($1.0\text{ m}$) | Compact for 3D printing & transport; smooth flight characteristics |
| **All-Up Weight (AUW)** | $\approx 1.0\text{ kg}$ | Target weight for 3D-printed trainer class |
| **Aerofoil** | **NACA 2412** | Gentle stall, high lift-to-drag ratio, clean trailing edge |
| **Design Load Factor** | **3g maneuver limit** | Accommodates pull-up stresses ($29.43\text{ N}$ total lift) |
| **Main Spar Sizing** | $6\text{ mm}$ OD / $4\text{ mm}$ ID Carbon Tube | Single continuous $750\text{ mm}$ tube ($\text{Safety Factor} \approx 6.3$) |
| **Wing Incidence** | $+3.8^\circ$ relative to body | Eliminates body drag during level cruise |
| **Thrust Offset** | $2^\circ$ Right Yaw / $2^\circ$ Down Pitch | Neutralizes motor torque, P-factor, and throttle pitch-up |
| **Airframe Material** | PLA ($\approx 800\text{ g}$ print mass) | Printed on standard FDM 3D printer (Elegoo PLA spool) |

---

## 🛠️ Key CAD & Engineering Features

* **High-Wing Pendulum Stability:** Designed with zero dihedral for simple, un-jointed spar pass-through; stability is recovered via natural high-wing pendulum dynamic.
* **Integrated Servo Recesses:** Molded underslung bays for 9g metal-gear servos (flushed into the skin to minimize drag) with internal wire routing tunnels.
* **Modular Motor Firewall & Cowl:** Heavy-duty forward firewall matching XXD 2212 motor bolt patterns with a removable protective nose cowl for easy servicing.
* **Optimized Ground Geometry:** Main axle shifted forward of CG to prevent nose-over; tail wheel mounted at extreme aft cone to transfer landing shocks into bulkheads.

---

## 📊 Aerodynamic & Stability Gallery

<p align="center">
  <img src="docs/images/cad_ground_stance.jpg" width="45%" alt="Ground Stance Alignment" />
  <img src="docs/images/vspaero_cm_alpha.png" width="45%" alt="Pitching Moment Stability Curve" />
</p>

*Left: CAD ground alignment maintaining a $+10^\circ$ nose-up attitude. Right: VSPAERO $C_m$ vs $\alpha$ curve showing static pitch stability at $10\%$ static margin.*

---

## 🛒 Bill of Materials (BOM) & Electronics

Total estimated new project outlay: **~£85.00**

| Component | Specification | Sourcing Notes |
| :--- | :--- | :--- |
| **Motor** | XXD A2212 1000KV Brushless | 3S LiPo optimized |
| **ESC** | Hobbywing Skywalker 40A V2 | 5V 3A SBEC prevents receiver brownout |
| **Servos** | 4x MG90D Metal-Gear Digital Servos | Brass/aluminum gears for crash resistance |
| **Receiver** | HappyModel EPW6 6CH PWM ELRS | Native EdgeTX compatibility |
| **Battery** | 3S 11.1V LiPo Pack | Sourced via UK local stock (Hobby RC) |
| **Propeller** | APC 9x6 Precision Electric | Dynamic thrust match |
| **Transmitter** | RadioMaster Pocket | Existing inventory (EdgeTX) |
| **Landing Gear** | $2.0\text{ mm}$ Aluminum + $65\text{ mm}$ Wheels | Sourced via AliExpress |

---

## 🚀 Future Post-Maiden Software Tuning

Following standard 1-to-1 baseline flight validation (Maiden Flight), software optimizations will be enabled in EdgeTX:

1. **Electronic Aileron Differential:** Limiting downward aileron deflection relative to upward deflection to suppress adverse yaw.
2. **Flaperon Mixing:** Enabling a transmitter switch to lower both ailerons by $10^\circ - 15^\circ$ as landing flaps.
3. **Sub-Trim Alignment:** Digital offset tuning to ensure level cruise glide paths.
