# File: `llm/tools/knowledge.py`

## Overview
Knowledge tools for managing guild and channel level memories.

This module provides tools for the LLM to store and update shared information
like inside jokes, relationships, aliases, and special events.

## Classes

### `UpdateKnowledgeInput`
Input for updating knowledge.

- **Attributes**:
  - `new_information` (`str`): Class attribute.
  - `category` (`str`): Class attribute.

### `UpdateGuildKnowledgeTool`
Tool to update knowledge shared across the entire server.

- **Attributes**:
  - `name` (`str`): Class attribute.
  - `description` (`str`): Class attribute.
  - `args_schema` (`Type[BaseModel]`): Class attribute.
  - `runtime` (`Optional[Any]`): Class attribute.

- **Methods**:
  - `_run(self, new_information: str, category: str) -> str`: Synchronous run (not used).
  - `_arun(self, new_information: str, category: str) -> str`: Update guild-level knowledge.

### `UpdateChannelKnowledgeTool`
Tool to update knowledge specific to the current channel.

- **Attributes**:
  - `name` (`str`): Class attribute.
  - `description` (`str`): Class attribute.
  - `args_schema` (`Type[BaseModel]`): Class attribute.
  - `runtime` (`Optional[Any]`): Class attribute.

- **Methods**:
  - `_run(self, new_information: str, category: str) -> str`: Synchronous run (not used).
  - `_arun(self, new_information: str, category: str) -> str`: Update channel-level knowledge.

### `ClearKnowledgeInput`
Input for clearing knowledge.

- **Attributes**:
  - `dummy` (`Optional[str]`): Class attribute.

### `ClearGuildKnowledgeTool`
Tool to clear all knowledge shared across the entire server.

- **Attributes**:
  - `name` (`str`): Class attribute.
  - `description` (`str`): Class attribute.
  - `args_schema` (`Type[BaseModel]`): Class attribute.
  - `runtime` (`Optional[Any]`): Class attribute.

- **Methods**:
  - `_run(self, dummy: Optional[str]) -> str`: Synchronous run (not used).
  - `_arun(self, dummy: Optional[str]) -> str`: Clear guild-level knowledge.

### `ClearChannelKnowledgeTool`
Tool to clear knowledge specific to the current channel.

- **Attributes**:
  - `name` (`str`): Class attribute.
  - `description` (`str`): Class attribute.
  - `args_schema` (`Type[BaseModel]`): Class attribute.
  - `runtime` (`Optional[Any]`): Class attribute.

- **Methods**:
  - `_run(self, dummy: Optional[str]) -> str`: Synchronous run (not used).
  - `_arun(self, dummy: Optional[str]) -> str`: Clear channel-level knowledge.

### `KnowledgeTools`
Wrapper class for discovering knowledge management tools.
Supported by the factory but get_tools() is preferred.

- **Attributes**:
  - `runtime` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, runtime: Any) -> None`: Method __init__.

## Functions

### `get_tools(runtime: Any) -> list`
Discovery function for the tools factory.
