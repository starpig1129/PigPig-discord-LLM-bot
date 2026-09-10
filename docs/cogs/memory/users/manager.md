# File: `cogs/memory/users/manager.py`

## Overview
User manager depending on StorageInterface.

## Classes

### `SQLiteUserManager`
Lightweight user manager that delegates storage operations to StorageInterface.

Responsibilities:
- delegate persistence to provided storage
- coordinate user data operations

- **Attributes**:
  - `storage` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, storage: StorageInterface) -> Any`: Initialize with a StorageInterface implementation.
  - `get_multiple_users(self, user_ids: List[str], use_cache: bool) -> Dict[str, UserInfo]`: Retrieve multiple users concurrently (storage handles caching).
  - `update_user_data(self, user_id: str, user_data: Any, discord_name: Optional[str], nickname: Optional[str]) -> bool`: Extracts fields from user_data and delegates to storage.
  - `delete_user_data(self, user_id: str) -> bool`: Delegate deletion to storage.
  - `update_user_activity(self, user_id: str, discord_name: str, nickname: Optional[str]) -> bool`: Delegate activity update to storage.
  - `search_users_by_display_name(self, name_pattern: str, limit: int) -> List[UserInfo]`: Search users by display name via storage.
  - `migrate_from_mongodb(self, mongodb_collection: Any) -> int`: Migrate users by delegating to update_user_data for each document.
  - `cleanup_inactive_users(self, days: int) -> int`: Delegate cleanup if storage provides method; otherwise no-op.

## Functions

### `extract_participant_ids(message: Any, conversation_history: List[Any]) -> set`
Extract participant IDs from a message and recent conversation history.

Args:
    message: Discord message object
    conversation_history: list of recent messages or dicts representing messages

Returns:
    set: set of participant ID strings
