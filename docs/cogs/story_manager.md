# File: `cogs/story_manager.py`

## Overview
Core module for story_manager.py.

## Classes

### `StoryManagerCog`
故事模組主要 Cog

重構後的故事模組採用 UI 驅動設計：
- 單一 /story 命令作為入口點
- 所有功能透過 Discord UI 元件操作
- 臨時性介面降低狀態管理複雜度

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.
  - `system_prompt_manager` (`Optional[SystemPromptManager]`): Instance attribute.
  - `story_manager` (`Optional[StoryManager]`): Instance attribute.
  - `ui_manager` (`Optional[UIManager]`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: commands.Bot) -> Any`: Method __init__.
  - `story_menu(self, interaction: discord.Interaction) -> Any`: 故事管理主命令
  - `intervene(self, interaction: discord.Interaction) -> Any`: Allows a user to intervene in the story with OOC instructions for the director.
  - `on_ready(self) -> Any`: Cog 準備就緒事件。
  - `handle_story_message(self, message: discord.Message) -> Any`: 處理故事頻道中的訊息

## Functions

### `setup(bot: commands.Bot) -> Any`
設定函式，將 Cog 加入到 bot 中

Args:
    bot: Discord Bot 實例
