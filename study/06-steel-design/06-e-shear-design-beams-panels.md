# Shear Design of Beams & Panels

**Subject area:** Steel Design (AISC 360-22)
**Design standard / primary reference:** AISC 360-22 §G2; AISC Steel Construction Manual, 16th Ed., Part 3
**Depth level:** Undergraduate — accessible
**Estimated study time:** 55 minutes

---

## 1. Introduction & Motivation

In most everyday steel beam designs, flexure governs: the engineer selects a W-shape based on required moment capacity, checks deflection, and moves on. Shear rarely controls for standard spans of 15–40 ft under typical floor or roof loads. Yet shear failures are far more dangerous than flexural failures because they can be sudden and brittle — a web that buckles or shears through near a support gives very little visible warning before collapse. This is why every beam must be checked for shear, even if the check is expected to be routine. The cases where shear does govern — short, heavily loaded transfer beams; beams with large notched (coped) ends; plate girders with slender webs; beams supporting heavy machinery or crane loads — represent exactly the high-consequence situations where a missed check is catastrophic.

The physical picture of shear in a steel I-beam is straightforward. The internal shear force $V$ at any cross-section is resisted almost entirely by the web. The two flanges, being positioned far from the neutral axis and having very small area in the direction of shear, contribute less than 5% of the total shear resistance. Within the web, classical beam theory (Hibbeler, *Mechanics of Materials*, Ch. 7) shows that the shear stress $\tau = VQ/(It_w)$ varies parabolically from zero at the flange tips to a maximum at the neutral axis — but for compact W-shapes this variation is modest (10–15%), so AISC rationally idealizes the web as a uniform shear panel with area $A_w = d \cdot t_w$. This idealization is both simple and slightly conservative, making it ideal for everyday design.

Two fundamentally different failure modes compete in a steel web. When the web is stocky (low $h/t_w$), shear yielding governs: the web reaches its yield shear stress $\tau_y \approx 0.6F_y$ uniformly, and the full plastic shear capacity is developed. When the web is slender (high $h/t_w$), the thin plate buckles in shear before it can yield, in the same way a slender column buckles before reaching its squash load. AISC 360-22 Chapter G handles both regimes — and the inelastic transition between them — through a single compact formula, $V_n = 0.6F_yA_wC_{v1}$, where the web shear coefficient $C_{v1}$ smoothly transitions from 1.0 (full yield) down toward the elastic-buckling limit. For plate girders with transverse stiffeners, post-buckling diagonal tension-field action is also available through the companion coefficient $C_{v2}$ in §G2.2. These shear-buckling concepts directly connect to the plate-buckling theory introduced in the Stability topic (Area 9-E) and to the web slenderness limits already encountered in flexural LTB design (Area 6-D, §F2).

---

## 2. Key Concepts & Definitions

| Term | Symbol | Definition |
|------|--------|------------|
| Web area | $A_w$ | Effective shear area of the web: $A_w = d \cdot t_w$ (overall depth × web thickness) |
| Web height | $h$ | Clear distance between flanges less fillets: for rolled shapes tabulated in AISC Manual; for built-up sections measured between fillet welds |
| Web slenderness | $h/t_w$ | Dimensionless ratio controlling the shear-buckling regime; tabulated in AISC Manual Table 1-1 |
| Shear plate-buckling coefficient | $k_v$ | Factor accounting for panel aspect ratio $a/h$; $k_v = 5.34$ for unstiffened webs (no transverse stiffeners, or $a/h > 3$) |
| Web shear coefficient (yielding) | $C_{v1}$ | Ratio of critical shear stress to $0.6F_y$; used in §G2.1 (no tension-field action) |
| Web shear coefficient (post-buckling) | $C_{v2}$ | Extended coefficient including tension-field action (diagonal strut mechanism); used in §G2.2 |
| Nominal shear strength | $V_n$ | Predicted maximum shear the section can carry before failure |
| LRFD resistance factor | $\phi_v$ | 1.00 for most W-shapes with compact webs (§G2.1(a)); 0.90 for all other cases |
| ASD safety factor | $\Omega_v$ | 1.50 for compact W-shape webs (§G2.1(a)); 1.67 for all other cases |
| Transverse stiffener | — | Vertical plate welded to the web perpendicular to the beam axis; subdivides the web into panels, increases $k_v$, and enables tension-field action |
| Panel aspect ratio | $a/h$ | Ratio of stiffener spacing $a$ to clear web height $h$; controls $k_v$ |
| Tension-field action | — | Post-buckling diagonal tensile stress band that develops in a stiffened web panel after the web buckles in shear; analogous to the tension diagonal of a Pratt truss |

