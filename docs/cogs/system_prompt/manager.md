# File: `cogs/system_prompt/manager.py`

## Overview
Channel system prompt manager.

Provides core system prompt management functionality, including three-level inheritance,
caching system, and configuration management.

## Classes

### `SystemPromptCache`
System prompt cache manager.

- **Attributes**:
  - `cache` (`Dict[str, Tuple[float, str]]`): Instance attribute.
  - `ttl` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, ttl: int) -> Any`: Initialize cache manager.
  - `get(self, guild_id: str, channel_id: str, lang: str) -> Optional[str]`: Get system prompt from cache.
  - `set(self, guild_id: str, channel_id: str, prompt: str, lang: str) -> None`: Set cache.
  - `invalidate(self, guild_id: str, channel_id: Optional[str]) -> None`: Invalidate cache.
  - `clear_all(self) -> None`: Clear all cache.

### `PromptValidator`
System prompt validator.

- **Attributes**:
  - `bot` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: discord.Client) -> Any`: Initialize system prompt validator.
  - `validate_prompt_content(self, content: str) -> Tuple[bool, str]`: Validate prompt content.
  - `validate_modules(self, modules: Dict[str, str], guild_id: Optional[str]) -> Tuple[bool, str]`: Validate module configuration.

### `SystemPromptManager`
System prompt manager - Core coordinator.

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.
  - `cache` (`Any`): Instance attribute.
  - `validator` (`Any`): Instance attribute.
  - `permission_validator` (`Any`): Instance attribute.
  - `data_dir` (`Any`): Instance attribute.
  - `_prompt_manager` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: discord.Client) -> Any`: Initialize system prompt manager.
  - `_init_prompt_manager(self) -> None`: Initialize YAML prompt manager.
  - `remove_channel_prompt(self, guild_id: str, channel_id: str) -> bool`: 移除頻道系統提示
  - `remove_server_prompt(self, guild_id: str) -> bool`: 移除伺服器級別系統提示
  - `copy_channel_prompt(self, source_guild: str, source_channel: str, target_guild: str, target_channel: str) -> bool`: 複製頻道提示設定
  - `get_module_descriptions(self, lang: str) -> Dict[str, str]`: 獲取模組說明字典
  - `clear_cache(self, guild_id: Optional[str], channel_id: Optional[str]) -> None`: 清除快取（全面同步清除）
  - `force_clear_all_caches(self, guild_id: str, channel_id: Optional[str], interaction: Optional[object]) -> None`: 強制清除所有相關快取（整合版）- 異步版本
  - `_enhanced_force_clear_all_caches(self, guild_id: str, channel_id: Optional[str]) -> None`: 增強的強制清除所有相關快取方法（整合版）
  - `_legacy_force_clear_all_caches(self, guild_id: str, channel_id: Optional[str]) -> None`: 原有的強制清除所有相關快取方法（降級使用）
  - `reload_system_prompts(self, guild_id: str, channel_id: Optional[str]) -> bool`: 重新載入系統提示配置（完整重新載入方案）
  - `_clear_yaml_prompt_cache(self, guild_id: Optional[str], channel_id: Optional[str]) -> None`: 清除 YAML PromptManager 的相關快取
  - `_force_clear_yaml_cache(self, guild_id: str) -> None`: 強制清除 YAML PromptManager 的所有相關快取
  - `_force_clear_sendmessage_cache(self, guild_id: str, channel_id: Optional[str]) -> None`: 強制清除 prompting 模組的所有相關快取
  - `_clear_hidden_caches(self, guild_id: str, channel_id: Optional[str]) -> None`: 清除可能的隱藏快取層級
  - `_deep_cache_cleanup(self, guild_id: str, channel_id: Optional[str]) -> None`: 深度快取清理（額外的清除策略）
  - `_reinitialize_components(self) -> None`: 重新初始化相關組件
  - `_verify_reload_result(self, guild_id: str, channel_id: Optional[str]) -> bool`: 驗證重新載入結果
  - `_load_guild_config(self, guild_id: str) -> Dict[str, Any]`: 載入伺服器配置
  - `_save_guild_config(self, guild_id: str, config: Dict[str, Any]) -> None`: 保存伺服器配置
  - `_get_default_config(self) -> Dict[str, Any]`: 取得預設配置
  - `_get_yaml_prompt(self, guild_id: str, message: Optional[discord.Message]) -> Dict[str, Any]`: 取得 YAML 基礎提示
  - `_append_protected_suffix(self, prompt: str) -> str`: Re-appends critical protected modules (output_format, reminders) from base YAML.
  - `_apply_server_overrides(self, base_prompt: str, server_config: Dict[str, Any], guild_id: Optional[str]) -> str`: 應用伺服器級別覆蓋
  - `_apply_channel_overrides(self, base_prompt: str, channel_config: Dict[str, Any], guild_id: Optional[str]) -> str`: 應用頻道級別覆蓋
  - `_apply_language_localization(self, prompt: str, lang: str, guild_id: str) -> str`: 應用語言本地化
  - `_rebuild_prompt_with_module_overrides(self, module_overrides: Dict[str, str], override_modules: List[str]) -> str`: 使用模組覆蓋重新建構 YAML 提示
  - `_apply_variable_replacements(self, prompt: str, guild_id: Optional[str]) -> str`: 對系統提示應用變數替換
  - `_get_system_variables(self) -> Dict[str, Any]`: 獲取系統變數字典
  - `_get_language(self, guild_id: str, message: Optional[discord.Message]) -> str`: 取得語言設定
  - `debug_cache_state(self, guild_id: str, channel_id: str) -> Dict[str, Any]`: 快取狀態除錯（供管理員使用）
  - `handle_discord_interaction_cache_issues(self, interaction: Any) -> Dict[str, Any]`: 處理 Discord 互動的快取問題（整合版）
  - `reload_all_configs(self) -> bool`: 重新載入所有配置（用於 UI 介面）
