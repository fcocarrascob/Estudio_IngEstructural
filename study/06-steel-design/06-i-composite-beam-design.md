# Composite Beam Design

**Subject area:** Steel Design (AISC 360-22)
**Design standard / primary reference:** AISC 360-22 Chapter I; Segui, *Steel Design*, 6th ed., Chapter 9
**Depth level:** Graduate — rigorous derivation
**Estimated study time:** 140 minutes

---

## 1. Introduction & Motivation

A composite beam is formed when a steel section and a concrete slab are mechanically connected so that they act as a single structural unit. Without connection, the steel and concrete slide freely at the interface under load, each bending independently. With headed shear stud anchors (connectors), the interface slip is resisted, and the combined section resists moment far more efficiently — the concrete acts as a wide compression flange and the steel acts as a tension element, maximizing the lever arm between the two resultant forces.

Composite beams are ubiquitous in building floor systems: they reduce steel weight by 25–40% compared to non-composite beams of the same span, and they inherently reduce floor vibrations. The trade-off is the cost of shear stud installation (stud welding) and slightly more complex design checks. AISC 360-22 Chapter I governs the design of composite floor members.

---

## 2. Key Concepts & Definitions

| Term | Symbol | Definition |
|------|--------|------------|
| Composite action | — | Combined bending behavior of steel + concrete achieved through shear connectors |
| Shear connector (headed stud) | — | Steel stud welded to the top flange; transfers horizontal shear at the steel–concrete interface |
| Degree of composite action | $\Sigma Q_n / C_{f,min}$ | Ratio of actual shear connector capacity to minimum required for full composite; ≥ 25% per AISC |
| Full composite | — | Shear connectors transfer the full horizontal shear force; concrete and steel both reach their force capacity |
| Partial composite | — | Fewer studs than full composite; at least 25% of full; intermediate strength and stiffness |
| Effective slab width | $b_{eff}$ | Width of slab on each side of beam centerline contributing to composite action (§I3.1a) |
| Compression force block | $C$ | Resultant compression in concrete at flexural limit state |
| Concrete strength | $f'_c$ | 28-day cylinder compressive strength |
| Modular ratio | $n$ | $E_s / E_c$ (typically 8–9 for normal-weight concrete) |
| Lower-bound moment of inertia | $I_{LB}$ | Transformed $I$ used for deflection in partially composite beams |

---

## 3. Governing Equations

