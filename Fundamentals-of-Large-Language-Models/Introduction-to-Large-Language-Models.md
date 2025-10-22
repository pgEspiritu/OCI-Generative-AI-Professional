# 🤖 Introduction to Large Language Models

## 🧠 What Is a Language Model?

A **language model** is a *probabilistic model of text*.  

To illustrate this, consider the sentence:

> “I wrote to the zoo to send me a pet. They sent me a ___.”

📚 This is the opening line of a children’s book.  
What a language model does is **compute a probability distribution** over its vocabulary to predict what word should fill in the blank.  

- 🧩 The model knows about a set of words (**vocabulary**).  
- 🎯 It assigns a **probability** to each possible word that could fit the blank.  
- 🔢 When we feed in a sequence of words, it computes a probability for *every single word* in its vocabulary — but none outside it.

---

## 💪 What Makes a Language Model “Large”?

**Large Language Models (LLMs)** are not fundamentally different from regular language models.  

The **“Large”** in *LLM* refers to the **number of parameters** in the model — the adjustable internal values that determine how the model behaves. ⚙️  
However, there’s **no universal threshold** defining when a language model becomes “large” or “extra-large.”

In general, when people talk about LLMs, they mean a **particular style** of model used for **text generation** 🗣️.  
That said, some smaller models (like **BERT**) are sometimes still called LLMs — even if they’re not particularly “large.”

---

## 💬 What Can LLMs Do?

We know that if we provide an LLM with a **sequence of text** (a prefix), it computes a **distribution over possible next words**.  

But there are some key questions 🤔:

1. 🎛️ Can we affect that distribution?  
2. 🧩 What mechanisms do we have for changing it?  
3. 🧾 How does this affect which words the model generates?

Once we have a probability distribution over text, we can use it to **generate new text** — sentences, paragraphs, or even full documents! ✍️

---

## 🧩 Key Topics in This Module

This learning module is structured around three main **technical areas**:

### 1️⃣ Architecture 🏗️
- How are these models built?  
- What do they look like under the hood?  
- What do their architectures imply about what they can do?

### 2️⃣ Affecting the Distribution 🎚️
We’ll explore two primary methods for influencing an LLM’s output:

- 🪄 **Prompting** — does *not* change the model’s parameters.  
- 🧠 **Training** — *does* change the model’s parameters.

### 3️⃣ Decoding 🔡
- **Decoding** is the process of generating text from an LLM.  
- It involves sampling from the model’s vocabulary in creative and structured ways to produce coherent text. 💬
---

## 🔍 Extensions and Research Directions

Finally, we’ll look at **extensions** of these core ideas and explore how researchers in academia and industry are advancing LLMs in **new and innovative ways**. 🧪✨

---

## ✅ Summary

In this module, we have:
- Defined what large language models are. 📘  
- Outlined the core topics: **architecture**, **prompting/training**, and **decoding**.  
- Previewed upcoming lessons that will dive deeper into these areas.


