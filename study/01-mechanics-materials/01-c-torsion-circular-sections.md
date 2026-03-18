# Torsion of Circular Sections

**Subject area:** Mechanics of Materials  
**Design standard / primary reference:** Hibbeler, *Mechanics of Materials*, 10th ed. — Ch. 5; Beer & Johnston, *Mechanics of Materials*, 7th ed. — Ch. 3  
**Depth level:** Undergraduate — accessible  
**Estimated study time:** 70 minutes

---

## 1. Introduction & Motivation

When you tighten a bolt with a wrench, twist the output shaft of an electric motor, or turn a steering column, you are applying **torque** — a moment about the longitudinal axis of a member. Unlike bending (which causes one face to extend and the opposite face to shorten), torsion causes the cross-section to rotate relative to adjacent cross-sections, generating **shear stresses** throughout the material.

Understanding torsion is essential for designing **power transmission shafts** (the most common application), drill bits, helical springs, and torsional frames. The formula $\tau = Tc/J$ is to torsion what $\sigma = P/A$ is to axial loading — the fundamental relationship between the applied action (torque $T$), the geometry ($J$, $c$), and the resulting stress ($\tau$).

Circular cross-sections (solid or hollow) are by far the most common torsional members because they are the only cross-section for which the elementary torsion theory gives exact results. For non-circular sections, different (more complex) theories apply — those are introduced in graduate-level elasticity courses.

---

## 2. Key Concepts & Definitions

| Term | Symbol | Definition |
|------|--------|------------|
| Torque | $T$ | Internal twisting moment about the longitudinal axis of a member |
| Polar moment of inertia | $J$ | Geometric property of cross-section: $J = \int_A \rho^2 \, dA$ |
| Shear stress due to torsion | $\tau$ | Shear stress at radial distance $\rho$ from the centroidal axis |
| Maximum shear stress | $\tau_{max}$ | Shear stress at the outer radius $c$ |
| Angle of twist | $\phi$ | Rotation of one end relative to the other (radians) |
| Shear modulus | $G$ | Ratio of shear stress to shear strain |
| Torsional rigidity | $GJ$ | Resistance of a shaft to twisting deformation |
| Power | $P_{power}$ | Rate of energy transmission; related to torque by $P_{power} = T\omega$ |
| Angular velocity | $\omega$ | Rotational speed in rad/s; $\omega = 2\pi f$ where $f$ is in Hz (rev/s) |
| Outer radius | $c$ | Distance from centroid to outermost fiber (solid shaft: $c = d/2$) |

---

## 3. Governing Equations

| Equation | Description | Source |
|----------|-------------|--------|
| $\tau = T\rho / J$ | Shear stress at radius $\rho$ from center | Hibbeler, 10th ed. Eq. 5-7 |
| $\tau_{max} = Tc / J$ | Maximum shear stress (at outer radius $c$) | Hibbeler, 10th ed. Eq. 5-8 |
| $\phi = TL / GJ$ | Angle of twist (radians) | Hibbeler, 10th ed. Eq. 5-15 |
| $J = \pi c^4 / 2$ | Polar moment of inertia, solid circular section | Hibbeler, 10th ed. Eq. 5-2a |
| $J = \pi (c_o^4 - c_i^4) / 2$ | Polar moment of inertia, hollow circular section | Hibbeler, 10th ed. Eq. 5-2b |
| $P_{power} = T\omega$ | Power-torque relation ($\omega$ in rad/s) | Hibbeler, 10th ed. §5.3 |

$$
\tau = \frac{T \rho}{J}, \qquad \tau_{max} = \frac{T c}{J}
$$

$$
\phi = \frac{TL}{GJ}
$$

**Variable legend:**

| Symbol | Description | SI Units | US Customary Units |
|--------|-------------|----------|--------------------|
| $T$ | Internal torque (right-hand rule: CCW positive looking from +x) | N·m; kN·m | lb·in; kip·in |
| $\rho$ | Radial distance from centroid to point of interest | mm; m | in |
| $c$ | Outer radius of cross-section | mm; m | in |
| $c_o$, $c_i$ | Outer and inner radii of hollow section | mm | in |
| $J$ | Polar moment of inertia | mm⁴; m⁴ | in⁴ |
| $\tau$ | Shear stress | MPa | ksi; psi |
| $\phi$ | Angle of twist | rad | rad |
| $L$ | Length of shaft | mm; m | in |
| $G$ | Shear modulus | MPa; GPa | ksi |
| $\omega$ | Angular velocity | rad/s | rad/s |
| $P_{power}$ | Power | W; kW | hp (1 hp = 745.7 W) |

---

## 4. Derivation

### 4-1. Kinematics of Torsion (Shear Strain Distribution)

**Step 1:** Assume the following for a circular bar of length $L$ twisted by $\phi$:
- **Plane sections remain plane** after twisting (no warping — true only for circular cross-sections).
- **Radii remain straight** — no circumferential distortion.
- **Small deformations** (valid for $\phi$ in radians, $\phi \ll 1$).