| Equation | Description | Source |
|----------|-------------|--------|
| $b_{eff} = \min\!\bigl(L/8,\; s/2,\; \text{edge dist.}\bigr)$ per side | Effective concrete width each side of beam CL | AISC 360-22 §I3.1a |
| $Q_n = 0.5 A_{sa}\!\sqrt{f'_c E_c} \le R_g R_p A_{sa} F_u$ | Nominal stud strength | AISC 360-22 §I8.2a |
| $C_f = \min(0.85 f'_c A_c,\; A_s F_y)$ | Compression force for full composite | AISC 360-22 §I3.2d |
| $a = \dfrac{C_f}{0.85 f'_c b_{eff}}$ | Equivalent stress block depth (full composite) | Plastic stress distribution |
| $\phi_b M_n = \phi_b \cdot C_f\!\left(\dfrac{d}{2} + t_s - \dfrac{a}{2}\right)$ | LRFD flexural strength (PNA in slab) | AISC 360-22 §I3.2 |
| $I_{LB} = I_s + \sqrt{\dfrac{\Sigma Q_n}{C_f}}\!\left(I_{tr} - I_s\right)$ | Lower-bound moment of inertia (deflection) | AISC 360-22 Commentary §IC3.2 |

$$
\boxed{
Q_n = 0.5 \, A_{sa}\sqrt{f'_c E_c} \;\le\; R_g R_p A_{sa} F_u
}
$$

**Variable legend:**

| Symbol | Description | SI Units | US Customary |
|--------|-------------|----------|--------------|
| $A_{sa}$ | Cross-sectional area of one headed stud | mm² | in² |
| $f'_c$ | Concrete compressive strength | MPa | ksi |
| $E_c$ | Concrete elastic modulus: $w_c^{1.5}\sqrt{f'_c}$ | MPa | ksi ($w_c$ in pcf) |
| $R_g$ | Group reduction factor (1.0 for solid slab or stud in deck rib parallel to beam) | — | — |
| $R_p$ | Position reduction factor (0.75 studs in deck ribs; 0.75 weak position in rib; 0.60 specific) | — | — |
| $F_u$ | Specified minimum tensile strength of stud = 65 ksi (ASTM A108) | MPa | ksi |
| $A_s$ | Steel section cross-sectional area | mm² | in² |
| $A_c$ | Effective concrete slab area $= b_{eff} \times t_c$ ($t_c$ = slab thickness above deck) | mm² | in² |
| $C_f$ | Total horizontal shear force for full composite | N | kips |
| $a$ | Depth of equivalent rectangular stress block | mm | in |
| $d$ | Depth of steel section | mm | in |
| $t_s$ | Total slab thickness | mm | in |
| $I_s$ | Moment of inertia of steel section alone | mm⁴ | in⁴ |
| $I_{tr}$ | Fully transformed moment of inertia (full composite) | mm⁴ | in⁴ |
| $I_{LB}$ | Lower-bound moment of inertia (partial composite) | mm⁴ | in⁴ |

---

## 4. Derivation

### 4.1 Effective Slab Width (§I3.1a)

The concrete slab participates in bending only within a limited width because in-plane shear lag limits force transfer away from the beam. AISC limits the effective width to the lesser of:

- $L/8$ measured from beam centerline to each side (where $L$ is the beam span), and
- Half the center-to-center spacing to adjacent parallel beams ($s/2$), and
- Distance to a slab edge

Both sides are summed for the total $b_{eff}$ used in the plastic stress block.

### 4.2 Concrete Compressive Rectangular Stress Block

At ultimate (plastic limit state), the Whitney rectangular stress block gives uniform compression at $0.85 f'_c$ over depth $a$:

$$C = 0.85 f'_c \times b_{eff} \times a$$

The total compression is limited to the smaller of the concrete's full capacity and the steel section's full tension capacity:

$$C_f = \min\!\Bigl(0.85 f'_c \, b_{eff} \, t_c,\quad A_s F_y\Bigr)$$

where $t_c$ = thickness of concrete above top of formed deck (or full slab if no deck). This is the maximum possible compression, corresponding to **full composite action**.

Setting $C = C_f$:

$$a = \frac{C_f}{0.85 f'_c \, b_{eff}}$$

### 4.3 Plastic Neutral Axis Location

**PNA in slab** (most common for composite beams — steel section in full tension):
This occurs when $A_s F_y \le 0.85 f'_c b_{eff} t_c$, i.e., the concrete can absorb all the steel's capacity without its stress block extending into the deck.

Internal forces:
- Concrete: $C = A_s F_y = C_f$ at stress $0.85 f'_c$ over width $b_{eff}$, depth $a$
- Steel: $T = A_s F_y = C_f$ (entire section in tension)

The moment arm from the centroid of steel to the centroid of the concrete force block is:

$$\bar{d} = \frac{d}{2} + t_s - \frac{a}{2}$$

where $d$ = steel section depth, $t_s$ = distance from top of slab to top of steel flange = $t_{slab}$ (above deck) + deck height. More precisely, define the geometry as:

$$\bar{d} = \underbrace{\frac{d}{2}}_{\substack{\text{centroid of} \\ \text{steel below}\\ \text{top flange}}} + \underbrace{(t_s - \frac{a}{2})}_{\substack{\text{top of steel to} \\ \text{centroid of} \\ \text{compression block}}}$$

For LRFD: $\phi_b = 0.90$
$$\phi_b M_n = 0.90 \times C_f \times \bar{d}$$

**PNA in steel section** (occurs when PNA falls below the top of steel — higher axial load or thick webs with low $C_f$): A portion of the top of the steel section is in compression. The calculation requires partitioning the steel section into compression and tension regions; AISC provides tables for this in the 16th ed. Manual.

### 4.4 Shear Stud Capacity (§I8.2a)

A headed stud welded to the top flange is pulled upward by the concrete and pushes back through its shank. The nominal strength per stud is the lesser of:

1. **Concrete failure** (shear cone pullout): $Q_n = 0.5 A_{sa}\sqrt{f'_c E_c}$
2. **Stud shear fracture**: $Q_n = R_g R_p A_{sa} F_u$

where:
- $R_g = 1.0$ for a solid slab or studs in a formed deck rib **parallel** to the beam; $R_g = 0.85$ for a single stud in a rib **perpendicular** to beam (deck ribs transverse); $R_g = 0.70$ for two studs in a transverse rib
- $R_p = 0.75$ for studs in transverse deck ribs; $R_p = 0.75$ for studs in parallel deck ribs with the stud in the "weak" (deck valley) position; $R_p = 0.60$ for studs in specific configurations — see Table I8.2a
- For **solid slabs**: $R_g = R_p = 1.0$

### 4.5 Number of Studs Required (§I3.2d)

The total horizontal shear between the point of maximum positive moment and the nearest zero-moment point (beam end or contraflexure) must be transferred through shear studs. For full composite, the required total stud strength:

$$\Sigma Q_n^{full} = C_f = \min(0.85 f'_c A_c,\; A_s F_y)$$

Number of studs per half-span (full composite):

$$N^{full} = \frac{C_f}{Q_n}$$

For **partial composite** ($0.25 \le \% \le 1.00$):

$$N^{partial} = \frac{\text{fraction} \times C_f}{Q_n}$$

Studs must be distributed uniformly between the zero-moment point and the maximum-moment point (§I8.2d), with a maximum spacing of ≤ 8$t_s$ ≤ 36 in and a minimum spacing of $6 d_{stud}$ along the beam and $4 d_{stud}$ transversely from the edge.

### 4.6 Partial Composite Flexural Strength

When partial composite is used, the stud force transferred is:

$$\Sigma Q_n^{partial} = N_{partial} \times Q_n$$

The compression in concrete is reduced: $C' = \Sigma Q_n^{partial}$. The plastic neutral axis shifts down into the steel section. The updated plastic stress block depth:

$$a' = \frac{C'}{0.85 f'_c b_{eff}}$$

The steel section now has a compression zone near the top and tension zone below, split by the PNA. The moment is recalculated using the modified geometry. AISC Manual tables (Table 3-19 and 3-20) provide this directly.

### 4.7 Deflection Using Lower-Bound Moment of Inertia (Commentary §IC3.2)

Composite beams are stiffer than non-composite, but the degree depends on how many studs are installed. AISC Commentary provides a simple interpolation:

$$I_{LB} = I_s + \sqrt{\frac{\Sigma Q_n}{C_f}} \left(I_{tr} - I_s\right)$$

The **transformed moment of inertia** uses the elastic modular ratio $n = E_s/E_c$:

$$I_{tr} = I_s + A_s \bar{y}^2 + \frac{b_{eff}}{n} t_c \left(\bar{y}_{top}^2 + \frac{t_c^2}{12}\right)$$

where $\bar{y}$ = distance from steel centroid to elastic neutral axis of transformed section. In practice the Manual's pre-computed $I_{LB}$ tables are used.

---

## 5. Design / Application Procedure

1. **Determine slab geometry**: slab thickness $t_s$, deck height $h_r$, concrete thickness above deck $t_c = t_s - h_r$, concrete strength $f'_c$, unit weight $w_c$.

2. **Compute $E_c$** and **modular ratio $n = E_s/E_c$**:

   $$E_c = w_c^{1.5} \sqrt{f'_c} \quad \text{($w_c$ in pcf, $E_c$ in psi)} \quad \text{e.g., } 145^{1.5}\!\sqrt{4000} \approx 3{,}650{,}000 \text{ psi} = 3{,}650 \text{ ksi}$$

   $$n = 29{,}000 / 3{,}650 \approx 8$$

3. **Establish effective slab width**: $b_{eff} = 2 \times \min(L/8,\; s/2)$ (both sides, symmetrical bay).

4. **Compute $C_f$** (full composite force):

   $$C_f = \min\!\left(0.85 f'_c b_{eff} t_c,\quad A_s F_y\right)$$

5. **Compute stud capacity $Q_n$**: Pick stud size; apply $R_g$, $R_p$ for deck orientation.

6. **Determine number of studs for full composite** and decide on degree of composite (typically 50–75% is economical):

   $$N_{half} = \lceil \% \times C_f / Q_n \rceil$$

7. **Compute plastic stress block depth $a$** (for the chosen $\Sigma Q_n$):

   $$a = \frac{\Sigma Q_n}{0.85 f'_c b_{eff}}$$

8. **Check PNA location** (in slab or in steel): If $a \le t_c$, PNA is in slab; proceed to step 9. If $a > t_c$, PNA is in steel; use AISC tables or partition the steel section.

9. **Compute nominal flexural strength** and check LRFD:

   $$\phi_b M_n = 0.90 \times \Sigma Q_n \times \bar{d} \ge M_u$$

   where $\bar{d} = d_s/2 + t_s - a/2$ (PNA in slab case).

10. **Shear check** (§I4.2): For composite beams, shear is resisted entirely by the steel web — check $\phi_v V_n$ per Chapter G (from 06-E notes) against $V_u$.

11. **Deflection check**: Compute $I_{LB}$ and verify:
    - Construction (pre-composite): $\Delta = 5wL^4/(384 E_s I_s)$
    - In-service (composite): $\Delta = 5wL^4/(384 E_s I_{LB})$
    - Check vs. $L/360$ (live load) and $L/240$ (total load with wet concrete excluded) or per governing code.

---

## 6. Worked Example

**Problem:** Design a composite floor beam spanning 30 ft, bay width $s = 10$ ft. Normal-weight concrete slab: $f'_c = 4$ ksi, $w_c = 145$ pcf, $t_s = 5.5$ in (3.5 in above 2-in deck ribs). LRFD moments: $M_u = 450$ kip-ft (construction) controlled by $M_u = 600$ kip-ft (composite, service + live). Try W18×50 (A992, $F_y = 50$ ksi). Use 3/4-in headed studs in transverse deck ribs (single stud/rib, $R_g = 0.85$, $R_p = 0.75$).

**Given:**
- W18×50: $d = 17.99$ in, $A_s = 14.7$ in², $I_x = 800$ in⁴, $S_x = 88.9$ in³, $Z_x = 101$ in³
- Stud: $d_{stud} = 3/4$ in, $L_{stud} = 3.5$ in (after welding), $A_{sa} = 0.4418$ in²
- $F_u^{stud} = 65$ ksi

**Required:** Check composite flexural strength; find number of studs.

**Solution:**

1. **$E_c$ and modular ratio**:

   $$E_c = 145^{1.5}\!\sqrt{4.0} = 1{,}746 \times 2 = 3{,}492 \text{ ksi} \approx 3{,}500 \text{ ksi}$$

   $$n = 29{,}000 / 3{,}500 \approx 8$$

2. **Effective slab width**:

   $$b_{eff} = 2 \times \min\!\left(\frac{30\times12}{8},\; \frac{10\times12}{2}\right) = 2 \times \min(45, 60) = 2 \times 45 = 90 \text{ in}$$

   $$A_c = 90 \times 3.5 = 315 \text{ in}^2$$

3. **Full composite force**:

   $$C_f^{conc} = 0.85 \times 4 \times 315 = 1{,}071 \text{ kips}$$
   $$C_f^{steel} = 14.7 \times 50 = 735 \text{ kips}$$
   $$C_f = 735 \text{ kips (steel controls)}$$

4. **Stud strength**:

   $$Q_n = 0.5 \times 0.4418\!\sqrt{4.0 \times 3{,}500} = 0.5 \times 0.4418 \times 118.3 = 26.1 \text{ kips}$$
   $$Q_n^{cap} = 0.85 \times 0.75 \times 0.4418 \times 65 = 18.3 \text{ kips}$$

   **Governs**: $Q_n = 18.3$ kips (stud fracture, deck reduction controls)

5. **50% partial composite ($\Sigma Q_n = 0.50 \times 735 = 367.5$ kips)**:

   $$N_{half} = \frac{367.5}{18.3} = 20.1 \implies 21 \text{ studs per half-span, } 42 \text{ total}$$

6. **Plastic stress block depth**:

   $$a = \frac{367.5}{0.85 \times 4 \times 90} = \frac{367.5}{306} = 1.20 \text{ in} \le t_c = 3.5 \text{ in} \checkmark \quad (\text{PNA in slab})$$

7. **Moment arm and nominal strength**:

   $$\bar{d} = \frac{17.99}{2} + (3.5 + 2.0) - \frac{1.20}{2} = 9.00 + 5.50 - 0.60 = 13.90 \text{ in}$$

   $$\phi_b M_n = 0.90 \times 367.5 \times \frac{13.90}{12} = 0.90 \times 367.5 \times 1.158 = 383 \text{ kip-ft}$$

   $383 < 600$ kip-ft → **50% composite with W18×50 insufficient; try 75% or a heavier section.**

   **At 75% composite**: $\Sigma Q_n = 0.75 \times 735 = 551$ kips; $a = 551/306 = 1.80$ in;

   $\bar{d} = 9.00 + 5.50 - 0.90 = 13.60$ in;

   $$\phi_b M_n = 0.90 \times 551 \times (13.60/12) = 0.90 \times 624 = 562 \text{ kip-ft} < 600 \text{ kip-ft}$$

   **Try 100% composite**: $\Sigma Q_n = 735$ kips; $a = 735/306 = 2.40$ in;

   $\bar{d} = 9.00 + 5.50 - 1.20 = 13.30$ in;

   $$\phi_b M_n = 0.90 \times 735 \times (13.30/12) = 0.90 \times 813 = 732 \text{ kip-ft} > 600 \text{ kip-ft} \checkmark$$

   $$N_{half} = \lceil 735/18.3 \rceil = \lceil 40.2 \rceil = 41 \text{ studs per half-span, } 82 \text{ total}$$

**Result:** W18×50 with full composite action ($\phi_b M_n = 732$ kip-ft > $M_u = 600$ kip-ft) is adequate using 82 studs total (41 per half-span). In practice, a deeper section with 50–75% composite may be more economical; full composite with W18×50 is a viable minimum-section solution.

---

## 7. Common Mistakes & Pitfalls

- **Including deck height in the compression block depth:** The concrete in the deck ribs (below the top surface) is typically **not** included in $A_c$ for strength (per §I3.2a, only concrete above the top of steel deck is used unless deck ribs are parallel to beam). Use only $t_c$ (above deck) in $A_c = b_{eff} \times t_c$.

- **Forgetting $R_g$ and $R_p$ for deck-slab systems:** Stud strength is significantly reduced when studs are in deck ribs perpendicular to the beam ($R_g = 0.85$, $R_p = 0.75$ for single stud). Using $R_g = R_p = 1.0$ overestimates each stud by 47% → far too few studs.

- **Using total slab thickness for $t_s$ in the moment arm:** The distance from the top of the steel to the resultant concrete force is from the top of the steel to $a/2$ within the concrete above the deck (not below the deck). Slab geometry must be carefully tracked: $d_{top-to-slab} = hr + t_c$.

- **Checking shear in the composite section:** AISC §I4.2 specifies that shear is resisted **only by the steel section web**, not the composite section. Apply the Chapter G shear check using $d$, $t_w$ of the steel section alone; never use the full transformed section for shear.

- **Ignoring construction stage:** Before concrete cures, the bare steel section ($I_s$) carries all wet concrete and construction loads. The construction stage often requires a heavier section than the composite stage, particularly for long spans.

---

## 8. Connections to Other Topics

- **Shear design of beams (06-E):** Composite beams still rely on steel web shear capacity; the composite concrete slab does not contribute to $V_n$. Shear must be checked using the bare steel section properties per §I4.2.
- **Loads and load combinations (10):** Construction-stage loads (wet concrete = dead load, workers = construction live load) create a separate LRFD load case; shoring vs. unshored construction affects which loads are in the composite vs. non-composite stage.
- **Beam deflections (01-F):** Composite stiffness ($I_{LB}$) reduces live-load deflections; the construction-stage deflection (under wet concrete weight) must be calculated with $I_s$ alone. Pre-cambering the steel beam is common practice to counteract dead-load sag.
- **Foundation design (12):** Composite floors increase tributary dead load on columns and foundations compared to non-composite; the concrete-slab weight must be included in gravity load tributary calculations.

---

## 9. Further Reading

| Resource | Where to look |
|----------|--------------|
| AISC 360-22 | Chapter I: Design of Composite Members |
| AISC Steel Construction Manual, 16th ed. | Part 3 (Design of Flexural Members — composite tables 3-19, 3-20) |
| Segui, *Steel Design*, 6th ed. | Chapter 9: Composite Beams |
| Viest, Fountain & Singleton, *Composite Construction in Steel and Concrete* | Background and test data |
| AISC Design Guide 3 | Live load deflections and floor vibration (composite beams) |

---

## 10. Quick Self-Check

- [ ] I can explain physically what full vs. partial composite action means and the minimum permitted degree (25%).
- [ ] I can compute $b_{eff}$, $C_f$, and $Q_n$ from given geometry and material data.
- [ ] I know to use only $t_c$ (concrete above the deck) in the compression block, not total slab depth.
- [ ] I can calculate $\phi_b M_n$ when the plastic neutral axis is in the slab.
- [ ] I understand why the construction stage must be checked with bare steel section properties.

---

---

## 11. Graduate Extension: Partial Interaction Theory, Creep & Floor Vibration

### 11.1 Elastic Transformed Section: Rigorous No-Slip Derivation

The **transformed section method** is the exact elastic solution for a composite beam assuming **no interface slip** (full interaction). It converts the concrete into equivalent steel by dividing concrete areas by the modular ratio $n = E_s/E_c$.

**Step 1 — Stress compatibility.** At any cross-section, compatibility requires the strain in the concrete at the interface equal the strain in the steel flange at the interface:

$$
\varepsilon_{c,int} = \varepsilon_{s,int} \implies \frac{\sigma_c}{E_c} = \frac{\sigma_s}{E_s} \implies \sigma_c = \frac{E_c}{E_s}\sigma_s = \frac{\sigma_s}{n}
$$

**Step 2 — Equivalent section.** A concrete area $A_c$ carrying stress $\sigma_c = \sigma_s/n$ contributes the same force as a steel area $A_c/n$ carrying stress $\sigma_s$. Replace the concrete slab (width $b_{eff}$, thickness $t_c$) with an equivalent steel area:

$$
A_{c,tr} = \frac{b_{eff} t_c}{n}
$$

**Step 3 — Centroid and $I_{tr}$.** Locate the neutral axis of the transformed section and compute:

$$
\bar{y}_{tr} = \frac{A_s \bar{y}_s + (A_c/n)\bar{y}_c}{A_s + A_c/n}
$$

$$
I_{tr} = I_s + A_s(\bar{y}_{tr} - \bar{y}_s)^2 + \frac{b_{eff} t_c^3}{12n} + \frac{A_c}{n}(\bar{y}_{tr} - \bar{y}_c)^2
$$

**Step 4 — Long-term modular ratio.** For sustained loads (dead load, superimposed dead), concrete creep effectively reduces $E_c$ over time. The **long-term modular ratio** is:

$$
n_{LT} = n \cdot (1 + \psi_L) \qquad \psi_L \approx 1.5\text{-}2.0 \text{ for normal-weight concrete}
$$

AISC 360-22 Commentary §IC3.1 recommends $n_{LT} = 3n$ for total long-term deflection calculations.

---

### 11.2 Partial Interaction Theory: Newmark, Siess & Viest (1951)

When shear connectors are deformable (not rigid), **partial interaction** occurs: the slab and steel beam undergo different longitudinal displacements at the interface, and the shear connector force is proportional to the interface slip. This is the *Newmark model* (Newmark, Siess & Viest, *Tests and Analysis of Composite Beams with Incomplete Interaction*, Illinois Bulletin No. 396, 1951).

**Step 1 — Degrees of freedom.** For a symmetric (midpoint-symmetric) composite beam of span $L$, define:
- $u(x)$: slip at the steel-concrete interface (positive = concrete displaced forward)
- $v(x)$: common vertical deflection

**Step 2 — Elastic connector law.** The horizontal shear force per unit length transferred by connectors:

$$
q(x) = k_s \cdot u(x)
$$

where $k_s$ is connector stiffness per unit length (N/mm per mm = N/mm²). For uniformly spaced studs at pitch $p$:

$$
k_s = \frac{K_{stud}}{p}
$$

Typically $K_{stud} \approx 185$ kN/mm (from push-out tests on 22 mm diameter studs in normal-weight concrete).

**Step 3 — Governing ODE.** Setting up compatibility of slip between the two sub-beams (Newmark et al., eq. 11):

$$
u'' - \alpha^2 u = -\alpha^2 u_f
$$

where $\alpha^2 = k_s(1/EA_s + 1/EA_c + e_{sc}^2/(EI_s + EI_c))$ is the **composite interaction parameter**, $e_{sc}$ is the distance between the centroids of the steel and concrete, and $u_f$ is the slip that would occur if the interface were free (i.e., in the non-composite beam). For a simply supported beam under uniform load $w$:

$$
u(x) = C_1\cosh(\alpha x) + C_2\sinh(\alpha x) + \frac{w}{k_s\alpha^2}x
$$

**Step 4 — Limiting cases.**
- $k_s \to \infty$ ($\alpha L \to \infty$, full interaction): $u = 0$, $I_{eff} = I_{tr}$ ✨
- $k_s \to 0$ ($\alpha L \to 0$, no interaction): $u = u_f$, $I_{eff} = I_s + I_c$

**Step 5 — AISC lower-bound $I_{LB}$.** The exact slip-deflection relationship from the NEwmark model is complex; AISC Commentary §IC3.2 provides the simple lower-bound interpolation:

$$
I_{LB} = I_s + \sqrt{\frac{\Sigma Q_n}{C_f}}(I_{tr} - I_s)
$$

This formula is a conservative approximation to the exact Newmark stiffness at the as-designed stud ratio $\Sigma Q_n/C_f \geq 0.25$. Research by Oehlers & Bradford (*Composite Steel and Concrete Structural Members*, 1995) shows the AISC formula underestimates actual stiffness by 5–15%.

---

### 11.3 Long-Term Deflection: Creep and Shrinkage

**Concrete creep.** Under sustained compressive stress $\sigma_c$, concrete continues to strain long after initial loading:

$$
\varepsilon_{cr}(t) = \phi(t, t_0) \cdot \frac{\sigma_c}{E_c}
$$

where $\phi(t, t_0)$ is the **creep coefficient** (ACI 209R; typical range 1.5–3.0 for normal-weight concrete). For structural composite beam design, creep effectively reduces $E_c$ and increases the modular ratio. The long-term deflection under sustained load:

$$
\delta_{LT} = \delta_{elastic}\left(\frac{I_{tr}}{I_{tr,LT}}\right)
$$

where $I_{tr,LT}$ is computed with $n_{LT} = n(1 + \phi)$ instead of $n$.

**Concrete shrinkage.** As concrete cures it shrinks (free strain $\varepsilon_{sh} \approx 200$–$600 \times 10^{-6}$). In a composite beam, shrinkage is restrained by the steel, inducing a **sagging (hogging) moment** and an axial tension in the concrete:

$$
M_{sh} = \varepsilon_{sh} E_c A_c e_{sc}\left(\frac{I_{tr}}{I_{tr} + A_{tr} e_{sc}^2}\right)
$$

This moment increases midspan deflection (both shrinkage itself and the secondary moment from the eccentricity). AISC Design Guide 3 provides simplified correction factors to account for shrinkage in long-term deflection calculations for floor systems.

---

### 11.4 Floor Vibration: AISC Design Guide 11

Composite floor systems, being stiff and lightweight compared to concrete flat slabs, are prone to **human-induced vibration** (walking). The AISC DG11 (Murray, Allen & Ungar, 2003) method computes the **peak acceleration** response:

**Step 1 — Natural frequency.** For a composite beam supporting a uniform tributary slab, the fundamental natural frequency is estimated from the Dunkerley series:

$$
f_n = 0.18\sqrt{g/\Delta_{composite}}
$$

where $\Delta_{composite}$ is the total mid-span deflection under the supported weight $W$ (DL + fixed LL), using $I_{tr}$ (transformed section, $n = 3n_e$ for long-term). For a simply supported beam:

$$
\Delta_{composite} = \frac{5wL^4}{384 E I_{tr}}
$$

**Step 2 — Combined system frequency.** For a beam-girder floor panel, the combined frequency is found by combining beam and girder deflections:

$$
\frac{1}{f_{system}^2} = \frac{1}{f_{beam}^2} + \frac{1}{f_{girder}^2} + \frac{1}{f_{column}^2}
$$

**Step 3 — Peak acceleration.** The AISC DG11 walking excitation model assumes a person walking generates a sinusoidal force at the third harmonic of the step frequency ($f_{step} \approx 1.6$–2.2 Hz; excitation at $if_{step}$, $i = 1, 2, 3, 4$). When $if_{step} \approx f_n$ (resonance condition), the peak acceleration normalized to $g$ is:

$$
\frac{a_p}{g} = \frac{P_0 e^{-0.35 f_n}}{\beta W}
$$

where $P_0 = 0.29$ kN (65 lb) is the dynamic force amplitude (3rd harmonic), $e^{-0.35f_n}$ accounts for the reduction in excitation force with increasing frequency, $\beta$ is the modal damping ratio (0.02–0.05 for typical office floors), and $W$ is the effective modal weight.

**Step 4 — Acceptance check.** Compare $a_p/g$ to the **tolerance limit** $a_0/g$ from Table 4.1 of DG11:

| Occupancy | $a_0/g$ |
|-----------|--------|
| Office / residential | 0.5% (0.005g) |
| Shopping mall | 1.5% |
| Outdoors footbridges | 5% |

**Design guidance.** To reduce floor vibration:
1. Increase composite beam depth (stiffness $\propto d^2$) to raise $f_n$ above 9–10 Hz (above typical walking harmonics)
2. Add mass (heavier concrete slab) to reduce $a_p/g$
3. Add viscous dampers under the floor (tuned mass dampers for sensitive applications)
4. Avoid equal beam and girder spans (prevents resonance coincidence between beam and girder modes)

---

### 11.5 Deck Geometry Effects and the Composite Section for Negative Moment

**Composite section in negative moment (continuous beams).** AISC 360-22 §I3.2.2 permits including slab reinforcing steel within $b_{eff}$ that passes through the shear connectors in computing the composite section for **negative moment** regions of continuous beams (or for serviceability). The negative-moment composite section uses only the steel deck ribs and reinforcing bars that are adequately developed.

For negative moment, the compression block is in the **steel bottom flange** and the tension force is shared by the steel section and the reinforcing bars:

$$
C_f^{neg} = \min\left(A_r F_{yr},\; A_s F_y\right)
$$

where $A_r$ is the area of longitudinal rebar within $b_{eff}$ and $F_{yr}$ is the rebar yield stress. Shear studs are still required at this location because the interface must transfer the rebar force from the deck into the steel section.

**Deck ribs perpendicular to beam.** When the deck ribs run perpendicular to the beam ($\alpha_{r} = 90°$), studs are placed in the narrow rib openings. AISC §I8.2a gives reduction factors:

$$
R_g = 0.85 \text{ (single stud per rib)}, \quad R_p = 0.75 \text{ ("strong" position — stud in rib, favorable)} 
$$

$$
R_p = 0.60 \text{ ("weak" position — stud at back of rib, emid deck wave)}
$$

Post-2010 research (Rambo-Roddenberry et al., *AISC Engineering Journal*, 2002; Pallardy, 2016) showed that the "staggered" placement alternating strong/weak positions achieves $R_g R_p \approx 0.65$ on average, higher than the $0.85\times0.60 = 0.51$ for all weak positions. AISC 360 simplified this by recommending strong position ($R_p = 0.75$) for design and requiring minimum stud spacing to allow strong positioning when practical.

---

*Created by Structural Engineering Tutor • 2026-03-18 | Upgraded to Graduate level: 2026-03-18*
