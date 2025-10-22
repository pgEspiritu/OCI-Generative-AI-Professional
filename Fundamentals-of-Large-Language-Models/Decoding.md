# Lesson: Decoding in Large Language Models

## Understanding Decoding

Let's return to the example we've seen a few times thus far:  
> "I wrote to the zoo to send me a pet. They sent me a--"

As we know, the LLM produces a **distribution over vocabulary words**. The question we're focused on now is:  
**How do we turn this distribution into a word or a sequence of words?**

Through this discussion, keep the following key ideas in mind:
- **Decoding is an iterative process** — text is generated *one word at a time*.
- After each word is produced, it is appended to the input, and the model recomputes the next distribution.
- The model does **not** emit full sentences or paragraphs all at once.

---

## Greedy Decoding

Once we compute the distribution over words in the vocabulary, how do we actually pick a word to emit?

The **simplest strategy** is called **greedy decoding**, where we simply select the word with the **highest probability**.

For example:

> "I wrote to the zoo to send me a pet. They sent me a—**dog**."

In greedy decoding:
1. The model selects “dog” (the highest probability token).
2. The word “dog” is appended to the input.
3. The process repeats until an **End Of Sentence (EOS)** token is generated.

The model then stops and returns:
> "I wrote to the zoo to send me a pet. They sent me a dog."

Greedy decoding is efficient and straightforward, but it can sometimes produce repetitive or overly predictable text.

---

## Non-Deterministic (Sampling-Based) Decoding

Greedy decoding isn’t the only option. There are **non-deterministic decoding strategies** that involve **random sampling**.

In these methods:
- Instead of always choosing the top word, we **sample** from the distribution — often favoring high-probability words.
- This allows the model to generate **more diverse** and sometimes more creative responses.

### Example:

Starting with the same input:

> "I wrote to the zoo to send me a pet. They sent me a—"

Instead of choosing the highest-probability word, we randomly sample among several likely options.

Let’s say we sample **“small”**.  
Then we append “small” and run the model again.

Next, we might sample **“red”**, and finally, the model outputs:
> "I wrote to the zoo to send me a pet. They sent me a small red panda."

This demonstrates how random sampling can yield interesting and unexpected combinations.

---

## The Role of Temperature

A crucial parameter in sampling-based decoding is called **temperature**.

### What Temperature Does:
- **Low temperature (< 1)** → sharpens the distribution, emphasizing the most probable words.  
  - Example: Higher chance of getting “dog.”
- **High temperature (> 1)** → flattens the distribution, increasing the chance of selecting rare words.  
  - Example: Unusual choices like “panther.”

Temperature affects **creativity vs. consistency**:
- **Low temperature:** closer to greedy decoding — more predictable, factual output.  
- **High temperature:** more diverse and creative, but also riskier or less coherent.

> 🧠 Note: Temperature changes the *shape* of the probability distribution, but not the *order* of word probabilities. The most likely word remains most likely; it just becomes more or less dominant.

---

## Choosing the Right Decoding Strategy

Different decoding methods serve different goals:

| Scenario | Ideal Method |
|-----------|---------------|
| Factual or Q&A tasks | **Greedy decoding** |
| Storytelling or creative writing | **Sampling with higher temperature** |
| Balanced factual and creative output | **Moderate temperature or nucleus sampling** |

---

## Common Types of Decoding

Below are the most common decoding strategies you’ll encounter:

1. **Greedy Decoding**  
   - Always picks the highest probability word.  
   - Fast and deterministic, but can produce dull or repetitive text.

2. **Nucleus Sampling (Top-p Sampling)**  
   - Samples only from the smallest subset of words whose cumulative probability exceeds *p* (e.g., 0.9).  
   - Produces coherent yet diverse text.

3. **Beam Search**  
   - Generates multiple candidate sequences simultaneously and keeps the highest-probability paths.  
   - Balances exploration and likelihood, producing higher-quality output than greedy decoding.

---

## Summary

Decoding is the process that converts the **distribution of possible next words** into actual text output.

- It happens **one word at a time**.
- Different strategies — like **greedy**, **sampling**, **temperature adjustment**, and **beam search** — produce different styles of text.
- The choice of decoding method depends on the desired trade-off between **accuracy, coherence, and creativity**.
