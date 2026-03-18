# Axial Deformation & Statically Indeterminate Axial Members

**Subject area:** Mechanics of Materials  
**Design standard / primary reference:** Hibbeler, *Mechanics of Materials*, 10th ed. — Ch. 4; Beer & Johnston, *Mechanics of Materials*, 7th ed. — Ch. 2  
**Depth level:** Undergraduate — accessible  
**Estimated study time:** 75 minutes

---

## 1. Introduction & Motivation

In Topic 01-A we learned how to compute the stress in an axially loaded member. Now the natural next question is: **how much does the member actually deform?** Knowing deformation is critical for two reasons. First, excessive deflections can make a structure unserviceable (a bridge deck that sags too much or a machine component that misaligns). Second, for **statically indeterminate** structures — where there are more unknowns than equilibrium equations — we must use deformation conditions to find the internal forces.

The formula $\delta = PL/AE$ is one of the most-used equations in structural engineering. It appears in truss analysis, column shortening calculations, foundation settlement estimates, and the stiffness matrix of every FEM bar element. The concept of **compatibility** — requiring that deformations are geometrically consistent — is the key idea that unlocks all statically indeterminate problems.

This topic also introduces **thermal effects**: when a member is free, temperature change causes uniform elongation with no stress; when restrained, it causes internal forces. This thermal-vs-mechanical superposition principle recurs constantly in real engineering problems.

---

## 2. Key Concepts & Definitions

| Term | Symbol | Definition |
|------|--------|------------|
| Axial deformation | $\delta$ | Change in length of a member along its axis; positive = elongation |
| Axial rigidity | $AE$ | Product of cross-sectional area and elastic modulus; governs stiffness |
| Axial stiffness | $k = AE/L$ | Force per unit deformation for a bar element (N/mm or kip/in) |
| Statically determinate | — | All reactions and internal forces found from equilibrium alone |
| Statically indeterminate | — | More unknowns than equilibrium equations; requires compatibility |
| Degree of indeterminacy | $n$ | Number of redundant reactions/forces |
| Compatibility equation | — | Geometric condition on deformations (e.g., total elongation = 0) |
| Superposition | — | Splitting a complex loading into simpler cases and adding results |
| Coefficient of thermal expansion | $\alpha$ | Strain per degree of temperature change |
| Thermal deformation | $\delta_T$ | Free elongation due to temperature: $\delta_T = \alpha \, \Delta T \, L$ |
| Thermal stress | $\sigma_T$ | Stress arising when thermal deformation is constrained |

---

## 3. Governing Equations

| Equation | Description | Source |
|----------|-------------|--------|
| $\delta = \dfrac{PL}{AE}$ | Deformation of a prismatic bar with constant $P$, $A$, $E$ | Hibbeler, 10th ed. Eq. 4-2 |
| $\delta = \displaystyle\sum_i \dfrac{P_i L_i}{A_i E_i}$ | Deformation by segments (varying $P$, $A$, or $E$) | Hibbeler, 10th ed. Eq. 4-4 |
| $\delta = \displaystyle\int_0^L \dfrac{P(x)}{A(x)E} \, dx$ | Deformation for continuously varying cross-section or load | Hibbeler, 10th ed. §4.2 |
| $\delta_T = \alpha \, \Delta T \, L$ | Free thermal deformation | Hibbeler, 10th ed. Eq. 4-3 |
| $\delta_{total} = \delta_{mech} + \delta_T$ | Total deformation (mechanical + thermal) | Superposition principle |

$$
\delta = \frac{PL}{AE}
$$

$$
\delta = \sum_{i} \frac{P_i L_i}{A_i E_i}
$$

$$
\delta_T = \alpha \, \Delta T \, L
$$

**Variable legend:**

| Symbol | Description | SI Units | US Customary Units |
|--------|-------------|----------|--------------------|
| $\delta$ | Axial deformation (elongation +) | mm; m | in |
| $P$ | Internal axial force (tension +) | N; kN | lb; kip |
| $L$ | Length of member or segment | mm; m | in |
| $A$ | Cross-sectional area | mm² | in² |
| $E$ | Young's modulus | MPa; GPa | ksi |
| $AE$ | Axial rigidity | N; kN | kip |
| $\alpha$ | Coefficient of thermal expansion | °C⁻¹; K⁻¹ | °F⁻¹ |
| $\Delta T$ | Change in temperature (positive = heating) | °C; K | °F |

---

## 4. Derivation

### 4-1. Derivation of $\delta = PL/AE$

**Step 1:** Consider a prismatic bar of length $L$, area $A$, modulus $E$, subjected to axial tension $P$ applied at the ends.

**Step 2:** From equilibrium, the internal axial force at every cross-section equals $P$ (constant along the length).

**Step 3:** From the normal stress formula: $\sigma = P/A$ (uniform over each cross-section).

**Step 4:** From Hooke's Law: $\varepsilon = \sigma/E = P/(AE)$ (also constant along the length).

