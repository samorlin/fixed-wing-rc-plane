# Daedalus 1.0m Fixed-Wing RC Aircraft (Aero-Structural Design)

![Isometric CAD View](daedulusrender2.png) <!-- Embed Fig 9/10 from your report -->

## Executive Summary
Complete design, structural sizing, aerodynamic simulation, and manufacturing layout for a 1.0 kg, 1.0 m wingspan 3D-printed RC trainer aircraft. 

* 📄 **[Read Full Engineering Report (PDF)](Aero_Structural_Design_Report.pdf)**
* 📐 **CAD Files:** Available in `/cad` (Fusion / STEP format)
* 📊 **Aero Simulation:** OpenVSP files available in `/aero`

## Key Engineering Specs
| Parameter | Value | Rationale |
| :--- | :--- | :--- |
| **All-Up Weight** | 1.0 kg | Target mass for 3D-printed trainer class |
| **Design Load Factor** | 3.0g ($29.43 \text{ N}$) | Maximum pull-up maneuver stress limit |
| **Airfoil / Wingspan** | NACA 2412 / $1000 \text{ mm}$ | High L/D, gentle stall, high-wing pendulum stability |
| **Static Margin** | 10% ($X_{\text{cg}} = 31\%$ MAC) | Stable hands-off pitch trim ($\text{d}C_m/\text{d}\alpha < 0$) |

## Highlights & Performance Images
### 1. Built-in $+3.8^\circ$ Wing Incidence
![Incidence Comparison](./images/incidence_comparison.png) <!-- Embed Figure 3 from report -->
*Designed to keep the fuselage level at $0^\circ$ pitch during $15\text{ m/s}$ cruise, eliminating parasite body drag.*

### 2. Structural Spar Verification
![Euler Bernoulli Load Diagram](./images/spar_loading.png) <!-- Embed Figure 1 from report -->
*Euler-Bernoulli beam sizing on $6\text{mm}$ OD / $4\text{mm}$ ID carbon tube yielding $\sigma_{\text{max}} = 190.4 \text{ MPa}$ ($SF = 6.3$).*
