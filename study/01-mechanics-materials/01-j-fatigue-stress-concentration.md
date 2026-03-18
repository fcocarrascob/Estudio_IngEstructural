# Fatigue & Stress Concentration Factors

**Subject area:** Mechanics of Materials  
**Design standard / primary reference:** Hibbeler, *Mechanics of Materials*, 10th ed. — Ch. 14 (§14.1–14.3); Shigley's *Mechanical Engineering Design*, 10th ed. — Ch. 6  
**Depth level:** Undergraduate — accessible  
**Estimated study time:** 75 minutes

---

## 1. Introduction & Motivation

All the failure criteria studied in Topic 01-I apply to **static** loading: the load is applied once and stays constant. But what happens when a structural member is loaded and unloaded repeatedly — like the wing of an aircraft, the crankshaft of an engine, or the joint of a bridge? Experiments by August Wöhler in the 1860s revealed a shocking fact: a metal can fail at a stress far below its static yield strength if the load is **cycled** thousands or millions of times. This is **fatigue failure**.

Fatigue is responsible for an estimated 80–90% of all mechanical and structural failures in service. Cracks initiate at **stress concentrations** — notches, holes, fillets, weld toes, surface scratches — where the local stress is amplified far above the nominal (average) stress. The **stress concentration factor** $K_t$ captures this amplification. Even a well-designed shaft running at half its yield stress can fail by fatigue if it has a keyway, a thread root, or a press-fit hub.

This topic introduces the tools to design against fatigue: S-N curves, the endurance limit, the modified Goodman diagram, and the stress concentration factor.

---

## 2. Key Concepts & Definitions

| Term | Symbol | Definition |
|------|--------|------------|
| Fatigue | — | Progressive, localized structural damage caused by cyclic loading; leads to crack growth and sudden fracture |
| S-N curve (Wöhler curve) | — | Plot of stress amplitude $S$ vs. number of cycles to failure $N_f$ (typically log-log) |
| Endurance limit | $S_e$ or $\sigma_e$ | Stress amplitude below which a material can theoretically withstand infinite cycles without fatigue failure (steels below $\approx 1400$ MPa $F_u$) |
| Fatigue strength | $S_f$ at $N$ cycles | Stress amplitude causing failure at exactly $N_f$ cycles (for materials with no endurance limit, like aluminum) |
| Stress concentration factor (theoretical) | $K_t$ | Ratio of actual peak stress at a notch to the nominal stress: $K_t = \sigma_{max}/\sigma_{nom}$ |
| Fatigue stress concentration factor | $K_f$ | Effective stress concentration for fatigue; $K_f \leq K_t$ due to notch sensitivity $q$ |
| Notch sensitivity | $q$ | Describes how strongly a material responds to a notch: $q = (K_f - 1)/(K_t - 1)$; $q = 0$ → immune; $q = 1$ → fully sensitive |
| Stress ratio | $R$ | $R = \sigma_{min}/\sigma_{max}$ for a cyclic stress cycle |
| Mean stress | $\sigma_m$ | $\sigma_m = (\sigma_{max} + \sigma_{min})/2$ |
| Stress amplitude | $\sigma_a$ | $\sigma_a = (\sigma_{max} - \sigma_{min})/2$ |
| Fully reversed | $R = -1$ | $\sigma_{mean} = 0$; equal tension and compression cycles — worst case |
| Goodman diagram | — | Diagram relating stress amplitude $\sigma_a$ and mean stress $\sigma_m$ to failure; used to assess combined steady + cyclic loading |

---

## 3. Governing Equations

| Equation | Description | Source |
|----------|-------------|--------|
| $K_t = \sigma_{max} / \sigma_{nom}$ | Theoretical (geometric) stress concentration factor | Hibbeler, 10th ed. Eq. 14-1 |
| $K_f = 1 + q(K_t - 1)$ | Fatigue stress concentration factor | Shigley's, 10th ed. Eq. 6-32 |
| $\sigma_{max} = K_t \, \sigma_{nom}$ | Peak stress at notch (static loading) | — |
| $\sigma_m = (\sigma_{max} + \sigma_{min})/2$ | Mean stress | Hibbeler, 10th ed. §14.1 |
| $\sigma_a = (\sigma_{max} - \sigma_{min})/2$ | Stress amplitude | Hibbeler, 10th ed. §14.1 |
| $\frac{\sigma_a}{S_e} + \frac{\sigma_m}{\sigma_u} = 1$ | Modified Goodman criterion (failure line) | Shigley's, 10th ed. Eq. 6-41 |
| $S_e \approx 0.5 \, S_u$ | Estimated endurance limit for steel ($S_u \leq 1400$ MPa) | Shigley's, 10th ed. Eq. 6-10 |

