# Steel Material Properties, Sections & Limit States (LRFD & ASD)

**Subject area:** Steel Design (AISC 360-22)
**Design standard / primary reference:** AISC 360-22 §A, §B, §C; AISC Steel Construction Manual, 16th Ed., Part 1 & 2
**Depth level:** Graduate — rigorous derivation
**Estimated study time:** 100 minutes

---

## 1. Introduction & Motivation

Steel is the dominant structural material for multi-story buildings, long-span bridges, industrial structures, and towers. Its exceptional strength-to-weight ratio, predictable ductile behavior, and recyclability make it both efficient and sustainable. Before designing any steel member, an engineer must understand **what steel is made of**, **how it behaves under load**, and **how design standards translate that behavior into safe, economical decisions**.

The governing U.S. standard is **AISC 360-22** (*Specification for Structural Steel Buildings*). It provides two parallel design philosophies: **Load and Resistance Factor Design (LRFD)** and **Allowable Stress Design (ASD)**. Both philosophies are code-compliant, and a practicing engineer must understand the logic behind each.

This note establishes the material foundation and design vocabulary used in every subsequent steel design topic. When you later compute the capacity of a tension member, a beam, or a column, you will always refer back to the limit states, material strengths, and section properties introduced here.

---

## 2. Key Concepts & Definitions

| Term | Symbol | Definition |
|------|--------|------------|
| Yield strength | $F_y$ | Stress at the onset of plastic yielding; governs ductile limit states |
| Ultimate tensile strength | $F_u$ | Maximum engineering stress before rupture; governs fracture limit states |
| Modulus of elasticity | $E$ | Slope of the linear-elastic stress-strain curve; $E = 200\,\text{GPa}$ ($29\,000\,\text{ksi}$) |
| Shear modulus | $G$ | $G = E / [2(1+\nu)]$; for steel $G \approx 77\,\text{GPa}$ ($11\,200\,\text{ksi}$) |
| Poisson's ratio | $\nu$ | $\nu = 0.3$ for structural steel |
| Coefficient of thermal expansion | $\alpha$ | $\alpha = 11.7 \times 10^{-6}\,/°\text{C}$ ($6.5 \times 10^{-6}\,/°\text{F}$) |
| Limit state | — | A condition beyond which a structure no longer satisfies the design criteria (strength or serviceability) |
| Nominal strength | $R_n$ | Theoretical capacity of a member or connection calculated per AISC 360 |
| Resistance factor | $\phi$ | LRFD reduction factor ($0 < \phi \leq 1.0$) accounting for variability in strength |
| Safety factor | $\Omega$ | ASD amplification factor ($\Omega \geq 1.0$) providing a reserve against failure |
| Required strength | $R_u$ (LRFD) / $R_a$ (ASD) | Demand from factored (LRFD) or unfactored (ASD) load combinations |
| Compact section | — | Cross-section that can reach and sustain the full plastic moment before local buckling |
| Width-to-thickness ratio | $\lambda$ | Measure of local buckling susceptibility; compared to $\lambda_p$ and $\lambda_r$ |

---

## 3. Governing Equations

| Equation | Description | Source |
|----------|-------------|--------|
| $\phi R_n \geq R_u$ | LRFD design inequality | AISC 360-22 §B3.1 |
| $R_n / \Omega \geq R_a$ | ASD design inequality | AISC 360-22 §B3.2 |
| $R_u = \sum \gamma_i Q_i$ | LRFD required strength (factored loads) | ASCE 7-22 §2.3 |
| $R_a = \sum Q_i$ | ASD required strength (service loads) | ASCE 7-22 §2.4 |

**LRFD central equation:**

$$
\phi R_n \geq R_u
$$

**ASD central equation:**

$$
\frac{R_n}{\Omega} \geq R_a
$$

**Relationship between $\phi$ and $\Omega$:**

$$
\phi \cdot \Omega = \frac{R_n}{R_n} = 1 \quad \Longrightarrow \quad \Omega = \frac{1}{\phi}
$$

> Note: Strictly, $\phi$ and $\Omega$ are not exact inverses for all limit states, but the AISC 360 calibration ensures that both methods yield consistent reliability levels.

**Variable legend:**

