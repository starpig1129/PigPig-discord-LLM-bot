# File: `cogs/language_manager.py`

## Overview
Core module for language_manager.py.

## Classes

### `MissingTranslationError`
Custom exception for missing translation keys

### `TranslationCache`
Multi-layer cache for translations with LRU eviction

- **Attributes**:
  - `_cache` (`Dict[str, str]`): Instance attribute.
  - `_max_size` (`Any`): Instance attribute.
  - `_access_times` (`Dict[str, float]`): Instance attribute.
  - `_access_counts` (`Dict[str, int]`): Instance attribute.

- **Methods**:
  - `__init__(self, max_size: int) -> Any`: Method __init__.
  - `get(self, key: str) -> Optional[str]`: Get cached translation with LRU tracking
  - `put(self, key: str, value: str) -> Any`: Store translation in cache with LRU eviction
  - `_evict_lru(self) -> Any`: Evict least recently used item
  - `clear(self) -> Any`: Clear all cached items
  - `size(self) -> int`: Get current cache size

### `LanguageManager`
Language Management System with modular translation support

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `config_dir` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.
  - `default_lang` (`Any`): Instance attribute.
  - `translations` (`Dict[str, Dict[str, Any]]`): Instance attribute.
  - `_translation_cache` (`Any`): Instance attribute.
  - `supported_languages` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: commands.Bot) -> Any`: Method __init__.
  - `_load_translations(self) -> Any`: Load all language translations, supporting multi-file structure.
  - `_load_directory(self, lang_code: str, directory: str, target_dict: Dict[str, Any]) -> Any`: Recursively load all JSON files in a directory.
  - `_get_supported_languages(self) -> Dict[str, str]`: Get the list of supported languages.
  - `get_server_lang(self, guild_id: str) -> str`: Get the server's language setting.
  - `save_server_lang(self, guild_id: str, lang: str) -> bool`: Save the server's language setting.
  - `_traverse_nested_dict(self, data: Dict[str, Any], keys: List[str]) -> Optional[Any]`: Traverse a nested dictionary.
  - `translate(self, guild_id: str, *keys: str, **kwargs: Any) -> str`: Translate specified text.
  - `_format_result(self, result: str, kwargs: Dict[str, Any]) -> str`: Format translation result.
  - `_log_missing_translation(self, guild_id: str, lang: str, keys: List[str]) -> Any`: Log missing translations.
  - `clear_cache(self) -> Any`: Clear translation cache.
  - `set_language(self, interaction: discord.Interaction, language: str) -> Any`: Set the display language of the server.
  - `current_language(self, interaction: discord.Interaction) -> Any`: Display the current language used by the server.

## Functions

### `setup(bot: commands.Bot) -> Any`
Function setup.
