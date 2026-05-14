# ATT_46 — The Banach-Tarski Paradox: A Geofinitist Reinterpretation

**College:** College of Attralucian Studies  
**Lesson ID:** ATT_46  
**Source essay:** ATT_46 — *The Banach-Tarski Paradox: A Geofinitist Reinterpretation*  
**Level:** Advanced  
**Prerequisites:** ATT_08; ATT_28; ATT_45 (recommended); background in real analysis and measure theory (Lebesgue measure, σ-algebras, the Axiom of Choice)  
**Next lesson:** ATT_47 (TBD — next in classical-problems series)

---

## Learning Outcomes

By the end of this lesson you will be able to:

1. State the Banach-Tarski theorem and identify the four sources of the paradox
2. Explain why the theorem depends on non-measurable sets and why this is the key admissibility failure
3. Define the voxel body S_η and explain what resolution η represents
4. Write μ_M(A) = (Σ η³, ε_μ(A)) and explain what ε_μ captures
5. State the finite additivity property for measured volume and where it fails
6. Define admissible rigid motions and explain why they preserve μ_M
7. State the Geofinite conservation theorem and explain why volume doubling is inadmissible
8. Explain the inverted collapse note and compare it with Essays 45 and 39–44
9. Distinguish the Geofinite response to Banach-Tarski from "it's not physical" and from rejecting AC
10. Apply all five Pillars to the Banach-Tarski paradox

---

## 1. The Classical Theorem

In 1924, Stefan Banach and Alfred Tarski proved that a solid ball in ℝ³ can be decomposed into finitely many pieces and reassembled — using only rigid motions (rotations and translations) — into two balls each identical in size to the original.

$$B = S_1 \cup S_2 \cup \cdots \cup S_k \quad \text{(pairwise disjoint)}$$

$$\bigcup_{i=1}^{k} T_i(S_i) = B_1 \cup B_2 \quad \text{where } B_1, B_2 \cong B$$

No material is added. No stretching is involved. Yet the volume appears to double. This is the Banach-Tarski paradox.

**Why it works classically:**

The proof exploits three simultaneous features of abstract mathematics:

1. The **Axiom of Choice** allows selection of one element from each set in an uncountable family — the pieces S_i are constructed using AC and cannot be built explicitly
2. The resulting pieces are **non-measurable** — they have no well-defined Lebesgue measure; the statement "they have zero volume" or "they have positive volume" is undefined
3. **SO(3) is non-amenable** — the rotation group in three dimensions contains a free group on two generators (the Hausdorff paradox, 1914), which is the algebraic engine that makes the doubling possible

---

## 2. Four Sources of the Paradox

The Banach-Tarski theorem requires four simultaneous conditions. Removing any one prevents the paradox:

| Source | Classical commitment | Geofinite replacement |
|--------|---------------------|----------------------|
| **Non-measurable sets** | S_i need not have defined Lebesgue measure | vol(S_i) ≥ δV > 0: all pieces must have positive measured volume |
| **Exact rigid motions on point sets** | T_i acts on arbitrary point sets | Admissible motions: T_i acts on measurable, bounded-error pieces |
| **Infinite precision** | Points identified exactly; no resolution limit | Finite resolution η > 0 declared; objects are voxel bodies |
| **No scale/resolution constraints** | Decomposition is resolution-independent | Piece count bounded: k ≤ N = V(B)/δV |

---

## 3. All Five Pillars Applied

### Pillar 1 — Geometric Container Space

**Classical:** ℝ³ is an exact, continuous, infinite-resolution space. Objects are arbitrary point sets — subsets of ℝ³ with no declared precision.

**Geofinite:** Geometric space is modelled at finite resolution η > 0. Objects are **voxel bodies** — finite collections of cubes of side η. The geometric container is the finite-resolution lattice, not the continuum. Every geometric operation is defined on the voxel representation, not on abstract point sets.

This is the first constraint: objects must be representable at the declared resolution. Non-measurable sets are not representable at any finite resolution — they are outside the container.

### Pillar 2 — Measured Volume (primary)

**Classical:** Volume is an exact real number, computable for measurable sets and undefined for non-measurable sets. The Banach-Tarski pieces are non-measurable — they fall outside the domain of Lebesgue measure entirely.

**Geofinite:** Volume is a **Measured Number**:

$$\mu_{\mathbb{M}}(A) = \left(\sum_{V_j \subseteq A} \eta^3,\; \varepsilon_\mu(A)\right)$$