**Step 2:** Consider a surface element on the outer surface of the shaft. When the shaft twists by angle $\phi$, a longitudinal line on the surface becomes a helix. The angle of distortion at the surface (shear strain) is:
$$\gamma_{max} = \frac{c \, \phi}{L}$$

**Step 3:** At an interior radius $\rho$, the arc length of distortion scales linearly with $\rho$:
$$\gamma = \frac{\rho \, \phi}{L} = \frac{\rho}{c} \, \gamma_{max}$$

Shear strain varies **linearly** from zero at the center to a maximum at the outer surface.

### 4-2. Shear Stress Distribution (via Hooke's Law)

**Step 4:** Apply Hooke's Law for shear: $\tau = G\gamma$:
$$\tau = G \frac{\rho \, \phi}{L}$$

Shear stress also varies **linearly** with $\rho$.

### 4-3. Polar Moment of Inertia and the Torsion Formula

**Step 5:** The internal torque on a cross-section is the resultant of all shear stress contributions. Each element $dA$ at radius $\rho$ contributes a tangential force $dF = \tau \, dA$ and a moment $dT = \rho \, dF = \rho \, \tau \, dA$:
$$T = \int_A \rho \, \tau \, dA = \int_A \rho \left( G \frac{\rho \, \phi}{L} \right) dA = \frac{G\phi}{L} \int_A \rho^2 \, dA$$

**Step 6:** Define polar moment of inertia $J = \int_A \rho^2 \, dA$. Then:
$$T = \frac{GJ\phi}{L} \quad \Rightarrow \quad \phi = \frac{TL}{GJ}$$

**Step 7:** Substitute back into the expression for $\tau$:
$$\tau = G \frac{\rho \phi}{L} = G \frac{\rho}{L} \cdot \frac{TL}{GJ} = \frac{T\rho}{J}$$

This is the **torsion formula**. At the outer surface $\rho = c$:
$$\tau_{max} = \frac{Tc}{J}$$

### 4-4. Polar Moments of Inertia

For a **solid circle** of radius $c$:
$$J = \int_0^c \rho^2 \cdot 2\pi\rho \, d\rho = \frac{\pi c^4}{2} = \frac{\pi d^4}{32}$$

For a **hollow circle** (outer radius $c_o$, inner radius $c_i$):
$$J = \frac{\pi}{2}(c_o^4 - c_i^4) = \frac{\pi}{32}(d_o^4 - d_i^4)$$

### 4-5. Power Transmission

A shaft rotating at $\omega$ rad/s transmitting torque $T$ delivers power:
$$P_{power} = T \cdot \omega \quad [\text{W} = \text{N·m} \cdot \text{rad/s}]$$

In practice, $\omega = 2\pi n / 60$ where $n$ is rotational speed in RPM. Solving for $T$:
$$T = \frac{P_{power}}{\omega} = \frac{60 \, P_{power}}{2\pi n}$$

---

## 5. Design / Application Procedure

1. **Find the internal torque $T$** along the shaft using a **torque diagram** (analogous to shear/moment diagrams). Use the right-hand rule for sign convention. Section the shaft and apply equilibrium to find $T$ at each critical section.
2. **Identify the critical section** (largest $T$ or smallest $J$).
3. **Compute $J$** for the cross-section (solid or hollow circle).
4. **Compute shear stress:** $\tau_{max} = Tc/J$. Check against allowable shear stress: $\tau_{allow} = \tau_y / FS \approx 0.577 \sigma_y / FS$ (von Mises) or $0.5 \sigma_y / FS$ (Tresca).
5. **Design for angle of twist if required:** $\phi = TL/GJ$. Service limit is typically $\phi_{allow} = 1°/m$ to $2°/m$ for power shafts, or as specified by the application.
6. **For power transmission shafts:** Calculate torque from $T = P_{power}/\omega$, then use steps 3–5.
7. **For hollow vs. solid comparison:** A hollow shaft of the same $J$ and length is lighter but more expensive. The ratio of inner to outer diameter $k = c_i/c_o$ governs the weight saving.

---

## 6. Worked Example

**Problem:** A solid steel shaft (G = 80 GPa, $\tau_{allow} = 70$ MPa) transmits 75 kW at 120 RPM. Determine: (a) the required minimum diameter to satisfy the stress limit, and (b) the angle of twist over a 2-meter length for the selected diameter.

**Given:**
- $P_{power} = 75$ kW $= 75{,}000$ W
- $n = 120$ RPM → $\omega = 2\pi(120)/60 = 4\pi$ rad/s $= 12.566$ rad/s
- $G = 80$ GPa $= 80{,}000$ MPa
- $\tau_{allow} = 70$ MPa
- $L = 2$ m $= 2000$ mm

**Required:** Minimum diameter $d$; angle of twist $\phi$.

**Solution:**

1. **Torque from power:**
$$T = \frac{P_{power}}{\omega} = \frac{75{,}000 \text{ W}}{12.566 \text{ rad/s}} = 5{,}968 \text{ N·m} = 5.968 \times 10^6 \text{ N·mm}$$

