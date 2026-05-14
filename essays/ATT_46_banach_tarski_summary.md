# ATT_46 — The Banach-Tarski Paradox: A Geofinitist Reinterpretation

**Essay ID:** ATT_46  
**Title:** The Banach-Tarski Paradox: A Geofinitist Reinterpretation  
**College:** College of Attralucian Studies  
**Series:** Classical Problems Through the Geofinite Lens (Essay 8 of series)  
**Lesson:** ATT_46  
**Pillars (primary → secondary):** P2, P5 (primary); P4, P1, P3 (secondary)  
**Status:** Stable  
**Last updated:** 2026-05-09

---

## Overview

The Banach-Tarski theorem (1924) is among the most striking results in classical mathematics: a solid ball can be decomposed into finitely many pieces and reassembled, using only rigid motions, into two balls each identical in size to the original. This appears to violate conservation of volume — something must have gone wrong. This essay locates exactly what: the theorem relies on constructions that are inadmissible under Geofinitist constraints. Applied Geofinitism reframes the result not as a violation of physics but as the signature of a construction that has exceeded admissible limits: non-measurable sets, infinite precision, and unbounded decomposition are the sources of the apparent paradox. Within any finite-resolution, measure-preserving regime, volume is conserved and the paradox cannot arise.

---

## Classical Theorem

Given a solid ball B ⊂ ℝ³, there exists a finite partition:

$$B = S_1 \cup S_2 \cup \cdots \cup S_k \quad (\text{pairwise disjoint})$$

and rigid motions T₁, …, T_k (rotations and translations) such that:

$$\bigcup_{i=1}^{k} T_i(S_i) = B_1 \cup B_2$$

where B₁ and B₂ are each a copy of B (same size and shape). The ball has been "doubled" using only rigid motions — no stretching, no adding material.

The theorem depends on:
- **Axiom of Choice:** to construct non-measurable sets S_i
- **Non-measurability:** the sets S_i do not have well-defined Lebesgue measure
- **Non-amenability of SO(3):** the rotation group in ℝ³ contains a free group on two generators, which is the algebraic engine of the paradox
- **Infinite precision:** the decomposition is an exact point-set construction

---

## Four Sources of the Paradox

| Source | Classical commitment | Geofinite replacement |
|--------|---------------------|----------------------|
| **Non-measurable sets** | Arbitrary subsets of ℝ³ are permissible decomposition pieces | All pieces must have well-defined, positive measure: vol(S_i) ≥ δV > 0 |
| **Exact rigid motions on point sets** | T_i acts on arbitrary point sets with infinite precision | Rigid motions are admissible only on measurable, bounded-error pieces |
| **Infinite precision** | Points are identified exactly; no resolution limit | Resolution η > 0 declared; objects are voxel bodies at scale η |
| **No scale or resolution constraints** | Decomposition is resolution-independent | Piece count bounded: k ≤ N = V(B)/δV; all operations carry declared error |

All four must hold simultaneously for the paradox to arise. Geofinitism removes each one.

---

## Geofinitist Reformulation

### Admissibility Constraints on Decomposition

Replace arbitrary point-set decomposition with **admissible decomposition**:

$$\text{vol}(S_i) \geq \delta V > 0, \qquad k \leq N = \frac{V(B)}{\delta V}$$

Every piece must have positive measure (no non-measurable fragments); the number of pieces is bounded by the volume of B divided by the minimum piece size. The reassembled body:

$$U = \bigcup_{i=1}^{k} T_i(S_i), \qquad \text{vol}(U) \approx V(B) \pm \sigma$$

where σ is the accumulated error from bounded-precision rigid motions. Volume is approximately conserved — within declared tolerance.

### Voxel Body Representation

At resolution η > 0, the ball B is represented as:

$$S_\eta = \bigcup_{j=1}^{N(\eta)} V_j$$

where {V_j} are non-overlapping voxels (cubes of side η), and N(η) is the finite voxel count. This is the **Geofinite body** at scale η — a finite construction with declared resolution.

### Measured Volume

Volume is not an exact real-valued function but a **Measured Number**:

$$\mu_{\mathbb{M}}(A) = \left(\sum_{V_j \subseteq A} \eta^3,\; \varepsilon_\mu(A)\right)$$

where ε_μ(A) is the boundary error (voxels that partially overlap the boundary of A). This is the Pillar 2 reformulation: all measurements carry provenance and uncertainty.

