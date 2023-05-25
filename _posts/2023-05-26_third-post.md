# Introduction to Transformer

## What is Transformer?

Transformer is a deep learning model architecture introduced in the paper "Attention Is All You Need" by Vaswani et al. (2017). It revolutionized natural language processing (NLP) tasks, particularly machine translation, and has since been adopted in various other domains.

## Key Concepts

### 1. Attention Mechanism
The Transformer model relies heavily on the attention mechanism. Attention allows the model to focus on different parts of the input sequence during processing. It assigns weights to different elements of the input, enabling the model to attend to the most relevant information at each step.

### 2. Self-Attention

In self-attention, the input sequence is transformed into queries, keys, and values. These representations are used to compute the attention weights that determine the importance of each position in the sequence.

Given an input sequence of length `L`, we can represent it as a matrix:

```
X = [x₁, x₂, ..., xᴸ]
```

To compute the queries, keys, and values, we project the input sequence into three different linear subspaces:

```
Q = XW_Q
K = XW_K
V = XW_V
```

Here, `W_Q`, `W_K`, and `W_V` are learnable weight matrices. The resulting `Q`, `K`, and `V` matrices have dimensions `L x d`, where `d` is the dimensionality of the projection.

Next, we compute the self-attention weights using the dot product between the queries and keys, scaled by a factor of `√(d)` to mitigate the effect of large values:

```
Attention(Q, K) = softmax((QKᵀ) / √(d))
```

This operation yields an attention matrix of size `L x L`, where each element `(i, j)` represents the attention weight between position `i` and position `j`.

We can then use the attention weights to compute a weighted sum of the values:

```
Z = Attention(Q, K)V
```

The resulting `Z` matrix has the same dimensions as `X` (`L x d`), and it represents the output of the self-attention mechanism.

To incorporate positional information, Transformer adds positional encodings to the input sequence. These encodings are added element-wise to the input embeddings and provide the model with information about the relative positions of the elements.

```
X̃ = X + P
```

Here, `P` is a matrix of positional encodings that has the same dimensions as `X`.

The self-attention mechanism in the Transformer architecture enables the model to capture dependencies between different words or positions within the input sequence. By attending to relevant information, the model can make more informed predictions and generate contextually appropriate output.

It's worth noting that the above description provides a simplified overview of self-attention in the Transformer model. The actual implementation may involve additional components, such as multiple attention heads and residual connections, to enhance the model's expressiveness and learning capabilities.

### 3. Encoder-Decoder Architecture
Transformer follows an encoder-decoder architecture. The encoder processes the input sequence, encoding it into a set of continuous representations. The decoder takes these representations and generates an output sequence, one step at a time. This architecture is commonly used in sequence-to-sequence tasks such as machine translation and text summarization.
<div align="center">
    <a href="./">
        <img src="images/Screen Shot 2023-03-23 at 04.27.53.png" width="40%"/>
    </a>
</div>
### 4. Positional Encoding
Since the Transformer model does not rely on recurrent or convolutional layers, it lacks the inherent notion of word order. To address this, positional encoding is introduced. Positional encoding provides the model with information about the relative positions of the words in the input sequence, enabling it to understand sequential relationships.

### 5. Multi-Head Attention
Transformer employs multi-head attention, where attention is computed multiple times in parallel. This allows the model to capture different types of dependencies and learn diverse representations. Multi-head attention enhances the model's ability to focus on different parts of the input and capture complex patterns.

## Applications

The Transformer model has been widely adopted in various NLP applications, including but not limited to:

- Machine Translation: Transformer achieved state-of-the-art performance on machine translation tasks, such as WMT 2014 English-German translation.

- Text Summarization: Transformer-based models have been successful in abstractive and extractive text summarization tasks.

- Language Modeling: Transformers have been used for language modeling tasks, generating coherent and context-aware text.

- Question Answering: Transformer models have shown promising results in question answering tasks, such as the Stanford Question Answering Dataset (SQuAD).

## Conclusion

The Transformer model has revolutionized the field of NLP by introducing the attention mechanism and self-attention. It has achieved impressive performance on various tasks and become the go-to architecture for many NLP applications. With its ability to capture long-range dependencies and model contextual information effectively, the Transformer continues to advance the state-of-the-art in natural language understanding and generation.
