# Mohr's Circle: Stress and Strain Transformation

**Subject area:** Mechanics of Materials  
**Design standard / primary reference:** Hibbeler, *Mechanics of Materials*, 10th ed. — Ch. 9 & 10; Beer & Johnston, *Mechanics of Materials*, 7th ed. — Ch. 7  
**Depth level:** Undergraduate — accessible  
**Estimated study time:** 90 minutes

---

## 1. Introduction & Motivation

Imagine you know the stress state at a point from axial, bending, and shear analyses — you have $\sigma_x$, $\sigma_y$, and $\tau_{xy}$ on a particular orientation of the stress element. But does a failure occur on those planes, or on some other inclined plane? For example, concrete fails in tension at a 45° angle in a member loaded in pure shear — not on the horizontal or vertical planes where $\tau$ is highest in the original reference frame.

**Stress transformation** answers the question: *what are the normal and shear stresses on any arbitrarily inclined plane through the same point?* The analytical answer is given by the transformation equations, but the graphical tool **Mohr's circle** (introduced by Otto Mohr in 1882) makes this immediate: just read off coordinates from a circle.

Mohr's circle also reveals two extremely important quantities:
- **Principal stresses** ($\sigma_1$, $\sigma_2$): the maximum and minimum normal stresses at a point, acting on planes with zero shear stress.
- **Maximum in-plane shear stress** ($\tau_{max}$): the highest shear on any inclined plane in the $xy$-plane.

These are the inputs to every failure criterion in Topic 01-I, and they appear throughout steel and concrete design.

---

## 2. Key Concepts & Definitions

| Term | Symbol | Definition |
|------|--------|------------|
| Stress element | — | Infinitesimal square element at a point oriented in some reference frame $(x, y)$ |
| Plane stress | — | State where $\sigma_z = \tau_{xz} = \tau_{yz} = 0$; stress acts in one plane only |
| Stress transformation | — | Computing stresses on a rotated element (angle $\theta$) from known stresses in the original frame |
| Principal stresses | $\sigma_1, \sigma_2$ | Normal stresses on the principal planes (where shear stress vanishes) |
| Principal angle | $\theta_p$ | Angle from $x$-axis to the principal plane; two solutions differ by 90° |
| Maximum in-plane shear stress | $\tau_{max}$ | Maximum shear on any in-plane inclined surface; equal to radius of Mohr's circle |
| Mohr's circle | — | Circle in ($\sigma$, $\tau$) space representing the stress state at a point; radius = $\tau_{max}$ |
| Average (center) stress | $\sigma_{avg}$ | Center of Mohr's circle: $\sigma_{avg} = (\sigma_x + \sigma_y)/2$ |
| Absolute maximum shear stress | $\tau_{abs,max}$ | Considering all three principal stresses (including out-of-plane); critical for failure |

---

## 3. Governing Equations

