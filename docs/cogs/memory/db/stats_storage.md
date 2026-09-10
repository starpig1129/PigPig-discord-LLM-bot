# File: `cogs/memory/db/stats_storage.py`

## Overview
StatsStorage: handles user statistics and log migration state persistence.

This module provides CRUD operations for the user_stats and
log_migration_state tables, supporting real-time message tracking and
historical log migration.

## Classes

### `StatsStorage`
Handles user_stats and log_migration_state table operations.

Attributes:
    db: The shared DatabaseConnection instance.

- **Attributes**:
  - `db` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, db: DatabaseConnection) -> None`: Initialize with a DatabaseConnection instance.
  - `_get_user_stats_sync(self, user_id: str, guild_id: str) -> Optional[Dict[str, Any]]`: Method _get_user_stats_sync.
  - `upsert_user_stats(self, user_id: str, guild_id: str, message_content: str, channel_id: str, timestamp: str) -> None`: Insert or update cumulative stats for a single message event.
  - `_upsert_user_stats_sync(self, user_id: str, guild_id: str, message_content: str, channel_id: str, timestamp: str) -> None`: Method _upsert_user_stats_sync.
  - `bulk_upsert_user_stats(self, records: List[Dict[str, Any]]) -> None`: Insert or update cumulative stats for a batch of message events.
  - `_bulk_upsert_user_stats_sync(self, records: List[Dict[str, Any]]) -> None`: Method _bulk_upsert_user_stats_sync.
  - `_get_migration_state_sync(self, guild_id: str) -> Optional[str]`: Method _get_migration_state_sync.
  - `_set_migration_state_sync(self, guild_id: str, date_str: str) -> None`: Method _set_migration_state_sync.

## Functions

### `_safe_json_load(raw: Any) -> Dict[str, int]`
Safely parse a JSON string into a dict, defaulting to empty dict.

### `_extract_emojis(text: str) -> List[str]`
Extract Unicode and Discord custom emojis from text.

### `_segment_words(text: str) -> List[str]`
Segment text using jieba and filter stop-words / noise.

Returns a list of meaningful words (length >= 2, not pure digits,
not in the stop-word set).

### `_trim_top_words(words_dict: Dict[str, int]) -> Dict[str, int]`
Keep only the top N words by frequency to prevent unbounded growth.

### `_compute_streak(current_streak: int, last_date_str: Optional[str], today_str: str) -> tuple[int, str]`
Compute the updated streak days based on the last active date.

Args:
    current_streak: The current consecutive active days count.
    last_date_str: The last active date in YYYY-MM-DD format, or None.
    today_str: Today's date in YYYY-MM-DD format.

Returns:
    A tuple of (updated_streak_days, updated_last_date_str).
