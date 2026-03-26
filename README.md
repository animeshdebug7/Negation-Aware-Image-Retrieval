# Negation-Aware Image Retrieval

## 🚀 Overview

Modern vision-language models such as CLIP perform well on descriptive queries but often fail when handling **negation** (e.g., “an image of an animal that is not a dog”). These models tend to retrieve images matching dominant concepts rather than respecting logical constraints in language.

This project explores a **"Zero-shot"** method to enable **negation-aware image retrieval**, improving text-to-image search by correctly identifying and excluding negated concepts.

---
## 📊 Comparison: Standard CLIP vs Negation-Aware Retrieval

We compare standard CLIP retrieval with my negation-aware approach on queries involving negation.

---

### 🧪 Query 1
**Text:** *"an image of an animal that is not a dog"*

| Model | Retrieved Image |
|------|----------------|
| DeBERTa-V3-large + CLIP | <img src="images/img10.jpeg" width="60%"/> |
| DistilBERT + CLIP | <img src="images/img9.jpeg" width="60%"/> |

**Observation:**  
DeBERTa-V3-large + CLIP retrieves images of dogs despite the negation.  
DistilBERT + CLIP method correctly excludes dogs and retrieves other animals.

---

### 🧪 Query 2
**Text:** *"an image of a fridge without fruits"*

| Model | Retrieved Image |
|------|----------------|
| DeBERTa-V3-large + CLIP | <img src="images/img7.jpeg" width="50%"/> |
| (My Approach)DistilBERT + CLIP | <img src="images/img13.jpeg" width="40%"/> |

**Observation:**  
DeBERTa-V3-large + CLIP retrieves images containing fruits.  
DistilBERT + CLIP method retrieves a fridge without fruits, respecting the negation.

---

### 🧪 Query 3
**Text:** *"an image of a boat not in the ocean"*

| Model | Retrieved Image |
|------|----------------|
| DeBERTa-V3-large + CLIP | ![](images/img3.jpeg) |
| DistilBERT + CLIP | ![](images/img4.jpeg) |

**Observation:**  
DeBERTa-V3-large + CLIP prioritizes dominant associations (boat → ocean).  
DistilBERT + CLIP method retrieves boats in alternative contexts.

---

### 🧪 Query 4
**Text:** *"an image of people playing in a park not children"*

| Model | Retrieved Image |
|------|----------------|
| DeBERTa-V3-large + CLIP | <img src="images/img5.jpeg" width="50%"/> |
| DistilBERT + CLIP | ![](images/img6.jpeg) |

**Observation:**  
DeBERTa-V3-large + CLIP retrieves children playing.  
DistilBERT + CLIP method correctly retrieves adults.

---

### 🧪 Query 5
**Text:** *"an image of people playing in a park not adults"*

| Model | Retrieved Image |
|------|----------------|
| DeBERTa-V3-large + CLIP | ![](images/img6.jpeg) |
| DistilBERT + CLIP | <img src="images/img5.jpeg" width="50%"/> |

**Observation:**  
DeBERTa-V3-large + CLIP retrieves adults playing as CLIP just sees adults.  
DistilBERT + CLIP method correctly retrieves children.

---

## 📌 Summary

- Standard CLIP struggles with **negation and compositional constraints**
- My approach improves retrieval by:
  - Identifying negated concepts  
  - Filtering or re-ranking results accordingly  

This leads to more **accurate and controllable text-to-image retrieval**.









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
  - Large pretrained encoders (non-task-specific) -> Outperforms it
  - Supervised NLI models (as a reference baseline) -> Gives Similar results

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

## 🔮 Future Work

- Handle very complex sentences
- Extend to more complex compositional reasoning  
- Improve robustness to long-range dependencies  
- Evaluate on larger and standardized benchmarks  

---

## 📌 Note

Details of the underlying method will be added in a future update.
