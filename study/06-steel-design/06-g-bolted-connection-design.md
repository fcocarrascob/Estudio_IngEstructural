# Bolted Connection Design: Shear, Bearing & Block Shear

**Subject area:** Steel Design (AISC 360-22)
**Design standard / primary reference:** AISC 360-22 §J3, §J4; Segui, *Steel Design*, 6th ed., Chapter 7
**Depth level:** Graduate — rigorous derivation
**Estimated study time:** 130 minutes

---

## 1. Introduction & Motivation

Bolted connections are the most common means of joining steel elements in the field. Unlike welds, bolts are installed with hand and power tools, are inspectable by torque testing or direct-tension indicators, and can be disassembled for modification. A typical steel frame may contain tens of thousands of bolts — in beam-to-column shear tabs, splice plates, gusset plates, and baseplate anchor rods.

Bolted connections can fail in several distinct ways, and the designer must check every applicable mode: the bolt itself may shear off; the connected plate may tear out locally at a bolt hole (bearing failure or block shear); or the net cross-section of the connected member may rupture. Slip-critical connections add a friction-based limit state for cyclic or vibration-sensitive loads. All of these failure paths must be evaluated, and the connection capacity is governed by the weakest one.

---

## 2. Key Concepts & Definitions

| Term | Symbol | Definition |
|------|--------|------------|
| Bolt nominal diameter | $d_b$ | Bolt shank diameter (e.g., 3/4 in, 7/8 in, 1 in) |
| Bolt gross area | $A_b$ | $\pi d_b^2 / 4$ |
| Nominal tensile stress of bolt | $F_{nt}$ | Tabulated in AISC Table J3.2 (ksi) |
| Nominal shear stress of bolt | $F_{nv}$ | Tabulated in AISC Table J3.2 (ksi) |
| Bearing-type connection | — | Bolt carries load in shear; slip is permitted |
| Slip-critical connection | — | Connection designed so slip does not occur (friction controls) |
| Pretension | $T_b$ | Minimum bolt pretension per AISC Table J3.1 |
| Surface class | — | Class A ($\mu = 0.35$) or Class B ($\mu = 0.50$) friction surface |
| Clear distance | $L_c$ | Clear distance in load direction between bolt hole edge and next hole / member edge |
| Block shear | — | Failure by simultaneous shear yielding / rupture on one plane and tension rupture on a perpendicular plane |
| $U_{bs}$ | — | Tension stress uniformity factor: 1.0 (uniform) or 0.5 (non-uniform) |

---

## 3. Governing Equations

| Equation | Description | Source |
|----------|-------------|--------|
| $R_n = F_{nv} \cdot A_b$ | Nominal bolt shear strength per bolt | AISC 360-22 §J3.6 |
| $R_n = 2.4 \, d_b \, t \, F_u$ | Nominal bearing strength (deformation permissible) | AISC 360-22 §J3.10 |
| $R_n = 1.2 \, L_c \, t \, F_u \le 2.4 \, d_b \, t \, F_u$ | Nominal bearing (edge bolt, deformation critical) | AISC 360-22 §J3.10 |
| $R_n = 0.6 F_y A_{gv} + U_{bs} F_u A_{nt} \le 0.6 F_u A_{nv} + U_{bs} F_u A_{nt}$ | Block shear rupture | AISC 360-22 §J4.3 |
| $R_n = \mu \, D_u \, h_f \, T_b \, n_s$ | Nominal slip-critical bolt strength | AISC 360-22 §J3.8 |

$$
\boxed{
R_n = F_{nv} \cdot A_b \qquad \phi = 0.75 \;(\text{LRFD}), \quad \Omega = 2.00 \;(\text{ASD})
}
$$

**Variable legend:**

