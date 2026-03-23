# Negation-Aware Image Retrieval

## 🚀 Overview

Modern vision-language models such as CLIP perform well on descriptive queries but often fail when handling **negation** (e.g., “an image of an animal that is not a dog”). These models tend to retrieve images matching dominant concepts rather than respecting logical constraints in language.

This project explores a method to enable **negation-aware image retrieval**, improving text-to-image search by correctly identifying and excluding negated concepts.

---

## 🎯 Problem Statement

Given a natural language query containing negation:

> "an image of an animal not a dog"

Standard retrieval systems often return images **containing the negated concept**, indicating a lack of proper negation understanding.

The goal of this project is to:

- Identify the **negated concept** in a query  
- Retrieve images based on **positive concepts only**  
- Improve robustness of retrieval systems to **logical constraints in language**

---

## 🧠 Key Idea

Instead of relying on training or fine-tuning large models, this project investigates whether:

> **Negation signals already exist in pretrained language models and can be extracted in a zero-shot manner**

---

## 🏗️ Pipeline Overview

1. Parse input query  
2. Identify candidate concepts  
3. Detect the negated target  
4. Retrieve images using positive concepts  
5. Re-rank or filter results accordingly  

---

## 🔬 Results

- Successfully identifies negated concepts across:
  - Object-level queries  
  - Contextual negation  
  - Fine-grained semantic distinctions (e.g., adult vs child)

- Demonstrates strong performance compared to:
  - Large pretrained encoders (non-task-specific)
  - Supervised NLI models (as a reference baseline)

- Improves retrieval quality in cases where standard CLIP fails

---

## ⚠️ Limitations

- Performance degrades when negated concepts are expressed as **compositional phrases** (e.g., “basket on it”)  
- Negation signals become less localized in longer or more complex sentences  

---

## 🧪 Example Queries

- "an image of an animal that is not a dog"  
- "a fridge without fruits"  
- "a boat not in the ocean"  
- "people playing in a park not children"  

---

## 🛠️ Tech Stack

- Python  
- PyTorch  
- HuggingFace Transformers  
- CLIP (Vision-Language Model)  

---

## 📊 Motivation

Negation is a fundamental component of language, yet many modern AI systems struggle to handle it correctly. Improving negation understanding is critical for:

- Reliable search systems  
- Human-AI interaction  
- Safety and correctness in AI outputs  

---

## 🔮 Future Work

- Extend to more complex compositional reasoning  
- Improve robustness to long-range dependencies  
- Evaluate on larger and standardized benchmarks  

---

## 📌 Note

Details of the underlying method will be added in a future update.
