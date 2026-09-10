# File: `cogs/memory/db/episodic_storage.py`

## Overview
EpisodicStorage: handles message-related tables (messages, pending_messages, messages_archive).

Extracted from the previous sqlite_storage implementation to separate concerns.
All error reporting uses func.report_error per project rules.

## Classes

### `EpisodicStorage`
Handles channel memory state management.

- **Attributes**:
  - `db` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, db: DatabaseConnection) -> None`: Method __init__.
  - `initialize_channel_memory_state(self) -> None`: Initialize the channel_memory_state table in the database.
  - `_initialize_channel_memory_state_sync(self) -> None`: Method _initialize_channel_memory_state_sync.
  - `_get_channel_memory_state_sync(self, channel_id: int) -> Optional[Dict[str, Any]]`: Method _get_channel_memory_state_sync.
  - `update_channel_memory_state(self, channel_id: int, message_count: int, start_message_id: int, last_summary_timestamp: Optional[float], last_summary_text: Optional[str]) -> None`: Update the memory state for a specific channel.
  - `_update_channel_memory_state_sync(self, channel_id: int, message_count: int, start_message_id: int, last_summary_timestamp: Optional[float], last_summary_text: Optional[str]) -> None`: Method _update_channel_memory_state_sync.
  - `_get_total_count_sync(self) -> int`: Method _get_total_count_sync.
