# ATT_25 — Complex Analysis as Takens Embedding: A Dynamical Systems Foundation for Analytic Functions

**College:** College of Attralucian Studies
**Level:** Expert (graduate-level mathematics assumed)
**Prerequisites:** ATT_24 — Complex Numbers as Dynamical Reconstruction | ATT_13 — The Pi Files: A Geometric Detective Story | ATT_09 — Geofinitism: Replacing the Ket with the Geofinitist Manifold | ATT_17 — Dissolution of the Riemann Hypothesis: A Phase-Space Reconstruction Approach
**Next lesson:** ATT_26 (TBD — Essay 26: Geometric Numbers III — Higher-Dimensional Unitary Roots)

---

> **Series note:** This is Geometric Numbers II — the formal technical companion to ATT_24 (Geometric Numbers I). Essay 24 established the foundational ontological claim: phase is relational delay; the complex plane is structurally equivalent to a minimal delay-coordinate reconstruction. This essay provides the formal mathematical proof programme. Both should be read together; Essay 24 first.
>
> **Forthcoming:** Kevin is developing Geometric Numbers III on higher-dimensional polynomial unitary roots. The current essay's framework will extend: the complex plane is the n=2 case; roots of unity provide the n-dimensional generalisation.

---

## Overview

Essay 24 established a foundational claim: complex numbers encode relational delay structure, not an independent imaginary dimension. The imaginary unit i is a rotational operator; phase is relational delay.

This essay proves it — rigorously, formally, and with full mathematical machinery.

The central new result: among all linear operators that can be expressed as weighted averages of delay operators, the Hilbert transform is the *unique* optimal choice. It preserves the L² norm of all signals, is orthogonal to the identity, and satisfies the Bedrosian time-frequency separation conditions. Given this optimality, every major theorem of complex analysis acquires a precise dynamical interpretation:

- The Cauchy-Riemann equations are conditions for the embedding to be conformal
- The Cauchy integral formula is a statement about determinism in the underlying dynamical system
- The Riemann mapping theorem is a dynamical normal-form theorem
- The imaginary unit i is the Hilbert operator — proven, not asserted

The programme then extends to nonlinear systems via the Koopman operator, and to non-stationary signals via synchrosqueezing as adaptive delay selection.

---

## Learning Outcomes

By the end of this lesson, a student should be able to:

1. State the Hilbert transform as an integral of delay operators and explain its significance
2. Prove that the Hilbert operator satisfies ℋ² = −I and relate this to i² = −1
3. State and interpret the theorem on analyticity as conformal embedding
4. State the Takens-Cauchy-Riemann theorem and explain what it says about delay embeddings
5. Reinterpret the Cauchy integral formula as a prediction theorem in dynamical systems terms
6. State the Riemann mapping theorem as a dynamical normal form and explain the connection to stability regions
7. Explain the Bedrosian theorem and the Takens-Bedrosian condition
8. Explain the Koopman operator and its connection to analytic embeddings of nonlinear systems
9. Explain synchrosqueezing as adaptive delay selection
10. Connect the results here to the forthcoming Geometric Numbers III programme on higher-dimensional roots

---

## From Essay 24 to Essay 25: What Changes

Essay 24 worked with the simplest delay pair:
$$X(t) = \bigl(x(t),\; x(t-\tau)\bigr)$$
and showed that this produces the essential structure of the complex plane.

Essay 25 asks a harder question: *which* delay, and *why*? Among all possible delay-based representations of a signal, what makes one better than another? The answer turns out to be the Hilbert transform — and once we see that the Hilbert transform is the optimal delay embedding, every major result of complex analysis becomes a theorem about dynamical systems.

The progression is:
- **Essay 24:** Discrete two-point delay → complex plane (structural equivalence asserted)
- **Essay 25:** Hilbert transform as continuum of delays → complex analysis (optimality proven; full theorems reinterpreted)
- **Essay 26 (forthcoming):** nth roots of unity as n-dimensional embeddings → geometric numbers programme

---

## The Hilbert Transform as a Continuum of Delays

The Hilbert transform of a signal x(t) is classically defined as:
$$\mathcal{H}[x](t) = \frac{1}{\pi} \text{P.V.} \int_{-\infty}^{\infty} \frac{x(\tau)}{t-\tau}\, d\tau$$

The key theorem — proven in this essay — reveals its deeper structure:

**Theorem:** The Hilbert transform admits the representation:
$$\mathcal{H}[x](t) = \frac{1}{\pi} \int_0^{\infty} \frac{x(t-\tau) - x(t+\tau)}{\tau}\, d\tau$$

