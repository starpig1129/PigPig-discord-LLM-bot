# File: `llm/orchestrator.py`

## Overview
Core module for orchestrator.py.

## Classes

### `DirectToolOutputMiddleware`
Class representing DirectToolOutputMiddleware.

- **Methods**:
  - `after_tools(self, state: Any, runtime: Any) -> Any`: Method after_tools.

### `Orchestrator`
Orchestrator updated to accept ContextManager's new return type.

ContextManager.get_context now returns Tuple[str, List[BaseMessage]]:
  (procedural_context_str, short_term_msgs)

Short-term memory (short_term_msgs) is passed directly as LangChain
BaseMessage objects into agents' `messages` parameter to preserve
structure and avoid double-serialization.

- **Attributes**:
  - `model_manager` (`Any`): Instance attribute.
  - `bot` (`Any`): Instance attribute.
  - `context_manager` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: Any) -> Any`: Initialize model manager and context manager.
  - `_build_info_agent_prompt(self, bot_id: int, message: Message) -> str`: Build system prompt for info_agent from settings with fallback.
  - `_get_info_agent_fallback_prompt(self, bot_id: int) -> str`: Method _get_info_agent_fallback_prompt.
  - `_build_message_agent_prompt(self, bot_id: int, message: Message) -> str`: Build system prompt for message_agent using ProtectedPromptManager.
  - `_build_action_tools_rules(tools: List[Any]) -> str`: Inject behavioral rules for message-mode action tools.
  - `_sanitize_messages_for_model(self, messages: List[BaseMessage], model_name: str, image_cache: Optional[MutableMapping[str, dict[str, Any]]]) -> List[BaseMessage]`: Sanitize messages for the specific model.
  - `handle_message(self, bot: Any, message_edit: Message, message: Message, logger: Any, announce_new_version: bool) -> OrchestratorResponse`: Main entrypoint for handling an incoming Discord message.
