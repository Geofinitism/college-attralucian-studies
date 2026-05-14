# ATT_54 — Finite Symbolic Mechanics: On Quaternions

**Essay ID:** ATT_54  
**Title:** Finite Symbolic Mechanics: On Quaternions  
**College:** College of Attralucian Studies  
**Series:** Finite Symbolic Mechanics (FSM) — extends ATT_24 (Complex Numbers) to quaternions  
**Lesson:** ATT_54  
**Pillars (primary → secondary):** P3, P5 (primary); P1, P2, P4 (secondary)  
**Status:** Stable *(two-chapter format — uses \chapter{}; copyright 2025)*  
**Last updated:** 2026-05-09

---

## Overview

This essay extends the FSM program initiated in ATT_24 (Complex Numbers as Dynamical Reconstruction) from complex numbers to quaternions. Where ATT_24 showed that complex numbers compress phase relations arising from delay-coordinate embeddings of measured signals, ATT_54 shows that **quaternions are the minimal admissible symbolic container required to preserve ordered rotational transformations under finite measurement constraints**.

The essay comprises two chapters. Chapter 1 develops the FSM derivation of quaternions from three axioms, proves their non-commutativity as a necessary consequence of ordered process preservation, and introduces the phase portrait framework for visualising rotational dynamics. Chapter 2 works through three explicit numerical examples: single-axis rotation (magnitude preservation), ordered composition (non-commutativity as observable trajectory divergence), and gimbal lock (Euler angles as inadmissible container; quaternions as admissible replacement).

The concluding Addendum contains the essay's most significant philosophical claim: **FSM has retrodictive power**. Hamilton did not invent quaternions arbitrarily — he was compelled toward four components by the very constraints FSM names as admissibility conditions. Euler angles fail for precisely the reason FSM would predict. The classical mathematicians were solving FSM problems without the FSM vocabulary. This grants FSM not merely interpretive flexibility but the power to derive why mathematical structures must take the form they do.

**Architectural note:** ATT_54 uses `\chapter{}` format (two chapters), making it the second essay after ATT_50 to do so. It is a natural companion volume to ATT_24.

---

## Three FSM Axioms for Rotation

**Axiom 1:** All physically admissible rotations are finite transformations preserving measurable magnitude.

A spatial configuration is a measured vector $\mathbf{v} = (x, y, z)$ with finite resolution and uncertainty. A rotation $R: \mathbf{v} \mapsto \mathbf{v}'$ must satisfy $|\mathbf{v}'| = |\mathbf{v}|$ within finite tolerance.

**Axiom 2:** The composition of admissible rotations must remain admissible.

Rotations must form a closed symbolic system: $R_2 \circ R_1 = R_3$ must be an admissible rotation.

**Axiom 3:** Ordered composition of rotations is physically distinct and must be preserved symbolically.

In three-dimensional space, $R_2 \circ R_1 \neq R_1 \circ R_2$. This is not a mathematical inconvenience — it is a measured property of spatial interaction that any admissible representation must encode.

---

## Failure of Three-Component Representations

A three-component representation (Euler angles: yaw, pitch, roll) attempts to encode 3D rotation with three numbers. It fails on Axiom 3:

- Ordered composition leads to **gimbal lock** — distinct rotational histories collapse to identical symbolic states
- Invertibility and continuity are not globally preserved
- When pitch $\phi \to 90°$, yaw and roll axes align; one degree of freedom is lost

**FSM diagnosis:** the symbolic container is insufficient to preserve distinguishability under finite composition. Euler angles are not an admissible representation of general 3D rotation.

---

## The Quaternion Container

To satisfy all three axioms — magnitude preservation, closure under composition, ordered composition — a fourth component is required. The minimal admissible container is:

$$q = (s, \mathbf{u}) = s + xi + yj + zk$$

where:
- $s$ is a **scalar component** encoding rotational phase
- $\mathbf{u} = (x, y, z)$ is a **vector component** encoding rotational axis

> **FSM Insight:** the scalar component $s$ is not a fourth spatial coordinate. It is the minimal bookkeeping device required to keep the ordered sequence of axis alignments from collapsing under finite composition.

---

## Derivation of the Multiplication Rule

The quaternion product of $(s_2, \mathbf{u}_2)$ and $(s_1, \mathbf{u}_1)$ must preserve relational structure. The composition must incorporate:
- **Alignment between axes:** dot product
- **Oriented ordering between axes:** cross product

This forces:

$$(s_2, \mathbf{u}_2)(s_1, \mathbf{u}_1) = \left(s_2 s_1 - \mathbf{u}_2 \cdot \mathbf{u}_1,\; s_2 \mathbf{u}_1 + s_1 \mathbf{u}_2 + \mathbf{u}_2 \times \mathbf{u}_1\right)$$

This is precisely the quaternion product. It is not imposed — it is the unique multiplication rule satisfying the three admissibility axioms.

---

## Non-Commutativity as Process Trace