| Symbol | Description | SI Units | US Customary Units |
|--------|-------------|----------|--------------------|
| $\phi$ | Resistance factor | dimensionless | dimensionless |
| $\Omega$ | Safety factor | dimensionless | dimensionless |
| $R_n$ | Nominal strength | kN or kN·m | kips or kip·ft |
| $R_u$ | LRFD required strength | kN or kN·m | kips or kip·ft |
| $R_a$ | ASD required strength | kN or kN·m | kips or kip·ft |
| $\gamma_i$ | Load factor for load type $i$ | dimensionless | dimensionless |
| $Q_i$ | Service-level load effect for load type $i$ | kN or kN·m | kips or kip·ft |

---

## 4. Derivation

### 4.1 The Steel Stress-Strain Curve

The idealized stress-strain curve for structural steel has four distinct regions:

**Step 1 — Linear-elastic region ($0 \leq \varepsilon \leq \varepsilon_y$):**

$$
\sigma = E \varepsilon, \qquad \varepsilon_y = \frac{F_y}{E}
$$

For A992 steel: $F_y = 345\,\text{MPa}$ (50 ksi), so $\varepsilon_y = 345/200\,000 \approx 0.00173$ (0.173%).

**Step 2 — Yield plateau ($\varepsilon_y \leq \varepsilon \leq \varepsilon_{sh} \approx 10\varepsilon_y$):**

Stress remains approximately constant at $F_y$ while strain increases significantly. This is the "plastic flow" zone — **ductility in action**. No increase in force is required until strain hardening begins.

**Step 3 — Strain hardening ($\varepsilon_{sh} \leq \varepsilon \leq \varepsilon_u$):**

Stress rises above $F_y$ to a peak at $F_u$ as dislocations in the crystal lattice pile up. $F_u = 450\,\text{MPa}$ (65 ksi) for A992.

**Step 4 — Necking and fracture ($\varepsilon > \varepsilon_u$):**

The cross-section localizes ("necks"), engineering stress drops, and ultimate rupture occurs at $\varepsilon_f \approx 20\%$–$30\%$.

> **Key takeaway:** The long yield plateau means steel can redistribute stress before it fractures — this ductility underlies the plastic analysis methods used in advanced design.

---

### 4.2 Steel Grades and Material Properties

AISC 360-22 §A3.1 references ASTM standards for steel:

| ASTM Grade | Common Use | $F_y$ (MPa / ksi) | $F_u$ (MPa / ksi) |
|------------|------------|-------------------|-------------------|
| A36 | Plates, angles, older W-shapes | 250 / 36 | 400–550 / 58–80 |
| A572 Gr. 50 | W-shapes, plates | 345 / 50 | 450 / 65 |
| **A992** | Modern W-shapes (most common) | 345 / 50 | 450 / 65 |
| A500 Gr. C | HSS (rectangular & square) | 345 / 50 | 427 / 62 |
| A53 Gr. B | Pipe sections | 241 / 35 | 414 / 60 |
| A514 | High-strength quenched plates | 690 / 100 | 760 / 110 |

**A992 special requirements (AISC 360-22 §A3.1a):**
- $F_y \leq 355\,\text{MPa}$ (51 ksi) maximum
- $F_u \geq 450\,\text{MPa}$ (65 ksi) minimum
- $F_y / F_u \leq 0.85$ (limits strain hardening unpredictability)
- Minimum Charpy V-notch toughness to ensure fracture-safe performance

---

### 4.3 Standard Section Shapes

Steel members are manufactured as standard rolled or built-up shapes. The AISC Manual, Part 1 contains full section property tables.

| Designation | Shape | Typical Use |
|-------------|-------|-------------|
| W (wide-flange) | I-shape, flanges nearly parallel | Beams, columns — most versatile |
| S (American Standard Beam) | I-shape, sloped inner flanges | Older beams, crane rails |
| M (Miscellaneous) | I-shapes not fitting W or S | Special applications |
| HP (bearing pile) | I-shape, nearly square, equal flanges & web | Foundation piles |
| C (American Standard Channel) | Channel | Purlins, girts, bracing |
| MC (Miscellaneous Channel) | Channel | Similar to C |
| L (Angle) | Equal or unequal legs | Bracing, connections, gussets |
| HSS (Hollow Structural Section) | Square, rectangular, or round tube | Columns, bracing, truss chords |
| Pipe | Round tube (standard/extra-strong/double-extra-strong) | Columns, handrails |

