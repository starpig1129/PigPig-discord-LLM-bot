# File: `addons/update/manager.py`

## Overview
核心更新管理器模組

整合所有更新相關功能，提供統一的更新管理介面。

## Classes

### `UpdateStatusTracker`
更新狀態追蹤器

- **Attributes**:
  - `current_status` (`Any`): Instance attribute.
  - `progress` (`Any`): Instance attribute.
  - `current_operation` (`Any`): Instance attribute.
  - `start_time` (`Any`): Instance attribute.
  - `last_check_time` (`Any`): Instance attribute.
  - `error_message` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self) -> Any`: Method __init__.
  - `update_status(self, status: str, progress: int, operation: str) -> Any`: 更新狀態
  - `set_error(self, error_message: str) -> Any`: 設定錯誤狀態
  - `reset(self) -> Any`: 重置狀態

### `UpdateLogger`
更新日誌管理器

- **Attributes**:
  - `log_dir` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.
  - `log_file` (`Any`): Instance attribute.
  - `current_log` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, log_dir: str) -> Any`: Method __init__.
  - `start_log(self, event_type: str, trigger_type: str, user_id: Optional[int]) -> Any`: 開始記錄更新事件
  - `update_log(self, **kwargs: Any) -> Any`: 更新日誌內容
  - `finish_log(self, status: str, error_message: Optional[str]) -> Any`: 完成日誌記錄
  - `_write_log(self) -> Any`: 寫入日誌檔案

### `UpdateManager`
核心更新管理器

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.
  - `update_settings` (`Any`): Instance attribute.
  - `config` (`Any`): Instance attribute.
  - `version_checker` (`Any`): Instance attribute.
  - `downloader` (`Any`): Instance attribute.
  - `permission_checker` (`Any`): Instance attribute.
  - `backup_manager` (`Any`): Instance attribute.
  - `config_protector` (`Any`): Instance attribute.
  - `notifier` (`Any`): Instance attribute.
  - `restart_manager` (`Any`): Instance attribute.
  - `status_tracker` (`Any`): Instance attribute.
  - `update_logger` (`Any`): Instance attribute.
  - `_update_lock` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: Any) -> Any`: 初始化更新管理器
  - `check_for_updates(self) -> Dict[str, Any]`: 檢查更新
  - `execute_update(self, interaction: Any, force: bool) -> Dict[str, Any]`: 執行更新流程
  - `_install_update(self, download_path: str, version: str) -> bool`: 安裝更新
  - `_verify_installation(self) -> bool`: 驗證安裝是否成功
  - `_start_auto_check(self) -> Any`: 啟動自動檢查
  - `post_restart_initialization(self) -> Any`: 重啟後初始化