| Equation | Description | Source |
|----------|-------------|--------|
| $\sigma_{x'} = \frac{\sigma_x + \sigma_y}{2} + \frac{\sigma_x - \sigma_y}{2}\cos 2\theta + \tau_{xy}\sin 2\theta$ | Normal stress on rotated plane | Hibbeler, 10th ed. Eq. 9-1 |
| $\tau_{x'y'} = -\frac{\sigma_x - \sigma_y}{2}\sin 2\theta + \tau_{xy}\cos 2\theta$ | Shear stress on rotated plane | Hibbeler, 10th ed. Eq. 9-2 |
| $\sigma_{1,2} = \frac{\sigma_x + \sigma_y}{2} \pm \sqrt{\left(\frac{\sigma_x - \sigma_y}{2}\right)^2 + \tau_{xy}^2}$ | Principal stresses | Hibbeler, 10th ed. Eq. 9-5 |
| $\tau_{max} = \sqrt{\left(\frac{\sigma_x - \sigma_y}{2}\right)^2 + \tau_{xy}^2}$ | Maximum in-plane shear stress (= radius $R$) | Hibbeler, 10th ed. Eq. 9-7 |
| $\tan 2\theta_p = \frac{2\tau_{xy}}{\sigma_x - \sigma_y}$ | Principal plane angle | Hibbeler, 10th ed. Eq. 9-4 |
| $\sigma_{avg} = \frac{\sigma_x + \sigma_y}{2}$ | Center of Mohr's circle | Hibbeler, 10th ed. §9.2 |

$$
\sigma_{1,2} = \sigma_{avg} \pm R = \frac{\sigma_x + \sigma_y}{2} \pm \sqrt{\left(\frac{\sigma_x - \sigma_y}{2}\right)^2 + \tau_{xy}^2}
$$

$$
\tau_{max} = R = \sqrt{\left(\frac{\sigma_x - \sigma_y}{2}\right)^2 + \tau_{xy}^2}
$$

**Variable legend:**

| Symbol | Description | SI Units | US Customary Units |
|--------|-------------|----------|--------------------|
| $\sigma_x$, $\sigma_y$ | Normal stresses on $x$ and $y$ faces of the element | MPa | ksi |
| $\tau_{xy}$ | Shear stress on the $x$-face in the $y$-direction | MPa | ksi |
| $\theta$ | Angle of rotation from $x$-axis to the new $x'$-axis (CCW positive) | degrees or rad | degrees or rad |
| $\sigma_{x'}$, $\tau_{x'y'}$ | Normal and shear stress on the rotated plane | MPa | ksi |
| $\sigma_1$, $\sigma_2$ | Principal stresses ($\sigma_1 \geq \sigma_2$) | MPa | ksi |
| $\sigma_{avg}$ | Average normal stress $= (\sigma_x + \sigma_y)/2$ | MPa | ksi |
| $R$ | Radius of Mohr's circle = $\tau_{max}$ (in-plane) | MPa | ksi |
| $\theta_p$ | Angle from $x$-axis to principal plane (on element) | degrees | degrees |
| $2\theta_p$ | Corresponding angle on Mohr's circle | degrees | degrees |

---

## 4. Derivation

### 4-1. Stress Transformation Equations

**Step 1:** Consider a stress element with known stresses $(\sigma_x, \sigma_y, \tau_{xy})$ in the $(x, y)$ frame. We wish to find stresses on a plane whose outward normal makes angle $\theta$ with the $x$-axis.

**Step 2:** Isolate a wedge-shaped element with the inclined face. The inclined face has area $dA$, so the $x$-face has area $dA \cos\theta$ and the $y$-face has area $dA \sin\theta$.

**Step 3:** Apply force equilibrium along the $x'$-direction (normal to the inclined face):
$$\sigma_{x'} \cdot dA = (\sigma_x \cdot dA\cos\theta)\cos\theta + (\tau_{xy} \cdot dA\cos\theta)\sin\theta + (\sigma_y \cdot dA\sin\theta)\sin\theta + (\tau_{xy} \cdot dA\sin\theta)\cos\theta$$

**Step 4:** Divide by $dA$ and use double-angle identities ($\cos^2\theta = (1+\cos 2\theta)/2$, etc.):
$$\sigma_{x'} = \frac{\sigma_x + \sigma_y}{2} + \frac{\sigma_x - \sigma_y}{2}\cos 2\theta + \tau_{xy}\sin 2\theta$$

**Step 5:** Similarly, equilibrium along $y'$-direction yields:
$$\tau_{x'y'} = -\frac{\sigma_x - \sigma_y}{2}\sin 2\theta + \tau_{xy}\cos 2\theta$$

### 4-2. Principal Stresses

**Step 6:** Principal stresses occur when $d\sigma_{x'}/d\theta = 0$, i.e., when $\tau_{x'y'} = 0$:
$$\tan 2\theta_p = \frac{2\tau_{xy}}{\sigma_x - \sigma_y}$$

Two solutions: $\theta_p$ and $\theta_p + 90°$ — the two principal planes are always perpendicular.

**Step 7:** Substitute $\theta_p$ back into the $\sigma_{x'}$ equation to get the principal stresses:
$$\sigma_{1,2} = \frac{\sigma_x + \sigma_y}{2} \pm \sqrt{\left(\frac{\sigma_x - \sigma_y}{2}\right)^2 + \tau_{xy}^2}$$

### 4-3. Mohr's Circle Construction

**Step 1:** Plot the point $A = (\sigma_x, \tau_{xy})$ and point $B = (\sigma_y, -\tau_{xy})$ on a $(\sigma, \tau)$ graph.

*Sign convention: positive $\tau_{xy}$ on the $x$-face is plotted **downward** (textbook convention) or **upward** — be consistent with your textbook. Hibbeler uses: positive $\tau$ on $x$-face → downward.*

**Step 2:** The center of the circle is at $C = (\sigma_{avg}, 0) = \left(\frac{\sigma_x+\sigma_y}{2}, 0\right)$.

**Step 3:** The radius is: $R = \overline{CA} = \sqrt{[(\\sigma_x - \sigma_y)/2]^2 + \tau_{xy}^2}$.

**Step 4:** Draw the circle. Its intersections with the $\sigma$-axis give the **principal stresses**:
$$\sigma_1 = \sigma_{avg} + R, \qquad \sigma_2 = \sigma_{avg} - R$$

**Step 5:** The top and bottom of the circle give the **maximum in-plane shear stress**: $\tau_{max} = R$.

**Step 6:** To find stresses on a plane rotated by $\theta$, rotate the reference line by $2\theta$ on the circle (CCW on element → CCW on circle). Read the coordinates of the new point.

### 4-4. Strain Transformation (Strain Rosette Analysis)

The strain transformation equations are analogous to stress transformation with:
- $\varepsilon_x \to \varepsilon_x$, $\varepsilon_y \to \varepsilon_y$, $\tau_{xy}/2 \to \gamma_{xy}/2$

The principal strains $\varepsilon_1$, $\varepsilon_2$ are found from a Mohr's circle for strain. Strain rosettes (electric resistance gauges at 0°, 45°, 90° or 0°, 60°, 120°) measure $\varepsilon_a$, $\varepsilon_b$, $\varepsilon_c$ and allow calculation of $\varepsilon_x$, $\varepsilon_y$, $\gamma_{xy}$ — and hence stresses via Hooke's Law generalized to biaxial state.

For a **45° rosette** ($a = 0°$, $b = 45°$, $c = 90°$):
$$\varepsilon_x = \varepsilon_a, \quad \varepsilon_y = \varepsilon_c, \quad \gamma_{xy} = 2\varepsilon_b - \varepsilon_a - \varepsilon_c$$

---

## 5. Design / Application Procedure

**For stress transformation:**

1. Identify the stress state at the point: $\sigma_x$, $\sigma_y$, $\tau_{xy}$.
2. Compute $\sigma_{avg} = (\sigma_x + \sigma_y)/2$ and $R = \sqrt{[(\sigma_x-\sigma_y)/2]^2 + \tau_{xy}^2}$.
3. Construct Mohr's circle (or use the equations directly).
4. Read off: $\sigma_1 = \sigma_{avg} + R$, $\sigma_2 = \sigma_{avg} - R$, $\tau_{max} = R$.
5. Compute $\theta_p$ from $\tan 2\theta_p = 2\tau_{xy}/(\sigma_x - \sigma_y)$ — verify which root gives $\sigma_1$ or $\sigma_2$.
6. **Absolute maximum shear stress** (3D consideration): If the structure is in plane stress ($\sigma_3 = 0$):
   - If $\sigma_1$ and $\sigma_2$ have **opposite signs**: $\tau_{abs,max} = (\sigma_1 - \sigma_2)/2 = R$.
   - If both **positive**: $\tau_{abs,max} = \sigma_1/2$.
   - If both **negative**: $\tau_{abs,max} = |\sigma_2|/2$.

---

## 6. Worked Example

**Problem:** At a critical point on a steel beam, the stress analysis revealed: $\sigma_x = 80$ MPa (tension), $\sigma_y = -20$ MPa (compression), $\tau_{xy} = 40$ MPa (conventional positive). Determine: (a) the principal stresses, (b) the principal plane angles, (c) the maximum in-plane shear stress and the plane on which it acts, (d) the absolute maximum shear stress.

**Given:**
- $\sigma_x = +80$ MPa
- $\sigma_y = -20$ MPa
- $\tau_{xy} = +40$ MPa

**Solution:**

1. **Center of Mohr's circle:**
$$\sigma_{avg} = \frac{80 + (-20)}{2} = \frac{60}{2} = 30 \text{ MPa}$$

2. **Radius of Mohr's circle:**
$$R = \sqrt{\left(\frac{80-(-20)}{2}\right)^2 + (40)^2} = \sqrt{(50)^2 + (40)^2} = \sqrt{2500 + 1600} = \sqrt{4100} = 64.0 \text{ MPa}$$

3. **Principal stresses:**
$$\sigma_1 = \sigma_{avg} + R = 30 + 64.0 = +94.0 \text{ MPa (tension)}$$
$$\sigma_2 = \sigma_{avg} - R = 30 - 64.0 = -34.0 \text{ MPa (compression)}$$

4. **Principal angles:**
$$\tan 2\theta_p = \frac{2\tau_{xy}}{\sigma_x - \sigma_y} = \frac{2(40)}{80-(-20)} = \frac{80}{100} = 0.800$$
$$2\theta_p = 38.66° \quad \Rightarrow \quad \theta_p = 19.3°$$

The second principal plane is at $\theta_p + 90° = 109.3°$ (or equivalently, $-70.7°$).

*Verification: the plane at 19.3° from the $x$-axis carries $\sigma_1 = 94.0$ MPa (tension).*

5. **Maximum in-plane shear stress:**
$$\tau_{max} = R = 64.0 \text{ MPa}$$

This acts on planes at $45°$ from the principal planes, i.e., at $\theta = 19.3° + 45° = 64.3°$ from the $x$-axis.

The normal stress on those planes: $\sigma = \sigma_{avg} = 30$ MPa (always at center of Mohr's circle on the shear-max plane).

6. **Absolute maximum shear stress** (plane stress: $\sigma_3 = 0$):
$\sigma_1 = +94.0$ MPa and $\sigma_2 = -34.0$ MPa have **opposite signs**, so:
$$\tau_{abs,max} = \frac{\sigma_1 - \sigma_2}{2} = \frac{94.0 - (-34.0)}{2} = \frac{128.0}{2} = 64.0 \text{ MPa}$$

In this case, $\tau_{abs,max} = \tau_{max}$ (in-plane) because $\sigma_1 > 0 > \sigma_2$.

**Result:** $\sigma_1 = 94.0$ MPa, $\sigma_2 = -34.0$ MPa on planes at $\theta_p = 19.3°$. Maximum in-plane shear: 64.0 MPa at $64.3°$ from $x$-axis. Absolute maximum shear: 64.0 MPa.

---

## 7. Common Mistakes & Pitfalls

- **Mistake 1 — Inconsistent shear sign convention:** Hibbeler's Mohr's circle plots positive $\tau_{xy}$ on the $x$-face **pointing downward** (so point $A = (\sigma_x, \tau_{xy})$ is plotted with $+\tau$ below the $\sigma$-axis). Other textbooks use the opposite convention. Pick one and stay consistent — the final principal stresses are the same.
- **Mistake 2 — Confusing the rotation angle:** An element rotation of $\theta$ CCW corresponds to a rotation of $2\theta$ CCW on Mohr's circle. Forgetting the factor of 2 puts the answer on the wrong plane.
- **Mistake 3 — Ignoring the out-of-plane (3D) shear when checking absolute maximum shear:** For plane stress with $\sigma_3 = 0$, if both $\sigma_1$ and $\sigma_2$ are positive, the absolute maximum shear is $\sigma_1/2$, not $(\sigma_1-\sigma_2)/2$. This distinction matters for the von Mises yield criterion.
- **Mistake 4 — Assuming the maximum shear plane also has zero normal stress:** On the maximum shear plane, the normal stress is $\sigma_{avg} = (\sigma_x + \sigma_y)/2$, which is generally not zero.
- **Mistake 5 — Applying 2D Mohr's circle to 3D problems:** In 3D, there are three principal stresses and three Mohr's circles. The in-plane Mohr's circle for plane stress captures only one of them.

---

## 8. Connections to Other Topics

- **Topic 01-G (Combined Loadings):** The stress state $(\sigma, \tau)$ found from combined loadings is the input for Mohr's circle — this is the natural bridge between the two topics.
- **Topic 01-I (Failure Criteria):** All three failure theories (von Mises, Tresca, max-normal-stress) use the principal stresses $\sigma_1$, $\sigma_2$ found via Mohr's circle.
- **Topic 05 (Dynamics) & Topic 08 (FEM):** In FEM post-processing, principal stresses are computed from the stress tensor at each integration point using the same eigenvalue approach as the analytical Mohr's circle.
- **Topic 07 (Concrete Design):** The inclined cracking direction in a reinforced concrete beam is perpendicular to $\sigma_1$ (principal tension), which is calculated from Mohr's circle for the combined bending + shear stress state — this is the physical basis of ACI shear design.
- **Topic 09 (Stability):** Buckling of thin-walled compression elements is linked to the principal compressive stress, which Mohr's circle makes explicit.

---

## 9. Further Reading

| Resource | Where to look |
|----------|--------------|
| Hibbeler, *Mechanics of Materials*, 10th ed. | Chapter 9: Stress Transformation; Chapter 10: Strain Transformation |
| Beer, Johnston & DeWolf, *Mechanics of Materials*, 7th ed. | Chapter 7: Transformations of Stress and Strain |
| Gere & Goodno, *Mechanics of Materials*, 9th ed. | Chapter 7: Analysis of Stress and Strain |

---

## 10. Quick Self-Check

- [ ] I can construct Mohr's circle from $(\sigma_x, \sigma_y, \tau_{xy})$, labeling the center $C$, radius $R$, points $A$ and $B$, and the principal stress points.
- [ ] I can compute $\sigma_1$, $\sigma_2$, and $\tau_{max}$ without drawing the circle (using the formulas directly).
- [ ] I understand the relationship between element rotation angle $\theta$ and Mohr's circle angle $2\theta$.
- [ ] I can determine the absolute maximum shear stress for a plane stress state with two nonzero principal stresses.
- [ ] I can explain why a brittle bar in pure torsion fails along a 45° helix by applying Mohr's circle to the pure-shear stress state on the bar surface.

---

*Created by Structural Engineering Tutor • 2026-03-14*