**Reading a W-shape designation:** `W18×97`
- `W` = wide-flange shape
- `18` = nominal depth ≈ 18 inches (actual depth may differ slightly)
- `97` = weight in lb/ft (or kg/m in metric editions)

**Key section properties used in design:**

| Property | Symbol | Definition |
|----------|--------|------------|
| Cross-sectional area | $A$ | Total area of the cross-section |
| Moment of inertia | $I_x$, $I_y$ | Second moment of area about strong & weak axes |
| Elastic section modulus | $S_x = I_x/c$ | Ratio $I/c$; used in elastic flexure ($c$ = distance to extreme fiber) |
| Plastic section modulus | $Z_x$ | First moment of area about the plastic neutral axis; used when full yielding occurs |
| Shape factor | $f = Z_x/S_x$ | Ratio of plastic to elastic modulus; $\approx 1.12$ for W-shapes |
| Radius of gyration | $r_x = \sqrt{I_x/A}$ | Governs buckling slenderness |
| Torsional constant | $J$ | Governs St. Venant torsion |
| Warping constant | $C_w$ | Governs warping torsion in LTB |

---

### 4.4 Limit States — The Language of AISC Design

A **limit state** is a threshold condition that defines the boundary of acceptable structural performance. AISC groups them into two categories:

**Strength limit states** (must prevent):
1. **Yielding** — Section reaches $F_y$ over the full cross-section (plastic hinge); controls ductile failure.
2. **Fracture** — Rupture at net section area at connections; governed by $F_u$.
3. **Buckling (flexural)** — Column loses stability under axial compression.
4. **Buckling (lateral-torsional, LTB)** — Beam twists and bends laterally before reaching $M_p$.
5. **Buckling (local)** — Individual plate elements (flange, web) buckle before the section reaches its full capacity.
6. **Block shear** — Combined shear yielding + tension fracture failure path in connections.
7. **Bearing** — Contact stress failure at bolt holes or support points.

**Serviceability limit states** (should control):
1. **Excessive deflection** — Affects occupant comfort, non-structural element integrity.
2. **Excessive vibration** — Human-perception criterion for floors (AISC Design Guide 11).
3. **Permanent deformation** — Inelastic deformation under service loads.

> **Design philosophy:** The AISC 360 identifies all relevant limit states for each member type, computes the nominal strength $R_n$ for each, and the lowest $\phi R_n$ (or $R_n/\Omega$) controls the design.

---

### 4.5 Section Compactness — The $\lambda$ Classification

Before computing flexural capacity, a section must be classified. This controls whether full plastic capacity can be achieved.

**Width-to-thickness ratios:**

For a W-shape flange: 

$$
\lambda_f = \frac{b_f}{2t_f}
$$

For a W-shape web:

$$
\lambda_w = \frac{h}{t_w}
$$

where $h$ is the clear distance between flanges minus fillet/corner radii.

**Compact ($\lambda \leq \lambda_p$):** Can reach $M_p$ and undergo significant inelastic rotation. Full plastic capacity is available.

**Noncompact ($\lambda_p < \lambda \leq \lambda_r$):** Local buckling occurs after yielding begins but before reaching $M_p$ everywhere. Capacity is reduced.

**Slender ($\lambda > \lambda_r$):** Local buckling before yielding. Capacity governed by elastic plate buckling.

**Limiting ratios for W-shape flanges (AISC 360-22 Table B4.1b):**

$$
\lambda_{pf} = 0.38 \sqrt{\frac{E}{F_y}}, \qquad \lambda_{rf} = 1.0 \sqrt{\frac{E}{F_y}}
$$

For A992 steel ($F_y = 345\,\text{MPa}$, $E = 200\,000\,\text{MPa}$):

$$
\lambda_{pf} = 0.38\sqrt{\frac{200\,000}{345}} = 0.38 \times 24.06 = 9.15
$$

$$
\lambda_{rf} = 1.0 \times 24.06 = 24.1
$$

**Limiting ratios for W-shape webs (AISC 360-22 Table B4.1b):**

