# File: `cogs/memory/vector/manager.py`

## Overview
Core module for manager.py.

## Classes

### `VectorManager`
Factory class to dynamically initialize and provide a vector store instance and embedding model.

Responsibilities:
- Manage an embedding provider registry (pluggable).
- Initialize embedding model asynchronously based on settings.
- Initialize vector store with dependency injection of the embedding model.

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `settings` (`Any`): Instance attribute.
  - `embedding_model` (`Optional[Embeddings]`): Instance attribute.
  - `_store` (`Optional[VectorStoreInterface]`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: 'Bot', settings: 'MemoryConfig') -> Any`: Args:
  - `_get_store_class(self, store_type: str) -> Type[VectorStoreInterface]`: Dynamically imports and returns the vector store class from the 'vector_stores' directory.
  - `_initialize_store(self) -> VectorStoreInterface`: Creates the configured VectorStore instance, injecting the embedding model.
  - `_initialize_embedding(self) -> Embeddings`: Initializes embedding model according to settings.embedding_provider.
  - `initialize(self) -> Any`: Async initialization entrypoint.
  - `store(self) -> VectorStoreInterface`: Provides public access to the vector store instance.
  - `get_embedding_model(self) -> Embeddings`: Return initialized embedding model synchronously (after initialize).

## Functions

### `register_embedding_provider(name: str) -> Any`
Decorator to register an embedding provider factory under a canonical name.

Example:
    @register_embedding_provider("openai")
    def openai_factory(settings: MemoryConfig) -> Embeddings:
        ...
