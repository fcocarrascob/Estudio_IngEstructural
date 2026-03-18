# Welded Connection Design: Fillet Welds, CJP & PJP

**Subject area:** Steel Design (AISC 360-22)
**Design standard / primary reference:** AISC 360-22 §J2; AWS D1.1/D1.1M:2020; Segui, *Steel Design*, 6th ed., Chapter 8
**Depth level:** Graduate — rigorous derivation
**Estimated study time:** 120 minutes

---

## 1. Introduction & Motivation

Welding creates a continuous metallic bond between steel elements by melting base metal and filler metal together. Welds are ubiquitous in fabrication shops — they eliminate bolt holes (which reduce net area), produce airtight joints, and allow clean aesthetics in architectural steel. Moment connections, column base plates, and built-up plate girders all rely primarily on welds.

Unlike bolts, welds are not field-adjustable once placed; quality depends entirely on the welder's skill, the welding procedure specification (WPS), and inspection. From a design standpoint, the engineer must choose the correct weld type for the load path, compute the required weld size and length, and verify that both the weld metal and the adjacent base metal do not fail.

---

## 2. Key Concepts & Definitions

| Term | Symbol | Definition |
|------|--------|------------|
| Fillet weld | — | Triangular cross-section weld at the junction of two surfaces meeting at 90° |
| Complete joint penetration (CJP) | — | Groove weld that extends through the full thickness of the thinner part |
| Partial joint penetration (PJP) | — | Groove weld that does not extend through the full thickness |
| Weld size (fillet) | $a$ (or $w$) | Leg of the equal triangle weld cross-section |
| Effective throat | $t_e$ | Shortest distance from weld root to weld face: $t_e = 0.707a$ for 45° fillet |
| Effective area of weld | $A_w$ | $t_e \times$ effective weld length $L_w$ |
| Electrode classification | $E\!X\!X\!X\!X$ | Designates tensile strength $F_{EXX}$ of deposited weld metal (e.g., E70: $F_{EXX} = 70$ ksi) |
| Nominal weld stress | $F_{nw}$ | $0.60 F_{EXX}$ for fillet and PJP welds in shear |
| Directional strength factor | $1.0 + 0.50\sin^{1.5}\!\theta$ | Increases strength when load is transverse (perpendicular) to weld axis |
| Throat direction angle | $\theta$ | Angle between applied load direction and weld axis ($0°$ = parallel, $90°$ = transverse) |
| Base metal checks | — | Plate areas adjacent to weld must also be checked for yielding and rupture |

---

## 3. Governing Equations

| Equation | Description | Source |
|----------|-------------|--------|
| $t_e = 0.707 \, a$ | Effective throat of 45° fillet weld | AISC 360-22 §J2.2a |
| $R_n = F_{nw} \cdot A_w = 0.60 F_{EXX} \cdot t_e \cdot L_w$ | Nominal fillet weld strength | AISC 360-22 §J2.4 |
| $F_{nw} = 0.60 F_{EXX}\!\left(1.0 + 0.50\sin^{1.5}\!\theta\right)$ | Directional strength increase | AISC 360-22 §J2.4-3 |
| $r_n = 0.60 F_{EXX} \times 0.707 a \times 1.0 = 0.4243 F_{EXX} \, a$ | Strength per unit length, parallel load ($\theta = 0°$) | AISC 360-22 §J2.4 |
| $r_n = 0.60 F_{EXX} \times 0.707 a \times 1.50 = 0.6364 F_{EXX} \, a$ | Strength per unit length, transverse load ($\theta = 90°$) | AISC 360-22 §J2.4 |
| $R_n = F_{nw} \cdot A_w$ | CJP / PJP groove weld (shear on effective area) | AISC 360-22 §J2.1 |

$$
\boxed{
r_n = 0.60 \, F_{EXX} \cdot (0.707 a) \cdot \bigl(1.0 + 0.50\sin^{1.5}\!\theta\bigr)
\qquad \phi = 0.75,\quad \Omega = 2.00
}
$$

