# 🛡️ Defence News Daily Brief Assistant

### AI-Powered Defence News Intelligence using Mistral-7B, RAG, FAISS & Gradio

[![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)](https://www.python.org/)
[![Mistral](https://img.shields.io/badge/LLM-Mistral--7B-orange)](https://mistral.ai/)
[![LangChain](https://img.shields.io/badge/LangChain-RAG-green)](https://www.langchain.com/)
[![FAISS](https://img.shields.io/badge/Vector_Search-FAISS-blue)](https://github.com/facebookresearch/faiss)
[![Gradio](https://img.shields.io/badge/UI-Gradio-yellow)](https://www.gradio.app/)
[![NLP](https://img.shields.io/badge/AI-NLP-purple)](https://en.wikipedia.org/wiki/Natural_language_processing)

---

## 📌 Project Overview

**Defence News Daily Brief Assistant** is an end-to-end Generative AI application designed to identify, classify, retrieve, and analyze defence-related news from large-scale news datasets.

The system combines **Large Language Models (LLMs), Natural Language Processing, semantic embeddings, vector search, and Retrieval-Augmented Generation (RAG)** to transform unstructured news headlines into a searchable defence intelligence knowledge base.

The application can also process **live RSS news feeds**, allowing newly retrieved headlines to pass through the same relevance and categorization pipeline.

### 🎯 Core Objective

> **Automatically identify defence-relevant information from large volumes of unstructured news and make it searchable through an intelligent RAG-based assistant.**

---

# 🏗️ System Architecture

```text
                    ┌──────────────────────┐
                    │   Historical News    │
                    │       Dataset        │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │ Data Preprocessing   │
                    │ & Candidate Filter   │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │   Mistral-7B LLM     │
                    │ Relevance Detection  │
                    │ + Classification     │
                    └──────────┬───────────┘
                               │
                       Defence Relevant
                               │
                               ▼
              ┌────────────────────────────────┐
              │ Defence News Knowledge Base    │
              │                                │
              │ Procurement                    │
              │ Exercises                      │
              │ Border Incidents               │
              │ Technology                     │
              │ Other                          │
              └───────────────┬────────────────┘
                              │
                              ▼
                  ┌──────────────────────┐
                  │ Sentence Transformer │
                  │   Embeddings         │
                  │ all-MiniLM-L6-v2     │
                  └──────────┬───────────┘
                             │
                             ▼
                    ┌──────────────────────┐
                    │    FAISS Index       │
                    │ Semantic Vector      │
                    │      Search          │
                    └──────────┬───────────┘
                               │
                         User Question
                               │
                               ▼
                    ┌──────────────────────┐
                    │       RAG            │
                    │ Retrieval + Context  │
                    │ + Generation         │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │  Gradio Intelligence │
                    │      Dashboard       │
                    └──────────────────────┘
```

---

# 🔄 End-to-End Workflow

### 1. Data Ingestion

The system begins with a large-scale historical news dataset containing more than **1.2 million news headlines**.

The dataset is cleaned and prepared for downstream processing.

### 2. Candidate Filtering

A preprocessing and filtering stage identifies headlines that have a potential connection to defence-related topics.

This reduces the amount of data that needs to be processed by the LLM.

### 3. LLM-Based Classification

Potential candidates are passed to:

**Mistral-7B-Instruct-v0.2**

The model determines whether a headline is relevant to defence and assigns an appropriate category.

### 4. Defence Categorization

Relevant headlines are classified into:

* 🛒 Procurement
* 🎖️ Exercises
* 🌐 Border Incidents
* 🛰️ Technology
* 📌 Other

### 5. Embedding Generation

Relevant documents are converted into numerical vector representations using:

**Sentence Transformers — all-MiniLM-L6-v2**

These embeddings capture the semantic meaning of each news headline.

### 6. Vector Indexing

The generated embeddings are stored in a:

**FAISS vector index**

FAISS enables efficient similarity-based retrieval from the defence news knowledge base.

### 7. Retrieval-Augmented Generation

When a user submits a question:

```text
User Question
      ↓
Query Embedding
      ↓
FAISS Similarity Search
      ↓
Relevant News Retrieval
      ↓
Context Construction
      ↓
LLM Response
```

The system retrieves the most relevant news records and uses them as context for generating an answer.

### 8. Source Traceability

Retrieved source headlines are displayed along with the generated response.

This helps users understand where the retrieved information originated and improves transparency.

### 9. Live News Processing

The application can also retrieve fresh headlines through **RSS feeds using Feedparser**.

The live headlines can then pass through the same filtering and classification workflow.

---

# 📊 Dataset & Results

The project was developed using a large-scale historical news dataset.

| Stage                          |    Result |
| ------------------------------ | --------: |
| Original news headlines        | **1.2M+** |
| Potential defence candidates   |  **67K+** |
| Final defence-relevant records | **1,756** |
| Manually validated headlines   |    **50** |

The final curated dataset contains **1,756 defence-relevant records** across the defined defence categories.

---

# 📈 Model Evaluation

A manually validated sample of 50 headlines was used to evaluate the classification pipeline.

| Metric    |      Score |
| --------- | ---------: |
| Accuracy  | **86.00%** |
| Precision | **79.17%** |
| Recall    | **90.48%** |
| F1 Score  | **84.44%** |

### Confusion Matrix

```text
                         Predicted
                     YES          NO
Actual YES           19           2
Actual NO             5          24
```

The evaluation demonstrates that the system was able to identify most relevant defence headlines while maintaining reasonable precision.

---

# 🧠 LLM Classification

The project uses:

### Mistral-7B-Instruct-v0.2

The model performs two important tasks:

1. **Relevance Detection**

   * Determines whether the headline is defence-related.

2. **Category Assignment**

   * Assigns relevant headlines to the appropriate defence category.

### Prompt Engineering

Structured prompts were used to control the model output and encourage consistent classification.

Example:

```text
Headline:
"Military forces conduct joint exercise near the border"

Task:
Determine whether the headline is defence relevant.

If relevant, assign one category:

- Procurement
- Exercises
- Border Incidents
- Technology
- Other

Return the result in a structured format.
```

---

# 🔎 RAG Pipeline

The RAG architecture combines retrieval with language generation.

### Retrieval

FAISS searches the embedding space to identify semantically similar news records.

### Augmentation

The retrieved documents are added to the context supplied to the language model.

### Generation

The LLM generates an answer using the retrieved context.

This approach helps ground responses in the project's curated knowledge base instead of relying entirely on the model's pretrained knowledge.

---

# 🛠️ Technology Stack

| Technology                   | Purpose                         |
| ---------------------------- | ------------------------------- |
| **Python**                   | Core development                |
| **Mistral-7B-Instruct-v0.2** | LLM classification & generation |
| **LangChain**                | LLM/RAG application framework   |
| **FAISS**                    | Vector similarity search        |
| **Sentence Transformers**    | Text embeddings                 |
| **all-MiniLM-L6-v2**         | Embedding model                 |
| **Gradio**                   | Interactive web interface       |
| **Pandas**                   | Data processing                 |
| **NumPy**                    | Numerical operations            |
| **Feedparser**               | RSS news ingestion              |
| **PyTorch**                  | Deep learning framework         |
| **NVIDIA Tesla T4**          | GPU acceleration                |
| **4-bit NF4 Quantization**   | Memory optimization             |

---

# ⚡ Model Optimization

Running a 7B parameter model in a limited GPU environment requires memory optimization.

The project uses:

### 4-bit NF4 Quantization

This reduces the memory footprint of the Mistral model while allowing it to run efficiently on an NVIDIA Tesla T4 GPU.

This was particularly useful for developing and testing the system in a Colab-based environment.

---

# 💻 Application Interface

The project includes an interactive **Gradio Defence Intelligence Dashboard**.

The interface is designed to provide:

* Defence news exploration
* Category-based analysis
* Semantic search
* RAG question answering
* Retrieved source headlines
* Historical news analysis
* Live RSS news processing

---

# 📂 Project Structure

```text
defence-news-daily-brief-assistant/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── notebooks/
│   └── Defence_News_Daily_Brief_Assistant.ipynb
│
├── app/
│   └── app.py
│
├── src/
│   ├── classification.py
│   ├── embeddings.py
│   ├── rag_pipeline.py
│   └── rss_ingestion.py
│
├── data/
│   └── README.md
│
├── RAG/
│   └── README.md
│
├── evaluation/
│   ├── metrics.csv
│   └── README.md
│
└── screenshots/
    ├── dashboard.png
    ├── architecture.png
    └── rag_query.png
```

> Large datasets, model weights, API credentials, cache files, and other generated artifacts should not be committed directly to the repository.

---

# 🚀 Installation

Clone the repository:

```bash
git clone https://github.com/YOUR-USERNAME/defence-news-daily-brief-assistant.git
cd defence-news-daily-brief-assistant
```

Create a virtual environment:

```bash
python -m venv venv
```

Activate it on Windows:

```bash
venv\Scripts\activate
```

Activate it on Linux/macOS:

```bash
source venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

# ▶️ Running the Application

After installing the dependencies:

```bash
python app/app.py
```

The Gradio interface will provide a local URL that can be opened in a web browser.

---

# 📚 Example Use Cases

The assistant can support questions such as:

```text
What defence technology developments are present in the archive?
```

```text
Show relevant border incident news.
```

```text
What procurement-related events are available?
```

```text
Find technology-related defence headlines similar to this topic.
```

The system retrieves semantically relevant records from the curated knowledge base before generating its response.

---

# 💡 Applications Beyond Defence

Although this project focuses on defence news, the underlying architecture is domain-independent.

The same pipeline can be adapted for:

* 🏦 Financial Intelligence
* 🔐 Cybersecurity Monitoring
* 📈 Market Intelligence
* ⚖️ Regulatory Intelligence
* 📰 News Analytics
* 📚 Research Assistants
* 🏢 Enterprise Knowledge Assistants
* 📄 Document Intelligence

The architecture can therefore serve as a foundation for domain-specific **GenAI + RAG applications**.

---

# 🔮 Future Improvements

Potential future enhancements include:

* [ ] Add additional defence news sources
* [ ] Improve classification with fine-tuning
* [ ] Add multilingual news support
* [ ] Add document-level RAG
* [ ] Implement retrieval reranking
* [ ] Improve source attribution
* [ ] Automate daily intelligence brief generation
* [ ] Add scheduled RSS ingestion
* [ ] Add cloud-based deployment
* [ ] Add monitoring and evaluation dashboards
* [ ] Introduce user feedback for continuous improvement

---

# 🎓 Key Learning Outcomes

This project provided practical experience across the complete AI application lifecycle:

```text
Data Collection
      ↓
Data Preprocessing
      ↓
Candidate Filtering
      ↓
Prompt Engineering
      ↓
LLM Classification
      ↓
Model Evaluation
      ↓
Embeddings
      ↓
Vector Search
      ↓
RAG
      ↓
Application Development
      ↓
Deployment
```

### Key technical areas explored:

* Generative AI
* Large Language Models
* Prompt Engineering
* Natural Language Processing
* Semantic Embeddings
* Vector Databases/Search
* Retrieval-Augmented Generation
* Model Evaluation
* GPU Optimization
* Real-time Data Ingestion
* AI Application Deployment

---

 👩‍💻 Author

Ankita Ulshai

AI / ML | Generative AI | NLP | RAG | Machine Learning

Interested in building intelligent, production-oriented AI systems that combine **LLMs, machine learning, NLP, retrieval systems, and real-world data pipelines.**

---

 ⭐ Acknowledgements

This project was developed as part of a **Generative AI / AI Engineering capstone project** and focuses on applying modern GenAI techniques to defence news intelligence.

---

 📜 License

This project is intended for educational and research purposes.

Please review the licensing terms of all third-party datasets, models, libraries, and news sources before using the project commercially.
