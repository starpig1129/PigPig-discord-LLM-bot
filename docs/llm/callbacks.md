# File: `llm/callbacks.py`

## Overview
Core module for callbacks.py.

## Classes

### `ToolFeedbackCallbackHandler`
Callback handler for providing feedback during tool execution.

- **Attributes**:
  - `message_edit` (`Any`): Instance attribute.
  - `language_manager` (`Any`): Instance attribute.
  - `guild_id` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, message_edit: Any, language_manager: Any, guild_id: str) -> Any`: Method __init__.
  - `on_tool_start(self, serialized: Dict[str, Any], input_str: str, run_id: UUID, parent_run_id: Optional[UUID], tags: Optional[List[str]], metadata: Optional[Dict[str, Any]], **kwargs: Any) -> Any`: Run when tool starts running.
