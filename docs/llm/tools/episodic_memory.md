# File: `llm/tools/episodic_memory.py`

## Overview
Core module for episodic_memory.py.

## Classes

### `EpisodicMemoryTools`
Container for episodic memory tools bound to a runtime.

This class provides LangChain-compatible tools that allow an LLM Agent
to query the long-term episodic memory (semantic vector store) managed
by the bot's VectorManager.

Usage:
    tools = EpisodicMemoryTools(runtime).get_tools()

- **Attributes**:
  - `runtime` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, runtime: Any) -> Any`: Method __init__.
  - `_get_bot(self) -> Optional[Any]`: Safely retrieve the bot instance from the runtime.
  - `get_tools(self) -> List`: Return a list of LangChain tools (closures) bound to the runtime.
