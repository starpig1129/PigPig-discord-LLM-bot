# File: `llm/memory/episodic.py`

## Overview
Automatic Episodic Memory Provider for context injection.

Performs a lightweight vector search on each incoming message and returns
the top-k relevant past memory fragments as a formatted string.
Silent failure design: any error returns None without raising.

## Classes

### `EpisodicMemoryProvider`
Retrieve semantically relevant past memory fragments for context injection.

The result is injected into procedural_context_str so both info_agent and
message_agent receive the episodic background without extra tool calls.

Args:
    bot: Discord bot instance (must have vector_manager attribute).
    top_k: Maximum number of fragments to retrieve. Default 3.
    max_chars: Hard character limit for the returned string. Default 1500.
    max_cache_size: Maximum number of entries to retain in the cache. Default 1000.
    cache_ttl: Cache Time-To-Live in seconds. Default 300.0.

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `top_k` (`Any`): Instance attribute.
  - `max_chars` (`Any`): Instance attribute.
  - `max_cache_size` (`Any`): Instance attribute.
  - `cache_ttl` (`Any`): Instance attribute.
  - `_cache` (`Dict[Tuple[str, str], Tuple[Optional[str], float]]`): Instance attribute.
  - `_pending_queries` (`Dict[Tuple[str, str], asyncio.Event]`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: Any, top_k: int, max_chars: int, max_cache_size: int, cache_ttl: float) -> None`: Method __init__.
  - `invalidate(self, channel_id: str) -> None`: Invalidate all cached episodic queries for a specific channel.
  - `get(self, message: discord.Message) -> Optional[str]`: Return formatted episodic context string, or None if nothing relevant.
