# Lateral-Torsional Buckling (LTB) of Beams

**Subject area:** Steel Design (AISC 360-22)
**Design standard / primary reference:** AISC 360-22 §F2; AISC Steel Construction Manual, 16th Ed.; Galambos & Surovek, *Structural Stability of Steel*
**Depth level:** Graduate — rigorous derivation
**Estimated study time:** 130 minutes

---

## 1. Introduction & Motivation

When a steel beam bends about its strong axis, the compression flange behaves like a slender column: if the beam is not adequately braced along its length, the compression flange can buckle sideways while the tension flange tries to remain in place. This out-of-plane movement couples lateral displacement with a twisting of the cross-section — the phenomenon is called **lateral-torsional buckling (LTB)**. LTB is the single most important stability limit state for steel beams and governs the design of the majority of unbraced beams in practice.

Unlike axial compression members, where buckling is purely translational, LTB is fundamentally a *coupled* instability: the beam simultaneously displaces laterally and rotates (twists) about its longitudinal axis. The resistance to LTB comes from two sources: the weak-axis bending stiffness $EI_y$ (resists lateral displacement) and the torsional stiffness $GJ + EI_w/L_b^2$ (resists twisting), where the $GJ$ term represents St. Venant (uniform) torsion and the $EI_w$ term represents warping torsion.

AISC 360-22 §F2 codifies LTB for doubly symmetric compact I-shaped members bent about their strong axis. The specification divides behavior into three zones based on the **unbraced length** $L_b$ (the distance between points of lateral bracing): a *plastic zone* where full plastic moment is reached, an *inelastic LTB zone* where strength is reduced but the beam has partially yielded, and an *elastic LTB zone* where buckling occurs before any yielding. Understanding which zone governs — and how the moment gradient amplifies or reduces LTB capacity — is the core skill of this topic.

## 2. Key Concepts & Definitions

| Term | Symbol | Definition |
|------|--------|------------|
| Unbraced length | $L_b$ | Distance between points of lateral brace, twist restraint, or end support (in or mm) |
| Limiting unbraced length — plastic | $L_p$ | Maximum $L_b$ for which LTB does not reduce $M_n$ below $M_p$ (full plasticity) |
| Limiting unbraced length — inelastic | $L_r$ | $L_b$ above which LTB is fully elastic (no yielding before buckling) |
| Plastic moment | $M_p$ | $F_y Z_x$; the cross-section's maximum moment capacity at full yielding |
| Elastic section modulus | $S_x$ | $I_x / (d/2)$; moment divided by extreme-fiber stress in elastic range (in³ or mm³) |
| Plastic section modulus | $Z_x$ | First moment of area about plastic neutral axis (in³ or mm³) |
| Effective radius of gyration | $r_{ts}$ | $r_{ts}^2 = \sqrt{I_y C_w}/S_x$; governs elastic LTB slenderness |
| Weak-axis radius of gyration | $r_y$ | $\sqrt{I_y/A}$; controls $L_p$ |
| St. Venant torsional constant | $J$ | Section property resisting uniform (St. Venant) torsion (in⁴ or mm⁴) |
| Warping constant | $C_w$ | Section property resisting warping (flange-bending) torsion (in⁶ or mm⁶) |
| Distance between flange centroids | $h_o$ | $\approx d - t_f$ for I-shapes (in or mm) |
| Moment gradient factor | $C_b$ | Amplification factor that accounts for non-uniform moment in the unbraced segment; $C_b = 1.0$ for uniform moment (worst case) |
| Monosymmetry parameter | $c$ | $c = 1$ for doubly symmetric I-shapes; $c = (h_o/2)\sqrt{I_y/C_w}$ for channels |
| Elastic critical stress | $F_{cr}$ | Elastic LTB stress; compares to $F_y$ to determine if yielding occurs before buckling |
| Resistance factor (LRFD) | $\phi_b$ | $\phi_b = 0.90$ for flexure |
| Safety factor (ASD) | $\Omega_b$ | $\Omega_b = 1.67$ for flexure |
| Compact section | — | Section satisfying $\lambda \le \lambda_{pf}$ (flange) and $\lambda \le \lambda_{pw}$ (web); required for $M_n = M_p$ |

## 3. Governing Equations

### 3.1 Equation Summary Table

| Equation | Description | AISC 360-22 Reference |
|----------|-------------|----------------------|
| $M_p = F_y Z_x$ | Plastic moment | §F2.1 |
| $M_n = M_p$ (when $L_b \le L_p$) | No LTB — plastic zone | §F2.1, Eq. F2-1 |
| $M_n = C_b\!\left[M_p - (M_p - 0.7F_y S_x)\frac{L_b - L_p}{L_r - L_p}\right] \le M_p$ | Inelastic LTB | §F2.2, Eq. F2-2 |
| $M_n = F_{cr} S_x \le M_p$ | Elastic LTB | §F2.3, Eq. F2-3 |
| $F_{cr} = \dfrac{C_b \pi^2 E}{(L_b/r_{ts})^2}\sqrt{1 + 0.078\dfrac{Jc}{S_x h_o}\!\left(\frac{L_b}{r_{ts}}\right)^{\!2}}$ | Elastic critical stress | §F2.4, Eq. F2-4 |
| $L_p = 1.76\, r_y\sqrt{E/F_y}$ | Limiting length — plastic zone | §F2.5, Eq. F2-5 |
| $L_r = 1.95\, r_{ts}\dfrac{E}{0.7F_y}\sqrt{\dfrac{Jc}{S_x h_o} + \sqrt{\left(\dfrac{Jc}{S_x h_o}\right)^{\!2} + 6.76\!\left(\dfrac{0.7F_y}{E}\right)^{\!2}}}$ | Limiting length — elastic zone | §F2.6, Eq. F2-6 |
| $r_{ts}^2 = \dfrac{\sqrt{I_y C_w}}{S_x}$ | Effective radius of gyration | §F2.7, Eq. F2-7 |
| $C_b = \dfrac{12.5\, M_{\max}}{2.5\, M_{\max} + 3M_A + 4M_B + 3M_C}$ | Moment gradient factor | §F1, Eq. F1-1 |