**Variable legend:**

| Symbol | Description | SI Units | US Customary |
|--------|-------------|----------|--------------|
| $a$ | Weld leg size (fillet weld) | mm | in |
| $t_e$ | Effective throat | mm | in |
| $L_w$ | Effective weld length | mm | in |
| $F_{EXX}$ | Electrode filler metal tensile strength | MPa | ksi |
| $F_{nw}$ | Nominal weld stress | MPa | ksi |
| $A_w$ | Effective weld area = $t_e \times L_w$ | mm² | in² |
| $\theta$ | Angle between load and weld longitudinal axis | — (degrees) | — (degrees) |
| $\phi$ | Resistance factor for welds = 0.75 | — | — |
| $\Omega$ | Safety factor for welds = 2.00 | — | — |

---

## 4. Derivation

### 4.1 Types of Welds — Visual Summary

```
  Fillet weld             CJP groove weld           PJP groove weld
                          
  ┌─────┐                 ┌─────────────────┐        ┌─────────────────┐
  │     │╲                │░░░░░░░░░░░░░░░░░│        │░░░░░░░░         │
  │plate│ ╲  a (leg)      │ full penetration│        │partial penetr.  │
  │     │  ╲              │░░░░░░░░░░░░░░░░░│        │░░░░░░░░         │
  └─────┘   ╲─────────    └─────────────────┘        └─────────────────┘
    base      weld throat
    plate     = 0.707a
```

### 4.2 Fillet Weld Effective Throat

For a standard 45° isoceles triangle fillet weld with leg size $a$:

$$t_e = a \sin 45° = 0.707 \, a$$

This is the **minimum distance from the root of the weld to the weld face**. It is the effective area for stress calculations because the critical shear plane passes through this throat.

For a fillet weld of leg $a$ and length $L_w$:

$$A_w = t_e \times L_w = 0.707 \, a \times L_w$$

### 4.3 Nominal Fillet Weld Strength

The weld failure plane is always on the effective throat regardless of load direction. The nominal stress is:

$$F_{nw} = 0.60 \, F_{EXX}$$

The factor 0.60 accounts for the shear-dominant failure mode on the inclined throat. Basic strength:

$$R_n = 0.60 \, F_{EXX} \times 0.707 \, a \times L_w \quad (\text{load parallel to weld axis, } \theta = 0°)$$

Per unit length: $r_n = 0.4243 \, F_{EXX} \, a$ kips/in

### 4.4 Directional Strength Increase

When the applied load is transverse (perpendicular) to the weld axis ($\theta = 90°$), laboratory tests show the weld is about 50% stronger because the inclined fracture plane is smaller and the state of stress is more favorable. AISC permits this increase:

$$F_{nw} = 0.60 F_{EXX}\!\left(1 + 0.50 \sin^{1.5}\!\theta\right)$$

| Load direction | $\theta$ | Factor | $r_n / (F_{EXX} \cdot a)$ |
|----------------|----------|--------|--------------------------|
| Parallel (longitudinal) | 0° | 1.00 | 0.4243 |
| 45° | 45° | 1.354 | 0.574 |
| Transverse (perpendicular) | 90° | 1.50 | 0.636 |

**For weld groups with mixed directions** (e.g., angle welded on two sides), AISC §J2.4(b) allows the increased strength on transverse segments provided: the governing failure mode is fracture of all welds simultaneously (not a progressive shear failure). This is conservative in most cases.

### 4.5 CJP and PJP Groove Welds

**CJP groove welds (§J2.1):** The weld penetrates the full thickness. When matching filler metal is used ($F_{EXX} \ge F_y$ of base metal), the weld is stronger than the base metal in all directions. AISC does not require a separate weld strength calculation for CJP in tension/compression — the base metal controls. For shear on the effective area:

$$R_n = 0.60 F_{EXX} \times A_w \quad \phi = 0.80$$

