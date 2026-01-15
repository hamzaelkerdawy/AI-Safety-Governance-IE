# LLM Processing Overview

## Perspective and Scope

## Perspective and Scope

This overview presents a high-level, non-technical explanation of how language models operate, intended to support safety, governance, and industrial risk analysis rather than technical implementation.


## Overview

When a text is provided to the model, it first converts all words (and in some models, sub-words, attached pronouns, and even spaces) into numerical representations that it can process. These numbers are represented as vectors.  

These vectors do not carry direct human-symbolic meaning, but instead encode statistical and geometric relationships between words based on how they appeared together in the training data. In this way, the values inside a vector reflect how close a word is to other words in a high-dimensional semantic space, not what the word explicitly “means” to a human.

---

## Positional Encoding

In addition to the token embeddings, the model adds a second vector representing the position of each word in the sentence (positional embeddings). This allows the model to distinguish between different word orders and understand sequence structure.

---

## The Attention Mechanism

The attention process then begins. Neural layers compute matrix multiplications on these vectors to produce three main matrices:

- Query (Q)  
- Key (K)  
- Value (V)  

These matrices allow the model to determine how much each word should attend to other words in the sequence, enabling it to infer contextual meaning. For example, the model can distinguish between the word “king” when used in chess and “king” when referring to a real monarch based on surrounding context.

---

## Logits and Probability Distribution

From all these computations, the model produces a single vector called logits, which represents raw numerical scores for how likely each possible next word is.  

A function called softmax is then applied to these logits, converting them into values between 0 and 1 whose total sum equals 1. These values represent the probability distribution over possible next words. The word with the highest probability is usually selected as the next output token.

---

## Key Conclusions

Two important conclusions follow from this process:

- The model does not “think” or “understand” in a human sense; it predicts the next word based on patterns learned from data.  
- The entire process is fundamentally a mathematical and statistical operation whose purpose is to rank and select one word over other possible words.
