# File: `cogs/memory/embedding_providers/huggingface.py`

## Overview
Core module for huggingface.py.

## Functions

### `huggingface_provider(settings: MemoryConfig) -> Embeddings`
Provider factory using langchain_huggingface.HuggingFaceEmbeddings.

Expects settings to provide:
  - embedding_model_name

Returns a langchain_core compatible Embeddings instance.