**PJP groove welds (§J2.2):** The effective throat depends on the groove geometry and welding process. For a single bevel groove weld (GMAW process), the effective throat is approximately the specified depth of groove $d - 1/8$ in. For design, shear on the effective area uses the same formula as fillet welds. Tension perpendicular to the weld axis on a PJP is limited by the base metal:

$$R_n = F_{nw} \cdot A_w \quad (\text{shear}), \qquad R_n = 0.6 F_y \cdot A_g \quad (\text{tension, base metal})$$

### 4.6 Weld Size Limits (§J2.2b)

**Minimum fillet weld size** (Table J2.4) — based on thicker of parts joined:

| Thickness of thicker part | Minimum weld size |
|---------------------------|-------------------|
| $t \le 1/4$ in | 1/8 in |
| $1/4 < t \le 1/2$ in | 3/16 in |
| $1/2 < t \le 3/4$ in | 1/4 in |
| $t > 3/4$ in | 5/16 in |

Minimum size ensures sufficient preheat and prevents rapid cooling (hydrogen cracking in HAZ).

**Maximum fillet weld size** (§J2.2b):
- Along edge of material with $t < 1/4$ in: $a_{max} = t$ (weld cannot exceed plate)
- Along edge of material with $t \ge 1/4$ in: $a_{max} = t - 1/16$ in

The 1/16 in set-back ensures the outer edge of the plate is not melted away, leaving a proper "land" for the weld.

### 4.7 Base Metal Checks (§J4)

The plate adjacent to the weld must also be verified:

| Failure mode | Formula | $\phi$ (LRFD) |
|---|---|---|
| Shear yielding on gross area | $R_n = 0.60 F_y A_{gv}$ | 1.00 |
| Shear rupture on net area | $R_n = 0.60 F_u A_{nv}$ | 0.75 |
| Tension yielding | $R_n = F_y A_g$ | 0.90 |
| Tension rupture | $R_n = F_u A_n$ | 0.75 |

For connections where the weld is stronger than the plate (thick plate, small weld), the base metal near the weld is the weak link.

### 4.8 Common Electrode Selection

| Electrode | $F_{EXX}$ | Typical use |
|-----------|----------|-------------|
| E70XX | 70 ksi | A36 and A992 base metal (most connections) |
| E80XX | 80 ksi | A572 Gr 60 steel |
| E90XX – E100XX | 90–100 ksi | A514 and other high-strength steel; special procedures |

Matching electrode means $F_{EXX} / \sqrt{3} \ge 0.6 F_y$ (weld yield strength ≥ plate shear yield). For A36 ($F_y = 36$ ksi), E70 satisfies: $70/\sqrt{3} = 40.4 > 0.6 \times 36 = 21.6$ ksi.

---

## 5. Design / Application Procedure

1. **Identify weld type**: fillet (most common), CJP, or PJP based on structural demand, accessibility, and inspection feasibility.

2. **Select electrode**: E70XX for A36/A992, matching electrode rule.

3. **Determine load direction $\theta$** relative to weld axis. Use $\theta = 0°$ (conservative) unless detail clearly shows a transverse weld direction.

4. **Compute required strength per unit length**:
   $$r_u = \frac{P_u}{L_w} \quad \text{(known length)} \quad \text{or} \quad L_w^{req} = \frac{P_u}{\phi r_n}$$

5. **Choose weld size $a$**:
   $$\phi r_n = 0.75 \times 0.60 F_{EXX} \times 0.707 a \times (1 + 0.50\sin^{1.5}\!\theta)$$
   $$a^{req} = \frac{r_u}{0.75 \times 0.6 F_{EXX} \times 0.707 \times (1 + 0.50\sin^{1.5}\!\theta)}$$

6. **Apply size limits**: $a \ge a_{min}$ (Table J2.4) and $a \le a_{max}$ (§J2.2b).

7. **Check base metal** (§J4): shear yielding and rupture, tension.