| Symbol | Description | SI Units | US Customary |
|--------|-------------|----------|--------------|
| $R_n$ | Nominal strength of one bolt | N | kips |
| $F_{nv}$ | Nominal shear stress of bolt | MPa | ksi |
| $A_b$ | Bolt gross cross-sectional area | mm² | in² |
| $d_b$ | Bolt nominal diameter | mm | in |
| $t$ | Thickness of connected part (bearing calculation) | mm | in |
| $F_u$ | Tensile strength of connected part | MPa | ksi |
| $L_c$ | Clear distance between hole edge and next hole / plate edge | mm | in |
| $A_{gv}$ | Gross area subject to shear (block shear) | mm² | in² |
| $A_{nv}$ | Net area subject to shear (block shear) | mm² | in² |
| $A_{nt}$ | Net area subject to tension (block shear) | mm² | in² |
| $U_{bs}$ | Tension-stress uniformity factor | — | — |
| $\mu$ | Slip coefficient (Class A=0.35, Class B=0.50) | — | — |
| $D_u$ | 1.13 (ratio of mean/specified pretension) | — | — |
| $h_f$ | Factor for fillers (1.0 if no fillers) | — | — |
| $T_b$ | Minimum bolt pretension (Table J3.1) | N | kips |
| $n_s$ | Number of slip planes | — | — |

---

## 4. Derivation

### 4.1 Standard Bolt Grades and Nominal Stresses

AISC 360-22 **Table J3.2** (condensed for common structural bolts):

| Bolt Specification | $F_{nt}$ (ksi) | $F_{nv}$ — threads **excluded** (ksi) | $F_{nv}$ — threads **included** (ksi) |
|--------------------|---------------|--------------------------------------|--------------------------------------|
| A307 (low-strength) | 27 | 27 | 27 |
| F3125 Grade A325 | 90 | 54 | 48 |
| F3125 Grade A490 | 113 | 68 | 60 |

> **Note:** The ASTM A325 and A490 designations were superseded by ASTM F3125 Grades A325 and A490 in 2016, but the names A325 and A490 remain in common use.

A325 bolts are the most used in practice. A490 (higher strength) requires more scrutiny for brittle fracture and is not permitted in slip-critical connections with Class A surfaces only.

**Nominal hole sizes** (Table J3.3 for standard holes):
- Standard (STD): $d_b + 1/16$ in for $d_b \le 1$ in; $d_b + 1/8$ in for $d_b > 1$ in
- Oversize (OVS): $d_b + 5/16$ in typical — reduces slip load; requires slip-critical connection

**Hole area deducted for net section (§B4.3b):** Add 1/16 in to hole diameter for punching damage →

$$d_h = d_b + \frac{1}{16} + \frac{1}{16} = d_b + \frac{1}{8} \text{ in}$$

### 4.2 Bolt Shear Strength (§J3.6)

A bolt loaded in shear on one shear plane (single shear) has nominal strength:

$$R_n = F_{nv} \cdot A_b$$

For $n_s$ shear planes (double shear, etc.):

$$R_n = F_{nv} \cdot A_b \cdot n_s$$

Whether threads are in the shear plane is set by the bolt length and grip; for calculations **assume threads included (conservative)** unless the bolt length and nut placement guarantee otherwise.

Design strength:

$$\phi R_n = 0.75 \times F_{nv} \times A_b \quad (\text{LRFD})$$

For a bolt group with $N_b$ bolts in single shear, total available shear = $N_b \times \phi R_n$.

### 4.3 Bearing on Connected Material (§J3.10)

When the bolt bears against the plate hole, the plate can yield/tear locally. AISC provides two equations based on whether deformation at service load is considered:

**When bolt hole deformation is a design consideration (standard case):**

$$R_n = 1.2 \, L_c \, t \, F_u \le 2.4 \, d_b \, t \, F_u$$

Here $L_c$ is the **clear distance** (in load direction) from the edge of the hole to the next hole or to the edge of the material:
- Interior bolt: $L_c = s - h_h$ (where $s$ = spacing, $h_h$ = hole diameter)
- Edge bolt: $L_c = L_e - h_h/2$ (where $L_e$ = edge distance)

