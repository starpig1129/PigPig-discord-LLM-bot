# File: `cogs/memory/embedding_providers/openai.py`

## Overview
Core module for openai.py.

## Functions

### `openai_provider(settings: MemoryConfig) -> Embeddings`
OpenAI embedding provider factory.

Expects settings to provide:
  - openai_api_key
  - openai_model_name

Returns a langchain_core compatible Embeddings instance.
