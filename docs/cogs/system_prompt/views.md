# File: `cogs/system_prompt/views.py`

## Overview
系統提示管理的統一 UI 選單系統

提供全新的統一介面，整合所有系統提示管理功能和模組化編輯。

## Classes

### `LocalizedView`
Base class for all system-prompt views.

Provides :meth:`_t` for translating strings at construction time using
the server's configured language.

- **Attributes**:
  - `manager` (`Any`): Instance attribute.
  - `guild_id` (`Any`): Instance attribute.
  - `_bot` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, manager: 'SystemPromptManager', guild_id: str, timeout: float) -> Any`: Method __init__.
  - `_t(self, *keys: str, fallback: str) -> str`: Translate *keys* using the guild's language.

### `SystemPromptMainView`
系統提示管理主選單

- **Attributes**:
  - `permission_validator` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, manager: SystemPromptManager, permission_validator: PermissionValidator, guild_id: str, timeout: float) -> Any`: Method __init__.
  - `_setup_main_buttons(self) -> Any`: 設定主要功能按鈕
  - `function_callback(self, interaction: discord.Interaction, function: str) -> Any`: 處理功能按鈕回調
  - `_handle_set_function(self, interaction: discord.Interaction) -> Any`: Method _handle_set_function.
  - `_handle_view_function(self, interaction: discord.Interaction) -> Any`: Method _handle_view_function.
  - `_handle_copy_function(self, interaction: discord.Interaction) -> Any`: Method _handle_copy_function.
  - `_handle_remove_function(self, interaction: discord.Interaction) -> Any`: Method _handle_remove_function.
  - `_handle_reset_function(self, interaction: discord.Interaction) -> Any`: Method _handle_reset_function.
  - `_handle_reload_function(self, interaction: discord.Interaction) -> Any`: Method _handle_reload_function.

### `SystemPromptFunctionButton`
系統提示功能按鈕

- **Attributes**:
  - `function` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, function: str, **kwargs: Any) -> Any`: Method __init__.
  - `callback(self, interaction: discord.Interaction) -> Any`: 按鈕回調

### `SystemPromptSetView`
設定系統提示的子選單

- **Attributes**:
  - `permission_validator` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, manager: SystemPromptManager, permission_validator: PermissionValidator, guild_id: str, timeout: float) -> Any`: Method __init__.
  - `scope_callback(self, interaction: discord.Interaction, scope: str) -> Any`: Method scope_callback.

### `EditModeSelectionView`
編輯模式選擇選單

- **Attributes**:
  - `permission_validator` (`Any`): Instance attribute.
  - `scope` (`Any`): Instance attribute.
  - `target_channel` (`Any`): Instance attribute.
  - `scope_text` (`Any`): Instance attribute.
  - `guild` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, manager: SystemPromptManager, permission_validator: PermissionValidator, scope: str, target_channel: Optional[discord.TextChannel], scope_text: str, guild: discord.Guild, guild_id: str, timeout: float) -> Any`: Method __init__.
  - `edit_mode_callback(self, interaction: discord.Interaction, edit_mode: str) -> Any`: 處理編輯模式選擇
  - `_handle_direct_edit(self, interaction: discord.Interaction) -> Any`: 處理直接編輯提示
  - `_restore_variable_placeholders(self, prompt: str, guild_id: str) -> str`: 將已替換的變數還原為占位符格式，以便編輯時顯示原始模板
  - `_handle_module_edit(self, interaction: discord.Interaction) -> Any`: 處理模組化編輯
  - `_handle_direct_set_callback(self, interaction: discord.Interaction, content: str) -> Any`: 處理直接設定回調

### `EditModeButton`
編輯模式按鈕

- **Attributes**:
  - `edit_mode` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, edit_mode: str, **kwargs: Any) -> Any`: Method __init__.
  - `callback(self, interaction: discord.Interaction) -> Any`: Method callback.

### `SystemPromptScopeButton`
範圍選擇按鈕

- **Attributes**:
  - `scope` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, scope: str, **kwargs: Any) -> Any`: Method __init__.
  - `callback(self, interaction: discord.Interaction) -> Any`: Method callback.

### `SystemPromptViewOptionsView`
查看配置選項選單

- **Attributes**:
  - `permission_validator` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, manager: SystemPromptManager, permission_validator: PermissionValidator, guild_id: str, timeout: float) -> Any`: Method __init__.
  - `view_callback(self, interaction: discord.Interaction, view_type: str) -> Any`: 處理查看回調

### `SystemPromptViewButton`
查看選項按鈕

