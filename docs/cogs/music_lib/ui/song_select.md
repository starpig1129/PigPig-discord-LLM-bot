# File: `cogs/music_lib/ui/song_select.py`

## Overview
Core module for song_select.py.

## Classes

### `SongSelectView`
Class representing SongSelectView.

- **Attributes**:
  - `player` (`Any`): Instance attribute.
  - `results` (`Any`): Instance attribute.
  - `original_interaction` (`Any`): Instance attribute.
  - `lang_manager` (`Optional[LanguageManager]`): Instance attribute.

- **Methods**:
  - `__init__(self, player: Any, results: Any, interaction: Any) -> Any`: Method __init__.
  - `_get_lang_manager(self) -> Any`: Get language manager instance
  - `_translate_music(self, *path: Any, **kwargs: Any) -> str`: 音樂模組專用翻譯方法
  - `_get_fallback_text(self, key: str, **kwargs: Any) -> str`: 備用文字機制
  - `on_timeout(self) -> Any`: Handle view timeout

### `SongSelectMenu`
Class representing SongSelectMenu.

- **Attributes**:
  - `view_parent` (`Any`): Instance attribute.
  - `results` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, results: Any, view: Any) -> Any`: Method __init__.
  - `callback(self, interaction: discord.Interaction) -> Any`: Handle song selection
