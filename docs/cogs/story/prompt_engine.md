# File: `cogs/story/prompt_engine.py`

## Overview
Core module for prompt_engine.py.

## Classes

### `StoryPromptEngine`
Builds high-quality prompts for the layered AI agents in the story.

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.
  - `system_prompt_manager` (`Any`): Instance attribute.
  - `language_manager` (`Optional[LanguageManager]`): Instance attribute.
  - `language_map` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: commands.Bot, system_prompt_manager: 'SystemPromptManager') -> Any`: Method __init__.
  - `build_gm_prompt(self, instance: StoryInstance, world: StoryWorld, characters: List[StoryCharacter], user_input: str, story_outlines: List[str], language: str, intervention_text: Optional[str]) -> str`: Constructs the prompt for the Game Master (GM) Agent.
  - `build_story_start_prompt(self, instance: StoryInstance, world: StoryWorld, characters: List[StoryCharacter]) -> str`: Constructs the prompt for the GM to generate the very first scene.
  - `_get_fallback_gm_prompt(self) -> str`: 提供回退的 GM 系統提示詞，當沒有頻道特定的系統提示詞時使用。
  - `build_character_prompt(self, character: StoryCharacter, gm_context: 'DialogueContext', guild_id: int, location: str, date: str, time: str) -> Tuple[str, str]`: Constructs the prompts for the Character Agent.
