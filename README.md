# RAG Project: BrewBean Coffee Co. Customer Assistant

A step-by-step **Retrieval-Augmented Generation (RAG)** project built with LangChain, OpenAI and FAISS.
It answers customer questions about a fictional coffee company (*BrewBean Coffee Co.*), using dummy company documents.

## Pipeline
1. **Data loading**: load `.txt` documents from `data/`
2. **Chunking**: split them with `RecursiveCharacterTextSplitter`
3. **Embeddings**: `text-embedding-3-small`
4. **Indexing**: store the vectors in a FAISS vector store
5. **Retrieval**: find the top-k similar chunks
6. **Generation**: `gpt-4o-mini` answers from the retrieved context

## Project structure
```
├── RAG_Project.ipynb   # main notebook with step-by-step explanations
├── data/               # dummy company knowledge base
├── requirements.txt
├── .env.example        # template for the API key
└── .gitignore          # excludes .env and secrets
```

## Setup
```bash
pip install -r requirements.txt
cp .env.example .env      # then put your OpenAI API key in .env
jupyter notebook RAG_Project.ipynb
```

> The `.env` file is excluded through `.gitignore`. No API keys are stored in this repository.