Every piece must have a computable measured volume. This immediately excludes non-measurable sets: they cannot be assigned a measured volume, so they are inadmissible as decomposition pieces.

The measured volume of the reassembled body is computable, carries declared uncertainty, and is conserved within tolerance.

### Pillar 3 — Scale-Dependent Structure (Dynamic Flow)

**Classical:** The Banach-Tarski decomposition is scale-independent — non-measurable sets are non-measurable at every resolution.

**Geofinite:** Structure is **scale-dependent**. At resolution η, the ball has N(η) = V(B)/η³ voxels. As η decreases, finer structure is captured. But at every finite η, volume is well-defined and conserved. The Banach-Tarski decomposition cannot be realised at any finite η — it is a property of the η → 0 limit, which exceeds the admissible domain.

This is the layered structure: voxels → measurable regions → voxel bodies → composed objects. Inadmissibility is detected at the first layer — non-measurable sets cannot enter the construction at all.

### Pillar 4 — Admissibility / Useful Fiction (secondary)

**Classical:** Non-measurable sets exist as abstract mathematical objects (given AC). The Banach-Tarski theorem is provable in ZFC — it is a genuine theorem of abstract mathematics.

**Geofinite:** Non-measurable sets are a **useful fiction**. Within abstract set theory they are well-defined; as decomposition pieces for physical or computational constructions they are inadmissible. The Axiom of Choice is contextually valid for abstract mathematics and inadmissible when its consequences would require non-measurable outputs.

This parallels the treatment of naive comprehension in ATT_45: the useful fiction (unrestricted comprehension / non-measurable sets) is powerful and internally consistent, but it generates inadmissible objects when applied outside its valid domain.

### Pillar 5 — Finite Realizability (primary)

**Classical:** The decomposition has no declared bounds on piece count, precision, or measure. Pieces S_i have no size lower bound.

**Geofinite:** All constructions carry declared bounds:
- vol(S_i) ≥ δV > 0 (pieces have positive minimum size)
- k ≤ N = V(B)/δV (piece count is bounded)
- Rigid motions produce outputs within declared precision

Any construction violating these bounds is **inadmissible**. The Banach-Tarski decomposition violates all three:
- k pieces with no size lower bound (δV → 0)
- Non-measurable sets (vol(S_i) undefined — violates vol(S_i) ≥ δV)
- Rigid motions on non-measurable inputs (no well-defined output)

---

## 4. The Voxel Body

At resolution η > 0, the ball B is represented as:

$$S_\eta = \bigcup_{j=1}^{N(\eta)} V_j$$

where {V_j} are non-overlapping cubes (voxels) of side η, and N(η) is the total count. Properties:

- **Finite:** N(η) = O(V(B)/η³) — a finite integer
- **Constructible:** the set {V_j} can be enumerated explicitly
- **Resolution-declared:** η is a committed parameter; S_η is the canonical representation of B at scale η
- **Boundary error:** voxels near the surface of B may partially protrude; this contributes to ε_μ(S_η)

The voxel body is the Geofinite analogue of a continuous solid. As η → 0, S_η → B in the limit. Geofinitism operates at finite η — it does not take this limit.

**Note for quantum/physics context:** the resolution η is not claimed to be the Planck length or any physical discreteness. It is a declared computational parameter — the granularity at which the construction is evaluated. Different applications declare different η.

---

## 5. Measured Volume

$$\mu_{\mathbb{M}}(A) = \left(\sum_{V_j \subseteq A} \eta^3,\; \varepsilon_\mu(A)\right)$$

**Components:**
- **Value:** Σ η³ = (number of voxels fully inside A) × (volume of one voxel)
- **Uncertainty:** ε_μ(A) = (number of boundary voxels) × η³ — the boundary error from partial coverage

**Properties:**
- μ_M(A) ≥ 0 always
- μ_M(∅) = (0, 0)
- For full interior A (no boundary voxels): ε_μ(A) = 0
- For A with complex boundary: ε_μ(A) grows with surface area

**Finite additivity:**

$$\mu_{\mathbb{M}}(A \cup B) \approx \mu_{\mathbb{M}}(A) + \mu_{\mathbb{M}}(B) \quad \text{when } A \cap B = \emptyset$$

Exact equality holds when A and B have no shared boundary voxels. In general:

$$\mu_{\mathbb{M}}(A \cup B) = \mu_{\mathbb{M}}(A) + \mu_{\mathbb{M}}(B) \pm \varepsilon_{\text{boundary}}$$

