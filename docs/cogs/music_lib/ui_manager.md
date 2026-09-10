# File: `cogs/music_lib/ui_manager.py`

## Overview
Core module for ui_manager.py.

## Classes

### `UIManager`
Class representing UIManager.

- **Attributes**:
  - `views` (`Dict[int, MusicControlView]`): Instance attribute.
  - `bot` (`Any`): Instance attribute.
  - `lang_manager` (`Optional[LanguageManager]`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: Any) -> Any`: Method __init__.
  - `_get_lang_manager(self) -> Any`: Get language manager instance
  - `_translate_music(self, guild_id: str, *path: Any, **kwargs: Any) -> str`: Music module specific translation method.
  - `_get_fallback_text(self, key: str, **kwargs: Any) -> str`: Fallback text for when translation fails.
  - `update_player_ui(self, interaction: discord.Interaction, item: Dict[str, Any], current_message: Optional[discord.Message], youtube_manager: Any, music_cog: Any) -> Optional[discord.Message]`: Update or create the music player UI.
  - `_create_player_embed(self, item: Dict[str, Any], youtube_manager: Any, guild_id: str) -> discord.Embed`: Create the player embed with song information
  - `cleanup_view(self, guild_id: int) -> Any`: Clean up the view for a specific guild.