---

## 3. Governing Equations

| Equation | Description | Source |
|----------|-------------|--------|
| $V_n = 0.6 F_y A_w C_{v1}$ | Nominal shear strength — no tension-field action | AISC 360-22 §G2.1 Eq. (G2-1) |
| $A_w = d \cdot t_w$ | Effective web shear area | AISC 360-22 §G2.1 |
| $C_{v1} = 1.0$ when $h/t_w \le 1.10\sqrt{k_v E/F_y}$ | No web buckling — full shear yielding | AISC 360-22 §G2.1.1(a) |
| $C_{v1} = \dfrac{1.10\sqrt{k_v E/F_y}}{h/t_w}$ when $1.10\sqrt{k_v E/F_y} < h/t_w \le 1.37\sqrt{k_v E/F_y}$ | Inelastic shear buckling regime | AISC 360-22 §G2.1.1(b) |
| $C_{v1} = \dfrac{1.51 k_v E}{(h/t_w)^2 F_y}$ when $h/t_w > 1.37\sqrt{k_v E/F_y}$ | Elastic shear buckling regime | AISC 360-22 §G2.1.1(c) |
| $k_v = 5 + \dfrac{5}{(a/h)^2}$ | Shear-buckling coefficient for stiffened web | AISC 360-22 §G2.1.1 |
| $k_v = 5.34$ | Shear-buckling coefficient for unstiffened web ($a/h > 3$ or no stiffeners) | AISC 360-22 §G2.1.1 |
| $\phi_v V_n \ge V_u$ (LRFD) | Design criterion | AISC 360-22 §B3.1 |
| $V_n/\Omega_v \ge V_a$ (ASD) | Design criterion | AISC 360-22 §B3.2 |

**Primary design equation:**

$$
\boxed{V_n = 0.6\,F_y\,A_w\,C_{v1}}
\tag{AISC 360-22 Eq. G2-1}
$$

**Web shear coefficient — three regimes:**

$$
C_{v1} = \begin{cases}
1.0 & \text{if } \dfrac{h}{t_w} \le 1.10\sqrt{\dfrac{k_v E}{F_y}} \\[10pt]
\dfrac{1.10\sqrt{k_v E/F_y}}{h/t_w} & \text{if } 1.10\sqrt{\dfrac{k_v E}{F_y}} < \dfrac{h}{t_w} \le 1.37\sqrt{\dfrac{k_v E}{F_y}} \\[10pt]
\dfrac{1.51\,k_v\,E}{(h/t_w)^2\,F_y} & \text{if } \dfrac{h}{t_w} > 1.37\sqrt{\dfrac{k_v E}{F_y}}
\end{cases}
\tag{AISC 360-22 §G2.1.1}
$$

**Special case — compact I-shapes (§G2.1(a)):**

$$
\text{If } \frac{h}{t_w} \le 2.24\sqrt{\frac{E}{F_y}}: \quad \phi_v = 1.00,\quad \Omega_v = 1.50,\quad C_{v1} = 1.0
$$

For A992 steel ($F_y = 50$ ksi): $2.24\sqrt{29{,}000/50} = 53.9$ → **virtually all standard W-shapes qualify.**

**Variable legend:**

