# BioMed (OHD) Hybrid-RAG System

This project implements a **Hybrid Retrieval-Augmented Generation (RAG)** architecture designed to eliminate hallucinations in dental and oral health AI. By fusing a **Vector Database** (semantic context) with a **Knowledge Graph** (structural clinical facts), the system provides verifiable, PMID-linked answers to complex oral-systemic health queries.

## 🚀 Key Features

* **Automated Evidence Ingestion:** Extracts and cleans metadata from 933 PubMed abstracts using `Bio.Entrez`.
* **Clinical Triple Extraction:** Utilizes a "Master Prompt" with Llama 3.2 to convert unstructured text into Subject-Predicate-Object clinical facts.
* **Dual-Memory Retrieval:** Combines FAISS (Vector Search) with a Knowledge Graph to ensure answers are both contextually relevant and biologically accurate.
* **Zero-Hallucination Citations:** Every claim made by the "Senior Clinician" persona is backed by a verified PubMed ID (PMID).
* **Interactive Visualization:** Generates a dynamic, browser-based map of the oral health knowledge base using `PyVis`.

## 🧠 System Architecture

The system operates on a dual-path logic:

1. **Semantic Path:** Uses `nomic-embed-text` to index abstracts in a **FAISS** vector store for broad context retrieval.
2. **Structural Path:** Extracts high-fidelity clinical relationships into a **Knowledge Graph** to define the direction of risk and causality.
3. **Synthesis:** The **Llama 3.2 (3B)** model synthesizes both paths to generate a grounded response.

## 🛠️ Tech Stack

* **LLM:** Llama 3.2 (3B) via Ollama
* **Embeddings:** `nomic-embed-text:latest`
* **Vector Store:** FAISS (Facebook AI Similarity Search)
* **Graph Logic:** NetworkX & PyVis
* **Data Source:** PubMed (NCBI Entrez API)
* **Language:** Python 3.10+

## 📥 Installation & Setup

1. **Clone the repository:**
```bash
git clone https://github.com/yourusername/OHD-Hybrid-RAG.git
cd OHD-Hybrid-RAG

```


2. **Install Dependencies:**
```bash
pip install pandas numpy biopython tqdm faiss-cpu networkx pyvis ollama scikit-learn

```


3. **Configure Ollama:**
Ensure you have Ollama installed and the models pulled:
```bash
ollama pull llama3.2
ollama pull nomic-embed-text

```



## 📊 Evaluation: Hybrid vs. General AI

This project includes a **Dual Comparison Report** module. In testing, Generalist LLMs often hallucinate citations (e.g., inventing a "Li et al. 2019" paper), whereas this Hybrid system successfully identifies deep systemic links—such as the relationship between **Periodontitis and Cerebral Small Vessel Disease**—using verified literature.

## ⚖️ Limitations & Future Work

* **Knowledge Sparsity:** Currently, the Knowledge Graph is built from a subset of the 933 abstracts. Expanding triple extraction to the full corpus is a primary goal.
* **Semantic Graph Retrieval:** Implementing vector-based triple retrieval to improve "soft matches" in the Knowledge Graph.

## 📄 License

This project is for research and educational purposes. Data retrieved from PubMed is subject to NCBI's terms of service.
