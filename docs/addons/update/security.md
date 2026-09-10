# File: `addons/update/security.py`

## Overview
安全控制模組

負責權限驗證、備份管理和回滾機制。

## Classes

### `UpdatePermissionChecker`
更新權限檢查器

- **Attributes**:
  - `bot_owner_id` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self) -> Any`: 初始化權限檢查器
  - `check_update_permission(self, user_id: int) -> bool`: 檢查更新權限 - 僅限 Bot 擁有者
  - `check_status_permission(self, interaction: discord.Interaction) -> bool`: 檢查狀態查看權限 - 管理員或擁有者

### `BackupManager`
備份管理器

- **Attributes**:
  - `backup_dir` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, backup_dir: str) -> Any`: 初始化備份管理器
  - `create_backup(self, protected_files: Optional[List[str]]) -> str`: 創建當前版本備份
  - `_backup_directory_safely(self, source_dir: str, dest_dir: str, backup_root: str) -> None`: 安全地備份目錄，避免備份目錄本身造成無限遞歸
  - `rollback_to_backup(self, backup_id: str) -> bool`: 回滾到指定備份
  - `list_backups(self) -> List[dict]`: 列出所有可用的備份
  - `cleanup_old_backups(self, max_backups: int) -> None`: 清理過期備份
  - `get_backup_size(self, backup_id: str) -> int`: 獲取備份大小

### `ConfigProtector`
配置檔案保護器

- **Attributes**:
  - `logger` (`Any`): Instance attribute.
  - `protected_files` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self) -> Any`: 初始化配置保護器
  - `backup_configs(self, backup_path: str) -> bool`: 備份配置檔案
  - `restore_configs(self, backup_path: str) -> bool`: 恢復配置檔案
  - `verify_configs(self) -> bool`: 驗證配置檔案完整性