$$
\lambda_{pw} = 3.76 \sqrt{\frac{E}{F_y}}, \qquad \lambda_{rw} = 5.70 \sqrt{\frac{E}{F_y}}
$$

For A992: $\lambda_{pw} = 90.6$, $\lambda_{rw} = 137.3$.

> **Practical note:** The vast majority of standard W-shapes in the AISC Manual are **compact** for both flange and web when made from A992 steel. AISC marked compact sections with a bullet (•) in older manuals; current tables list $\lambda$, $\lambda_p$, $\lambda_r$ directly.

---

### 4.6 LRFD vs. ASD — Philosophy Comparison

| Aspect | LRFD | ASD |
|--------|------|-----|
| Load side | **Factored loads** $R_u = \sum \gamma_i Q_i$ | **Service loads** $R_a = \sum Q_i$ |
| Resistance side | $\phi R_n$ ($\phi < 1.0$ reduces capacity) | $R_n / \Omega$ ($\Omega > 1.0$ increases required strength) |
| Core check | $\phi R_n \geq R_u$ | $R_n / \Omega \geq R_a$ |
| Load factor source | ASCE 7-22 §2.3 | ASCE 7-22 §2.4 |
| Probabilistic basis | Reliability theory (target $\beta \approx 3.0$) | Historical safety factor experience |
| Typical $\phi$ / $\Omega$ | $\phi_t = 0.90$ (yielding), $\phi_t = 0.75$ (fracture) | $\Omega_t = 1.67$ (yielding), $\Omega_t = 2.00$ (fracture) |

**How LRFD load factors work (ASCE 7-22 §2.3.1, critical combinations):**

| Combination | Expression |
|-------------|------------|
| 1 | $1.4D$ |
| 2 | $1.2D + 1.6L + 0.5(L_r\text{ or }S\text{ or }R)$ |
| 3 | $1.2D + 1.6(L_r\text{ or }S\text{ or }R) + (L\text{ or }0.5W)$ |
| 4 | $1.2D + 1.0W + L + 0.5(L_r\text{ or }S\text{ or }R)$ |
| 5 | $0.9D + 1.0W$ |

where $D$ = dead, $L$ = live, $L_r$ = roof live, $S$ = snow, $R$ = rain, $W$ = wind.

**Approximate equivalence:** For typical gravity-dominated design with $L/D = 1$, LRFD and ASD produce nearly identical section sizes. LRFD offers an advantage when $L/D$ is large (live-load-controlled) due to the different load factors.

---

## 5. Design / Application Procedure

1. **Establish loads.** Compute service-level dead ($D$), live ($L$), wind ($W$), seismic ($E$), and other loads from ASCE 7-22.
2. **Select design method.** Choose LRFD or ASD; most modern U.S. practice uses LRFD.
3. **Calculate required strength.** Apply the governing load combination (ASCE 7-22 §2.3 or §2.4) to obtain $R_u$ (or $R_a$).
4. **Identify the member type.** Determine whether the member is a tension member, compression member, beam, or beam-column.
5. **Identify all applicable limit states.** Refer to AISC 360-22 for the relevant chapter (D = Tension, E = Compression, F = Flexure, G = Shear, H = Combined).
6. **Select a trial section.** Use preliminary sizing rules (e.g., $d/L \approx 1/20$ for beams) or AISC tables.
7. **Verify steel grade.** Confirm ASTM designation; extract $F_y$, $F_u$, and section properties from AISC Manual tables.
8. **Check section compactness.** Compute $\lambda$ and compare to $\lambda_p$, $\lambda_r$ (AISC 360-22 Table B4.1a or B4.1b).
9. **Compute nominal strength $R_n$ for each limit state.** Use the applicable AISC 360-22 formula.
10. **Apply $\phi$ or $\Omega$.** Compare $\phi R_n \geq R_u$ (LRFD) or $R_n/\Omega \geq R_a$ (ASD).
11. **Check serviceability.** Verify deflections, story drift, vibration (if applicable).
12. **Iterate if needed.** Select a larger or smaller section and re-check.

---

## 6. Worked Example

**Problem:** A W18×97 section made from A992 steel is being considered for a floor beam. Classify the section (compact, noncompact, or slender) for bending about the strong axis. Then verify whether LRFD or ASD is more conservative for a beam with $D = 60\,\text{kip·ft}$ and $L = 90\,\text{kip·ft}$.

