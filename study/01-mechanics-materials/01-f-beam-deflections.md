# Beam Deflections: Integration, Moment-Area, and Superposition

**Subject area:** Mechanics of Materials  
**Design standard / primary reference:** Hibbeler, *Mechanics of Materials*, 10th ed. — Ch. 12; Beer & Johnston, *Mechanics of Materials*, 7th ed. — Ch. 9; ASCE 7-22 §L for deflection limits  
**Depth level:** Undergraduate — accessible  
**Estimated study time:** 90 minutes

---

## 1. Introduction & Motivation

Knowing the stress in a beam is only half the picture. Engineers must also verify that the beam **does not deflect excessively** — a floor beam that bounces when you walk across it, or a roof purlin that pools rainwater because it sags too much, has failed in *serviceability* even if it hasn't yielded. Design codes (e.g., ASCE 7, IBC) set deflection limits such as $L/360$ for live load or $L/240$ for total load.

Beam deflections arise because every element of the beam cross-section strains under the bending moment, and these differential strains accumulate into a visible **deflection curve** (the elastic curve). The governing differential equation $EI \, v'' = M(x)$ connects curvature to moment, and integrating it twice gives the deflection $v(x)$.

Three methods are taught at the undergraduate level:
1. **Double integration** — applies boundary conditions to the ODE; exact but algebraically heavy.
2. **Moment-area method** — uses geometric properties of the moment diagram; fast for specific deflection points.
3. **Superposition** — adds results from standard beam tables; essential in practice.

---

## 2. Key Concepts & Definitions

| Term | Symbol | Definition |
|------|--------|------------|
| Elastic curve | $v(x)$ | Deflection of the beam's neutral axis at position $x$ along the span |
| Curvature | $\kappa = v''$ | Second derivative of deflection (for small slopes: $1/\rho \approx v''$) |
| Flexural rigidity | $EI$ | Stiffness against bending; governs curvature for a given moment |
| Slope | $\theta = v'$ | First derivative of deflection; angle of the elastic curve (radians) |
| Maximum deflection | $\delta_{max}$ or $v_{max}$ | Peak downward deflection; usually occurs at midspan (symmetric loading) |
| Boundary conditions | B.C. | Conditions on $v$ and $v'$ at supports (pin/roller: $v=0$; fixed: $v=0$, $v'=0$) |
| Superposition | — | Adding deflections from multiple load cases, valid within elastic range |
| Moment-area theorem 1 | — | Change in slope between two points = area of $M/(EI)$ diagram between them |
| Moment-area theorem 2 | — | Tangential deviation of a point from the tangent at another = first moment of $M/(EI)$ area about the first point |
| Serviceability limit | — | Deflection limit set by code (e.g., $\Delta \leq L/360$ for live load per ASCE 7-22) |

---

## 3. Governing Equations

| Equation | Description | Source |
|----------|-------------|--------|
| $EI \, v'' = M(x)$ | Elastic curve ODE (positive $M$ convention matches sign of $v''$) | Hibbeler, 10th ed. Eq. 12-8 |
| $EI \, v' = \int M(x) \, dx + C_1$ | First integration → slope | — |
| $EI \, v = \iint M(x) \, dx \, dx + C_1 x + C_2$ | Second integration → deflection | — |
| $\theta_{B/A} = \int_A^B \frac{M}{EI} \, dx$ | Moment-area theorem 1: change in slope | Hibbeler, 10th ed. §12.3 |
| $t_{B/A} = \int_A^B \frac{M}{EI} \cdot \bar{x} \, dx$ | Moment-area theorem 2: tangential deviation | Hibbeler, 10th ed. §12.3 |

$$
EI \frac{d^2 v}{dx^2} = M(x)
$$

$$
\theta_{B/A} = \int_A^B \frac{M(x)}{EI} \, dx
$$

$$
t_{B/A} = \int_A^B \frac{M(x)}{EI} \, \bar{x} \, dx
$$

**Standard deflection formulas (for superposition — memorize these):**

