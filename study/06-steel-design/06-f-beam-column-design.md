# Beam-Column Design: Combined Axial + Bending (H1 Equations)

**Subject area:** Steel Design (AISC 360-22)
**Design standard / primary reference:** AISC 360-22 §H1, §C, Appendix 8; Segui, *Steel Design*, 6th ed., Chapter 6
**Depth level:** Graduate — rigorous derivation
**Estimated study time:** 130 minutes

---

## 1. Introduction & Motivation

Most real steel members carry both axial load and bending moment simultaneously — columns in moment frames receive moments from beams framing into them, roof columns carry axial compression from gravity plus lateral moment from wind, and bracing gusset connections transmit combined effects. These members, called **beam-columns**, must satisfy interaction requirements: axial load reduces the section's capacity for moment, and vice versa.

The AISC approach bundles both failure modes — axial yielding/buckling and flexural yielding/lateral-torsional buckling — into a single pair of linear interaction equations (H1-1a and H1-1b). The equations are conservative but simple to apply, and they gracefully reduce to the pure tension/compression check when $M = 0$ and to the pure flexure check when $P = 0$.

A second critical issue for beam-columns is **second-order effects**: as the member deflects, the eccentric axial load creates additional moment ($P$-$\delta$ effect for individual member curvature, $P$-$\Delta$ for story sway). AISC accounts for these through amplification factors **B₁** (member) and **B₂** (story-level) applied to the first-order moments before entering the interaction check.

---

## 2. Key Concepts & Definitions

| Term | Symbol | Definition |
|------|--------|------------|
| Required axial strength | $P_r$ | Factored (LRFD) or unfactored (ASD) axial demand |
| Available axial strength | $P_c$ | $\phi_c P_n$ (LRFD) or $P_n/\Omega_c$ (ASD) |
| Required flexural strength (major axis) | $M_{rx}$ | Amplified factored/unfactored moment about strong axis |
| Available flexural strength (major axis) | $M_{cx}$ | $\phi_b M_n$ (LRFD) or $M_n/\Omega_b$ (ASD) |
| $P$-$\delta$ amplifier | $B_1$ | Accounts for moment from axial load acting on member deflection |
| $P$-$\Delta$ amplifier | $B_2$ | Accounts for moment from axial load acting on story drift |
| No-lateral-translation moment | $M_{nt}$ | First-order moment when lateral drift is artificially restrained |
| Lateral-translation moment | $M_{lt}$ | First-order moment due entirely to sidesway |
| Equivalent moment factor | $C_m$ | Reduces uniform-moment assumption when end moments are unequal |
| First-order Euler buckling load | $P_{e1}$ | $\pi^2 EI^* / L_{c1}^2$ based on actual unbraced length |

---

## 3. Governing Equations

| Equation | Description | Source |
|----------|-------------|--------|
| $\dfrac{P_r}{P_c} + \dfrac{8}{9}\!\left(\dfrac{M_{rx}}{M_{cx}} + \dfrac{M_{ry}}{M_{cy}}\right) \le 1.0$ | H1-1a: controls when $P_r/P_c \ge 0.20$ | AISC 360-22 §H1.1 |
| $\dfrac{P_r}{2P_c} + \dfrac{M_{rx}}{M_{cx}} + \dfrac{M_{ry}}{M_{cy}} \le 1.0$ | H1-1b: controls when $P_r/P_c < 0.20$ | AISC 360-22 §H1.1 |
| $M_r = B_1 M_{nt} + B_2 M_{lt}$ | Amplified required moment | AISC 360-22 App. 8 §8.2 |
| $B_1 = \dfrac{C_m}{1 - \alpha P_r / P_{e1}} \ge 1.0$ | $P$-$\delta$ amplifier | AISC 360-22 App. 8 §8.2-1 |
| $B_2 = \dfrac{1}{1 - \alpha \Sigma P_{story} / \Sigma P_{e,story}} \ge 1.0$ | $P$-$\Delta$ amplifier | AISC 360-22 App. 8 §8.2-2 |
| $C_m = 0.6 - 0.4\!\left(\dfrac{M_1}{M_2}\right)$ | Equivalent moment factor (no transverse load) | AISC 360-22 App. 8 §8.2 |

