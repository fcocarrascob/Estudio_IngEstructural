# Pure Bending: Normal Stresses

**Subject area:** Mechanics of Materials  
**Design standard / primary reference:** Hibbeler, *Mechanics of Materials*, 10th ed. — Ch. 6; Beer & Johnston, *Mechanics of Materials*, 7th ed. — Ch. 4  
**Depth level:** Undergraduate — accessible  
**Estimated study time:** 75 minutes

---

## 1. Introduction & Motivation

Bending is the most common type of loading in structural engineering. Virtually every horizontal member — floor beams, roof girders, bridge decks — must carry transverse loads that bend it. The resulting deformation is accompanied by **normal stresses** that vary across the depth of the cross-section: the top fibers compress and the bottom fibers stretch (for a simply supported beam with a downward load), while somewhere in between, the stress is zero — the **neutral axis**.

The flexure formula $\sigma = -My/I$ (or $\sigma = Mc/I$ for the maximum magnitude) is the core result of bending theory. It allows us to find the **bending stress at any point** in a cross-section from the applied moment $M$, the distance from the neutral axis $y$, and the **second moment of area** $I$ (often called the moment of inertia). This formula is used thousands of times per day by structural engineers worldwide to size beams, check stress limits in steel design (AISC 360), and verify that concrete sections have adequate flexural strength before providing reinforcement.

This topic covers **pure bending** — the idealized case where the internal moment $M$ is constant along the beam and shear forces are absent. Topic 01-E extends the analysis to beams with shear.

---

## 2. Key Concepts & Definitions

| Term | Symbol | Definition |
|------|--------|------------|
| Bending moment | $M$ | Internal resultant couple on a cross-section (N·m; kip·ft) |
| Neutral axis | N.A. | Line in the cross-section where normal stress (and strain) = 0; passes through centroid of section |
| Flexural normal stress | $\sigma$ | Normal stress due to bending: varies linearly from N.A. |
| Second moment of area (moment of inertia) | $I$ | Geometric section property: $I = \int_A y^2 \, dA$; resists bending |
| Distance to extreme fiber | $c$ | Maximum value of $|y|$ from neutral axis to outermost fiber |
| Section modulus | $S$ | $S = I / c$; compact form for peak bending stress: $\sigma_{max} = M/S$ |
| Centroid | $\bar{y}$ | Point where the first moment of area is zero; location of neutral axis |
| Radius of curvature | $\rho$ (or $R$) | Radius of the bent beam's centroidal axis |
| Curvature | $\kappa$ | $\kappa = 1/\rho = M/(EI)$; inverse of radius of curvature |
| Flexural rigidity | $EI$ | Product of modulus and moment of inertia; governs bending stiffness |

---

## 3. Governing Equations

| Equation | Description | Source |
|----------|-------------|--------|
| $\sigma = -My/I$ | Flexure formula: normal stress at distance $y$ from N.A. | Hibbeler, 10th ed. Eq. 6-13 |
| $\sigma_{max} = Mc/I = M/S$ | Maximum normal stress (at extreme fiber) | Hibbeler, 10th ed. Eq. 6-14 |
| $\kappa = M/(EI)$ | Curvature-moment relation | Hibbeler, 10th ed. Eq. 6-10 |
| $S = I/c$ | Elastic section modulus | Definition |
| $I = \int_A y^2 \, dA$ | Second moment of area about the neutral axis | Definition |
| Parallel axis theorem: $I = \bar{I} + A d^2$ | Transfer moment of inertia to a parallel axis at distance $d$ | Hibbeler, Appendix A |

$$
\sigma = -\frac{M y}{I}, \qquad |\sigma_{max}| = \frac{M c}{I} = \frac{M}{S}
$$

$$
\kappa = \frac{1}{\rho} = \frac{M}{EI}
$$

**Variable legend:**

| Symbol | Description | SI Units | US Customary Units |
|--------|-------------|----------|--------------------|
| $\sigma$ | Normal bending stress (+tension, −compression) | MPa | ksi; psi |
| $M$ | Bending moment at the section (positive = sagging) | N·m; kN·m | kip·ft; kip·in |
| $y$ | Distance from neutral axis (+upward typical) | mm; m | in |
| $I$ | Second moment of area about neutral axis | mm⁴; m⁴ | in⁴ |
| $c$ | Distance from N.A. to extreme fiber | mm | in |
| $S$ | Elastic section modulus $= I/c$ | mm³ | in³ |
| $E$ | Young's modulus | MPa; GPa | ksi |
| $\kappa$ | Curvature | mm⁻¹; m⁻¹ | in⁻¹ |
| $\rho$ (or $R$) | Radius of curvature | mm; m | in |

---

## 4. Derivation

### 4-1. Kinematic Assumption (Plane Sections Remain Plane)

