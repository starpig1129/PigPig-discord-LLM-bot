# File: `cogs/memory/embedding_providers/ollama.py`

## Overview
Core module for ollama.py.

## Functions

### `ollama_provider(settings: MemoryConfig) -> Embeddings`
Ollama embedding provider factory using langchain_ollama.OllamaEmbeddings.

Expects settings to provide:
  - embedding_model_name
  - ollama_url (optional, if the client needs a custom endpoint)

Returns a langchain_core compatible Embeddings instance.
