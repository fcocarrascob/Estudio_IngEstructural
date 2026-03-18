# Transverse Loading: Shear Stresses in Beams

**Subject area:** Mechanics of Materials  
**Design standard / primary reference:** Hibbeler, *Mechanics of Materials*, 10th ed. — Ch. 7; Beer & Johnston, *Mechanics of Materials*, 7th ed. — Ch. 6  
**Depth level:** Undergraduate — accessible  
**Estimated study time:** 70 minutes

---

## 1. Introduction & Motivation

Topic 01-D showed that bending moments produce normal stresses that vary linearly across the cross-section depth. But in real beams, transverse loads also produce **shear forces** — and these shear forces produce **shear stresses** on horizontal and vertical planes inside the beam. As a dramatic example: a wooden beam, if loaded heavily enough, will sometimes split horizontally along its grain before it fails in bending. This horizontal splitting is driven by **horizontal shear stress**, which has the same magnitude as the vertical shear stress at any point.

The shear formula $\tau = VQ/(Ib)$ gives the shear stress at any point in a cross-section. While shear stresses are often smaller than bending stresses in long beams, they can govern the design of **short, deep beams**, **webs of steel I-sections**, and **built-up sections** (glued or bolted composite beams). In steel design, checking shear in the web is a required limit state per AISC 360 §G.

Understanding the concept of **shear flow** $q = VQ/I$ is also essential for designing the connectors (bolts, welds, nails) that hold built-up sections together.

---

## 2. Key Concepts & Definitions

