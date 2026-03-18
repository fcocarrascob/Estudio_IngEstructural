# Compression Member Design: Flexural Buckling, λ_r, λ_p

**Subject area:** Steel Design (AISC 360-22)
**Design standard / primary reference:** AISC 360-22 §E3, §E7, Table B4.1a; AISC Steel Construction Manual, 16th Ed.; Segui, *Steel Design*, 6th Ed.
**Depth level:** Undergraduate — accessible
**Estimated study time:** 60 minutes

---

## 1. Introduction & Motivation

Compression members — columns, struts, chord members of trusses, braces — are among the most critical structural elements in any building or bridge. Unlike tension members, which fail by material yielding or fracture at a predictable cross-sectional stress, compression members are governed by **instability**: the tendency of a slender element to suddenly deflect sideways (buckle) at a load that may be far below the squash load $P_y = F_y A_g$. This distinction makes compression design fundamentally different from tension design and requires engineers to account for the geometry of the member — its length, end conditions, and cross-sectional shape — not just its material strength.

The physical phenomenon at the heart of column design is **flexural (Euler) buckling**. When an ideally straight, concentrically loaded column is subjected to an increasing axial load, it remains straight until a critical load $P_e$ is reached, at which point the column can exist in a slightly bent equilibrium. For slender columns the critical stress is well below $F_y$ and the failure is purely elastic; for stocky columns the material yields before the elastic buckling load is reached, producing **inelastic buckling**. Real columns also contain **residual stresses** (locked-in stresses from cooling after rolling) and initial geometric imperfections, both of which reduce the actual buckling load below the theoretical Euler value. The AISC column curve embedded in AISC 360-22 §E3 is an empirical fit to hundreds of column tests that implicitly accounts for these real-world effects.

The second major concern in compression design is **local buckling** — the buckling of individual plate elements (flanges, webs, HSS walls) that make up the cross-section. If the width-to-thickness ratio $\lambda$ of a plate element exceeds the **slender element limit** $\lambda_r$ (from AISC Table B4.1a), the effective area is reduced below the gross area and the member's strength is penalized. For design of compression members the **compact limit** $\lambda_p$ is also noted: this limit, which is stricter than $\lambda_r$, applies primarily to **flexural members** (beams) and is included here for completeness and because beam-column design later requires both limits. Understanding the distinction between $\lambda_p$ (compact) and $\lambda_r$ (non-slender) is essential for correctly applying AISC Chapter E (columns) versus Chapter F (beams).

---

## 2. Key Concepts & Definitions

| Term | Symbol | Definition |
|------|--------|------------|
| Column | — | A structural member carrying primarily axial compressive load along its longitudinal axis. |
| Axial compression | $P$ | Force directed along the centroidal axis of a member, tending to shorten it. |
| Slenderness ratio | $KL/r$ | Dimensionless measure of a column's susceptibility to buckling; the ratio of effective length to radius of gyration. |
| Effective length | $KL$ | The length of an equivalent pin-ended column that has the same elastic buckling load as the actual column with its real end conditions. |
| Effective length factor | $K$ | Dimensionless multiplier applied to the actual unbraced length $L$ to obtain the effective length; depends on end restraint conditions (AISC Table C-A-7.2). |
| Euler elastic buckling stress | $F_e$ | The theoretical elastic critical stress at which a perfect column buckles: $F_e = \pi^2 E / (KL/r)^2$. |
| Critical stress | $F_{cr}$ | The AISC design compressive stress accounting for both elastic and inelastic buckling and implicitly for residual stresses. |
| Nominal compressive strength | $P_n$ | The nominal (unfactored) compressive strength of a column: $P_n = F_{cr} A_g$ (non-slender sections). |
| Gross cross-sectional area | $A_g$ | Total cross-sectional area of a member, including all plate elements; no holes deducted for compression members. |
| Radius of gyration | $r$ | $r = \sqrt{I/A}$; measure of how far cross-sectional area is distributed from the centroidal axis; determines resistance to buckling about that axis. |
| Local buckling | — | Buckling of an individual plate element (flange, web, HSS wall) before the overall member buckles. |
| Width-to-thickness ratio | $\lambda$ | Slenderness of a plate element: $b/t$ for unstiffened elements (e.g., flanges), $h/t_w$ for stiffened elements (e.g., webs). |
| Slender element limit | $\lambda_r$ | Maximum $\lambda$ for a plate element to be classified as non-slender in compression; tabulated in AISC Table B4.1a. Sections with $\lambda > \lambda_r$ require reduced effective area per §E7. |
| Compact element limit | $\lambda_p$ | Maximum $\lambda$ for a plate element to be classified as compact in **flexure** (beams); tabulated in AISC Table B4.1b. This is the stricter limit relevant to lateral-torsional buckling and plastic hinge formation. Not directly used in Chapter E column checks. |
| Governing axis | — | The axis about which $KL/r$ is largest; controls the column strength. Usually the weak axis (y–y) for W-shapes unless strong-axis unbraced length is much larger. |