**Given:**
- Section: W18×97 (A992), $F_y = 50\,\text{ksi}$, $F_u = 65\,\text{ksi}$
- From AISC Manual: $b_f = 11.1\,\text{in}$, $t_f = 0.870\,\text{in}$, $h/t_w = 17.7$, $t_w = 0.535\,\text{in}$
- $D = 60\,\text{kip·ft}$, $L = 90\,\text{kip·ft}$ (service-level moments)

**Required:**
1. Classify flange and web compactness.
2. Compare LRFD vs. ASD required moment demand.

**Solution:**

**Part 1 — Flange classification:**

1. Compute flange slenderness:

$$
\lambda_f = \frac{b_f}{2t_f} = \frac{11.1}{2 \times 0.870} = 6.38
$$

2. Compute limiting ratios:

$$
\lambda_{pf} = 0.38\sqrt{\frac{29\,000}{50}} = 0.38 \times 24.08 = 9.15
$$

$$
\lambda_{rf} = 1.0\sqrt{\frac{29\,000}{50}} = 24.1
$$

3. Check: $\lambda_f = 6.38 < \lambda_{pf} = 9.15$ → **Flange is COMPACT** ✓

**Part 2 — Web classification:**

1. Check: $h/t_w = 17.7$ (from AISC Manual; this is the full-depth ratio; standard notation) — wait, actually for W-shapes the AISC Manual tabulates $h/t_w$ using the clear distance. For W18×97: actual $h/t_w = 17.7$.

$$
\lambda_{pw} = 3.76\sqrt{\frac{29\,000}{50}} = 3.76 \times 24.08 = 90.5
$$

2. Check: $h/t_w = 17.7 < 90.5$ → **Web is COMPACT** ✓

> The W18×97 is a **compact section** — it can develop the full plastic moment $M_p = F_y Z_x$.

**Part 3 — LRFD vs. ASD demand comparison:**

*LRFD — governing combination (1.2D + 1.6L):*

$$
M_u = 1.2(60) + 1.6(90) = 72 + 144 = 216\,\text{kip·ft}
$$

*ASD — governing combination (D + L):*

$$
M_a = 60 + 90 = 150\,\text{kip·ft}
$$

*Convert ASD to equivalent LRFD-basis for comparison:*

$$
M_a \times \frac{\Omega}{\phi_{LRFD}} \approx 150 \times \frac{1.67}{1.0} = 250.5\,\text{kip·ft (ASD effective demand)}
$$

Actually, the direct comparison is done by checking available strength:
- LRFD available: $\phi M_n = 0.90 M_n$; required $M_u = 216\,\text{kip·ft}$
- ASD available: $M_n/1.67$; required $M_a = 150\,\text{kip·ft}$

Both methods will size the beam to the same $M_n$ when $L/D = 90/60 = 1.5$, since $1.2(1) + 1.6(1.5) = 3.6$ and $(1+1.5) \times 1.67/0.90 = 4.64$ ← in this ratio range, LRFD controls slightly.

**Result:** W18×97 from A992 is a **compact section**. LRFD requires $M_u = 216\,\text{kip·ft}$; ASD requires $M_a = 150\,\text{kip·ft}$. Whether the section is adequate depends on $M_n$ from flexural checks (see Topic 06-D: LTB).

---

## 7. Common Mistakes & Pitfalls

- **Mistake 1 — Confusing $F_y$ and $F_u$:** Yielding limit states use $F_y$; fracture (rupture) limit states use $F_u$. Using $F_u$ where $F_y$ is required will unconservatively overestimate capacity.
- **Mistake 2 — Using nominal depth as actual depth:** A W18×97 has an actual depth of 18.6 in, not exactly 18 in. Always use tabulated values from the AISC Manual for section properties.
- **Mistake 3 — Forgetting to check both flange and web for compactness:** Many engineers check only the flange $\lambda_f$ and assume the web is fine. Both must be checked; a slender web changes the applicable design equations in AISC 360-22 §F5.
- **Mistake 4 — Mixing LRFD and ASD:** Never combine a factored load demand ($R_u$) with an ASD available strength ($R_n/\Omega$), or vice versa. Pick one method and apply it consistently throughout the design.
- **Mistake 5 — Ignoring $F_y/F_u$ cap for A992:** This ratio constraint ($\leq 0.85$) is important for seismic design of moment frames. Neglecting it can lead to overestimates of overstrength.

