# File: `cogs/help.py`

## Overview
Core module for help.py.

## Classes

### `HelpCog`
Class representing HelpCog.

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `lang_manager` (`Optional[LanguageManager]`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: Any) -> Any`: Method __init__.
  - `cog_load(self) -> Any`: 當 Cog 載入時初始化語言管理器
  - `_translate(self, guild_id: str, *keys: str, default: str) -> str`: Helper to translate with a safe fallback when keys are missing.
  - `_chunk_field_values(self, lines: List[str], limit: int) -> List[str]`: Split command lines into chunks that respect Discord's 1024-char field limit.
  - `_create_embed_page(self, title: str, description: Optional[str]) -> discord.Embed`: Create a new embed page for the help command.
  - `_build_help_embeds(self, guild_id: str, title: str, description: str) -> List[discord.Embed]`: Construct one or more embeds while respecting Discord limits.
  - `help_command(self, interaction: discord.Interaction) -> Any`: Method help_command.

## Functions

### `setup(bot: Any) -> Any`
Function setup.
