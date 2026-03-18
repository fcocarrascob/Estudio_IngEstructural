# Tension Member Design (Yielding & Fracture)

**Subject area:** Steel Design (AISC 360-22)
**Design standard / primary reference:** AISC 360-22 §D; AISC Steel Construction Manual, 16th Ed.
**Depth level:** Graduate — rigorous derivation
**Estimated study time:** 110 minutes

---

## 1. Introduction & Motivation

Tension members are among the most common structural elements in steel construction. They appear as chord members in roof trusses, hangers in floor framing, diagonal bracing in lateral-force-resisting systems, tie rods in arch bridges, and cable stays in long-span roofs. Unlike compression members, tension members do not buckle — they simply stretch. This makes them highly efficient: they can mobilize the full cross-sectional area of steel to resist load.

Despite this simplicity, tension member design is not trivial. The member can fail in two fundamentally different ways: (1) the gross cross-section can yield over its full length, dissipating energy in a ductile manner; or (2) the net cross-section at the connection region can fracture suddenly through the reduced area remaining after bolt holes are drilled. Fracture is a brittle, sudden failure mode and must be guarded against with a more conservative resistance factor. Understanding the interplay between these two limit states — and learning how to compute the effective net area that accounts for shear lag — is the core skill of tension member design under AISC 360-22.

This note also introduces block shear as a third connection-region limit state, discusses the shear lag factor U, and connects net-area calculations to hole geometry and bolt-line layout. By the end, you will be able to fully design and check a W-shape tension member using both LRFD and ASD methods.

---

## 2. Key Concepts & Definitions

| Term | Symbol | Definition |
|------|--------|------------|
| Gross area | $A_g$ | Total cross-sectional area of the member, ignoring holes (in², mm²) |
| Net area | $A_n$ | Gross area minus the material removed by bolt holes along the critical path |
| Effective net area | $A_e$ | Net area reduced by shear lag factor: $A_e = U A_n$ |
| Shear lag factor | $U$ | Reduction factor (≤ 1.0) accounting for uneven stress transfer at connections |
| Yield strength | $F_y$ | Stress at which steel begins to deform plastically (ksi or MPa) |
| Ultimate tensile strength | $F_u$ | Stress at which fracture initiates; always $F_u > F_y$ for structural steels |
| Factored tensile demand | $P_u$ | Required strength under LRFD load combinations (kips) |
| Allowable tensile demand | $P_a$ | Required strength under ASD load combinations (kips) |
| Nominal strength | $P_n$ | Theoretical member capacity before applying $\phi$ or $\Omega$ |
| LRFD resistance factor | $\phi_t$ | 0.90 for yielding; 0.75 for fracture — multiplied by $P_n$ |
| ASD safety factor | $\Omega_t$ | 1.67 for yielding; 2.00 for fracture — divides $P_n$ |
| Hole diameter for design | $d_h$ | Bolt diameter + 1/8 in total (bolt dia + 1/16 in clearance + 1/16 in punch damage) |
| Bolt spacing (pitch) | $s$ | Center-to-center distance along the length between consecutive bolt holes in the same line |
| Gauge | $g$ | Center-to-center distance transverse to the load between two bolt lines |
| Slenderness ratio | $L/r$ | Ratio of unbraced length to minimum radius of gyration; recommended ≤ 300 for tension |

---

## 3. Governing Equations

### 3.1 Limit State 1 — Gross-Section Yielding

$$
P_n = F_y \, A_g
\tag{AISC 360-22 §D2(a)}
$$

**LRFD:** $\phi_t = 0.90 \Rightarrow \phi_t P_n = 0.90 \, F_y \, A_g \geq P_u$

**ASD:** $\Omega_t = 1.67 \Rightarrow P_n / \Omega_t = F_y A_g / 1.67 \geq P_a$

| Symbol | Description | US Customary Units | SI Units |
|--------|-------------|-------------------|----------|
| $F_y$ | Yield stress of steel | ksi | MPa |
| $A_g$ | Gross cross-sectional area | in² | mm² |
| $P_n$ | Nominal tensile strength (yielding) | kips | kN |

---

### 3.2 Limit State 2 — Net-Section Fracture

$$
P_n = F_u \, A_e
\tag{AISC 360-22 §D2(b)}
$$

**LRFD:** $\phi_t = 0.75 \Rightarrow \phi_t P_n = 0.75 \, F_u \, A_e \geq P_u$

**ASD:** $\Omega_t = 2.00 \Rightarrow P_n / \Omega_t = F_u A_e / 2.00 \geq P_a$

| Symbol | Description | US Customary Units | SI Units |
|--------|-------------|-------------------|----------|
| $F_u$ | Ultimate (tensile rupture) stress | ksi | MPa |
| $A_e$ | Effective net area | in² | mm² |
| $P_n$ | Nominal tensile strength (fracture) | kips | kN |

