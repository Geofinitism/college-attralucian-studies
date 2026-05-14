# ATT_57 — The Geofinitist Computability Thesis

**College:** College of Attralucian Studies  
**Lesson ID:** ATT_57  
**Source essay:** ATT_57 — *On Computability: A Geofinitist Computability Thesis*  
**Level:** Advanced  
**Prerequisites:** ATT_08; ATT_28; ATT_40 (Church-Turing survey — essential, ATT_57 is the formal companion); ATT_56 (Geofinite Halting Thesis — strongly recommended, shares measured-procedure machinery); ATT_48 (Liar Paradox — recommended); background in theoretical computer science and computability theory  
**Next lesson:** ATT_58 (Quantum Decoherence)

---

## Learning Outcomes

By the end of this lesson you will be able to:

1. State the classical Church-Turing Thesis (CTT) and identify the three assumptions Geofinitism challenges
2. Explain the distinction between the mathematical convergence result underlying CTT and the physical claims it is typically taken to make
3. Represent a computation as a trajectory through a resource manifold $M$ with dimensions of time, memory, energy, and precision
4. Define a measured procedure $\mathsf{Proc}_{D,\theta}(x) = (y, \varepsilon_y, P_D; T, \varepsilon_T; S, \varepsilon_S) \in \mathbb{M}$ and explain each component
5. Define $(\tau, \delta)$-computability and explain the role of committed tolerance and confidence parameters
6. State the emulation condition between devices and explain the role of encoding provenance $P_E$
7. State the boxed $\mathsf{CTT}_{\mathbb{M}}$ thesis and explain what it claims and what it withholds
8. Explain the labels INADMISSIBLE and UNDERDETERMINED for super-Turing capability claims
9. Define the emulation residual $R_{\text{emu}}$ and describe how universality at $(\tau, \delta)$ is corroborated
10. Explain the forward collapse: when tolerances vanish and budgets extend, recover classical CTT
11. Apply all five Pillars to the Geofinitist reframing of computability
12. Articulate why the Geofinitist CTT is an engineering standard rather than a philosophical thesis

---

## 1. The Classical Church-Turing Thesis

### What CTT Claims

The Church-Turing Thesis (CTT) asserts: any function computable by a human following a step-by-step procedure is computable by a Turing machine — equivalently by $\lambda$-calculus or general recursive functions.

CTT is not a theorem. It is a *thesis*: a claim about the relationship between informal human computation and formal machine computation. Its strength lies in the convergence of multiple independent formalisms — Turing machines, $\lambda$-calculus, recursive functions — all arriving at the same class of computable functions.

### The Three Critical Assumptions

Geofinitism does not contest the mathematical convergence result. It challenges the **assumptions under which CTT is posed**:

| Assumption | What it requires | Geofinite critique |
|-----------|-----------------|-------------------|
| Infinite tape | Unbounded memory | No physical device has infinite storage |
| Exact symbols | Perfect, noiseless symbol manipulation | Every physical symbol is subject to noise and drift |
| Universal applicability | CTT holds across all scales, substrates, and physical systems | Not a testable claim — it is a projection beyond measurable scope |

The mathematical content of CTT is valid within the abstract domain. The extension to physical computation is not testable and is therefore inadmissible as a physical claim.

---

## 2. Computation as Trajectory Through a Resource Manifold

### The Manifold $M$

Classical CTT treats computability as binary: a function is computable or it is not. Geofinitism replaces this with a **trajectory through a resource manifold**.

The manifold $M$ has dimensions:
- **Time** — steps required
- **Memory** — space consumed
- **Energy** — physical cost per operation
- **Precision** — symbol resolution and noise tolerance

A computation is a *path* through $M$. Whether a function is computable depends on which region of $M$ is accessible to the device performing the computation.

**Pillar I:** $M$ is the geometric container. Different physical substrates (classical processor, quantum chip, biological neural network) trace different trajectories through $M$. The CTT claim that they all compute "the same things" is only admissible where their trajectories can be shown to converge within $M$.