$$
K_t = \frac{\sigma_{max}}{\sigma_{nom}}
$$

$$
\frac{\sigma_a}{S_e} + \frac{\sigma_m}{\sigma_u} = 1 \quad \text{(Modified Goodman line — failure)}
$$

$$
\sigma_m = \frac{\sigma_{max} + \sigma_{min}}{2}, \quad \sigma_a = \frac{\sigma_{max} - \sigma_{min}}{2}
$$

**Variable legend:**

| Symbol | Description | SI Units | US Customary Units |
|--------|-------------|----------|--------------------|
| $K_t$ | Theoretical stress concentration factor | dimensionless | dimensionless |
| $K_f$ | Fatigue stress concentration factor | dimensionless | dimensionless |
| $q$ | Notch sensitivity (0–1) | dimensionless | dimensionless |
| $\sigma_{nom}$ | Nominal stress (computed ignoring the notch) | MPa | ksi |
| $\sigma_{max}$ | Peak stress at notch | MPa | ksi |
| $\sigma_m$ | Mean (average) stress over a cycle | MPa | ksi |
| $\sigma_a$ | Stress amplitude (half the stress range) | MPa | ksi |
| $S_e$ | Endurance limit (corrected) | MPa | ksi |
| $S_u$ or $F_u$ | Ultimate tensile strength | MPa | ksi |
| $N_f$ | Number of cycles to failure | cycles | cycles |

---

## 4. Derivation / Development

### 4-1. The S-N Curve

**Wöhler's experiment (1860s):** Rotating bending fatigue tests on steel specimens. Each specimen is subjected to a fully reversed sinusoidal stress amplitude $\sigma_a$ and cycled until fracture. The number of cycles to failure $N_f$ is recorded.

**S-N curve characteristics:**
- Plotted on a log-log (or semi-log) scale: stress $S$ (MPa) vs. $N_f$ (cycles).
- For **carbon steels** (and most alloy steels): the curve flattens at $\approx 10^6$–$10^7$ cycles, defining an **endurance limit** $S_e$. Below $S_e$, the material theoretically never fails by fatigue.
- For **aluminum, copper, and many non-ferrous metals**: no clear endurance limit — the S-N curve continues to slope downward. A **fatigue strength at $10^8$ cycles** is used instead.

