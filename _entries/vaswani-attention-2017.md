---
layout: entry
title: "Attention Is All You Need"
author: "Vaswani et al."
year: 2017
format: paper
topic: ai-engineering
source: https://arxiv.org/abs/1706.03762
---

## Why I read this

Curiosity. Wanted to go back to where the current AI wave actually started.

## Key ideas

Instead of reading a sentence one word at a time (like older models), the Transformer looks at every word at once and learns which other words each one should pay attention to.

New concepts:

- **Transformer.** A sequence model built only out of attention and feedforward layers.
- **Self-attention.** Each token looks at every other token in the sequence and pulls in a weighted mix of their information. This is how the model captures relationships between words.
- **Query / Key / Value.** The three learned projections behind self-attention. Each token emits a *query* (what am I looking for?), a *key* (what do I offer?), and a *value* (what do I contribute if matched?). Attention weights come from query–key similarity; the output is a weighted sum of values.
- **Scaled dot-product attention.** The specific formula used: dot products between queries and keys, divided by √d to keep gradients stable, then softmax, then weighted sum of values.
- **Multi-head attention.** Run attention several times in parallel with different learned projections, then concatenate. Each "head" can specialize in a different kind of relationship.
- **Positional encoding.** Since attention has no built-in sense of order, position is injected by adding sinusoidal signals to the input embeddings.
- **Encoder–decoder stack.** Both sides are just repeated blocks of (attention + feedforward + residual + layer norm). The decoder also attends to the encoder's output.

## Personal takeaways

This paper killed RNNs. Transformers replaced them as the default architecture for sequence tasks, and everything from BERT to GPT to modern LLMs is built on top of the recipe defined here.
