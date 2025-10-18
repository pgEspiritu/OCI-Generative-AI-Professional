# 🧱 Lesson 2: Understanding LLM Architectures

In this lesson, we’ll talk about **LLM architectures** — focusing on two major types:

1. 🧩 **Encoders**
2. 🔡 **Decoders**

These two architectures correspond to two important capabilities of language models:

- ✴️ **Embedding**
- 🗣️ **Text Generation**

Before diving deeper, remember that **both encoders and decoders** are built on a foundational structure called the **Transformer**.

---

## ⚙️ What Is a Transformer?

The **Transformer architecture**, introduced in the landmark 2017 paper *“Attention Is All You Need”*, completely revolutionized Natural Language Processing (NLP) and machine learning.  

While we won’t go into the full details of the Transformer here, there are plenty of great tutorials available if you’d like to explore this architecture further. 💡

---

## 🧠 Encoders vs. Decoders — The Basics

| Architecture | Purpose | Example Models | Key Use Case |
|---------------|----------|----------------|--------------|
| **Encoder** | Converts text into numerical **embeddings** | BERT, RoBERTa | Classification, Search, Semantic Similarity |
| **Decoder** | **Generates text** token by token | GPT-4, Llama, Cohere Command | Text Generation, Chatbots, Summarization |
| **Encoder-Decoder** | Combines both for sequence-to-sequence tasks | T5, BART | Translation, Summarization, Complex NLP Pipelines |

---

## 🪄 What Are Text Embeddings?

When we talk about *embedding text*, we’re referring to converting a sequence of words into a **vector (or a sequence of vectors)** — a **numerical representation** that captures the *meaning* (semantics) of the text.  

For example, given the input:

> “They sent me a ...”

An encoder model like **BERT** produces:
- A **vector for each word**, and  
- A **vector for the whole sentence** 🧭  

These embeddings can be used for:
- 🔍 **Semantic search** — finding similar documents in a corpus  
- 🏷️ **Classification** or **regression** tasks  
- 🧩 **Clustering** or **recommendation systems**

---

## 🧩 Encoders in Action

Let’s walk through an example of how an **encoder** like **BERT** works:

1. 📥 Input text: `"They sent me a"`
2. 🧠 The model converts each token into an **embedding vector**
3. 🧮 These vectors represent semantic meaning
4. 📤 These embeddings are then used by downstream models or systems (e.g., search, categorization, etc.)

For **semantic search**, you might:
- Encode all documents in a database  
- Encode the user’s query  
- Compare vectors to find the *most similar* document 🧷

---

## 💬 Decoders: The Text Generators

Now let’s talk about **decoders**, such as **GPT-4**, **Llama**, or **Cohere Command**.

Decoders take a **sequence of tokens** and **predict the next token** based on their internal probability distribution — exactly as discussed in Lesson 1.

🧩 **Key characteristic:**  
A decoder **only generates one token at a time**!  

To generate a full sequence:
1. Feed in an initial text (prompt).  
2. The model outputs the **next token**.  
3. Append that token to the input and feed it back in.  
4. Repeat until the full sequence is generated. 🔁  

💡 While powerful, this process can be **computationally expensive**, especially for very large models.

> 📝 Typically, **decoders** are *not* used for embedding tasks — that’s the job of **encoders**.

---

## 🚀 Why Are Decoders So Popular?

Decoders have shown **remarkable fluency** in:
- Generating coherent, human-like text ✍️  
- Answering questions ❓  
- Engaging in dialogue 💬  
- Performing reasoning tasks 🧮  

They’re the backbone of today’s conversational AI systems — including models like ChatGPT.

---

## 🔄 The Hybrid: Encoder–Decoder Models

**Encoder–Decoder models** combine the strengths of both architectures.  
They’re especially effective for **sequence-to-sequence** tasks like **translation**. 🌐

Here’s how it works:
1. 🧠 The **encoder** processes input text (e.g., English sentence) and converts it into embeddings.  
2. 🔡 The **decoder** takes those embeddings and generates the translated text (e.g., in French).  
3. 🔁 The decoder generates one token at a time, feeding its own outputs back into the sequence until completion.

---

## 📊 Model Size and Scale

In LLMs, **size** refers to the number of **trainable parameters**.  

A few key observations:
- ⚖️ **Decoder models** are usually much **larger** than encoders.  
- 📈 The **y-axis** in most parameter-count charts grows **by orders of magnitude**, not linearly.  
- 🧮 Bigger isn’t always better — small models can perform surprisingly well with clever training techniques.

Recent research shows that with smarter methods, **smaller models** can still generate fluent, high-quality text! 💡✨

---

## 🧾 Choosing the Right Architecture

At a glance, here’s a quick guide on which model type is typically used for each task:

| Task | Encoder | Decoder | Encoder-Decoder |
|------|----------|----------|----------------|
| Text Classification | ✅ | ❌ | ✅ |
| Text Generation | ❌ | ✅ | ✅ |
| Translation | ❌ | ❌ | ✅ |
| Semantic Search | ✅ | ❌ | ❌ |
| Summarization | ❌ | ✅ | ✅ |
| Dialogue / Chatbots | ❌ | ✅ | ✅ |

> ⚠️ Note: Any model *could* theoretically perform any task, but not all combinations are efficient or commonly used.

---

## ✅ Lesson Summary

- 🧩 **Encoders** convert text into embeddings.  
- 🔡 **Decoders** generate text, token by token.  
- 🔀 **Encoder–Decoder** models combine both for translation and sequence tasks.  
- ⚙️ All are built upon the **Transformer** architecture.  
- 🧮 Model **size** (parameters) varies widely, with decoders often being the largest.  
© 2025 Oracle University  
[🔒 Privacy / Do Not Sell My Info](#) · [📞 Contact Us](#) · [📜 Terms of Use](#) · [🍪 Cookie Preferences](#) · [⚙️ Ad Choices](#)