| Term | Symbol | Definition |
|------|--------|------------|
| Shear force | $V$ | Internal resultant shear force on the cross-section at a given location $x$ |
| First moment of area | $Q$ | $Q = \int_{A'} y \, dA = \bar{y}' A'$; statical moment of the area $A'$ above (or below) the cut point about the neutral axis |
| Shear stress | $\tau$ | Average shear stress on a horizontal plane at distance $y$ from the neutral axis |
| Shear flow | $q$ | Force per unit length: $q = \tau b = VQ/I$; used for connector design in built-up beams |
| Width at cut | $b$ | Width of the cross-section at the point where $\tau$ is computed |
| Neutral axis | N.A. | Axis of zero bending stress (passes through centroid); typically location of maximum shear stress |
| Shear center | S.C. | Point about which a cross-section rotates under a shear force with no twisting; relevant for asymmetric and thin-walled sections |

---

## 3. Governing Equations

| Equation | Description | Source |
|----------|-------------|--------|
| $\tau = VQ / (Ib)$ | Shear formula: average shear stress at a horizontal cut | Hibbeler, 10th ed. Eq. 7-4 |
| $Q = \bar{y}' A'$ | First moment of area above (or below) the cut line | Definition |
| $q = VQ / I$ | Shear flow (force per unit length) | Hibbeler, 10th ed. Eq. 7-6 |
| $q = F / s$ | Connector force per unit length ($F$=connector capacity, $s$=spacing) | Hibbeler, 10th ed. §7.4 |

$$
\tau = \frac{VQ}{Ib}
$$

$$
q = \frac{VQ}{I}
$$

**Variable legend:**

| Symbol | Description | SI Units | US Customary Units |
|--------|-------------|----------|--------------------|
| $\tau$ | Shear stress | MPa | ksi; psi |
| $V$ | Internal shear force at the section | N; kN | lb; kip |
| $Q$ | First moment of area above/below cut | mm³; m³ | in³ |
| $I$ | Second moment of area of entire section about N.A. | mm⁴ | in⁴ |
| $b$ | Width of section at the cut | mm | in |
| $q$ | Shear flow (force per unit length) | N/mm; kN/m | lb/in; kip/ft |
| $\bar{y}'$ | Distance from N.A. to centroid of $A'$ | mm | in |
| $A'$ | Cross-sectional area above (or below) the cut line | mm²; m² | in² |

---

## 4. Derivation

### 4-1. Horizontal Shear Stress — Complementary Shear Law

**Step 1:** Consider two adjacent cross-sections in a beam separated by distance $\Delta x$, with bending moments $M$ and $M + \Delta M$ respectively. The normal stress on any horizontal fiber at height $y$ changes from $\sigma$ to $\sigma + \Delta\sigma$.

**Step 2:** Isolate a horizontal slice of the beam between the two sections, from height $y = y_1$ to the top of the beam (area $A'$). Apply horizontal equilibrium to this slice:

$$\sum F_x = 0: \quad \tau \cdot b \cdot \Delta x = \int_{A'} \Delta\sigma \, dA = \int_{A'} \frac{\Delta M \cdot y}{I} \, dA = \frac{\Delta M}{I} \int_{A'} y \, dA = \frac{\Delta M}{I} Q$$

where $Q = \int_{A'} y \, dA$.

**Step 3:** Divide by $\Delta x$ and use $dM/dx = V$ (from beam equilibrium):
$$\tau \cdot b = \frac{dM}{dx} \cdot \frac{Q}{I} = \frac{VQ}{I}$$

$$\tau = \frac{VQ}{Ib}$$

*Physical interpretation:* This horizontal shear stress is the "longitudinal glue stress" — it acts on horizontal planes inside the beam. By the **complementary shear principle** (equal horizontal and vertical shear stresses at any point), this equals the vertical shear stress.

### 4-2. Shear Stress Distribution in a Rectangular Section

For a rectangle of width $b$ and height $h$, with $y$ measured from the neutral axis:

$$Q = \bar{y}' A' = \left(\frac{h/2 + y}{2}\right) \cdot b \left(\frac{h}{2} - y\right) = \frac{b}{2}\left(\frac{h^2}{4} - y^2\right)$$

$$\tau = \frac{VQ}{Ib} = \frac{V \cdot \frac{b}{2}\left(\frac{h^2}{4} - y^2\right)}{(bh^3/12) \cdot b} = \frac{6V}{bh^3}\left(\frac{h^2}{4} - y^2\right)$$

This is a **parabolic distribution**:
- At the top and bottom ($y = \pm h/2$): $\tau = 0$ (free surfaces have no shear)
- Maximum at the neutral axis ($y = 0$):

$$\tau_{max} = \frac{6V}{bh^3} \cdot \frac{h^2}{4} = \frac{3V}{2bh} = \frac{3V}{2A}$$

The maximum shear stress in a rectangle is **1.5 times** the average $V/A$.

### 4-3. Shear Flow in Built-up Sections

For a built-up beam (boards nailed, bolted, or glued together), the **shear flow** $q = VQ/I$ gives the shear force per unit length on the bonding surface. If connectors (nails, bolts) are spaced at $s$ and each has capacity $F$:
$$q = F/s \quad \Rightarrow \quad s = F/q = FI/(VQ)$$

---

## 5. Design / Application Procedure

1. **Draw the shear diagram** for the beam. Identify the section with maximum shear $V_{max}$.
2. **Compute the moment of inertia $I$** of the entire cross-section about the neutral axis.
3. **Identify the cut location** where shear stress is desired. Determine $b$ at that location.
4. **Compute $Q$**: isolate the area $A'$ above (or below) the cut line, find its centroid $\bar{y}'$ relative to the neutral axis, then $Q = \bar{y}' A'$.
5. **Compute shear stress:** $\tau = VQ/(Ib)$.
6. **For the maximum shear stress:** Usually occurs at the neutral axis. Compute $Q_{max}$ = first moment of the area above the neutral axis.
7. **For built-up beams:** Use shear flow $q = VQ/I$ to find required connector spacing $s = F_{connector}/q$.
8. **Check against allowable values:** For steel, shear yield: $\tau_y = 0.6 F_y$ (AISC 360 §G2 for unstiffened webs).

---

## 6. Worked Example

**Problem:** An I-shaped steel beam (built-up from three plates) carries a shear force $V = 120$ kN. Section: top and bottom flanges each 150 mm × 20 mm; web 260 mm × 10 mm (overall depth = 300 mm). Determine: (a) the maximum shear stress in the web, (b) the shear stress at the flange-web junction, and (c) the shear stress in the flange.

**Given:**
- Flanges: $b_f = 150$ mm, $t_f = 20$ mm (top and bottom)
- Web: $b_w = 10$ mm, $h_w = 260$ mm
- Total depth: $d = 300$ mm → $c = 150$ mm
- $V = 120$ kN $= 120{,}000$ N

**Solution:**

1. **Moment of inertia $I$ (about centroidal horizontal axis — section is symmetric):**
$$I = \frac{b_f d^3}{12} - 2 \times \frac{(b_f - b_w)(h_w)^3}{24}$$

More clearly, using built-up approach:
$$I_{flanges} = 2\left[\frac{150 \times 20^3}{12} + (150 \times 20)(140)^2\right] = 2[100{,}000 + 58{,}800{,}000] = 117{,}800{,}000 \text{ mm}^4$$
$$I_{web} = \frac{10 \times 260^3}{12} = \frac{10 \times 17{,}576{,}000}{12} = 14{,}647{,}000 \text{ mm}^4$$
$$I = 117{,}800{,}000 + 14{,}647{,}000 = 132{,}447{,}000 \approx 132.4 \times 10^6 \text{ mm}^4$$

*(Note: $\bar{y}'$ for each flange from N.A. = $130 + 10 = 140$ mm)*

2. **Shear stress at the flange-web junction** (just inside the web, $b = b_w = 10$ mm):
$$Q_{junction} = A_{flange} \times \bar{y}'_{flange} = (150 \times 20) \times 140 = 420{,}000 \text{ mm}^3$$
$$\tau_{junction} = \frac{VQ}{Ib} = \frac{120{,}000 \times 420{,}000}{132.4 \times 10^6 \times 10} = \frac{5.04 \times 10^{10}}{1.324 \times 10^9} = 38.1 \text{ MPa}$$

3. **Maximum shear stress at the neutral axis** (area above N.A. = top flange + upper half of web):
$$Q_{max} = Q_{flange} + Q_{web\_half} = 420{,}000 + \left(10 \times 130 \times \frac{130}{2}\right) = 420{,}000 + 84{,}500 = 504{,}500 \text{ mm}^3$$
$$\tau_{max} = \frac{VQ_{max}}{Ib_w} = \frac{120{,}000 \times 504{,}500}{132.4 \times 10^6 \times 10} = 45.7 \text{ MPa (at N.A., in web)}$$

4. **Shear stress in the flange** (at flange-web junction, $b = b_f = 150$ mm):
$$\tau_{flange} = \frac{VQ_{junction}}{I \times b_f} = \frac{120{,}000 \times 420{,}000}{132.4 \times 10^6 \times 150} = 2.54 \text{ MPa (much lower)}$$

**Result:** Maximum shear stress = 45.7 MPa at the neutral axis in the web. At the flange-web junction, the web carries 38.1 MPa while the flange carries only 2.54 MPa — shear stress drops sharply as width increases jumping into the wide flange. This illustrates why the **web carries essentially all the shear** in an I-beam.

---

## 7. Common Mistakes & Pitfalls

- **Mistake 1 — Computing $Q$ with the wrong reference area:** $Q$ is the first moment of the area on **one side** of the cut (above or below — same result by symmetry for doubly symmetric sections, but at other cuts, choose one side consistently).
- **Mistake 2 — Using the wrong $b$:** In an I-section at the junction, $b$ changes abruptly. Just **inside the web**, $b = t_w$; just **outside in the flange**, $b = b_f$. These give very different stresses at the same $Q$.
- **Mistake 3 — Thinking maximum shear always occurs at the neutral axis:** This is true for rectangular and most standard sections, but not always. For a T-section, the maximum $\tau$ may occur just below the flange where $Q$ is still large but $b$ is now the narrow web.
- **Mistake 4 — Forgetting the complementary shear:** The horizontal and vertical shear stresses at any internal point are equal in magnitude. The formula gives *both* simultaneously.
- **Mistake 5 — Using the shear formula for circular sections with incorrect $b$:** For circular sections, $b = 2\sqrt{r^2 - y^2}$ varies with $y$. $\tau_{max} = 4V/(3A)$ at the neutral axis for a solid circle.

---

## 8. Connections to Other Topics

- **Topic 01-D (Pure Bending):** Bending stress $\sigma = My/I$ and shear stress $\tau = VQ/Ib$ coexist at most points in a loaded beam. Together, they define the complete stress state at any interior point.
- **Topic 01-G (Combined Loadings):** The combination of bending normal stress and transverse shear stress is exactly the combined loading scenario analyzed with Mohr's circle.
- **Topic 01-H (Mohr's Circle):** At a point in the web of a beam, both $\sigma$ (from bending) and $\tau$ (from shear) act. Mohr's circle transforms these to principal stresses — critical for identifying brittle failure planes.
- **Topic 06 (Steel Design, AISC 360):** Shear design of steel beams (§G) uses $V_n = 0.6 F_y A_w$ for stocky webs, rooted in the shear yield stress of the web material.
- **Topic 07 (Concrete Design, ACI 318):** Shear design of concrete beams is fundamentally about preventing diagonal tension cracking driven by combined normal and shear stresses — the exact situation analyzed with Mohr's circle building on this topic.

---

## 9. Further Reading

| Resource | Where to look |
|----------|--------------|
| Hibbeler, *Mechanics of Materials*, 10th ed. | Chapter 7: Transverse Shear |
| Beer, Johnston & DeWolf, *Mechanics of Materials*, 7th ed. | Chapter 6: Shearing Stresses in Beams |
| Gere & Goodno, *Mechanics of Materials*, 9th ed. | Chapter 5: Stresses in Beams (§5.8–5.10) |
| AISC 360-22 §G | Shear strength of members |

---

## 10. Quick Self-Check

- [ ] I can state the shear formula $\tau = VQ/(Ib)$ and define every symbol.
- [ ] I can explain why shear stress is zero at free surfaces (top and bottom of a beam).
- [ ] I can compute $Q$ for an arbitrary cut location in a standard I-section.
- [ ] I can sketch the shear stress distribution across the depth of a rectangular beam (parabolic) and an I-beam (parabola in web, near-zero in flanges).
- [ ] I can apply the shear flow concept to find the required connector spacing in a built-up beam.

---

*Created by Structural Engineering Tutor • 2026-03-14*