### Why Device Comparison Requires Measurement

Classical CTT assumes devices can be compared abstractly. Geofinitism requires that any equivalence claim between devices be grounded in measured convergence — with explicit tolerance and provenance — across the resource manifold.

---

## 3. Symbols as Approximations

### Pillar II Applied to Computation

Classical CTT: symbols on a Turing machine's tape are perfect; steps are exact; precision is unlimited.

Physical reality: bits flip due to electrical noise; quantum states wobble; timing is imperfect; reading and writing introduce error.

Geofinitism models symbols and computational states as **approximations** subject to:
- $\sigma_t$ — timing uncertainty
- $\sigma_s$ — storage uncertainty

Computation becomes **measurable**, rooted in physical imperfection rather than abstracted away from it. This is Pillar II applied directly: symbols are measurements of intended values, not the values themselves.

---

## 4. Measured Procedures

### The Formal Definition

A device $D$ with control parameters $\theta$ and input $x \in \Sigma^\star$ induces a **measured procedure**:

$$\mathsf{Proc}_{D,\theta}(x) = \big(y,\ \varepsilon_y,\ P_D;\ T,\ \varepsilon_T;\ S,\ \varepsilon_S\big) \in \mathbb{M}$$

| Component | Meaning |
|-----------|---------|
| $y \in \Sigma^\star$ | Output |
| $\varepsilon_y$ | Output uncertainty — precision of the result |
| $P_D$ | Provenance: hardware, calibration, noise model, operator protocol |
| $T, \varepsilon_T$ | Time and time uncertainty |
| $S, \varepsilon_S$ | Space and space uncertainty |

**Connection to ATT_08:** this is M = (v, ε, P) applied to computational procedures. Every computation is a measurement. Every output carries uncertainty and provenance. No computational output is an exact, context-free value.

### What Provenance Records

Provenance $P_D$ answers: *which device, under what conditions, with what calibration, by what operator, at what point in the device's operational lifetime?* Computation without provenance is not admissible as a reproducible finite procedure.

---

## 5. $(\tau, \delta)$-Computability

### Replacing Binary Decidability

Classical CTT asks: does a Turing machine compute $f$? The answer is binary.

Geofinitism replaces this with a probabilistic, tolerance-bounded notion.

A partial function $f: \Sigma^\star \rightharpoonup \Sigma^\star$ is **$(\tau, \delta)$-computable by $D$ on domain $\mathcal{X}$** if:

$$\forall x \in \mathcal{X}: \Pr_\omega\!\Big[d_{\mathbb{M}}\big(\mathsf{Proc}_{D,\theta}(x;\omega),\ f(x)\big) \leq \tau\Big] \geq 1 - \delta$$

within declared time/space budgets and with documented provenance.

| Parameter | Meaning |
|-----------|---------|
| $d_{\mathbb{M}}$ | Distance in measured-number space between output and ideal $f(x)$ |
| $\tau$ | Tolerance — how close the output must be to the ideal |
| $\delta$ | Failure probability — how often the output may exceed tolerance |
| $\omega$ | Randomness seed — captured in provenance |

**$\tau$ and $\delta$ are committed parameters** (ATT_28): declared in advance, not derived post hoc. The computability claim is relative to these committed values.

### Asymmetry of Certifiability

HALT (output reached) admits an explicit certificate — the terminal configuration. Non-computability within budget does not generate an equivalent certificate unless a structural argument (cycle, monotone ranking) is available. This asymmetry is preserved rather than erased, as in the Halting framework (ATT_56).

---

## 6. Emulation Between Devices

### The Emulation Condition

Universal Turing machine $U$ **emulates** device $D$ at tolerance $\tau$ and confidence $1-\delta$ if there exists encoding $E$ and program $p_D$ such that:

$$\forall x \in \mathcal{X}: \Pr_\omega\!\Big[d_{\mathbb{M}}\big(U(p_D, E(x);\omega),\ \mathsf{Proc}_{D,\theta}(x;\omega)\big) \leq \tau\Big] \geq 1-\delta$$

with resource overhead bounded by measured polynomial $n \mapsto \mathrm{poly}(n)$, and with provenance $P_E, P_{p_D}$ documenting the encoding and emulator.

### What Emulation Requires

Emulation is not a philosophical equivalence. It is a **measurable engineering claim**: $U$ can reproduce what $D$ does, within stated tolerance, with bounded overhead, with documented encoding. Every component of this claim is testable.

---

## 7. The Geofinitist Church-Turing Thesis

### The Boxed Statement

$$\boxed{\mathsf{CTT}_{\mathbb{M}}: \quad \forall D \in \mathfrak{D}\ \exists\ (U, p_D, E): U \text{ emulates } D \text{ at } (\tau, \delta) \text{ with poly overhead on all calibrated ranges.}}$$

where $\mathfrak{D}$ is the class of **admissible physical procedures**: finite, reproducible, locally causal; bounded energy/precision per step.

Equivalently: any $(\tau, \delta)$-computable transformation realised by an admissible device is $(\tau', \delta')$-computable by $U$ with $\tau', \delta'$ controllable by standard error-reduction.

### What Changes from Classical CTT

| Aspect | Classical CTT | $\mathsf{CTT}_{\mathbb{M}}$ |
|--------|--------------|--------------------------|
| Scope | All effectively calculable functions | Admissible physical procedures in $\mathfrak{D}$ |
| Claim type | Philosophical thesis | Measurable engineering standard |
| Output | Exact value | Measured triple $(y, \varepsilon_y, P_D)$ |
| Universality | Absolute | At $(\tau, \delta)$ on calibrated ranges |
| Overhead | Abstract polynomial | Measured polynomial with provenance |

### Admissibility Class $\mathfrak{D}$

$\mathfrak{D}$ is the set of admissible devices. Admissibility requires:
- **Finite:** bounded steps, bounded precision per step
- **Reproducible:** same inputs → same distribution of outputs within $\tau$
- **Locally causal:** no superluminal information; no hidden unbounded resources
- **Bounded energy/precision:** no infinite-precision encodings in the input/output

Devices that violate these conditions are not excluded from study — they are labelled INADMISSIBLE for $\mathsf{CTT}_{\mathbb{M}}$ and treated separately.

---

## 8. Special Device Classes

### Randomized Computation

Seed $\omega$ is captured in provenance $P_\omega$. $U$ emulates randomized devices via PRNG or sampling, preserving total variation within $\tau$.

### Analog Computation

Signals are discretised at finite resolution. Admissibility requires Lipschitz/energy bounds preventing super-TM encodings in noise. Analog devices that require infinite precision to specify inputs or read outputs are INADMISSIBLE.

### Quantum Computation

For finite-precision unitary dynamics and measurement, $U$ emulates to $(\tau, \delta)$ via quantum circuit simulation with polynomial overhead in time and exponential in qubits only if required by target accuracy.

Claims of super-Turing quantum power must specify **which admissibility guard is broken**. Until specified, they are UNDERDETERMINED.

### Oracles

Oracle access is treated as provenance — an external service. Emulation includes the same oracle. Oracle-augmented computation is not a claim of computation beyond $U$; it is a provenance-documented extension of the procedure.

---

## 9. Inadmissibility and Abstention

### When to Label INADMISSIBLE

- Device behaviour is unstable (non-reproducible beyond tolerance): label **INADMISSIBLE** for $\mathsf{CTT}_{\mathbb{M}}$
- Unbounded precision or energy required to specify inputs or read outputs: label **INADMISSIBLE**

### When to Label UNDERDETERMINED

- Super-Turing capability claimed without specifying which admissibility guard is broken: report **UNDERDETERMINED**

