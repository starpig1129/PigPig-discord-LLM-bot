# File: `addons/update/checker.py`

## Overview
版本檢查器模組

負責檢查 GitHub 上的最新版本並與當前版本進行比較。

## Classes

### `VersionChecker`
版本檢查器

- **Attributes**:
  - `github_api_url` (`Any`): Instance attribute.
  - `current_version` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, github_config: Dict[str, str]) -> Any`: 初始化版本檢查器
  - `_get_current_version(self) -> str`: 獲取當前版本
  - `check_for_updates(self) -> Dict[str, any]`: 檢查是否有可用更新
  - `_compare_versions(self, current: str, latest: str) -> bool`: 比較版本號
  - `_get_error_result(self, error_message: str) -> Dict[str, any]`: 獲取錯誤結果