**Step 5:** Strain is the elongation per unit length, so for a small element $dx$:
$$d\delta = \varepsilon \, dx = \frac{P}{AE} \, dx$$

**Step 6:** Integrate over the full length (since $P$, $A$, $E$ are constant):
$$\delta = \int_0^L \frac{P}{AE} \, dx = \frac{PL}{AE}$$

This is the **axial deformation formula**.

### 4-2. Statically Indeterminate Axial Members — Method of Compatibility

**Concept:** When a structure has more unknowns than equilibrium equations, we write additional equations from the **geometry of deformation** (compatibility conditions), then use the force-deformation relation $\delta = PL/AE$ to express compatibility in terms of the unknowns.

**Step 1 — Equilibrium:** Write all available equilibrium equations. Identify how many redundant unknowns remain.

**Step 2 — Release the redundant:** Choose one redundant reaction (call it $R$). Release its constraint to get a **released (statically determinate) structure**. Compute the deformation $\delta_0$ at the released coordinate due to all applied loads (with $R = 0$).

**Step 3 — Apply unit redundant:** Apply $R = 1$ alone on the released structure. Compute the deformation $\delta_R$ per unit $R$.

**Step 4 — Compatibility condition:** The actual deformation at the released coordinate must match the real boundary condition. For a fixed support: total deformation = 0:
$$\delta_0 + R \cdot \delta_R = 0 \quad \Rightarrow \quad R = -\frac{\delta_0}{\delta_R}$$

**Step 5 — Back-substitute:** With $R$ known, compute all other reactions and internal forces from equilibrium.

### 4-3. Thermal Effects

**Free case (no constraint):** Temperature increases by $\Delta T$. The bar wants to elongate by:
$$\delta_T = \alpha \, \Delta T \, L$$
No stress is developed because the bar can expand freely.

**Constrained case:** If the bar is fixed at both ends and temperature rises by $\Delta T$:

Step 1: Treat one end as free (release it). Free thermal elongation: $\delta_T = \alpha \Delta T L$.

Step 2: To restore the released end to zero displacement, a compressive force $P$ must be applied such that:
$$\frac{PL}{AE} = \alpha \Delta T L \quad \Rightarrow \quad P = AE \alpha \Delta T$$

Step 3: The thermal stress is:
$$\sigma_T = \frac{P}{A} = E \alpha \Delta T \quad \text{(compressive)}$$

---

## 5. Design / Application Procedure

1. **Draw an FBD** of each member/joint. Label all external loads and unknown reactions.
2. **Write equilibrium equations.** Count unknowns. If unknown count = equation count → determinate. If greater → indeterminate.
3. **For indeterminate problems:**
   a. Identify the degree of indeterminacy ($n$ = unknowns − equations).
   b. Choose $n$ redundants. Release them to create a determinate structure.
   c. Write $n$ compatibility equations (geometric conditions on displacements/deformations).
   d. Express deformations in terms of unknowns using $\delta = PL/AE$ (and $\delta_T = \alpha \Delta T L$ if needed).
   e. Solve the system of equations for the redundants.
4. **Recover all internal forces** by back-substituting redundants into equilibrium.
5. **Compute stresses** $\sigma = P/A$ and check against allowable values.
6. **Compute deformations** at points of interest using $\delta = \sum P_i L_i / (A_i E_i)$.

---

## 6. Worked Example

**Problem:** A steel rod (1) and a brass rod (2) are placed end-to-end between two rigid walls, as shown below. Both rods have the same diameter $d = 30$ mm. A force $P = 20$ kN is applied at the junction. Steel: $L_1 = 0.8$ m, $E_1 = 200$ GPa. Brass: $L_2 = 0.5$ m, $E_2 = 105$ GPa. Find the reactions at the walls and the stress in each rod.

```
Wall A ——[Steel, L₁=0.8m]——◄P=20kN►——[Brass, L₂=0.5m]—— Wall B
```

**Given:**
- $d = 30$ mm → $A = \pi(30)^2/4 = 706.9$ mm²
- $P = 20$ kN (applied at junction, directed toward Wall B)
- $E_1 = 200{,}000$ MPa; $L_1 = 800$ mm
- $E_2 = 105{,}000$ MPa; $L_2 = 500$ mm

**Required:** Reactions $R_A$ (at Wall A) and $R_B$ (at Wall B); stresses $\sigma_1$, $\sigma_2$.

**Solution:**

1. **Equilibrium** (taking rightward forces as positive; $R_A$ = reaction at A pointing right, $R_B$ at B pointing left):
$$R_A + P = R_B \quad \Rightarrow \quad R_A - R_B + 20 = 0 \quad \Rightarrow \quad R_A = R_B - 20 \quad \text{...(i)}$$
*One equation, two unknowns → 1 degree of indeterminacy.*