### 3.2 Key Display Equations

**Plastic moment (full plasticity, no LTB):**
$$M_p = F_y Z_x \tag{F2-1}$$

**Inelastic LTB nominal strength ($L_p < L_b \le L_r$):**
$$M_n = C_b\!\left[M_p - (M_p - 0.7F_y S_x)\frac{L_b - L_p}{L_r - L_p}\right] \le M_p \tag{F2-2}$$

**Elastic LTB nominal strength ($L_b > L_r$):**
$$M_n = F_{cr} S_x \le M_p \tag{F2-3}$$

**Elastic critical stress:**
$$F_{cr} = \frac{C_b \pi^2 E}{(L_b/r_{ts})^2}\sqrt{1 + 0.078\frac{Jc}{S_x h_o}\!\left(\frac{L_b}{r_{ts}}\right)^{\!2}} \tag{F2-4}$$

**Limiting unbraced lengths:**
$$L_p = 1.76\, r_y\sqrt{\frac{E}{F_y}} \tag{F2-5}$$

$$L_r = 1.95\, r_{ts}\frac{E}{0.7F_y}\sqrt{\frac{Jc}{S_x h_o} + \sqrt{\left(\frac{Jc}{S_x h_o}\right)^{\!2} + 6.76\!\left(\frac{0.7F_y}{E}\right)^{\!2}}} \tag{F2-6}$$

**Moment gradient factor:**
$$C_b = \frac{12.5\, M_{\max}}{2.5\, M_{\max} + 3M_A + 4M_B + 3M_C} \tag{F1-1}$$

**LRFD design check:**
$$\phi_b M_n \ge M_u \qquad (\phi_b = 0.90)$$

**ASD design check:**
$$\frac{M_n}{\Omega_b} \ge M_a \qquad (\Omega_b = 1.67)$$

### 3.3 Variable Legend

| Symbol | Description | SI Units | US Customary Units |
|--------|-------------|----------|--------------------|
| $M_n$ | Nominal flexural strength | N·mm | kip-in (or kip-ft) |
| $M_p$ | Plastic moment capacity | N·mm | kip-in |
| $M_u$ | Required flexural strength (LRFD) | N·mm | kip-in |
| $M_a$ | Required flexural strength (ASD) | N·mm | kip-in |
| $F_y$ | Specified minimum yield stress | MPa | ksi |
| $E$ | Modulus of elasticity (200,000 MPa / 29,000 ksi) | MPa | ksi |
| $Z_x$ | Plastic section modulus about strong axis | mm³ | in³ |
| $S_x$ | Elastic section modulus about strong axis | mm³ | in³ |
| $I_y$ | Moment of inertia about weak axis | mm⁴ | in⁴ |
| $J$ | St. Venant torsional constant | mm⁴ | in⁴ |
| $C_w$ | Warping constant | mm⁶ | in⁶ |
| $r_y$ | Weak-axis radius of gyration | mm | in |
| $r_{ts}$ | Effective radius of gyration for LTB | mm | in |
| $h_o$ | Distance between flange centroids | mm | in |
| $c$ | Monosymmetry parameter ($c = 1$ for doubly symmetric I) | — | — |
| $L_b$ | Unbraced length | mm | in |
| $L_p$ | Limiting length for plastic behavior | mm | in |
| $L_r$ | Limiting length for inelastic behavior | mm | in |
| $F_{cr}$ | Elastic critical buckling stress | MPa | ksi |
| $C_b$ | Moment gradient amplification factor | — | — |
| $M_{\max}$ | Maximum moment in unbraced segment (absolute value) | N·mm | kip-in |
| $M_A$ | Moment at quarter point of unbraced segment (absolute value) | N·mm | kip-in |
| $M_B$ | Moment at midpoint of unbraced segment (absolute value) | N·mm | kip-in |
| $M_C$ | Moment at three-quarter point of unbraced segment (absolute value) | N·mm | kip-in |

## 4. Derivation

The following derivation explains *why* the three LTB zones exist and where the limiting lengths $L_p$ and $L_r$ come from. The treatment is physical and algebraic — the full variational derivation is reserved for graduate depth.

**Step 1 — Elastic LTB critical moment.**
Consider a simply supported, doubly symmetric I-beam of length $L_b$ under uniform moment $M$, laterally unbraced. Classical stability theory (Timoshenko & Gere, *Theory of Elastic Stability*, 2nd ed., §5.2) shows that the beam buckles when the applied moment equals the elastic critical moment:

$$M_{ocr} = \frac{\pi}{L_b}\sqrt{EI_y\!\left(GJ + \frac{\pi^2 EI_y r_o^2}{L_b^2}\right)}$$

where $r_o^2 = r_x^2 + r_y^2 + \bar{x}_o^2$ and the warping stiffness $EI_w$ is embedded in $r_o$. AISC reformulates this for practical sections into the $F_{cr}$ expression of Eq. F2-4 using $r_{ts}$ and $h_o$, which groups $EI_y$ and $EC_w$ into one convenient parameter ($r_{ts}^2 = \sqrt{I_y C_w}/S_x$).