---

## 3. Governing Equations

### 3.1 Equation Summary Table

| Equation | Description | Source |
|----------|-------------|--------|
| $F_e = \dfrac{\pi^2 E}{(KL/r)^2}$ | Euler elastic buckling stress | AISC 360-22 §E3-4 |
| $F_{cr} = \left[0.658^{F_y/F_e}\right] F_y$ | Inelastic buckling critical stress (when $KL/r \leq 4.71\sqrt{E/F_y}$) | AISC 360-22 §E3-2 |
| $F_{cr} = 0.877 F_e$ | Elastic buckling critical stress (when $KL/r > 4.71\sqrt{E/F_y}$) | AISC 360-22 §E3-3 |
| $P_n = F_{cr} A_g$ | Nominal compressive strength (non-slender sections) | AISC 360-22 §E3-1 |
| $\phi_c P_n \geq P_u$ | LRFD design check; $\phi_c = 0.90$ | AISC 360-22 §E1 |
| $P_n / \Omega_c \geq P_a$ | ASD design check; $\Omega_c = 1.67$ | AISC 360-22 §E1 |
| $\lambda_r = 0.56\sqrt{E/F_y}$ | Non-slender limit for unstiffened flanges of W-shapes (compression) | AISC Table B4.1a, Case 1 |
| $\lambda_r = 1.49\sqrt{E/F_y}$ | Non-slender limit for stiffened webs of W-shapes (compression) | AISC Table B4.1a, Case 5 |
| $\lambda_r = 1.40\sqrt{E/F_y}$ | Non-slender limit for walls of square/rectangular HSS (compression) | AISC Table B4.1a, Case 6 |
| $\lambda_p = 0.38\sqrt{E/F_y}$ | Compact limit for flanges of W-shapes in **flexure** (for reference) | AISC Table B4.1b, Case 10 |
| $KL/r \leq 200$ | Recommended maximum slenderness ratio (serviceability) | AISC 360-22 §E2 (Commentary) |

### 3.2 Display Equations

**Euler elastic buckling stress:**
$$F_e = \frac{\pi^2 E}{\left(\dfrac{KL}{r}\right)^2} \tag{AISC §E3-4}$$

**Transition slenderness (boundary between inelastic and elastic buckling):**
$$\left(\frac{KL}{r}\right)_{\text{transition}} = 4.71\sqrt{\frac{E}{F_y}} \tag{AISC §E3}$$

**Inelastic buckling critical stress** (when $KL/r \leq 4.71\sqrt{E/F_y}$, or equivalently $F_e \geq 0.44 F_y$):
$$F_{cr} = \left[0.658^{\,F_y / F_e}\right] F_y \tag{AISC §E3-2}$$

**Elastic buckling critical stress** (when $KL/r > 4.71\sqrt{E/F_y}$, or $F_e < 0.44 F_y$):
$$F_{cr} = 0.877 \, F_e \tag{AISC §E3-3}$$

**Nominal compressive strength (non-slender cross-section):**
$$P_n = F_{cr} \, A_g \tag{AISC §E3-1}$$

**LRFD design strength:**
$$\phi_c P_n \geq P_u \qquad \phi_c = 0.90 \tag{AISC §E1, LRFD}$$

**ASD allowable strength:**
$$\frac{P_n}{\Omega_c} \geq P_a \qquad \Omega_c = 1.67 \tag{AISC §E1, ASD}$$

**Local buckling limits (compression, AISC Table B4.1a):**
$$\lambda_r^{\,\text{flange, W-shape}} = 0.56\sqrt{\frac{E}{F_y}}, \qquad
  \lambda_r^{\,\text{web, W-shape}}  = 1.49\sqrt{\frac{E}{F_y}}, \qquad
  \lambda_r^{\,\text{HSS wall}}      = 1.40\sqrt{\frac{E}{F_y}}$$

**Compact limit for flanges in flexure (reference only, Table B4.1b):**
$$\lambda_p^{\,\text{flange, flexure}} = 0.38\sqrt{\frac{E}{F_y}}$$

### 3.3 Variable Legend