UNDERDETERMINED is not a verdict of impossibility — it is a principled suspension of judgment. The question cannot be resolved within the evidence supplied. This is the same admissible abstention as in ATT_56 (Halting: UNDERDETERMINED) and ATT_58 (Decoherence: INDETERMINATE).

---

## 10. Verification: The Emulation Residual

### Definition

Given test battery $\mathcal{B}$, the **emulation residual**:

$$R_{\text{emu}}(D \Rightarrow U) = \mathrm{median}_{(x,\omega) \in \mathcal{B}}\ d_{\mathbb{M}}\big(U(p_D, E(x);\omega),\ \mathsf{Proc}_{D,\theta}(x;\omega)\big)$$

with uncertainty bands across the battery.

### Corroboration Condition

Universality at $(\tau, \delta)$ is **corroborated** when:
- $R_{\text{emu}} \leq \tau$ across the test battery
- Failure rates $\leq \delta$ across perturbations of input $x$, control $\theta$, and environment

This is not a proof of universality — it is a corroboration relative to the test battery and committed parameters. Further testing may extend or restrict the corroborated range.

**Pillar IV:** the claim that a device falls within the universal emulation class is a useful engineering model, corroborated within a calibrated range. It is not a cosmic truth about the nature of computation.

---

## 11. CTT as Auditable Universality Principle

The Geofinitist $\mathsf{CTT}_{\mathbb{M}}$ transforms CTT from a philosophical claim about mind and computation into an **engineering standard**:

> *What counts as 'effective' is precisely what we can reproduce, emulate, and verify within finite tolerance on physical devices. The thesis is upheld to the degree that admissible devices fall into the same emulation class as $U$ under $\mathbb{M}$; departures must specify which guard (precision/energy/causality/reproducibility) they break.*

This shift makes the thesis:
- **Auditable:** any claimed failure of universality must specify which guard is broken
- **Testable:** corroboration is via measured emulation residual, not philosophical argument
- **Bounded:** claims hold within calibrated ranges, with committed $(\tau, \delta)$

---

## 12. Forward Collapse

When Geofinite constraints are relaxed toward the classical limit:

$$\varepsilon \to 0, \quad \text{budgets extend}, \quad \text{encoders/decoders become ideal}$$

- Output uncertainty $\varepsilon_y \to 0$: outputs become exact
- $(\tau, \delta) \to (0, 0)$: computability becomes exact and certain
- INADMISSIBLE and UNDERDETERMINED cases collapse to the classical domain
- $\mathsf{CTT}_{\mathbb{M}}$ reduces to classical CTT: every effectively calculable function is Turing-computable, every reasonable model is simulable with at most polynomial overhead

**The classical CTT is the forward collapse of $\mathsf{CTT}_{\mathbb{M}}$.** It is not wrong — it is the idealised limit. Admissible as an approximation where finite guardrails are negligible; inadmissible as a description of physically realisable computation.

---

## 13. All Five Pillars Applied

### Pillar I — Computation as Trajectory Through a Resource Manifold (secondary)

The resource manifold $M$ (time × memory × energy × precision) is the geometric container. A computation is a path through $M$. Computability is the question of whether a trajectory through $M$ can reach the output region within the accessible sub-manifold. Different physical substrates access different regions of $M$; emulation is convergence of trajectories within the manifold.

### Pillar II — Symbols Are Approximations (secondary)

Every output $y$ carries uncertainty $\varepsilon_y$. Every step operates within noise bounds $\sigma_t, \sigma_s$. The measured procedure $\mathsf{Proc}_{D,\theta}(x) \in \mathbb{M}$ is M = (v, ε, P) applied to computation. No symbol on any physical tape is exact; no computational output is context-free.

### Pillar III — Cascade of Scales (secondary)

The recursive structure $C_n = f(C_{n-1}, \Delta r)$ — computation at each scale built on the layer below — is Dynamic Flow applied to multi-scale computation. Classical CTT assumes one description fits all scales. Geofinitism preserves the layered structure: hardware, microarchitecture, algorithm, and application each contribute constraints and uncertainties.

