# File: `llm/utils/file_watcher.py`

## Overview
Core module for file_watcher.py.

## Classes

### `FileWatcher`
檔案監控和熱重載

- **Attributes**:
  - `watched_files` (`Dict[str, datetime]`): Instance attribute.
  - `callbacks` (`Dict[str, Callable]`): Instance attribute.
  - `check_interval` (`Any`): Instance attribute.
  - `_running` (`Any`): Instance attribute.
  - `_thread` (`Any`): Instance attribute.
  - `_lock` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, check_interval: float) -> Any`: 初始化檔案監控器
  - `watch_file(self, path: str, callback: Callable) -> Any`: 監控檔案變更
  - `_start_watching(self) -> Any`: 開始監控執行緒
  - `_watch_loop(self) -> Any`: 監控迴圈
  - `stop_watching(self) -> Any`: 停止監控
  - `check_changes(self) -> bool`: 手動檢查變更
  - `add_file(self, path: str, callback: Callable) -> Any`: 添加要監控的檔案（watch_file 的別名）
  - `remove_file(self, path: str) -> Any`: 移除監控檔案
  - `is_watching(self, path: str) -> bool`: 檢查是否正在監控指定檔案