| Symbol | Description | SI Units | US Customary Units |
|--------|-------------|----------|--------------------|
| $F_e$ | Euler elastic buckling stress | MPa | ksi |
| $F_{cr}$ | Critical compressive stress (AISC column curve) | MPa | ksi |
| $F_y$ | Specified minimum yield stress of steel | MPa | ksi |
| $E$ | Modulus of elasticity of steel (200 000 MPa; 29 000 ksi) | MPa | ksi |
| $K$ | Effective length factor (dimensionless) | — | — |
| $L$ | Unbraced length of column | mm | in or ft |
| $KL$ | Effective length | mm | in or ft |
| $r$ | Radius of gyration of cross-section about the axis of buckling | mm | in |
| $KL/r$ | Slenderness ratio (dimensionless) | — | — |
| $A_g$ | Gross cross-sectional area | mm² | in² |
| $P_n$ | Nominal compressive strength | kN | kips |
| $P_u$ | Required strength (factored load, LRFD) | kN | kips |
| $P_a$ | Required strength (service load, ASD) | kN | kips |
| $\phi_c$ | Resistance factor for compression = 0.90 | — | — |
| $\Omega_c$ | Safety factor for compression = 1.67 | — | — |
| $\lambda$ | Width-to-thickness ratio of a plate element | — | — |
| $\lambda_r$ | Slender element limit (compression, Table B4.1a) | — | — |
| $\lambda_p$ | Compact element limit (flexure, Table B4.1b) | — | — |
| $b$ | Width of an unstiffened element (e.g., half-flange $b_f/2$) | mm | in |
| $t$ | Thickness of a plate element ($t_f$ or $t_w$) | mm | in |
| $h$ | Clear distance between flanges in the web of a W-shape | mm | in |
| $I$ | Second moment of area (moment of inertia) | mm⁴ | in⁴ |

---

## 4. Derivation

### Step 1 — Euler's differential equation of the deflected column

Consider an axially loaded, initially straight column of length $L$, with pin supports at both ends (no rotational restraint). Let $y(x)$ be the lateral deflection at a distance $x$ from one end, and let $P$ be the applied compressive load. Taking a free-body diagram of the upper portion of the deflected column and summing moments about the cut section, the internal bending moment is $M = -P\,y$ (the load $P$ acting at the eccentric position $y$ creates a restoring moment, but the sign convention for the elastic curve gives a negative curvature):

$$EI\,\frac{d^2 y}{dx^2} = -P\,y$$

Rearranging:

$$EI\,y'' + P\,y = 0$$

This is a second-order linear ODE with constant coefficients. Let $k^2 = P/(EI)$; the equation becomes $y'' + k^2 y = 0$.

*(Source: Timoshenko & Gere, Theory of Elastic Stability, 2nd Ed., §1.2)*

### Step 2 — Apply boundary conditions (pinned–pinned) to obtain the Euler load

The general solution is:

$$y(x) = A\sin(kx) + B\cos(kx)$$

**Boundary conditions** for a pin–pin column:
- $y(0) = 0 \Rightarrow B = 0$
- $y(L) = 0 \Rightarrow A\sin(kL) = 0$

For a non-trivial solution ($A \neq 0$), we need $\sin(kL) = 0$, which requires $kL = n\pi$ for $n = 1, 2, 3, \ldots$ The first (critical) mode $n=1$ gives the lowest load:

$$k = \frac{\pi}{L} \Rightarrow \frac{P}{EI} = \frac{\pi^2}{L^2}$$

$$\boxed{P_e = \frac{\pi^2 EI}{L^2}} \tag{Euler critical load}$$

The buckled shape is a half-sine wave: $y(x) = A\sin(\pi x / L)$. The amplitude $A$ is indeterminate at this bifurcation point — linear buckling theory only predicts the **load level** at which buckling initiates, not the post-buckling amplitude.

*(Source: Timoshenko & Gere, §1.2; Segui, Steel Design, 6th Ed., Ch. 4)*

### Step 3 — Convert to critical stress using radius of gyration

Divide both sides of $P_e$ by the gross area $A_g$, and substitute $I = r^2 A_g$:

$$F_e = \frac{P_e}{A_g} = \frac{\pi^2 EI}{L^2 A_g} = \frac{\pi^2 E (r^2 A_g)}{L^2 A_g} = \frac{\pi^2 E}{(L/r)^2}$$

$$\boxed{F_e = \frac{\pi^2 E}{(L/r)^2}} \tag{Euler stress, pin–pin}$$

This is valid only for elastic, pin-ended columns with no imperfections or residual stresses.

*(Source: Segui, §4.2; AISC 360-22 §E3-4 notation)*

### Step 4 — Introduce effective length $KL$ to account for end conditions

Real columns rarely have perfectly pinned ends. Rotational and translational restraints at the supports alter the buckled shape and thus the buckling load. The effective length concept replaces a column with any end conditions by an **equivalent pin-ended column** of length $KL$:

$$F_e = \frac{\pi^2 E}{(KL/r)^2} \tag{AISC 360-22 §E3-4}$$

The effective length factor $K$ depends on end conditions:

| Condition | Theoretical $K$ | Recommended Design $K$ (AISC Table C-A-7.2) |
|-----------|----------------|----------------------------------------------|
| Both ends pinned | 1.0 | 1.0 |
| Both ends fixed | 0.5 | 0.65 |
| One end fixed, one end pinned | 0.699 | 0.80 |
| One end fixed, one end free (flagpole) | 2.0 | 2.10 |
| Both ends fixed, with sway | 1.0 | 1.20 |

