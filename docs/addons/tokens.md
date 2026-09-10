# File: `addons/tokens.py`

## Overview
Core module for tokens.py.

## Classes

### `TOKENS`
Class representing TOKENS.

- **Attributes**:
  - `token` (`Any`): Instance attribute.
  - `client_id` (`Any`): Instance attribute.
  - `client_secret_id` (`Any`): Instance attribute.
  - `secret_key` (`Any`): Instance attribute.
  - `bug_report_channel_id` (`Any`): Instance attribute.
  - `anthropic_api_key` (`Any`): Instance attribute.
  - `openai_api_key` (`Any`): Instance attribute.
  - `google_api_key` (`Any`): Instance attribute.
  - `tenor_api_key` (`Any`): Instance attribute.
  - `vllm_api_key` (`Any`): Instance attribute.
  - `vector_store_api_key` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self) -> None`: Method __init__.
  - `_validate_environment_variables(self) -> None`: Verify all required environment variables exist and are valid; terminate if validation fails.