8. **Check effective length**: fillet weld minimum effective length $\ge 4a$ and never < 1.5 in (§J2.2b). For end returns or weld terminations: treat return welds as zero-length if < twice the weld size.

---

## 6. Worked Example

**Problem:** A PL 5/8 × 8 (A36, $F_y = 36$ ksi, $F_u = 58$ ksi) tension plate is welded to a support gusset with two longitudinal fillet welds, one on each edge. The plate carries $P_u = 160$ kips (LRFD). Available weld length is $L_w = 6$ in per side (12 in total). Determine the required weld size and check base metal shear.

**Given:**
- Plate: $t = 5/8$ in, width $b = 8$ in
- Load: parallel to weld axis ($\theta = 0°$)
- Electrode E70XX: $F_{EXX} = 70$ ksi
- Two welds, each 6 in long → total $L_w = 12$ in

**Required:** Minimum fillet weld size $a$.

**Solution:**

1. **Weld strength per unit length** (per inch), $\theta = 0°$:

   $$\phi r_n = 0.75 \times 0.60 \times 70 \times 0.707 \times a = 22.27 \, a \text{ kips/in}$$

2. **Required strength per unit length**:

   $$r_u = \frac{P_u}{L_w} = \frac{160}{12} = 13.33 \text{ kips/in}$$

3. **Required weld size**:

   $$a^{req} = \frac{r_u}{\phi r_n / a} = \frac{13.33}{22.27} = 0.599 \text{ in} \approx \frac{5}{8} \text{ in}$$

   Rounding up to nearest 1/16 in: $a = 5/8$ in.

4. **Check maximum weld size** (edge of 5/8-in plate):

   $$a_{max} = t - 1/16 = 5/8 - 1/16 = 9/16 \text{ in} \quad < \quad 5/8 \text{ in}$$
   
   The required size (5/8 in) exceeds the maximum (9/16 in) → **increase weld length or use two-sided 9/16-in welds with longer length.**

   **Try $a = 9/16$ in** (maximum permitted):

   $$\phi r_n = 22.27 \times (9/16) = 22.27 \times 0.5625 = 12.53 \text{ kips/in}$$

   $$L_w^{req} = \frac{160}{12.53} = 12.8 \text{ in} \implies \text{use } 13 \text{ in per pair (6.5 in each side)}$$

5. **Base metal shear check** (plate, gross area in shear along both weld lines):

   $$\phi R_n^{bm} = 1.00 \times 0.60 \times 36 \times (2 \times 13 \times 5/8) = 21.6 \times 16.25 = 351 \text{ kips} \gg 160 \text{ kips} \checkmark$$

**Result:** Use 9/16-in E70 fillet welds, 6.5 in long each side (two welds, 13 in total). Base metal governs with over 2× reserve — weld size is the critical limit state.

---

## 7. Common Mistakes & Pitfalls

- **Forgetting the 0.707 factor:** The strength formula $R_n = 0.60 F_{EXX} \times t_e \times L_w$ requires the effective throat $t_e = 0.707a$. Omitting 0.707 overestimates strength by 41%.

- **Using $\phi = 0.90$ for welds:** Welds use $\phi = 0.75$ throughout (shear fracture mode), not 0.90 which applies to yielding in bending. The difference is significant.

- **Not checking base metal:** The weld metal may be adequate, but the HAZ (heat-affected zone) of the plate can govern, especially for thin plates or high-heat welds. §J4 checks must always accompany §J2.4 checks.

- **Applying directional increase incorrectly:** The directional increase ($1.50\times$ for $\theta = 90°$) applies only to the weld itself — it does NOT apply to the adjacent base metal checks, which use $F_y$ and $F_u$ of the steel plate.

- **Ignoring minimum effective length:** A fillet weld shorter than $4a$ in effective length is unreliable per AISC §J2.2b. Short welds used as end returns (< 2a) are counted as zero.

---