For columns in frames, $K$ is determined using the **alignment chart** (AISC Commentary to Appendix 7), which accounts for the relative stiffnesses of columns and beams framing into each joint. In sway frames, $K > 1.0$ and columns are much more susceptible to buckling.

*(Source: AISC 360-22 Commentary §C-A-7; Segui, §4.3)*

### Step 5 — Why inelastic buckling occurs: residual stresses and the tangent modulus

For stocky columns with $KL/r$ below the transition value, the Euler stress $F_e$ would exceed the yield stress $F_y$. In reality, the column yields partially before buckling due to **residual stresses**:

- **Residual stresses** are locked-in stresses from uneven cooling after hot-rolling. In a W-shape, the flange tips cool faster than the flange–web junction, causing compressive residual stresses at the tips (typically $0.3 F_y$ for rolled shapes) and tensile residual stresses at the web–flange junction.
- When an external compressive load is applied, the **flange tips** (which already have compressive residual stress) yield first, at a load less than $P_y = F_y A_g$.
- As the load increases, the yielded zones spread inward. The remaining elastic core carries additional load. The **tangent modulus** $E_t < E$ governs buckling of this partially yielded section.
- The result is that inelastic buckling occurs at a stress **lower** than $F_e$ but **higher** than would be predicted by simple elastic buckling with a corrected $E_t$ (because the Shanley theory shows that buckling can begin before full plasticity).

The AISC column curve (§E3) bypasses the need to explicitly compute residual stresses by using an empirical formulation calibrated to test data.

*(Source: Galambos & Surovek, Structural Stability of Steel, 2008, §4.3; Segui, §4.4)*

### Step 6 — The AISC column curve: empirical fit to test data

The AISC inelastic buckling equation:

$$F_{cr} = \left[0.658^{F_y/F_e}\right] F_y$$

was introduced by Bjorhovde (1972) as a fit to column test data. It can be rewritten by substituting $\lambda_c = \sqrt{F_y/F_e}$ (the column slenderness parameter used in older AISC editions):

$$F_{cr} = \left[0.658^{\lambda_c^2}\right] F_y = e^{-0.4191\,\lambda_c^2}\,F_y \quad (\text{since } 0.658 = e^{-0.4191})$$

- When $KL/r \to 0$ (very stocky), $F_e \to \infty$, $F_y/F_e \to 0$, and $0.658^0 = 1$, so $F_{cr} \to F_y$ ✓ (squash load).
- When $KL/r$ is large but still at the transition point, the inelastic curve blends continuously into the elastic equation $0.877 F_e$ (see Step 7).
- The factor 0.877 in the elastic range represents a 12 % reduction from the Euler load to account for initial out-of-straightness (geometric imperfections), consistent with an assumed bow of $L/1500$.

*(Source: Bjorhovde, 1972, as cited in AISC Commentary §C-E3; McCormac & Csernak, Structural Steel Design, 6th Ed., §5.3)*

### Step 7 — Derive the transition slenderness $4.71\sqrt{E/F_y}$

At the transition, both equations must give the same $F_{cr}$. Set the elastic formula equal to the inelastic formula and solve for $KL/r$:

$$0.877\,F_e = \left[0.658^{F_y/F_e}\right] F_y$$

AISC defines the transition at $F_e = 0.44\,F_y$ (i.e., the elastic equation applies when the Euler stress drops below 44 % of yield). Setting $F_e = 0.44\,F_y$:

$$\frac{\pi^2 E}{(KL/r)^2} = 0.44\,F_y$$

$$(KL/r)^2 = \frac{\pi^2 E}{0.44\,F_y}$$

$$\frac{KL}{r} = \pi\sqrt{\frac{E}{0.44\,F_y}} = \pi \times \frac{1}{\sqrt{0.44}}\sqrt{\frac{E}{F_y}} = \pi \times 1.508\sqrt{\frac{E}{F_y}} \approx 4.71\sqrt{\frac{E}{F_y}}$$

**Verification:** For A992 steel ($F_y = 50$ ksi, $E = 29{,}000$ ksi):

$$4.71\sqrt{\frac{29{,}000}{50}} = 4.71 \times 24.08 = 113.4$$

Columns with $KL/r \leq 113.4$ use the inelastic curve; those with $KL/r > 113.4$ use $0.877 F_e$.

*(Source: AISC 360-22 §E3; Segui, §4.2)*

### Step 8 — Local buckling check: why slender elements reduce strength

A compression member is composed of plate elements (flanges, webs, HSS walls). Each plate element can buckle locally — like the wall of a thin-walled box under axial compression — before the overall column buckles. The slenderness of a plate element is characterized by $\lambda = b/t$ (unstiffened, e.g., W-flange half-width) or $\lambda = h/t_w$ (stiffened, e.g., web clear height).