This is not just a notational rearrangement. It reveals that ℋ[x](t) is a weighted average of **all** delay coordinates x(t−τ) and **all** advanced coordinates x(t+τ), with weight 1/τ (harmonic weighting — giving more influence to shorter delays).

Compare to Essay 24's two-point embedding (x(t), x(t−τ)): that was a single delay at a chosen τ. The Hilbert transform uses a *continuum* of delays, harmonically weighted. It is the infinite-delay-integral version of the discrete delay pair — and it is optimal.

This is the precise bridge between the elementary insight of Essay 24 and the full power of complex analysis.

---

## Analyticity as Conformal Embedding

**The Hilbert Embedding:** Define:
$$\Phi_{\mathcal{H}}[x](t) = \bigl(x(t),\; \mathcal{H}[x](t)\bigr) \in \mathbb{R}^2$$

This maps a real signal to a curve in the plane, using the signal and its Hilbert transform as the two coordinates.

**Theorem (Analyticity and Conformal Embedding):** The curve traced by Φ_ℋ[x] is the image of an analytic function f(t) = u(t) + iv(t) if and only if the embedding is *conformal* — it preserves angles between the tangent and normal directions to the curve.

**Corollary:** Analytic functions are precisely those whose Hilbert embeddings are locally conformal maps from the time axis into ℝ².

**Why this matters:** Conformal maps preserve local geometry — they stretch uniformly in all directions but do not shear. A conformal embedding is an *information-preserving* embedding. An analytic function is therefore precisely a function whose delay structure is non-distorting — it reconstructs the geometry of the underlying dynamics without introducing artefacts.

Analyticity, the core concept of complex analysis, is revealed as an embedding property — not a Platonic property of abstract functions.

---

## The Imaginary Unit as Proven Optimal Delay

**Theorem (Hilbert Operator as Phase Shifter):** For a pure sinusoid x(t) = e^{iωt} with ω > 0:
$$\mathscr{H}x = -ix$$

The Hilbert operator introduces a phase shift of −π/2, equivalently a time delay of π/(2ω) — a **quarter-period**.

**Proof:** ℋ[cos(ωt)] = sin(ωt) and ℋ[sin(ωt)] = −cos(ωt). In complex notation e^{iωt} = cos(ωt) + i sin(ωt):
$$\mathcal{H}[e^{i\omega t}] = \sin(\omega t) - i\cos(\omega t) = -i(\cos(\omega t) + i\sin(\omega t)) = -ie^{i\omega t}$$

**Corollary (the key result):** ℋ² = −I. Applying the Hilbert operator twice gives:
$$\mathscr{H}(\mathscr{H}x) = \mathscr{H}(-ix) = -i\mathscr{H}x = -i(-ix) = -x$$

So ℋ² = −I. The Hilbert operator is a square root of negative identity.

**This is i² = −1.** The mysterious algebraic fact of complex arithmetic is nothing more than: two successive quarter-period delays equal a half-period delay, which inverts the signal. No mysticism required.

**Optimality Theorem:** Among all linear operators expressible as weighted averages of delay operators, the Hilbert operator is the *unique* (up to scaling) operator satisfying:
1. **Norm preservation:** ‖ℋx‖_{L²} = ‖x‖_{L²} for all signals
2. **Orthogonality:** ⟨Ix, ℋx⟩ = 0 for all x (the signal and its quarter-period shift are uncorrelated at zero lag)
3. **Bedrosian separability:** ℋ[a(t)b(t)] = a(t)ℋ[b(t)] when spectra are separated

The complex plane is not an arbitrary two-dimensional space. It is the unique two-dimensional space generated by the optimal delay operator for oscillatory signals.

---

## The Major Theorems Reinterpreted

### Cauchy-Riemann as Dynamical Constraints

The Cauchy-Riemann equations for f(z) = u(x,y) + iv(x,y):
$$\frac{\partial u}{\partial x} = \frac{\partial v}{\partial y}, \qquad \frac{\partial u}{\partial y} = -\frac{\partial v}{\partial x}$$

**Takens-Cauchy-Riemann Theorem:** The delay embedding of x(t) yields an analytic curve if and only if the embedding satisfies a generalised Cauchy-Riemann condition in embedding coordinates.

**Interpretation:** The Cauchy-Riemann equations are not abstract conditions imposed on pairs of real functions. They are the conditions that ensure the delay embedding is conformal — that it preserves local geometry and does not distort the reconstruction of the underlying dynamics. They guarantee the embedding is information-preserving in the strongest sense.

