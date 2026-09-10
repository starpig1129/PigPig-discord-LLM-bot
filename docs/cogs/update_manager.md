# File: `cogs/update_manager.py`

## Overview
Discord 更新管理 Cog

提供 Discord 命令介面來管理自動更新系統。

## Classes

### `UpdateManagerCog`
Discord 更新管理介面

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.
  - `lang_manager` (`Optional[LanguageManager]`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: Any) -> Any`: 初始化更新管理 Cog
  - `cog_load(self) -> Any`: Cog 載入時初始化語言管理器
  - `_get_translation(self, guild_id: str, *keys: Any, **kwargs: Any) -> str`: 取得翻譯文字的安全方法
  - `check_update(self, interaction: discord.Interaction) -> Any`: 檢查更新命令
  - `update_now(self, interaction: discord.Interaction, force: bool) -> Any`: 立即更新命令
  - `update_status(self, interaction: discord.Interaction) -> Any`: 更新狀態查詢
  - `configure_update(self, interaction: discord.Interaction) -> Any`: 更新配置命令
  - `_create_status_embed(self, status: dict, guild_id: str) -> discord.Embed`: 創建狀態嵌入

### `UpdateActionView`
更新操作視圖

- **Attributes**:
  - `update_manager` (`Any`): Instance attribute.
  - `guild_id` (`Any`): Instance attribute.
  - `get_translation` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, update_manager: Any, guild_id: str, get_translation_func: Any) -> Any`: Method __init__.
  - `update_now(self, interaction: discord.Interaction, button: discord.ui.Button) -> Any`: 立即更新按鈕
  - `remind_later(self, interaction: discord.Interaction, button: discord.ui.Button) -> Any`: 稍後提醒按鈕

### `UpdateConfirmView`
更新確認視圖

- **Attributes**:
  - `update_manager` (`Any`): Instance attribute.
  - `version_info` (`Any`): Instance attribute.
  - `guild_id` (`Any`): Instance attribute.
  - `get_translation` (`Any`): Instance attribute.
  - `force` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, update_manager: Any, version_info: Any, guild_id: str, get_translation_func: Any, force: Any) -> Any`: Method __init__.
  - `confirm_update(self, interaction: discord.Interaction, button: discord.ui.Button) -> Any`: 確認更新按鈕
  - `cancel_update(self, interaction: discord.Interaction, button: discord.ui.Button) -> Any`: 取消更新按鈕
  - `_execute_update(self, interaction: Any) -> Any`: 執行更新

### `UpdateConfigView`
更新配置視圖

- **Attributes**:
  - `update_manager` (`Any`): Instance attribute.
  - `guild_id` (`Any`): Instance attribute.
  - `get_translation` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, update_manager: Any, guild_id: str, get_translation_func: Any) -> Any`: Method __init__.
  - `toggle_auto_update(self, interaction: discord.Interaction, button: discord.ui.Button) -> Any`: 切換自動更新開關
  - `set_check_interval(self, interaction: discord.Interaction, button: discord.ui.Button) -> Any`: 設定檢查間隔

## Functions

### `setup(bot: Any) -> Any`
設定 Cog