$$
\boxed{
\frac{P_r}{P_c} + \frac{8}{9}\!\left(\frac{M_{rx}}{M_{cx}} + \frac{M_{ry}}{M_{cy}}\right) \le 1.0
\qquad \Bigl(P_r/P_c \ge 0.20\Bigr)
}
$$

**Variable legend:**

| Symbol | Description | SI Units | US Customary |
|--------|-------------|----------|--------------|
| $P_r$ | Required axial strength | N | kips |
| $P_c$ | Available axial strength | N | kips |
| $M_{rx}, M_{ry}$ | Required flexural strength (strong, weak axis) | N·mm | kip-in |
| $M_{cx}, M_{cy}$ | Available flexural strength (strong, weak axis) | N·mm | kip-in |
| $B_1, B_2$ | Moment amplification factors | — | — |
| $\alpha$ | 1.0 (LRFD) or 1.6 (ASD) | — | — |
| $P_{e1}$ | Euler load for member: $\pi^2 EI^* / L_{c1}^2$ | N | kips |
| $L_{c1}$ | Actual unbraced length (for $B_1$) | mm | in |
| $\Sigma P_{story}$ | Total vertical load on story | N | kips |
| $\Sigma P_{e,story}$ | $R_M \cdot HL/\Delta_H$ = story Euler load | N | kips |
| $R_M$ | 0.85 for moment frames, 1.0 for braced frames | — | — |
| $C_m$ | Equivalent moment factor (≤ 1.0) | — | — |
| $M_1/M_2$ | End-moment ratio (positive = double curvature) | — | — |

---

## 4. Derivation

### 4.1 Origin of the Interaction Equations

**Step 1 — Plastic capacity with axial load (simplified).**
Consider a compact wide-flange section with full plastic moment $M_p = Z_x F_y$. When an axial force $P$ is present, part of the cross-section yields in axial compression, reducing the area available for the moment couple. For a rectangular cross-section of area $A$ and plastic modulus $Z$, the interaction is exact and parabolic:

$$\frac{M_n}{M_p} = 1 - \left(\frac{P}{P_y}\right)^2$$

For wide-flange sections the interaction is almost linear. The AISC bilinear form (H1-1a/b) is a conservative simplification that fits within the exact curves for all standard sections, is slightly conservative (more so for low $P_r/P_c$), and is linear — easy to apply.

**Step 2 — Why two equations (H1-1a vs H1-1b)?**
The full bilinear form consists of:
- A high-axial branch: passes through $(P_c, 0)$ and the transition at $P_r/P_c = 0.20$
- A low-axial branch: passes through $(0, M_c)$ and meets H1-1a at $P_r/P_c = 0.20$

At $P_r/P_c = 0.20$, both equations give the same result (you can verify by substitution). The break into two branches simply avoids penalizing sections that carry negligible axial load.

### 4.2 Second-Order Effects: B₁ and B₂

**P-δ effect (member deflects between braced points):**

A compressive load $P$ acting on a member with a mid-span lateral deflection $\delta$ creates an additional moment $P \cdot \delta$ at mid-span. This is the *secondary* moment. For a sinusoidal deflected shape, exact amplification is:

$$\text{Amplified moment} = M_0 \cdot \frac{1}{1 - P/P_{e1}}$$

where $P_{e1} = \pi^2 EI / L^2$ is the Euler buckling load. When end moments are unequal (not the worst case), $C_m$ modifies the amplifier:

$$B_1 = \frac{C_m}{1 - \alpha P_r / P_{e1}} \ge 1.0$$

For $M_1/M_2$ positive (double-curvature bending = reverse curvature), $C_m < 0.6$, which reduces $B_1$ — physically, the column deflects less when bent in reverse curvature.

**P-Δ effect (story sways laterally by Δ):**

When a story drifts by $\Delta$ under lateral load $H$, the total vertical load $\Sigma P_{story}$ causes an overturning moment $\Sigma P \cdot \Delta$. The amplified story shear (and column moments) follow from the stability equation:

$$B_2 = \frac{1}{1 - \alpha \Sigma P_{story} / \Sigma P_{e,story}} \ge 1.0$$

where AISC 360-22 App. 8-7 gives:

$$\Sigma P_{e,story} = R_M \cdot \frac{H \cdot L}{\Delta_H}$$

This is derived by recognizing that $H \cdot L/\Delta_H$ is the shear stiffness of the story, and $R_M$ accounts for additional stiffness contributed by leaning columns (moment frames: 0.85, braced frames: 1.0).

---

## 5. Design / Application Procedure

1. **Determine load demands** (LRFD or ASD): factored axial force $P_u$ and factored moments $M_{ux}$, $M_{uy}$ from structural analysis under all applicable load combinations (ASCE 7-22 §2.3).

2. **Separate moments into $M_{nt}$ and $M_{lt}$** (AISC App. 8 §8.2):
   - $M_{nt}$: run gravity-only analysis (no sway) → moment
   - $M_{lt}$: run lateral analysis (wind/seismic only) → sway moment

3. **Compute $B_1$** for each member (P-δ):
   - Find $C_m$: no transverse loads between braced points → $C_m = 0.6 - 0.4(M_1/M_2)$; transverse loads → $C_m = 1.0$ (conservative)
   - Compute $P_{e1} = \pi^2 E I_x / L_{c1}^2$ (use $0.8 \times$ nominal $EI$ if using Direct Analysis Method per §C2)
   - $B_1 = C_m / (1 - \alpha P_r / P_{e1}) \ge 1.0$

4. **Compute $B_2$** for the story (P-Δ):
   - From first-order analysis: $H$, $\Delta_H$, story height $L$
   - $\Sigma P_{e,story} = R_M \cdot H L / \Delta_H$
   - $B_2 = 1 / (1 - \alpha \Sigma P_{story}/\Sigma P_{e,story}) \ge 1.0$

5. **Amplify moments**:
   $$M_{rx} = B_1 M_{nt,x} + B_2 M_{lt,x}$$

6. **Compute available axial strength $P_c$**:
   - Determine $F_{cr}$ per Chapter E (§C or §E, with $KL$ from effective-length method or $L$ from direct-analysis method)
   - LRFD: $P_c = \phi_c P_n = 0.90 F_{cr} A_g$

7. **Compute available flexural strength $M_{cx}$**:
   - Determine $M_n$ per Chapter F (consider LTB from $06$-D notes)
   - LRFD: $M_{cx} = \phi_b M_n = 0.90 M_n$

8. **Check interaction ratio** (AISC 360-22 §H1.1):
   - If $P_r / P_c \ge 0.20$: use H1-1a
   - If $P_r / P_c < 0.20$: use H1-1b
   - Result must be ≤ 1.0

9. **Serviceability check**: verify drift $\Delta / L \le $ code limits (AISC DG3; ASCE 7 §12.12 for seismic).

---

## 6. Worked Example

**Problem:** An interior column in a steel moment frame (ASTM A992, W12×96, $F_y = 50$ ksi) in a 12-ft story has the following first-order demands from LRFD load combinations:
- Gravity (no-sway): $P_u = 400$ kips (compression), $M_{nt,x} = 80$ kip-ft, $M_{lt,x} = 0$
- Lateral (sway): $P_u = 0$, $M_{lt,x} = 120$ kip-ft

Story properties: $\Sigma P_{story} = 4{,}000$ kips, $H = 60$ kips, $\Delta_H = 0.30$ in (story height $L = 144$ in, $R_M = 0.85$).

**Given:**
- W12×96: $A_g = 28.2$ in², $I_x = 833$ in⁴, $Z_x = 131$ in³, $r_x = 5.44$ in, $r_y = 3.09$ in
- Unbraced length for in-plane buckling (sway frame): use $KL_x = 1.2 \times 12 = 14.4$ ft (Direct Analysis uses $K = 1.0$, but here we use Effective Length Method for illustration)
- Weak-axis braced at each floor: $KL_y = 12$ ft = 144 in