## 8. Connections to Other Topics

- **Bolted connections (06-G):** Welds and bolts can appear in the same connection (shop-welded, field-bolted); generally AISC does not allow them to share load in the same direction unless one draws load plastically before the other engages.
- **Tension member design (06-B):** Welded connections eliminate bolt holes and therefore avoid net section reduction and shear lag penalty (§D3 — $U = 1.0$ for welds when the full section is connected or near-full).
- **Lateral-torsional buckling (06-D):** Plate girders (built-up I-shapes) use longitudinal fillet welds to connect flanges to web — the weld must carry horizontal shear flow $q = VQ/I$, making shear flow design a direct application of this topic.
- **Seismic detailing (11-E):** Seismic critical connections (beam flanges to columns in SMF) require CJP welds with demanding inspection (UT, magnetic particle), controlled toughness ($C_{\nu 1}$ notch toughness), and minimum preheat provisions per AISC 358 and AWS D1.8.

---

## 9. Further Reading

| Resource | Where to look |
|----------|--------------|
| AISC 360-22 | §J2 (Welds), §J4 (Base metal), Table J2.4 (Minimum sizes) |
| AISC Steel Construction Manual, 16th ed. | Part 8 (Design of Welds) |
| AWS D1.1/D1.1M:2020 — Structural Welding Code (Steel) | Section 2 (Design of Welded Connections) |
| Segui, *Steel Design*, 6th ed. | Chapter 8: Welded Connections |
| Lincoln Electric, *The Procedure Handbook of Arc Welding* | Filler metal selection and processes |

---

## 10. Quick Self-Check

- [ ] I can compute the effective throat of a fillet weld from its leg size without looking it up.
- [ ] I know the correct $\phi$ = 0.75 for welds and can apply the directional strength formula for $\theta = 0°$ and $\theta = 90°$.
- [ ] I can determine minimum and maximum fillet weld sizes given plate thickness.
- [ ] I understand what CJP, PJP, and fillet welds are, and when each is typically specified.
- [ ] I can perform a complete weld design check including base metal shear, from given geometry and load.

---

---

## 11. Graduate Extension: Eccentric Weld Groups, Residual Stresses & Weld Fatigue

### 11.1 Instantaneous Center of Rotation (ICR) Method for Eccentric Weld Groups

Just as for bolt groups (§06-G §11.4), the ICR method applies to weld groups under eccentric in-plane shear. The key difference is that welds are **distributed** (continuous) rather than discrete, requiring integration over the weld line.

**Step 1 — Weld load-deformation relationship.** The Lesik-Kennedy (1990) formulation, based on fillet weld tests under combined loading:

$$
r(\Delta, \theta) = r_{ult}(\theta) \cdot f(\Delta / \Delta_{ult})
$$

$$
r_{ult}(\theta) = 0.60 F_{EXX} \cdot 0.707 a \cdot (1 + 0.50\sin^{1.5}\theta)
$$

$$
\Delta_{ult}(\theta) = 0.209(\theta + 2)^{-0.32} \cdot 0.707 a \quad (\text{in})
$$

The deformation function $f(\cdot)$ from Kanvinde & Deierlein (2009) is:

$$
f(\rho) = \rho^{0.32}(1.9 - 0.9\rho) \quad \text{where } \rho = \Delta/\Delta_{ult}
$$

**Step 2 — Compatibility and equilibrium.** Each infinitesimal weld element at distance $r_i$ from the ICR undergoes deformation:

$$
\Delta_i = r_i \cdot \theta_{rot} = \Delta_{max}\frac{r_i}{r_{max}}
$$

The angle between the load and the weld axis at each element varies around the weld perimeter, making $\theta$ position-dependent. The three equilibrium equations:

$$
\int_L r_x(s)\,ds = 0, \quad \int_L r_y(s)\,ds = P, \quad \int_L [r_y(s)\cdot x_i - r_x(s)\cdot y_i]\,ds = P \cdot e_{ICR}
$$

