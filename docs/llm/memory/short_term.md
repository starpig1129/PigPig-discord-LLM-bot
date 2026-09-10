# File: `llm/memory/short_term.py`

## Overview
Core module for short_term.py.

## Classes

### `ShortTermMemoryProvider`
Provides short-term memory as a list of LangChain messages.

The provider fetches recent message history from the channel and converts
each Discord message to a LangChain HumanMessage or AIMessage.

- **Attributes**:
  - `limit` (`Any`): Instance attribute.
  - `bot` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: Any, limit: int) -> Any`: Initialize the provider.
  - `get(self, message: discord.Message) -> List[BaseMessage]`: Fetch recent messages and return as LangChain BaseMessage list.