**AISC 360-22 §E2** classifies elements as:
- **Non-slender** ($\lambda \leq \lambda_r$): The element does not buckle locally before the column reaches $F_{cr}$; use full $A_g$. This is the common case for standard W-shapes in A992 steel.
- **Slender** ($\lambda > \lambda_r$): Local buckling reduces the effective area. Per **AISC §E7**, compute an effective area $A_{eff}$ using a reduced effective width $b_e$, then use $P_n = F_{cr} A_{eff}$ (or an equivalent stress approach). The derivation of $b_e$ follows Winter's effective width formula for plates. At the undergraduate level, the key takeaway is: **always check $\lambda$ vs $\lambda_r$ first; if slender, the §E7 reduction is required**.

The compact limit $\lambda_p$ (Table B4.1b) is a **flexural member** concept. It is the maximum $b/t$ at which a cross-section can develop its full plastic moment $M_p$ and sustain inelastic rotation for plastic hinge formation. It is listed in these notes because beam-column design (§H1) and the Chapter F beam design require it, but it does **not** appear in the column (Chapter E) strength calculation directly.

*(Source: AISC 360-22 §E7, Table B4.1a; Segui, §4.6)*

---

## 5. Design / Application Procedure

The following procedure follows AISC 360-22 Chapter E for a doubly symmetric I-shaped or HSS compression member. Steps correspond directly to code sections.

1. **Establish material properties.** Record the specified minimum yield stress $F_y$ and modulus of elasticity $E$. For ASTM A992 W-shapes: $F_y = 50$ ksi (345 MPa), $E = 29{,}000$ ksi (200{,}000 MPa). *(AISC 360-22 §A3.1)*

2. **Identify section properties.** From the AISC Steel Construction Manual (16th Ed.), record: $A_g$, $r_x$, $r_y$, $b_f$, $t_f$, $d$, $t_w$, and $h$ (or $h/t_w$ directly tabulated as $(h/t_w)$ in the Manual). For HSS, use the HSS tables for $A_g$, $r$, and $b/t$ or $h/t$.

3. **Determine effective length $KL$ for both axes.** Apply the effective length factor $K$ from AISC Commentary Table C-A-7.2 (idealized conditions) or the alignment chart (frames). Multiply by the unbraced length $L$ in each direction. Strong-axis unbraced length $L_x$ and weak-axis unbraced length $L_y$ may differ if intermediate bracing is present. *(AISC 360-22 §E2, Commentary Appendix 7)*

4. **Compute $KL/r$ for both axes; identify the governing (larger) value.**
   $$\frac{KL_x}{r_x} \quad \text{and} \quad \frac{KL_y}{r_y}$$
   The larger ratio controls column strength. For standard W-shapes $r_y < r_x$, so the weak axis usually governs when $KL$ is the same for both axes.

5. **Check local buckling ($\lambda$ vs. $\lambda_r$, AISC Table B4.1a).**
   - **Flanges of W-shapes:** $\lambda = b_f/(2t_f)$; compare to $\lambda_r = 0.56\sqrt{E/F_y}$.
   - **Webs of W-shapes:** $\lambda = h/t_w$; compare to $\lambda_r = 1.49\sqrt{E/F_y}$.
   - **HSS walls:** $\lambda = b/t$ (or $h/t$); compare to $\lambda_r = 1.40\sqrt{E/F_y}$.
   - If all elements satisfy $\lambda \leq \lambda_r$: section is **non-slender** → proceed with $A_g$. *(AISC 360-22 §E2)*
   - If any element has $\lambda > \lambda_r$: section is **slender** → use AISC §E7 to compute $A_{eff}$; substitute $A_{eff}$ for $A_g$ in Step 8.

6. **Compute the Euler elastic buckling stress $F_e$** using the governing $KL/r$:
   $$F_e = \frac{\pi^2 E}{(KL/r)^2} \tag{AISC §E3-4}$$

7. **Select the correct $F_{cr}$ equation** by comparing $KL/r$ to the transition value $4.71\sqrt{E/F_y}$ (equivalently, compare $F_e$ to $0.44 F_y$):
   - If $KL/r \leq 4.71\sqrt{E/F_y}$ (inelastic buckling):
     $$F_{cr} = \left[0.658^{F_y/F_e}\right] F_y \tag{AISC §E3-2}$$
   - If $KL/r > 4.71\sqrt{E/F_y}$ (elastic buckling):
     $$F_{cr} = 0.877\,F_e \tag{AISC §E3-3}$$

8. **Compute nominal compressive strength:**
   $$P_n = F_{cr} \times A_g \quad (\text{or } F_{cr} \times A_{eff} \text{ if slender}) \tag{AISC §E3-1}$$

