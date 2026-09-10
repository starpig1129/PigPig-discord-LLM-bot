# File: `cogs/episodic_memory.py`

## Overview
Core module for episodic_memory.py.

## Classes

### `EpisodicMemoryService`
A background service responsible for the first stage of the ETL process
for episodic memory. It fetches full message objects from Discord's API
based on pending messages tracked by the MessageTracker.

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `storage` (`StorageInterface`): Instance attribute.
  - `settings` (`MemoryConfig`): Instance attribute.
  - `message_tracker` (`MessageTracker`): Instance attribute.
  - `is_processing` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: 'PigPig | commands.Bot', storage: 'StorageInterface') -> Any`: Args:
  - `cog_load(self) -> None`: Load the episodic memory service.
  - `cog_unload(self) -> None`: Unload the episodic memory service.
  - `_translate_text(self, lang_manager: Any, guild_id: str, *args: str, **kwargs: Any) -> str`: Helper method to safely translate text with fallback.
  - `force_update_memory(self, interaction: discord.Interaction) -> Any`: Force update the memory for the current channel. Owner only.
  - `search_episodic_memory(self, interaction: discord.Interaction, vector_query: Optional[str], keyword_query: Optional[str], user_id: Optional[str], channel_id: Optional[str]) -> Any`: Search episodic memory with multiple query parameters. Owner only.

## Functions

### `setup(bot: commands.Bot) -> Any`
The setup function for the cog.