### Cauchy Integral Formula as Prediction

The classical formula:
$$f(z_0) = \frac{1}{2\pi i} \oint_{\Gamma} \frac{f(z)}{z - z_0}\, dz$$

**Dynamical interpretation:** In phase-space reconstruction, Γ is a closed trajectory — a complete cycle of the system. The formula states that knowledge of the observable along a complete cycle determines its value at any interior point.

**This is a statement about determinism.** If you know the system's full trajectory around a cycle, you can predict its state at any interior point without further observation. The Cauchy kernel (z−z₀)⁻¹ is a weighting function averaging information from all cycle states — exactly as delay-coordinate embeddings use past observations to predict future states.

The Cauchy integral formula is Takens reconstruction applied to a closed orbit.

### Riemann Mapping Theorem as Dynamical Normal Form

**Classical statement:** Any simply connected proper subset U ⊂ ℂ can be conformally mapped to the unit disk 𝔻.

**Dynamical interpretation:** Any sufficiently well-behaved attractor (with appropriate topology) can be smoothly deformed into the simplest possible shape — the unit disk — while preserving the analytic structure of the dynamics.

This is exactly what normal form theory does in dynamical systems: find a coordinate transformation that simplifies the system to its canonical representative.

**Connection to stability:** In filter theory, the unit disk is the stability region — poles inside the unit circle give stable discrete-time systems. The Riemann mapping theorem therefore guarantees that any simply connected dynamical region can be mapped to the canonical stability region. Stability and analytic structure are the same thing, viewed from different angles.

---

## Bedrosian Theorem and Clean Amplitude-Phase Separation

**Theorem (Bedrosian, 1963):** If a(t) and b(t) have spectra supported on disjoint frequency intervals (a at lower, b at higher frequencies):
$$\mathcal{H}[a(t)b(t)] = a(t)\mathcal{H}[b(t)]$$

**Takens-Bedrosian Corollary:** When dynamics separate into slow amplitude variations (a(t)) and fast oscillations (b(t)), the Hilbert embedding factors cleanly:
$$\Phi_{\mathcal{H}}[a(t)b(t)] = \bigl(a(t)b(t),\; a(t)\tilde{b}(t)\bigr)$$

The amplitude a(t) modulates the entire embedding, preserving the circular structure of the fast oscillation.

**Why this explains the analytic signal:** The representation z(t) = a(t)e^{iφ(t)} works cleanly — amplitude and phase genuinely separate — when the Bedrosian condition holds. When signals have overlapping spectra, the separation is distorted. This gives a precise, measurement-based criterion for when the complex representation is trustworthy and when it introduces artefacts.

---

## Koopman Operator: Extension to Nonlinear Systems

Everything above applies to linear systems. The Koopman operator extends the framework to nonlinear dynamics.

**Definition:** For a dynamical system φt: M → M, the Koopman operator 𝒦t acts on observable functions g: M → ℂ by:
$$({\mathcal{K}}_t g)(x) = g(\phi_t(x))$$

The Koopman operator is linear — even when the underlying dynamics φt are nonlinear. This is the Koopman trick: linearise the system by lifting from state space to function space.

**Theorem:** When Koopman eigenfunctions have purely imaginary eigenvalue λ = iω, they satisfy:
$$\psi(x(t)) = \psi(x(0))e^{i\omega t}$$
The real and imaginary parts of ψ are Hilbert transform pairs along trajectories of the system.

**Consequence:** Koopman eigenfunctions provide the natural coordinates for analytic embeddings of nonlinear systems. The entire complex-analysis-as-Takens-embedding programme generalises from linear to nonlinear dynamics via the Koopman operator.

This is significant: it means the geometric structure uncovered in Essays 24–25 is not limited to linear oscillators. Any dynamical system with Koopman eigenvalues on the imaginary axis has an analytic embedding — complex analysis governs its geometry.

---

## Synchrosqueezing: Adaptive Delay Selection

The Hilbert transform uses a fixed quarter-period delay — optimal for stationary signals with a single frequency. For non-stationary signals (chirps, signals with changing frequency), a fixed delay is suboptimal.

The **synchrosqueezing transform** generalises this by adaptively selecting the local optimal delay based on instantaneous frequency:
$$\omega(a,b) = \frac{\partial}{\partial b} \arg(W_f(a,b))$$
where Wf(a,b) is the continuous wavelet transform.

**Interpretation in the Geofinite framework:** Synchrosqueezing is adaptive Takens embedding — at each moment, it selects the delay that best preserves the local oscillatory structure. It is the natural extension of the Hilbert framework to signals whose optimal reconstruction delay changes over time.