9. **Apply the design check:**
   - **LRFD:** $\phi_c P_n \geq P_u$ where $\phi_c = 0.90$. *(AISC §E1)*
   - **ASD:** $P_n/\Omega_c \geq P_a$ where $\Omega_c = 1.67$. *(AISC §E1)*
   - If demand exceeds capacity, select a heavier section or reduce the unbraced length (add intermediate bracing), then repeat from Step 2.

10. **Serviceability check:** Verify that the governing slenderness ratio does not exceed 200:
    $$\frac{KL}{r} \leq 200 \tag{AISC 360-22 §E2, Commentary}$$
    This is a recommended (not mandatory) limit that guards against excessive flexibility, handling damage, vibration sensitivity, and large second-order effects. Columns exceeding $KL/r = 200$ are rarely economical.

---

## 6. Worked Example

**Problem:** A W10×49 column of ASTM A992 steel is used in a braced frame. Both ends are pin-connected (no rotational restraint). The unbraced length is $L = 20$ ft for both axes. Determine whether the column can support a factored axial load of $P_u = 300$ kips (LRFD). Also compute the ASD allowable load for reference.

**Given:**
- Section: W10×49, ASTM A992
- $F_y = 50$ ksi, $E = 29{,}000$ ksi
- $A_g = 14.4\ \text{in}^2$
- $r_x = 4.35\ \text{in}$, $r_y = 2.54\ \text{in}$
- $d = 10.0\ \text{in}$, $b_f = 10.0\ \text{in}$, $t_f = 0.560\ \text{in}$, $t_w = 0.340\ \text{in}$
- $b_f/(2t_f) = 10.0/(2 \times 0.560) = 8.93$
- $h/t_w \approx 23.5$ (using tabulated values from AISC Manual, 16th Ed.)
- $K = 1.0$ for both axes (pin–pin)
- $L = 20\ \text{ft} = 240\ \text{in}$

**Required:** (a) Check LRFD adequacy for $P_u = 300$ kips; (b) compute ASD allowable load.

---

**Solution:**

**Step 1 — Compute effective slenderness ratios for both axes.**

Strong axis:
$$\frac{KL_x}{r_x} = \frac{1.0 \times 240}{4.35} = 55.2$$

Weak axis:
$$\frac{KL_y}{r_y} = \frac{1.0 \times 240}{2.54} = 94.5 \quad \leftarrow \textbf{governs (larger value)}$$

**Step 2 — Check local buckling (AISC Table B4.1a).**

Compute transition slenderness limits for $F_y = 50$ ksi, $E = 29{,}000$ ksi:

*Flange (unstiffened element, Case 1):*
$$\lambda_r^{\,\text{flange}} = 0.56\sqrt{\frac{E}{F_y}} = 0.56\sqrt{\frac{29{,}000}{50}} = 0.56 \times 24.08 = 13.49$$

$$\lambda_{\text{flange}} = \frac{b_f}{2t_f} = 8.93 \quad < \quad 13.49 \quad \checkmark \text{ (non-slender)}$$

*Web (stiffened element, Case 5):*
$$\lambda_r^{\,\text{web}} = 1.49\sqrt{\frac{E}{F_y}} = 1.49\sqrt{\frac{29{,}000}{50}} = 1.49 \times 24.08 = 35.88$$

$$\lambda_{\text{web}} = \frac{h}{t_w} = 23.5 \quad < \quad 35.88 \quad \checkmark \text{ (non-slender)}$$

**Conclusion:** All plate elements are non-slender. Use full $A_g = 14.4\ \text{in}^2$. No §E7 reduction needed.

**Step 3 — Compute transition slenderness and identify buckling regime.**

$$4.71\sqrt{\frac{E}{F_y}} = 4.71\sqrt{\frac{29{,}000}{50}} = 4.71 \times 24.08 = 113.4$$

$$\frac{KL}{r} = 94.5 \quad \leq \quad 113.4 \quad \Rightarrow \textbf{Inelastic buckling governs (§E3-2)}$$

**Step 4 — Compute the Euler elastic buckling stress.**

$$F_e = \frac{\pi^2 E}{\left(KL/r\right)^2} = \frac{\pi^2 \times 29{,}000}{(94.5)^2} = \frac{286{,}279}{8{,}930} = 32.06 \text{ ksi}$$

**Step 5 — Compute the critical stress $F_{cr}$ (inelastic branch).**

$$\frac{F_y}{F_e} = \frac{50}{32.06} = 1.560$$

$$F_{cr} = \left[0.658^{1.560}\right] \times 50$$

Evaluate: $0.658^{1.560} = e^{1.560 \times \ln(0.658)} = e^{1.560 \times (-0.4191)} = e^{-0.6538} = 0.5201$

$$F_{cr} = 0.5201 \times 50 = 26.0 \text{ ksi}$$

**Step 6 — Compute nominal strength.**

$$P_n = F_{cr} \times A_g = 26.0 \times 14.4 = 374.5 \text{ kips}$$

**Step 7 — LRFD design check.**

