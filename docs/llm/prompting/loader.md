# File: `llm/prompting/loader.py`

## Overview
Core module for loader.py.

## Classes

### `PromptLoader`
YAML 提示配置載入器

- **Attributes**:
  - `config_path` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.
  - `_cached_config` (`Optional[Dict[str, Any]]`): Instance attribute.
  - `_last_loaded` (`Optional[datetime]`): Instance attribute.

- **Methods**:
  - `__init__(self, config_path: str) -> Any`: 初始化載入器
  - `load_yaml_config(self) -> Dict[str, Any]`: 載入 YAML 配置檔案
  - `reload_if_changed(self) -> bool`: 檢查檔案是否變更，如有變更則重新載入
  - `get_cached_config(self) -> Optional[Dict[str, Any]]`: Get the cached configuration.
  - `is_config_loaded(self) -> bool`: Check whether a configuration has been loaded into the cache.
  - `get_config_section(self, section_name: str) -> Optional[Dict[str, Any]]`: Retrieve a specific section from the configuration.
  - `validate_config_structure(self, config: Dict[str, Any]) -> bool`: 驗證配置結構的基本完整性
