# File: `cogs/system_prompt/cache_checker.py`

## Overview
快取一致性檢查工具

提供快取系統的一致性檢查和修復功能

## Classes

### `CacheConsistencyChecker`
快取一致性檢查器

- **Attributes**:
  - `cache_manager` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, cache_manager: Any) -> Any`: Method __init__.
  - `check_cache_consistency(self, guild_id: str, channel_id: str, expected_content: str) -> Dict[str, Any]`: 檢查快取一致性
  - `force_cache_refresh(self, guild_id: str, channel_id: str) -> bool`: 強制重新整理快取