2. **Internal forces by section method:**
   - In rod 1 (between A and junction): $P_1 = R_A$ (tension if $R_A > 0$).
   - In rod 2 (between junction and B): $P_2 = -R_B$ (compression if $R_B > 0$, i.e., rod 2 is compressed).

   Re-orienting: Let $R_A$ = left-wall reaction (tension on rod 1) and $R_B$ = right-wall reaction (compression on rod 2).
   
   Equilibrium at junction: $R_A + 20 = R_B$ ...(i).

3. **Compatibility:** Both walls are rigid, so total deformation of the system = 0:
$$\delta_1 + \delta_2 = 0$$
$$\frac{R_A \cdot L_1}{A \cdot E_1} + \frac{(-R_B) \cdot L_2}{A \cdot E_2} = 0$$
$$\frac{R_A \cdot 800}{706.9 \times 200{,}000} - \frac{R_B \cdot 500}{706.9 \times 105{,}000} = 0$$
$$R_A \times 5.658 \times 10^{-6} = R_B \times 6.748 \times 10^{-6}$$
$$R_A = 1.1925 \, R_B \quad \text{...(ii)}$$

4. **Solve:** Substitute (ii) into (i):
$$1.1925 \, R_B - R_B = 20 \text{ kN}$$
$$0.1925 \, R_B = 20 \quad \Rightarrow \quad R_B = 103.9 \text{ kN}$$
$$R_A = 1.1925 \times 103.9 = 123.9 \text{ kN}$$

*Check equilibrium: $123.9 - 103.9 = 20$ kN ✓*

5. **Stresses:**
$$\sigma_1 = \frac{R_A}{A} = \frac{123{,}900 \text{ N}}{706.9 \text{ mm}^2} = 175.3 \text{ MPa (tension)}$$
$$\sigma_2 = \frac{R_B}{A} = \frac{103{,}900 \text{ N}}{706.9 \text{ mm}^2} = 147.0 \text{ MPa (compression)}$$

**Result:** $R_A = 123.9$ kN, $R_B = 103.9$ kN. Steel rod: 175.3 MPa tension; Brass rod: 147.0 MPa compression. Both are well within typical yield limits for these materials.

---

## 7. Common Mistakes & Pitfalls

- **Mistake 1 — Wrong sign convention in compatibility:** Always define a positive deformation direction consistently (e.g., elongation = positive). Mixing positive directions for different segments will give wrong compatibility equations.
- **Mistake 2 — Forgetting that reactions can both be pointing inward (compressive pre-stress):** When a rigid structure heats up and is constrained, both end reactions press inward. Don't assume one reaction must be tension and the other compression based on the applied load direction.
- **Mistake 3 — Applying $\delta = PL/AE$ when $A$ or $E$ varies continuously:** If the cross-section tapers (e.g., a cone), use the integral form $\delta = \int P \, dx / [A(x)E]$.
- **Mistake 4 — Ignoring thermal deformation in mixed problems:** When both mechanical loads and temperature changes coexist, both contributions must appear in the compatibility equation.
- **Mistake 5 — Assuming deformation is zero just because a support exists:** A support prevents displacement at a specific point, not along the whole member. The member between two fixed ends can still have internal deformation (and stress).

---

## 8. Connections to Other Topics

- **Topic 01-A (Stress & Strain):** $\delta = PL/AE$ is a direct application of Hooke's Law: $\varepsilon = P/(AE)$ integrated over length.
- **Topic 02 (Structural Analysis — Determinate):** Method of consistent deformations (force method) for trusses uses the same compatibility concept generalized to multi-member systems.
- **Topic 04 (Matrix Structural Analysis):** The axial stiffness $k = AE/L$ is the $2 \times 2$ stiffness matrix of a bar element — the simplest FEM element.
- **Topic 08 (FEM):** Deriving the bar element stiffness matrix from $\delta = PL/AE$ is the entry point to finite element method.
- **Topic 10 (Loads — ASCE 7):** Thermal loads in building frames produce forces in restrained members exactly as derived above.

---

## 9. Further Reading

| Resource | Where to look |
|----------|--------------|
| Hibbeler, *Mechanics of Materials*, 10th ed. | Chapter 4: Axial Load |
| Beer, Johnston & DeWolf, *Mechanics of Materials*, 7th ed. | Chapter 2: Stress and Strain — Axial Loading |
| Gere & Goodno, *Mechanics of Materials*, 9th ed. | Chapter 2: Axially Loaded Members |

---

## 10. Quick Self-Check

- [ ] I can derive $\delta = PL/AE$ from first principles starting with $\varepsilon = \sigma/E$.
- [ ] I can identify whether an axial problem is statically determinate or indeterminate and state the degree of indeterminacy.
- [ ] I can write compatibility conditions for a multi-segment axially loaded system with fixed ends.
- [ ] I can compute thermal stress in a fully constrained bar when temperature changes.
- [ ] I can correctly apply superposition when both mechanical and thermal loads act simultaneously.

---

*Created by Structural Engineering Tutor • 2026-03-14*