**Step 2 — Identify the elastic LTB limit ($L_r$).**
Elastic LTB is possible only when the beam is still fully elastic at buckling, i.e., $F_{cr} \ge F_y$. The threshold $L_r$ is defined as the unbraced length at which the elastic critical stress equals $0.7 F_y$ (the stress in the compression flange that remains elastic at the onset of inelastic LTB, which is $0.7 F_y$ because residual compressive stresses in hot-rolled sections are typically $0.3 F_y$). Setting $F_{cr} = 0.7 F_y$ in Eq. F2-4 (with $C_b = 1$) and solving for $L_b$ yields the closed-form expression in Eq. F2-6.

**Step 3 — Identify the plastic limit ($L_p$).**
Full plasticity ($M_n = M_p$) is achieved when the beam yields uniformly across its cross-section before any lateral movement occurs. Research by Yura, Galambos, and Ravindra (1978) established that the unbraced length below which a steel beam can reliably rotate to the plastic mechanism without lateral instability is:
$$L_p = 1.76\, r_y\sqrt{\frac{E}{F_y}} \tag{F2-5}$$
This expression comes from calibration of test data, but physically it resembles the Euler buckling length for a column with slenderness $r_y$: a shorter column buckles at a higher stress, so the column analogy for the compression flange dictates that shorter beams reach full plasticity. Note $L_p$ depends on $r_y$ (not $r_{ts}$) because weak-axis bending stiffness dominates at short lengths where warping effects are negligible.

**Step 4 — Inelastic LTB linear interpolation.**
Between $L_p$ and $L_r$, the nominal strength transitions from $M_p$ (full plasticity) down to $0.7 F_y S_x$ (which corresponds to $F_{cr} = 0.7 F_y$ at $L_r$). AISC adopts a **linear interpolation** between these two anchor points:

$$M_n = M_p - (M_p - 0.7F_y S_x)\frac{L_b - L_p}{L_r - L_p}$$

This is consistent with extensive experimental and analytical evidence that shows the $M_n$–$L_b$ relationship in the inelastic zone is nearly linear. The factor $C_b$ amplifies the whole expression upward (never reducing it below $C_b = 1$ results) because a non-uniform moment diagram reduces the demand on the compression flange compared to uniform moment — the physical justification is that the compression-flange stress peak is lower when the moment gradient is steeper.

**Step 5 — Role of $C_b$.**
The Eq. F1-1 formula for $C_b$ was developed by Kirby and Nethercot (1979) and later refined. It weights the moments at the quarter, mid, and three-quarter points of the unbraced segment. For uniform moment throughout the segment, $M_A = M_B = M_C = M_{\max}$, giving $C_b = 12.5/(2.5 + 3 + 4 + 3) = 12.5/12.5 = 1.0$ — the reference (worst-case) condition. For a segment with moment at one end and zero at the other (single-curvature triangular diagram), $C_b \approx 1.67$. For double-curvature bending (reverse moment), $C_b$ can exceed 2, reflecting that the compression-flange stress reverses and the beam is much more stable.

**Step 6 — Compact section prerequisite.**
The three-zone LTB model in §F2 assumes the cross-section is **compact** — meaning local buckling of the flange or web does not occur before LTB. AISC 360-22 Table B4.1b requires:

Flange: $\displaystyle\lambda_f = \frac{b_f}{2t_f} \le \lambda_{pf} = 0.38\sqrt{\frac{E}{F_y}}$

Web: $\displaystyle\lambda_w = \frac{h}{t_w} \le \lambda_{pw} = 3.76\sqrt{\frac{E}{F_y}}$

If either limit is violated, non-compact or slender provisions (§F3, §F4) apply instead.

## 5. Design / Application Procedure

The following LRFD procedure applies to doubly symmetric compact I-shapes bent about their strong axis (AISC 360-22 §F2):

1. **Confirm compact section.** Verify $\lambda_f \le \lambda_{pf}$ and $\lambda_w \le \lambda_{pw}$ from AISC 360-22 Table B4.1b. Most W-shapes of A992 steel (Fy = 50 ksi) are compact; confirm using the AISC Manual Part 1 "compact/noncompact" designation.

2. **Collect section properties.** From the AISC Manual Part 1 tables, record $Z_x$, $S_x$, $r_y$, $J$, $C_w$, $r_{ts}$, and $h_o$ for the chosen W-shape.

3. **Compute $M_p$.** $M_p = F_y Z_x$ (AISC 360-22 Eq. F2-1). Convert to kip-ft if needed ($\div 12$).

4. **Determine $L_b$.** Identify all lateral bracing points (top flange braced by slab, deck, purlins; or explicit lateral braces). $L_b$ is the maximum spacing between them.

5. **Compute $L_p$ (Eq. F2-5):**
$$L_p = 1.76\, r_y\sqrt{\frac{E}{F_y}}$$
Result in inches. Divide by 12 for feet.

6. **Compute $L_r$ (Eq. F2-6):**
$$L_r = 1.95\, r_{ts}\frac{E}{0.7F_y}\sqrt{\frac{Jc}{S_x h_o} + \sqrt{\left(\frac{Jc}{S_x h_o}\right)^{\!2} + 6.76\!\left(\frac{0.7F_y}{E}\right)^{\!2}}}$$
Use $c = 1$ for doubly symmetric I-shapes. Result in inches.

7. **Determine the LTB zone:**
   - If $L_b \le L_p$: **No LTB**. Proceed to Step 10 with $M_n = M_p$.
   - If $L_p < L_b \le L_r$: **Inelastic LTB**. Proceed to Steps 8–10.
   - If $L_b > L_r$: **Elastic LTB**. Proceed to Steps 8–10.

