# 🧠 Lesson: Training in Large Language Models

---

## 🎯 Prompting vs. Training

### Prompting
- **Definition:** Adjusting the *input* to an LLM to influence its output distribution.
- **Limitations:**
  - Highly sensitive — small prompt changes can cause large output differences.
  - The model’s **parameters remain fixed**, so control is limited.
- **Result:** Prompting can guide behavior but **cannot truly reprogram the model**.

### Training
- **Definition:** Changing the model’s parameters to alter its behavior fundamentally.
- **Purpose:** Used when prompting alone is insufficient, such as in **domain adaptation** (e.g., adapting a general model to a medical or legal domain).

---

## ⚙️ How Training Works

At a high level:
1. Provide the model with an **input** and an expected **output** (e.g., the next word or the correct answer).  
2. The model makes a **prediction**.
3. Based on the accuracy of its prediction, the model’s **parameters are updated** to improve future outputs.

After parameter updates, the **distribution over words** changes — ideally, in a way that improves performance.

---

## 🧩 Types of Training Approaches

There are several methods for modifying a model’s parameters, each with different costs and benefits.

### 1. Fine-Tuning
- **Description:** Traditional approach (around 2019).  
- **Process:** Take a pre-trained model (e.g., *BERT*) and train it on a **labeled dataset** for a specific task by updating **all parameters**.
- **Cost:** Expensive but effective.  
- **Usage:** Common before the era of massive LLMs.

---

### 2. Parameter-Efficient Fine-Tuning (PEFT)
Because full fine-tuning is costly, newer **cheaper alternatives** emerged.

- **Goal:** Train only a small subset of parameters or add a few new ones.  
- **Example Method:** **LoRA (Low-Rank Adaptation)**  
  - Keeps the original model parameters **frozen**.  
  - Adds small **trainable layers** that adjust behavior efficiently.  
- **Benefit:** Much cheaper and faster than full fine-tuning.

---

### 3. Soft Prompting
- **Concept:** Instead of modifying model parameters, add *learnable tokens* to the input prompt.
- These *soft prompts* act like specialized “virtual words” that steer the model toward a specific task.
- **Difference from regular prompting:**  
  - Regular prompts are fixed text.  
  - **Soft prompts are trained** — their embeddings are fine-tuned over time.
- **Cost:** Relatively low.

---

### 4. Continual Pretraining
- **Description:** Similar to fine-tuning (updates *all* parameters), but **does not require labeled data**.  
- **Process:** Feed the model large volumes of **unlabeled text** and train it to **predict the next word**.
- **Use Case:** Ideal for adapting a general model to a **new domain** (e.g., general → scientific text).  
- **Cost:** High — requires significant compute resources.

---

## 💰 Cost of Training

A variety of factors affect training cost:
- Training duration  
- Dataset size  
- GPU type and count  
- Model size and precision  

### Relative Cost Comparison
| Approach | Example | Typical GPU Use | Cost/Time | Notes |
|-----------|----------|----------------|------------|-------|
| **Text Generation** | Inference only | 1 GPU | Seconds | Cheap |
| **Parameter-Efficient Fine-Tuning (e.g., LoRA)** | Partial retraining | Few GPUs | Hours | Moderate |
| **Full Fine-Tuning** | BERT-level | Many GPUs | Days | Expensive |
| **Continual Pretraining** | Large-scale retraining | Hundreds–Thousands GPUs | Weeks | Extremely Expensive |

**Observation:**  
- Text generation is inexpensive.  
- PEFT methods are moderately costly.  
- Full fine-tuning and pretraining are **massively resource-intensive**.

---

## 🧠 Related Research: “Cramming”
A notable paper explores **training efficiency**, asking:

> “How far can you get if you have only one GPU and 24 hours to train a model?”

This experiment, called **cramming**, investigates how much progress is possible under extreme compute constraints — a recommended read for those interested in efficient model training.

---

## 🏁 Summary

| Concept | Description |
|----------|--------------|
| **Prompting** | Adjusts input text only — quick but limited. |
| **Training** | Changes model parameters — powerful but costly. |
| **Fine-Tuning** | Full retraining for specific tasks. |
| **PEFT (LoRA)** | Train only small, efficient subsets of parameters. |
| **Soft Prompting** | Learnable input tokens guide model behavior. |
| **Continual Pretraining** | Domain adaptation without labels, very compute-intensive. |