The cap $2.4 d_b t F_u$ corresponds to the "full bearing" value when $L_c$ is large. The $1.2 L_c t F_u$ term controls when the clear distance is short.

$\phi = 0.75$ (LRFD), $\Omega = 2.00$ (ASD) for bearing.

> **Practical note:** The limit $L_c \ge 1.5d_h$ implicit in standard spacing and edge-distance requirements usually ensures that bearing, not bolt shear, governs only in thin plates.

### 4.4 Block Shear (§J4.3)

Block shear is a tearing-type failure where a block of material pulls out from the connection, bounded by a shear failure surface (parallel to load) and a tension failure surface (perpendicular to load). It is critical in:
- Tension members connected through gusset plates (the gusset corner block)
- Coped beams (web block shear)
- Angles connected with one leg

The governing equation:

$$R_n = 0.6 F_y A_{gv} + U_{bs} F_u A_{nt} \le 0.6 F_u A_{nv} + U_{bs} F_u A_{nt}$$

**Physical meaning:**
- $0.6 F_y A_{gv}$: shear **yielding** on gross shear area
- $0.6 F_u A_{nv}$: shear **rupture** on net shear area (upper bound for shear)
- $U_{bs} F_u A_{nt}$: tension **rupture** on net tension area (same in both terms, so it cancels in the governing expression — only the shear term changes)

The factored resistance:

$$\phi R_n = 0.75 \, R_n \quad (\text{LRFD})$$

### 4.5 Slip-Critical Connections (§J3.8)

For vibration-sensitive structures, fatigue loading, connections with oversized holes, or seismic systems (AISC 341), bolts are designed to not slip. Slip resistance per bolt:

$$R_n = \mu \, D_u \, h_f \, T_b \, n_s$$

Where:
- $\mu = 0.35$ (Class A: clean mill scale, hot-dip galvanized and roughened) or $0.50$ (Class B: blast-cleaned)
- $T_b$: from AISC Table J3.1, e.g., for 3/4 in A325: $T_b = 28$ kips; for 7/8 in A325: $T_b = 39$ kips

$\phi = 1.00$ for serviceability limit state; $\phi = 0.85$ for strength limit state (LRFD).

---

## 5. Design / Application Procedure

1. **Determine bolt grade and size**: Select A325 or A490, and a trial diameter $d_b$ (most common: 3/4 in or 7/8 in). Determine whether connection is bearing-type or slip-critical.

2. **Set bolt spacing and edge distances** (§J3.3, §J3.4):
   - Minimum spacing: $2\tfrac{2}{3} d_b$; preferred: $3 d_b$
   - Minimum edge distance: per AISC Table J3.4 (e.g., for 3/4-in bolts, STD holes: 1 in edge distance to cut edge, 7/8 in to rolled edge)
   - Maximum spacing: lesser of $24t$ or 12 in (for weather/corrosion; §J3.5)

3. **Compute bolt shear capacity** per bolt:
   $$\phi r_n^{bolt} = 0.75 \times F_{nv} \times A_b$$
   Select "threads included" unless detailing confirms otherwise.

4. **Compute bearing capacity** per bolt per connected part (inner plates vs. outer plates for double-lap connections):
   $$\phi r_n^{bear} = 0.75 \times \min\!\left(1.2 L_c t F_u,\; 2.4 d_b t F_u\right)$$

5. **Governing bolt/bearing capacity**: $\phi r_n = \min(\phi r_n^{bolt},\; \phi r_n^{bear, \text{each layer}})$

6. **Number of bolts required** (simple shear connection):
   $$N_b \ge \frac{P_u}{\phi r_n} \quad (\text{LRFD})$$
   Round up to next whole number.

7. **Check block shear** on every potential failure block:
   - Identify $A_{gv}$, $A_{nv}$, $A_{nt}$ from geometry and hole sizes
   - Compute $\phi R_n = 0.75 R_n$ and verify $\ge P_u$