### Finite Additivity (Measured)

$$\mu_{\mathbb{M}}(A \cup B) \approx \mu_{\mathbb{M}}(A) + \mu_{\mathbb{M}}(B) \quad \text{(when } A \cap B = \emptyset\text{)}$$

Exact additivity holds only in the limit η → 0. For finite η, boundary errors accumulate and the equality is approximate.

### Admissible Rigid Motions

Rigid motions T_i are **admissible** if they preserve measured volume within tolerance:

$$\mu_{\mathbb{M}}(T_i A) \approx \mu_{\mathbb{M}}(A) \quad \text{for all admissible pieces } A$$

A rigid motion applied to a non-measurable set is inadmissible — no measured-volume output is defined.

### Conservation Theorem (Geofinite)

For any admissible decomposition with admissible rigid motions:

$$\mu_{\mathbb{M}}(U) \approx \mu_{\mathbb{M}}(S_\eta)$$

**No admissible decomposition yields** μ_M(U) ≈ 2·μ_M(S_η). Volume doubling is constructionally impossible within admissible bounds. The Banach-Tarski construction is not realised — it is inadmissible before the doubling claim can be evaluated.

---

## All Five Pillars Applied

### Pillar 1 — Geometric Container Space

**Classical:** ℝ³ is an exact, continuous, infinite-resolution space. Objects are arbitrary point sets.

**Geofinite:** Physical space is modelled at finite resolution η. Objects are voxel bodies S_η — finite collections of cubes. The "container" for all geometric operations is the finite-resolution lattice, not the continuum. Geometric operations are defined on the voxel representation, not on abstract point sets.

### Pillar 2 — Measured Decomposition (primary)

**Classical:** Volume is an exact real number. Decomposition pieces either have measure or they don't — non-measurable pieces are permissible as set-theoretic objects.

**Geofinite:** Volume is μ_M(A) = (Σ η³, ε_μ(A)) — a Measured Number with declared uncertainty. Every piece must have well-defined measured volume. The measured volume of the reassembled body is computable and conserved within tolerance. The Banach-Tarski pieces have no measured volume — they are inadmissible inputs.

### Pillar 3 — Scale-Dependent Structure (Dynamic Flow)

**Classical:** The decomposition is scale-independent — it works at every scale simultaneously (the sets are non-measurable at all scales).

**Geofinite:** Structure is scale-dependent. At voxel resolution η, the ball has N(η) = V(B)/η³ pieces, finite boundary, and measurable volume. As η decreases, finer structure is revealed but the volume remains conserved at each scale. The Banach-Tarski decomposition cannot be realised at any finite η — it is a property of the η → 0 limit, which is inadmissible.

### Pillar 4 — Admissibility / Useful Fiction (secondary primary)

**Classical:** Non-measurable sets exist (given AC). The Banach-Tarski theorem is a theorem of ZFC.

**Geofinite:** Non-measurable sets are a **useful fiction** — powerful as mathematical objects, but inadmissible as physical decompositions. The Axiom of Choice is admitted for abstract mathematics; its consequences are contextually valid within set theory and inadmissible when applied to physical constructions requiring measurable, finite-resource outputs. Banach-Tarski is a theorem about the useful fiction of non-measurable sets; it is not a theorem about admissible physical decompositions.

### Pillar 5 — Finite Realizability (primary)

**Classical:** The decomposition is exact — no declared bounds on piece count, precision, or measure.

**Geofinite:** All constructions carry declared bounds: vol(S_i) ≥ δV; k ≤ N; rigid motions produce bounded-error outputs. These are the finite realizability constraints. Any construction exceeding them is inadmissible. The Banach-Tarski decomposition requires: k pieces with no lower bound on size, non-measurable sets (violating vol(S_i) ≥ δV), and rigid motions on non-measurable inputs (inadmissible). All three constraints are violated simultaneously.

---

## The Inverted Collapse Note

Essays ATT_39–ATT_44 all end with collapse notes of the form: "as bounds and uncertainties vanish → classical result recovered." The Geofinite framework subsumes the classical theory in the limit.

Essay 46's collapse note has the **inverse structure** (matching Essay 45 — Russell's Paradox):

> Removing the measurability constraint and the finite resolution bound restores the classical paradox. As δV → 0 and η → 0, admissible decompositions become arbitrary point-set decompositions, and the Banach-Tarski construction becomes available.

