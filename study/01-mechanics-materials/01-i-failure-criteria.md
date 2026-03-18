# Failure Criteria: Von Mises, Tresca, and Maximum Normal Stress

**Subject area:** Mechanics of Materials  
**Design standard / primary reference:** Hibbeler, *Mechanics of Materials*, 10th ed. — Ch. 10 (§10.7); Beer & Johnston, *Mechanics of Materials*, 7th ed. — Ch. 7 (§7.5–7.6)  
**Depth level:** Undergraduate — accessible  
**Estimated study time:** 65 minutes

---

## 1. Introduction & Motivation

We now know how to find the principal stresses ($\sigma_1$, $\sigma_2$, $\sigma_3$) at any point in a loaded structure using stress transformation and Mohr's circle. The remaining question is: **will the material fail at this point?** This question is the whole point of stress analysis in engineering design.

Simple tension tests tell us a material yields when $\sigma = \sigma_y$ or fractures when $\sigma = \sigma_u$ — but that is for a **uniaxial** state. Real structural points have biaxial or triaxial stress states. We need **failure criteria** (also called *theories of failure* or *yield criteria*) that predict failure under general multiaxial states based on results from simple uniaxial tests.

Three criteria are covered:
1. **Maximum Normal Stress (Rankine) criterion** — best for brittle materials (cast iron, concrete, ceramics).
2. **Tresca (Maximum Shear Stress) criterion** — conservative, easy to apply to ductile metals.
3. **Von Mises (Distortion Energy) criterion** — most accurate for ductile metals; used in steel design (implicitly, through $0.6F_y$ for shear).

These are not just academic — the allowable shear stress $\tau = 0.6 F_y$ in AISC 360 and the factor $\phi_v = 0.9$ for shear in steel design both trace back to the von Mises criterion.

---

## 2. Key Concepts & Definitions

| Term | Symbol | Definition |
|------|--------|------------|
| Principal stresses | $\sigma_1, \sigma_2, \sigma_3$ | Normal stresses on the three principal planes (no shear); $\sigma_1 \geq \sigma_2 \geq \sigma_3$ |
| Yield stress (uniaxial) | $\sigma_y$ or $F_y$ | The uniaxial tensile stress at which permanent deformation begins |
| Ultimate stress | $\sigma_u$ or $F_u$ | Uniaxial stress at fracture |
| Von Mises stress | $\sigma_{VM}$ or $\bar{\sigma}$ | Effective (equivalent) stress combining principal stresses to predict yielding in ductile materials |
| Hydrostatic stress | $\sigma_h = (\sigma_1+\sigma_2+\sigma_3)/3$ | Component that causes uniform volume change only; does not contribute to yielding |
| Deviatoric stress | — | Stress state minus hydrostatic part; causes distortion → drives yielding |
| Factor of safety | $FS$ | Ratio of failure stress to applied stress; larger = more conservative design |

---

## 3. Governing Equations

| Equation | Description | Source |
|----------|-------------|--------|
| $\sigma_1 \leq \sigma_u$ (tension) and $\sigma_2 \geq -\sigma_{ult,c}$ (compression) | Maximum Normal Stress criterion | Hibbeler, 10th ed. §10.7 |
| $|\sigma_1 - \sigma_2| \leq \sigma_y$ | Tresca criterion (plane stress, $\sigma_3 = 0$) | Hibbeler, 10th ed. §10.7 |
| $\sigma_{VM} = \sqrt{\sigma_1^2 - \sigma_1\sigma_2 + \sigma_2^2} \leq \sigma_y$ | Von Mises criterion (plane stress) | Hibbeler, 10th ed. §10.7 |
| Full 3D von Mises: $\sigma_{VM} = \frac{1}{\sqrt{2}}\sqrt{(\sigma_1-\sigma_2)^2+(\sigma_2-\sigma_3)^2+(\sigma_3-\sigma_1)^2}$ | Von Mises in 3D | Beer & Johnston, 7th ed. §7.6 |
| $\tau_y = 0.5 \, \sigma_y$ | Shear yield stress — Tresca | Derived from Tresca |
| $\tau_y = \sigma_y / \sqrt{3} \approx 0.577 \, \sigma_y$ | Shear yield stress — von Mises | Derived from von Mises |

$$
\sigma_{VM} = \sqrt{\sigma_1^2 - \sigma_1\sigma_2 + \sigma_2^2} \quad \text{(plane stress, } \sigma_3 = 0 \text{)}
$$

$$
|\sigma_1 - \sigma_2| = \sigma_y \quad \text{(Tresca, plane stress)}
$$

**Variable legend:**