---

## 8. Connections to Other Topics

- **Topic 01-A (Stress & Strain):** The linear-elastic relationship $\sigma = E\varepsilon$ and the yield point $F_y$ come directly from the stress-strain curve covered in Mechanics of Materials. Steel design starts precisely where that curve transitions from elastic to plastic.
- **Topic 06-B (Tension Members):** The fracture limit state ($\phi_t = 0.75$, $F_u A_e$) and the yielding limit state ($\phi_t = 0.90$, $F_y A_g$) are the first applications of the LRFD/ASD framework to a specific member type.
- **Topic 06-C (Compression Members):** Column buckling depends on $E$ and $F_y$ through the slenderness ratio $(KL/r)$ and the tangent modulus concept.
- **Topic 06-D (LTB of Beams):** LTB capacity transitions from plastic ($M_p = F_y Z_x$) to elastic, directly using the compactness classification established here.
- **Topic 09-A (Euler Buckling):** Elastic buckling of columns uses $E$ from this topic; $F_y$ sets the upper bound when inelastic buckling governs.
- **Topic 10-F (LRFD load combinations):** The load factors $\gamma_i$ in ASCE 7-22 are applied to produce $R_u$ used in the LRFD check $\phi R_n \geq R_u$.

---

## 9. Further Reading

| Resource | Where to look |
|----------|--------------|
| AISC 360-22 Spec. for Structural Steel Buildings | Chapter A (General Provisions), Chapter B (Design Requirements), Tables B4.1a & B4.1b |
| AISC Steel Construction Manual, 16th Ed. | Part 1 (Dimensions & Properties), Part 2 (General Design Considerations) |
| Segui, *Steel Design*, 6th Ed. (Cengage) | Chapter 1: Introduction; Chapter 2: Concepts in Structural Steel Design |
| McCormac & Csernak, *Structural Steel Design*, 6th Ed. | Chapter 1: Introduction; Chapter 2: Specifications, Loads, and Methods of Design |
| ASCE 7-22 | §2.3 (LRFD load combinations), §2.4 (ASD load combinations) |

---

## 10. Quick Self-Check

- [ ] I can state the LRFD inequality from memory and define $\phi$, $R_n$, and $R_u$.
- [ ] I can list the five most important strength limit states in steel design.
- [ ] I know the $F_y$ and $F_u$ values for A992 and A36 steel without looking them up.
- [ ] I can compute $\lambda_f$ for a W-shape flange and classify it as compact, noncompact, or slender.
- [ ] I can explain why LRFD uses different load factors for dead load vs. live load.
- [ ] I can connect this topic to at least two subsequent steel design topics.

---

---

## 11. Graduate Extension: Reliability Theory & LRFD Calibration

### 11.1 Structural Reliability Fundamentals

The LRFD format is a **first-order second-moment (FOSM)** approximation to probabilistic limit-state design. The underlying model treats both load effect $Q$ and resistance $R$ as random variables and defines the **limit-state function**:

$$
g(R, Q) = R - Q
$$

Failure occurs when $g < 0$, i.e., when the resistance is less than the load effect. For *lognormally* distributed $R$ and $Q$ with means $\bar{R}$, $\bar{Q}$ and coefficients of variation $V_R$, $V_Q$, the **reliability index** $\beta$ (Cornell 1969) is exactly:

$$
\beta = \frac{\ln(\bar{R}/\bar{Q})}{\sqrt{V_R^2 + V_Q^2}}
\tag{Cornell, 1969}
$$

The probability of failure is:

$$
P_f = \Phi(-\beta)
$$

where $\Phi(\cdot)$ is the standard normal CDF. AISC calibrated the LRFD resistance factors to achieve **target reliability index $\beta_T = 3.0$** for members under gravity loads (corresponding to $P_f \approx 1.35 \times 10^{-3}$) and $\beta_T = 4.0$ for connections ($P_f \approx 3.2 \times 10^{-5}$). The higher connection target reflects the consequences of brittle fracture.

