# File: `cogs/userdata.py`

## Overview
User data management cog for Discord bot.

This module provides commands and utilities for managing personalized user data,
including preferences, display names, and interaction rules stored in a database.

## Classes

### `UserDataResponse`
Structured response schema for user data agent.

Attributes:
    procedural_memory: Free-form memory about user preferences and interactions.
    user_background: List of background information about the user.
    display_names: List of display names the user has used.

- **Attributes**:
  - `procedural_memory` (`Optional[str]`): Class attribute.
  - `user_background` (`Optional[str]`): Class attribute.
  - `display_names` (`List[str]`): Class attribute.

### `UserDataCog`
Manages personalized user data for Discord bot interactions.

Provides /memory command group allowing users to save or view bot's
memory about them, such as preferences, nicknames, or interaction rules.

Attributes:
    bot: The Discord bot instance.
    user_manager: Manager for user data persistence.
    lang_manager: Manager for multi-language support.
    logger: Logger instance for this cog.

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `user_manager` (`Any`): Instance attribute.
  - `_knowledge_lock` (`Any`): Instance attribute.
  - `lang_manager` (`Optional[LanguageManager]`): Instance attribute.
  - `logger` (`Any`): Instance attribute.
  - `knowledge_storage` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: commands.Bot, user_manager: Optional[SQLiteUserManager]) -> None`: Initializes the UserDataCog.
  - `cog_load(self) -> None`: Initializes language manager and user manager when cog loads.
  - `_translate(self, guild_id: str, *path: str, fallback_key: str, **kwargs: Any) -> str`: Unified translation method with fallback mechanism.
  - `_get_guild_id_from_context(self, context: Union[discord.Interaction, discord.Message]) -> str`: Extracts guild_id from various context types.
  - `_extract_json_from_response(self, response_text: str) -> Optional[Dict[str, Any]]`: Extracts and validates JSON from AI response text.
  - `_validate_user_data_response(self, data: Dict[str, Any]) -> bool`: Validates that response contains expected user data fields.
  - `_extract_user_id_from_context(self, context: Union[discord.Interaction, discord.Message]) -> Optional[str]`: Extracts user ID from context (interaction or message).
  - `_read_user_data(self, user_id: str, context: Union[discord.Interaction, discord.Message]) -> str`: Core logic for reading and formatting user's stored data.
  - `_invoke_ai_merge_agent(self, existing_data: Optional[UserInfo], new_data: str, user_id: str) -> UserDataResponse`: Invokes AI agent to merge existing and new user data.
  - `_invoke_knowledge_merge_agent(self, existing_knowledge: Optional[str], new_knowledge: str, target_type: str, category: str) -> str`: Invokes AI agent to merge existing and new guild/channel knowledge.
  - `_save_knowledge_data(self, target_type: str, target_id: str, content: str, category: str, context: Union[discord.Interaction, discord.Message]) -> str`: Core logic for saving guild/channel knowledge with AI merge.
  - `_clear_knowledge_data(self, target_type: str, target_id: str) -> str`: Core logic for clearing guild/channel knowledge.
  - `_save_user_data(self, user_id: str, discord_name: str, user_data: str, context: Union[discord.Interaction, discord.Message], nickname: Optional[str]) -> str`: Core logic for saving user data with AI-assisted merge.
  - `memory_save(self, interaction: discord.Interaction, preference: str) -> None`: Handles /memory save command to store user preferences.
  - `memory_clear(self, interaction: discord.Interaction) -> None`: Handles /memory clear command to clear user preferences.
  - `memory_show(self, interaction: discord.Interaction) -> None`: Handles /memory show command to display stored user preferences.
  - `knowledge_show(self, interaction: discord.Interaction, scope: app_commands.Choice[str]) -> None`: Handles /knowledge show command to display stored knowledge.
  - `knowledge_save(self, interaction: discord.Interaction, scope: app_commands.Choice[str], content: str, category: str) -> None`: Handles /knowledge save command to save or update stored knowledge.
  - `knowledge_clear(self, interaction: discord.Interaction, scope: app_commands.Choice[str]) -> None`: Handles /knowledge clear command to clear stored knowledge.
  - `manage_user_data(self, context: Union[discord.Interaction, discord.Message], user: Union[discord.User, discord.Member], user_data: str, action: str, message_to_edit: Optional[discord.Message]) -> str`: Dispatcher for managing user data operations.
  - `_clear_user_data(self, user_id: str, context: Union[discord.Interaction, discord.Message]) -> str`: Core logic for clearing user data.
  - `manage_user_data_message(self, message: Union[discord.Interaction, discord.Message], user_id: Optional[str], user_data: str, action: str, message_to_edit: Optional[discord.Message]) -> str`: Manages user data triggered from message (for internal tool use).
  - `get_user_statistics(self) -> Dict[str, Any]`: Retrieves user statistics from user manager.
  - `update_user_activity(self, user_id: str, discord_name: str, nickname: Optional[str]) -> bool`: Updates user activity status.

## Functions

### `setup(bot: commands.Bot) -> None`
Sets up the UserDataCog.

Args:
    bot: The Discord bot instance.
