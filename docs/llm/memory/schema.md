# File: `llm/memory/schema.py`

## Overview
Core module for schema.py.

## Classes

### `UserInfo`
Information about a single user used by procedural memory.

- **Attributes**:
  - `user_background` (`Optional[str]`): Class attribute.
  - `procedural_memory` (`Dict[str, Any]`): Class attribute.
  - `last_updated` (`Optional[str]`): Class attribute.

### `ProceduralMemory`
Holds procedural memory for multiple users keyed by user_id.

- **Attributes**:
  - `user_info` (`Dict[str, UserInfo]`): Class attribute.

### `ShortTermMemory`
Stores recent messages; each message is a mapping containing at least author_id, author, content, timestamp (numeric UNIX seconds as float).

- **Attributes**:
  - `messages` (`List[Dict[str, Any]]`): Class attribute.

### `SystemContext`
Aggregated context used to build prompts for the LLM.

- **Attributes**:
  - `short_term_memory` (`ShortTermMemory`): Class attribute.
  - `procedural_memory` (`ProceduralMemory`): Class attribute.
  - `current_channel_name` (`str`): Class attribute.
  - `timestamp` (`float`): Class attribute.