**Step 1:** The fundamental assumption of Euler-Bernoulli beam theory: **plane cross-sections perpendicular to the beam axis remain plane and perpendicular to the deformed beam axis** after bending. This is a kinematic assumption verified experimentally for slender beams.

**Step 2:** Consider two adjacent cross-sections separated by $dx$ along the beam axis. After bending, the angle between them is $d\theta$. The centroidal axis bends to radius $\rho$.

**Step 3:** A fiber at distance $y$ above the centroidal axis has arc length $(ρ - y)d\theta$ after bending and original length $\rho \, d\theta$. The normal strain is:
$$\varepsilon = \frac{(\rho - y)d\theta - \rho \, d\theta}{\rho \, d\theta} = -\frac{y}{\rho}$$

Strain **varies linearly** with $y$: zero at the centroidal axis, maximum at the extreme fibers.

### 4-2. Neutral Axis and Normal Stress

**Step 4:** Apply Hooke's Law: $\sigma = E\varepsilon = -Ey/\rho$.

**Step 5:** For equilibrium, the resultant of normal stresses on the cross-section must equal zero (pure bending — no axial force):
$$\int_A \sigma \, dA = 0 \quad \Rightarrow \quad -\frac{E}{\rho}\int_A y \, dA = 0$$

This requires $\int_A y \, dA = 0$, which means $y$ is measured from the **centroid** of the cross-section. Therefore: **the neutral axis passes through the centroid**.

### 4-3. Moment-Curvature Relation

**Step 6:** The internal moment $M$ must equal the resultant moment of the normal stress distribution:
$$M = \int_A (-\sigma) \cdot (-y) \, dA = \int_A \sigma \cdot (-y) \, dA$$

*Note on sign convention: using the beam mechanics convention where positive $M$ causes compression above and tension below (sagging positive), the moment is:*
$$M = -\int_A \sigma \, y \, dA = -\int_A \left(-\frac{Ey}{\rho}\right) y \, dA = \frac{E}{\rho} \int_A y^2 \, dA = \frac{EI}{\rho}$$

Therefore: $\kappa = 1/\rho = M/(EI)$.

### 4-4. The Flexure Formula

**Step 7:** Substitute $1/\rho = M/(EI)$ back into $\sigma = -Ey/\rho$:
$$\sigma = -\frac{Ey}{\rho} = -E \cdot \frac{M}{EI} \cdot y = -\frac{My}{I}$$

This is the **flexure formula**.

**Maximum stress at extreme fiber** $y = \pm c$:
$$|\sigma_{max}| = \frac{Mc}{I} = \frac{M}{S}, \quad \text{where } S = \frac{I}{c}$$

### 4-5. Second Moments of Area for Common Sections

| Section | $I$ about centroidal horizontal axis |
|---------|---------------------------------------|
| Rectangle ($b \times h$) | $I = bh^3/12$ |
| Circle (diameter $d$) | $I = \pi d^4/64$ |
| Hollow rectangle | $I = (bh^3 - b_i h_i^3)/12$ |
| Hollow circle | $I = \pi(d_o^4 - d_i^4)/64$ |

**Parallel axis theorem** (transfer $\bar{I}$ about centroidal axis to axis at distance $d$):
$$I = \bar{I} + A d^2$$

---

## 5. Design / Application Procedure

1. **Draw the shear and moment diagram** to find the maximum bending moment $M_{max}$ and its location.
2. **Locate the neutral axis** by finding the centroid of the cross-section.
3. **Compute the moment of inertia $I$** about the centroidal axis. For built-up sections, use the parallel axis theorem.
4. **Determine $c$**: for doubly symmetric sections $c = h/2$; for asymmetric sections, compute $c_{top}$ and $c_{bot}$ separately.
5. **Compute bending stress:** $\sigma_{max} = M \cdot c / I$.
6. **Check adequacy:** $\sigma_{max} \leq \sigma_{allow}$ (or $\sigma_y$ for yield-strength check).
7. **For design (finding required size):** Rearrange to get required section modulus $S_{req} = M/\sigma_{allow}$, then select a section from steel tables (AISC) or size a custom section.

---

## 6. Worked Example

**Problem:** A simply-supported W-shaped steel beam spans $L = 6$ m and carries a uniform load $w = 20$ kN/m. Use the section W310×97 (AISC properties: $I_x = 222 \times 10^6$ mm⁴, $d = 308$ mm, $S_x = 1440 \times 10^3$ mm³). Determine: (a) the maximum bending moment, (b) the maximum bending stress, and (c) whether the beam yields ($\sigma_y = 250$ MPa for A36).

*(Note: For this problem we use the section properties directly; a full AISC design would also check shear and deflection.)*

**Given:**
- $w = 20$ kN/m; $L = 6$ m
- $I_x = 222 \times 10^6$ mm⁴
- $d = 308$ mm → $c = 154$ mm
- $S_x = 1440 \times 10^3$ mm³
- $\sigma_y = 250$ MPa

