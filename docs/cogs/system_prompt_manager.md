# File: `cogs/system_prompt_manager.py`

## Overview
頻道系統提示管理模組的主要 Cog

這個檔案作為系統提示管理模組的入口點，整合所有功能組件。

## Classes

### `SystemPromptManagerCog`
系統提示管理主要 Cog 類別

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.
  - `manager` (`Any`): Instance attribute.
  - `permission_validator` (`Any`): Instance attribute.
  - `commands_cog` (`Any`): Instance attribute.
  - `language_manager` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: commands.Bot) -> Any`: 初始化系統提示管理 Cog
  - `_get_language_manager(self) -> Any`: 安全地取得語言管理器實例
  - `_translate(self, guild_id: str, *keys: Any) -> Any`: 安全的翻譯方法，使用 getattr 避免類型檢查問題
  - `cog_load(self) -> Any`: Cog 載入時的初始化
  - `cog_unload(self) -> Any`: Cog 卸載時的清理
  - `validate_user_permission(self, user: discord.Member, action: str, target: any) -> bool`: 驗證用戶權限（供外部模組調用的便利方法）
  - `on_guild_join(self, guild: discord.Guild) -> Any`: 當機器人加入新伺服器時的處理
  - `on_guild_remove(self, guild: discord.Guild) -> Any`: 當機器人離開伺服器時的處理
  - `system_prompt_status(self, ctx: Any) -> Any`: View system prompt module status (bot owner only)
  - `clear_system_prompt_cache(self, ctx: Any, guild_id: Optional[str]) -> Any`: Clear system prompt cache (bot owner only)

## Functions

### `setup(bot: Any) -> Any`
設定函式，用於載入 Cog