---

### 3.3 Effective Net Area

$$
A_e = U \, A_n
\tag{AISC 360-22 §D3-1}
$$

| Symbol | Description | US Customary | SI |
|--------|-------------|-------------|-----|
| $U$ | Shear lag factor (see Table D3.1) | dimensionless | dimensionless |
| $A_n$ | Net area along critical failure path | in² | mm² |

---

### 3.4 Net Area — Straight and Staggered Hole Paths

For a plate or flange of thickness $t$, with bolt holes of diameter $d_h$, the net area along any potential failure path is:

$$
A_n = A_g - \sum \left(d_h \cdot t\right) + \sum \frac{s^2}{4g} \cdot t
\tag{AISC 360-22 §B4.3b}
$$

The $s^2/(4g)$ correction applies only to **diagonal segments** of a staggered path. Straight paths have no staggered correction. The designer must check **all plausible failure paths** and take the **minimum** $A_n$.

| Symbol | Description | US Customary | SI |
|--------|-------------|-------------|-----|
| $d_h$ | Design hole diameter (bolt dia + 1/8 in) | in | mm |
| $t$ | Thickness of element being reduced | in | mm |
| $s$ | Bolt spacing (pitch) along member axis | in | mm |
| $g$ | Transverse gauge between bolt lines | in | mm |

---

### 3.5 Block Shear (Third Limit State — Reference)

At the connection, a block of material can tear out combining shear rupture on one plane and tension rupture on a perpendicular plane. Per AISC 360-22 §J4.3:

$$
R_n = 0.60 \, F_u \, A_{nv} + U_{bs} \, F_u \, A_{nt} \leq 0.60 \, F_y \, A_{gv} + U_{bs} \, F_u \, A_{nt}
\tag{AISC 360-22 §J4.3-1}
$$

$\phi = 0.75$ (LRFD), $\Omega = 2.00$ (ASD).

$U_{bs} = 1.0$ for uniform tension stress; $U_{bs} = 0.5$ when tension stress is non-uniform (e.g., beam web connections). Block shear is covered in full depth under Topic G (Bolted Connections, §J4).

| Symbol | Description |
|--------|-------------|
| $A_{nv}$ | Net area subject to shear (along bolt lines) |
| $A_{nt}$ | Net area subject to tension (perpendicular to bolt lines) |
| $A_{gv}$ | Gross area subject to shear |
| $U_{bs}$ | Tension stress uniformity factor |

---

## 4. Derivation

The following steps build up the tension member design model from physical reasoning.

**Step 1 — Why two limit states?**

When you pull a steel bar in tension, two things can happen depending on where you are looking:
- Away from the connection, the full gross area $A_g$ is available. The member yields over its full length first. This is ductile and desirable: $P_n = F_y A_g$.
- At the connection, bolt holes have been drilled, reducing the cross-sectional area. If the reduced area, corrected for incomplete load transfer (shear lag), reaches the fracture stress $F_u$, the member tears apart suddenly. This is brittle and must be guarded against: $P_n = F_u A_e$.

Both limit states must be checked. The **governing (lower) capacity** controls design.

**Step 2 — Physical meaning of gross-section yielding**

The yield stress $F_y$ represents the point where steel transitions from elastic to plastic behavior. When the average stress on the gross section reaches $F_y$, the entire member length has yielded. Elongation becomes large and visible — this is the intended ductile failure mode. Using $\phi_t = 0.90$ reflects that material variability is modest and the failure mode is ductile.

**Step 3 — Why is $\phi_t$ lower for fracture (0.75 vs. 0.90)?**

Fracture depends on $F_u$, which has more variability than $F_y$, especially near stress concentrations at holes. Additionally, fracture is sudden — there is no warning. AISC assigns $\phi_t = 0.75$ to reflect both greater uncertainty and the undesirable brittle failure mode. The ASD analog is $\Omega_t = 2.00$ versus $\Omega_t = 1.67$ for yielding.

**Step 4 — Hole diameter deduction rule**

Bolt holes are punched (or drilled) to the bolt diameter plus a 1/16-in clearance for installation. The punching process also damages approximately 1/16 in of metal around the hole perimeter. Therefore, the total deduction per hole is:

$$
d_h = d_{bolt} + \frac{1}{16} + \frac{1}{16} = d_{bolt} + \frac{1}{8} \text{ in}
\tag{AISC 360-22 §B4.3b}
$$

For a 3/4-in bolt: $d_h = 3/4 + 1/8 = 7/8$ in.

**Step 5 — Staggered hole path correction ($s^2/4g$)**