$$\phi_c P_n = 0.90 \times 374.5 = \mathbf{337.1 \text{ kips}}$$

$$P_u = 300 \text{ kips} \quad \leq \quad \phi_c P_n = 337.1 \text{ kips} \quad \checkmark$$

Demand-to-capacity ratio:
$$\frac{P_u}{\phi_c P_n} = \frac{300}{337.1} = 0.89 \quad (89\% \text{ utilization})$$

The W10×49 is **adequate** for the 300-kip factored load with 11% reserve capacity.

**Step 8 — ASD allowable load (for reference).**

$$\frac{P_n}{\Omega_c} = \frac{374.5}{1.67} = 224.3 \text{ kips}$$

This is the maximum service (unfactored) load the column may carry under ASD. Note that the LRFD result of $337.1$ kips and the ASD result of $224.3$ kips are consistent: $337.1 / 1.5 \approx 225$ kips, reflecting the typical $D + L$ load combination factor relationship between the two methods.

**Step 9 — Serviceability check.**

$$\frac{KL}{r} = 94.5 \quad \leq \quad 200 \quad \checkmark$$

**Result:** The W10×49 (A992, $K=1.0$, $L=20$ ft) has a LRFD design strength of $\phi_c P_n = 337.1$ kips, which exceeds the required $P_u = 300$ kips (D/C = 0.89). The section is non-slender, inelastic buckling governs about the weak axis, and the slenderness ratio is well within the 200 limit.

---

## 7. Common Mistakes & Pitfalls

- **Forgetting to check both axes.** Many students compute only $KL_y/r_y$ (weak-axis) and assume it governs. However, if intermediate bracing is present on the weak axis but not the strong axis, or if the bay dimensions differ, strong-axis buckling may govern. **Always compute both $KL/r$ values and use the larger one.**

- **Using $L$ instead of $KL$.** Substituting the actual unbraced length $L$ without multiplying by $K$ underestimates the effective slenderness. For a fixed–fixed column ($K = 0.65$) this over-conservatism is benign but wasteful; for a column with sway ($K = 1.2$ to $2.0$) it can be dangerously unconservative. **Always apply $K$ before computing the slenderness ratio.**

- **Using $r_x$ when $r_y$ governs.** For standard W-shapes, $r_x > r_y$, meaning $KL/r_y > KL/r_x$ when both unbraced lengths are equal. Using $r_x$ produces a lower (unconservative) slenderness ratio. **Pick the axis that maximizes $KL/r$.**

- **Skipping the local buckling check.** Standard W-shapes in A992 steel are almost always non-slender under compression, so engineers often skip this step. However, built-up sections, light gauge sections, HSS with large $b/t$, or older A36 sections with thin flanges may be slender. **Always verify $\lambda \leq \lambda_r$ before using $A_g$.**

- **Misreading $K$ from the alignment chart.** The alignment chart requires computing the stiffness ratio $G = \sum(EI/L)_{\text{col}} / \sum(EI/L)_{\text{beam}}$ at each end. Common errors include (a) using beams pinned at the far end without applying the far-end pin correction factor of 1.5, (b) ignoring beams that frame in the perpendicular direction, and (c) reading from the wrong chart (braced vs. unbraced frame). **Use the correct chart (sidesway inhibited vs. sidesway uninhibited) and apply far-end corrections.**

- **Applying the wrong $F_{cr}$ formula branch.** Using the inelastic formula when $KL/r > 4.71\sqrt{E/F_y}$ (elastic regime) gives an unconservative $F_{cr}$ because the inelastic formula predicts stresses above the elastic curve in that range. Using the elastic formula when $KL/r < 4.71\sqrt{E/F_y}$ gives an overly conservative result. **Compare $KL/r$ to $4.71\sqrt{E/F_y}$ explicitly every time; do not guess which branch applies.**

- **Neglecting the $KL/r \leq 200$ serviceability limit.** Columns with very high slenderness ratios are structurally inefficient, prone to damage during erection, and sensitive to vibration. AISC §E2 recommends $KL/r \leq 200$ as a practical upper bound. A column violating this limit may technically have a non-zero $\phi_c P_n$, but should be redesigned. **Check slenderness against 200 as a final quality-control step.**

---

## 8. Connections to Other Topics

- **Structural Stability — Euler Buckling (Area 9-A):** The governing equation of the deflected column, $EI\,y'' + P\,y = 0$, derived in Step 1 above, is the foundation of classical stability theory. Area 9 extends this to imperfect columns (Southwell plot, Area 9-B), inelastic buckling (tangent-modulus theory, Area 9-C), and energy methods (Rayleigh-Ritz, Area 9-G). The AISC column curve is the practitioner's translation of that academic stability theory into a design tool.

