# File: `cogs/music.py`

## Overview
Core module for music.py.

## Classes

### `YTMusic`
Class representing YTMusic.

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `youtube` (`Any`): Instance attribute.
  - `_executor` (`Any`): Instance attribute.
  - `settings` (`Any`): Instance attribute.
  - `audio_manager` (`Any`): Instance attribute.
  - `state_manager` (`Any`): Instance attribute.
  - `queue_manager` (`Any`): Instance attribute.
  - `ui_manager` (`Any`): Instance attribute.
  - `lang_manager` (`Optional[LanguageManager]`): Instance attribute.
  - `disconnect_timers` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: Any) -> Any`: Method __init__.
  - `setup_hook(self) -> Any`: Initialize async components and LanguageManager.
  - `mode(self, interaction: discord.Interaction, mode: app_commands.Choice[str]) -> Any`: 播放模式命令
  - `shuffle(self, interaction: discord.Interaction) -> Any`: 隨機播放命令
  - `play(self, interaction: discord.Interaction, query: Optional[str]) -> Any`: 播放音樂或刷新UI命令
  - `_handle_playlist(self, interaction: discord.Interaction, url: str) -> Any`: Handle playlist URL
  - `_handle_single_video(self, interaction: discord.Interaction, url: str) -> bool`: Handle single video URL
  - `_handle_search(self, interaction: discord.Interaction, query: str) -> Any`: Handle search query
  - `play_next(self, interaction: discord.Interaction, force_new: bool) -> None`: Play the next song in the queue.
  - `_handle_single_loop(self, interaction: discord.Interaction, state: Any, voice_client: Any) -> Any`: Handle single song loop playback
  - `_get_next_song(self, interaction: discord.Interaction, guild_id: int, force_new: bool) -> Any`: Get the next song to play, handling autoplay and ensuring download.
  - `_refill_queue(self, guild_id: int) -> Any`: Refill the queue with songs
  - `_play_song(self, interaction: discord.Interaction, song: dict, voice_client: Any) -> None`: Play a song and update UI
  - `_handle_after_play(self, interaction: discord.Interaction, song: dict) -> None`: Handle cleanup and queue transitions after a song finishes playing.
  - `_trigger_autoplay(self, interaction: discord.Interaction, guild_id: int) -> Any`: 根據最後播放的歌曲觸發自動播放，精確填充推薦歌曲至5首，並排除重複。
  - `_get_guild_folder(self, guild_id: int) -> tuple`: Get guild queue and folder
  - `handle_previous(self, interaction: discord.Interaction) -> Any`: Method handle_previous.
  - `handle_toggle_playback(self, interaction: discord.Interaction) -> Any`: Method handle_toggle_playback.
  - `handle_skip(self, interaction: discord.Interaction) -> Any`: Method handle_skip.
  - `handle_stop(self, interaction: discord.Interaction) -> Any`: Method handle_stop.
  - `handle_toggle_mode(self, interaction: discord.Interaction) -> Any`: Method handle_toggle_mode.
  - `handle_toggle_shuffle(self, interaction: discord.Interaction) -> Any`: Method handle_toggle_shuffle.
  - `handle_show_queue(self, interaction: discord.Interaction) -> Any`: Method handle_show_queue.
  - `handle_toggle_autoplay(self, interaction: discord.Interaction) -> Any`: 切換自動播放模式
  - `get_queue_text(self, guild_id: int) -> str`: Generates the text for the queue display.
  - `_fill_autoplay_queue(self, interaction: discord.Interaction) -> None`: Fills the queue with recommended songs when autoplay is on.
  - `_cleanup_voice_session(self, guild_id: int) -> Any`: Cleans up the voice session for a guild.
  - `_cancel_disconnect_timer(self, guild_id: int) -> Any`: Cancels the disconnect timer for a guild.
  - `_start_disconnect_timer(self, guild_id: int) -> Any`: Starts the disconnect timer for a guild.
  - `_disconnect_after_delay(self, guild_id: int) -> Any`: Disconnects the bot after a 5-minute delay if it's still paused.
  - `on_voice_state_update(self, member: Any, before: Any, after: Any) -> Any`: Handle voice state changes, including auto-pause and auto-disconnect.
  - `_create_dummy_interaction(self, channel: Any, guild: Any, original_interaction: Any) -> Any`: Creates a dummy interaction object for internal use.
  - `_player_loop(self, interaction: discord.Interaction, song: dict) -> Any`: Monitors the player and handles song completion.

## Functions

### `setup(bot: Any) -> Any`
Initialize the music cog
