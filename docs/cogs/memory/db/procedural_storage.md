# File: `cogs/memory/db/procedural_storage.py`

## Overview
ProceduralStorage: handles users table and configuration storage.

This module extracts the procedural (user) related SQL logic from the previous
sqlite_storage implementation so responsibilities are separated.
All error reporting uses func.report_error per project rules.

## Classes

### `ProceduralStorage`
Handles users table and config storage.

- **Attributes**:
  - `db` (`Any`): Instance attribute.
  - `_user_cache` (`Dict[str, UserInfo]`): Instance attribute.
  - `_cache_size_limit` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, db: DatabaseConnection) -> None`: Method __init__.
  - `_get_user_info_sync(self, discord_id: str) -> Optional[UserInfo]`: Method _get_user_info_sync.
  - `get_users_info(self, discord_ids: List[str]) -> Dict[str, UserInfo]`: Fetch multiple users efficiently using a single SQL query.
  - `update_user_data(self, discord_id: str, discord_name: str, procedural_memory: Optional[str], user_background: Optional[str], display_names: Optional[List[str]], nickname: Optional[str]) -> bool`: Method update_user_data.
  - `_update_user_data_sync(self, discord_id: str, discord_name: str, procedural_memory: Optional[str], user_background: Optional[str], display_names: Optional[List[str]], nickname: Optional[str]) -> bool`: Method _update_user_data_sync.
  - `delete_user_data(self, discord_id: str) -> bool`: Method delete_user_data.
  - `_delete_user_data_sync(self, discord_id: str) -> bool`: Method _delete_user_data_sync.
  - `update_user_activity(self, discord_id: str, discord_name: str, nickname: Optional[str]) -> bool`: Method update_user_activity.
  - `_update_user_activity_sync(self, discord_id: str, discord_name: str, nickname: Optional[str]) -> bool`: Method _update_user_activity_sync.
  - `_get_all_users_sync(self, limit: int, offset: int) -> List[UserInfo]`: Method _get_all_users_sync.
  - `_get_users_count_sync(self) -> int`: Method _get_users_count_sync.
  - `_get_config_sync(self, key: str) -> Optional[str]`: Method _get_config_sync.
  - `_set_config_sync(self, key: str, value: str) -> None`: Method _set_config_sync.
  - `_update_cache(self, user_id: str, user_info: UserInfo) -> None`: Method _update_cache.