If bolt holes are staggered, a diagonal failure path passes through fewer holes but travels a longer route through the material. The net area along a diagonal path is:
- **Subtract** all hole widths $d_h$ that the path crosses.
- **Add back** the $s^2/(4g)$ term for each diagonal segment, which accounts for the additional path length.

This empirical formula (Cochrane, 1922, adopted by AISC) gives a smooth transition between the straight-path result and the path that avoids all holes. The designer must evaluate **all possible paths** (straight and staggered) and use the minimum $A_n$.

**Step 6 — Shear lag and the $U$ factor**

When only part of a cross-section is connected (e.g., only the flanges of a W-shape, or only one leg of an angle), the load must "spread in" from the connected elements to the unconnected elements via shear. This means the unconnected portion carries less stress than the connected portion — the net section is not fully effective. AISC 360-22 §D3 defines the shear lag factor:

$$
U = 1 - \frac{\bar{x}}{L}
\tag{AISC 360-22 Table D3.1, Case 2}
$$

where $\bar{x}$ is the distance from the centroid of the connected element to the connection plane, and $L$ is the connection length (distance from first to last bolt). A longer connection allows more load redistribution, so $U$ approaches 1.0 as $L$ increases.

When **all elements** of the cross-section are connected (e.g., flanges and web all bolted), shear lag does not occur and $U = 1.0$ per Table D3.1 Case 1.

**Step 7 — Governing design strength**

Both limit states are checked. The design strength is the **minimum** of the two:

$$
\phi_t P_n = \min\!\bigl(0.90 \, F_y A_g,\; 0.75 \, F_u A_e\bigr)
$$

The member is adequate if $\phi_t P_n \geq P_u$ (LRFD) or $P_n/\Omega_t \geq P_a$ (ASD).

---

## 5. Design / Application Procedure

Follow these steps for every tension member check or design:

1. **Identify the factored demand.** Determine $P_u$ (LRFD) or $P_a$ (ASD) from the governing load combination per ASCE 7-22 §2.3 or §2.4.

2. **Select or confirm the member section.** Obtain $A_g$, $b_f$, $d$, $t_f$, $t_w$, and $r_y$ (minimum radius of gyration) from AISC Steel Construction Manual tables.

3. **Check slenderness (serviceability guideline).** Compute $L/r$ where $r = r_{\min}$. AISC 360-22 §D1 recommends $L/r \leq 300$ for tension members to avoid excessive vibration and sag. This is not a formal limit state — members may exceed it with engineering judgment — but it should be noted if violated.

4. **Compute gross yielding strength.**
   $$P_n^{(1)} = F_y \, A_g \quad (\text{§D2(a)})$$
   LRFD design strength: $\phi_t P_n^{(1)} = 0.90 \, F_y A_g$.

5. **Determine the bolt-hole diameter.** $d_h = d_{bolt} + 1/8$ in.

6. **Identify the critical failure path for net area.** Sketch all possible straight and staggered paths through the holes at the connection. For each path, apply:
   $$A_n = A_g - \sum(d_h \cdot t) + \sum \frac{s^2}{4g} \cdot t$$
   Use the **minimum** $A_n$ from all paths.

7. **Determine the shear lag factor $U$** from AISC 360-22 Table D3.1 (see Section 2 and the table in Section 3 of this note). For W-shapes with all elements connected, $U = 1.0$. For partial connections, use Case 2 formula or the tabulated values.

8. **Compute effective net area.** $A_e = U \cdot A_n$.

9. **Compute net fracture strength.**
   $$P_n^{(2)} = F_u \, A_e \quad (\text{§D2(b)})$$
   LRFD design strength: $\phi_t P_n^{(2)} = 0.75 \, F_u A_e$.

10. **Check block shear at the connection (§J4.3).** Apply Eq. J4-5 (see Section 3.5). This check governs at short, wide connections. Full procedure is in Topic G of these notes.

11. **Identify the governing limit state.** The member capacity is:
    $$\phi_t P_n = \min\!\bigl(\phi_t P_n^{(1)},\; \phi_t P_n^{(2)},\; \phi R_n^{(\text{block shear})}\bigr)$$

12. **Check adequacy.** LRFD: $\phi_t P_n \geq P_u$ ✓ or ✗. ASD: $P_n/\Omega_t \geq P_a$ ✓ or ✗.

13. **If the section is inadequate,** select a larger section or a section with more favorable connection geometry (higher $U$) and repeat.

---

## 6. Worked Example

### Shear Lag Factor U — Table D3.1 Reference (Selected Cases)

Before the example, the five most representative cases from AISC 360-22 Table D3.1 are reproduced for quick reference:

| Case | Connection Configuration | $U$ Value |
|------|--------------------------|-----------|
| 1 | All elements of the cross section are connected (plates, W-shapes fully bolted through flanges AND web) | $U = 1.0$ |
| 2 | General case: any member connected through some but not all elements | $U = 1 - \bar{x}/L$ (where $\bar{x}$ = distance from centroid of connected element to connection plane; $L$ = connection length) |
| 3 | W-shapes or Tees connected by **flanges only**, $b_f \geq 2/3 \, d$, with $\geq 3$ fasteners per line | $U = 0.90$ |
| 4 | W-shapes connected by **web only** (not flanges), with $\geq 3$ fasteners per line | $U = 0.70$ |
| 5 | Single angle connected by **one leg**, with $\geq 3$ fasteners per line | $U = 0.80$ |
| 5† | Single angle connected by **one leg**, with 2 fasteners per line | $U = 0.60$ |
| 6 | Plates connected through the plate itself (full width connected) | $U = 1.0$ |

*† For reference; Case 5 has two sub-rows in Table D3.1.*

---

### Problem Statement

**Member:** W8×31 used as a tension chord in a roof truss.
**Steel grade:** ASTM A992 — $F_y = 50$ ksi, $F_u = 65$ ksi.
**Section properties (from AISC Manual):**

| Property | Value |
|----------|-------|
| $A_g$ | 9.13 in² |
| $d$ (depth) | 8.00 in |
| $b_f$ (flange width) | 8.00 in |
| $t_f$ (flange thickness) | 0.435 in |
| $t_w$ (web thickness) | 0.285 in |
| $r_y$ (minor-axis radius of gyration) | 2.02 in |

**Connection:** 8 bolts total — 4 bolts per flange line, placed in two lines (one on each flange), connecting the W8×31 through **both flanges** to a gusset plate.
- Bolt diameter: 3/4 in (A325-N)
- Bolt spacing (pitch): $s = 3$ in (along member axis)
- Edge distance: 1.5 in
- The connection engages both flanges; the web is **not directly bolted** to the gusset plate (typical clip-angle or direct-flange connection).

**Design hole diameter:** $d_h = 3/4 + 1/8 = 7/8$ in

**Factored tensile demand (LRFD):** $P_u = 320$ kips

**Unbraced length:** $L = 15$ ft = 180 in

**Required:** Check adequacy of the W8×31 for (a) gross yielding, (b) net fracture, (c) block shear note, (d) slenderness.

---

### Solution

#### Step (a) — Gross-Section Yielding

$$P_n^{(1)} = F_y A_g = 50 \times 9.13 = 456.5 \text{ kips}$$

LRFD design strength:
$$\phi_t P_n^{(1)} = 0.90 \times 456.5 = \mathbf{410.9 \text{ kips}}$$

Check: $410.9 \geq 320$ ✅ **PASS** (Gross Yielding)

---

#### Step (b) — Net Area Calculation

The bolts pass through **both flanges**. Each flange has 2 bolt holes across its width (one bolt per line per flange cross-section at each bolt location). Since all 4 bolts in each flange are in a single line (no stagger in this configuration), the holes are in-line along the member length.

**Deduction per hole in the flange (per hole cross-section):**
Each flange has **one bolt hole** per transverse cross-section (one bolt line per flange face).

> In a typical W-shape flange connection with one line of bolts per flange, each bolt removes a hole from the flange thickness at that cross-section. Both flanges are connected, so at any bolt cross-section, holes appear in the top flange and the bottom flange.

At the critical cross-section (where holes are present):

**Area deducted from top flange** (1 hole × $d_h$ × $t_f$):
$$\Delta A_{top} = 1 \times \frac{7}{8} \times 0.435 = 0.381 \text{ in}^2$$

**Area deducted from bottom flange** (same, by symmetry):
$$\Delta A_{bot} = 0.381 \text{ in}^2$$

**Total hole deduction at the critical section:**
$$\sum (d_h \cdot t) = 2 \times 0.381 = 0.762 \text{ in}^2$$

Since the bolt holes are in a straight line (no stagger), there is **no** $s^2/(4g)$ correction:

$$A_n = A_g - \sum(d_h \cdot t) = 9.13 - 0.762 = \mathbf{8.37 \text{ in}^2}$$

> *Note: If the bolts were in two lines per flange (staggered pattern), additional path checks and $s^2/(4g)$ corrections would be required per AISC 360-22 §B4.3b. For this single-line-per-flange layout, the straight path governs.*

---

#### Step (c) — Shear Lag Factor U and Effective Net Area

The W8×31 is connected through **both flanges**. The flanges are the primary tension-carrying elements. The web is not directly connected to the gusset plate — load must transfer from the web into the flanges via shear before entering the connection.

**Check Table D3.1 Case 3:** W-shapes connected through flanges only, $b_f \geq 2/3 \, d$:
$$\frac{2}{3}d = \frac{2}{3}(8.00) = 5.33 \text{ in} < b_f = 8.00 \text{ in} \quad \checkmark$$