8. **Compute $C_b$ (Eq. F1-1).**
   For each unbraced segment, identify $M_{\max}$, $M_A$ (quarter point), $M_B$ (midpoint), $M_C$ (three-quarter point) as absolute values along the unbraced segment:
   $$C_b = \frac{12.5\, M_{\max}}{2.5\, M_{\max} + 3M_A + 4M_B + 3M_C}$$
   For conservative design with unknown moment diagram, use $C_b = 1.0$.

9. **Compute $M_n$:**
   - *Inelastic LTB (Eq. F2-2):*
     $$M_n = C_b\!\left[M_p - (M_p - 0.7F_y S_x)\frac{L_b - L_p}{L_r - L_p}\right] \le M_p$$
   - *Elastic LTB (Eqs. F2-3 and F2-4):*
     $$F_{cr} = \frac{C_b \pi^2 E}{(L_b/r_{ts})^2}\sqrt{1 + 0.078\frac{Jc}{S_x h_o}\!\left(\frac{L_b}{r_{ts}}\right)^{\!2}}$$
     $$M_n = F_{cr} S_x \le M_p$$

10. **Apply LRFD (or ASD) check:**
    - LRFD: $\phi_b M_n \ge M_u$, where $\phi_b = 0.90$
    - ASD: $M_n / \Omega_b \ge M_a$, where $\Omega_b = 1.67$
    - Utilization ratio: $U = M_u / (\phi_b M_n) \le 1.0$

## 6. Worked Example

**Problem:** A W18×50 (A992 steel, $F_y = 50$ ksi, $E = 29{,}000$ ksi) simply supported beam spans $L = 20$ ft and carries a **superimposed dead load** of $w_D = 1.0$ kip/ft and a **live load** of $w_L = 2.0$ kip/ft (uniform along the full span). The beam is braced laterally at the supports and at midspan only, giving an **unbraced length $L_b = 10$ ft**. The compression flange is the top flange; bracing is provided by purlins at the supports and at midspan.

**Given:**

*Loading:*
- $w_D = 1.0$ kip/ft, $w_L = 2.0$ kip/ft (uniform)
- Span $L = 20$ ft
- Unbraced length $L_b = 10$ ft = 120 in

*W18×50 section properties (AISC Manual, 16th Ed., Part 1):*

| Property | Value |
|----------|-------|
| $d$ | 18.0 in |
| $b_f$ | 7.495 in |
| $t_f$ | 0.570 in |
| $t_w$ | 0.355 in |
| $Z_x$ | 101 in³ |
| $S_x$ | 88.9 in³ |
| $I_y$ | 40.1 in⁴ |
| $r_y$ | 1.65 in |
| $J$ | 1.24 in⁴ |
| $C_w$ | 3,160 in⁶ |
| $r_{ts}$ | 1.98 in |
| $h_o$ | 17.4 in |

**Required:** (a) Check compactness; (b) Compute $L_p$ and $L_r$; (c) Determine LTB zone; (d) Compute $C_b$ for the critical unbraced segment; (e) Compute $\phi_b M_n$; (f) Check adequacy against $M_u$.

**Solution:**

**Step 1 — Factored load and required moment.**

Using LRFD load combination 2 (ASCE 7-22 §2.3.1):
$$w_u = 1.2\,w_D + 1.6\,w_L = 1.2(1.0) + 1.6(2.0) = 1.2 + 3.2 = 4.4 \text{ kip/ft}$$

Maximum factored moment at midspan of a simply supported beam with uniform load:
$$M_u = \frac{w_u L^2}{8} = \frac{4.4(20)^2}{8} = \frac{4.4 \times 400}{8} = 220 \text{ kip-ft} = 2{,}640 \text{ kip-in}$$

**Step 2 — Check compactness (AISC 360-22 Table B4.1b).**

Flange slenderness:
$$\lambda_f = \frac{b_f}{2t_f} = \frac{7.495}{2(0.570)} = \frac{7.495}{1.140} = 6.57$$
$$\lambda_{pf} = 0.38\sqrt{\frac{E}{F_y}} = 0.38\sqrt{\frac{29{,}000}{50}} = 0.38 \times 24.08 = 9.15$$
$$6.57 < 9.15 \quad \checkmark \quad \text{Compact flange}$$

Web slenderness (using tabulated value from AISC Manual; for W18×50: $h/t_w = 45.2$):
$$\lambda_w = 45.2$$
$$\lambda_{pw} = 3.76\sqrt{\frac{E}{F_y}} = 3.76\sqrt{\frac{29{,}000}{50}} = 3.76 \times 24.08 = 90.5$$
$$45.2 < 90.5 \quad \checkmark \quad \text{Compact web}$$

The W18×50 is a **compact section**. AISC 360-22 §F2 applies.

**Step 3 — Compute $M_p$ (Eq. F2-1).**
$$M_p = F_y Z_x = 50 \times 101 = 5{,}050 \text{ kip-in} = 420.8 \text{ kip-ft}$$

**Step 4 — Compute $L_p$ (Eq. F2-5).**
$$L_p = 1.76\, r_y\sqrt{\frac{E}{F_y}} = 1.76 \times 1.65 \times \sqrt{\frac{29{,}000}{50}} = 1.76 \times 1.65 \times 24.08$$
$$L_p = 2.904 \times 24.08 = 69.9 \text{ in} = \mathbf{5.83 \text{ ft}}$$

**Step 5 — Compute $L_r$ (Eq. F2-6).** Use $c = 1$ for doubly symmetric I-shape.

First, evaluate the argument of the outer square root:
$$\text{Term}_1 = \frac{Jc}{S_x h_o} = \frac{1.24 \times 1}{88.9 \times 17.4} = \frac{1.24}{1{,}546.9} = 8.02 \times 10^{-4}$$