| Loading | Max deflection $\delta_{max}$ | Location |
|---------|-------------------------------|----------|
| Simply supported, midpoint load $P$ | $\dfrac{PL^3}{48EI}$ | Midspan |
| Simply supported, uniform load $w$ | $\dfrac{5wL^4}{384EI}$ | Midspan |
| Cantilever, tip load $P$ | $\dfrac{PL^3}{3EI}$ | Free end |
| Cantilever, uniform load $w$ | $\dfrac{wL^4}{8EI}$ | Free end |
| Simply supported, off-center load $P$ at $a$ from left | $\dfrac{Pb(L^2 - b^2)^{3/2}}{9\sqrt{3}EIL}$ | At $x = \sqrt{(L^2-b^2)/3}$ |

**Variable legend:**

| Symbol | Description | SI Units | US Customary Units |
|--------|-------------|----------|--------------------|
| $v(x)$ | Vertical deflection (+ upward) | mm | in |
| $v' = dv/dx$ | Slope (rotation of elastic curve) | rad | rad |
| $v'' = d^2v/dx^2$ | Curvature ≈ $M/(EI)$ | rad/mm | rad/in |
| $M(x)$ | Bending moment at position $x$ | N·mm; kN·m | kip·in |
| $E$ | Young's modulus | MPa | ksi |
| $I$ | Second moment of area | mm⁴ | in⁴ |
| $EI$ | Flexural rigidity | N·mm² | kip·in² |
| $L$ | Beam span | mm | in |
| $P$ | Concentrated load | N; kN | kip |
| $w$ | Distributed load per unit length | N/mm; kN/m | kip/ft |
| $\theta_{B/A}$ | Angle of elastic curve at B relative to tangent at A | rad | rad |
| $t_{B/A}$ | Tangential deviation of B from tangent at A | mm | in |

---

## 4. Derivation

### 4-1. The Elastic Curve Differential Equation

**Step 1:** From the curvature-moment relation in Topic 01-D: $\kappa = 1/\rho = M/(EI)$.