| Symbol | Description | SI Units | US Customary Units |
|--------|-------------|----------|--------------------|
| $\sigma_1, \sigma_2$ | In-plane principal stresses ($\sigma_1 > \sigma_2$) | MPa | ksi |
| $\sigma_3$ | Out-of-plane principal stress (= 0 for plane stress) | MPa | ksi |
| $\sigma_y$ | Uniaxial yield stress | MPa | ksi |
| $\sigma_u$ | Ultimate tensile stress (for brittle criterion) | MPa | ksi |
| $\sigma_{VM}$ | Von Mises equivalent stress | MPa | ksi |
| $\tau_y$ | Shear yield stress | MPa | ksi |

---

## 4. Derivation

### 4-1. Maximum Normal Stress (Rankine) Criterion

**Physical basis:** A material fails (fractures or yields) when the maximum principal stress reaches the failure stress in a uniaxial test.

**Criterion (biaxial state):**
$$\text{No failure if:} \quad -\sigma_{ult,c} \leq \sigma_2 \leq \sigma_1 \leq \sigma_{ult,t}$$

For materials where tensile and compressive ultimate stresses are equal (like some brittle metals):
$$|\sigma_1| \leq \sigma_u \quad \text{and} \quad |\sigma_2| \leq \sigma_u$$

**Graphical safe region ($ \sigma_1$-$\sigma_2$ space):** A square centered at the origin, with sides at $\pm \sigma_u$.

**Best for:** Brittle materials (concrete, cast iron, glass, ceramics) where fracture — not yielding — controls.

**Limitation:** Performs poorly for ductile metals under shear — it predicts shear yield at $\tau_y = \sigma_y$, but experiments show $\tau_y \approx 0.5\text{–}0.577 \, \sigma_y$.

### 4-2. Tresca (Maximum Shear Stress) Criterion

**Physical basis:** A ductile material yields when the **maximum shear stress** at a point reaches the shear stress at yield in a uniaxial tension test.

**Derivation:**
- In a uniaxial tension test at yield, the two in-plane principal stresses are $\sigma_1 = \sigma_y$ and $\sigma_2 = 0$.
- Mohr's circle gives: $\tau_{max} = (\sigma_1 - \sigma_2)/2 = \sigma_y/2$.
- Therefore, yielding occurs in a general stress state when: $\tau_{max} = \sigma_y/2$.

**For plane stress** ($\sigma_3 = 0$):
- If $\sigma_1$ and $\sigma_2$ have the **same sign**: $\tau_{max} = \max(|\sigma_1|, |\sigma_2|)/2$.
   Tresca criterion: $\max(|\sigma_1|, |\sigma_2|) \leq \sigma_y$.
- If $\sigma_1$ and $\sigma_2$ have **opposite signs**: $\tau_{max} = |\sigma_1 - \sigma_2|/2$.
   Tresca criterion: $|\sigma_1 - \sigma_2| \leq \sigma_y$.

**Graphical safe region:** A hexagon inscribed in the von Mises ellipse in ($\sigma_1$, $\sigma_2$) space.

**Shear yield stress from Tresca:** In pure shear, $\sigma_1 = -\sigma_2 = \tau$:
$$|\sigma_1 - \sigma_2| = 2\tau = \sigma_y \quad \Rightarrow \quad \tau_y = \frac{\sigma_y}{2} = 0.5 \, \sigma_y$$

**Summary:** Tresca is **conservative** (always on the safe side relative to experiments) and is preferred when safety is paramount or for conservative design.

### 4-3. Von Mises (Distortion Energy) Criterion

**Physical basis:** A ductile material yields when the **distortion strain energy per unit volume** at a point equals the distortion energy at yield in a uniaxial test. The hydrostatic component of stress does NOT cause yielding; only the deviatoric (shape-changing) part does.

**Distortion energy per unit volume:**
$$U_d = \frac{1+\nu}{3E}\left[\frac{(\sigma_1-\sigma_2)^2 + (\sigma_2-\sigma_3)^2 + (\sigma_3-\sigma_1)^2}{2}\right]$$

**Setting equal to uniaxial yield value** (where $\sigma_1 = \sigma_y$, $\sigma_2 = \sigma_3 = 0$):
$$\frac{(\sigma_1-\sigma_2)^2 + (\sigma_2-\sigma_3)^2 + (\sigma_3-\sigma_1)^2}{2} = \sigma_y^2$$

Defining the **von Mises equivalent stress**:
$$\sigma_{VM} = \frac{1}{\sqrt{2}}\sqrt{(\sigma_1-\sigma_2)^2+(\sigma_2-\sigma_3)^2+(\sigma_3-\sigma_1)^2}$$

**Criterion:** $\sigma_{VM} \leq \sigma_y$.

