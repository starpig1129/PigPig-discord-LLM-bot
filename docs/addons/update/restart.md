# File: `addons/update/restart.py`

## Overview
簡單可靠的重啟管理模組

採用直接、簡單但可靠的重啟機制，放棄複雜的進程分離方案。
使用系統級重啟命令和強制退出機制確保重啟成功。

## Classes

### `SimpleRestartManager`
簡單可靠的重啟管理器

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.
  - `restart_config` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: Any, restart_config: Optional[Dict[str, Any]]) -> Any`: 初始化重啟管理器
  - `execute_restart(self, reason: str) -> None`: 執行簡單重啟流程
  - `post_restart_check(self) -> bool`: 重啟後檢查
  - `_save_restart_flag(self, reason: str) -> None`: 保存重啟標記
  - `_notify_restart(self) -> None`: 通知即將重啟
  - `_shutdown_bot(self) -> None`: 關閉 Bot
  - `_execute_simple_restart(self) -> None`: 執行簡單重啟
  - `_windows_simple_restart(self, python_exe: str, current_dir: str) -> bool`: Windows 簡單重啟方法
  - `_unix_simple_restart(self, python_exe: str, current_dir: str) -> bool`: Unix/Linux 簡單重啟方法
  - `_simple_health_check(self) -> bool`: 簡單健康檢查
  - `_notify_restart_success(self, restart_info: Dict[str, Any]) -> None`: 通知重啟成功
  - `_notify_restart_failure(self, error: Exception) -> None`: 通知重啟失敗
  - `_handle_restart_failure(self, error: Exception) -> None`: 處理重啟失敗
  - `_create_emergency_restart_file(self) -> None`: 創建緊急重啟指示文件
  - `is_restart_pending(self) -> bool`: 檢查是否有待處理的重啟
  - `get_restart_info(self) -> Optional[Dict[str, Any]]`: 獲取重啟資訊
  - `cancel_restart(self) -> bool`: 取消重啟
