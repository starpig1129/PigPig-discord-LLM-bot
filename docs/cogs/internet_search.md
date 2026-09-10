# File: `cogs/internet_search.py`

## Overview
Core module for internet_search.py.

## Classes

### `InternetSearchCog`
Cog for internet search functionality including general web search, YouTube, and food recommendations.

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `db` (`Any`): Instance attribute.
  - `recommender` (`Any`): Instance attribute.
  - `provider` (`Any`): Instance attribute.
  - `lang_manager` (`Optional[LanguageManager]`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: Any) -> Any`: Method __init__.
  - `cog_load(self) -> Any`: Initialize LanguageManager when the cog is loaded.
  - `cog_unload(self) -> Any`: Close the restaurant provider's HTTP session when the cog is unloaded.
  - `search_command(self, interaction: discord.Interaction, type: Optional[app_commands.Choice[str]], query: str) -> None`: Slash command wrapper for internet_search.
  - `internet_search(self, ctx: Any, query: str, search_type: str, message_to_edit: Optional[discord.Message], guild_id: str) -> Any`: High-level search entry point that delegates to specific search functions.
  - `google_search(self, ctx: Any, query: Any, message_to_edit: Any) -> Any`: Perform a web search using Gemini grounding, with fallback to legacy scraping.
  - `_extract_sources_from_grounding(self, response: Any) -> Any`: Extract source URLs and titles from Gemini grounding metadata.
  - `_legacy_google_search(self, ctx: Any, query: Any, message_to_edit: Any) -> Any`: Original Selenium-based Google scraping preserved as a fallback.
  - `get_chrome_options() -> Any`: Configure Chrome options for headless scraping.
  - `youtube_search(self, ctx: Any, query: Any, message_to_edit: Any) -> Any`: Search for YouTube videos and return a random result from the top hits.
  - `eat_search(self, ctx: Any, keyword: str, message_to_edit: discord.Message) -> Any`: Food recommendation search using WeightedRecommender and restaurant providers.

## Functions

### `install_driver() -> Any`
Install Chrome driver using ChromeDriverManager.

### `setup(bot: Any) -> Any`
Set up the InternetSearchCog.
