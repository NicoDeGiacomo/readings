---
layout: entry
title: "Visualizing A Neural Machine Translation Model (Mechanics of Seq2seq Models With Attention)"
author: "Jay Alammar"
year: 2018
format: blog
topic: ai-engineering
source: https://jalammar.github.io/visualizing-neural-machine-translation-mechanics-of-seq2seq-models-with-attention/
---

## Why I read this

Filling in my mental map of how we got to modern AI. Seq2seq with attention is the step right before the Transformer, and seeing the problem attention was originally invented to solve makes everything that came after easier to follow.

## Key ideas

- A seq2seq model is two RNNs glued together: an encoder that reads the input (words turned into vectors via a word embedding) and a decoder that produces the output one token at a time.
- The encoder compresses the entire input into a single hidden state — the "context vector" — and hands it to the decoder. For long inputs this becomes a bottleneck: one fixed-size vector can't carry everything.
- Attention removes the bottleneck. The encoder passes *all* of its hidden states to the decoder, and at each output step the decoder does an extra step — scoring which input states matter most and using a weighted combination of them, effectively looking back at the relevant parts of the input.

## Personal takeaways

Scratched a curiosity I didn't know I had: how Google Translate actually worked back in the day. This is roughly the architecture behind it from 2016 onward, before Transformers took over.