This is the signature of a paradox that arises *specifically from* the unbounded/non-measurable limit — not from any finite regime. Geofinitism does not inhabit the limit η → 0 or δV → 0; it does not encounter the paradox.

**What this reveals:** The Banach-Tarski theorem is not a flaw in mathematics — it is precise evidence that non-measurable sets, once admitted as physical decomposition pieces, violate conservation laws. The paradox is inadmissible, not inconsistent. It signals the boundary of admissible geometric construction, exactly as Russell's paradox signals the boundary of admissible set-theoretic construction.

---

## Comparison with Classical Responses

| Response | Mechanism | Limitation |
|----------|-----------|-----------|
| **"It's not physical"** | BT is a pure mathematical result; non-measurable sets don't exist in physics | Lacks a formal criterion for what makes it non-physical |
| **Reject AC** | Some constructive/intuitionistic frameworks deny the Axiom of Choice | Removes powerful tools used throughout mathematics |
| **Geofinitism** | Non-measurable sets are inadmissible constructions; admissible decompositions conserve measured volume | Preserves AC for abstract use; provides a formal admissibility criterion |

The Geofinite approach preserves the classical theorem as a theorem within abstract set theory (a useful fiction), while formally excluding its application to admissible physical or computational constructions.

---

## Formal Core (Tcolorbox Summary)

**Context:** Banach-Tarski paradox arises from non-measurable decomposition and exact rigid motions. We model geometric bodies as finite voxel representations with measured volume.

**Voxel body:** S_η = ∪_{j=1}^{N(η)} V_j (resolution η > 0)

**Measured volume:** μ_M(A) = (Σ_{V_j ⊆ A} η³, ε_μ(A))

**Finite additivity:** μ_M(A ∪ B) ≈ μ_M(A) + μ_M(B)

**Admissible motions:** μ_M(T_i A) ≈ μ_M(A)

**Conservation:** μ_M(U) ≈ μ_M(S_η)

**Result:** No admissible decomposition yields μ_M(U) ≈ 2·μ_M(S_η)

**Collapse note:** Removing measurability and finite resolution restores the classical paradox.

**Interpretation:** Banach-Tarski is a boundary violation — a construction inadmissible within finite, measurable geometry.

---

## Re-style Checklist (LaTeX)

- [ ] **Double `\maketitle`** (lines 94 and 151) — second call redundant; remove
- [ ] **`\textbf\textbf{}`** (line 133, secondary title page) — nested bold command; correct to `\textbf{}`
- [ ] **Plain `\begin{tcolorbox}`** used in Formal Core (consistent with Essays 42–45; `axiomline` defined in preamble but unused — decision needed on series standardisation)
- [ ] **No `\chapter*`** — essay uses `\section*` directly (consistent with Essays 39–45; verify book-format rendering against template)
- [ ] **Running header:** "The Banach-Tarski Paradox" ✓ (correct)
- [ ] **Secondary title page:** "The Banach-Tarski Paradox: A Geofinitist Reinterpretation" ✓ (correct)
- [ ] **Body section title:** "The Banach-Tarski Paradox: A Geofinitist Reinterpretation" ✓ (correct — no template carryover error)

---

## Cross-References

| Essay / Lesson | Connection |
|----------------|-----------|
| ATT_28 | Commitment, Consensus, Admissibility: admissibility criterion (vol ≥ δV; k ≤ N; bounded-error motions) is ATT_28's framework applied to geometric decomposition |
| ATT_45 | Russell's Paradox — parallel inverted collapse note; both paradoxes arise from removing finiteness/measurability constraints; both are reclassified as inadmissible constructions rather than contradictions |
| ATT_08 | Geofinitism — Measurement-First: μ_M(A) = (Σ η³, ε_μ) inherits M = (v, ε, P); every measured volume is a Measured Number with provenance |
| ATT_23 | The Generon: voxel body S_η = ∪V_j is a finite generative construction (like Gen(θ,B)); the Banach-Tarski decomposition requires a Generon that cannot produce measurable outputs — inadmissible |
| ATT_39 | P vs NP (first in series): series pattern — each essay applies Geofinite Five Pillars to a classical problem; BT is the eighth, completing the "paradox pair" with ATT_45 |
| ATT_10 | Geometry in Geofinitism — The Alphon Lattice: voxel representation S_η as an Alphon-level lattice structure; finite-resolution geometry as the Alphon container for physical objects |

---

*Kevin R. Haylett — School of Geofinitism*  
*Simul Pariter.*
