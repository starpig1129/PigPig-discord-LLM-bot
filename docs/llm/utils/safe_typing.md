# File: `llm/utils/safe_typing.py`

## Overview
Core module for safe_typing.py.

## Classes

### `SafeTyping`
Typing indicator that handles per-channel deduplication and rate-limiting.

This class ensures that only one typing heart-beat loop is running per channel,
even if multiple tasks are processing messages for the same channel.
It also enforces a minimum interval between trigger_typing() calls and
handles 429 rate limits gracefully.

- **Attributes**:
  - `_sessions` (`Dict[int, int]`): Class attribute.
  - `_tasks` (`Dict[int, asyncio.Task]`): Class attribute.
  - `_last_trigger` (`Dict[int, float]`): Class attribute.
  - `_channel` (`Any`): Instance attribute.
  - `_channel_id` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, channel: Any) -> None`: Method __init__.
  - `_loop(self, channel_id: int) -> None`: Background loop to keep the typing indicator alive.