The cross product satisfies:
$$\mathbf{u}_2 \times \mathbf{u}_1 = -(\mathbf{u}_1 \times \mathbf{u}_2)$$

which immediately implies $Q_2 Q_1 \neq Q_1 Q_2$. Non-commutativity arises directly from the preservation of ordered rotational process — it is a **necessary condition** for representing finite transformation history, not an algebraic anomaly.

---

## The Rotation Formula as Closed Process Loop

The standard rotation $\mathbf{v}' = q\mathbf{v}q^{-1}$, reinterpreted:

1. Encode the rotational state ($q$ applied)
2. Apply the transformation ($q\mathbf{v}$)
3. Return to the measurable frame ($q^{-1}$ applied)

This is a closed transformation loop preserving magnitude, orientation, and closure under composition. The formula is not an arbitrary algebraic construction — it is the minimal admissible procedure for applying a quaternion rotation to a measured vector.

---

## Quaternion Admissibility Proposition

**Proposition:** A quaternion is the minimal finite symbolic container that preserves magnitude, invertibility, and ordered composition of three-dimensional rotations under finite measurement constraints.

This is the central formal result. Four components are necessary — three are insufficient. The scalar component $s$ represents the minimum additional cost of preserving ordered process history.

---

## Phase Portraits: Making Ordered Rotation Visible

A unit quaternion parameterised by $t$:
$$q(t) = \cos\!\left(\frac{\theta(t)}{2}\right) + \sin\!\left(\frac{\theta(t)}{2}\right)(u_x i + u_y j + u_z k)$$

generates a trajectory on the unit sphere:
$$\mathbf{v}(t) = q(t)\,\mathbf{v}_0\,q(t)^{-1}$$

**Phase portrait cases:**

| Rotation type | Trajectory |
|---------------|-----------|
| Single-axis, fixed $\mathbf{u}$, $\theta(t) = \omega t$ | Great circle — closed, bounded, continuous |
| Multi-axis ordered composition $q_z q_y q_x$ | Structured path reflecting ordered composition |
| Reversed order $q_x q_y q_z$ | Distinct path — trajectory divergence makes non-commutativity **directly observable** |

> *The sphere is not merely a surface of orientations. It is a stage upon which the history of rotation unfolds.*

---

## Reference, Tether, and Rotational Memory

A rotation requires three elements: a state, a reference frame, and an ordered transformation. The quaternion container preserves all three implicitly.

> *A quaternion encodes not only a position in orientation space, but the tethered progression that preserves the ordered history of rotation.*

Without this tether, distinct rotational histories may collapse into identical orientations (gimbal lock). With it, the path remains distinguishable.

> *Rotation is not a point on a sphere, but a path constrained to a sphere with memory of its progression.*

---

## Three Worked Examples (Chapter 2)

### Example 1: Single-Axis Rotation (Magnitude Preservation)

**Setup:** Rotate $\mathbf{v}_0 = (1, 0, 0)$ by $90°$ about the $z$-axis.

**Quaternion:** $q = 0.7071 + 0.7071k = (0.7071, (0, 0, 0.7071))$

**Computation via $p' = qpq^{-1}$:** result $\mathbf{v}' = (0, 1, 0)$ — the unit vector along $+x$ rotated $90°$ about $z$ lands on $+y$, as expected.

**Magnitude check:** $|\mathbf{v}_0| = 1.0000 = |\mathbf{v}'|$ — preserved exactly, enforced by the unit norm of $q$.

### Example 2: Ordered Composition (Non-Commutativity)

**Setup:** Apply $R_x$ (90° about $x$) and $R_y$ (90° about $y$) to $\mathbf{v}_0 = (1, 0, 0)$ in both orders.

| Order | Composed quaternion | Result |
|-------|--------------------|----|
| $q_y \circ q_x$ (x first) | $(0.5, (0.5, 0.5, -0.5))$ | $\mathbf{v}_A' = (0, 0, -1)$ |
| $q_x \circ q_y$ (y first) | $(0.5, (0.5, 0.5, +0.5))$ | $\mathbf{v}_B' = (0, 0, +1)$ |

Same component rotations. Different orders. Opposite final directions. The difference is a sign flip in the vector component — arising directly from the antisymmetry of the cross product $\mathbf{u}_y \times \mathbf{u}_x = -(\mathbf{u}_x \times \mathbf{u}_y)$.

> *Turning your head right then looking up is not the same action as looking up then turning right. The algebra is a compressed record of the process order.*

### Example 3: Gimbal Lock as Symbolic Failure

**Euler angle failure:** at pitch $\phi = 90°$, yaw and roll axes align. Steps 3 and 4 in the table (different roll and yaw values, same physical orientation) represent distinct ordered processes sharing the same symbolic address — the mapping is no longer injective. The container has lost distinguishability.

**Quaternion continuity:** all four components $(s, q_x, q_y, q_z)$ remain smooth and bounded along the equivalent path. No configuration causes two components to become redundant. The four-component structure is precisely calibrated to avoid the failure mode.