**For plane stress** ($\sigma_3 = 0$):
$$\sigma_{VM} = \sqrt{\sigma_1^2 - \sigma_1\sigma_2 + \sigma_2^2} \leq \sigma_y$$

**Graphical safe region:** An **ellipse** in ($\sigma_1$, $\sigma_2$) space, passing through $(\pm\sigma_y, 0)$ and $(0, \pm\sigma_y)$.

**Shear yield stress from von Mises:** In pure shear, $\sigma_1 = -\sigma_2 = \tau$, $\sigma_3 = 0$:
$$\sigma_{VM} = \sqrt{\tau^2 - \tau(-\tau) + \tau^2} = \sqrt{3\tau^2} = \tau\sqrt{3} = \sigma_y \quad \Rightarrow \quad \tau_y = \frac{\sigma_y}{\sqrt{3}} \approx 0.577 \, \sigma_y$$

**Comparison:**
| Criterion | Shear yield $\tau_y$ | Error vs. experiment |
|-----------|----------------------|----------------------|
| Tresca    | $0.500 \, \sigma_y$  | Conservative (10–15% below experiment) |
| Von Mises | $0.577 \, \sigma_y$  | Excellent agreement with ductile metals |
| Max Normal Stress | $\sigma_y$ | Wrong for shear — non-conservative |

---

## 5. Design / Application Procedure

1. **Find the principal stresses** $\sigma_1$, $\sigma_2$ (and $\sigma_3$ if 3D) at the critical point using Mohr's circle or transformation equations (from Topic 01-H).
2. **Identify the material type:**
   - Ductile metal → use **von Mises** (preferred) or **Tresca** (conservative).
   - Brittle material → use **maximum normal stress**.
3. **Compute the appropriate criterion value:**
   - Von Mises: $\sigma_{VM} = \sqrt{\sigma_1^2 - \sigma_1\sigma_2 + \sigma_2^2}$.
   - Tresca: $|\sigma_1 - \sigma_2|$ (when $\sigma_1$ and $\sigma_2$ have opposite signs).
   - Max Normal: $\sigma_1$ and $\sigma_2$.
4. **Compare to material strength:**
   - $\sigma_{VM} \leq \sigma_y/FS$ (von Mises) or $|\sigma_1 - \sigma_2| \leq \sigma_y/FS$ (Tresca).
   - $\sigma_1 \leq \sigma_u/FS$ and $|\sigma_2| \leq \sigma_{ult,c}/FS$ (max normal stress).
5. **If the check fails:** Increase section size, use a stronger material, reduce loads, or redesign the geometry.

---

## 6. Worked Example

**Problem:** At a critical point in a steel shaft ($\sigma_y = 250$ MPa), the stress state is an in-plane biaxial stress: $\sigma_x = +120$ MPa (bending, tension), $\sigma_y = 0$, $\tau_{xy} = 70$ MPa (torsion). (a) Find the principal stresses. (b) Apply the Von Mises criterion. (c) Apply the Tresca criterion. (d) Determine if the material yields, and compute the factor of safety for each criterion.

**Given:**
- $\sigma_x = 120$ MPa, $\sigma_y = 0$, $\tau_{xy} = 70$ MPa
- $\sigma_y = 250$ MPa (material yield)

**Solution:**

1. **Mohr's circle / principal stresses:**
$$\sigma_{avg} = \frac{120 + 0}{2} = 60 \text{ MPa}$$
$$R = \sqrt{\left(\frac{120-0}{2}\right)^2 + 70^2} = \sqrt{60^2 + 70^2} = \sqrt{3600 + 4900} = \sqrt{8500} = 92.2 \text{ MPa}$$
$$\sigma_1 = 60 + 92.2 = +152.2 \text{ MPa}$$
$$\sigma_2 = 60 - 92.2 = -32.2 \text{ MPa}$$

2. **Von Mises criterion:**
$$\sigma_{VM} = \sqrt{\sigma_1^2 - \sigma_1\sigma_2 + \sigma_2^2} = \sqrt{(152.2)^2 - (152.2)(-32.2) + (-32.2)^2}$$
$$= \sqrt{23{,}165 + 4{,}901 + 1{,}037} = \sqrt{29{,}103} = 170.6 \text{ MPa}$$
$$FS_{VM} = \frac{\sigma_y}{\sigma_{VM}} = \frac{250}{170.6} = 1.47 \quad \checkmark \text{ (no yield)}$$

3. **Tresca criterion:**
$\sigma_1 = +152.2$ MPa and $\sigma_2 = -32.2$ MPa have **opposite signs**:
$$|\sigma_1 - \sigma_2| = |152.2 - (-32.2)| = 184.4 \text{ MPa}$$
$$FS_{Tresca} = \frac{\sigma_y}{|\sigma_1 - \sigma_2|} = \frac{250}{184.4} = 1.36 \quad \checkmark \text{ (no yield, but more conservative)}$$

