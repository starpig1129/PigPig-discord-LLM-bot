# File: `llm/tools/system_prompt_tools.py`

## Overview
LangChain tool for the bot to modify its own system prompt.

The LLM reads its current personality from the system-prompt context it
already has, generates a merged version, and calls this tool to write it.
Only the write side lives here — no extra LLM call is needed.

## Classes

### `SystemPromptTools`
Container for the bot's self-modification tool.

- **Attributes**:
  - `runtime` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, runtime: 'OrchestratorRequest') -> None`: Initialize with the orchestrator runtime context.
  - `get_tools(self) -> list`: Return the list of self-modification tools.

## Functions

### `write_personality(guild_id: str, channel_id: str, merged_prompt: str, scope: str, bot: Any, user_id: str) -> str`
Write a merged personality string to the system prompt store.

Args:
    guild_id: Discord guild ID string.
    channel_id: Discord channel ID string.
    merged_prompt: The complete merged system prompt text.
    scope: "channel" or "server".
    bot: The discord.ext.commands.Bot instance.
    user_id: ID of the user requesting the change (for audit).

Returns:
    A human-readable confirmation or error string.