With $\geq 3$ fasteners per line (we have 4), **Case 3 applies:**
$$U = 0.90$$

> *Alternative: If we used the general Case 2 formula, we would need $\bar{x}$ (distance from the centroid of the flange to the face of the connection). For a W8×31 flange, $\bar{x} \approx t_f/2 = 0.435/2 = 0.218$ in (approx.) and the connection length $L = 3 \times 3 = 9$ in (3 spaces between 4 bolts). This gives $U = 1 - 0.218/9 = 0.976$, which is higher than 0.90. Per AISC commentary, the designer may use the higher of Case 2 and Case 3. We conservatively use Case 3: $U = 0.90$.*

**Effective net area:**
$$A_e = U \cdot A_n = 0.90 \times 8.37 = \mathbf{7.53 \text{ in}^2}$$

---

#### Step (d) — Net-Section Fracture

$$P_n^{(2)} = F_u \, A_e = 65 \times 7.53 = 489.5 \text{ kips}$$

LRFD design strength:
$$\phi_t P_n^{(2)} = 0.75 \times 489.5 = \mathbf{367.1 \text{ kips}}$$

Check: $367.1 \geq 320$ ✅ **PASS** (Net Fracture)

---

#### Step (e) — Block Shear Note

At the bolted connection, block shear must also be checked per AISC 360-22 §J4.3. For the flange connection with 4 bolts per line, a block of flange material can shear out along the two bolt lines while tensile rupture occurs across the end bolt cross-section. Using Eq. J4-5:

$$R_n = 0.60 F_u A_{nv} + U_{bs} F_u A_{nt} \leq 0.60 F_y A_{gv} + U_{bs} F_u A_{nt}$$

A full block shear check requires computing $A_{nv}$ and $A_{nt}$ based on the bolt layout geometry. For this example, the detailed block shear calculation is deferred to Topic G (§J4). Typical block shear for this connection geometry does **not** govern over net fracture when $U = 0.90$ and $F_u = 65$ ksi, but it must always be verified in practice.

---

#### Step (f) — Slenderness Check

$$\frac{L}{r_y} = \frac{180 \text{ in}}{2.02 \text{ in}} = \mathbf{89.1}$$

AISC 360-22 §D1 recommends $L/r \leq 300$ for tension members.

Check: $89.1 \leq 300$ ✅ **PASS** (Slenderness — well within guideline)

---

#### Step (g) — Summary and Governing Limit State

| Limit State | $\phi_t P_n$ (kips) | $P_u$ (kips) | Result |
|-------------|---------------------|--------------|--------|
| Gross yielding (§D2-a) | 410.9 | 320 | ✅ PASS |
| Net fracture (§D2-b) | 367.1 | 320 | ✅ PASS |
| Slenderness $L/r$ | $89.1 \leq 300$ | — | ✅ OK |

**Governing limit state: Net-Section Fracture** at $\phi_t P_n = 367.1$ kips.

**Demand-to-capacity ratio:**
$$\frac{P_u}{\phi_t P_n} = \frac{320}{367.1} = 0.872 \quad (87.2\% \text{ utilized})$$

**Conclusion:** The **W8×31 (A992) is adequate** for the 320-kip factored tension demand. Net-section fracture governs with 87% utilization, leaving a 13% reserve. Block shear must be checked separately but is not expected to govern here.

---

## 7. Common Mistakes & Pitfalls

- **Mistake 1 — Using the wrong hole diameter.** Students often subtract only 3/4 in (the bolt diameter) from the gross area. AISC 360-22 §B4.3b requires adding 1/16 in for clearance AND 1/16 in for punch damage, for a total of $d_{bolt} + 1/8$ in. For a 3/4-in bolt, this means 7/8 in, not 3/4 in. Always add 1/8 in total to the bolt diameter for the design hole size.

- **Mistake 2 — Forgetting to check all failure paths.** When holes are staggered, there can be multiple possible failure paths (straight, diagonal, zigzag). The critical path is the one giving the **minimum** $A_n$. Checking only the straight path or only one diagonal path can lead to an unconservative (unsafe) answer. Sketch the connection layout and systematically label every path.

- **Mistake 3 — Applying $U = 1.0$ when shear lag exists.** If only part of the section is connected (common for W-shapes connected by flanges only, or single angles), the effective net area is **less** than the net area. Using $U = 1.0$ when shear lag is present overestimates the capacity and is unconservative. Always consult Table D3.1 and verify whether all elements of the section are connected.

- **Mistake 4 — Using the same $\phi_t$ for both limit states.** Yielding uses $\phi_t = 0.90$; fracture uses $\phi_t = 0.75$. These are different values and must not be confused. The lower factor for fracture reflects its brittle nature and higher uncertainty.

