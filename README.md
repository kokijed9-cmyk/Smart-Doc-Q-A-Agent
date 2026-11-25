# smart_doc__agent

A local Retrieval-Augmented Generation (RAG) workflow built with **n8n** and **Ollama** using an in-memory vector store (`vector_store_key`) and an AI Agent (`llama3.2:latest` + `nomic-embed-text:latest`) with zero paid API keys required.

## Overview

- **Document Ingestion Flow:** Reads a local PDF (`/home/node/.n8n-files/guide.pdf`), splits and loads documents, generates embeddings via `nomic-embed-text:latest`, and stores them in memory under `vector_store_key`.
- **Conversational Q&A Flow:** Listens for incoming chat messages (`When chat message received`) and routes them to an **AI Agent** powered by `llama3.2:latest` and a vector store retrieval tool (`knowledge_base`) sharing the same `nomic-embed-text:latest` embeddings.

## Tech Stack

- **Workflow Automation:** n8n
- **Local LLM & Embeddings:** Ollama (`llama3.2:latest`, `nomic-embed-text:latest`)
- **Vector Storage:** n8n In-Memory Vector Store (`vector_store_key`)

## Prerequisites

1. **n8n** running locally or in Docker.
2. **Ollama** installed and reachable from n8n (for example, `http://host.docker.internal:11434`).
3. Pull the required models:
   ```bash
   ollama pull nomic-embed-text:latest
   ollama pull llama3.2:latest
