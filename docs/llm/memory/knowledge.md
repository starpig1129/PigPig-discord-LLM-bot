# File: `llm/memory/knowledge.py`

## Overview
KnowledgeMemoryProvider: provides guild and channel level knowledge with caching.

This provider handles retrieval of shared interaction knowledge (memes, facts, etc.)
and implements a TTL cache to optimize performance during message orchestration.

## Classes

### `KnowledgeMemory`
Represents the fetched knowledge for a specific context.

- **Attributes**:
  - `guild_knowledge` (`Any`): Instance attribute.
  - `channel_knowledge` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, guild_knowledge: Optional[str], channel_knowledge: Optional[str]) -> Any`: Method __init__.

### `KnowledgeMemoryProvider`
Provides guild/channel knowledge with caching.

- **Attributes**:
  - `storage` (`Any`): Instance attribute.
  - `max_cache_size` (`Any`): Instance attribute.
  - `_cache` (`Dict[Tuple[str, str], Tuple[Optional[str], float]]`): Instance attribute.
  - `_pending_queries` (`Dict[Tuple[str, str], asyncio.Event]`): Instance attribute.

- **Methods**:
  - `__init__(self, storage: KnowledgeStorage, max_cache_size: int) -> None`: Initialize with storage and cache limit.
  - `get(self, guild_id: Optional[str], channel_id: str) -> KnowledgeMemory`: Fetch knowledge for the current guild and channel.
  - `_get_single(self, target_type: str, target_id: str) -> Optional[str]`: Internal helper with TTL cache and thundering herd protection.
  - `invalidate(self, target_type: str, target_id: str) -> None`: Invalidate cache for a specific target.