| Symbol | Description | SI Units | US Customary Units |
|--------|-------------|----------|--------------------|
| $V_n$ | Nominal shear strength | kN | kips |
| $V_u$ | Required shear strength (LRFD, factored) | kN | kips |
| $V_a$ | Required shear strength (ASD, service) | kN | kips |
| $F_y$ | Yield stress of steel | MPa | ksi |
| $E$ | Modulus of elasticity (29,000 ksi / 200,000 MPa) | MPa | ksi |
| $A_w$ | Web shear area $= d \cdot t_w$ | mm² | in² |
| $d$ | Overall depth of section | mm | in |
| $t_w$ | Web thickness | mm | in |
| $h$ | Clear web height between flanges (less fillets for rolled shapes) | mm | in |
| $k_v$ | Shear plate-buckling coefficient (dimensionless) | — | — |
| $C_{v1}$ | Web shear coefficient (dimensionless, $0 < C_{v1} \le 1$) | — | — |
| $a$ | Clear spacing between transverse stiffeners | mm | in |
| $\phi_v$ | LRFD resistance factor for shear (1.00 or 0.90) | — | — |
| $\Omega_v$ | ASD safety factor for shear (1.50 or 1.67) | — | — |

---

## 4. Derivation

### Background: Shear stress in an I-shaped cross-section

**Step 1 — Shear flow in the web.**
From Mechanics of Materials (Hibbeler, *Mechanics of Materials*, Ch. 7), the shear stress at a point in the web is:

$$
\tau = \frac{VQ}{It_w}
$$

where $V$ is the internal shear force, $Q$ is the first moment of area above the point of interest, $I$ is the moment of inertia of the full section, and $t_w$ is the web thickness. For an I-shaped section, $Q$ varies parabolically through the web, reaching a maximum at the neutral axis. Numerically, more than **95%** of the total shear force is resisted by the web in a typical W-shape, so it is rational to assign all shear resistance to the web.

**Step 2 — Uniform shear idealization.**
For most standard W-shapes the variation of $\tau$ across the web depth is small (less than 10–15%). AISC therefore replaces the parabolic distribution with an equivalent uniform shear stress acting over the web area:

$$
\tau_{avg} = \frac{V}{A_w}, \qquad A_w = d \cdot t_w
$$

This is a conservative simplification — the actual peak shear stress at the neutral axis is slightly higher, but using $A_w = d \cdot t_w$ (overall depth, not just clear web $h$) compensates.

**Step 3 — Shear yield limit.**
The web yields in shear when the average shear stress reaches the shear yield stress $\tau_y$. From the von Mises criterion:

$$
\tau_y = \frac{F_y}{\sqrt{3}} \approx 0.577\,F_y
$$

AISC rounds this to **0.6 $F_y$** (a slight overestimate of 3.9%, conservative enough for design). The nominal shear strength based on full web yielding is therefore:

$$
V_{n,yield} = \tau_y \cdot A_w = 0.6\,F_y\,A_w
$$

**Step 4 — Web shear buckling.**
A slender web acts like a thin plate loaded in shear along its edges. Classical plate-buckling theory (Timoshenko & Gere, *Theory of Elastic Stability*, §9) gives the elastic critical shear stress:

$$
\tau_{cr} = k_v \frac{\pi^2 E}{12(1-\nu^2)} \left(\frac{t_w}{h}\right)^2
$$

For steel ($\nu = 0.3$): $12(1-\nu^2) \approx 10.92$, so:

$$
\tau_{cr} \approx \frac{k_v \cdot 0.904 \cdot E}{(h/t_w)^2}
$$

AISC approximates this coefficient as **1.51** (slightly conservative), giving the elastic-buckling branch of $C_{v1}$.

**Step 5 — Inelastic buckling transition.**
When the theoretical $\tau_{cr}$ falls between $0.8\tau_y$ and $\tau_y$, the web buckles inelastically. AISC defines two slenderness thresholds that bound this transition:

- **Lower bound** ($C_{v1} = 1.0$): buckling stress exceeds yield — no buckling before yielding:
  $$\frac{h}{t_w} \le 1.10\sqrt{\frac{k_v E}{F_y}}$$

- **Upper bound** (elastic buckling governs):
  $$\frac{h}{t_w} > 1.37\sqrt{\frac{k_v E}{F_y}}$$

Between these two limits a linear interpolation in $h/t_w$ (equivalent to $C_{v1}$ proportional to $1/(h/t_w)$) handles the inelastic transition, producing the second branch of $C_{v1}$.

**Step 6 — Incorporating $C_{v1}$ into a single equation.**
Combining Steps 3–5, the nominal strength for all slenderness regimes is written compactly as:

$$
V_n = 0.6\,F_y\,A_w\,C_{v1}
$$

where $C_{v1} \in (0, 1]$ reduces the full-yield capacity when web buckling is the controlling limit state.

**Step 7 — Shear-buckling coefficient $k_v$.**
The coefficient $k_v$ depends on the boundary conditions of the web panel. For a panel of height $h$ and width $a$ (between stiffeners) with simply supported edges:

$$
k_v = 5.34 + \frac{4}{(a/h)^2} \quad (a/h \le 1) \qquad \text{or} \qquad k_v = 4 + \frac{5.34}{(a/h)^2} \quad (a/h > 1)
$$

AISC 360-22 §G2.1.1 consolidates this as:

$$
k_v = 5 + \frac{5}{(a/h)^2}
$$

which is a reasonable approximation across the full range of $a/h$. For $a/h > 3$ or no stiffeners, $k_v = 5.34$ (pure shear buckling of a long panel).

**Step 8 — Tension-field action (§G2.2, Cv2).**
After the web buckles in shear, it does not immediately fail. Instead, a diagonal tension field (analogous to the tension diagonal of a Pratt truss) develops between vertical stiffeners and the flanges. This post-buckling strength is captured by the coefficient $C_{v2}$ in §G2.2:

$$
V_n = 0.6\,F_y\,A_w\left[C_{v2} + \frac{1-C_{v2}}{1.15\sqrt{1+(a/h)^2}}\right]
\tag{AISC 360-22 Eq. G2-7}
$$

The first term is the web-buckling contribution; the second term is the tension-field increment. Tension-field action is only permitted for doubly-symmetric I-shapes, channels, and similar sections with adequate flange stiffness — **not** for end panels, panels with large holes, or when $2A_w/(A_{fc}+A_{ft}) > 2.5$ (flanges too small to anchor the tension field).

---

## 5. Design / Application Procedure

**LRFD checklist — Shear design of an I-shaped beam (AISC 360-22 §G2)**

1. **Determine required shear.** From structural analysis under LRFD load combinations (ASCE 7-22 §2.3), find the maximum factored shear $V_u$ (kips).

2. **Identify section properties.** From the AISC Manual Table 1-1, record: overall depth $d$, web thickness $t_w$, web slenderness $h/t_w$, and compute $A_w = d \cdot t_w$.

3. **Check §G2.1(a) — compact web (most W-shapes on A992).**
   $$\text{If } \frac{h}{t_w} \le 2.24\sqrt{\frac{E}{F_y}}: \quad \phi_v = 1.00,\quad C_{v1} = 1.0$$
   For $F_y = 50$ ksi: limit = 53.9. Check AISC Manual column "$\phi_v V_n$" directly — for most W-shapes this is pre-tabulated.

4. **If §G2.1(a) does not apply**, determine $k_v$:
   - No transverse stiffeners (or $a/h > 3$): $k_v = 5.34$
   - With stiffeners: $k_v = 5 + 5/(a/h)^2$

5. **Compute $C_{v1}$** using the three-regime table in §3 above (compare $h/t_w$ to $1.10\sqrt{k_v E/F_y}$ and $1.37\sqrt{k_v E/F_y}$). Set $\phi_v = 0.90$, $\Omega_v = 1.67$.