8. **Check connected member net section** (§J4.1for plate tension, §D for member design — already covered in 06-B note).

9. **For slip-critical**: check $\phi_{slip} R_n \ge V_u$ per bolt using $\phi = 1.00$ (serviceability) or $0.85$ (strength).

---

## 6. Worked Example

**Problem:** A gusset plate (PL 3/8 × 10, A36 steel, $F_y = 36$ ksi, $F_u = 58$ ksi) is lap-spliced to a main plate using 3/4-in A325 bolts (bearing-type, threads included). The LRFD factored tension: $P_u = 90$ kips. Bolt layout: two vertical lines of bolts, 3 rows, 3-in spacing, 1.5-in edge distance (top and bottom), 3-in gauge.

**Given:**
- $d_b = 3/4$ in → $A_b = \pi(0.75)^2/4 = 0.4418$ in²
- $F_{nv} = 48$ ksi (threads included, A325)
- Gusset thickness $t = 3/8$ in; $F_u = 58$ ksi
- Standard hole: $d_h = 3/4 + 1/16 = 13/16$ in (design for net section: use $d_h + 1/16 = 7/8$ in)

**Required:** (a) Bolt shear, (b) Bearing (govern?), (c) Block shear for gusset.

**Solution:**

**a) Bolt shear capacity per bolt:**

$$\phi r_n^{bolt} = 0.75 \times 48 \times 0.4418 = 15.9 \text{ kips/bolt}$$

Total for 6 bolts: $6 \times 15.9 = 95.4$ kips > 90 kips ✓

**b) Bearing capacity per bolt (interior bolts):**

Inner bolt: $L_c = 3 - 13/16 = 2.1875$ in

$$\phi r_n^{bear} = 0.75 \times 1.2 \times 2.1875 \times (3/8) \times 58 = 0.75 \times 57.1 = 42.8 \text{ kips/bolt}$$

Upper bound: $2.4 \times 0.75 \times (3/8) \times 58 = 39.2$ kips → **bearing cap at 39.2 kips/bolt**

Since 39.2 kips > 15.9 kips (bolt shear), **bolt shear governs** → 95.4 kips > 90 kips ✓

**c) Block shear on gusset plate (4-bolt block: 2 lines × 2 rows shear + 1 row tension):**

Shear area (2 planes, 2 bolt spacings + top edge distance each):

$$A_{gv} = 2 \times (L_{edge} + 2s) \times t = 2 \times (1.5 + 2 \times 3) \times 0.375 = 2 \times 7.5 \times 0.375 = 5.625 \text{ in}^2$$

$$A_{nv} = 2 \times \left[(1.5 + 2\times 3) - 2.5 \times \frac{7}{8}\right] \times 0.375 = 2 \times [7.5 - 2.1875] \times 0.375 = 2 \times 5.3125 \times 0.375 = 3.984 \text{ in}^2$$

Tension area (cross-bar between 2 bolt lines, 1 hole):

$$A_{nt} = \left[3 - \frac{7}{8}\right] \times 0.375 = 2.125 \times 0.375 = 0.797 \text{ in}^2$$

$U_{bs} = 1.0$ (uniform tension).

$$R_n = 0.6 \times 36 \times 5.625 + 1.0 \times 58 \times 0.797 = 121.5 + 46.2 = 167.7 \text{ kips}$$
$$R_n^{cap} = 0.6 \times 58 \times 3.984 + 1.0 \times 58 \times 0.797 = 138.6 + 46.2 = 184.8 \text{ kips}$$

Governing $R_n = 167.7$ kips → $\phi R_n = 0.75 \times 167.7 = 125.8$ kips > 90 kips ✓

**Result:** All three limit states are satisfied. Bolt shear controls the bolt layout (95.4 kips > 90 kips), and block shear has ample reserve (125.8 kips >> 90 kips).

---

## 7. Common Mistakes & Pitfalls

