# File: `cogs/story/ui/ui_manager.py`

## Overview
Core module for ui_manager.py.

## Classes

### `UIManager`
故事模組的 UI 管理器

負責協調和管理所有 UI 介面的顯示、更新與生命週期。
採用臨時性 (ephemeral) 介面設計，降低狀態管理複雜度。

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `story_manager` (`Any`): Instance attribute.
  - `character_db` (`Any`): Instance attribute.
  - `system_prompt_manager` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: commands.Bot, story_manager: 'StoryManager', system_prompt_manager: SystemPromptManager) -> Any`: Method __init__.
  - `show_main_menu(self, interaction: discord.Interaction) -> Any`: 顯示主要的故事管理選單
  - `_create_initial_story_embed(self, guild_id: int, channel_id: int) -> discord.Embed`: 創建初始故事選單的 Embed
  - `_create_active_story_embed(self, story_instance: Any) -> discord.Embed`: 創建進行中故事的 Embed
  - `_update_world_select_options(self, view: Any, guild_id: int) -> Any`: 更新視圖中的世界選擇選單選項
  - `handle_load_default_character(self, interaction: discord.Interaction) -> Any`: 處理從頻道預設設定載入角色的請求
  - `show_character_create_modal(self, interaction: discord.Interaction, name: str, description: str) -> Any`: 顯示角色創建 Modal，可選填預設值
