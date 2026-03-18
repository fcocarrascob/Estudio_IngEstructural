# Mechanics of Materials — Subject Overview

**Folder:** `study/01-mechanics-materials/`  
**Total subtopics:** 10 (A through J)  
**Prerequisites:** Statics (equilibrium, free-body diagrams), Calculus I & II

---

## What This Subject Is About

Mechanics of Materials (also called *Strength of Materials* or *Mechanics of Deformable Bodies*) extends rigid-body statics by asking: **what happens *inside* a structural member when loads are applied?** Instead of treating members as infinitely stiff, we model the internal stresses and deformations that determine whether a component will **yield**, **fracture**, or **deflect excessively** under load.

This is the foundational course for all structural, mechanical, and civil engineering design. Every beam, column, shaft, and pressure vessel you will ever design traces back to the concepts here.

---

## Topic Index

| File | Subtopic | Key Concepts |
|------|----------|--------------|
| [01-a-stress-strain-axial-shear.md](01-a-stress-strain-axial-shear.md) | A. Stress & Strain (axial, shear) | σ, τ, ε, γ, Hooke's Law, Poisson's ratio |
| [01-b-axial-deformation-indeterminate.md](01-b-axial-deformation-indeterminate.md) | B. Axial Deformation & Indeterminate Members | δ = PL/AE, compatibility, thermal effects |
| [01-c-torsion-circular-sections.md](01-c-torsion-circular-sections.md) | C. Torsion of Circular Sections | τ = Tc/J, φ = TL/GJ, power transmission |
| [01-d-pure-bending-normal-stresses.md](01-d-pure-bending-normal-stresses.md) | D. Pure Bending: Normal Stresses | σ = −My/I, neutral axis, section modulus |
| [01-e-transverse-loading-shear-stresses.md](01-e-transverse-loading-shear-stresses.md) | E. Shear Stresses in Beams | τ = VQ/Ib, shear flow, built-up sections |
| [01-f-beam-deflections.md](01-f-beam-deflections.md) | F. Beam Deflections | Double integration, moment-area, superposition |
| [01-g-combined-loadings.md](01-g-combined-loadings.md) | G. Combined Loadings | Stress superposition, thin-walled pressure vessels |
| [01-h-mohrs-circle.md](01-h-mohrs-circle.md) | H. Mohr's Circle | Stress/strain transformation, principal stresses |
| [01-i-failure-criteria.md](01-i-failure-criteria.md) | I. Failure Criteria | Von Mises, Tresca, max-normal-stress |
| [01-j-fatigue-stress-concentration.md](01-j-fatigue-stress-concentration.md) | J. Fatigue & Stress Concentration | S-N curves, Kt, Goodman diagram |

---

## Recommended Study Order

Study the topics in order A → J. Each builds on the previous:

```
A (stress/strain basics)
  └─→ B (extend to deformation)
        └─→ C (torsion — a new type of stress/deformation)
              └─→ D (bending stress)
                    └─→ E (shear stress in beams)
                          └─→ F (deflections — integration of moment)
                                └─→ G (combine A–F into real problems)
                                      └─→ H (transform stress states)
                                            └─→ I (use transformed stresses for failure)
                                                  └─→ J (cyclic loading — fatigue)
```

---

## Key Textbook References

| Textbook | Notes |
|----------|-------|
| Hibbeler, R.C. — *Mechanics of Materials*, 10th ed. (Pearson, 2017) | Standard undergraduate reference; clear examples |
| Beer, Johnston & DeWolf — *Mechanics of Materials*, 7th ed. (McGraw-Hill, 2015) | Alternative; rigorous derivations |
| Gere & Goodno — *Mechanics of Materials*, 9th ed. (Cengage, 2018) | Good treatment of energy methods |

---

*Structural Engineering Tutor — Subject overview created 2026-03-14*