**Required:** Check AISC 360-22 H1-1 interaction.

**Solution:**

1. **Available axial strength** (Chapter E, governs about weak axis here):

   $$\frac{KL_y}{r_y} = \frac{144}{3.09} = 46.6 \quad < \quad 4.71\sqrt{E/F_y} = 4.71\sqrt{29{,}000/50} = 113 \implies \text{inelastic buckling}$$

   $$F_e = \frac{\pi^2 \times 29{,}000}{(46.6)^2} = \frac{286{,}000}{2{,}172} = 131.7 \text{ ksi}$$

   $$F_{cr} = 0.658^{(F_y/F_e)} F_y = 0.658^{(50/131.7)} \times 50 = 0.658^{0.380} \times 50 = 0.833 \times 50 = 41.6 \text{ ksi}$$

   $$P_c = \phi_c P_n = 0.90 \times 41.6 \times 28.2 = 1{,}054 \text{ kips}$$

2. **Available flexural strength** (assume LTB not critical with $L_b = 12$ ft within plastic range for W12×96 — confirm from 06-D):

   $$M_{cx} = \phi_b M_p = 0.90 \times 131 \times 50 / 12 = 491 \text{ kip-ft}$$

3. **Compute $B_2$**:

   $$\Sigma P_{e,story} = 0.85 \times \frac{60 \times 144}{0.30} = 0.85 \times 28{,}800 = 24{,}480 \text{ kips}$$

   $$B_2 = \frac{1}{1 - (1.0)(4{,}000/24{,}480)} = \frac{1}{1 - 0.163} = \frac{1}{0.837} = 1.19$$

4. **Compute $B_1$** (P-δ for gravity moments, no transverse loads between supports):

   For single-curvature bending with $M_1/M_2 ≈ 0$ (assume one end pinned):
   $C_m = 0.6 - 0.4(0) = 0.60$

   $$P_{e1} = \frac{\pi^2 \times 29{,}000 \times 833}{(144)^2} = \frac{238{,}400{,}000}{20{,}736} = 11{,}497 \text{ kips}$$

   $$B_1 = \frac{0.60}{1 - (1.0)(400/11{,}497)} = \frac{0.60}{1 - 0.035} = \frac{0.60}{0.965} = 0.622 \implies \text{use } B_1 = 1.00$$

5. **Amplified moment**:

   $$M_{rx} = 1.00 \times 80 + 1.19 \times 120 = 80 + 143 = 223 \text{ kip-ft}$$

6. **Interaction check**:

   $$\frac{P_r}{P_c} = \frac{400}{1{,}054} = 0.380 \ge 0.20 \implies \text{H1-1a}$$

   $$0.380 + \frac{8}{9}\left(\frac{223}{491} + 0\right) = 0.380 + 0.889 \times 0.454 = 0.380 + 0.404 = 0.784 \le 1.0 \checkmark$$

**Result:** Interaction ratio = **0.784** < 1.0 → W12×96 is adequate. The column uses about 78% of its combined capacity; there is no need to upsize, but the moment amplification ($B_2 = 1.19$) increased the required bending demand by 19%.

---

## 7. Common Mistakes & Pitfalls

- **Forgetting $B_2 \ge 1.0$ rule:** AISC requires both $B_1$ and $B_2$ to be at least 1.0. A computed $B_1 < 1.0$ (physically possible for double-curvature) is set to 1.0 because the equations cannot amplify "negative" P-δ effects in the conservative direction.

- **Using wrong sign convention for $M_1/M_2$:** AISC defines $M_1/M_2$ as *positive when the member bends in reverse (double) curvature*. Many students use the opposite sign. Reverse curvature → lower $C_m$ → lower $B_1$ → less amplification, which is correct (the bent column gets less additional moment).

- **Mixing $P_c$ and $P_n$:** Always apply $\phi_c = 0.90$ before entering the interaction equation. Entering nominal $P_n$ (unfactored capacity) against factored demand $P_u$ gives an unconservative result.