- **Wrong hole diameter for net section:** AISC §B4.3b requires adding 1/16 in to the punched or drilled hole size for the material damage allowance. Failure to add this 1/16 in underestimates hole size → overestimates net area → unconservative.

- **Forgetting to check both plates in bearing:** Each connected element must be checked independently. In a bolted splice, the thinner or weaker plate governs bearing, and each plate uses its own thickness and $F_u$.

- **Incorrect $U_{bs}$:** Non-uniform tension stress ($U_{bs} = 0.5$) occurs when the tension rupture plane is in a wide flange web with a non-uniform resultant (e.g., coped beams where not all flanges are connected). Using $U_{bs} = 1.0$ everywhere is unconservative for some geometries.

- **Omitting the $1.2 L_c t F_u$ check for edge bolts:** Edge bolts often have shorter $L_c$ than interior bolts; applying the cap $2.4 d_b t F_u$ without checking $1.2 L_c t F_u$ first is unconservative when edge distance is small.

- **Using $\phi = 0.90$ for bolt shear:** The resistance factor for connections (bolts and welds) is $\phi = 0.75$, not 0.90 which applies to yielding of members. This is a common slip in hurried calculations.

---

## 8. Connections to Other Topics

- **Tension member design (06-B):** Net area reduction ($U$ factor, shear lag) applies to the member at the connection — block shear is the third limit state alongside yielding on $A_g$ and rupture on $A_e$.
- **Welded connections (06-H):** Many connections use both welds and bolts (e.g., shop-welded / field-bolted). The relative stiffnesses require careful treatment; AISC generally does not allow sharing load between welds and bolts in the same direction.
- **Seismic design (11-E/F):** AISC 341 requires that connections in seismic moment frames and braced frames be slip-critical with a higher safety class and that block shear and net fracture strengths exceed member plastic capacity (capacity design).
- **Load combinations (10-F):** The $P_u$ entering all connection checks must reflect the governing ASCE 7 LRFD combination including load factors; never use unfactored service loads with $\phi = 0.75$.

---

## 9. Further Reading

| Resource | Where to look |
|----------|--------------|
| AISC 360-22 | §J3 (Bolts), §J4 (Affected elements), Table J3.1–J3.4 |
| AISC Steel Construction Manual, 16th ed. | Part 9 (Design of Connecting Elements); Part 10 (Design of Simple Shear Connections) |
| Segui, *Steel Design*, 6th ed. | Chapter 7: Simple Connections |
| Fisher & Struik, *Guide to Design Criteria for Bolted and Riveted Joints* | All chapters for detailed background |

---

## 10. Quick Self-Check

- [ ] I can state the three bolt failure modes (shear, bearing, block shear) from memory with their $\phi$ factors.
- [ ] I understand the difference between a bearing-type and a slip-critical connection and when each is required.
- [ ] I know the correct hole diameter to use for net section calculations (add 1/8 in to nominal hole size).
- [ ] I can identify $A_{gv}$, $A_{nv}$, and $A_{nt}$ on a sketch of a bolted tension connection.
- [ ] I can connect this topic to net section design (06-B) and to seismic connection requirements (11).

---

---

## 11. Graduate Extension: Slip Mechanics, Prying Action & Eccentric Bolt Groups

### 11.1 Bolt Preload Mechanics: Torque-Tension Relationship

High-strength bolts (A325/F1852 and A490/F2280, now consolidated into ASTM F3125) derive their clamping force from being **pretensioned** during installation. The torque-tension relationship is:

$$
T = K \cdot d_b \cdot T_b
$$

where $T$ is applied torque (ft-lb or N·m), $d_b$ is bolt diameter, $T_b$ is the required minimum pretension (AISC Table J3.1), and $K$ is the **nut factor** (or torque coefficient), which depends on surface condition, lubrication, and thread geometry. For clean and dry A325 bolts, $K \approx 0.20$; for waxed or lubricated bolts, $K \approx 0.12$–0.15 (Kulak, Fisher & Struik, *Guide to Design Criteria for Bolted and Riveted Joints*, 2nd ed., Ch. 8).