This opens the possibility of a fully adaptive version of the geometric numbers programme — one where the "imaginary unit" is not a fixed operator but adapts to the local dynamics of the system being measured.

---

## The Full Picture: What Complex Analysis Is

The essay closes with five conclusions that collectively redefine what complex analysis is:

**1.** Complex numbers are not imaginary. They are the natural coordinates for representing oscillatory phenomena with a quarter-period delay between coordinates.

**2.** Analyticity is an embedding property. A function is analytic when its delay embedding is conformal and information-preserving.

**3.** The Cauchy-Riemann equations are dynamical constraints. They ensure the embedding preserves local angles and orientation.

**4.** The Hilbert transform is nature's optimal delay. Uniquely preserves energy, orthogonality, and time-frequency separation.

**5.** Complex analysis is the linear theory of oscillatory dynamical systems. Just as Fourier analysis handles linear time-invariant systems, complex analysis handles systems with a well-defined analytic (Hilbert) embedding.

> *"Complex analysis is precisely the study of dynamical systems under a specific, optimal delay embedding."*

---

## Connection to the Series

| Essay | Connection |
|-------|-----------|
| ATT_24 (Geometric Numbers I) | Foundational ontological claim proven here; discrete delay pair extended to Hilbert continuum |
| ATT_13 (The Pi Files) | Takens theorem stated and applied formally; the theorem cited here (Takens 1981) is the same one applied informally throughout the series |
| ATT_17 (Riemann) | Complex argument of ζ(s) now has precise formal interpretation; zeros as destructive interference in conformal relational structure; the reframing here grounds Essay 17's claims |
| ATT_09 (Ket Limit) | Koopman operator connects directly to Hilbert-space quantum formalism; this essay provides the dynamical systems foundation for Essay 09's reinterpretation |
| ATT_19 (Static Embeddings) | Hilbert transform as optimal Takens embedding is the formal justification for why contextual representations are necessary; static embeddings are m=1 approximations |
| ATT_23 (Generon) | Hilbert transform as a specific Generon — an unbounded Generon operating as an infinite delay integral; Koopman eigenfunctions as the natural Generons for nonlinear systems |
| Essay 26 (forthcoming) | Geometric Numbers III — roots of unity as n-dimensional embeddings; the complex plane as the n=2 case |

---

## Essay Path

- **Primary:** [ATT_25 — Complex Analysis as Takens Embedding](../essays/ATT_25_complex_analysis_takens_embedding_summary.md)
- **Companion:** [ATT_24 — Complex Numbers as Dynamical Reconstruction](../essays/ATT_24_complex_numbers_dynamical_reconstruction_summary.md) (read first)

---

## Key phrases

> *"Complex analysis is precisely the study of dynamical systems under a specific, optimal delay embedding."*

> *"The imaginary unit i is not a mystical 'imaginary' number but the abstract representation of the Hilbert operator, which advances signals by a quarter-period delay."*

> *"The property i² = −1 is simply the statement that two successive quarter-period delays equal a half-period delay, which inverts the signal."*

> *"The Hilbert transform is nature's optimal delay."*

---

## Suggested next steps

- Prove the Hilbert operator result ℋ² = −I directly from the action of ℋ on cos(ωt) and sin(ωt). Then interpret: what does "applying i twice" mean geometrically in the reconstructed phase space?
- The Optimality Theorem says the Hilbert operator is the unique operator satisfying three conditions. Which of these three conditions is most fundamental? Could you weaken one without losing the key structure? What would the resulting operator look like?
- The Cauchy integral formula is reinterpreted as a prediction theorem: knowing the system on a full cycle determines interior points. What does this say about the information content of a cycle relative to its interior? Is this a form of the data processing inequality from Essay 19?
- The Bedrosian condition requires spectrally separated amplitude and carrier. What happens to the analytic signal representation z(t) = a(t)e^{iφ(t)} when the Bedrosian condition fails — when amplitude and carrier overlap in frequency? What artefacts appear? How does this connect to the uncertainty ε in the Measured Number framework?
- The Koopman operator linearises nonlinear dynamics in function space. In what sense is a Koopman eigenfunction with λ = iω a "Generon" in the sense of Essay 23? What is its Q, A, δ, q₀, F?
- Consider the forthcoming Part 3: if the complex plane is the n=2 case of a general programme, what do you expect the n=3 and n=4 cases to look like? What physical or mathematical systems would they describe? Do quaternions arise from n=4?

---

*Kevin R. Haylett — School of Geofinitism*
*Simul Pariter.*