Classical Lebesgue measure is exactly additive (for measurable sets). Geofinite measured volume is approximately additive, with error bounded by the boundary complexity. This is the appropriate statement for finite-resolution geometry.

---

## 6. Admissible Rigid Motions

A rigid motion T (rotation or translation) is **admissible** if it maps measurable pieces to measurable pieces and preserves measured volume within tolerance:

$$\mu_{\mathbb{M}}(TA) \approx \mu_{\mathbb{M}}(A)$$

**Why this fails for non-measurable sets:** T applied to a non-measurable set A produces a set T(A) whose measurability is also undefined. There is no output μ_M(T(A)) — the motion is inadmissible as an operation on A.

**Why it holds for voxel pieces:** T_i(V_j) is a rotated/translated cube. At finite resolution, the image is re-voxelised — the boundary changes but the total volume is preserved within ε_T (the precision of T_i). For admissible T_i with bounded precision, μ_M(T_i A) ≈ μ_M(A) ± ε_T.

**Admissibility criterion for a decomposition-and-reassembly:** the operation:

$$\{S_i\} \xrightarrow{T_i} \{T_i(S_i)\} \to U = \bigcup_i T_i(S_i)$$

is admissible if and only if each S_i has vol(S_i) ≥ δV, k ≤ N, each T_i is admissible, and boundary errors accumulate within declared tolerance.

---

## 7. The Conservation Theorem

**Theorem (Geofinite):** For any admissible decomposition of S_η with admissible rigid motions:

$$\mu_{\mathbb{M}}(U) \approx \mu_{\mathbb{M}}(S_\eta)$$

No admissible decomposition yields μ_M(U) ≈ 2·μ_M(S_η).

**Proof sketch:**

1. Each S_i has vol(S_i) ≥ δV — no infinitesimally small pieces
2. Total volume: Σ vol(S_i) ≈ V(B) ± k·ε_boundary
3. Each T_i preserves μ_M within ε_T
4. Reassembled volume: μ_M(U) ≈ Σ μ_M(T_i(S_i)) ≈ Σ μ_M(S_i) ≈ V(B) ± (k·ε_boundary + k·ε_T)
5. With k ≤ N and bounded ε, total error is bounded: μ_M(U) ≈ V(B) ± σ

The doubling would require μ_M(U) ≈ 2V(B). This requires either: (a) pieces with no size lower bound (δV → 0, inadmissible) or (b) motions that are not volume-preserving (inadmissible) or (c) non-measurable pieces (inadmissible). All three routes are blocked by admissibility.

---

## 8. The Inverted Collapse Note

Each essay in the series ATT_39–ATT_44 ends with a **forward collapse note**: as uncertainties and bounds vanish, the classical result is recovered. Geofinitism subsumes classical theory in the limit.

ATT_46 (like ATT_45) has an **inverted collapse note**:

> Removing the measurability constraint and finite resolution bound restores the classical paradox. As δV → 0 and η → 0, admissible decompositions become arbitrary point-set decompositions, and the Banach-Tarski construction becomes available.

**Series collapse-note table (complete through ATT_46):**

| Essay | Classical limit recovered | Direction |
|-------|--------------------------|-----------|
| ATT_39 | P vs NP binary verdict | Forward |
| ATT_40 | Classical CTT | Forward |
| ATT_41 | Classical K_U(x) | Forward |
| ATT_42 | PAC generalization bounds | Forward |
| ATT_43 | Classical consensus guarantees | Forward |
| ATT_44 | Standard decoherence predictions | Forward |
| ATT_45 | Classical Russell paradox | **Inverted** |
| ATT_46 | Classical Banach-Tarski paradox | **Inverted** |

**Pattern:** Essays 139–144 apply Geofinitism to problems where the classical result is correct but the Geofinite framework adds measurability, uncertainty, and admissibility. Essays 145–146 apply Geofinitism to paradoxes where the classical "result" is a contradiction — here, Geofinitism resolves the paradox by showing it arises only in the unbounded/non-measurable limit that Geofinitism does not inhabit.

---

## 9. Comparison with Classical Responses

