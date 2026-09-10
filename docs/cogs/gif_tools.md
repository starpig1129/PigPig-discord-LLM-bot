# File: `cogs/gif_tools.py`

## Overview
Core module for gif_tools.py.

## Classes

### `GifTools`
GIF 搜尋與管理工具。

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `tenor_api_key` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.
  - `lang_manager` (`Optional[LanguageManager]`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: Any) -> Any`: Method __init__.
  - `cog_load(self) -> Any`: 當 Cog 載入時初始化語言管理器
  - `search_gif(self, query: str, limit: int, guild_id: str) -> list`: 搜尋 GIF。
  - `search_gif_command(self, interaction: discord.Interaction, query: str) -> Any`: Discord 指令: 搜尋 GIF。

## Functions

### `setup(bot: Any) -> Any`
Function setup.
