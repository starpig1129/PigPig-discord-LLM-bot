# File: `cogs/memory/embedding_providers/google.py`

## Overview
Core module for google.py.

## Functions

### `google_genai_provider(settings: MemoryConfig) -> Embeddings`
Google Generative AI embeddings provider using langchain_google_genai.

Expects settings to provide:
  - google_api_key
  - embedding_model_name

Returns a langchain_core compatible Embeddings instance.
