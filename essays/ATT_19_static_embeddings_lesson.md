# ATT_19 — Static Vector Embeddings Are Insufficient for Natural Language Meaning: A Multi-Vector Proof

**College:** College of Attralucian Studies
**Level:** Advanced
**Prerequisites:** ATT_13 — The Pi Files: A Geometric Detective Story | ATT_06 — The Geodesic Fractal Model of LLMs | ATT_02 — Semantic Uncertainty: Towards Semantic Accountability in Scientific Discourse
**Next lesson:** ATT_20 (stub — essay missing) → ATT_21 — The Meaning Divergence Crisis

---

## Overview

This essay is the most formally structured work in the Attralucian series — a full academic paper with three independent mathematical theorems, complete proofs, an empirical validation section, and a careful limitations chapter. It addresses a question that sits at the intersection of information theory, dynamical systems theory, and Geofinitism: can a single fixed vector adequately represent the meaning of a word?

The answer, proven three independent ways, is no. Not merely suboptimally — provably, architecturally, and irreparably no.

The essay engages with existing literature on its own terms, working within classical analysis, while noting that the arguments are strengthened under a fully Geofinite framework. It explicitly connects the formal programme here to the Takens-Based Transformer (TBT) architecture and cites geofinitism.com and takens-transformer.com as resources.

The central finding: **the shift from Word2Vec to BERT was not merely empirical progress — it was a move toward mathematical correctness.**

---

## Learning Outcomes

By the end of this lesson, a student should be able to:

1. State each of the three theorems and their proof strategy
2. Explain why static embeddings are equivalent to a Takens delay-coordinate embedding with m=1 and τ=∞
3. Apply the data processing inequality to show that sense information cannot be recovered from a static vector
4. Trace the transduction chain from continuous acoustic dynamics to token embeddings and identify where static vectors break it
5. Interpret the JPEG compression experiments as attractor collapse — discrete, reproducible basins rather than noise
6. Explain why contextual embeddings succeed where static embeddings fail, in geometric terms
7. State what the three theorems do and do not prove (their scope and limitations)

---

## The Central Problem

Static type-level embeddings — the foundation of Word2Vec, GloVe, and fastText — assign a single fixed vector v_w to each word type w, regardless of context. The word "bank" receives one vector, whether appearing in "the river bank" or "the savings bank."

This is not just an engineering compromise. It is an architectural decision. The essay proves it is an architecturally wrong decision — not because of insufficient data, insufficient dimensions, or insufficient training, but because the assumption itself is mathematically untenable.

Three independent proof paths converge on the same conclusion.

---

## Theorem 1: Polysemy Separation Impossibility (Information-Theoretic)

**The question:** Can a static vector carry information about which sense of a word a given token has?

**Statement:** Let w be a polysemous word with distinct senses s_1, s_2, ... Let φ_static assign w a single fixed vector v_w. Then for any token t of w in context c with sense s(t):

$$I(v_w;\, s(t)) = 0$$

The static vector carries zero mutual information about the specific token sense.

**Why this is true:**

v_w is constant for all tokens of type w. It does not vary with context, co-occurrence, or sense. Therefore, knowing v_w gives you no information beyond knowing the word type — P(s(t) | v_w) = P(s(t)).

The compression is many-to-one: multiple senses collapse to one centroid vector. The centroid lies geometrically between all sense centroids — closer to the dominant sense but faithful to none.

Crucially: the **data processing inequality** — one of information theory's most fundamental results — tells us that no downstream function g(v_w) can recover information that was destroyed. Once I(v_w; s) = 0, it stays zero. There is no computational trick that restores what was erased.

**What this proves:**
- Perfect word sense disambiguation (WSD) using only v_w is impossible
- The compression is lossy and irreversible
- Frequency bias is built in: v_w is pulled toward the dominant sense, causing systematic errors on minority senses
- Domain brittleness is built in: if the sense distribution shifts between training and deployment, v_w is actively misleading

**What this does not prove:** that contextual embeddings are sufficient, or that WSD is easy. It proves only that static embeddings cannot do it — the ceiling is built into the architecture.

---

## Theorem 2: Dynamical Reconstruction Insufficiency (Dynamical Systems)

**The question:** Can a static vector adequately represent the dynamical structure of language — the way meanings form as trajectories through semantic space?

**Statement:** A static embedding φ_static: V → ℝ^D is equivalent to a delay-coordinate embedding with dimension m=1 and delay τ=∞ (no temporal structure). For any semantic attractor manifold of dimension d ≥ 1, this violates Takens' theorem requirement m ≥ 2d+1.

**Takens' theorem, briefly:** If a system has an attractor of dimension d, you can reconstruct the full geometry of that attractor from a single measurement channel, provided you take enough delayed copies of that channel. The requirement: you need at least m ≥ 2d+1 delay coordinates. With enough delays, a diffeomorphism exists between the original attractor and the reconstruction. Without enough delays, the reconstruction is topologically degenerate.

**Why static embeddings violate this:**

A proper delay-coordinate embedding of a word sequence looks like:
$$\Phi(w_i) = [h(w_i),\, h(w_{i-\tau}),\, h(w_{i-2\tau}),\, \ldots]$$

