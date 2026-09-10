# File: `addons/update/downloader.py`

## Overview
更新下載管理器模組

負責安全地下載更新檔案，包括進度追蹤、檔案驗證和錯誤處理。

## Classes

### `UpdateDownloader`
更新下載管理器

- **Attributes**:
  - `download_dir` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, download_dir: str) -> Any`: 初始化下載管理器
  - `download_update(self, download_url: str, progress_callback: Optional[Callable[Any, Awaitable[None]]], chunk_size: int) -> str`: 下載更新檔案
  - `_verify_download(self, filepath: str, expected_size: int) -> bool`: 驗證下載的檔案
  - `calculate_file_hash(self, filepath: str, algorithm: str) -> str`: 計算檔案雜湊值
  - `cleanup_downloads(self, keep_latest: int) -> None`: 清理下載目錄中的舊檔案