- **Mistake 5 — Treating the slenderness limit as a hard code limit.** AISC §D1 states that $L/r$ "preferably should not exceed 300." It is a serviceability guideline, not a hard limit state. A member with $L/r = 320$ is not automatically "failed" by the code — but the engineer should evaluate whether vibration or sag under self-weight is a concern.

- **Mistake 6 — Forgetting block shear.** The two tension member limit states (yielding and fracture) do not cover all possible failure modes. Block shear at the connection (§J4.3) is a third, independent limit state that can govern, especially for short connections or thick plates. Always include it in a complete design check.

---

## 8. Connections to Other Topics

- **Topic 06-A (Steel Material Properties & Limit States):** Gross yielding and net fracture directly apply the $F_y$ and $F_u$ properties defined there, and the LRFD/ASD framework ($\phi$, $\Omega$) introduced in that note underpins all the checks here.

- **Topic 06-C (Compression Members — Buckling):** The slenderness ratio $L/r$ appears in both topics. For tension, $L/r \leq 300$ is a serviceability guideline; for compression, $L/r$ controls the elastic/inelastic buckling curve. Understanding why tension members are far less sensitive to slenderness than compression members deepens understanding of both.

- **Topic 06-F (Beam-Column Design — Combined Loading):** Tension members subject to simultaneous bending (e.g., a truss chord carrying out-of-plane loads) must be designed using interaction equations. The axial tension capacity $\phi_t P_n$ derived here feeds directly into those equations as the $P_c$ denominator.

- **Topic 06-G (Bolted Connections — §J):** Block shear (§J4.3) is the third tension member limit state. All net-area calculations performed here are also needed for connection design, since the connection region often controls both the member and the bolt group simultaneously.

- **Topic 10-F / 10-G (LRFD and ASD Load Combinations):** The factored demand $P_u$ used in every tension check comes from ASCE 7-22 §2.3 (LRFD) or §2.4 (ASD). Understanding how load factors produce $P_u$ is a prerequisite to setting up any strength check.

- **Topic 09-A (Euler Buckling):** Tension members do not buckle, which is why they are efficient. This contrast — yielding/fracture vs. buckling — is the fundamental difference between tension and compression member behavior and motivates the separate design chapters in AISC 360-22 (Chapter D vs. Chapter E).

---

## 9. Further Reading

| Resource | Where to Look |
|----------|--------------|
| AISC 360-22 Specification for Structural Steel Buildings | Chapter D (Tension Members), §B4.3 (Net Area), Table D3.1 (Shear Lag) |
| AISC Steel Construction Manual, 16th Ed. | Part 5 (Design of Tension Members); Part 8 (Connection Design) |
| Segui, W.T. — *Steel Design*, 6th Ed. (Cengage) | Chapter 3 (Tension Members) |
| McCormac & Csernak — *Structural Steel Design*, 6th Ed. (Pearson) | Chapter 3 (Tension Members) |
| Gere & Goodno — *Mechanics of Materials*, 9th Ed. | Chapter 1 (Stress & Strain) — review of axial stress fundamentals |
| AISC Design Examples (v16.0, available free at aisc.org) | Example D.1–D.8 (Tension member worked problems) |

---

## 10. Quick Self-Check

- [ ] I can state both limit-state equations ($P_n = F_y A_g$ and $P_n = F_u A_e$) from memory and identify the correct $\phi_t$ for each.
- [ ] I know why the resistance factor for fracture (0.75) is lower than for yielding (0.90) and can explain it physically.
- [ ] I can compute the design hole diameter for any bolt size using the +1/8-in rule.
- [ ] I can draw all possible failure paths for a staggered bolt layout and apply the $s^2/(4g)$ correction to each diagonal segment.
- [ ] I can look up the appropriate shear lag factor $U$ from Table D3.1 for W-shapes, angles, and plates.
- [ ] I can compute $A_e = U A_n$ and use it to find the fracture design strength $\phi_t P_n = 0.75 F_u A_e$.
- [ ] I have reproduced the W8×31 worked example on my own (without looking) and matched each result within rounding.
- [ ] I can connect this topic to bolted connection design (block shear) and to the concept of ductile vs. brittle failure modes.

---

---

## 11. Graduate Extension: Fracture Mechanics, Shear Lag Theory & Net Path Rigorous Treatment

### 11.1 Fracture Mechanics Background for Net-Section Rupture

The net-section fracture limit state ($\phi_t = 0.75$, $P_n = F_u A_e$) is phenomenologically correct but disguises rich fracture mechanics. The underlying concept is **linear elastic fracture mechanics (LEFM)**. At a bolt hole, the stress concentration factor for an infinite plate is:

$$
K_t = 3 \qquad (\text{circular hole in uniaxial tension, Kirsch 1898})
$$

This implies a local stress $3\sigma_{nom}$ at the hole edge. However, in a ductile steel the high local stress triggers localized yielding that redistributes stress — preventing unstable fracture until the average net-section stress reaches $F_u$. The **effective stress intensity factor** at the hole in an elastic body (Inglis 1913) is:

$$
K_I = \sigma_{net}\sqrt{\pi a} \cdot F(a/W)
$$

where $a$ is the half-crack length at the hole edge, $W$ is the plate width, and $F(a/W)$ is a finite-width correction factor (typically 1.0–1.2 for typical $a/W$ ratios). Fracture initiates when $K_I \geq K_{Ic}$ (plane-strain fracture toughness). For structural steels at room temperature, $K_{Ic} \approx 50$–$200\,\text{MPa}\sqrt{\text{m}}$, which is large enough that LEFM fracture is prevented by ductile yielding — the member typically necks and tears rather than cleaving. **At low temperature or in thick plates (plane-strain conditions dominate)**, $K_{Ic}$ falls toward the lower-shelf Charpy $C_v$ values, and brittle fracture becomes possible at stresses below $F_u$. This is why AISC requires **notch-toughness** (CVN impact testing) for seismic moment-frame connections and fatigue-critical members.

**J-integral and ductile fracture.** For large-scale yielding around a hole (typical of A992 steel), LEFM is inappropriate. Rice's **J-integral** (1968):

$$
J = \oint_\Gamma \left(W_0\,dy - \mathbf{T}\cdot\frac{\partial\mathbf{u}}{\partial x}\,ds\right)
$$

where $W_0$ is strain energy density, $\mathbf{T}$ is the traction vector, and $\mathbf{u}$ is the displacement vector on contour $\Gamma$, is a path-independent energy release rate applicable with plasticity. Fracture initiates when $J = J_{Ic}$ (the critical tearing modulus). For structural steels, $J_{Ic}$ is large enough that global net-section yielding precedes any initiation of ductile tearing — validating the $P_n = F_u A_e$ formula for normal service temperature conditions.

---

### 11.2 Rigorous Derivation of the Shear Lag Reduction Factor $U$

The shear lag factor $U$ in AISC Table D3.1 originates from the elastic shear flow analysis of partially connected sections. Consider an angle with one leg connected (say, the outstanding (unconnected) leg has cross-sectional area $A_{out}$). Under axial load $P$, the connected leg transfers force immediately through the fasteners; the outstanding leg mobilizes through shear flow at the fillet radius.

**Step 1 — Governing differential equation.** Consider a thin strip element $dx$ of the unconnected leg at distance $z$ from the connected leg. The axial force in the strip $dF(x)$ satisfies:

$$
\frac{d^2 u_{out}}{dx^2} - \frac{G t_{out}}{E A_{out}}(u_{out} - u_{conn}) = 0
$$

where $u_{out}$ and $u_{conn}$ are the axial displacements of the outstanding and connected portions respectively, $G$ is the shear modulus, and $t_{out}$ is the leg thickness.

**Step 2 — Solution.** Defining the slip $\delta(x) = u_{conn} - u_{out}$, this becomes:

$$
\frac{d^2\delta}{dx^2} = \lambda^2 \delta, \qquad \lambda^2 = \frac{G t_{out}}{E A_{out}} \cdot \frac{A}{A_{out}}
$$

With boundary conditions $\delta(0) = 0$ (full engagement at the far connection end) and $\frac{d\delta}{dx}\big|_{L} = -P/(EA)$ (applied load at the near end), the solution is:

$$
\delta(x) = C_1 \cosh(\lambda x) + C_2 \sinh(\lambda x)
$$

**Step 3 — $\bar{x}$ interpretation.** The quantity $\bar{x}$ (distance from the connected plane to the centroid of the full unconnected section) measures the eccentricity of force transfer. Leibholz (1949) and Chesson & Munse (1963) showed that the average stress efficiency of the outstanding leg over length $L$ approaches:

$$
U = 1 - \frac{\bar{x}}{L}
\tag{AISC Table D3.1, Case 2}
$$

as a first-order approximation valid when $L \gg \bar{x}$. The exact hyperbolic solution gives:

$$
U_{exact} = \frac{\tanh(\lambda L)}{\lambda L}
$$

For practical connection lengths ($L \geq 2\bar{x}$ to $3\bar{x}$), $U_{exact}$ and $1 - \bar{x}/L$ agree within 5%. AISC Table D3.1 tabulates specific values for W-shapes, single angles, and double angles based on this theory combined with test calibration.