4. **Comparison:**
   - Von Mises: FS = 1.47. No yielding. (Closer to experimental reality.)
   - Tresca: FS = 1.36. No yielding. (More conservative by 7.7%.)

**Result:** No yielding by either criterion. Tresca gives a lower (more conservative) factor of safety. The material has a safety margin of 36–47% against yielding under this combined loading.

---

## 7. Common Mistakes & Pitfalls

- **Mistake 1 — Using von Mises for brittle materials:** Von Mises and Tresca are **only applicable to ductile materials** (metals that yield before fracturing). For brittle materials (concrete, ceramics, cast iron), use the Maximum Normal Stress criterion or the Mohr-Coulomb criterion.
- **Mistake 2 — Forgetting the out-of-plane principal stress in 3D:** In plane stress, $\sigma_3 = 0$, but you still need to check if the absolute maximum shear comes from the out-of-plane Mohr circle. For both Tresca and von Mises, include $\sigma_3 = 0$ if the two in-plane stresses have the same sign.
- **Mistake 3 — Comparing $\sigma_{VM}$ to $\sigma_u$ instead of $\sigma_y$:** Von Mises predicts **yielding**. For fracture, the criterion changes. Always match the criterion to the appropriate material property.
- **Mistake 4 — Computing $\sigma_{VM}$ from $\sigma_x$, $\sigma_y$, $\tau_{xy}$ directly without converting to principal stresses first:** You can do this using the formula $\sigma_{VM} = \sqrt{\sigma_x^2 - \sigma_x\sigma_y + \sigma_y^2 + 3\tau_{xy}^2}$ (valid for plane stress in the original frame), but be careful to use the correct form.
- **Mistake 5 — Treating the Tresca yield hexagon incorrectly:** When both $\sigma_1$ and $\sigma_2$ have the **same sign**, the Tresca criterion is $\max(|\sigma_1|, |\sigma_2|) \leq \sigma_y$ (not $|\sigma_1 - \sigma_2| \leq \sigma_y$, which would be less conservative).

---

## 8. Connections to Other Topics

- **Topic 01-H (Mohr's Circle):** Mohr's circle produces the principal stresses $\sigma_1$, $\sigma_2$ that are the input to every failure criterion.
- **Topic 01-G (Combined Loadings):** The stress state from combined loadings is first found (Topic 01-G), then transformed (Topic 01-H), then checked against a failure criterion here.
- **Topic 06 (Steel Design, AISC 360):** AISC uses $\tau_y = 0.6 F_y$ for shear yielding (close to the von Mises value of $0.577 F_y$, rounded up). The plastic mechanism and $R_y$ factors implicitly use distortion energy concepts.
- **Topic 07 (Concrete Design, ACI 318):** Concrete is a brittle material whose tensile strength is much lower than compressive strength — the maximum normal stress idea governs tensile cracking. ACI shear design limits diagonal tension using this concept.
- **Topic 08 (FEM):** In FEM post-processing, the von Mises stress $\sigma_{VM}$ is the most common result plotted in color contour maps — it immediately tells the engineer where yield is approached.

---

## 9. Further Reading

| Resource | Where to look |
|----------|--------------|
| Hibbeler, *Mechanics of Materials*, 10th ed. | §10.7: Theories of Failure |
| Beer, Johnston & DeWolf, *Mechanics of Materials*, 7th ed. | §7.5–7.6: Yield Criteria for Ductile Materials; Fracture Criteria for Brittle Materials |
| Gere & Goodno, *Mechanics of Materials*, 9th ed. | Chapter 7: Analysis of Stress and Strain (§7.6–7.7) |
| Lubliner, *Plasticity Theory* (free PDF) | Chapter 1: Phenomenological aspects of plastic deformation (graduate) |

---

## 10. Quick Self-Check

- [ ] I can state the Von Mises criterion for plane stress and explain what physical phenomenon it is based on.
- [ ] I can state the Tresca criterion, handle both cases (same-sign and opposite-sign principal stresses), and explain why it is conservative relative to von Mises.
- [ ] I know which criterion applies to ductile vs. brittle materials.
- [ ] I can derive $\tau_y = \sigma_y/2$ (Tresca) and $\tau_y = \sigma_y/\sqrt{3}$ (von Mises) for pure shear.
- [ ] Given $(\sigma_x, \sigma_y, \tau_{xy})$ at a point, I can complete the full analysis: find principal stresses via Mohr's circle, apply both criteria, and compute the factor of safety.

---

*Created by Structural Engineering Tutor • 2026-03-14*