### Pillar IV — CTT as Useful Fiction (primary)

CTT's claim of universal "effective calculability" is a useful fiction: valid within its formal domain (abstract machines, exact symbols, unbounded resources) but inadmissible as a physical claim about all possible computing devices. $\mathsf{CTT}_{\mathbb{M}}$ identifies the fictional boundary: universality is upheld within $\mathfrak{D}$; claims outside $\mathfrak{D}$ without specifying the broken guard are UNDERDETERMINED. The thesis becomes testable precisely because it names the boundary.

### Pillar V — Finite Quanta (primary)

Minimum time unit $\delta t > 0$ and minimum space unit $\delta s > 0$ bound all reasoning. Classical CTT assumes infinite tape and unlimited precision; both are useful fictions. $\mathsf{CTT}_{\mathbb{M}}$ keeps the finite guardrails in place: computability and universality are measured claims with provenance, tolerance, and resource profiles.

---

## 14. Summary

| Concept | Classical CTT | $\mathsf{CTT}_{\mathbb{M}}$ (ATT_57) |
|---------|--------------|--------------------------------------|
| Scope | All effectively calculable functions | Admissible devices $\mathfrak{D}$: finite, reproducible, locally causal, bounded |
| Computability | Binary: computable or not | $(\tau, \delta)$-computable within declared budgets and provenance |
| Output | Exact symbol string | Measured triple $(y, \varepsilon_y, P_D)$ |
| Universality | Absolute philosophical claim | Corroborated at $(\tau, \delta)$ on calibrated ranges |
| Overhead | Abstract polynomial | Measured polynomial with provenance |
| Super-Turing claim | Contested philosophically | UNDERDETERMINED until broken guard specified |
| Non-admissible device | No category | INADMISSIBLE for $\mathsf{CTT}_{\mathbb{M}}$ |
| Classical limit | The thesis itself | Forward collapse as $\varepsilon \to 0$, budgets extend |
| Status of CTT | Philosophical universal | Engineering standard — auditable, testable, bounded |

---

## Connections to Other Lessons

| Lesson | Connection |
|--------|-----------|
| ATT_40 | Church-Turing Thesis (survey): ATT_57 is the formal companion — ATT_40 applied Five Pillars conceptually; ATT_57 develops the full measured-procedure and $(\tau,\delta)$-computability machinery |
| ATT_56 | Geofinite Halting Thesis: both lessons reframe classical computability results using the same measured-procedure framework; UNDERDETERMINED (ATT_57) maps to UNDERDETERMINED (ATT_56) |
| ATT_48 | Liar Paradox: UNDERDETERMINED/INADMISSIBLE in ATT_57 are instances of the three-valued admissible abstention; all three domains (truth, halting, computability) share the same principled response to underdetermination |
| ATT_08 | Geofinitism — Measurement-First: $\mathsf{Proc}_{D,\theta}(x) = (y, \varepsilon_y, P_D; T, \varepsilon_T; S, \varepsilon_S)$ is M = (v, ε, P) applied to procedures; every computation carries provenance |
| ATT_28 | Commitment, Consensus, Admissibility: $(\tau, \delta)$ are committed parameters; $\mathfrak{D}$ is the admissibility class; INADMISSIBLE is the ATT_28 label applied to out-of-domain computation |
| ATT_58 | Quantum Decoherence: ATT_57's quantum model note (finite-precision unitary dynamics) connects to ATT_58's treatment; together they establish Geofinite accounts of both computation and quantum measurement |
| ATT_39 | P vs NP: ATT_39's resource-bounded complexity sits within the $\mathsf{CTT}_{\mathbb{M}}$ framework — complexity classes are regions of the resource manifold $M$ |

---

*Kevin R. Haylett — School of Geofinitism*  
*Simul Pariter.*
