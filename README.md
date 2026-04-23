# Project: Recursive Agentic RAG for Indian Legal Q&A

**Project Shadow** is an advanced AI framework designed to provide high-fidelity answers from a massive corpus of **48,000 Indian Supreme Court judgments**. 

While standard RAG systems often suffer from hallucinations in specialized domains, Shadow introduces a **Recursive Loop-back** mechanism. This allows the system to evaluate its own confidence and refine its retrieval strategy autonomously, bridging the "reliability gap" in legal technology.

---

## 🏗️ Project Architecture

The system is modularized into three primary stages, represented by the core files in this repository:

1. **`kb_new` (Knowledge Base Construction)**: 
   - Handles recursive PDF extraction of 48k judicial documents.
   - Implements legal-specific metadata extraction (Petitioner, Respondent, Date, Judgment).
   - Generates a searchable **FAISS** vector index using `bge-small-en-v1.5` embeddings.

2. **`adapter` (Model Adaptation)**: 
   - Fine-tunes the **Mistral-7B-v0.1** model using **LoRA (Low-Rank Adaptation)**.
   - Trained on the **IndicLegalQA** dataset to master Indian judicial terminology and reasoning.
   - Utilizes 4-bit quantization to maintain high performance with low VRAM footprint.

3. **`work-final` (Agentic Orchestration)**: 
   - The "brain" of the project built with **LangGraph**.
   - Implements a **Strategic Two-Stage Retrieval**: Noisy search $\rightarrow$ Adapter Alignment $\rightarrow$ Refined Search.
   - Features a **Vector-Based Decision Gate** that triggers a recursive loop if the answer's fidelity score is below 0.7.

---

## 🚀 Performance Benchmarks

Shadow significantly outperforms standard linear RAG pipelines:

| Metric | Standard RAG | **Shadow (Agentic RAG)** | Improvement |
| :--- | :--- | :--- | :--- |
| **Overall F1 Score** | 0.2455 | **0.3573** | **+45.5%** |
| **Semantic Similarity** | 0.6210 | **0.7512** | **+21.0%** |

---

## 🛠️ Technical Stack

- **Core LLM**: Mistral-7B (4-bit Quantized)
- **Agentic Framework**: LangGraph, LangChain
- **Vector Database**: FAISS
- **Optimization**: PEFT / LoRA, FlashAttention
- **Frontend**: Gradio (Dark-themed UI for legal researchers)
- **Environment**: Kaggle / Linux (Ubuntu)

---

## 📂 File Descriptions

- `kb_new.ipynb`: The data engineering pipeline for cleaning and indexing the Supreme Court corpus.
- `adapter.ipynb`: The PEFT/LoRA training script for domain-specific fine-tuning.
- `work-final.ipynb`: The final deployment file containing the agentic graph logic and the interactive Gradio UI.

---

## ⚖️ Sustainable Development Goals (SDGs)

This project is mapped to the following United Nations SDGs:
* **SDG 16 (Peace, Justice, and Strong Institutions)**: Promoting access to justice through transparent, citation-backed AI.
* **SDG 9 (Industry, Innovation, and Infrastructure)**: Developing cutting-edge recursive AI architectures for national legal infrastructure.

---

## 👨‍💻 Developer
**Althaf Nawaz Mohammad** *Final Year Computer Science Engineering (AI & ML)* *PVP Siddhartha Institute of Technology*