2. **Required diameter from stress condition:**
$$\tau_{max} = \frac{Tc}{J} = \frac{T \cdot (d/2)}{\pi d^4/32} = \frac{16T}{\pi d^3} \leq \tau_{allow}$$
$$d^3 \geq \frac{16T}{\pi \, \tau_{allow}} = \frac{16 \times 5.968 \times 10^6}{\pi \times 70} = 433{,}700 \text{ mm}^3$$
$$d \geq \sqrt[3]{433{,}700} = 75.6 \text{ mm}$$

Round up to nearest standard size: **use $d = 80$ mm**.

3. **Recalculate $J$ and $\tau_{max}$ for $d = 80$ mm:**
$$J = \frac{\pi (80)^4}{32} = \frac{\pi \times 40{,}960{,}000}{32} = 4.021 \times 10^6 \text{ mm}^4$$
$$\tau_{max} = \frac{Tc}{J} = \frac{5.968 \times 10^6 \times 40}{4.021 \times 10^6} = 59.4 \text{ MPa} < 70 \text{ MPa} \quad \checkmark$$

4. **Angle of twist:**
$$\phi = \frac{TL}{GJ} = \frac{5.968 \times 10^6 \text{ N·mm} \times 2000 \text{ mm}}{80{,}000 \text{ MPa} \times 4.021 \times 10^6 \text{ mm}^4}$$
$$\phi = \frac{1.194 \times 10^{10}}{3.217 \times 10^{11}} = 0.03711 \text{ rad} = 2.13°$$

**Result:** Use a solid shaft with $d = 80$ mm. Maximum shear stress: 59.4 MPa (< 70 MPa allowed). Angle of twist over 2 m: 2.13°.

---

## 7. Common Mistakes & Pitfalls

- **Mistake 1 — Confusing $J$ (polar moment) with $I$ (second moment of area for bending):** For a solid circle, $J = \pi d^4/32$ and $I_x = \pi d^4/64$. Note $J = 2I$ for a circle. Using $I$ instead of $J$ in the torsion formula gives a stress twice as large.
- **Mistake 2 — Forgetting that $\tau = Tc/J$ gives the magnitude only at the outer fiber:** The stress at an interior point is $\tau = T\rho/J$, not $Tc/J$.
- **Mistake 3 — Not converting RPM to rad/s** when using $P_{power} = T\omega$: The formula requires $\omega$ in rad/s, not RPM.
- **Mistake 4 — Applying torsion theory to non-circular sections:** For rectangular, I-shaped, or thin-walled open sections, the shear stress and angle of twist formulas are completely different (Saint-Venant torsion theory). The $\tau = Tc/J$ formula is **only valid for circular sections**.
- **Mistake 5 — Wrong sign/direction of angle of twist in multi-segment shafts:** Define one positive direction of rotation (e.g., right-hand rule about the positive $x$-axis) and apply it consistently for all segments.

---

## 8. Connections to Other Topics

- **Topic 01-A (Stress & Strain):** Torsion produces pure shear stress. The shear stress $\tau$ from torsion will later be combined with bending stresses on Mohr's circle (Topic 01-H) to find principal stresses.
- **Topic 01-H (Mohr's Circle):** A shaft in torsion has a state of pure shear at its surface ($\sigma = 0$, $\tau = Tc/J$). Mohr's circle for this state has a 45° principal stress equal to $\tau_{max}$ — this explains why brittle materials fail in torsion along a 45° helix.
- **Topic 01-I (Failure Criteria):** The shear yield stress $\tau_y = \sigma_y/2$ (Tresca) or $\tau_y = \sigma_y/\sqrt{3}$ (von Mises) is the limit.
- **Topic 04 (Matrix Analysis):** The torsional stiffness $k_T = GJ/L$ of a bar element appears in the 3D frame stiffness matrix alongside the axial stiffness $AE/L$.
- **Topic 09 (Stability):** Open thin-walled sections resist torsion poorly — warping torsion and the shear center concept arise here, which directly inflences lateral-torsional buckling (AISC 360 §F).

---

## 9. Further Reading

| Resource | Where to look |
|----------|--------------|
| Hibbeler, *Mechanics of Materials*, 10th ed. | Chapter 5: Torsion |
| Beer, Johnston & DeWolf, *Mechanics of Materials*, 7th ed. | Chapter 3: Torsion |
| Gere & Goodno, *Mechanics of Materials*, 9th ed. | Chapter 3: Torsion |
| Timoshenko & Goodier, *Theory of Elasticity*, 3rd ed. | Chapter 10: Torsion (non-circular sections — graduate level) |

---

## 10. Quick Self-Check

- [ ] I can state $\tau_{max} = Tc/J$ and $\phi = TL/GJ$, define every symbol, and explain the assumptions.
- [ ] I can compute $J$ for both solid and hollow circular cross-sections.
- [ ] I understand why shear stress is zero at the center and maximum at the outer surface.
- [ ] I can draw a torque diagram for a shaft with multiple applied torques.
- [ ] I can convert power (kW or hp) and RPM to torque, then design a shaft.

---

*Created by Structural Engineering Tutor • 2026-03-14*
