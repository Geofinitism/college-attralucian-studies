# ATT_57 — On Computability: A Geofinitist Computability Thesis

**Essay ID:** ATT_57  
**Title:** On Computability: A Geofinitist Computability Thesis  
**College:** College of Attralucian Studies  
**Series:** Computational application series — formal companion to ATT_40 (Church-Turing)  
**Lesson:** ATT_57  
**Pillars (primary → secondary):** P4, P5 (primary); P2, P1, P3 (secondary)  
**Status:** Stable  
**Last updated:** 2026-05-09

---

## Architectural Note

ATT_57 is the formal companion to ATT_40 (The Church-Turing Thesis: A Geofinitist Reinterpretation), in the same relationship as ATT_58 is to ATT_44. ATT_40 applied the Five Pillars conceptually; ATT_57 develops the full formal machinery — measured procedures with output uncertainty and provenance, $(\tau, \delta)$-computability, device emulation with measured residual, and the boxed $\mathsf{CTT}_{\mathbb{M}}$ statement.

The essay is structurally distinctive: it contains two registers within a single document. The first is a narrative, pedagogically accessible treatment applying the Five Pillars through analogy (the scribe and the supercomputer; the engineer measuring $x^2$ across architectures). The second is a rigorous formal tcolorbox containing the mathematical formulation of the Geofinitist Church-Turing Thesis. The essay is the most technically complete in the computational series.

---

## Overview

The Church-Turing Thesis (CTT) claims that any function computable by a human following a step-by-step procedure is computable by a Turing machine (or $\lambda$-calculus, or recursive function). ATT_57 does not contest the mathematical convergence result that underlies CTT — it challenges the **assumptions under which the thesis is posed**: infinite tape, exact symbols, unlimited precision, universal applicability across all scales and physical substrates.

The Geofinitist reframing: CTT is not a cosmic truth but an **auditable universality principle** — a measured claim about what finite physical procedures can emulate, within stated tolerance and confidence bounds, with documented provenance. When the finite guardrails are in place, the thesis becomes testable. When they are removed, the thesis becomes a useful fiction.

---

## Narrative Part: Five Pillars Applied to CTT

### Pillar I — Computation as Trajectory Through a Resource Manifold

Classical CTT treats computation as binary: a function is computable or it is not. Geofinitism replaces this with a **trajectory through a resource manifold** $M$. The manifold has dimensions of time, memory, energy, and precision. A computation is a path through $M$. Whether a function is computable depends on which region of $M$ is accessible.

Different physical substrates (quantum chip, classical processor, biological neural network) trace different trajectories through $M$. Claiming they all compute "the same things" is only admissible where their trajectories can be shown to converge within $M$.

### Pillar II — Symbols Are Approximations

Classical CTT: symbols on a Turing machine's tape are perfect; steps are exact; precision is unlimited. Reality: bits flip due to electrical noise; quantum states wobble; timing is imperfect. Geofinitism models symbols and states as approximations subject to uncertainties $\sigma_t$ (timing) and $\sigma_s$ (storage). Computation becomes measurable, rooted in physical imperfection rather than abstracted away from it.

### Pillar III — The Cascade of Scales

Computation is a cascade from electron flicker to algorithm. Each layer — hardware, microarchitecture, algorithm — adds constraints and uncertainties. The recursive structure:

$$C_n = f(C_{n-1}, \Delta r)$$

where $C_n$ is computation at one scale, built on layer $C_{n-1}$ with resource increments $\Delta r$. Classical CTT assumes one description fits all scales. Geofinitism preserves the layered structure.

### Pillar IV — CTT as Useful Fiction

CTT claims "effective calculability" as a universal property. Geofinitism identifies this as a **useful fiction**: a claim that extends beyond what can be measured or tested. The convergence of Turing machines, $\lambda$-calculus, and recursive functions is well established within their formal domain. The extension to all possible physical processes is not testable and is therefore inadmissible as a physical claim. CTT is valid within stable, measurable boundaries; it becomes inadmissible when applied outside them.

### Pillar V — Finite Quanta

Classical CTT assumes infinite time, infinite tape, unlimited precision. Geofinitism insists on finite quanta: minimum time unit $\delta t > 0$ and minimum space unit $\delta s > 0$. All reasoning operates within these bounds.