**Solution:**

1. **Maximum moment (midspan):**
$$M_{max} = \frac{wL^2}{8} = \frac{20 \times 6^2}{8} = \frac{720}{8} = 90 \text{ kN·m} = 90 \times 10^6 \text{ N·mm}$$

2. **Maximum bending stress:**
$$\sigma_{max} = \frac{M_{max}}{S_x} = \frac{90 \times 10^6 \text{ N·mm}}{1440 \times 10^3 \text{ mm}^3} = 62.5 \text{ MPa}$$

3. **Yield check:**
$$\sigma_{max} = 62.5 \text{ MPa} \ll \sigma_y = 250 \text{ MPa} \quad \checkmark$$

*(This section is quite oversized for this load — for a real design, a lighter section would be tried.)*

4. **Verify using $I$ directly:**
$$\sigma_{max} = \frac{M_{max} \cdot c}{I_x} = \frac{90 \times 10^6 \times 154}{222 \times 10^6} = \frac{13.86 \times 10^9}{222 \times 10^6} = 62.4 \text{ MPa} \quad \checkmark$$

**Result:** $M_{max} = 90$ kN·m at midspan. Maximum bending stress: 62.5 MPa in compression at the top flange and tension at the bottom flange. The beam remains well within the elastic range.

---

## 7. Common Mistakes & Pitfalls

- **Mistake 1 — Forgetting the negative sign in $\sigma = -My/I$:** The sign matters. For a positive (sagging) moment and $y$ measured upward, the top fiber has compressive (negative) stress. Many students drop the sign and get the wrong fiber in tension/compression.
- **Mistake 2 — Using $I$ about the wrong axis:** Always compute $I$ about the **centroidal axis** of the cross-section. For L-shapes, C-shapes, or built-up beams, the centroid is not at mid-height.
- **Mistake 3 — Forgetting the parallel axis theorem for composite sections:** When combining rectangles or circles to find $I$ of a built-up shape, each component's $I$ must be transferred to the overall centroidal axis using $I = \bar{I} + Ad^2$.
- **Mistake 4 — Applying the flexure formula when cross-sections are not symmetric:** For bending about a non-principal axis, or for unsymmetric bending, the simple $\sigma = -My/I$ formula is insufficient; the full biaxial bending formula must be used.
- **Mistake 5 — Confusing $S$ and $I$:** $S = I/c$ is section modulus (units: mm³ or in³). If $M$ is in N·mm and $S$ is in mm³, then $\sigma = M/S$ gives MPa directly.

---

## 8. Connections to Other Topics

- **Topic 01-E (Shear Stresses):** Beams in reality carry both bending and shear simultaneously. The shear stress formula $\tau = VQ/Ib$ adds the transverse shear component to the bending normal stress.
- **Topic 01-F (Beam Deflections):** The curvature-moment relationship $d^2v/dx^2 \approx M/(EI)$ used to find beam deflections by double integration comes directly from this topic's derivation.
- **Topic 01-G (Combined Loadings):** When a member carries axial load plus bending, stresses are superimposed: $\sigma = P/A \pm My/I$.
- **Topic 06 (Steel Design, AISC 360):** Every beam design check starts with computing $\sigma = M/S$ and comparing to the yield limit. The plastic section modulus $Z$ and the plastic moment $M_p = F_y Z$ extend this elastic analysis to plastic design.
- **Topic 07 (Concrete Design, ACI 318):** Flexural analysis of RC sections uses the same linear strain distribution (plane sections remain plane) but with a nonlinear concrete stress-strain response.

---

## 9. Further Reading

| Resource | Where to look |
|----------|--------------|
| Hibbeler, *Mechanics of Materials*, 10th ed. | Chapter 6: Bending |
| Beer, Johnston & DeWolf, *Mechanics of Materials*, 7th ed. | Chapter 4: Pure Bending |
| Gere & Goodno, *Mechanics of Materials*, 9th ed. | Chapter 5: Stresses in Beams |
| AISC *Steel Construction Manual*, 16th ed. | Chapter on beam design; tables for $S_x$, $Z_x$, $I_x$ |

---

## 10. Quick Self-Check

- [ ] I can state the flexure formula $\sigma = -My/I$ and explain the sign convention.
- [ ] I know that the neutral axis passes through the centroid, and I can locate the centroid of a composite cross-section.
- [ ] I can compute $I$ for a rectangle, a circle, and a built-up shape using the parallel axis theorem.
- [ ] I understand why $\sigma_{max} = M/S$ is equivalent to $\sigma_{max} = Mc/I$.
- [ ] I can connect bending stress to beam deflections through the curvature-moment relation $\kappa = M/(EI)$.

---

*Created by Structural Engineering Tutor • 2026-03-14*
