# File: `llm/tools/tools_overview.py`

## Overview
Core module for tools_overview.py.

## Classes

### `ToolsOverviewTools`
Container for a tool that lists available tools and their short descriptions.

Usage:
    tools = ToolsOverviewTools(runtime).get_tools()

- **Attributes**:
  - `runtime` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, runtime: Any) -> Any`: Method __init__.
  - `get_tools(self) -> List`: Return a list containing a single tool that summarizes available tools.