**Step 2:** For small deflections and slopes ($|v'| \ll 1$), the exact curvature formula simplifies:
$$\kappa = \frac{v''}{(1 + v'^2)^{3/2}} \approx v''$$

**Step 3:** Therefore: $EI \, v'' = M(x)$.

*This is the governing ODE of the elastic curve. The sign depends on the sign convention: with $x$ to the right and $v$ positive upward, and positive $M$ causing concave-up bending, the equation is $EI v'' = M(x)$.*

**Step 4:** Differentiate once more — $EI v''' = dM/dx = V(x)$ (shear). Differentiate again — $EI v'''' = dV/dx = -w(x)$ (load intensity, negative for downward).

### 4-2. Double Integration Method

**Step 1:** Write $M(x)$ as a function of $x$. If the moment diagram has different expressions in different regions of the beam (e.g., under a point load), write separate $M_i(x)$ expressions per region, using **Macaulay brackets** $\langle x - a \rangle$ to handle discontinuities cleanly.

**Step 2:** Integrate once to get $EI v' = \int M(x) dx + C_1$.

**Step 3:** Integrate again to get $EI v = \iint M(x) dx + C_1 x + C_2$.

**Step 4:** Apply **boundary conditions** to find $C_1$ and $C_2$:
- Pinned or roller support: $v = 0$.
- Fixed support: $v = 0$ **and** $v' = 0$.
- Free end: $v''= 0$ (moment = 0) and $v''' = 0$ (shear = 0).

### 4-3. Moment-Area Theorems

These theorems provide a **geometric interpretation** of integration without explicitly performing the algebra.

**Theorem 1:** The change in slope between two points A and B on the elastic curve equals the area of the $M/(EI)$ diagram between A and B:
$$\theta_{B/A} = \int_A^B \frac{M}{EI} \, dx = \text{Area of } M/(EI) \text{ diagram from A to B}$$

**Theorem 2:** The tangential deviation $t_{B/A}$ (vertical distance from B to the tangent drawn at A) equals the **first moment** of the $M/(EI)$ area between A and B, taken about the vertical line at B:
$$t_{B/A} = \int_A^B \frac{M}{EI} \cdot \bar{x} \, dx = \text{(Area of } M/EI \text{ from A to B)} \times \bar{x}_{B}$$

where $\bar{x}_B$ is the distance from the centroid of the $M/(EI)$ area to point B.

*Note: $t_{B/A} \neq t_{A/B}$ in general — the order matters.*

**Applying to a simply supported beam with midpoint load $P$:**
By symmetry, the slope at midspan is zero. The tangential deviation of the support (A) from the midspan tangent gives the midspan deflection:
$$\delta_{midspan} = t_{A/mid} = \frac{1}{\,EI} \cdot \left(\frac{L/2 \times PL/4}{2}\right) \cdot \frac{2L/3 \cdot \frac{1}{2}}{?}$$
(This becomes the standard formula $\delta = PL^3/(48EI)$ after careful computation.)

### 4-4. Superposition

Within the elastic range, deflections from multiple load cases may be added algebraically:
$$v_{total}(x) = v_1(x) + v_2(x) + \cdots$$

Tabulated solutions for common beam cases (simply supported, cantilever) are available in all textbooks and the AISC Steel Construction Manual (Part 3). Superposition requires that the total load still satisfies small-deflection assumptions.

---

## 5. Design / Application Procedure

1. **Identify the beam type** (simply supported, cantilever, propped, etc.) and loading.
2. **For simple cases:** Look up the standard formula in beam tables and apply directly.
3. **For complex loading:** Apply superposition — decompose the load into components matching table entries, compute each deflection, and sum.
4. **For non-standard cases:** Use double integration or moment-area.
   - Write $M(x)$ for each segment (use Macaulay brackets if possible).
   - Integrate twice; apply boundary conditions to find constants.
5. **Check against code limit:** ASCE 7-22 §L (Table L-1):
   - Live load only: $\Delta_L \leq L/360$ (floors), $L/240$ (roof).
   - Total load (dead + live): $\Delta_{D+L} \leq L/240$ (floors), $L/180$ (roof).
6. **For indeterminate beams:** Deflection calculations feed back into compatibility equations — see Topic 03.

---

## 6. Worked Example

**Problem:** A simply supported steel beam, $L = 8$ m, $EI = 50 \times 10^{12}$ N·mm² ($= 50,000$ kN·m²), carries: (a) a uniform load $w = 15$ kN/m over the full span, and (b) a midpoint concentrated load $P = 40$ kN. Using superposition, find the maximum deflection at midspan and check against $\delta_{allow} = L/360$.

**Given:**
- $L = 8{,}000$ mm
- $EI = 50 \times 10^{12}$ N·mm²
- $w = 15$ N/mm; $P = 40{,}000$ N
- $\delta_{allow} = L/360 = 8000/360 = 22.2$ mm

**Solution:**

1. **Deflection due to uniform load $w$:**
$$\delta_w = \frac{5wL^4}{384 EI} = \frac{5 \times 15 \times (8000)^4}{384 \times 50 \times 10^{12}}$$
$$= \frac{5 \times 15 \times 4.096 \times 10^{15}}{1.92 \times 10^{16}} = \frac{3.072 \times 10^{17}}{1.92 \times 10^{16}} = 16.0 \text{ mm}$$

2. **Deflection due to midpoint load $P$:**
$$\delta_P = \frac{PL^3}{48 EI} = \frac{40{,}000 \times (8000)^3}{48 \times 50 \times 10^{12}}$$
$$= \frac{40{,}000 \times 5.12 \times 10^{11}}{2.4 \times 10^{15}} = \frac{2.048 \times 10^{16}}{2.4 \times 10^{15}} = 8.53 \text{ mm}$$

3. **Total midspan deflection by superposition:**
$$\delta_{total} = \delta_w + \delta_P = 16.0 + 8.53 = 24.5 \text{ mm}$$

4. **Serviceability check:**
$$\delta_{total} = 24.5 \text{ mm} > \delta_{allow} = 22.2 \text{ mm} \quad \text{✗  FAILS}$$

The beam deflects too much. To fix this, $EI$ must be increased (use a stiffer or deeper section) by the ratio $24.5/22.2 = 1.10$, so the required $EI = 55 \times 10^{12}$ N·mm².

**Result:** Midspan deflection = 24.5 mm, which exceeds the $L/360 = 22.2$ mm limit by 10%. A heavier (stiffer) section is required.

---

## 7. Common Mistakes & Pitfalls

- **Mistake 1 — Forgetting consistent units:** If $w$ is in N/mm but $L$ is in m, the formula $5wL^4/(384EI)$ gives a nonsensical result. Convert everything to N and mm (or kN and m) before substituting.
- **Mistake 2 — Wrong sign convention in double integration:** Choose upward $v$ as positive and sagging $M$ as positive, then $EI v'' = M$. If you flip any sign, double-check both integrations and boundary conditions.
- **Mistake 3 — Applying superposition for nonlinear problems:** Superposition requires linear elastic behavior ($\sigma < \sigma_y$ everywhere). It also requires **small deflections**. For large deflections or plastic hinge behavior, superposition is invalid.
- **Mistake 4 — Applying the wrong standard formula:** The midpoint-load formula $PL^3/(48EI)$ is for a load at the center of a simply supported beam. For a cantilever or an off-center load, different formulas apply.
- **Mistake 5 — Ignoring the boundary condition at a location of zero moment:** At a pin or roller support, both $v = 0$ and $M = 0$ hold. At the free end of a cantilever, $M = 0$ and $V = 0$, not $v = 0$.

---

## 8. Connections to Other Topics

- **Topic 01-D (Pure Bending):** The ODE $EIv'' = M(x)$ comes directly from the curvature-moment relation derived in Topic 01-D. Beam deflections are cumulative bending strains.
- **Topic 03 (Indeterminate Analysis):** The compatibility conditions in the force method and three-moment equation rely on deflection formulas computed using the methods taught here.
- **Topic 04 (Matrix Analysis):** The stiffness matrix of a beam element is derived from the elastic curve ODE — the $12EI/L^3$ terms come from double-integrating the cubic elastic curve shape functions.
- **Topic 05 (Structural Dynamics):** The natural frequency of a beam is $\omega_n = \sqrt{k/m}$ where $k = 48EI/L^3$ (midpoint stiffness) — directly from $\delta = PL^3/(48EI)$.
- **Topic 06 (Steel Design):** Serviceability deflection checks are a required design step per AISC 360 Commentary and ASCE 7-22 §L.

---

## 9. Further Reading

| Resource | Where to look |
|----------|--------------|
| Hibbeler, *Mechanics of Materials*, 10th ed. | Chapter 12: Deflection of Beams and Shafts |
| Beer, Johnston & DeWolf, *Mechanics of Materials*, 7th ed. | Chapter 9: Deflection of Beams |
| Gere & Goodno, *Mechanics of Materials*, 9th ed. | Chapter 9: Deflections of Beams |
| AISC *Steel Construction Manual*, 16th ed. | Part 3: Design of Flexural Members (beam tables) |
| ASCE 7-22 | Appendix C: Serviceability Considerations |

---

## 10. Quick Self-Check

- [ ] I can state the elastic curve ODE $EIv'' = M(x)$ and explain where it comes from.
- [ ] I can apply double integration with boundary conditions to find $v(x)$ for a simply supported beam with a uniform load.
- [ ] I can state both moment-area theorems and explain what $\theta_{B/A}$ and $t_{B/A}$ represent geometrically.
- [ ] I can use superposition to find midspan deflection of a beam with multiple loads.
- [ ] I know the common deflection formulas ($PL^3/48EI$, $5wL^4/384EI$, $PL^3/3EI$) and when each applies.

---

*Created by Structural Engineering Tutor • 2026-03-14*