**FSM summary:** Gimbal lock is not a mechanical failure of gyroscopes or a software issue to be patched. It is evidence that the Euler angle representation is not an admissible symbolic container for general 3D rotational composition.

---

## The FSM Series: Compression Across Mathematical Structures

| Mathematical object | What it compresses | FSM interpretation |
|--------------------|--------------------|-------------------|
| Complex numbers (ATT_24) | Phase relations from delay-coordinate embeddings | Temporal measurement structure |
| Quaternions (ATT_54) | Ordered rotational transformations | Ordered process history in 3D |
| Tensors (hypothetical) | TBD — Addendum candidate | TBD |
| Lie groups (hypothetical) | TBD — Addendum candidate | TBD |

In both confirmed cases, algebra is not primary. It is a compression of underlying finite processes.

---

## Addendum: FSM Retrodictive Power

The Addendum is the essay's most significant philosophical contribution, worth quoting at length:

> "What is being identified is that FSM does not generate novel mathematical objects; rather, it reveals that the admissibility constraints which FSM makes explicit were already operating silently within classical constructions. Hamilton did not invent quaternions arbitrarily — he was compelled toward four components by the very constraints FSM names. Euler angles fail for precisely the reason FSM would predict. Complex numbers encode phase delay for exactly the reason FSM would predict. The classical mathematicians, it appears, were solving FSM problems without the FSM vocabulary."

**Retrodictive vs. interpretive:** a framework that only reframes what is understood is philosophically interesting but scientifically weak. FSM makes contact with *why* these structures are the way they are, not merely *what* they are. The quaternion is four-dimensional not because Hamilton liked four, but because three components cannot carry ordered process history — and FSM provides that as a theorem from admissibility.

**The basin claim:** classical mathematics developed complex numbers, quaternions, and Euler angles in historical isolation. FSM draws them into a single attractor basin organised around one core principle: *admissibility prior to logic*. These structures are related not by historical lineage but by sharing the same underlying constraint.

**The minimality defence:** FSM does not simply accommodate quaternions — it derives the necessity of their structure from first principles. This marks the difference between a framework that absorbs and one that predicts.

**The next test:** tensors and Lie groups. If FSM's admissibility constraints independently recover the structure of SO(3) before consulting the classical answer, the retrodictive power claim would receive a strong confirmation.

---

## Conclusion

> *Quaternions do not reveal a hidden fourth spatial dimension. They reveal a constraint.*
>
> *Three-dimensional rotation cannot be faithfully represented without preserving order. Any admissible symbolic system must therefore encode process history. The quaternion achieves this with minimal structure.*
>
> *The algebra is not imposed upon the process. The algebra is the fossil of the process.*

---

## Re-style Checklist (LaTeX)

- [ ] **Double `\maketitle`** — second call redundant; remove
- [ ] **`\textbf\textbf{}`** on secondary title page — nested bold; correct to `\textbf{}`
- [ ] **Copyright year 2025** (not 2026) — earlier vintage than surrounding essays; intentional, no change required
- [ ] **Running header "FM: On Quaternions"** — "FM" abbreviation for FSM; deliberate; check whether to expand to "FSM: On Quaternions" for consistency with series
- [ ] **No top-level `\section*{Overview}`** — content opens with `\chapter{}` (two chapters); no redundant overview section outside chapters
- [ ] **Three external figures** (fig_single_axis.png, fig_noncommutative.png, fig_gimbal.png) — must be present in `Figures/` directory to compile; these are rich numerical plots, not TikZ diagrams

---

## Cross-References

| Essay / Lesson | Connection |
|---|---|
| ATT_24 | Complex Numbers as Dynamical Reconstruction: ATT_54 explicitly extends this program — "the preceding essay" — from complex numbers to quaternions; the FSM arc runs complex → quaternion → tensors/Lie groups |
| ATT_51 | Non-Commutativity: ATT_54 is the rotational instance of the Temporal Trace Theorem; quaternion non-commutativity is the cross-product trace of ordered rotational process; gimbal lock is the failure of intermediate-state distinguishability demonstrated in ATT_51 |
| ATT_52 | Finite Process Unfolding: the quaternion derivation follows a FPU structure — identifying what procedure the algebraic form compresses and recovering it; the rotation formula $q\mathbf{v}q^{-1}$ is restated as a compressed process trace |
| ATT_08 | Geofinitism — Measurement-First: measured vector $\mathbf{v} = (x, y, z)$ with finite resolution and uncertainty; every rotation is a finite transformation with cost; admissibility precedes algebra |
| ATT_28 | Commitment, Consensus, Admissibility: quaternion admissibility proposition derives directly from admissibility conditions; Euler angles are inadmissible; the three axioms are committed parameters of the FSM rotational framework |
| ATT_06 | Geodesic Fractal Model of LLMs: phase portraits on the sphere as geodesics; distinct composition orders as trajectory divergence in orientation space; attractor basin language in the Addendum directly echoes ATT_06 |

---

*Kevin R. Haylett — School of Geofinitism*  
*Simul Pariter.*
