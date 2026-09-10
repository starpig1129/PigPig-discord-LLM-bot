# File: `cogs/botinfo.py`

## Overview
Core module for botinfo.py.

## Classes

### `BotInfo`
Cog for displaying bot information and system statistics.

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `start_time` (`Any`): Instance attribute.
  - `lang_manager` (`Optional[LanguageManager]`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: Any) -> Any`: Method __init__.
  - `cog_load(self) -> Any`: Initialize LanguageManager when the cog is loaded.
  - `_format_uptime(self, uptime: Any, guild_id: str) -> Any`: Format uptime duration into a localized human-readable string.
  - `botinfo(self, interaction: discord.Interaction) -> Any`: Display comprehensive bot information and performance metrics.

## Functions

### `setup(bot: Any) -> Any`
Set up the BotInfo cog.