are solved numerically. AISC Manual Table 8-3 through 8-11 tabulate the capacity coefficient $C$ for standard weld groups (C-shaped, L-shaped) as a function of eccentricity $e_x$ (in multiples of bolt pitch or weld length).

**Elastic (vector) method vs. ICR.** The elastic method assumes weld force is proportional to distance from the group centroid and components add vectorially. It is simpler but conservative: for a C-shaped weld group with $e = 5$ in, the ICR method typically gives 20–40% more capacity than the elastic vector method.

---

### 11.2 Residual Stress Field in the Heat-Affected Zone (HAZ)

During welding, the **heat-affected zone (HAZ)** undergoes a complex thermal cycle: rapid heating to near or above $1000°C$, then quenching. This cycle:

1. **Metallurgically alters the base metal:** Grain growth near the fusion line reduces toughness; partial austenitization beyond the HAZ boundary restores grain structure; the region more than ~12 mm from the weld centerline is largely unaffected.

2. **Creates residual stresses:** High tensile residual stress along the weld axis ($\sigma_{res} \approx F_y$) balanced by compressive residual stresses in the base metal outside the HAZ. For a butt weld in a plate:

$$
\sigma_{res,x}(y) \approx F_y \quad |y| < b_{HAZ} \qquad \sigma_{res,x}(y) \approx -F_y\frac{b_{HAZ}}{(W/2 - b_{HAZ})} \quad |y| > b_{HAZ}
$$

where $b_{HAZ} \approx 1.5a$ is the half-width of the tensile residual zone and $W$ is the plate width.

**Structural significance:**
- Tensile residual stresses at the weld are **additive** to applied tension stresses, driving fracture at lower applied loads than expected.
- The HAZ has lower yield strength and toughness than the parent metal due to grain coarsening — this is why AWS D1.1 Clause 4 prescribes minimum preheat temperatures to slow cooling and reduce thermal gradient magnitudes.
- Post-weld heat treatment (PWHT) can relieve 80–90% of residual stresses but is impractical for field connections.

---

### 11.3 Fracture Toughness and CVN Requirements

The design of welded connections in fracture-critical applications (seismic moment frames, bridges) requires assuring adequate **fracture toughness** of both the weld metal and the HAZ.

**Charpy V-Notch (CVN) test.** The CVN test measures energy absorbed by a $10 \times 10$ mm notched specimen at specified temperature. The CVN energy is correlated to the fracture toughness $K_{Ic}$ by the Barsom-Rolfe correlation (1970):

$$
K_{Ic}^2 / E \approx 5 \cdot C_v \quad (\text{upper-shelf region})
$$

$$
K_{Ic} \approx 0.54 C_v - 55 \quad (\text{ksi}\sqrt{\text{in, CVN in ft-lbf, valid for lower shelf}})
$$

**AISC 341-22 and AWS D1.8 requirements for seismic critical connections (SMF):**

| Component | CVN requirement |
|-----------|----------------|
| Electrode deposited metal | $\geq 54$ J (40 ft-lbf) at $-29°C$ ($-20°F$) |
| Heat-affected zone of base metal | $\geq 27$ J (20 ft-lbf) at $-29°C$ |
| Column flange material (Div. I) | AISC A992 with $C_v \geq 27$ J at $-7°C$ (ASTM A6 Supp. S30) |

These requirements developed after the **1994 Northridge earthquake** revealed unexpected brittle fracture of beam-flange CJP welds in Special Moment Frames, which previously had no explicit toughness requirements. Post-Northridge research (SAC Joint Venture, 1996–2000) demonstrated that the combination of high residual stresses, poor CVN weld metal, and strain demand at the column face drove fractures. The design improvements (AISC 358, AWS D1.8) require:
1. Weld access holes to specific geometric tolerances (reducing stress concentration)
2. Back-gouging and re-welding of the weld root (eliminating fusion defects)
3. Minimum CVN as tabulated above
4. Ultrasonic testing (UT) of all CJP welds

