# File: `cogs/music_lib/ui/controls.py`

## Overview
Core module for controls.py.

## Classes

### `MusicControlView`
Class representing MusicControlView.

- **Attributes**:
  - `guild` (`Any`): Instance attribute.
  - `message` (`Any`): Instance attribute.
  - `current_embed` (`Any`): Instance attribute.
  - `song_info` (`Any`): Instance attribute.
  - `lang_manager` (`Optional[LanguageManager]`): Instance attribute.
  - `_is_updating` (`Any`): Instance attribute.
  - `update_task` (`Any`): Instance attribute.
  - `current_position` (`Any`): Instance attribute.
  - `previous_callback` (`Any`): Instance attribute.
  - `toggle_playback_callback` (`Any`): Instance attribute.
  - `skip_callback` (`Any`): Instance attribute.
  - `stop_callback` (`Any`): Instance attribute.
  - `toggle_mode_callback` (`Any`): Instance attribute.
  - `toggle_shuffle_callback` (`Any`): Instance attribute.
  - `show_queue_callback` (`Any`): Instance attribute.
  - `toggle_autoplay_callback` (`Any`): Instance attribute.
  - `get_queue_manager` (`Any`): Instance attribute.
  - `get_state_manager` (`Any`): Instance attribute.
  - `get_voice_client` (`Any`): Instance attribute.
  - `get_lang_manager` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, interaction: discord.Interaction, song_info: dict, previous_callback: Any, toggle_playback_callback: Any, skip_callback: Any, stop_callback: Any, toggle_mode_callback: Any, toggle_shuffle_callback: Any, show_queue_callback: Any, toggle_autoplay_callback: Any, get_queue_manager: Any, get_state_manager: Any, get_voice_client: Any, get_lang_manager: Any) -> Any`: Method __init__.
  - `_get_lang_manager(self) -> Any`: Get language manager instance
  - `_translate_music(self, *path: Any, **kwargs: Any) -> str`: 音樂模組專用翻譯方法
  - `_get_fallback_text(self, key: str, **kwargs: Any) -> str`: 備用文字機制
  - `_get_mode_name(self, mode: str) -> str`: 獲取播放模式翻譯名稱
  - `_get_shuffle_status(self, is_enabled: bool) -> str`: 獲取隨機播放狀態文字
  - `update_button_state(self, update_message: bool) -> Any`: Update button states based on current playback and mode status
  - `start_progress_updater(self, duration: int) -> Any`: Method start_progress_updater.
  - `stop_progress_updater(self) -> Any`: Method stop_progress_updater.
  - `update_progress(self, duration: Any) -> Any`: Method update_progress.
  - `update_embed(self, interaction: discord.Interaction, title: str, color: discord.Color) -> Any`: Update the embed with error handling and message recreation
  - `previous(self, interaction: discord.Interaction, button: discord.ui.Button) -> Any`: Method previous.
  - `toggle_playback(self, interaction: discord.Interaction, button: discord.ui.Button) -> Any`: Method toggle_playback.
  - `skip(self, interaction: discord.Interaction, button: discord.ui.Button) -> Any`: Method skip.
  - `stop(self, interaction: discord.Interaction, button: discord.ui.Button) -> Any`: Method stop.
  - `toggle_mode(self, interaction: discord.Interaction, button: discord.ui.Button) -> Any`: 切換播放模式
  - `toggle_shuffle(self, interaction: discord.Interaction, button: discord.ui.Button) -> Any`: 切換隨機播放
  - `show_queue(self, interaction: discord.Interaction, button: discord.ui.Button) -> Any`: Method show_queue.
  - `toggle_autoplay(self, interaction: discord.Interaction, button: discord.ui.Button) -> Any`: 切換自動播放
