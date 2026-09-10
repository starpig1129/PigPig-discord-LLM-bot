# File: `bot.py`

## Overview
Discord bot main module.

This module contains the main bot class and configuration for a Discord bot
with music playback, message handling, and logging capabilities.

## Classes

### `PigPig`
Main Discord bot class with music, messaging, and logging features.

This bot extends discord.ext.commands.Bot with additional functionality including:
- Per-guild logging system
- Music playback state management
- AI-powered message handling
- Performance monitoring
- Dynamic status updates

Attributes:
    loggers (dict): Dictionary mapping guild names to their logger instances.
    state_manager (StateManager): Manager for music playback states.
    ui_manager (UIManager): Manager for music player UI components.
    status_cycle (itertools.cycle): Cycle iterator for rotating bot status messages.
    message_handler (MessageHandler): Handler for processing Discord messages.

- **Attributes**:
  - `loggers` (`Any`): Instance attribute.
  - `state_manager` (`Any`): Instance attribute.
  - `ui_manager` (`Any`): Instance attribute.
  - `stats_collector` (`Any`): Instance attribute.
  - `status_cycle` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, *args: Any, **kwargs: Any) -> Any`: Initialize the PigPig bot instance.
  - `change_status_task(self) -> Any`: Update bot status every 15 seconds.
  - `_change_presence(self, *args: Any, **kwargs: Any) -> Any`: Wrapper for change_presence to handle connection errors.
  - `get_logger_for_guild(self, guild_id: Any) -> Any`: Get or create logger for a specific guild.
  - `setup_logger_for_guild(self, guild_id: Any) -> Any`: Set up logger for a guild if it doesn't exist.
  - `on_message(self, message: discord.Message) -> None`: Handle incoming Discord messages.
  - `on_message_edit(self, before: discord.Message, after: discord.Message) -> Any`: Handle edited Discord messages.
  - `setup_hook(self) -> None`: Set up bot before connecting to Discord.
  - `on_ready(self) -> Any`: Handle bot ready event.
  - `on_error(self, event_method: str, *args: Any, **kwargs: Any) -> Any`: Handle errors in event handlers.
  - `on_command_error(self, ctx: commands.Context, error: commands.CommandError) -> Any`: Handle errors in command execution.
  - `send_error_report(self, embed: discord.Embed) -> Any`: Method send_error_report.
  - `close(self) -> Any`: Gracefully shut down the bot and all systems.
