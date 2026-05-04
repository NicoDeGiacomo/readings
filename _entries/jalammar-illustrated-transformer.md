---
layout: entry
title: "The Illustrated Transformer"
author: "Jay Alammar"
year: 2018
format: blog
topic: ai-engineering
source: https://jalammar.github.io/illustrated-transformer/
---

## Why I read this

Filling in my mental map of how we got to modern AI. The Transformer is the architecture every current LLM is built on, and walking through it visually is the cleanest way to understand why it replaced RNNs.

## Key ideas

- A Transformer is a stack of encoders feeding a stack of decoders. Each encoder is a self-attention layer followed by a feed-forward layer; each decoder is the same with an encoder-decoder attention layer wedged between, so it can attend to the encoder's output.
- Self-attention derives three vectors per word — Query, Key, Value — from the input embedding via trained matrices. For each position, the model scores its Query against every Key, softmaxes the scores, and takes a weighted sum of the Values. The whole thing is matrix multiplication, so all positions are processed in parallel — the property that let Transformers scale where RNNs couldn't.
- Multi-head attention runs several self-attention computations in parallel, each in its own "representation subspace," then concatenates the results. This lets the model attend to different kinds of relationships at once instead of collapsing them into one set of weights.

## Personal takeaways

Best read before or alongside [*Attention Is All You Need*]({% link _entries/vaswani-attention-2017.md %}) — the visuals make the paper much easier to follow.
