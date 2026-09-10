# File: `cogs/story/ui/modals.py`

## Overview
Core module for modals.py.

## Classes

### `WorldCreateModal`
世界創建 Modal

提供表單介面讓使用者輸入新世界的名稱、背景和第一個地點的資訊

- **Attributes**:
  - `story_manager` (`Any`): Instance attribute.
  - `story_db` (`Any`): Instance attribute.
  - `guild_id` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, manager: 'StoryManager', guild_id: int) -> Any`: Method __init__.
  - `on_submit(self, interaction: discord.Interaction) -> Any`: 處理世界創建表單提交
  - `on_error(self, interaction: discord.Interaction, error: Exception) -> Any`: 處理 Modal 錯誤

### `CharacterCreateModal`
角色創建 Modal

提供表單介面讓使用者創建新角色

- **Attributes**:
  - `story_manager` (`Any`): Instance attribute.
  - `character_db` (`Any`): Instance attribute.
  - `guild_id` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.
  - `character_name` (`Any`): Instance attribute.
  - `description` (`Any`): Instance attribute.
  - `webhook_url` (`Any`): Instance attribute.
  - `privacy_input` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, manager: 'StoryManager', guild_id: int, name: str, description: str) -> Any`: Method __init__.
  - `on_submit(self, interaction: discord.Interaction) -> Any`: 處理角色創建表單提交
  - `on_error(self, interaction: discord.Interaction, error: Exception) -> Any`: 處理 Modal 錯誤

### `StoryStartModal`
故事開始 Modal

收集故事開始時的初始世界狀態

- **Attributes**:
  - `story_manager` (`Any`): Instance attribute.
  - `bot` (`Any`): Instance attribute.
  - `guild_id` (`Any`): Instance attribute.
  - `channel_id` (`Any`): Instance attribute.
  - `world_name` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, story_manager: 'StoryManager', bot: commands.Bot, guild_id: int, channel_id: int, world_name: str) -> Any`: Method __init__.
  - `on_submit(self, interaction: discord.Interaction) -> Any`: 立即回應互動以防止超時，並在背景準備 NPC 選擇介面。
  - `_prepare_and_send_npc_select(self, interaction: discord.Interaction) -> Any`: 在背景中執行耗時操作，然後發送帶有 NPC 選擇視圖的 followup 訊息。
  - `on_error(self, interaction: discord.Interaction, error: Exception) -> Any`: 處理 Modal 錯誤

### `InterventionModal`
A modal for users to submit an OOC intervention to the story director.

- **Attributes**:
  - `manager` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, manager: 'StoryManager') -> Any`: Method __init__.
  - `on_submit(self, interaction: discord.Interaction) -> Any`: Handles the submission of the intervention.
  - `on_error(self, interaction: discord.Interaction, error: Exception) -> Any`: Handles errors in the modal.
