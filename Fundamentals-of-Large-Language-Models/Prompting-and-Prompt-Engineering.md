# 🧠 Lesson 3: Prompting in Large Language Models

---

## 💬 What Is Prompting?

Let’s revisit our familiar sentence:

> “I wrote to the zoo to send me a pet. They sent me a ___.”

As we know, an LLM computes a **distribution** over possible next words.  
Prompting refers to **how we can influence this distribution** — that is, how to make certain words more or less likely.  

There are **two main ways** to affect this distribution:
1. 🪄 **Prompting** – by changing the input text itself  
2. 🧠 **Training** – by adjusting the model’s parameters (we’ll cover this later)

---

## 🪄 Prompting: Changing the Input Text

Prompting is simply about **altering the content or structure of the input** passed to the model.  

Even small changes — like adding or removing a single word — can **significantly shift the probabilities** of the model’s vocabulary.

### 🐾 Example
If we modify our earlier prompt to:

> “I wrote to the zoo to send me a **little** pet. They sent me a ___.”

...the model might increase probabilities for **small animals** (🐭 “mouse,” 🐹 “hamster”)  
and decrease probabilities for **large animals** (🦁 “lion,” 🐘 “elephant”).  

That’s because during **pre-training**, the model learns statistical patterns — e.g., *“little cat”* appears far more often than *“little lion.”*  

---

## 🧱 How the Model Learns This

During **pre-training**, the LLM is shown **massive amounts of text** and learns to predict the next word in a sequence.  
Through this process, it learns:
- Common phrases and patterns (e.g., “little dog,” “big elephant”)  
- The likelihood of certain word combinations  
- General world knowledge 🧠  

So when we prompt the model differently, we’re indirectly tapping into these learned relationships.

---

## 🧠 What Is Prompt Engineering?

**Prompt engineering** is the process of **refining your input text** to guide the model toward a desired output.  

It’s often done **iteratively** — by experimenting with phrasing, context, or examples until the results look right.

However:
- ⚠️ It can be **unpredictable** — even small tweaks (like whitespace!) can drastically change output.
- 🌀 You might rephrase an input (e.g., “I wanted a pet, so I asked the zoo to send me one…”) and get a completely different response.

Despite the unpredictability, **prompt engineering can be extremely powerful** — especially for well-defined tasks.  
Many organizations and researchers use it to tune model behavior effectively.

---

## 🧩 In-Context Learning (a.k.a. Example-Based Prompting)

One of the most effective prompt engineering strategies is called **In-Context Learning**.  
Despite the name, this technique does **not** involve the model *learning* new parameters.

Instead, we construct a prompt that **shows examples** (called *demonstrations*) of the task before asking the model to complete a similar one.

### 📘 Example: *3-Shot Prompting* (from the GPT-3 paper)
Translate English to French:
```text
sea -> mer
book -> livre
computer -> ordinateur
chair ->
```

Here:
- The model sees **3 examples** (→ “3-shot prompting”)
- It learns from the **pattern** in the input
- It completes the final translation: `chair -> chaise`

---

### 🧮 Terminology Note

The term *prompt* is often **overloaded**:
- Sometimes it refers to the **entire input text** sent to the model.
- Other times it refers only to the **final query portion** (after examples).  

It’s important to be aware of how others use the term in different contexts.

---

## 🔢 K-Shot vs. Zero-Shot Prompting

| Type | Description | Example |
|-------|--------------|----------|
| 🧠 **Zero-Shot** | No examples, just instructions | “Translate ‘apple’ to French.” |
| 💡 **One-Shot** | One example + task | “cat -> chat, apple -> ” |
| 🧩 **K-Shot** | Several examples (k = number of demonstrations) | 3-shot example above |

Studies show that **including demonstrations** (1-shot or k-shot) often yields **better performance** than zero-shot prompting.

---

## 🧮 Examples of Different Prompt Styles

Let’s explore a few **real prompt examples** that highlight the variety of prompt engineering styles:

### 1️⃣ **Two-Shot Arithmetic Prompt**
```text
2 + 3: 5
4 + 5: 9
1 + 8:
```

🧠 The model doesn’t actually “compute” the sum — it learns from examples that numbers after `:` are expected answers.

---

### 2️⃣ **Instruction Prompt (from MPT-Instruct)**

Follow these instructions carefully. Be concise.

Instruction:

Write a SQL query to count the number of users registered in 2024.

Response:
This structure tells the model exactly what format and style to use.

---

### 3️⃣ **Long, Detailed System Prompt**
These were famously used in early Bing Chat and research examples.  
They often include detailed instructions like:
> “If you don’t know the answer, reply: ‘I’m not sure.’ Do not guess. Stay polite. Format output as markdown.”

Such prompts define the model’s **tone, constraints, and behavior**. 🎭

---

## 🔗 Advanced Prompting Strategies

### 🧵 Chain-of-Thought Prompting (CoT)

Introduced in 2022, **Chain-of-Thought prompting** encourages the model to **show its reasoning steps** for complex problems.

#### 🧩 Example:
> Q: If there are 3 red balls and 2 blue balls in a bag, and I add 4 more red balls, how many are red in total?  
>
> A: There are 3 red balls initially. I add 4 more, so 3 + 4 = **7 red balls**.

Instead of jumping to the answer, the model **writes intermediate reasoning steps**, leading to **more accurate multi-step reasoning**.

🧠 Why it works:
- The model might have seen **step-by-step reasoning examples** during pre-training.  
- Or, breaking a problem into smaller chunks makes it **easier for the model to handle**.

---

### 🪜 Least-to-Most Prompting

Another variant that builds on CoT — introduced in later research.

Here, the model solves **simpler subproblems first**, then uses those results to tackle **harder problems**.

🧮 Example:
Given words `["think", "machine", "learning"]`, concatenate the **last letters**.

- Step 1: “think” → **k**
- Step 2: “machine” → **e**
- Step 3: Combine → **ke**
- Step 4: “learning” → **g**
- Final: “ke” + “g” → **keg**

This incremental reasoning tends to improve accuracy compared to direct prompting.

---

### ⚛️ Concept-Based Prompting (DeepMind)

Researchers at **DeepMind** found that prompting models to **explicitly recall relevant concepts or formulas** improves their accuracy in subjects like physics and chemistry.

Example:
> “To solve this, recall Newton’s Second Law: F = ma.”

By prompting the model to state the *principles* first, it anchors its reasoning and produces better solutions. 🔬

---

## 🧾 Summary

| Concept | Description |
|----------|--------------|
| 🪄 **Prompting** | Influencing LLM output by modifying input text |
| 🧠 **Prompt Engineering** | Crafting inputs iteratively to improve outputs |
| 🧩 **In-Context Learning** | Showing examples within the prompt |
| 🧵 **Chain-of-Thought** | Guiding models to “show their reasoning” |
| 🪜 **Least-to-Most** | Solving simpler problems first |
| ⚛️ **Concept-Based** | Including principles or equations for scientific reasoning |

---

## ✅ Key Takeaways

- Prompting lets us control LLM behavior **without retraining**.  
- Small input changes can yield **big output differences**.  
- Prompt engineering is **both art and science** — sometimes unpredictable, but highly effective.  
- Advanced strategies like **Chain-of-Thought** and **Least-to-Most** prompting can unlock deeper reasoning abilities.  
