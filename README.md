# QA Retrieval Chatbot (RAG): BrewBean Coffee Co.

A step-by-step **Retrieval-Augmented Generation (RAG)** project built with **LangChain, OpenAI and Pinecone**.
It answers customer questions about a fictional coffee company (*BrewBean Coffee Co.*) using its company handbook PDF (dummy data).

## RAG phases
**1. Indexing (once):** PDF → `PyMuPDFLoader` → `RecursiveCharacterTextSplitter` (1000 / 200) → OpenAI embeddings (`text-embedding-3-small`, 1024 dims) → Pinecone index

**2. Retrieval (every question):** question → retriever (top-3 chunks) → `format_docs` → prompt (instructions + context + question) → `gpt-4.1-mini` → answer

## Project structure
```
├── RAG_Project.ipynb                    # main notebook with step-by-step explanations
├── data/brewbean_company_handbook.pdf   # dummy company knowledge base
├── pyproject.toml / uv.lock             # dependencies (uv)
├── .env.example                         # template for API keys
└── .gitignore                           # excludes .env and secrets
```

## Setup (with uv)
```bash
uv sync                  # creates .venv and installs everything
cp .env.example .env     # add your OPENAI_API_KEY and PINECONE_API_KEY
```
Open `RAG_Project.ipynb` in VS Code / Jupyter, select the `.venv` kernel and run all the cells.

> 🔒 The `.env` file is excluded through `.gitignore`. No API keys are stored in this repository.
