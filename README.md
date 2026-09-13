# defence-news-daily-brief-assistant
AI-powered Defence News Intelligence Assistant using Mistral-7B, RAG, FAISS, LangChain, Sentence Transformers, and Gradio for news classification, semantic search, and intelligent Q&amp;A.
# Defence News Daily Brief Assistant

An AI-powered Defence News Intelligence Assistant built using
Mistral-7B, RAG, FAISS, LangChain and Gradio.

## 🚀 Project Overview

The Defence News Daily Brief Assistant is an end-to-end Generative AI
application designed to identify, classify and retrieve defence-related
news from large-scale news datasets.

The system combines LLM-based classification with Retrieval-Augmented
Generation (RAG) to create a searchable defence intelligence knowledge base.

## 🎯 Objectives

- Identify defence-relevant news
- Classify news into defence categories
- Build a searchable knowledge base
- Enable semantic question answering
- Provide source traceability
- Support live RSS news ingestion
- Provide an interactive intelligence dashboard

## 🏗️ Architecture

News Dataset
     ↓
Data Preprocessing
     ↓
Candidate Filtering
     ↓
Mistral-7B Classification
     ↓
Relevant Defence News
     ↓
Sentence Transformer Embeddings
     ↓
FAISS Vector Search
     ↓
RAG Pipeline
     ↓
Gradio Dashboard
     ↓
User Query + Retrieved Sources

## 🧠 Defence Categories

- Procurement
- Exercises
- Border Incidents
- Technology
- Other

## 🛠️ Tech Stack

- Python
- Mistral-7B-Instruct-v0.2
- LangChain
- Retrieval-Augmented Generation
- FAISS
- Sentence Transformers
- Gradio
- Pandas
- NumPy
- Feedparser
- NVIDIA Tesla T4
- 4-bit NF4 Quantization

## 📊 Results

Manual validation on 50 headlines:

| Metric | Score |
|---|---:|
| Accuracy | 86% |
| Precision | 79.17% |
| Recall | 90.48% |
| F1 Score | 84.44% |

The final curated dataset contains 1,756 defence-relevant records.

## 💡 Key Features

- LLM-powered news classification
- Defence category detection
- Semantic search
- RAG-based question answering
- Source headline retrieval
- Historical news analysis
- Live RSS news ingestion
- Interactive Gradio dashboard

## 🔮 Future Improvements

- Add more defence news sources
- Improve classification using fine-tuning
- Add multilingual news support
- Introduce reranking for better retrieval
- Add automated daily briefing generation
- Deploy the application as a scalable cloud service

## 👩‍💻 Author

Ankita Ulshai

Interested in Generative AI, Machine Learning, NLP, RAG and AI Engineering.
