# File: `llm/prompting/manager.py`

## Overview
Core module for manager.py.

## Classes

### `PromptManager`
YAML 基礎的系統提示管理器

- **Attributes**:
  - `config_path` (`Any`): Instance attribute.
  - `loader` (`Any`): Instance attribute.
  - `cache` (`Any`): Instance attribute.
  - `builder` (`Any`): Instance attribute.
  - `file_watcher` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.
  - `_initialized` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, config_path: str) -> Any`: 初始化提示管理器
  - `_initialize(self) -> Any`: 初始化管理器
  - `_validate_config(self, config: dict) -> bool`: 驗證配置的基本結構
  - `_get_language_key(self, message: Any) -> str`: 取得語言鍵值用於快取
  - `_apply_dynamic_replacements(self, prompt: str, bot_id: str, message: Any) -> str`: 套用動態替換（整合現有語言管理功能）
  - `_get_fallback_prompt(self, bot_id: str) -> str`: 降級策略：使用硬編碼的基本提示
  - `reload_prompts(self) -> bool`: 重新載入提示配置
  - `_on_config_changed(self, path: str) -> Any`: 配置檔案變更回調
  - `compose_prompt(self, modules: Optional[List[str]]) -> str`: 組合指定模組的提示內容
  - `validate_modules(self, modules: List[str]) -> Dict[str, bool]`: 驗證模組是否存在
  - `cleanup(self) -> Any`: 清理資源

## Functions

### `get_prompt_manager(config_path: str) -> PromptManager`
取得指定 config_path 的 PromptManager 實例（若不存在則建立並快取）。
這樣可以支援多個不同 agent 的配置檔案，而不會互相覆寫單一全域實例。

Args:
    config_path: 配置檔案路徑

Returns:
    PromptManager 實例