| Response | Mechanism | Strength | Limitation |
|----------|-----------|----------|-----------|
| **"It's not physical"** | BT uses abstract mathematics; physics doesn't have non-measurable sets | Intuitively correct | No formal criterion; cannot be generalised |
| **Reject AC** | Constructive/intuitionistic mathematics denies AC; then BT cannot be proved | Logically rigorous | Removes powerful tools; restricts large portions of analysis |
| **Restrict comprehension** | As in ZF: limit which sets can be formed | Standard mathematical practice | Does not provide a physical admissibility criterion |
| **Geofinitism** | Non-measurable sets are inadmissible as decomposition pieces; measured volume is conserved | Preserves AC for abstract use; gives formal physical admissibility criterion; generalises to other domains | Requires declaring resolution η and minimum piece size δV |

**The Geofinite advantage:** the admissibility criterion (vol ≥ δV, k ≤ N, bounded-precision motions) generalises. It can be applied to any geometric, physical, or computational decomposition problem — not just to set-theoretic paradoxes. It is the same criterion used in ATT_45 for set construction (Gen(θ,B)) and in ATT_28 for symbolic systems generally.

---

## 10. Inadmissibility vs. Impossibility

A key distinction: Geofinitism does not say Banach-Tarski is *impossible* — it says it is *inadmissible* within finite, measurable geometry.

| Statement | Status |
|-----------|--------|
| "Banach-Tarski is impossible in ZFC" | **False** — it is a theorem of ZFC |
| "Banach-Tarski is impossible in intuitionistic mathematics" | **True** — AC is not available |
| "Banach-Tarski is inadmissible as a finite, measurable decomposition" | **True (Geofinite)** — non-measurable sets fail admissibility conditions |
| "The classical theorem is still true within abstract set theory" | **True** — Geofinitism does not contradict it |

This is the same structure as ATT_45: Russell's paradox is not *inconsistent* within Geofinitism — it is *inadmissible*. The classical theorem stands as a theorem about useful fictions; it fails the admissibility criterion for constructions that must produce measurable, finite-resource outputs.

---

## 11. Summary

| Concept | Classical | Geofinitist |
|---------|-----------|-------------|
| Decomposition pieces | Arbitrary subsets of ℝ³ (including non-measurable) | Admissible: vol(S_i) ≥ δV; k ≤ N |
| Volume | Lebesgue measure (exact; undefined for non-measurable sets) | μ_M(A) = (Σ η³, ε_μ) — Measured Number |
| Rigid motions | Exact; defined on arbitrary point sets | Admissible: μ_M(T_i A) ≈ μ_M(A) |
| Volume additivity | Exact (for measurable sets) | Approximate: μ_M(A∪B) ≈ μ_M(A) + μ_M(B) ± ε |
| Conservation | Fails for non-measurable decompositions | Holds for all admissible decompositions |
| BT result | Volume doubling — paradox | Inadmissible — non-measurable pieces fail admissibility |
| Resolution | ℝ³ — infinite precision | Finite η > 0 — voxel body S_η |
| Collapse note | Classical paradox in the limit (inverted) | Removing bounds recovers the paradox |

---

## Connections to Other Lessons

| Lesson | Connection |
|--------|-----------|
| ATT_45 | Russell's Paradox — parallel inverted collapse note; both paradoxes reclassified as inadmissible constructions; both arise from removing finiteness/measurability constraints; BT is the geometric analogue of Russell's set-theoretic inadmissibility |
| ATT_28 | Commitment, Consensus, Admissibility: admissibility criterion (vol ≥ δV; k ≤ N; bounded-error motions) is ATT_28's admissibility framework applied to geometric decomposition; ATT_46 is the geometric instantiation of ATT_28 |
| ATT_08 | Geofinitism — Measurement-First: μ_M(A) = (Σ η³, ε_μ) directly inherits M = (v, ε, P); measured volume is a Measured Number with provenance (resolution η, procedure voxelisation, boundary error) |
| ATT_23 | The Generon: voxel body S_η as a finite generative construction — analogous to Gen(θ,B); a Banach-Tarski decomposition would require a Generon that produces non-measurable output — inadmissible by the Generon's finite execution property |
| ATT_39 | P vs NP (first essay in series): series pattern — each essay applies the Five Pillars to a classical problem; ATT_46 completes the "paradox pair" (with ATT_45) forming the inverted-collapse-note sub-series |
| ATT_10 | Geometry in Geofinitism — The Alphon Lattice: the voxel representation S_η = ∪V_j is an Alphon-level lattice structure; finite-resolution geometry as the Alphon container; rigid motions as admissible lattice transformations |

---

*Kevin R. Haylett — School of Geofinitism*  
*Simul Pariter.*
