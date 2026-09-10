# File: `cogs/story/manager.py`

## Overview
Core module for manager.py.

## Classes

### `StoryManager`
The core manager for story logic. It coordinates the database, state,
and prompt engine to generate story progression based on the v5 layered AI agent architecture.

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `cog` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.
  - `system_prompt_manager` (`Any`): Instance attribute.
  - `_initialized` (`Any`): Instance attribute.
  - `db_instances` (`Dict[int, StoryDB]`): Instance attribute.
  - `character_db` (`Any`): Instance attribute.
  - `prompt_engine` (`Any`): Instance attribute.
  - `state_manager` (`Any`): Instance attribute.
  - `language_manager` (`LanguageManager`): Instance attribute.
  - `interventions` (`Dict[int, str]`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: commands.Bot, cog: commands.Cog, system_prompt_manager: SystemPromptManager) -> Any`: Method __init__.
  - `_get_db(self, guild_id: int) -> StoryDB`: Gets or creates a database connection for a specific guild.
  - `_extract_structured_response(self, response: Any, expected_model: Type[T], context: str) -> Optional[T]`: Unified extractor for structured agent responses.
  - `initialize(self) -> Any`: Initializes the StoryManager and its components.
  - `add_intervention(self, channel_id: int, text: str) -> Any`: Stores an intervention for a specific channel.
  - `intervene(self, interaction: discord.Interaction) -> Any`: Opens a modal for the user to provide an OOC intervention.
  - `_update_relationships(self, db: StoryDB, story_id: int, updates: List[RelationshipUpdate]) -> Any`: Updates player-NPC relationships based on the GM plan.
  - `_record_event(self, db: StoryDB, world: StoryWorld, instance: StoryInstance, gm_plan: GMActionPlan, final_content: str) -> Any`: Creates and records an event in the world state.
  - `_send_story_response(self, channel: discord.TextChannel, character: Optional[StoryCharacter], story_instance: StoryInstance, content: str | CharacterAction) -> Any`: Constructs and sends the story response as an embed, using a webhook if available.
  - `process_story_message(self, message: discord.Message) -> Any`: Processes a message from a story channel using the v5 layered agent architecture.
  - `_find_speaking_character(self, speaker_name: Optional[str], characters: List[StoryCharacter], channel: discord.abc.Messageable) -> Optional[StoryCharacter]`: Unified character lookup logic, supports multiple matching methods.
  - `_generate_and_save_summary(self, story_instance: StoryInstance) -> Any`: Generates a summary of the last 20-40 messages and saves it.
  - `_generate_and_save_outline(self, story_instance: StoryInstance) -> Any`: Generates a high-level outline from the last 10 summaries and saves it.
  - `start_story(self, interaction: discord.Interaction, world_name: str, character_ids: List[str], use_narrator: bool, initial_date: Optional[str], initial_time: Optional[str], initial_location: str) -> Any`: Handles the logic of starting a new story, creating the instance,
  - `generate_first_scene(self, interaction: discord.Interaction, story_instance: StoryInstance) -> Any`: Generates the introductory scene for a new story using the v5 architecture.
