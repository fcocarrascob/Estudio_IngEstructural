# Combined Loadings

**Subject area:** Mechanics of Materials  
**Design standard / primary reference:** Hibbeler, *Mechanics of Materials*, 10th ed. — Ch. 8; Beer & Johnston, *Mechanics of Materials*, 7th ed. — Ch. 8  
**Depth level:** Undergraduate — accessible  
**Estimated study time:** 70 minutes

---

## 1. Introduction & Motivation

Real structural members rarely carry only one type of loading. A column in a multi-story building resists axial compression **and** bending from wind loads. A pipe in a chemical plant carries internal pressure **and** bending from its own weight. A shaft in a machine transmits torque **and** bends under belt tensions. In all these cases, we must determine the **combined stress state** at any point by superimposing the individual stress contributions.

The key principle is that within the **linear elastic range**, stresses from multiple load effects can be **added algebraically** at any point on the cross-section, provided all contributions are in the same direction (same type of stress: normal with normal, or shear with shear). This topic integrates everything from Topics 01-A through 01-E into a unified procedure for finding the full stress state at any critical point — which can then be analyzed with Mohr's circle (Topic 01-H) and failure criteria (Topic 01-I).

Two special and very practical cases are also covered: **thin-walled pressure vessels**, which are present in virtually every industrial plant, and the combined **axial + bending** loading, which appears in column design in both steel (AISC 360 §H) and concrete (ACI 318).

---

## 2. Key Concepts & Definitions

| Term | Symbol | Definition |
|------|--------|------------|
| Superposition of stresses | — | Algebraic addition of stresses from multiple load effects at a point (valid only in elastic range) |
| Stress element | — | Infinitesimal cube at a point; faces carry normal and shear stresses |
| Thin-walled pressure vessel | — | Vessel with $r/t > 10$; internal pressure causes membrane stresses (hoop and longitudinal) |
| Hoop (circumferential) stress | $\sigma_1$ or $\sigma_\theta$ | Stress around the circumference of a cylindrical vessel; resists bursting |
| Longitudinal (axial) stress | $\sigma_2$ or $\sigma_x$ | Stress along the axis of a cylindrical vessel |
| Spherical vessel stress | $\sigma$ | Uniform biaxial stress in a spherical pressure vessel |
| Eccentricity | $e$ | Distance from the centroid of a section to the line of action of an axial load |

---

## 3. Governing Equations

| Equation | Description | Source |
|----------|-------------|--------|
| $\sigma = P/A \pm My/I$ | Axial + bending normal stress | Hibbeler, 10th ed. §8.1 |
| $\tau = Tc/J + VQ/(Ib)$ | Torsion + transverse shear (add if directions agree) | Hibbeler, 10th ed. §8.2 |
| $\sigma_1 = \dfrac{pr}{t}$ | Hoop stress in thin-walled cylinder | Hibbeler, 10th ed. Eq. 8-1 |
| $\sigma_2 = \dfrac{pr}{2t}$ | Longitudinal stress in thin-walled cylinder | Hibbeler, 10th ed. Eq. 8-2 |
| $\sigma = \dfrac{pr}{2t}$ | Biaxial stress in thin-walled sphere | Hibbeler, 10th ed. Eq. 8-3 |

$$
\sigma = \frac{P}{A} \pm \frac{M y}{I}
$$

$$
\sigma_1 = \frac{p r}{t} \qquad \text{(hoop)}, \qquad \sigma_2 = \frac{p r}{2t} \qquad \text{(longitudinal)}
$$

**Variable legend:**

| Symbol | Description | SI Units | US Customary Units |
|--------|-------------|----------|--------------------|
| $\sigma$ | Normal stress | MPa | ksi |
| $\tau$ | Shear stress | MPa | ksi |
| $P$ | Axial force (tension +, compression −) | N; kN | lb; kip |
| $A$ | Cross-sectional area | mm² | in² |
| $M$ | Bending moment | N·mm; kN·m | kip·in |
| $y$ | Distance from neutral axis | mm | in |
| $I$ | Second moment of area | mm⁴ | in⁴ |
| $T$ | Torque | N·mm | kip·in |
| $c$ | Outer radius (torsion) | mm | in |
| $J$ | Polar moment of inertia | mm⁴ | in⁴ |
| $V$ | Shear force | N; kN | kip |
| $Q$ | First moment of area | mm³ | in³ |
| $b$ | Width at shear cut point | mm | in |
| $p$ | Internal pressure | MPa | psi; ksi |
| $r$ | Inner radius of pressure vessel (thin-walled: $\approx$ mid-surface radius) | mm | in |
| $t$ | Wall thickness | mm | in |

---

## 4. Derivation

### 4-1. Principle of Superposition for Stresses