- **Using one interaction equation for all columns:** Check the ratio $P_r/P_c$ first — forgetting to switch to H1-1b for lightly loaded columns gives excessively conservative designs.

- **Neglecting biaxial bending** in 3-D frames: columns in corner bays bend about both axes simultaneously; H1-1a must include both the $x$ and $y$ moment ratios.

---

## 8. Connections to Other Topics

- **Compression member design (06-C):** The available axial strength $P_c$ is computed from Chapter E using the slenderness curve — beam-column design is a direct extension with $M \neq 0$.
- **Lateral-torsional buckling (06-D):** $M_{cx}$ is taken from the Chapter F LTB check; a beam-column with long unbraced lengths will have a reduced $M_{cx}$, making it less efficient.
- **Structural dynamics and seismic (11):** Moment frames rely on beam-column behavior for ductile energy dissipation; the $R$, $\Omega_0$, $C_d$ factors amplify design demands precisely because beam-columns must remain stable at large drifts.
- **Matrix structural analysis (04):** The stiffness matrix of a beam-column element includes a geometric stiffness term $[K_g]$ that represents the softening effect of axial compression — the mathematical basis for $B_1$ and $B_2$.

---

## 9. Further Reading

| Resource | Where to look |
|----------|--------------|
| AISC 360-22 | Chapter C (Direct Analysis), Chapter H (H1 equations), Appendix 8 (B₁-B₂ method) |
| Segui, *Steel Design*, 6th ed. | Chapter 6: Beam-Columns |
| AISC Design Guide 3 | Serviceability drift limits for frames |
| McGuire, Gallagher & Ziemian, _Matrix Structural Analysis_ | Chapter 9: Geometric nonlinearity |
| Galambos & Surovek, *Structural Stability of Steel* | Chapter 8: Beam-column behavior |

---

## 10. Quick Self-Check

- [ ] I can state both H1-1a and H1-1b from memory and know when each applies.
- [ ] I can explain the physical difference between the $P$-$\delta$ ($B_1$) and $P$-$\Delta$ ($B_2$) effects.
- [ ] I know what $C_m$ represents and why double-curvature bending gives a lower value.
- [ ] I can carry out a full 9-step beam-column check from given section properties.
- [ ] I can connect this topic to compression design (06-C) and flexural design (06-D).

---

---

## 11. Graduate Extension: Stability Functions, Direct Analysis & $P$-$\Delta$ Theory

### 11.1 Beam-Column ODE and Stability Functions

The fundamental equation for a beam-column with end moments $M_A$ (near end) and $M_B$ (far end) and axial compression $P$ is (Timoshenko & Gere, *Theory of Elastic Stability*, §1.10):

$$
EI y'' + Py = M_A - (M_A - M_B)\frac{x}{L}
\tag{second-order ODE}
$$

Let $k = \sqrt{P/EI}$ (compression case). The **general solution** is:

$$
y(x) = C_1 \sin(kx) + C_2 \cos(kx) + \frac{M_A}{P} - \frac{(M_A - M_B)}{PL}x
$$

Applying boundary conditions $y(0) = 0$, $y(L) = 0$ and differentiating to find the end slopes $\theta_A = y'(0)$ and $\theta_B = y'(L)$, then expressing end moments in terms of end slopes through matrix inversion, yields the **stability functions** $s$ and $c$ (also called $S$ and $C$ in some texts):

$$
\begin{pmatrix} M_A \\ M_B \end{pmatrix} = \frac{EI}{L}\begin{bmatrix} s & c \\ c & s \end{bmatrix}\begin{pmatrix} \theta_A \\ \theta_B \end{pmatrix}
$$

where:

$$
s(\mu) = \mu \frac{\sin\mu - \mu\cos\mu}{2 - 2\cos\mu - \mu\sin\mu}, \qquad c(\mu) = \mu \frac{\mu - \sin\mu}{2 - 2\cos\mu - \mu\sin\mu}
$$

and $\mu = kL = L\sqrt{P/EI} = \pi\sqrt{P/P_e}$.