---

### 11.4 Weld Fatigue: S-N Curves and Detail Categories

For members subject to **cyclic loading** (crane girders, bridge girders, offshore platforms), the governing limit state shifts from monotonic fracture to **fatigue**. AISC 360-22 Appendix 3 (adopted from AASHTO) classifies fatigue-prone details into categories A through F+ based on their stress-concentration severity:

| Category | Description | Constant amplitude fatigue limit (CAFL) $F_{TH}$ (ksi) | Threshold $F_{TH}$ (MPa) |
|----------|-------------|-------------------------------------------------------|-------------------------|
| A | Plain material away from welds | 24 | 165 |
| B | Continuous longitudinal fillet weld | 16 | 110 |
| C | Transverse stiffener welds | 10 | 69 |
| D | Attachments with $L < 51$ mm | 7 | 48 |
| E | Long attachments, shear connector studs | 4.5 | 31 |
| F | Fillet welds in shear | 8 | 55 |

**S-N equation.** For each category, the allowable stress range $F_{SR}$ at $N$ cycles:

$$
F_{SR} = \left(\frac{C_f}{N}\right)^{1/3} \geq F_{TH}
\tag{AISC 360-22 Appendix 3 Eq. A-3-1}
$$

where $C_f$ is a fatigue constant (tabulated in AISC 360 Table A-3.1) specific to each detail category.

**Design approach.** The required fatigue strength check:

$$
(\Delta f) \leq F_{SR}
$$

where $\Delta f$ is the computed stress range (maximum minus minimum stress, without load factors for fatigue). Note that **compressive stresses can be beneficial**: if the minimum stress is compressive and $|\Delta f| = f_{max} - f_{min} < F_{TH}$, fatigue is not a concern.

**Connection of fatigue to residual stresses.** Because tensile residual stresses at welds are of order $F_y$, crack closure during the compressive phase of a stress cycle may not occur until well into the nominal compressive stress range. This is why the AISC Appendix 3 fatigue checks are based on the full algebraic stress range (positive, ignoring sign), without benefit for nominal compressive stress — the residual stresses keep the crack tip in tension throughout the cycle.

---

### 11.5 Weld Process Engineering: Prequalified Joints and WPS

The **Welding Procedure Specification (WPS)** is the written document that specifies the welding process, base metal, filler metal, joint geometry, preheat, interpass temperature, heat input range, and post-weld treatment for each weld in a fabrication shop. AWS D1.1 Clause 4 requires a WPS for all work.

**Prequalified joints (AWS D1.1 Annex A)** are weld joint configurations for which the WPS need not be qualified by testing, provided the joint geometry, electrode designation, and welding process are all within the prequalified limits. The advantage is time and cost savings; the limitation is that prequalified joints cannot be used outside their tabulated limits without qualification testing.

**Heat input control.** The heat input per unit length:

$$
Q_{heat} = \frac{60 \cdot E \cdot I}{1000 \cdot v} \quad (\text{kJ/mm})
$$

where $E$ is arc voltage (V), $I$ is welding current (A), and $v$ is travel speed (mm/min). **High heat input** (low travel speed) extends the HAZ, reduces cooling rate, and increases grain growth (lower toughness). **Low heat input** increases cooling rate potential for hydrogen cracking in hardenable steels, especially when preheat is inadequate. AWS D1.1 Clause 7.6 prescribes minimum preheat temperatures based on the carbon equivalent (CE) of the steel:

$$
CE = C + \frac{Mn}{6} + \frac{Cr+Mo+V}{5} + \frac{Ni+Cu}{15}
$$

For A992 steel ($CE \approx 0.43$–0.47), minimum preheat is typically $66°$C ($150°$F) for thicknesses above 38 mm (1.5 in).

---

*Created by Structural Engineering Tutor • 2026-03-18 | Upgraded to Graduate level: 2026-03-18*