**Sources of variation in pretension.** The coefficient of variation of pretension for standard torque installation is $V_{T_b} \approx 0.25$, meaning that a bolt specified at $T_b = 28$ kips (3/4-in A325) may achieve anywhere from 15 to 40 kips in practice. This large variability is why the AISC minimum pretension $T_b$ is set at 70% of the proof load ($0.7 F_u A_b$), providing a buffer against under-installation.

**Turn-of-Nut method.** To avoid relying on the variable $K$ factor, the turn-of-nut method achieves pretension by specifying bolt elongation directly. After snug-tight, additional rotation is specified (1/3 to 1 full turn depending on bolt length and diameter). This method achieves $V_{T_b} \approx 0.12$, significantly more consistent than torque installation.

**Long-term relaxation.** Pretension loss occurs due to embedding and creep of contact surface asperities: approximately 5–10% loss occurs within the first 24–48 hours after installation (Sterling & Fisher 1966). AISC Table J3.1 pretension values already incorporate this relaxation factor.

---

### 11.2 Slip Mechanics and Coefficient of Friction

In a slip-critical connection, slip is resisted by friction between the faying (contact) surfaces. The slip load per bolt per slip plane is:

$$
V_{slip} = \mu T_b
$$

where $\mu$ is the **slip coefficient** (also called coefficient of friction, $k_s$ in the RCSC Specification).

**Surface preparation classes (AISC Table J3.2 and RCSC):**

| Class | Surface condition | $\mu = k_s$ |
|-------|------------------|--------------|
| A | Unpainted clean mill scale; hot-dip galvanized and roughened | 0.35 |
| B | Unpainted blast-cleaned; Class B coatings | 0.50 |
| C | Hot-dip galvanized and wire-brushed | 0.35 |

The experimental basis (Kulak et al. Ch. 3): when a bolted joint slips, the bolt shank bears against the hole walls and the joint transitions from friction-controlled to bearing-controlled behavior. The slip displacement at this transition is typically 0.25–1.0 mm (0.01–0.04 in). For seismic connections (AISC 341), **Class B surfaces** are required because smaller slip displacements and higher energy dissipation are critical.

**The $D_u = 1.13$ factor** in AISC Eq. J3-4 is the ratio of the mean installed bolt pretension to the specified minimum $T_b$. From load testing of large samples: $\bar{T}_b = 1.13 T_b$ on average (Fisher et al. 1974). The factor $D_u$ corrects for the fact that AISC specifies the minimum pretension, not the mean, ensuring the design strength is calibrated to the expected (mean) performance.

---

### 11.3 Prying Action in Hanger Connections: Kulak–Fisher Model

When a bolt group is loaded in tension and the connecting plate deforms flexurally, the plate bears on the support surface near the bolt (for a T-stub or a clip angle in tension). This creates an additional compressive force at the plate tip, called **prying force** $Q$, which adds to the tension in the bolt:

$$
B_t = T + Q
$$

where $T$ is the applied tensile force per bolt and $B_t$ is the total bolt tension. If prying is ignored, bolts will be undersized.

**Step 1 — Geometry.** Define (from AISC SCM Part 9, T-stub connections):
- $b'$: distance from bolt centerline to face of the stem (plate flexure arm, reducing by $d_b/2$ for prying)
- $a'$: distance from bolt centerline to the edge of the plate
- $\rho = b'/(a')$: geometric ratio
- $\delta = 1 - d_h/p$ where $p$ is bolt pitch and $d_h$ is hole diameter (tributary width correction)

**Step 2 — Prying force from plastic analysis (Kulak 1975).** When the plate thickness is inadequate, plastic hinges form at the bolt line and at the plate edge. Using yield-line theory for a unit-length strip:

$$
Q = T\rho\delta\left(\frac{t_{req}^2}{t^2} - 1\right) \geq 0
$$

where $t_{req}$ is the minimum plate thickness without prying:

