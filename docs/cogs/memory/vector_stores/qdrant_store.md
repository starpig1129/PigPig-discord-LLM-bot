# File: `cogs/memory/vector_stores/qdrant_store.py`

## Overview
Qdrant-based Vector Store using LangChain integration.
Simplified implementation using langchain-qdrant package.

## Classes

### `QdrantStore`
LangChain Qdrant vector store wrapper.

- **Attributes**:
  - `settings` (`Any`): Instance attribute.
  - `embedding_model` (`Any`): Instance attribute.
  - `collection_name` (`Any`): Instance attribute.
  - `embedding_dim` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, settings: MemoryConfig, embedding_model: Optional[Embeddings]) -> None`: Method __init__.
  - `ensure_storage(self) -> None`: Ensure payload indexes exist.
  - `add_memories(self, memories: List[MemoryFragment]) -> None`: Add memories using LangChain's add_documents.
  - `search_memories_by_vector(self, query_text: str, limit: int, user_id: Optional[str], channel_id: Optional[str], min_score: Optional[float]) -> List[MemoryFragment]`: Vector similarity search with metadata filtering.
  - `search_memories_by_keyword(self, query_text: str, user_id: Optional[str], channel_id: Optional[str], k: int) -> List[MemoryFragment]`: Keyword search using Qdrant query API with payload filtering.
  - `search(self, vector_query: Optional[str], keyword_query: Optional[str], user_id: Optional[str], channel_id: Optional[str]) -> List[MemoryFragment]`: Hybrid search combining vector and keyword results.
  - `delete_vectors_by_user(self, user_id: str) -> int`: Delete all vectors where user_id appears in metadata.author_ids.
  - `_report_error(self, error: Exception) -> None`: Helper to report errors.