**Physical meaning:** When $P = 0$, $\mu = 0$, and using L’Hôpital’s rule: $s(0) = 4$ and $c(0) = 2$, recovering the standard slope-deflection stiffness matrix. As $P \to P_e$ (the Euler load), $\mu \to \pi$: the denominator vanishes, $s \to \infty$, meaning the member goes unstable at zero applied moment — exactly the Euler buckling condition.

---

### 11.2 Derivation of the $B_1$ Amplifier from Stability Functions

For a **no-sway** (braced) member with end moments $M_A$ and $M_B$ ($|M_A| \geq |M_B|$) and no transverse loading, the maximum moment amplification due to axial compression can be derived from the stability-function stiffness equations.

**Exact amplifier (Chen & Atsuta 1977).** For a perfectly pinned-pinned member with uniform moment $M_0$, the maximum deflection occurs at $x = L/2$:

$$
y_{max} = \frac{M_0}{P}\left(\frac{1}{\cos(\mu/2)} - 1\right)
$$

The total moment at midspan, including the $P \cdot y$ term:

$$
M_{max} = M_0 \cdot \frac{1}{\cos(\mu/2)} = M_0 \cdot \frac{1}{\cos\left(\frac{\pi}{2}\sqrt{P/P_e}\right)}
$$

**AISC $B_1$ approximation.** Replacing the exact trigonometric amplifier with a simple closed-form fit (Ketter 1961; AISC Commentary App. 8):

$$
B_1 = \frac{C_m}{1 - P/P_{e1}} \geq 1.0
\tag{AISC App. 8 Eq. A-8-3}
$$

Validation: at $P = 0.5 P_e$, exact amplifier for $C_m = 1$ is $1/\cos(\pi/(2\sqrt{2})) = 1/\cos(1.11) = 1/0.414 = 2.41$; AISC approximation: $1/(1-0.5) = 2.0$. The AISC formula is **conservative by ~20%** for high axial ratios.

For non-uniform moment, $C_m < 1$ because the maximum moment occurs at a less amplified location than the end moment. The $C_m = 0.6 - 0.4(M_1/M_2)$ formula (AISC Eq. A-8-4) is a fit to the exact stability-function result:

$$
C_m = 1 - \frac{\pi^2 EI \delta_0^2}{M_0 L^2}
$$

for built-up end moments, where $\delta_0$ is the first-order deflection under the end moments alone.

---

### 11.3 Story-Level $P$-$\Delta$ ($B_2$) and Story Buckling

The $P$-$\Delta$ effect acts at the story level: the total vertical load $\Sigma P_{story}$ on all columns in the story acts on the story drift $\Delta_H$, creating an overturning moment increment. Yura (1971) derived the **story buckling load** by treating all columns in a story as a unit:

$$
\Sigma P_{e,story} = \frac{R_M \Sigma H \cdot L_{story}}{\Delta_H}
$$

where $\Sigma H$ is the total story shear, $\Delta_H$ is the corresponding first-order story drift, and $R_M$ accounts for the different column types in the story:

- $R_M = 1.0$: braced frames (no sway columns)
- $R_M = 0.85$: moment frames (typically)

**Derivation of $R_M = 0.85$.** Consider a story with a mix of leaning columns (gravity-only, no lateral stiffness) and moment columns. The moment columns must resist both their own $P$-$\Delta$ and that of the leaning columns. The ratio of story sway capacity accounting for this redistribution was derived by Yura using story stiffness summation:

$$
R_M = 1 - 0.15\frac{\Sigma P_{leaning}}{\Sigma P_{story}} \approx 0.85 \text{ for typical building frames}
$$

The $B_2$ amplifier follows immediately:

$$
B_2 = \frac{1}{1 - \alpha \Sigma P_{story}/\Sigma P_{e,story}} \geq 1.0
\tag{AISC App. 8 Eq. A-8-6}
$$

where $\alpha = 1.0$ (LRFD) or $1.6$ (ASD). The factor $1.6$ for ASD compensates for the fact that service loads $P_a$ are lower than factored loads $P_u \approx 1.6 P_a$ on average.

---