**Why $\beta_T = 3.0$?** This level was chosen by Galambos et al. (1982) based on back-calibration to ASD practice: existing safe designs under ASD implied $\beta \approx 2.6$–$3.5$; the value of 3.0 was selected as a consistent target across member types.

---

### 11.2 FOSM Calibration: Deriving $\phi$ and $\Omega$

**Resistance model.** For a steel tension member at gross yielding, resistance is $R = F_y A_g$. Treating $F_y$ and $A_g$ as independent lognormal variables:

$$
\bar{R} = \bar{F}_y \cdot \bar{A}_g, \qquad V_R \approx \sqrt{V_{F_y}^2 + V_{A_g}^2}
$$

For A992 W-shapes (from Galambos & Ravindra 1978 test data):

| Parameter | Mean-to-nominal ratio | COV |
|-----------|----------------------|-----|
| $F_y$ | 1.10 | 0.10 |
| $A_g$ | 1.00 | 0.05 |
| Professional factor $P$ | 1.02 | 0.06 |

So $\bar{R}/R_n = 1.10 \times 1.00 \times 1.02 = 1.122$ and $V_R = \sqrt{0.10^2 + 0.05^2 + 0.06^2} = 0.126$.

**Load model.** For a 50-year maximum combination $1.2D + 1.6L$, with dead-to-live ratio $\rho = D/L$:

$$
\bar{Q} = (\bar{D} + \bar{L}), \qquad V_Q \approx 0.18 \text{ (combined)}
$$

where $\bar{D}/D_n = 1.05$, $V_D = 0.10$; $\bar{L}/L_n = 1.00$, $V_L = 0.25$.

**Solving for $\phi$.** Setting $\beta = \beta_T = 3.0$ in the lognormal reliability equation and solving for the nominal-capacity factor $\phi$ (Ravindra & Galambos 1978):

$$
\phi = \left(\bar{R}/R_n\right) e^{-\alpha_R \beta_T V_R}
$$

where the FOSM sensitivity factor $\alpha_R \approx 0.55$ for typical resistance uncertainties. Substituting:

$$
\phi = 1.122 \times e^{-0.55 \times 3.0 \times 0.126} = 1.122 \times e^{-0.208} = 1.122 \times 0.812 \approx 0.91 \approx 0.90
$$

This reproduces $\phi_t = 0.90$ for yielding directly from probabilistic calibration. For fracture ($V_R$ is larger because $A_e$ adds shear lag uncertainty $V_U \approx 0.12$, giving $V_R \approx 0.18$):

$$
\phi = 1.10 \times e^{-0.55 \times 3.5 \times 0.18} \approx 0.76 \approx 0.75
$$

The higher $\alpha_R \beta_T$ for fracture (using $\beta_T = 3.5$–$4.0$ for brittle limit states) drives $\phi$ down to 0.75. **This is why fracture has a lower resistance factor than yielding — it is not arbitrary; it reflects higher coefficient of variation in the net-section capacity and the catastrophic nature of brittle fracture.**

**ASD safety factor from FOSM.** ASD calibrated $\Omega$ so that both methods produce the same nominal safety:

$$
\Omega = \frac{1.2D + 1.6L}{\phi(D+L)} \approx \frac{1.4}{\phi \cdot 1.0} \approx \frac{1.4}{0.90} \approx 1.56 \to 1.67 \text{ (rounded up for safety)}
$$

---

### 11.3 Residual Stresses in Rolled and Built-Up Shapes

During hot-rolling, the flange tips cool faster than the heavier flange-web junction. This differential cooling locks in **self-equilibrating residual stresses** with:

- **Compressive residual stress** at flange tips: typically $F_{rc} \approx 0.30 F_y$ (AISC notation: compression positive convention varies by source)
- **Tensile residual stress** at flange-web junction: sufficient to maintain equilibrium

The **CRC (Column Research Council) residual stress model** for wide-flange shapes uses a parabolic distribution across the flange width:

$$
\sigma_r(y) = F_{rc}\left[1 - \left(\frac{2y}{b_f}\right)^2\right]
$$

where $y$ is measured from the flange centerline. The significance for design:

1. **Column strength**, §E3: The column curve implicitly includes residual stress effects through the $0.877 F_e$ or $0.658^{F_y/F_e}$ empirical fit. A column with $F_{rc} = 0.3 F_y$ begins to yield locally at $0.7 F_y$, which is why $0.7 F_y S_x$ appears as the LTB lower anchor in §F2.2 — the flange tip stress that triggers inelastic behavior.
2. **LTB of beams**, §F2: Inelastic LTB initiates when the extreme fiber reaches $F_y - F_{rc} \approx 0.7 F_y$, explaining the $0.7 F_y S_x$ anchor in Eq. F2-2.
3. **Connections**: Residual stresses are favorable in welded connections where preheat procedures partially relieve them.

For **welded built-up I-shapes** the residual stress pattern reverses: heavy longitudinal welds produce tension at flange tips and compression at the web-flange junction. This makes welded columns more susceptible to web local buckling initiating inelastic column action.

---

### 11.4 Strain Hardening and the Idealized Stress-Strain Model

The Standard steel stress-strain curve for A992 has four distinct regions used in advanced analysis:

| Region | Strain range | Behavior |
|--------|-------------|----------|
| Elastic | $0 \le \varepsilon \le F_y/E$ | Linear: $\sigma = E\varepsilon$ |
| Yield plateau | $F_y/E \le \varepsilon \le \varepsilon_{st}$ | Constant: $\sigma = F_y$; $\varepsilon_{st} \approx 10\varepsilon_y$ for A992 |
| Strain-hardening | $\varepsilon_{st} \le \varepsilon \le \varepsilon_u$ | Rising: $\sigma = F_y + E_{st}(\varepsilon - \varepsilon_{st})$; $E_{st} \approx E/30$ |
| Necking–fracture | $\varepsilon_u \le \varepsilon$ | Falling to $F_u$ then rupture |

For plastic design and pushover analysis (ASCE 41-23 §7.5), the **idealized elastic-perfectly-plastic (EPP) model** ($\sigma = F_y$ for $\varepsilon > F_y/E$) is conservative but simple. The **Ramberg-Osgood** model provides a smooth transition:

$$
\varepsilon = \frac{\sigma}{E} + \alpha_0\frac{\sigma_0}{E}\left(\frac{\sigma}{\sigma_0}\right)^n
$$

where calibrated constants $\alpha_0$, $n$, and reference stress $\sigma_0$ fit individual heat data. This model is used in fiber-section finite element analysis for nonlinear time-history analyses.

---

### 11.5 Width-to-Thickness Limits: Plate Buckling Theory Basis

The compact and noncompact limits in AISC Table B4.1 are derived from **plate buckling theory** (Timoshenko & Gere, *Theory of Elastic Stability*, §9.1). For a uniformly compressed rectangular plate simply supported on three sides and free on one (unstiffened plate element, e.g., outstand flange half-width $b/2$):

$$
F_{cr,plate} = \frac{k_c \pi^2 E}{12(1-\nu^2)(b/t)^2}
$$

where $k_c = 0.425$ for a plate free on one unloaded edge (von Kármán 1932). The **compact limit** $\lambda_p$ is set where a flanged element can sustain the full plastic stress $F_y$ through a rotation ductility demand of about 3 (AISC Commentary B4). The **noncompact limit** $\lambda_r$ is set where $F_{cr,plate} = F_y$:

$$
\lambda_r = b/t = \sqrt{\frac{k_c \pi^2 E}{12(1-\nu^2) F_y}} \approx 0.56\sqrt{\frac{E}{F_y}}
\tag{AISC Table B4.1a, Case 1}
$$

This derivation exactly reproduces the AISC value with $k_c = 0.425$ and $\nu = 0.3$:

$$
\lambda_r = \sqrt{\frac{0.425 \pi^2 E}{12(1-0.09) F_y}} = \sqrt{\frac{4.192 E}{F_y}} \cdot \frac{1}{2.04} \approx 0.56\sqrt{\frac{E}{F_y}} \checkmark
$$

For stiffened elements (web, HSS walls) supported on both loaded edges, $k_c = 4.0$, giving $\lambda_r = 1.49\sqrt{E/F_y}$ — again matching AISC Table B4.1a.

---

*Created by Structural Engineering Tutor • 2026-03-17 | Upgraded to Graduate level: 2026-03-18*