**Computability functional (narrative):**

$$C_f(x) = \frac{\Delta O}{\delta t \cdot \delta s} + \sigma_c(x, \delta t, \delta s)$$

where $\Delta O$ measures progress toward the correct output, and $\sigma_c$ captures hardware noise and decoding errors. Across scales:

$$C_f(x) = \frac{1}{K}\sum_{i=1}^K C_f^{(i)}(x)$$

A function is Geofinitist-computable if $C_f(x)$ exceeds threshold $\theta$ along a stable path in $M$.

---

## Formal Part: The Boxed $\mathsf{CTT}_{\mathbb{M}}$ Statement

### Measured Procedures

A device $D$ with control parameters $\theta$ and input $x \in \Sigma^\star$ induces a measured procedure:

$$\mathsf{Proc}_{D,\theta}(x) = \big(y,\ \varepsilon_y,\ P_D;\ T,\ \varepsilon_T;\ S,\ \varepsilon_S\big) \in \mathbb{M}$$

| Component | Meaning |
|-----------|---------|
| $y \in \Sigma^\star$ | Output |
| $\varepsilon_y$ | Output uncertainty |
| $P_D$ | Provenance: hardware, calibration, noise model, operator protocol |
| $T, \varepsilon_T$ | Time and time uncertainty |
| $S, \varepsilon_S$ | Space and space uncertainty |

Every computation is a measurement. Every output carries uncertainty and provenance. This is M = (v, ε, P) applied to computational outputs.

### $(\tau, \delta)$-Computability

A partial function $f: \Sigma^\star \rightharpoonup \Sigma^\star$ is **$(\tau, \delta)$-computable by $D$ on domain $\mathcal{X}$** if:

$$\forall x \in \mathcal{X}: \Pr_\omega\!\Big[d_{\mathbb{M}}\big(\mathsf{Proc}_{D,\theta}(x;\omega),\ f(x)\big) \leq \tau\Big] \geq 1 - \delta$$

within declared time/space budgets and with documented provenance. $d_{\mathbb{M}}$ is the distance in measured-number space between the output and the ideal $f(x)$. The tolerance $\tau$ and failure probability $\delta$ are committed parameters.

### Emulation Between Devices

Universal Turing machine $U$ **emulates** device $D$ at tolerance $\tau$ and confidence $1-\delta$ if there exists encoding $E$ and program $p_D$ such that:

$$\forall x \in \mathcal{X}: \Pr_\omega\!\Big[d_{\mathbb{M}}\big(U(p_D, E(x);\omega),\ \mathsf{Proc}_{D,\theta}(x;\omega)\big) \leq \tau\Big] \geq 1-\delta$$

with resource overhead bounded by measured polynomial $n \mapsto \mathrm{poly}(n)$. Provenance $P_E, P_{p_D}$ documents the encoding and emulator.

### The Geofinitist Church-Turing Thesis

$$\boxed{\mathsf{CTT}_{\mathbb{M}}: \quad \forall D \in \mathfrak{D}\ \exists\ (U, p_D, E): U \text{ emulates } D \text{ at } (\tau, \delta) \text{ with poly overhead on all calibrated ranges.}}$$

where $\mathfrak{D}$ is the class of **admissible physical procedures**: finite, reproducible, locally causal; bounded energy/precision per step.

Equivalently: any $(\tau, \delta)$-computable transformation realised by an admissible device is $(\tau', \delta')$-computable by $U$ with $\tau', \delta'$ controllable by standard error-reduction.

### Model Notes

**Randomized:** seed $\omega$ captured in $P_\omega$; $U$ emulates distributions via PRNG or sampling, preserving total variation within $\tau$.

**Analog:** signals discretised at finite resolution; admissibility requires Lipschitz/energy bounds preventing super-TM encodings in noise.

**Quantum:** For finite-precision unitary dynamics and measurement, $U$ emulates to $(\tau, \delta)$ via quantum circuit simulation with poly overhead in time and exponential in qubits only if required by target accuracy. Claims of super-TM power must specify which admissibility guard is broken.

**Oracles:** Oracle access is treated as provenance (external service); emulation includes the same oracle — not a claim of computation beyond $U$.

### Verification

Given test battery $\mathcal{B}$, the **emulation residual**:

$$R_{\text{emu}}(D \Rightarrow U) = \mathrm{median}_{(x,\omega) \in \mathcal{B}}\ d_{\mathbb{M}}\big(U(p_D, E(x);\omega),\ \mathsf{Proc}_{D,\theta}(x;\omega)\big)$$

with uncertainty bands. Universality at $(\tau, \delta)$ is corroborated when $R_{\text{emu}} \leq \tau$ and failure rates $\leq \delta$ across perturbations of $x$, $\theta$, and environment.

### Inadmissibility and Abstention

- Device behaviour **unstable** (non-reproducible beyond tolerance) → label **INADMISSIBLE** for $\mathsf{CTT}_{\mathbb{M}}$
- Unbounded precision/energy required to specify inputs or read outputs → **INADMISSIBLE**
- Super-Turing capability claimed without specifying which guard is broken → report **UNDERDETERMINED**

### Forward Collapse Note

As $\varepsilon \to 0$, budgets extend, and encoders/decoders become ideal: the Geofinitist account reduces to classical CTT — every effectively calculable function is Turing-computable, every reasonable model simulable by universal TM with at most polynomial overhead. Geofinitism keeps the finite guardrails in place: computability and universality are **measured claims with provenance, tolerance, and resource profiles**.

---

## CTT as Auditable Universality Principle

> "What counts as 'effective' is precisely what we can reproduce, emulate, and verify within finite tolerance on physical devices. The thesis is upheld to the degree that admissible devices fall into the same emulation class as $U$ under $\mathbb{M}$; departures must specify which guard (precision/energy/causality/reproducibility) they break."

This is the definitive shift: CTT stops being a philosophical claim about the nature of mind and computation, and becomes an **engineering standard** — auditable, testable, and bounded.

---

## Re-style Checklist (LaTeX)

- [ ] **PRIORITY: Running header "P vs NP"** — carries over from ATT_39's template; should be updated to "Geofinitist Computability Thesis" or "On Computability"
- [ ] **`\section*{}` → `\subsection*{}` → `\subsubsection*{}`** — three header levels used; elevate `\subsubsection*{}` (Pillars 1–5) to `\subsection*{}` or `\section*{}` for series consistency
- [ ] **Double `\maketitle`** — second call redundant; remove
- [ ] **`\textbf\textbf{}`** on secondary title page — nested bold; correct to `\textbf{}`
- [ ] **tcolorbox without title** — the formal section uses a plain tcolorbox; consider adding a title frame (e.g. "The Geofinitist Church-Turing Thesis — Formal Statement") for navigability

---

## Cross-References

| Essay / Lesson | Connection |
|---|---|
| ATT_40 | Church-Turing Thesis (survey): ATT_57 is the formal companion; ATT_40 applied Five Pillars conceptually; ATT_57 develops the full measured-procedure and $(\tau,\delta)$-computability machinery |
| ATT_56 | Geofinite Halting Thesis: both ATT_56 and ATT_57 reframe classical computability results (Halting / Church-Turing) using the same Geofinite machinery; UNDERDETERMINED (ATT_56) maps to UNDERDETERMINED / INADMISSIBLE (ATT_57) |
| ATT_08 | Geofinitism — Measurement-First: $\mathsf{Proc}_{D,\theta}(x) = (y, \varepsilon_y, P_D; T, \varepsilon_T; S, \varepsilon_S) \in \mathbb{M}$ is M = (v, ε, P) applied to computational procedures; every computation carries provenance |
| ATT_28 | Commitment, Consensus, Admissibility: $(\tau, \delta)$ are committed parameters; admissible procedures are those meeting the finite/reproducible/bounded criteria; $\mathfrak{D}$ is the admissibility class |
| ATT_58 | Geofinite Decoherence Thesis: ATT_57's quantum model note (finite-precision unitary dynamics) connects directly to ATT_58's treatment; together they establish Geofinite accounts of both computation and quantum measurement |
| ATT_39 | P vs NP: ATT_39's resource-bounded complexity sits within the $\mathsf{CTT}_{\mathbb{M}}$ framework — complexity classes are regions of the resource manifold $M$ |

---

*Kevin R. Haylett — School of Geofinitism*  
*Simul Pariter.*
