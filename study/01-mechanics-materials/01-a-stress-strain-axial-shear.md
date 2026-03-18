# Stress & Strain (Axial and Shear)

**Subject area:** Mechanics of Materials  
**Design standard / primary reference:** Hibbeler, *Mechanics of Materials*, 10th ed. — Ch. 1 & 2; Beer & Johnston, *Mechanics of Materials*, 7th ed. — Ch. 1 & 2  
**Depth level:** Undergraduate — accessible  
**Estimated study time:** 60 minutes

---

## 1. Introduction & Motivation

When you pull on a steel rod or push down on a concrete column, the member doesn't just move — it *deforms* internally, and internal forces are distributed throughout its cross-section. To understand how strong or stiff a member really is, we need to describe these internal effects in a way that is **independent of the member's size**. That is exactly what *stress* and *strain* accomplish.

Stress characterizes the **intensity of an internal force** (force per unit area), while strain characterizes the **intensity of deformation** (change in length per unit length or change in angle). Together, they form the language of all structural engineering: every failure criterion, every design check, and every FEM simulation is ultimately written in terms of stresses and strains.

This topic is the bedrock of Mechanics of Materials. Every subsequent topic — torsion, bending, buckling — is built on the stress and strain concepts introduced here. Mastering the sign conventions and the elastic relationship (Hooke's Law) now will save enormous confusion in more advanced subjects.

---

## 2. Key Concepts & Definitions

| Term | Symbol | Definition |
|------|--------|------------|
| Normal stress | $\sigma$ | Internal force per unit area acting **perpendicular** to a cross-section |
| Shear stress | $\tau$ | Internal force per unit area acting **parallel** to a cross-section |
| Normal strain | $\varepsilon$ | Change in length per unit original length (dimensionless) |
| Shear strain | $\gamma$ | Change in angle (in radians) between two originally perpendicular line elements |
| Modulus of elasticity (Young's modulus) | $E$ | Ratio of normal stress to normal strain in the elastic range |
| Shear modulus (modulus of rigidity) | $G$ | Ratio of shear stress to shear strain in the elastic range |
| Poisson's ratio | $\nu$ | Ratio of lateral strain to axial strain (magnitude), always positive |
| Ultimate stress | $\sigma_u$ | Maximum stress a material can withstand (from coupon test) |
| Yield stress | $\sigma_y$ or $F_y$ | Stress at which permanent (plastic) deformation begins |
| Factor of safety | $FS$ | Ratio of failure load (or stress) to allowable load (or stress) |

---

## 3. Governing Equations

| Equation | Description | Source |
|----------|-------------|--------|
| $\sigma = P / A$ | Average normal stress on a cross-section (axial load) | Hibbeler, 10th ed. Eq. 1-11 |
| $\tau_{avg} = V / A$ | Average shear stress on a cross-section (direct shear) | Hibbeler, 10th ed. Eq. 1-14 |
| $\varepsilon = \delta / L$ | Average normal strain | Hibbeler, 10th ed. Eq. 2-1 |
| $\sigma = E \varepsilon$ | Hooke's Law (normal) | Hibbeler, 10th ed. Eq. 3-9 |
| $\tau = G \gamma$ | Hooke's Law (shear) | Hibbeler, 10th ed. Eq. 3-11 |
| $\nu = -\varepsilon_{lat} / \varepsilon_{long}$ | Poisson's ratio | Hibbeler, 10th ed. Eq. 3-10 |
| $G = E / [2(1+\nu)]$ | Relation between E, G, and ν | Hibbeler, 10th ed. Eq. 10-18 |

$$
\sigma = \frac{P}{A}, \qquad \tau_{avg} = \frac{V}{A}
$$

$$
\varepsilon = \frac{\delta}{L_0}, \qquad \gamma \approx \tan\gamma = \frac{\Delta}{L_0}
$$

$$
\sigma = E\,\varepsilon, \qquad \tau = G\,\gamma, \qquad \nu = -\frac{\varepsilon_{lat}}{\varepsilon_{long}}
$$

**Variable legend:**

| Symbol | Description | SI Units | US Customary Units |
|--------|-------------|----------|--------------------|
| $\sigma$ | Normal stress | Pa (N/m²); MPa common | psi; ksi common |
| $\tau$ | Shear stress | Pa; MPa | psi; ksi |
| $P$ | Axial (normal) force | N; kN | lb; kip |
| $V$ | Shear force on section | N; kN | lb; kip |
| $A$ | Cross-sectional area | m²; mm² | in² |
| $\varepsilon$ | Normal strain | dimensionless (m/m) | dimensionless (in/in) |
| $\gamma$ | Shear strain | dimensionless (rad) | dimensionless (rad) |
| $\delta$ | Axial deformation (elongation) | m; mm | in |
| $L_0$ | Original length | m; mm | in |
| $E$ | Young's modulus | Pa; GPa | psi; ksi |
| $G$ | Shear modulus | Pa; GPa | psi; ksi |
| $\nu$ | Poisson's ratio | dimensionless | dimensionless |

---

## 4. Derivation

### 4-1. Normal Stress from Internal Force

**Step 1:** Take a body in equilibrium under external loads. Pass an imaginary cutting plane through the body at the section of interest. Remove one part, keeping the other in a free-body diagram (FBD).

**Step 2:** For the FBD to remain in equilibrium, the cut face must carry internal forces. The component perpendicular to the cut face is the **resultant normal force** $P$ (positive = tension, negative = compression).

**Step 3:** If we assume the normal force is **uniformly distributed** over area $A$, then every infinitesimal element $dA$ carries a stress $d F = \sigma \, dA$, and integrating:
$$P = \int_A \sigma \, dA$$

**Step 4:** For a uniform distribution (valid when the cross-section is away from load application points — Saint-Venant's principle):
$$\sigma = \frac{P}{A}$$

### 4-2. Shear Stress from Direct Shear

**Step 1:** Consider a bolt in single shear connecting two plates. Pass a cutting plane through the shear plane.

**Step 2:** The resultant internal shear force $V$ must equal the applied load $P$ by equilibrium.

**Step 3:** Assuming uniform shear stress distribution over the shear area $A$:
$$\tau_{avg} = \frac{V}{A}$$

*Note: This is the **average** shear stress. The actual distribution on most cross-sections is non-uniform. Topic 01-E addresses the true shear stress distribution in beams.*

### 4-3. Normal Strain

**Step 1:** Consider a line segment of original length $L_0$ along the axis of a deformed body. After loading, it has length $L$.

**Step 2:** The change in length is $\delta = L - L_0$.

**Step 3:** Normal strain is the normalized elongation:
$$\varepsilon = \frac{\delta}{L_0} = \frac{L - L_0}{L_0}$$

This is positive for elongation (tension) and negative for shortening (compression).

### 4-4. Hooke's Law and the Stress-Strain Diagram

**Step 1:** A tensile coupon test on a ductile metal (e.g., mild steel) reveals distinct regions:
- **Elastic region** (linear): $\sigma \propto \varepsilon$ — stress returns to zero when load is removed.
- **Yielding plateau** (steel): stress remains nearly constant while strain increases.
- **Strain-hardening**: material strengthens again.
- **Necking & fracture**: area localizes, apparent stress drops, fracture occurs.

**Step 2:** In the **elastic region**, the slope of the $\sigma$-$\varepsilon$ diagram is Young's modulus $E$:
$$\sigma = E \, \varepsilon \quad \text{(valid for } \sigma \leq \sigma_y \text{)}$$

**Step 3:** Analogously for shear: within the elastic range, $\tau = G \gamma$.

**Step 4:** Poisson's ratio: axial tension causes lateral contraction. If $\varepsilon_{long}$ is the axial strain and $\varepsilon_{lat}$ is the lateral strain:
$$\nu = -\frac{\varepsilon_{lat}}{\varepsilon_{long}} \quad \Rightarrow \quad \varepsilon_{lat} = -\nu \, \varepsilon_{long}$$

Typical values: steel $\nu \approx 0.30$, concrete $\nu \approx 0.20$, rubber $\nu \approx 0.50$.

**Step 5:** The three elastic constants are related. Using theory of elasticity (derivation in graduate treatment):
$$G = \frac{E}{2(1+\nu)}$$

For steel: $E = 200$ GPa (29,000 ksi), $\nu = 0.30$ → $G = 77$ GPa (11,200 ksi).

---

## 5. Design / Application Procedure

1. **Draw a complete FBD** of the member or a portion of it. Identify all external loads and reactions.
2. **Pass a cutting plane** at the section of interest. Apply the equations of equilibrium to find the internal resultant normal force $P$ and/or shear force $V$ on that section.
3. **Identify the cross-sectional area $A$** resisting the force. For direct shear, count the number of shear planes (single vs. double shear).
4. **Compute stress:**  $\sigma = P/A$ or $\tau_{avg} = V/A$.
5. **Check adequacy:** Compare the computed stress to the allowable stress:
   - Allowable normal stress: $\sigma_{allow} = \sigma_y / FS$ or $\sigma_u / FS$ (depending on the failure mode of concern).
   - Allowable shear stress typically taken as $\approx 0.6 \sigma_y$ for ductile metals.
6. **Compute strain** if deformation is required: $\varepsilon = \sigma / E$ (if elastic), then $\delta = \varepsilon \cdot L$.
7. **Check serviceability** (deflection limits) separately from strength (stress limits).

---

## 6. Worked Example

**Problem:** A circular steel rod with diameter $d = 25$ mm and length $L = 1.2$ m is subjected to a tensile axial load $P = 50$ kN. For steel, $E = 200$ GPa, $\sigma_y = 250$ MPa. Determine: (a) the average normal stress, (b) the axial strain, (c) the elongation, (d) the lateral strain (using $\nu = 0.30$), and (e) whether the rod yields.

**Given:**
- $d = 25$ mm → $r = 12.5$ mm
- $L = 1.2$ m $= 1200$ mm
- $P = 50$ kN $= 50{,}000$ N (tension)
- $E = 200$ GPa $= 200{,}000$ MPa
- $\sigma_y = 250$ MPa
- $\nu = 0.30$

**Required:** $\sigma$, $\varepsilon$, $\delta$, $\varepsilon_{lat}$, and yield check.

**Solution:**

1. **Cross-sectional area:**
$$A = \frac{\pi d^2}{4} = \frac{\pi (25)^2}{4} = 490.87 \text{ mm}^2$$

2. **Normal stress:**
$$\sigma = \frac{P}{A} = \frac{50{,}000 \text{ N}}{490.87 \text{ mm}^2} = 101.9 \text{ MPa (tension)}$$

3. **Yield check:**
$$\sigma = 101.9 \text{ MPa} < \sigma_y = 250 \text{ MPa} \quad \checkmark \text{ (elastic — Hooke's Law applies)}$$

4. **Axial strain:**
$$\varepsilon = \frac{\sigma}{E} = \frac{101.9 \text{ MPa}}{200{,}000 \text{ MPa}} = 5.095 \times 10^{-4} \text{ mm/mm}$$

5. **Elongation:**
$$\delta = \varepsilon \cdot L = (5.095 \times 10^{-4})(1200 \text{ mm}) = 0.611 \text{ mm}$$

6. **Lateral strain:**
$$\varepsilon_{lat} = -\nu \, \varepsilon = -(0.30)(5.095 \times 10^{-4}) = -1.529 \times 10^{-4} \text{ mm/mm}$$
The rod contracts laterally (diameter decreases slightly).

**Result:** $\sigma = 101.9$ MPa (well below yield), $\delta = 0.611$ mm elongation, lateral contraction strain $= -1.53 \times 10^{-4}$. The rod remains elastic.

---

## 7. Common Mistakes & Pitfalls

- **Mistake 1 — Mixed units:** Mixing N with mm² gives MPa correctly ($1 \text{ N/mm}^2 = 1 \text{ MPa}$), but mixing kN with mm² gives GPa, which is almost certainly wrong. Always check units explicitly at each step.
- **Mistake 2 — Forgetting Poisson's ratio changes the lateral dimension:** The diameter of a tensioned rod decreases. This matters for press-fit and interference-fit problems.
- **Mistake 3 — Applying $\sigma = P/A$ near load application points:** Saint-Venant's principle says the uniform stress formula is only valid at sections **away from** concentrated loads (at least one cross-sectional dimension away). Near the load, stress concentrations exist.
- **Mistake 4 — Confusing single and double shear:** A bolt in double shear has two shear planes, so $A$ in $\tau = V/A$ is **twice** the bolt's cross-sectional area.
- **Mistake 5 — Using $\sigma = P/A$ for bending:** This formula applies **only to axial loads**. For beams in bending, use $\sigma = -My/I$ (Topic 01-D).

---

## 8. Connections to Other Topics

- **Topic 01-B (Axial Deformation):** Uses $\sigma = P/A$ and Hooke's Law directly to compute elongation $\delta = PL/AE$.
- **Topic 01-H (Mohr's Circle):** The stresses $\sigma$ and $\tau$ found on any section are transformed to find principal stresses on inclined planes — needed for failure analysis.
- **Topic 01-I (Failure Criteria):** Von Mises and Tresca criteria check whether a combination of $\sigma$ and $\tau$ causes yielding.
- **Topic 06 (Steel Design, AISC 360):** Design limit states for tension members ($F_y$, $F_u$) come directly from the stress-strain diagram defined here.
- **Topic 08 (FEM):** The constitutive matrix $[D]$ relating stress vector $\{\sigma\}$ to strain vector $\{\varepsilon\}$ generalizes Hooke's Law from 1D to 3D.

---

## 9. Further Reading

| Resource | Where to look |
|----------|--------------|
| Hibbeler, *Mechanics of Materials*, 10th ed. | Chapters 1 (Stress) and 2 (Strain); Chapter 3 (Mechanical Properties) |
| Beer, Johnston & DeWolf, *Mechanics of Materials*, 7th ed. | Chapters 1–2 |
| Gere & Goodno, *Mechanics of Materials*, 9th ed. | Chapter 1 |
| ASTM E8/E8M-22 | Standard test method for tension testing of metallic materials |

---

## 10. Quick Self-Check

- [ ] I can state $\sigma = P/A$ and $\tau = V/A$, define every symbol, and explain the difference between normal and shear stress.
- [ ] I understand Saint-Venant's principle and know when the uniform stress assumption is valid.
- [ ] I can draw and label the key features of a stress-strain diagram for mild steel (elastic region, yield point, ultimate stress, fracture).
- [ ] I can apply Hooke's Law and Poisson's ratio to find all strains from a given axial stress state.
- [ ] I can connect stress and strain to deformation ($\delta = \varepsilon L$) for a simple axial member.

---

*Created by Structural Engineering Tutor • 2026-03-14*