$$\text{Term}_2 = 6.76\!\left(\frac{0.7F_y}{E}\right)^{\!2} = 6.76\!\left(\frac{35}{29{,}000}\right)^{\!2} = 6.76 \times (1.207 \times 10^{-3})^2 = 6.76 \times 1.457 \times 10^{-6} = 9.85 \times 10^{-6}$$

$$\sqrt{\text{Term}_1^2 + \text{Term}_2} = \sqrt{(8.02\times10^{-4})^2 + 9.85\times10^{-6}} = \sqrt{6.43\times10^{-7} + 9.85\times10^{-6}} = \sqrt{1.049\times10^{-5}} = 3.24\times10^{-3}$$

$$\text{Radicand} = \text{Term}_1 + \sqrt{\text{Term}_1^2 + \text{Term}_2} = 8.02\times10^{-4} + 3.24\times10^{-3} = 4.04\times10^{-3}$$

$$L_r = 1.95 \times 1.98 \times \frac{29{,}000}{0.7 \times 50} \times \sqrt{4.04 \times 10^{-3}}$$
$$= 1.95 \times 1.98 \times 828.6 \times 0.0636$$
$$= 3.861 \times 828.6 \times 0.0636 = 3.861 \times 52.7 = 203.4 \text{ in} = \mathbf{16.9 \text{ ft}}$$

**Step 6 — Determine LTB zone.**

$$L_p = 5.83 \text{ ft} \quad < \quad L_b = 10 \text{ ft} \quad < \quad L_r = 16.9 \text{ ft}$$

$$\Rightarrow \textbf{Inelastic LTB zone (Eq. F2-2 governs).}$$

**Step 7 — Compute $C_b$ for the left half-span unbraced segment (0 to 10 ft).**

The moment diagram for a simply-supported beam under uniform load is parabolic. Moments at key points within the left unbraced segment (braced at $x = 0$ and $x = 10$ ft, so segment runs from $x = 0$ to $x = 10$ ft):

$$M(x) = \frac{w_u L}{2}\cdot x - \frac{w_u x^2}{2} = \frac{4.4 \times 20}{2}\cdot x - \frac{4.4\, x^2}{2} = 44x - 2.2x^2 \quad \text{[kip-ft, } x \text{ in ft]}$$

| Point | $x$ (ft) | Moment (kip-ft) |
|-------|-----------|-----------------|
| Start of segment | 0 | 0 |
| Quarter point $M_A$ | 2.5 | $44(2.5) - 2.2(2.5)^2 = 110 - 13.75 = 96.3$ |
| Midpoint $M_B$ | 5.0 | $44(5.0) - 2.2(5.0)^2 = 220 - 55.0 = 165.0$ |
| Three-quarter point $M_C$ | 7.5 | $44(7.5) - 2.2(7.5)^2 = 330 - 123.75 = 206.3$ |
| End of segment $M_{\max}$ | 10.0 | $44(10) - 2.2(10)^2 = 440 - 220 = 220.0$ |

$$C_b = \frac{12.5 \times 220}{2.5(220) + 3(96.3) + 4(165.0) + 3(206.3)}$$
$$= \frac{2{,}750}{550 + 288.9 + 660.0 + 618.9} = \frac{2{,}750}{2{,}117.8} = \mathbf{1.30}$$

> The moment gradient ($M = 0$ at support, increasing to $M_{\max}$ at midspan) gives $C_b = 1.30 > 1.0$, meaning the beam is 30% more stable than under uniform moment.

**Step 8 — Compute $M_n$ using Eq. F2-2 (Inelastic LTB).**

First, compute the lower anchor point $0.7 F_y S_x$:
$$0.7 F_y S_x = 0.7 \times 50 \times 88.9 = 3{,}111.5 \text{ kip-in} = 259.3 \text{ kip-ft}$$

Convert all quantities to kip-in for calculation:
- $M_p = 5{,}050$ kip-in
- $0.7 F_y S_x = 3{,}111.5$ kip-in
- $L_b = 120$ in, $L_p = 69.9$ in, $L_r = 203.4$ in

$$\frac{L_b - L_p}{L_r - L_p} = \frac{120 - 69.9}{203.4 - 69.9} = \frac{50.1}{133.5} = 0.375$$

$$M_n = C_b\!\left[M_p - (M_p - 0.7F_y S_x)\frac{L_b - L_p}{L_r - L_p}\right]$$
$$= 1.30 \times \left[5{,}050 - (5{,}050 - 3{,}111.5)(0.375)\right]$$
$$= 1.30 \times \left[5{,}050 - 1{,}938.5 \times 0.375\right]$$
$$= 1.30 \times \left[5{,}050 - 727.2\right]$$
$$= 1.30 \times 4{,}322.8 = 5{,}619.6 \text{ kip-in}$$

Apply the cap: $M_n \le M_p = 5{,}050$ kip-in

$$\therefore\; M_n = 5{,}050 \text{ kip-in} = \mathbf{420.8 \text{ kip-ft}}$$

> The $C_b$ factor boosted the calculated value to 5,619.6 kip-in, but since this exceeds $M_p$, the strength is capped at $M_p$. This means the beam reaches full plasticity — the $C_b$ amplification completely offset the LTB penalty for this unbraced length.

**Step 9 — LRFD capacity check.**

$$\phi_b M_n = 0.90 \times 420.8 = \mathbf{378.7 \text{ kip-ft}}$$

$$M_u = 220 \text{ kip-ft}$$

$$U = \frac{M_u}{\phi_b M_n} = \frac{220}{378.7} = 0.581 \le 1.0 \quad \checkmark$$