$$
t_{req} = \sqrt{\frac{4Tb'}{\phi_b F_y p}}
$$

**Step 3 — Required bolt tension with prying.** The modified bolt force:

$$
B_t = T\left(1 + \frac{\rho\delta\, t_{req}^2/t^2}{1 + \rho\delta}\right)
$$

**AISC SCM Table 9-1** through Table 9-3 (T-stub and clip angle tables) automate this calculation. The key design implication: **use the thickest economical plate possible** to minimize prying; for critical connections set $t \geq t_{req}$ so that $Q = 0$.

---

### 11.4 Instantaneous Center of Rotation (ICR) Method for Bolt Groups

For **eccentrically loaded bolt groups** (bolt group loaded in shear with an eccentricity $e$), the AISC approach uses the **Instantaneous Center of Rotation (ICR) method** rather than simple vector addition. The ICR approach is more accurate because it accounts for the non-linear load-deformation behavior of individual bolts.

**Step 1 — Load-deformation relationship.** From Kulak (1975) tests, the load per bolt at deformation $\Delta_i$ follows (Crawford & Kulak 1971):

$$
r_i = r_{ult}\left(1 - e^{-10\Delta_i}\right)^{0.55}
$$

where $r_{ult} = F_{nv} A_b$ and $\Delta_i$ is the deformation of bolt $i$ in inches.

**Step 2 — Deformation compatibility.** For a rigid bolt group rotating about the ICR at distance $d_0$ from the centroid of the bolt group, each bolt $i$ at distance $r_i$ from the ICR deforms proportionally to its distance:

$$
\Delta_i = \Delta_{max}\frac{r_i}{r_{max}}
$$

where $r_{max}$ is the distance from the ICR to the farthest bolt and $\Delta_{max}$ is its deformation (taken as 0.34 in for A325 bolts at fracture, from Crawford & Kulak).

**Step 3 — Equilibrium equations.** Three equations must be satisfied:

$$
\sum F_x = 0, \quad \sum F_y = P, \quad \sum M_{ICR} = P \cdot e_{ICR} = 0
$$

where $e_{ICR}$ is the eccentricity from the load to the ICR. The ICR location is found iteratively (Newton-Raphson or tabulated in AISC Manual tables).

**AISC Table 8-3 through 8-11** tabulate the ICR solution for standard bolt patterns as the **coefficient $C$** (where $P_{design} = C \cdot r_{ult}$). The elastic vector method (no ICR, assuming proportional bolt loads) is conservative by 15–35% compared to the ICR method for typical eccentricities.

---

### 11.5 High-Strength Bolt Development and ASTM F3125

High-strength (HS) bolt technology evolved through several ASTM grades now unified under **ASTM F3125** (2014):

| ASTM F3125 Grade | Legacy grade | $F_u$ (ksi) | Nominal shear $F_{nv}$ (ksi) | Thread cond. |
|-----------------|-------------|-------------|------------------------------|-------------|
| A | A325 | 120 (1”), 105 (>1”) | 54 (N), 48 (X) | N or X |
| B | A490 | 150 | 68 (N), 60 (X) | N or X |
| C | A354 Gr. BC | 125 | 57 | N or X |
| F | A354 Gr. BD | 150 | 68 | N or X |

**N** = threads included in shear plane; **X** = threads excluded.

The AISC $F_{nv}$ values incorporate:
1. A 20% reduction from $F_u$ to convert from pure tension to shear strength (von Mises: $F_{nv,max} = F_u/\sqrt{3} \approx 0.577 F_u$)
2. A further ~6% reduction to account for the bolt head bearing area carrying tensile load when threads are in the shear plane (N condition)

The 2014 consolidation into F3125 also introduced **Grade F** (discontinued ASTM A449, medium-carbon hex bolts) and clarified pretension and inspection requirements for each combination type.

---

*Created by Structural Engineering Tutor • 2026-03-18 | Upgraded to Graduate level: 2026-03-18*
