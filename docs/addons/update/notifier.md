# File: `addons/update/notifier.py`

## Overview
Discord 通知系統模組

負責發送更新相關的通知給 Bot 擁有者和管理員。

## Classes

### `DiscordNotifier`
Discord 通知系統

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.
  - `owner_id` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: Any) -> Any`: 初始化通知系統
  - `_get_bot_owner_safely(self) -> Optional[discord.User]`: 安全地獲取 Bot 擁有者
  - `notify_update_available(self, version_info: Dict[str, Any]) -> bool`: 通知有新版本可用
  - `notify_update_progress(self, stage: str, progress: int, details: str) -> bool`: 通知更新進度
  - `notify_update_complete(self, result: Dict[str, Any]) -> bool`: 通知更新完成
  - `notify_update_error(self, error: Exception, context: str) -> bool`: 通知更新錯誤
  - `notify_restart_success(self, restart_info: Dict[str, Any]) -> bool`: 通知重啟成功
  - `_create_progress_bar(self, progress: int, length: int) -> str`: 創建進度條
  - `send_channel_notification(self, channel_id: int, embed: discord.Embed) -> bool`: 發送頻道通知

### `QuickUpdateView`
快速更新視圖

- **Methods**:
  - `__init__(self) -> Any`: Method __init__.
  - `quick_update(self, interaction: discord.Interaction, button: discord.ui.Button) -> Any`: 快速更新按鈕
  - `remind_later(self, interaction: discord.Interaction, button: discord.ui.Button) -> Any`: 稍後提醒按鈕
  - `ignore_update(self, interaction: discord.Interaction, button: discord.ui.Button) -> Any`: 忽略更新按鈕