### 11.4 Direct Analysis Method (DAM): Theoretical Basis

The Appendix 8 ($B_1$-$B_2$) method is an **indirect second-order analysis** method. The **Direct Analysis Method (DAM)** in AISC 360-22 Chapter C is a more rigorous alternative that more accurately captures second-order effects by modifying the analysis model itself rather than amplifying first-order results.

**DAM modifications (AISC 360-22 Chapter C):**

1. **Reduced stiffness:** Replace $EI$ with $0.8\tau_b EI$ and $EA$ with $0.8 EA$ for all members in the analysis.$\tau_b = 1.0$ when $P_r/(\phi_c P_y) \leq 0.5$; for $P_r/(\phi_c P_y) > 0.5$: $\tau_b = 4[P_r/(\phi_cP_y)][1-P_r/(\phi_cP_y)]$.

2. **Notional loads:** Apply horizontal notional loads $N_i = 0.002\alpha Y_i$ at each story level ($Y_i$ = gravity load at level $i$) to account for initial imperfections equivalent to $L/500$ out-of-plumbness.

3. **No effective length factor:** Use $K = 1.0$ (i.e., $KL = L_{actual}$) in all member strength calculations, because the analysis already captures the sway amplification.

**Theoretical basis.** The 0.8 stiffness reduction has two components:
- Factor of 0.9 for uncertainty in $EI$ (material variability, joint flexibility)
- Factor of $\tau_b \leq 1.0$ for partial yielding under residual stresses (analogous to the tangent-modulus reduction for columns)

The notional load $N_i = 0.002 \alpha Y_i$ corresponds to a story out-of-plumbness $\Delta_0/L = 1/500$ (AISC Commentary C1), which the commentary notes is consistent with the $L/1000$ initial crookedness assumed in column curve calibration applied to a story of two half-column heights.

**Comparison of methods:**

| Method | Analysis type | $K$ factor | Accounts for system imperfections |
|--------|--------------|-----------|----------------------------------|
| ELM (Effective Length) | 1st-order + $B_1B_2$ | $K \neq 1$ from chart | No (implicit in $K$) |
| Appendix 8 ($B_1B_2$) | 1st-order + amplifiers | $K = 1$ | Via notional loads |
| DAM (Direct Analysis) | Rigorous 2nd-order | $K = 1$ | Explicitly via $\tau_b$, $N_i$ |

For $\Delta_H/L \leq 1/500$, all methods give essentially the same result; for $\Delta_H/L > 1/500$ (flexible frames such as industrial buildings), DAM gives the most accurate and typically the least conservative result.

---

### 11.5 Interaction Equations for Unsymmetric Loading & Biaxial Bending

The H1-1a and H1-1b equations are **linear interaction equations** that are conservative approximations of the true elliptical interaction surface derived from plasticity theory. For a compact doubly-symmetric I-section under combined axial, strong-axis moment, and weak-axis moment, the **true plastic interaction surface** (Duan & Chen 1989) is:

$$
\left(\frac{M_x}{M_{px}}\right)^{1.6} + \left(\frac{M_y}{M_{py}}\right)^2 + \frac{P}{P_y} \leq 1.0
$$

The AISC H1 linear interaction can overestimate required strength by up to 15% compared to this surface for intermediate biaxial loading levels (strong $M_x$ + moderate $M_y$). Recent research by Ziemian (2010) shows that **ELM + H1-1a** gives $\beta \geq 2.5$ for typical proportions even at the most critical loading combinations, confirming the AISC approach is safe.

For **hollow structural sections (HSS)** under biaxial bending with axial load, AISC 360-22 Commentary H1 provides an alternative circular interaction:

$$
\frac{P_r}{P_c} + \left(\frac{M_{rx}^2 + M_{ry}^2}{M_{cx}^2}\right)^{0.5} \leq 1.0
$$

This is more accurate for HSS because the box section has equal bending capacity in both directions and the cross terms in the moment interaction are dominated by the combined magnitude, not an additive sum.

---

*Created by Structural Engineering Tutor • 2026-03-18 | Upgraded to Graduate level: 2026-03-18*