- **Attributes**:
  - `view_type` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, view_type: str, **kwargs: Any) -> Any`: Method __init__.
  - `callback(self, interaction: discord.Interaction) -> Any`: Method callback.

### `ModuleEditView`
Class representing ModuleEditView.

- **Attributes**:
  - `permission_validator` (`Any`): Instance attribute.
  - `modules` (`Any`): Instance attribute.
  - `guild` (`Any`): Instance attribute.
  - `scope` (`Any`): Instance attribute.
  - `target_channel` (`Any`): Instance attribute.
  - `scope_text` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.
  - `selected_scope` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, manager: SystemPromptManager, permission_validator: PermissionValidator, modules: List[str], guild: discord.Guild, scope: Optional[str], target_channel: Optional[discord.TextChannel], scope_text: Optional[str], guild_id: str, timeout: float) -> Any`: Method __init__.
  - `_setup_scope_selector(self) -> Any`: Method _setup_scope_selector.
  - `_setup_module_selector(self) -> Any`: Method _setup_module_selector.
  - `scope_callback(self, interaction: discord.Interaction, scope: str) -> Any`: Method scope_callback.

### `ModuleScopeButton`
模組範圍選擇按鈕

- **Attributes**:
  - `scope` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, scope: str, **kwargs: Any) -> Any`: Method __init__.
  - `callback(self, interaction: discord.Interaction) -> Any`: Method callback.

### `ModuleSelect`
模組選擇器

- **Attributes**:
  - `manager` (`Any`): Instance attribute.
  - `scope` (`Any`): Instance attribute.
  - `channel` (`Any`): Instance attribute.
  - `guild` (`Any`): Instance attribute.
  - `scope_text` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, manager: SystemPromptManager, scope: str, channel: Optional[discord.TextChannel], guild: discord.Guild, scope_text: Optional[str], **kwargs: Any) -> Any`: Method __init__.
  - `_update_option_descriptions(self) -> Any`: 更新選項的說明文字 (基於語言管理器)
  - `callback(self, interaction: discord.Interaction) -> Any`: 選擇器回調
  - `_handle_module_callback(self, interaction: discord.Interaction, module_name: str, content: str) -> Any`: 處理模組編輯回調

### `SystemPromptCopyView`
複製系統提示選單

- **Attributes**:
  - `permission_validator` (`Any`): Instance attribute.
  - `guild` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, manager: SystemPromptManager, permission_validator: PermissionValidator, guild: discord.Guild, guild_id: str, timeout: float) -> Any`: Method __init__.

### `SystemPromptRemoveView`
移除系統提示的子選單

- **Attributes**:
  - `permission_validator` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, manager: SystemPromptManager, permission_validator: PermissionValidator, guild_id: str, timeout: float) -> Any`: Method __init__.

### `SystemPromptResetView`
重置系統提示的子選單

- **Attributes**:
  - `permission_validator` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, manager: SystemPromptManager, permission_validator: PermissionValidator, guild_id: str, timeout: float) -> Any`: Method __init__.

### `BackButton`
返回主選單按鈕

- **Attributes**:
  - `guild_id` (`str`): Instance attribute.
  - `_bot` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, row: int, guild_id: str, bot: Any) -> Any`: Method __init__.
  - `callback(self, interaction: discord.Interaction) -> Any`: 返回主選單

### `ChannelSelect`
頻道選擇器（用於複製功能）

- **Attributes**:
  - `selected_channel_id` (`Optional[str]`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, **kwargs: Any) -> Any`: Method __init__.
  - `callback(self, interaction: discord.Interaction) -> Any`: Method callback.

### `CopyExecuteButton`
執行複製按鈕

- **Attributes**:
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, label: str, **kwargs: Any) -> Any`: Method __init__.
  - `callback(self, interaction: discord.Interaction) -> Any`: Method callback.

### `RemoveButton`
移除按鈕

- **Attributes**:
  - `remove_type` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, label: str, remove_type: str, **kwargs: Any) -> Any`: Method __init__.
  - `callback(self, interaction: discord.Interaction) -> Any`: Method callback.

### `ResetButton`
重置按鈕

- **Attributes**:
  - `reset_type` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, label: str, reset_type: str, **kwargs: Any) -> Any`: Method __init__.
  - `callback(self, interaction: discord.Interaction) -> Any`: Method callback.

## Functions

### `_ti(interaction: discord.Interaction, *keys: str, fallback: str) -> str`
Translate a key using the guild language from an interaction context.

Falls back to ``fallback`` (or the last key segment) when LanguageManager
is unavailable or the key is missing.
