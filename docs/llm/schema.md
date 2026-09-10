# File: `llm/schema.py`

## Overview
LangChain compatible data schemas.

This file defines the Pydantic models for receiving Discord requests and returning responses.

## Classes

### `OrchestratorRequest`
Class representing OrchestratorRequest.

- **Attributes**:
  - `bot` (`Any`): Class attribute.
  - `message` (`Message`): Class attribute.
  - `logger` (`Any`): Class attribute.
  - `announce_new_version` (`bool`): Class attribute.

### `OrchestratorResponse`
Response model returned by the orchestrator.

Attributes:
    reply: The agent's reply or structured response (type varies by provider).
    tool_calls: Optional list of tool call records represented as dicts.

- **Attributes**:
  - `reply` (`Any | None`): Class attribute.
  - `tool_calls` (`List[Dict] | None`): Class attribute.