**Result:** The W18×50 (A992) beam is **adequate for LTB** at $L_b = 10$ ft. The utilization ratio is 58.1%, indicating significant reserve capacity. The $C_b = 1.30$ gradient factor fully restored the beam to plastic-moment capacity for this unbraced length. The governing design check is $\phi_b M_n = 378.7$ kip-ft $\ge M_u = 220$ kip-ft. ✓

## 7. Common Mistakes & Pitfalls

- **Mistake 1 — Using $L_b$ as the full span instead of the unbraced segment length.** $L_b$ is the distance *between* lateral bracing points, not the total beam span. If a 30-ft beam is braced at the third points, $L_b = 10$ ft. Always identify every bracing point first — including slab-on-deck connections, cross-frames, and column flanges — before computing $L_b$.

- **Mistake 2 — Setting $C_b = 1.0$ for all segments without checking.** Using $C_b = 1.0$ is conservative but can lead to uneconomical designs. For most real loading conditions ($C_b > 1.0$), properly computing $C_b$ substantially increases the available moment. Conversely, do **not** apply $C_b > 1.0$ to cantilevers — AISC 360-22 Commentary §F1 states that $C_b$ shall be taken as 1.0 for cantilevers with free ends.

- **Mistake 3 — Forgetting to cap $M_n \le M_p$ when using $C_b > 1.0$.** Equation F2-2 with $C_b > 1.0$ can mathematically yield $M_n > M_p$. The specification cap of $M_n \le M_p$ is mandatory and reflects the physical limit that the cross-section cannot exceed full plasticity regardless of the moment gradient.

- **Mistake 4 — Applying §F2 to non-compact or slender sections.** If the flange or web fails the Table B4.1b compact limits, §F2 does not apply — use §F3 (non-compact) or §F4/§F5 (slender). Skipping the compactness check leads to unconservative results for slender sections.

- **Mistake 5 — Confusing $r_{ts}$ with $r_y$.** These are different section properties: $r_y = \sqrt{I_y/A}$ is the weak-axis radius of gyration; $r_{ts}^2 = \sqrt{I_y C_w}/S_x$ is the effective radius that governs LTB slenderness in the elastic zone and in computing $L_r$. The AISC Manual lists $r_{ts}$ directly in Part 1 tables — always use the tabulated value rather than computing it by hand to avoid errors.

- **Mistake 6 — Incorrectly locating the $C_b$ moment points.** $M_A$, $M_B$, and $M_C$ are at the **quarter, half, and three-quarter points of the unbraced segment** (not of the full span). If the unbraced segment runs from $x = 5$ ft to $x = 15$ ft, then $M_A$ is at $x = 7.5$ ft, $M_B$ at $x = 10$ ft, and $M_C$ at $x = 12.5$ ft.

## 8. Connections to Other Topics

- **Mechanics of Materials — Pure Bending (01-D):** LTB is a stability failure of the compression flange, which carries the same bending stress $\sigma = M\,c / I$ derived in pure bending theory. Without understanding bending stress distribution, it is impossible to appreciate why the compression flange is the unstable element.

- **Structural Stability — Euler Buckling (09-A):** LTB is a three-dimensional generalization of Euler column buckling. The compression flange behaves as a column of length $L_b$; the weak-axis $EI_y$ provides bending resistance and the warping stiffness $EC_w$ provides an additional "spring" analogous to an elastic foundation. The effective-length concept from column buckling reappears in the unbraced-length framework.

- **Structural Stability — LTB Theory (09-D):** This note covers the AISC code provisions. Topic 09-D derives the elastic LTB critical moment from the governing differential equations, including the effects of load height, end restraint, and monosymmetry — the theoretical foundation underlying the AISC expressions.

- **Steel Design — Compression Members (06-C):** The $L_p$ equation is structurally analogous to the Euler critical length for a column with $r_y$. The $C_b$ amplification factor in LTB parallels the effective-length factor $K$ in compression design — both adjust the nominal slenderness to reflect actual boundary and loading conditions.

- **Steel Design — Beam-Column Design (06-F):** When axial compression acts simultaneously with bending, the AISC H1 interaction equations combine the LTB flexural capacity $\phi_b M_n$ from §F2 with the compression capacity from §E. LTB capacity is the denominator of the bending term in those interaction equations.

- **Steel Design — Composite Beams (06-I):** A composite beam (steel + concrete slab) has the top flange continuously braced by the concrete slab through shear studs, effectively making $L_b \to 0$ for positive-moment regions. This eliminates LTB as a limit state for composite beams in positive moment zones, but LTB remains relevant in the construction stage before the slab hardens.

- **Structural Dynamics / Seismic Design (11-E):** Special Moment Frame (SMF) beams require plastic hinge formation. AISC 341-22 prescribes maximum $L_b$ limits (based on $r_y$) to ensure the beam can sustain cyclic plastic rotation without LTB degradation — a direct application of the $L_p$ concept under reversed cyclic loading.

## 9. Further Reading

| Resource | Where to look |
|----------|--------------|
| AISC 360-22 Specification for Structural Steel Buildings | Chapter F (§F1–F2); Commentary on Chapter F |
| AISC Steel Construction Manual, 16th Ed. | Part 1 (section properties); Part 3 (beam design tables with $\phi_b M_{px}$, $BF$); Part 6 (design examples) |
| Galambos, T.V. & Surovek, A.E., *Structural Stability of Steel* (2008) | Chapter 5: Beams |
| Timoshenko, S.P. & Gere, J.M., *Theory of Elastic Stability*, 2nd Ed. (1961) | §5.2: Lateral Buckling of Beams |
| Segui, W.T., *Steel Design*, 6th Ed. (2018) | Chapter 5: Beams |
| McCormac, J.C. & Csernak, S.F., *Structural Steel Design*, 6th Ed. (2021) | Chapter 8: Bending Members |
| Yura, J.A., Galambos, T.V. & Ravindra, M.K. (1978), "The bending resistance of steel beams," *ASCE J. Structural Division*, 104(ST9) | Full paper (basis for $L_p$ formula) |
| AISC Design Guide 25: *Frame Design Using Web-Tapered Members* (2011) | Appendix on LTB of non-prismatic members |