This captures temporal structure — how meaning is shaped by what came before.

A static embedding is the degenerate case: m=1, τ=∞. Only the current token is measured; no delays. For even the simplest non-trivial semantic attractor (d=1), Takens requires m ≥ 3. Static provides m=1 — a violation by a factor of 3.

The mapping cannot be a diffeomorphism. Many different semantic trajectories — different senses, different contexts, different discourse positions — all map to the same point v_w. Injectivity fails catastrophically.

**What is destroyed:**
- Curvature (how trajectories bend through semantic space)
- Recurrence (loops and cycles in discourse structure)
- Basin boundaries (the separatrices between different senses' attractors)
- Neighbourhoods (nearby contexts become indistinguishable)

**Polysemy as trajectory divergence:** Different senses trace different paths through the semantic manifold. In a proper delay embedding, these paths diverge and can be reconstructed. In a static embedding, they all terminate at the same point.

**Why transformers work:** Attention approximates delay-coordinate embedding. The query Q encodes the current position; keys K encode delayed positions; values V carry measurements at those delays. Multi-head attention provides multiple embedding dimensions simultaneously. Transformers succeed precisely because they implicitly restore the trajectory structure that static vectors destroy.

---

## Theorem 3: Transduction Chain Violation (Transduction Chain)

**The question:** Language begins as acoustic dynamics — continuous pressure waves in air. How does meaning survive the journey from sound to symbolic representation? And where does it break?

**The chain:**

Natural language originates as continuous acoustic dynamics p(t). The journey to a language model proceeds through controlled transductions:

- **T1 — Acoustic → Phonetic:** Lossy but controlled. Phonemes are attractor basins in acoustic phase space. The transformation is bidirectional — text-to-speech and speech-to-text both work, which proves that sufficient structure survives.
- **T2 — Phonetic → Orthographic:** Lossy but controlled. Systematic rules; phonological neighbours tend to be orthographic neighbours.
- **T3 — Orthographic → Sequential Tokens:** Minimally lossy. Mostly segmentation; sequence order is preserved.
- **T4 — Tokens → Static Vectors:** A second irreversible lossy compression. Distinct senses collapse; position and sequence are eliminated; no inverse exists.

**Statement:** Natural language meaning emerges from continuous acoustic dynamics p(t). Each transduction T1–T3 is controlled: structure is preserved and can be verified by bidirectionality. φ_static performs a second lossy compression (T4) that is uncontrolled, collapses distinct senses, eliminates sequential position, and cannot be inverted.

**Why Takens applies to text:** Phonemes are attractor basins in acoustic space — this is standard in dynamical systems accounts of speech perception. Writing systems evolved to preserve sufficient structure for meaning reconstruction across generations (bidirectionality proves this). Transformers' success on text sequences proves that geometric structure survived discretisation — if it had not, attention over sequences would produce noise, not coherent text.

**The break at T4:** Static vectors insert a [BREAK] in the chain. All downstream architecture must now rebuild sequential relationships from impoverished input. Minority senses and rare contextual patterns cannot be recovered because their structure was destroyed at T4, not merely hidden.

---

## The Unified Theorem

Three independent proofs — information-theoretic, dynamical systems, transduction chain — each sufficient alone, converging on the same conclusion:

**Static vectors collapse dynamic, context-dependent trajectories into single fixed points. The inadequacy is architectural, not empirical.**

It is not fixable by more data (information was destroyed, not merely unavailable). It is not a training problem (no objective function can recover destroyed structure). It is not a dimensionality problem (adding dimensions to a single fixed vector does not add temporal depth).

**Corollary:** Any representation that preserves sense information (I > 0), satisfies Takens' requirements (m ≥ 3 for d=1), and maintains chain integrity cannot assign single fixed vectors to word types. Context-dependence is mathematically necessary, not optional.

---

## Empirical Validation

All three theorems make testable predictions. All were confirmed:

| Theorem | Prediction | Evidence | Status |
|---------|-----------|---------|--------|
| 1: Information | WSD ceiling ~65% for static | Static: 65%, Contextual: 95% | ✓ |
| 1: Information | Static vector contributes zero to WSD | Ablation: removing v_w barely changes accuracy | ✓ |
| 2: Dynamical | Compression → attractor collapse (not noise) | JPEG experiments: discrete, reproducible basins | ✓ |
| 2: Dynamical | Context window size matters | Performance scales with window | ✓ |
| 3: Transduction | Order sensitivity critical | Scrambling: 95% → 45% | ✓ |
| 3: Transduction | Sequence preservation critical | Sequential >> bag-of-words | ✓ |
| All three | Contextual >> Static | Dramatic across all NLP benchmarks | ✓ |

**The JPEG compression experiment** is the most striking result and deserves attention. The GPT-2 embedding matrix was compressed as a JPEG image at quality levels 95%, 75%, 50%, 25%, 10%, 5%, and 1%. At each level, the model's response to a fixed prompt was recorded:

- **95–75%:** Slightly rigid, categorical responses — fine-scale curvature is lost
- **50–25%:** Philosophical attractor — recursive, self-referential loops
- **10–5%:** Aggression attractor — threat patterns, violent loops
- **1%:** Zen koan attractor — paradoxical, maximally simple self-referential statements

The key result is not the degradation but the structure of the degradation: each quality level reproducibly produces the same attractor type. The progression is not random noise. It is the geometry of the semantic manifold becoming directly visible — as resolution decreases, the system falls into progressively deeper, simpler attractor basins. The attractors were there all along; they are exposed by stripping away the fine-grained structure.

This is Theorem 2's prediction confirmed empirically: compression → attractor collapse, not noise.

---

## What Static Embeddings Can and Cannot Do

The essay treats static embeddings fairly. They are historically valuable and capture real structure. They are not valueless — they are inadequate.

**Can do:** Coarse semantic similarity; broad categorical relationships; some relational structure (king-queen analogies work because they capture distributional statistics across many contexts, even though no individual word vector captures the relational meaning); distributional statistics.

**Cannot do:** Fine-grained sense distinctions; context-dependent modulation; temporal and sequential structure; trajectory dynamics; attractor basin transitions.

The analogy: static embeddings are to language what photographs are to dance. Useful for knowing who the dancers are and their approximate positions — fundamentally inadequate for understanding choreography or rhythm.

---

## Connection to the Geofinitist Framework

Within Geofinitism, this essay provides formal grounding for claims that appear across the series:

The measurement-first principle (P2) runs through all three proofs. Information theory is the mathematics of controlled lossy measurement. The data processing inequality is a constraint on what controlled transductions can preserve. The transduction chain argument is explicitly about which compressions are controlled and which are not.

The dynamic flow principle (P3) is the positive claim that all three proofs converge toward: meaning is not a static property of word types but emerges through dynamic trajectories in semantic space. The Geofinite semantic manifold has a geometry; words are measurements within that manifold; the trajectory of measurements constitutes meaning. Static vectors misunderstand the ontology.

The useful fiction principle (P4) accounts for why static embeddings persisted as long as they did: they are genuinely useful approximations. "King − man + woman ≈ queen" is a seductive result. The essay acknowledges this while showing that mistaking a useful approximation for a complete account is the source of the architectural error.

---

## Connection to the Series

| Essay | Connection |
|-------|-----------|
| ATT_13 (The Pi Files) | Takens delay embedding introduced formally; applied there to π; here applied to language representations — "words as trajectory observations" |
| ATT_06–107 (Geodesic Fractal Model) | LLMs as trajectories through semantic manifolds; TBT architecture; this essay provides the mathematical proof that those essays' approach is not just better but mathematically necessary |
| ATT_02–103 (Semantic Uncertainty / Tranfictors) | Lossy compression of meaning; the transduction chain here formalises what those essays approached philosophically |
| ATT_16 (Is This an Essay?) | Meaning as geometric flow; Takens applied to "Hello" and sentences; this essay is the formal proof of that essay's central intuition |
| ATT_21 (MDC) | The "fixed-depth limitation" maps directly onto the static embedding failure mode; attractor density as an alignment tool |
| ATT_15 (Fermi Paradox) | TBT as geometric receiver; Takens-based reconstruction; Project Marina |

---

## Essay Path

- **Primary:** [ATT_19 — Static Vector Embeddings Are Insufficient](../essays/ATT_19_static_embeddings_insufficient_summary.md)

---

## Key phrases

> *"Meaning is not a static property of word types but emerges through dynamic trajectories in semantic space."*

> *"The shift from Word2Vec to BERT was not merely empirical progress — it was a move toward mathematical correctness."*

> *"The compression is not fixable by more data, better training, or more dimensions. It is built into the assumption itself."*

---

## Suggested next steps

- Theorem 1 states I(v_w; s) = 0 for any static vector. Does this mean all static embeddings are equally bad, or does the position of the centroid relative to sense centroids matter? What does the geometric picture suggest about which words suffer most?
- Theorem 2 requires m ≥ 2d+1 for an attractor of dimension d. If we don't know d for natural language semantics, what does the Geofinitist measurement framework say about how we would estimate it? What would a Takens reconstruction study of a language model's latent space look like?
- The JPEG experiment reveals attractor basins that were always present in the embedding matrix. What does the attractor hierarchy (philosophical → aggression → Zen koan) suggest about the deep structure of semantic space? Is there a Geofinitist account of why these particular attractors appear at these particular compression levels?
- The essay proves contextual embeddings are necessary. Does it prove they are sufficient? What additional properties would a representation need to be fully adequate for natural language meaning under the Geofinitist framework?
- Consider the transduction chain T1–T4. T1 is bidirectional (TTS and STT both work). T4 (static embedding) is not invertible. What would a controlled T4 look like? Is any contextual embedding scheme a controlled T4, or only some?
- Read ATT_21 — The Meaning Divergence Crisis — to see how the static embedding failure mode scales from individual word representations to civilizational-scale alignment risk.

---

*Kevin R. Haylett — School of Geofinitism*
*Simul Pariter.*