- **Tension Member Design (Area 6-B):** Tension and compression members are the two primary categories of axially loaded members. The contrast is instructive: tension members fail by material fracture or yielding on the net or gross section — a **strength** limit state with no buckling concern. Compression members fail by buckling — a **stability** limit state controlled by geometry. Both use $\phi = 0.90$ for LRFD and both require a gross area check, but the physics and failure modes are fundamentally different.

- **Beam-Column Design (Area 6-F):** In practice, most columns also carry bending moments (from wind, seismic, frame action, or eccentric connections). The AISC interaction equations for beam-columns (§H1) combine $P_u / (\phi_c P_n)$ with $M_u / (\phi_b M_n)$. A strong grasp of $P_n$ from this note is prerequisite to understanding beam-column design. The slenderness ratio $KL/r$ computed here feeds directly into the $P_n$ term of the interaction equation.

- **Lateral-Torsional Buckling of Beams (Area 6-D):** Beams under flexure can buckle laterally out-of-plane — a phenomenon structurally analogous to column flexural buckling but involving both lateral bending and torsion. The compact limit $\lambda_p$ introduced here (for flanges in flexure) is used in Chapter F to determine whether a beam can reach $M_p$ before LTB or local flange buckling controls. The same width-to-thickness language ($\lambda, \lambda_p, \lambda_r$) appears in both chapters.

- **Matrix Structural Analysis (Area 4):** The column stiffness matrix for a compression member must be augmented by a **geometric stiffness matrix** $k_G$ to capture the destabilizing effect of axial load on lateral stiffness. This leads directly to the eigenvalue problem $(\mathbf{K} - \lambda \mathbf{K}_G)\mathbf{v} = \mathbf{0}$, where $\lambda$ is the load multiplier at buckling — the matrix-analysis counterpart to the Euler load derived in this note.

- **Structural Stability — Effective Length Theory (Area 9):** The concept of effective length factor $K$ and the alignment chart originate in the stability analysis of frames. For sway frames ($K > 1$), the interaction between the column's axial load and the frame's sidesway produces second-order ($P$-$\Delta$) moments that amplify deformations and reduce the effective buckling load. Area 9 treats this rigorously using eigenvalue stability analysis and the concept of story-level buckling.

---

## 9. Further Reading

| Resource | Where to Look |
|----------|--------------|
| AISC 360-22, *Specification for Structural Steel Buildings* | Chapter E (Compression), §E3 (Flexural Buckling), §E7 (Slender Elements), Table B4.1a (local buckling limits) |
| AISC Steel Construction Manual, 16th Edition | Part 4 (Column Design), Table 4-1a through 4-14 (column load tables for W-shapes), Commentary to Chapter E |
| Segui, W. T., *Steel Design*, 6th Edition (Cengage, 2017) | Chapter 4 (Compression Members): §4.2 (Euler load), §4.3 (Effective length), §4.4 (AISC column curve), §4.6 (Local buckling) |
| McCormac, J. C. & Csernak, S. F., *Structural Steel Design*, 6th Edition (Pearson, 2018) | Chapter 5 (Columns): §5.2 (Slenderness), §5.3 (AISC column curve), §5.5 (Design examples) |
| Gere, J. M. & Goodno, B. J., *Mechanics of Materials*, 9th Edition (Cengage, 2018) | Chapter 11 (Columns): §11.2 (Euler buckling), §11.3 (Critical load), §11.5 (End conditions) |
| Timoshenko, S. P. & Gere, J. M., *Theory of Elastic Stability*, 2nd Edition (McGraw-Hill, 1961) | Chapter 1 (Beam-Columns), Chapter 5 (Torsional Buckling) — for rigorous derivations beyond undergraduate level |
| Galambos, T. V. & Surovek, A. E., *Structural Stability of Steel*, 1st Edition (Wiley, 2008) | Chapter 4 (Columns with residual stresses), Chapter 5 (Frame stability) |

---

## 10. Quick Self-Check

- [ ] I can write the Euler elastic buckling stress formula $F_e = \pi^2 E / (KL/r)^2$ from memory, define every symbol, and explain what each factor represents physically.
- [ ] I understand why the AISC column curve uses $0.658^{F_y/F_e}$ in the inelastic range and can explain the roles of residual stresses and initial imperfections in reducing real column strength below the Euler load.
- [ ] I can reproduce the derivation of the transition slenderness $4.71\sqrt{E/F_y}$ by setting $F_e = 0.44 F_y$ and solving for $KL/r$, and I can identify which formula branch to use for any given $KL/r$.
- [ ] I have worked through the W10×49 example step by step, verified each numerical result independently, and confirmed that the demand-to-capacity ratio is 0.89.
- [ ] I can connect this topic to at least three other subjects: I can explain how $P_n$ from this note feeds into the beam-column interaction equation (§H1), how the Euler derivation links to the matrix geometric stiffness problem, and how $\lambda_r$ for compression differs from $\lambda_p$ for flexure.

---

*Created by Structural Engineering Tutor • 2026-03-18*