6. **Compute nominal shear strength:**
   $$V_n = 0.6\,F_y\,A_w\,C_{v1}$$

7. **Apply resistance factor and check demand:**
   $$\phi_v V_n \ge V_u \quad \text{(LRFD)}$$
   $$\frac{V_n}{\Omega_v} \ge V_a \quad \text{(ASD)}$$
   If the check fails, try the next heavier section in the same depth family and repeat from Step 2.

8. **Check if transverse stiffeners are required (§G2.2).** Stiffeners are needed when the calculated $C_{v1}$ (without stiffeners, $k_v = 5.34$) falls below 1.0 **and** you wish to use tension-field action to boost capacity. Stiffeners are also required per §G2.2 whenever:
   $$\frac{h}{t_w} > 2.46\sqrt{\frac{E}{F_y}}$$
   For $F_y = 50$ ksi: limit = $2.46 \times 24.08 = 59.2$. Most standard W-shapes have $h/t_w < 59.2$, so no stiffeners are required for shear.

9. **If using tension-field action (§G2.2):** Verify stiffener proportions, compute $C_{v2}$, and use Eq. (G2-7) from §4, Step 8. This is typically reserved for plate girders.

10. **Document.** Record $\phi_v V_n$, the controlling limit state (yielding or buckling), and whether stiffeners are required. For plate girders also check bearing stiffeners at supports (§G6).

---

## 6. Worked Example

**Problem:** A simply supported steel beam spanning 18 ft carries a uniform dead load of 3 kip/ft and a uniform live load of 5 kip/ft. A trial section W24×62 (A992 steel, $F_y = 50$ ksi) has been selected for flexure. Verify that the section is adequate for shear under LRFD. Also perform the ASD check and confirm that transverse stiffeners are not required.

**Given:**
- Span $L = 18$ ft
- $w_D = 3.0$ kip/ft (dead), $w_L = 5.0$ kip/ft (live)
- Section: W24×62, A992 steel
- $F_y = 50$ ksi, $E = 29{,}000$ ksi
- From AISC Manual Table 1-1 for W24×62:
  - $d = 23.7$ in, $t_w = 0.430$ in, $h/t_w = 50.1$, $b_f = 7.04$ in, $t_f = 0.590$ in
- Tabulated $\phi_v V_n = 306$ kips (AISC Manual Part 3, Beam Tables)

**Required:**
1. Maximum factored shear $V_u$ (LRFD)
2. Maximum service shear $V_a$ (ASD)
3. Verify $\phi_v V_n \ge V_u$ and $V_n/\Omega_v \ge V_a$
4. Check whether transverse stiffeners are required

---

**Solution:**

**Step 1 — Factored loads (LRFD, ASCE 7-22 §2.3).**
$$w_u = 1.2\,w_D + 1.6\,w_L = 1.2(3.0) + 1.6(5.0) = 3.6 + 8.0 = 11.6 \text{ kip/ft}$$

Maximum shear at the support of a simply supported beam:
$$V_u = \frac{w_u L}{2} = \frac{11.6 \times 18}{2} = \mathbf{104.4 \text{ kips}}$$

**Step 2 — Service loads (ASD, ASCE 7-22 §2.4).**
$$w_a = w_D + w_L = 3.0 + 5.0 = 8.0 \text{ kip/ft}$$
$$V_a = \frac{w_a L}{2} = \frac{8.0 \times 18}{2} = 72.0 \text{ kips}$$

**Step 3 — Check §G2.1(a): compact web.**
$$2.24\sqrt{\frac{E}{F_y}} = 2.24\sqrt{\frac{29{,}000}{50}} = 2.24 \times 24.08 = 53.9$$
$$\frac{h}{t_w} = 50.1 \le 53.9 \quad \checkmark$$