**Estimated endurance limit for wrought steel (Shigley's 10th ed. Eq. 6-10):**
$$S_e' \approx 0.5 \, S_u \quad \text{for } S_u \leq 1400 \text{ MPa}$$
$$S_e' \approx 700 \text{ MPa} \quad \text{for } S_u > 1400 \text{ MPa}$$

**Corrected endurance limit** (accounting for real surface, size, and loading conditions):
$$S_e = k_a \cdot k_b \cdot k_c \cdot k_d \cdot k_e \cdot S_e'$$

where $k_a$ = surface condition factor, $k_b$ = size factor, $k_c$ = load type factor, $k_d$ = temperature factor, $k_e$ = reliability factor. Full tables available in Shigley's Ch. 6.

### 4-2. Stress Concentration Factor $K_t$

**Physical meaning:** Near a geometric discontinuity (hole, notch, fillet), stress "flows" around the discontinuity and peaks sharply. The **theoretical stress concentration factor** is defined as:
$$K_t = \frac{\sigma_{max}}{\sigma_{nom}}$$

where $\sigma_{nom}$ is the nominal stress computed by the standard formulas ($P/A$, $Mc/I$, etc.) using the **net section properties** (excluding the hole/notch area).

**Values of $K_t$:** Determined from theory of elasticity solutions, FEM, or experimental photoelasticity. Published in charts for common geometries:
- Circular hole in a wide plate under uniaxial tension: $K_t = 3$.
- Circular hole in plate under biaxial tension (equal stresses): $K_t = 2$.
- Elliptical hole with semi-axes $a$ (transverse) and $b$ (along load): $K_t = 1 + 2a/b$.
- Values for notches, fillets, shoulders are in textbook charts (Peterson's or Pilkey's *Stress Concentration Factors*).

### 4-3. Notch Sensitivity and $K_f$

$K_t$ is a **geometric** property. But materials do not always respond fully to the theoretical stress concentration under **fatigue** loading (due to microstructural grain averaging and stress redistribution). The **notch sensitivity index** $q$ bridges the two:
$$q = \frac{K_f - 1}{K_t - 1} \quad \Rightarrow \quad K_f = 1 + q(K_t - 1)$$

- $q = 0$: fully insensitive to notch — notch has no effect on fatigue ($K_f = 1$). Typical for very ductile or coarse-grained materials.
- $q = 1$: fully sensitive — notch acts at full theoretical severity ($K_f = K_t$). Typical for high-strength steels.

**Typical trend:** Smaller notch radii → lower $q$ (smaller $K_f$ despite same $K_t$). High-strength steels → $q \to 1$.

### 4-4. The Modified Goodman Diagram

Under real conditions, stress cycles are often **not fully reversed** — there is a mean (steady) stress $\sigma_m$ plus a fluctuating amplitude $\sigma_a$.

**Modified Goodman criterion (failure line):**
$$\frac{\sigma_a}{S_e} + \frac{\sigma_m}{S_u} = 1$$

- Points **below** the line are safe from fatigue failure.
- Points **above** the line fall by fatigue.
- The $x$-intercept is $S_u$ (pure static) and the $y$-intercept is $S_e$ (fully reversed fatigue).

**FOS under Goodman:**
$$FS = \frac{1}{\dfrac{\sigma_a}{S_e} + \dfrac{\sigma_m}{S_u}}$$

**Alternative criteria:**
- **Gerber parabola:** $(\sigma_a/S_e) + (\sigma_m/S_u)^2 = 1$ — less conservative, closer to experimental data.
- **Soderberg line:** $(\sigma_a/S_e) + (\sigma_m/\sigma_y) = 1$ — more conservative (uses $\sigma_y$ instead of $S_u$).
- Modified Goodman is the most common in practice (conservative but not excessively so).

---

## 5. Design / Application Procedure

1. **Define the stress cycle:** Find $\sigma_{max}$ and $\sigma_{min}$ at the critical point.
2. **Compute** $\sigma_m = (\sigma_{max} + \sigma_{min})/2$ and $\sigma_a = (\sigma_{max} - \sigma_{min})/2$.
3. **Apply stress concentration:**
   - Find $K_t$ from geometry charts for the cross-section discontinuity.
   - Find $q$ from notch sensitivity charts for the material and notch radius.
   - Compute $K_f = 1 + q(K_t - 1)$.
   - Modified amplitudes: $\sigma_a^* = K_f \, \sigma_a$; $\sigma_m^* = \sigma_m$ (for ductile materials, mean stress is not amplified by $K_f$ because local yielding redistributes the peak).
4. **Find the endurance limit $S_e$** — from tables or estimate $S_e \approx 0.5 S_u$ for steel, then apply correction factors ($k_a$ through $k_e$).
5. **Apply Modified Goodman:**
   $\dfrac{\sigma_a^*}{S_e} + \dfrac{\sigma_m^*}{S_u} \leq \frac{1}{FS}$
6. **Also check static yielding separately:** $\sigma_{max} = \sigma_m + \sigma_a \leq \sigma_y / FS$ (Langer static yield line).

---

## 6. Worked Example

**Problem:** A rotating steel shaft ($S_u = 600$ MPa, $\sigma_y = 420$ MPa) has a shoulder with a stress concentration factor $K_t = 1.8$ (from charts) and notch sensitivity $q = 0.82$. The nominal bending stress amplitude is $\sigma_a = 130$ MPa (fully reversed: $\sigma_m = 0$). The uncorrected endurance limit is $S_e' = 0.5 \times 600 = 300$ MPa; assume all correction factors give $S_e = 0.75 \times S_e' = 225$ MPa. Check for fatigue failure and compute the factor of safety.

**Given:**
- $S_u = 600$ MPa; $\sigma_y = 420$ MPa; $S_e = 225$ MPa
- $K_t = 1.8$; $q = 0.82$
- $\sigma_a = 130$ MPa; $\sigma_m = 0$ (fully reversed)

**Solution:**

1. **Fatigue stress concentration factor:**
$$K_f = 1 + q(K_t - 1) = 1 + 0.82(1.8 - 1) = 1 + 0.82(0.8) = 1 + 0.656 = 1.656$$

2. **Modified stress amplitude:**
$$\sigma_a^* = K_f \cdot \sigma_a = 1.656 \times 130 = 215.3 \text{ MPa}$$

3. **Modified Goodman check** (fully reversed, so $\sigma_m = 0$):
$$\frac{\sigma_a^*}{S_e} + \frac{\sigma_m}{S_u} = \frac{215.3}{225} + 0 = 0.957 < 1.0 \quad \checkmark \text{ (safe)}$$

4. **Factor of safety:**
$$FS = \frac{1}{\sigma_a^*/S_e + \sigma_m/S_u} = \frac{1}{0.957} = 1.045$$

5. **Static check:**
$$\sigma_{max} = \sigma_m + \sigma_a^* = 0 + 215.3 = 215.3 \text{ MPa} < \sigma_y = 420 \text{ MPa} \quad \checkmark$$

**Result:** The shaft is marginally safe (FS = 1.045) under fatigue. This is a very low factor of safety for a rotating shaft — in practice, a minimum FS of 1.5–2.0 is typically required. A redesign to increase the fillet radius (reducing $K_t$) or to select a material with a higher endurance limit would be appropriate.

---

## 7. Common Mistakes & Pitfalls

- **Mistake 1 — Using $K_t$ (not $K_f$) in fatigue calculations:** The fatigue stress concentration factor $K_f$ accounts for notch sensitivity and is always $\leq K_t$. Using $K_t$ directly overestimates the severity — it is conservative but may lead to unnecessary redesign.
- **Mistake 2 — Applying $K_f$ to the mean stress $\sigma_m$:** For ductile materials under combined mean + alternating stress, the mean stress is typically **not** multiplied by $K_f$ (because local plastic deformation at the notch redistributes the peak stress steady-state). Only the alternating component is amplified.
- **Mistake 3 — Assuming all metals have an endurance limit:** Steel has one; aluminum, copper, titanium, and most non-ferrous metals do not. For those materials, a finite-life fatigue strength at a high cycle count (e.g., $10^8$ cycles) must be used.
- **Mistake 4 — Ignoring surface finish and manufacturing effects:** A polished lab specimen can have $S_e = 0.5 S_u$, but a rough-machined surface reduces $S_e$ by 30–50% through the surface factor $k_a$. Neglecting $k_a$ seriously overestimates the allowable fatigue stress.
- **Mistake 5 — Confusing $K_t$ for different loading modes:** Charts give separate $K_t$ values for axial, bending, and torsional loading on the same geometry. Using the bending $K_t$ for a torsional stress is incorrect.

---

## 8. Connections to Other Topics

- **Topic 01-A (Stress & Strain):** Fatigue failure occurs at stress levels below the static yield stress — it is a reminder that the stress-strain curve alone is insufficient for design under cyclic loading.
- **Topic 01-G (Combined Loadings):** Real fatigue failures almost always involve combined bending + torsion + axial stresses. The stress concentration and Goodman analysis must be applied at the critical point identified from combined loading analysis.
- **Topic 01-H (Mohr's Circle):** Multiaxial fatigue criteria (beyond scope of this note) extend modified Goodman to biaxial or triaxial stress states using effective stresses from Mohr's circle or the von Mises criterion.
- **Topic 06 (Steel Design, AISC 360):** AISC 360 Appendix 3 provides fatigue design provisions for steel structures (bridges, cranes, etc.), defining **stress categories** (A through F) based on weld type and geometry — these are essentially prescriptive stress concentration factor charts.
- **Topic 07 (Concrete Design, ACI 318):** Fatigue in reinforcing bars (seismic loading, bridge decks) is addressed in ACI 318M §26 and ACI 215R — the S-N concept applies to rebar directly.

---

## 9. Further Reading

| Resource | Where to look |
|----------|--------------|
| Hibbeler, *Mechanics of Materials*, 10th ed. | §14.1–14.3: Fatigue |
| Shigley, Mischke & Budynas, *Mechanical Engineering Design*, 10th ed. | Chapter 6: Fatigue Failure resulting from Variable Loading |
| Beer, Johnston & DeWolf, *Mechanics of Materials*, 7th ed. | §2.16–2.17: Repeated Loading; Fatigue |
| Pilkey & Pilkey, *Peterson's Stress Concentration Factors*, 3rd ed. | Comprehensive charts for $K_t$ |
| AISC 360-22, Appendix 3 | Design for Fatigue — structural steel |

---

## 10. Quick Self-Check

- [ ] I can sketch a typical S-N curve for steel, label the endurance limit $S_e$, and explain what it means physically (infinite life below $S_e$).
- [ ] I can define $K_t$, $K_f$, and notch sensitivity $q$, and compute $K_f$ from the other two.
- [ ] I can compute $\sigma_m$ and $\sigma_a$ from a given cyclic stress history ($\sigma_{max}$, $\sigma_{min}$).
- [ ] I can apply the Modified Goodman criterion to determine if a point is safe and compute the factor of safety.
- [ ] I understand why fatigue is far more common in practice than static yielding failures, and what role stress concentrations play in crack initiation.

---

*Created by Structural Engineering Tutor • 2026-03-14*