**Condition:** The material is **linear elastic** (Hooke's Law holds), deflections are small, and the geometry does not change appreciably under load (no second-order/P-Δ effects).

**Step 1:** At any point of interest in the cross-section, identify all stress contributions:
- Axial load $P$ → normal stress $\sigma_P = P/A$ (uniform over section).
- Bending moment $M_z$ → normal stress $\sigma_M = -M_z y / I_z$ (varies with $y$).
- Torque $T$ → shear stress $\tau_T = T\rho/J$ at radius $\rho$.
- Transverse shear $V$ → shear stress $\tau_V = VQ/(Ib)$ acting vertically.

**Step 2:** Sum all **normal stress** contributions at the point:
$$\sigma_{total} = \sigma_P + \sigma_M = \frac{P}{A} - \frac{M y}{I}$$

**Step 3:** Sum all **shear stress** contributions, noting that $\tau_T$ and $\tau_V$ may act on the **same** shear stress face and be additive, or they may act on perpendicular faces (in which case they form the two shear stress components of the stress element).

**Step 4:** The resulting stress state ($\sigma$, $\tau$) at the point is then analyzed via Mohr's circle to find principal stresses (Topic 01-H).

### 4-2. Thin-Walled Cylindrical Pressure Vessel

**Step 1:** Consider a cylinder of internal radius $r$, wall thickness $t$, and internal pressure $p$. The condition "thin-walled" means $r/t \geq 10$, so the stress variation through the wall is negligible (treated as uniform).

**Step 2: Hoop stress** — pass a longitudinal cutting plane through the cylinder's diameter. The resultant force from internal pressure on a cylindrical wall segment of length $L$ is $F = p \cdot (2r \cdot L)$ (pressure × projected area). This is resisted by two cut walls: $2(t \cdot L) \cdot \sigma_1 = F$:
$$\sigma_1 = \frac{pr}{t}$$

**Step 3: Longitudinal stress** — pass a transverse cutting plane. The internal pressure force on a full circular end cap is $F = p \cdot \pi r^2$. This is resisted by the wall cross-section area $2\pi r t$:
$$\sigma_2 = \frac{p \pi r^2}{2\pi r t} = \frac{pr}{2t}$$

Note: $\sigma_1 = 2\sigma_2$ — hoop stress is always twice the longitudinal stress. This is why pipes and cylinders burst with a longitudinal split (hoop stress controls).

**Step 4: Additional stresses** — if the vessel also bends (from self-weight or external loads), or carries a torque (from piping forces), those stresses are **added** to $\sigma_1$, $\sigma_2$ at the location of interest using superposition.

### 4-3. Spherical Pressure Vessel

By symmetry, both membrane stresses in a sphere are equal:
$$\sigma = \frac{pr}{2t}$$ (same in all tangential directions)

This is why spheres are the most efficient shape for containing pressure — equal biaxial stress.

---

## 5. Design / Application Procedure

**For combined axial + bending:**

1. Find $P$ and $M$ at the critical section using equilibrium/FBD.
2. Locate the neutral axis (centroid of the section).
3. Identify critical points: usually the extreme fibers where bending stress peaks. Check where $\sigma_P$ and $\sigma_M$ **add** (same sign → highest tensile or compressive stress).
4. Compute $\sigma_{total} = P/A \pm Mc/I$ at the critical points.
5. If torque and shear are also present, compute $\tau_{total}$ at the critical points.
6. Use Mohr's circle (Topic 01-H) to find principal stresses and maximum shear stress.
7. Check against yield (Topic 01-I).

**For pressure vessels:**

1. Determine the loading: internal pressure $p$, plus any bending moments or axial loads from external sources.
2. Compute thin-wall stresses: $\sigma_1 = pr/t$, $\sigma_2 = pr/2t$.
3. Add bending/axial contributions using superposition at the critical location (where bending adds tensile stress to the hoop stress, for example).
4. Verify design code requirements (ASME Pressure Vessel Code, or appropriate standard).

---

## 6. Worked Example

**Problem:** A cantilever circular pipe (outer diameter $D_o = 100$ mm, wall thickness $t = 5$ mm) is fixed at the wall. At the free end, it carries: a vertical load $P = 5$ kN (downward) and an axial compressive force $F = 20$ kN. It is *not* pressurized for this example. Find the maximum combined normal stress at the fixed end cross-section at the top and bottom fibers (points A and B respectively).

**Given:**
- $D_o = 100$ mm → $D_i = 90$ mm; $r_o = 50$ mm; $r_i = 45$ mm
- $t = 5$ mm; $L_{cantilever} = 500$ mm
- $P = 5$ kN (vertical, downward)
- $F = 20$ kN (axial, compression)

**Solution:**

1. **Cross-sectional properties:**
$$A = \frac{\pi}{4}(D_o^2 - D_i^2) = \frac{\pi}{4}(100^2 - 90^2) = \frac{\pi}{4}(1900) = 1{,}492 \text{ mm}^2$$
$$I = \frac{\pi}{64}(D_o^4 - D_i^4) = \frac{\pi}{64}(100^4 - 90^4) = \frac{\pi}{64}(10^8 - 65{,}610{,}000) = \frac{\pi}{64}(34{,}390{,}000) = 1{,}689{,}000 \text{ mm}^4$$

2. **Internal forces at the fixed end:**
   - Axial: $N = -20{,}000$ N (compression)
   - Bending moment: $M = P \times L = 5{,}000 \times 500 = 2{,}500{,}000$ N·mm (sagging, so top fiber compressed by bending, bottom fiber tensioned)

3. **Axial stress (uniform):**
$$\sigma_{axial} = \frac{N}{A} = \frac{-20{,}000}{1{,}492} = -13.4 \text{ MPa (compression, uniform)}$$

4. **Bending stress at extreme fibers ($c = 50$ mm):**
$$\sigma_{bending} = \frac{M \cdot c}{I} = \frac{2{,}500{,}000 \times 50}{1{,}689{,}000} = 74.0 \text{ MPa}$$
- Top fiber (Point A, $y = +50$ mm): $\sigma_M = -74.0$ MPa (compression from sagging)
- Bottom fiber (Point B, $y = -50$ mm): $\sigma_M = +74.0$ MPa (tension from sagging)

5. **Combined normal stress:**
$$\sigma_A (top) = \sigma_{axial} + \sigma_M^{top} = -13.4 + (-74.0) = -87.4 \text{ MPa (compression)}$$
$$\sigma_B (bottom) = \sigma_{axial} + \sigma_M^{bot} = -13.4 + 74.0 = +60.6 \text{ MPa (tension)}$$

**Result:** Maximum compressive stress at the top fiber of the fixed end: 87.4 MPa. Maximum tensile stress at the bottom fiber: 60.6 MPa. The compressive side governs here due to the combined action of axial compression and bending compression at the top.

---

## 7. Common Mistakes & Pitfalls

- **Mistake 1 — Adding stress components that act on different planes:** Only stresses **on the same face** can be added. $\sigma_{from bending}$ and $\sigma_{from axial}$ both act on the cross-section face (same direction) and can be added. But $\tau_{from torsion}$ and $\sigma_{from bending}$ act on perpendicular components and must be handled via the stress element and Mohr's circle — not added directly.
- **Mistake 2 — Forgetting the sign of the axial load:** Tensile axial load adds positive (tensile) normal stress uniformly; compressive load adds negative (compressive) stress. The bending stress sign depends on which fiber (top or bottom) you evaluate.
- **Mistake 3 — Confusing inner radius $r_i$ and outer radius $r_o$ in thick-vs-thin wall problems:** The thin-wall formulas ($\sigma = pr/t$) use the **inner radius** approximately equal to the mid-surface radius. For $r/t < 10$, use Lamé's thick-wall cylinder equations.
- **Mistake 4 — Ignoring the hoop stress when the vessel bends:** When a pipe spans between supports, the bottom fiber in the hoop direction has both hoop tension ($pr/t$) and bending tension ($Mc/I$), which add — this can be the controlling stress location.
- **Mistake 5 — Superposing deflections in nonlinear (P-Δ) problems:** For columns with significant axial load, the lateral deflection amplifies the bending moment (P-Δ effect). Simple superposition underestimates stresses. Steel design (AISC 360 §C) requires second-order analysis or moment amplification in these cases.

---

## 8. Connections to Other Topics

- **Topics 01-A through 01-E (All previous topics):** Combined loadings is the synthesis of everything taught so far. Every stress contribution ($P/A$, $Mc/I$, $Tc/J$, $VQ/Ib$) comes from a previous topic.
- **Topic 01-H (Mohr's Circle):** Once the combined $\sigma$ and $\tau$ at a point are found, Mohr's circle transforms them to principal stresses and max shear — needed for failure checks.
- **Topic 01-I (Failure Criteria):** The principal stresses found after combined loading analysis are fed into failure criteria.
- **Topic 06 (Steel Design, AISC 360 §H):** Beam-column design directly addresses combined axial compression and bending. The H1-1 interaction equations are the code operationalization of the combined loading check.
- **Topic 07 (Concrete Design, ACI 318 §22.4):** Columns under combined axial + bending are analyzed with the **interaction diagram** ($P_n$-$M_n$ diagram), which is the ACI approach to combined loading failure.

---

## 9. Further Reading

| Resource | Where to look |
|----------|--------------|
| Hibbeler, *Mechanics of Materials*, 10th ed. | Chapter 8: Combined Loadings |
| Beer, Johnston & DeWolf, *Mechanics of Materials*, 7th ed. | Chapter 8: Principal Stresses Under Given Loading Conditions |
| Gere & Goodno, *Mechanics of Materials*, 9th ed. | Chapter 8: Applications of Plane Stress |
| ASME Boiler and Pressure Vessel Code, Section VIII | Pressure vessel design — industry standard |

---

## 10. Quick Self-Check

- [ ] I can write $\sigma_{total} = P/A \pm Mc/I$ and identify which sign applies at each extreme fiber for a given load combination.
- [ ] I can identify the critical cross-section and critical point(s) on the cross-section for a member in combined axial + bending.
- [ ] I can derive and apply the thin-wall cylinder equations $\sigma_1 = pr/t$ and $\sigma_2 = pr/2t$.
- [ ] I understand why $\sigma_1 = 2\sigma_2$ for a cylinder, and the practical consequence (direction of failure crack).
- [ ] I can list the conditions under which superposition of stresses is valid.

---

*Created by Structural Engineering Tutor • 2026-03-14*