Since this limit is satisfied: $\phi_v = 1.00$, $\Omega_v = 1.50$, $C_{v1} = 1.0$.

**Step 4 — Compute $A_w$.**
$$A_w = d \cdot t_w = 23.7 \times 0.430 = 10.19 \text{ in}^2$$

**Step 5 — Nominal shear strength.**
$$V_n = 0.6\,F_y\,A_w\,C_{v1} = 0.6 \times 50 \times 10.19 \times 1.0 = \mathbf{305.7 \text{ kips}}$$

*(This matches the tabulated value of 306 kips in the AISC Manual to within rounding.)*

**Step 6 — LRFD shear check.**
$$\phi_v V_n = 1.00 \times 305.7 = 305.7 \text{ kips} \ge V_u = 104.4 \text{ kips} \quad \checkmark$$
Utilization ratio: $104.4/305.7 = \mathbf{34\%}$ → section is **adequate with large reserve** (typical for long spans where flexure governs).

**Step 7 — ASD shear check.**
$$\frac{V_n}{\Omega_v} = \frac{305.7}{1.50} = 203.8 \text{ kips} \ge V_a = 72.0 \text{ kips} \quad \checkmark$$

**Step 8 — Stiffener check.**
For the compact-web case (§G2.1(a)), AISC does not require transverse stiffeners for shear. As an additional confirmation:
$$2.46\sqrt{\frac{E}{F_y}} = 2.46 \times 24.08 = 59.2$$
$$\frac{h}{t_w} = 50.1 < 59.2 \quad \checkmark \quad \text{No stiffeners required.}$$

**Result:** W24×62 (A992) is adequate for shear under both LRFD ($\phi_v V_n = 305.7$ kips $\gg V_u = 104.4$ kips) and ASD ($V_n/\Omega_v = 203.8$ kips $\gg V_a = 72.0$ kips). No transverse stiffeners are required. This confirms the typical design scenario where flexure, not shear, governs W-shape selection on moderate-length spans.

> **Design note — heavier shear demands:** If the span were shorter (say, 8 ft with heavy point loads), $V_u$ could approach or exceed $\phi_v V_n$, and a deeper, heavier section or a plate girder with stiffeners would be required.

---

## 7. Common Mistakes & Pitfalls

- **Mistake 1 — Using $h \cdot t_w$ instead of $d \cdot t_w$ for $A_w$.** AISC 360-22 §G2.1 explicitly defines $A_w = d \cdot t_w$ (using overall depth $d$, not clear web height $h$). Using $h \cdot t_w$ underestimates the web area by roughly 10–15% and gives an unnecessarily conservative answer. Reserve $h$ for computing slenderness ratios $h/t_w$.

- **Mistake 2 — Applying $\phi_v = 1.00$ to all I-shapes.** The enhanced factor $\phi_v = 1.00$ (and $\Omega_v = 1.50$) applies **only** to doubly-symmetric I-shapes satisfying $h/t_w \le 2.24\sqrt{E/F_y}$ per §G2.1(a). Channels, HSS, built-up sections, or any section that fails this limit must use $\phi_v = 0.90$ ($\Omega_v = 1.67$). Applying 1.00 indiscriminately is unconservative.

- **Mistake 3 — Forgetting to check the end panel.** Tension-field action (§G2.2) is **not permitted** in the end panels of a plate girder (the panel adjacent to the end bearing stiffener). The end panel must be designed without tension-field action, using the §G2.1 formula with $k_v = 5.34$ unless a stiffener is placed very close to the support. This is a frequent oversight on plate girder designs.

- **Mistake 4 — Confusing $C_{v1}$ and $C_{v2}$.** $C_{v1}$ (§G2.1) applies when tension-field action is **not** used — it covers both yielding and shear-buckling regimes. $C_{v2}$ (§G2.2) is a related but different coefficient used in the tension-field-action formula for stiffened plate girders. Substituting one for the other leads to significant errors.

