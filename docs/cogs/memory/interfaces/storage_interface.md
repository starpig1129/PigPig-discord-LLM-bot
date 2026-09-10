# File: `cogs/memory/interfaces/storage_interface.py`

## Overview
Core module for storage_interface.py.

## Classes

### `ProceduralStorageInterface`
Interface for procedural (user) storage operations.

- **Methods**:
  - `delete_user_data(self, discord_id: str) -> bool`: Method delete_user_data.
  - `update_user_data(self, discord_id: str, discord_name: str, procedural_memory: Optional[str], user_background: Optional[str], display_names: Optional[List[str]], nickname: Optional[str]) -> bool`: Method update_user_data.
  - `update_user_activity(self, discord_id: str, discord_name: str, nickname: Optional[str]) -> bool`: Method update_user_activity.

### `EpisodicStorageInterface`
Interface for episodic (channel memory state) storage operations.

- **Methods**:
  - `initialize_channel_memory_state(self) -> None`: Initialize the channel_memory_state table in the database.
  - `update_channel_memory_state(self, channel_id: int, message_count: int, start_message_id: int, last_summary_timestamp: Optional[float], last_summary_text: Optional[str]) -> None`: Update the memory state for a specific channel.

### `StorageInterface`
Combined interface kept for backward compatibility.