## 10. Quick Self-Check

- [ ] I can state the three LTB zones, the governing equation for each, and name the physical meaning of $L_p$ and $L_r$.
- [ ] I can write the inelastic LTB equation (Eq. F2-2) from memory and identify every symbol, including the two anchor moments $M_p$ and $0.7 F_y S_x$.
- [ ] I know the difference between $r_y$ and $r_{ts}$ and can explain which property controls $L_p$ versus $L_r$.
- [ ] I can compute $C_b$ using Eq. F1-1, correctly locating $M_A$, $M_B$, $M_C$ within the unbraced segment, and explain why $C_b = 1.0$ for uniform moment and why it is capped downward (not upward) for cantilevers.
- [ ] I understand why $M_n$ must be capped at $M_p$ even when $C_b > 1.0$ amplifies the bracketed expression above $M_p$.
- [ ] I can perform the compactness check from Table B4.1b and know which code section applies if the section is non-compact.
- [ ] I reproduced the worked example (W18×50, $L_b = 10$ ft) and obtained $\phi_b M_n = 378.7$ kip-ft with utilization $U = 58.1\%$.
- [ ] I can connect LTB to at least two other structural engineering topics and explain the physical link.

---

---

## 11. Graduate Extension: Full LTB Derivation from Variational Mechanics

### 11.1 Governing Differential Equations for Elastic LTB

The complete elastic LTB problem was first solved by Prandtl (1899) for a narrow rectangular cross-section and generalized by Michell (1899) and Timoshenko (1905) to I-sections. The derivation below follows Timoshenko & Gere, *Theory of Elastic Stability*, §5.2.

**Setup.** A doubly symmetric I-beam of span $L$, loaded by equal and opposite end moments $M_0$ (pure bending case, $C_b = 1$). The pre-buckled state has displacement $v = 0$ (no lateral deflection), $\phi = 0$ (no twist). Under the buckling perturbation:

- $u(x)$: lateral displacement of shear center
- $\phi(x)$: angle of twist about longitudinal axis

**Equilibrium of the laterally displaced configuration.** The moment vector in the pre-buckled state is $\mathbf{M}_0 = M_0 \mathbf{e}_z$ (about the strong axis). After lateral bending by $u$ and twisting by $\phi$:

- Component causing lateral bending: $M_0 \phi$ (moment about weak axis due to twist)
- Component causing twisting: $M_0 u'$ (torque due to lateral curvature)

The coupled governing equations for the buckled state are:

$$
EI_y u'' + M_0 \phi = 0 \tag{1: lateral bending}
$$

$$
EC_w \phi'''' - GJ \phi'' + M_0 u'' = 0 \tag{2: torsion}
$$

where the torsion equation combines **St. Venant torsion** ($GJ\phi'$) and **warping torsion** ($EC_w\phi'''$).

**Step 1 — Decouple the equations.** From equation (1): $u'' = -M_0\phi/(EI_y)$. Substitute into equation (2):

$$
EC_w \phi'''' - GJ \phi'' - \frac{M_0^2}{EI_y} \phi = 0
$$

**Step 2 — Assume sinusoidal mode shape.** For pin-ended beam: $\phi(x) = \Phi \sin(\pi x / L)$, so $\phi'' = -(\pi/L)^2 \phi$ and $\phi'''' = (\pi/L)^4 \phi$. Substituting:

$$
EC_w\left(\frac{\pi}{L}\right)^4 \Phi + GJ\left(\frac{\pi}{L}\right)^2 \Phi - \frac{M_0^2}{EI_y}\Phi = 0
$$

**Step 3 — Solve for critical moment.** Dividing by $\Phi(\pi/L)^2$:

$$
M_{cr}^2 = EI_y\left[GJ\left(\frac{\pi}{L}\right)^2 + EC_w\left(\frac{\pi}{L}\right)^4\right]\cdot\frac{L^2}{\pi^2}
$$

$$
M_{cr} = \frac{\pi}{L}\sqrt{EI_y\left(GJ + \frac{\pi^2 EC_w}{L^2}\right)}
\tag{Prandtl-Michell-Timoshenko}
$$

This is the **exact elastic critical moment for a pin-ended beam under uniform moment**.

---

### 11.2 Rewriting $M_{cr}$ in AISC Form: Derivation of $r_{ts}$ and $F_{cr}$

Divide $M_{cr}$ by the elastic section modulus $S_x$:

$$
F_{cr} = \frac{M_{cr}}{S_x} = \frac{\pi}{L/r_{ts}}\sqrt{\frac{EI_y}{S_x^2}\left(GJ + \frac{\pi^2 EC_w}{L^2}\right)}
$$

Define $r_{ts}$ such that $I_y C_w / S_x^2 = r_{ts}^4/\pi^2$:

$$
r_{ts}^2 = \frac{\sqrt{I_y C_w}}{S_x}
\tag{AISC Eq. F2-7}
$$

With $G/E = 1/(2(1+\nu)) \approx 0.385$ and the normalized torsion $J/(S_x h_o)$, the AISC elastic LTB stress becomes:

$$
F_{cr} = \frac{C_b\pi^2 E}{(L_b/r_{ts})^2}\sqrt{1 + 0.078\frac{Jc}{S_x h_o}\left(\frac{L_b}{r_{ts}}\right)^2}
\tag{AISC 360-22 Eq. F2-4}
$$

The term $0.078 Jc/(S_x h_o)$ is derived by expanding the square-root product:

$$
\sqrt{1 + \frac{GJ}{\pi^2 E C_w / L_b^2}} = \sqrt{1 + \frac{GJ L_b^2}{\pi^2 E C_w}}
$$

Using $G/E \approx 0.385$, $C_w \approx I_y h_o^2/4$ (approximation for I-sections), and $r_{ts}^2 = \sqrt{I_y C_w}/S_x$:

$$
\frac{GJ L_b^2}{\pi^2 E C_w} = \frac{0.385 J L_b^2}{\pi^2 C_w} \approx 0.078\frac{J}{S_x h_o}\left(\frac{L_b}{r_{ts}}\right)^2
$$

confirming the AISC coefficient 0.078 exactly (using $\pi^2 \cdot 0.385/0.385 = \pi^2 \approx 9.87$ and the $I_y h_o^2/4$ approximation).

---

### 11.3 Derivation of $L_p$ and $L_r$

**$L_p$ — plastic zone limit.** The plastic zone ends when inelastic LTB begins. This happens when the inelastic critical moment (accounting for residual stresses and partial yielding) drops below $M_p$. Using the Yura-Galambos-Ravindra (1978) test database, $L_p$ was calibrated as the unbraced length at which the 5th-percentile test strength equals $0.95 M_p$:

$$
L_p = 1.76 r_y\sqrt{E/F_y}
\tag{AISC Eq. F2-5}
$$

**Physical interpretation:** At $L_b = L_p$, the elastic $M_{cr}$ is approximately $1.6 M_p$ (Yura et al. 1978), meaning there is a large margin against elastic buckling and inelastic redistribution can occur without LTB degradation.

**$L_r$ — elastic zone limit.** $L_r$ is defined as the unbraced length at which the elastic critical stress equals the residual-stress-reduced proportional limit, $F_{cr} = 0.7 F_y$:

$$
\frac{C_b=1.0 \cdot \pi^2 E}{(L_r/r_{ts})^2}\sqrt{1 + 0.078\frac{Jc}{S_x h_o}\left(\frac{L_r}{r_{ts}}\right)^2} = 0.7 F_y
$$

Letting $\xi = L_r/r_{ts}$ and squaring:

$$
\xi^4 \left(0.7F_y\right)^2 - \xi^2 \left(\pi^2 E\right)^2 \cdot 0.078\frac{Jc}{S_x h_o} - \left(\pi^2 E\right)^2 = 0
$$

Solving the quadratic in $\xi^2$ and back-substituting yields the AISC Eq. F2-6 exactly, confirming that $L_r$ is the analytically correct transition from the elastic critical formula to the inelastic straight-line interpolation.

---

### 11.4 Load Height Effect and the Modified $C_b$

The standard $C_b$ formula assumes the load is applied at the **shear center**. When load is applied at the **top flange** (e.g., a simply supported beam with uniform load from a slab), the load point is destabilized because the top flange displaces outward during LTB twist, giving the load an additional overturning moment. This reduces $M_{cr}$.

The **load height correction factor** for uniform load at the top flange vs. shear center (Trahair 1993):

$$
M_{cr,top} = M_{cr,shear\ center} \cdot \left[1 - \frac{\pi^2 E I_y e_a^2}{M_{cr,sc} L^2}\right]^{1/2} \leq M_{cr,sc}
$$

where $e_a$ is the height of load application above the shear center. For the common case of top-flange loading on an I-beam ($e_a = d/2 \approx h_o/2$):

$$
M_{cr,top} \approx \frac{M_{cr,sc}}{1 + 2\bar{e}}
$$

where $\bar{e} = e_a/(h_o)$ is the normalized load height. **AISC 360-22 does not explicitly adjust $C_b$ for load height** — it relies on conservative bracing close enough that this effect is small. However, **AISC Design Guide 25** (non-prismatic members) and AASHTO LRFD (girder design) apply load height corrections directly.

---

### 11.5 Monosymmetric Beams and the Wagner Effect

For a **monosymmetric** I-section (different top and bottom flange sizes, as in a plate girder), twisting moves the centroid of the cross-section relative to its mean position, doing work on the normal stresses. This **Wagner effect** (Wagner 1929) modifies the torsion equation:

$$
EC_w \phi'''' - (GJ + P\beta_x) \phi'' + \frac{M_y^2}{EI_y} \phi = 0
$$

where the **monosymmetry parameter** $\beta_x$ is:

$$
\beta_x = \frac{1}{I_x}\int_A y(x^2 + y^2)\,dA - 2y_0
$$

$y_0$ being the distance from the shear center to the centroid. For doubly symmetric sections, $\beta_x = 0$ and the standard equations recover. For a singly symmetric I-section (as in hybrid plate girders with a larger tension flange for fatigue reasons), $\beta_x \neq 0$ and can be either stabilizing ($\beta_x < 0$ when the larger flange is in compression, increasing $M_{cr}$) or destabilizing. AISC accommodates this through the $c$ factor in Eq. F2-4:

$$
c = \frac{h_o}{2}\sqrt{\frac{I_y}{C_w}} \quad (\text{for channels; }c = 1\text{ for doubly symmetric I-shapes})
$$

---

*Created by Structural Engineering Tutor • 2026-03-18 | Upgraded to Graduate level: 2026-03-18*