- **Mistake 5 — Neglecting combined shear and bending interaction at cope/notch locations.** At coped beam ends, the reduced section depth drastically reduces $A_w$ and the shear capacity. AISC Design Guide 2 provides specific procedures for coped beams; the standard §G2 formula is not directly applicable to notched webs without adjustment.

---

## 8. Connections to Other Topics

- **Mechanics of Materials — E (Transverse Shear Stresses):** The $\tau = VQ/(It)$ formula is the parent equation for everything in §G. Understanding how shear stress is distributed parabolically across the web, and why $A_w = d \cdot t_w$ is an adequate idealization, requires solid grounding in this topic.
- **Structural Stability — E (Local Plate Buckling):** The derivation of $C_{v1}$ in the inelastic and elastic regimes is an application of plate buckling theory. The shear-buckling coefficient $k_v$ plays the same role as the plate-buckling coefficient $k$ in the local buckling of compression flanges.
- **Steel Design — C (Compression Member Design):** The concept of slenderness-controlled capacity — full strength at low slenderness, reduced strength by a transition function, elastic buckling at high slenderness — is structurally identical in column design (KL/r) and shear design ($h/t_w$). Recognizing this parallel accelerates learning both topics.
- **Steel Design — D (Lateral-Torsional Buckling):** LTB and shear buckling are both member-level instabilities. In flexure, the slenderness parameter is $L_b/r_{ts}$; in shear, it is $h/t_w$. Both use a three-regime framework (plastic/inelastic/elastic) and the same $\phi = 0.90$ factor for the non-compact case.
- **Steel Design — F (Beam-Columns):** When a beam carries both moment and shear, the interaction provisions of §H or the web yielding check under combined stresses may be required for very slender webs. In practice this is only relevant for plate girders.
- **Steel Design — G (Connections — Bolted/Welded):** The design shear $V_u$ determined here directly sizes the end-connection (bolt group, weld length) — a natural downstream application of the shear design workflow.

---

## 9. Further Reading

| Resource | Where to look |
|----------|---------------|
| AISC 360-22 Specification for Structural Steel Buildings | Chapter G (Shear); also §B3 (design basis) |
| AISC Steel Construction Manual, 16th Ed. | Part 3 (Beam selection tables, $\phi_v V_n$ column); Part 16A (§G commentary) |
| AISC Design Examples, Vol. 1 (freely downloadable) | Example G.1 (W-shape in shear); Example G.2 (plate girder with stiffeners) |
| Salmon, Johnson & Malhas — *Steel Structures: Design and Behavior*, 5th Ed. | Chapter 11 (Plate girders and shear) |
| Segui — *Steel Design*, 6th Ed. | Chapter 6 (Beams: shear) |
| Timoshenko & Gere — *Theory of Elastic Stability*, 2nd Ed. | §9.1–9.4 (Buckling of plates in shear) |
| Hibbeler — *Mechanics of Materials*, 10th Ed. | Chapter 7 (Transverse shear) |

---

## 10. Quick Self-Check

- [ ] I can state $V_n = 0.6 F_y A_w C_{v1}$ from memory and define every symbol, including what makes up $A_w$.
- [ ] I know the two conditions (§G2.1(a) vs. §G2.1(b)) that determine whether $\phi_v = 1.00$ or $\phi_v = 0.90$.
- [ ] I can identify which of the three $C_{v1}$ regimes applies to a given $h/t_w$ without referring to notes.
- [ ] I understand physically why a slender web buckles in shear before it yields, and why adding stiffeners helps.
- [ ] I can explain tension-field action using the Pratt-truss analogy, and state one condition that prohibits it.
- [ ] I have reproduced the W24×62 worked example from scratch and obtained $\phi_v V_n \approx 306$ kips.
- [ ] I can connect shear design to plate buckling theory (via $k_v$) and to transverse shear stress distribution (via $A_w$).

---

*Created by Structural Engineering Tutor • 2026-03-18*
