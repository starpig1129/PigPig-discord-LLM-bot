# File: `llm/memory/procedural.py`

## Overview
Core module for procedural.py.

## Classes

### `ProceduralMemoryProvider`
Provides procedural memory for multiple users with per-user TTL cache.

The provider fetches UserInfo for each user_id using the provided user manager
and caches results per user_id to avoid redundant DB calls within the TTL window.

- **Attributes**:
  - `user_manager` (`Any`): Instance attribute.
  - `max_cache_size` (`Any`): Instance attribute.
  - `_cache` (`Dict[str, Tuple[Optional[UserInfo], float]]`): Instance attribute.
  - `_pending_queries` (`Dict[str, asyncio.Event]`): Instance attribute.

- **Methods**:
  - `__init__(self, user_manager: SQLiteUserManager, max_cache_size: int) -> None`: Initializes the provider with a user manager instance and cache size limit.
  - `get(self, user_ids: List[str]) -> ProceduralMemory`: Fetch procedural memory with per-user TTL cache.
  - `invalidate(self, user_id: str) -> None`: Evict a single user from the cache.
