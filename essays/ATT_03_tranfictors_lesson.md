# ATT_03 — Tranfictors: Measuring Semantic Precision

**College:** College of Attralucian Studies
**Level:** Intermediate
**Prerequisites:** ATT_02 — Words as Transducers | ATT_02 — Semantic Uncertainty and Accountability
**Next lesson:** ATT_04 (TBD — Essay 04)

---

## Overview

A tranfictor is what you get when a transducer compresses reality into a useful fiction. Every word does this — but with wildly different degrees of precision. This lesson introduces the fiction quality metric: a way of measuring how precisely a word maps to its referents, and by extension, how much decompression work the reader must supply to make it meaningful.

The lesson draws on Essays 01, 02, and 03, which form the founding trilogy of the word-model thread in the Attralucian series.

---

## Learning Outcomes

By the end of this lesson, a student should be able to:

1. Define a tranfictor and explain how it synthesises the Useful Fiction and Transducer models
2. Calculate or estimate fiction quality using the compression ratio formula
3. Give examples of high-, medium-, and low-quality tranfictors and explain why they differ
4. Describe the reader's role as active co-author in the decompression process
5. Use the SUA (from ATT_02) as a practical tool for measuring and documenting fiction quality
6. Connect fiction quality to LLM embedding stability

---

## The Tranfictor

> **Tranfictor** — A word that shapes observations into a precise linguistic fiction through transduction, with a measurable semantic quality determined by its compression ratio.

A tranfictor is the fusion of two models from Essay 01:

- **Useful Fiction** — a word is a simplified, context-dependent map of a complex territory
- **Transducer** — a word converts high-dimensional observations into a compressed linguistic signal

The fusion is precise: every word is simultaneously a fiction (it simplifies) and a transducer (it compresses). The quality of the fiction is determined by how much compression has occurred.

---

## Fiction Quality

The fiction quality metric runs from 0% to 100% and measures how precisely a word maps to its referents:

**Quality ≈ 1 − Compression Ratio**

where the Compression Ratio reflects the number of distinct referents a word can plausibly map to in a corpus.

| Word | Fiction Quality | Why |
|------|----------------|-----|
| cheetah | ~99% | One biological species; minimal ambiguity |
| chair | ~50% | 100+ referents (stool, throne, office chair, board chair...) |
| freedom | ~20% | Near-infinite interpretations; abstracts across philosophy, law, emotion |
| consciousness | ~10% | Entire fields of philosophy compressed into one noun |

**Key implication:** Low-quality tranfictors are not bad words — they are high-compression tools. But their use requires either context, qualification, or a Semantic Uncertainty Appendix (ATT_02) to become precise.

---

## The Reader as Co-Author

Meaning is not decoded — it is co-constructed. When a reader encounters "chair":

- In a boardroom → decompresses to "the person chairing the meeting"
- At a dining table → decompresses to "a wooden dining chair"
- In a physics lab → unlikely, requires explicit context

The reader's environment, knowledge, and expectations act as a **high-pass filter** — they add precision to the signal the writer compressed. This is internal transduction in action (ATT_01): the reader reconstructs the latent semantic geometry the word was pointing at.

High-quality tranfictors ("cheetah") require minimal reader decompression. Low-quality ones ("justice") require the reader to supply almost all the precision.

---

## The SUA as Falsifiability Tool

A Semantic Uncertainty Appendix (introduced in ATT_02) can be read as a direct measure of fiction quality:

- **A short, simple SUA** → high quality tranfictor (few ambiguities, narrow valid context)
- **A long, complex SUA** → low quality tranfictor (many ambiguities, wide drift, multiple valid contexts)

This makes fiction quality **falsifiable**: build the SUA, count the ambiguities and valid contexts, derive the compression ratio. The SUA transforms intuition about word precision into documented, checkable structure.

---

## LLM Implications

If fiction quality is real, LLMs should reflect it:

- High-quality tranfictors ("mitochondria," "cheetah") should embed more stably across contexts
- Low-quality tranfictors ("fairness," "consciousness") should show higher embedding variance across corpora and prompts
- Degradation experiments (compression artefacts applied to embeddings) should destabilise low-quality terms first

This is a testable prediction — one of the first falsifiable bridges between the Attralucian word models and the College of Machine Intelligence empirical programme.

---

## The Founding Trilogy

Essays 01, 02, and 03 form the first thematic cluster of the Attralucian series:

| Essay | Contribution |
|-------|-------------|
| ATT_01 — Words as Transducers | Establishes the five models; introduces transducer and useful fiction |
| ATT_02 — Semantic Uncertainty | Applies measurement uncertainty to scientific language; proposes the SUA |
| ATT_03 — Tranfictors | Synthesises the two models; introduces fiction quality metric |

---

## Essay Path

- **Primary:** [ATT_03 — Tranfictors](../essays/ATT_03_tranfictors_summary.md)
- **Foundation:** [ATT_01 — Words as Transducers](../essays/ATT_01_finite_models_of_words_summary.md)
- **Foundation:** [ATT_02 — Semantic Uncertainty](../essays/ATT_02_semantic_uncertainty_summary.md)

---

## Key phrase

> *"Words are not static symbols but dynamic transducers of finite fictions."*

---

## Suggested next steps

- Build a small SUA for a word from your own field and estimate its fiction quality
- Consider: what would it mean for an LLM to have a "fiction quality map" of its vocabulary?
- Read Essay 04 (ATT_04 — TBD) to continue the series

---

*Kevin R. Haylett — School of Geofinitism*
*Simul Pariter.*