**Physical implication.** A longer connection (larger $L$) gives larger $U$ because the outstanding elements have more length over which to pick up load through shear flow. A fully connected section (all elements connected, $\bar{x} = 0$) achieves $U = 1.0$ exactly. **This is why AISC Table D3.1 provides $U = 1.0$ for any tension member connected through all its cross-sectional elements**: there is no eccentricity of the load path.

---

### 11.3 Staggered Bolt Path: Whitney's Rule Derivation

For staggered fasteners, testing by Cochrane (1922) and Whitney (1929) showed that the net width for a diagonal path segment must account for the path obliquity. Consider two adjacent bolt holes at spacing $s$ (longitudinal) and gauge $g$ (transverse). The inclined path between them has length:

$$
d_{path} = \sqrt{s^2 + g^2}
$$

Using an **energy approach** (or equivalently, equating the work done by the net force on the projected areas), the effective width removed per diagonal segment is:

$$
\Delta w_{diag} = d_h - \frac{s^2}{4g}
\tag{Whitney 1929; AISC 360-22 \S B4.3b}
$$

**Derivation by similar triangles (Cochrane 1922).** Consider the shear lag analogy: the inclined failure surface is treated as a vertical surface of net width $d_h$ minus a correction $s^2/(4g)$ that credits the zig-zag for its angle. Setting the failure stress equal in both paths:

$$
\frac{P}{t(w_n)_{diag}} = \frac{P}{t(w_n)_{straight}} \implies (w_n)_{diag} = d - d_h + \frac{s^2}{4g}
$$

Validation against test data by Davis & Woodruff (1941) showed the formula is accurate to within 5% for $0.3 \leq s/g \leq 1.5$. For very small $s/g$, the correction overestimates the staggered path capacity (the formula becomes unconservative); AISC Commentary §B4 notes that $s^2/(4g)$ should not be applied when $s < g/2$.

---

### 11.4 Probabilistic Basis for $\phi_t$ Values

The lower resistance factor for **net-section fracture** ($\phi_t = 0.75$) versus **gross-section yielding** ($\phi_t = 0.90$) is fully justified by FOSM reliability analysis (see Topic 06-A §11.2). The key difference lies in the coefficient of variation of the resistance:

| Limit state | COV of $R$ | $\beta_T$ | Computed $\phi$ |
|-------------|-----------|-----------|----------------|
| Gross yielding: $F_y A_g$ | $V_R = 0.126$ | 3.0 | $\approx 0.90$ |
| Net fracture: $F_u A_e$ | $V_R = 0.185$ | 3.5 | $\approx 0.75$ |

The larger $V_R$ for fracture arises because:

1. $F_u$ has higher scatter than $F_y$ ($V_{F_u} \approx 0.11$ vs. $V_{F_y} \approx 0.10$, Galambos 1978)
2. $A_e = U A_n$ adds shear lag factor uncertainty ($V_U \approx 0.12$)
3. The net area $A_n$ depends on hole punching quality ($V_{A_n} \approx 0.08$)
4. The higher target reliability index ($\beta_T = 3.5$) used for fracture limit states reflects the brittle, sudden nature of net-section rupture

Combining in quadrature: $V_R = \sqrt{0.11^2 + 0.12^2 + 0.08^2} \approx 0.185$, confirming the table above.

---

### 11.5 Block Shear: Variational Mechanics Interpretation

Block shear (AISC §J4.3) is often presented as a cookbook formula. The deeper mechanics: consider a bolt group with $n$ bolts in a $p \times q$ pattern attached to a gusset plate. The block of material defined by the bolt perimeter can fail by simultaneous:

- **Shear yielding OR fracture** on the longitudinal planes (parallel to load)
- **Tension fracture** on the transverse plane (perpendicular to load)

This is a **mixed-mode failure**: Laboratory work by Hardash & Bjorhovde (1985) and Gross et al. (1995) showed that the governing equation:

$$
R_n = 0.6 F_u A_{nv} + U_{bs} F_u A_{nt}
\tag{governs when shear fracture controls}
$$
$$
R_n = 0.6 F_y A_{gv} + U_{bs} F_u A_{nt}
\tag{governs when shear yielding controls with cap applied}
$$

can be derived from upper-bound plasticity theory by finding the kinematically admissible failure mechanism that minimizes the lateral resistance. The $0.6 F_u$ factor is the shear fracture stress ($\approx F_u/\sqrt{3}$ from von Mises, with $F_u/\sqrt{3} \approx 0.577 F_u \approx 0.60 F_u$ rounded).

The $U_{bs} = 0.5$ case arises when the tension stress on the transverse plane is non-uniform (e.g., wide flanges where the web is connected but flanges carry less tension). The factor effectively reduces the tension rupture contribution to account for stress redistribution limitations before fracture.

---

*Created by Structural Engineering Tutor • 2026-03-18 | Upgraded to Graduate level: 2026-03-18*
