# File: `cogs/system_prompt/commands.py`

## Overview
頻道系統提示管理模組的 Discord 斜線命令

提供完整的 Discord 斜線命令介面，包含所有系統提示管理功能。

## Classes

### `SystemPromptCommands`
系統提示管理命令類別

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.
  - `manager` (`Any`): Instance attribute.
  - `permission_validator` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: discord.Client) -> Any`: 初始化命令類別
  - `system_prompt(self, interaction: discord.Interaction) -> Any`: 統一的系統提示管理命令 - 主選單介面
  - `set_personality(self, interaction: discord.Interaction, scope: app_commands.Choice[str], description: str) -> None`: Slash command to adjust bot personality via natural language description.

## Functions

### `handle_system_prompt_error(func: Any) -> Any`
系統提示錯誤處理裝飾器

### `setup(bot: Any) -> Any`
設定函式，用於載入 Cog
