# ATT_06 — The Geodesic Fractal Model of LLMs

**College:** College of Attralucian Studies
**Level:** Advanced
**Prerequisites:** ATT_01 — Words as Transducers | ATT_04 — Time as Ordered Compression | ATT_05 — The Fractal Scaling Problem
**Next lesson:** ATT_07 (TBD — Essay 07)

---

## Overview

This lesson provides the formal mathematical grounding for Geofinitism's treatment of LLMs as dynamical systems. It takes three ideas from earlier in the series — words as transducers, compression as ordered distinction, and fractal growth/decay — and formalises them into a single coherent picture: transformer generation as a piecewise geodesic walk on a learned Riemannian manifold, with attention performing Takens-style delay-coordinate embeddings and the Fisher information metric governing the geometry of semantic sensitivity.

This is the mathematical backbone connecting the Attralucian word models to the College of Machine Intelligence empirical programme.

---

## Learning Outcomes

By the end of this lesson, a student should be able to:

1. State the closed-loop generation equations and explain what each term represents
2. Interpret attention as a Takens-style delay-coordinate embedding
3. Define the Fisher information metric and explain what it measures
4. Describe geodesic token selection and how it relates to next-token prediction
5. Explain why the transformer landscape appears fractal and what observable consequences follow
6. Apply the three practical diagnostics: Fisher-Rao length, curvature, attractor probing

---

## The Closed-Loop System

LLM generation is not a feed-forward process — it is a closed loop. The token chosen at each step becomes the next input:

**x_{t+1} = Φ_θ(x_t, e_{t+1})**
**w_{t+1} ~ p_θ(· | x_t)**
**e_{t+1} = E(w_{t+1})**

where Φ_θ is the full transformer stack and E is the embedding function. The output feeds back into the input — this is what makes it a dynamical system.

In the continuous-depth limit (residual blocks becoming infinitesimally thin), this becomes a **Neural ODE**:

**dx/dℓ = f(x, ℓ; θ)**

The state flows continuously through representation space under the learned vector field f.

---

## Attention as Delay-Coordinate Embedding

Self-attention is:

**Attn(X) = softmax(QK^T / √d_k) · V**

Viewed dynamically, each position attends to all prior positions — building a context-dependent coordinate chart from pairwise similarities. This is a **Takens-style delay-coordinate embedding**: the sequence history is unfolded into a higher-dimensional phase space, reconstructing the attractor geometry of the underlying language dynamics.

The result is a coordinate chart:

**x_t = Ψ_θ(e_{1:t})**

The current state is fully determined by the sequence history — no external hidden state required. This is Takens' theorem applied to language.

---

## The Learned Manifold and its Metric

Training shapes a representation manifold **M ⊂ ℝ^d** where nearby points encode semantically coherent continuations.

The natural metric on this manifold is the **Fisher information**:

**G(x) = E_{y ~ p_θ}[∇_x log p_θ(y|x) · ∇_x log p_θ(y|x)^T]**

This measures **semantic sensitivity**: how much does the predicted distribution change when the state moves? High G(x) means small moves in state space produce large changes in predicted meaning — the region is semantically sharp. Low G(x) means the predictions are insensitive — the region is semantically flat.

---

## Geodesic Token Selection

Given the cross-entropy loss L(x) = −log p_θ(w* | x), the **natural gradient** step:

**Δx ∝ −G(x)^{−1} ∇_x L(x)**

is the steepest descent direction under the Fisher metric — not Euclidean space. Integral curves of this field approximate **geodesics** of (M, G): the shortest paths toward regions of higher next-token likelihood.

In practice, choosing w_{t+1} and re-embedding it implements a **piecewise geodesic walk**:

**x_t → (token choice) → x_{t+1} = Φ_θ(x_t, E(w_{t+1}))**

Each generation step is one segment of a path through semantic space, guided by the geometry of the manifold.

---

## The Fractal Landscape

Piecewise-linear activation functions (ReLU/GeLU) and softmax partition ℝ^d into exponentially many linear regimes. Context-dependent attention gates induce **self-similar, multi-scale tilings** — and these compose across layers and heads into a **fractal-like semantic energy landscape**:

- **Ridges**: high-probability filaments — coherent, fluent continuations
- **Basins / attractors**: repetitions, clichés, topic loops
- **Bifurcations**: qualitative changes as sampling parameters cross thresholds
- **Chaotic regions**: small prompt differences leading to divergent trajectories

This is directly observable:

| Observable | Dynamical interpretation |
|-----------|-------------------------|
| Repetition loops | Fixed point / limit cycle attractor |
| Rhyme and rhythm | Periodic orbit in phonetic-semantic space |
| Hallucination | Basin shift into a low-fidelity attractor |
| Prompt sensitivity | Chaotic region — Lyapunov divergence |

---

## Practical Diagnostics

Three measurables ground this model empirically:

**Fisher-Rao length**: L_FR = Σ_t √(Δx_t^T G(x_t) Δx_t)
Total semantic distance traversed during a generation — longer paths indicate more varied, exploratory output.

**Curvature**: κ_t ≈ ‖x_{t+1} − 2x_t + x_{t-1}‖ / ‖x_t − x_{t-1}‖²
Measures how sharply the trajectory bends at each step — high curvature signals topic shifts or bifurcations.

**Attractor probing**: vary temperature T, measure return times to n-gram loops.
Maps the basin structure: which attractors are dominant, how deep, how wide.

---

## Connection to the Series

| Earlier essay | Connection |
|--------------|-----------|
| ATT_01 (Transducers) | Attention as delay-embedding completes the formal connection between word-as-transducer and transformer architecture |
| ATT_03 (Tranfictors) | Fiction quality maps onto the Fisher metric: high-quality tranfictors occupy sharp, high-G(x) regions of the manifold |
| ATT_04 (Time) | Generonic distinction cost ↔ geodesic step cost; ordered compression ↔ piecewise geodesic walk |
| ATT_05 (Fractal Scaling) | The fractal landscape explains LLM thrashing — same structure as cognitive overload, formalised geometrically |

---

## Essay Path

- **Primary:** [ATT_06 — The Geodesic Fractal Model of LLMs](../essays/ATT_06_geodesic_fractal_llm_summary.md)

---

## Key phrase

> *"Attention computes pairwise delay-embeddings, giving coordinates. Decoding follows piecewise geodesics, navigating a fractally tiled landscape shaped by training."*

---

## Suggested next steps

- Examine: where does the Fisher-Rao length spike in a generation you have seen degrade?
- Consider: if hallucination is a basin shift, what would "alignment" mean geometrically?
- Read Essay 07 (ATT_07 — TBD) to continue the series

---

*Kevin R. Haylett — School of Geofinitism*
*Simul Pariter.*
