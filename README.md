# FinQA Bench: Multi-Vector-Database Benchmark for Financial Compliance RAG

> **Evaluating Pinecone, Qdrant, and FAISS on recall, latency, cost, and hybrid search for a regulated knowledge assistant.**

[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![LangChain](https://img.shields.io/badge/LangChain-0.3+-green.svg)](https://www.langchain.com/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.115+-teal.svg)](https://fastapi.tiangolo.com/)

## 🎯 Why This Project

As an AI Solution Architect in finance, I needed to:
- Choose the right vector DB for a 10,000+ document regulatory assistant
- Prove hybrid search (dense + sparse) improves compliance Q&A
- Benchmark real-world performance (p99 latency, recall, cost)
- Demonstrate production-ready RAG with metadata filtering and real-time ingestion

**This repo contains the complete benchmark, code, and results.**

## 🏗️ Architecture

![Architecture](docs/architecture.png) *Mermaid diagram below*

```mermaid
graph LR
    A[Financial PDFs] --> B[Chunking + Embedding]
    B --> C[Kafka]
    C --> D1[Pinecone]
    C --> D2[Qdrant]
    C --> D3[FAISS]
    D1 & D2 & D3 --> E[Benchmark Harness]
    E --> F[Results: Recall/Latency/Cost]
    D1 & D2 & D3 --> G[FastAPI + LangChain RAG]
    G --> H[Streamlit UI]
.
.
.
