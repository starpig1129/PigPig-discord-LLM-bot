# File: `cogs/memory/users/models.py`

## Overview
UserInfo model for user data.

## Classes

### `UserInfo`
Dataclass matching the new `users` schema.

Fields:
  - discord_id: primary identifier (TEXT)
  - discord_name: current display name
  - display_names: historical display names (stored as JSON array)
  - procedural_memory: free-form procedural memory (string)
  - user_background: free-form background info (string)
  - created_at: creation timestamp

- **Attributes**:
  - `discord_id` (`str`): Class attribute.
  - `discord_name` (`str`): Class attribute.
  - `display_names` (`List[str]`): Class attribute.
  - `procedural_memory` (`Optional[str]`): Class attribute.
  - `user_background` (`Optional[str]`): Class attribute.
  - `created_at` (`Optional[datetime]`): Class attribute.

- **Methods**:
  - `to_dict(self) -> Dict[str, Any]`: Convert to dict for serialization; datetimes become ISO strings.
  - `from_dict(cls, data: Dict[str, Any]) -> 'UserInfo'`: Instantiate from dict, handling created_at and display_names formats.
