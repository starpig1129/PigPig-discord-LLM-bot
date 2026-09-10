# File: `cogs/summarizer.py`

## Overview
Core module for summarizer.py.

## Classes

### `SummarizerCog`
Cog for conversation summarization using AI with source mapping and character limits.

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `MAX_CHAR_COUNT` (`Any`): Instance attribute.
  - `EMBED_DESC_LIMIT` (`Any`): Instance attribute.
  - `lang_manager` (`Optional[LanguageManager]`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: commands.Bot) -> Any`: Method __init__.
  - `cog_load(self) -> Any`: Initialize LanguageManager when the cog is loaded.
  - `_split_text_robustly(self, text: str) -> Any`: Split long text into multiple chunks safely, handling exceptionally long single lines.
  - `summarize(self, interaction: discord.Interaction, limit: int, persona: Optional[str], only_me: bool) -> None`: Analyze and summarize recent channel conversation history using an AI agent.

## Functions

### `setup(bot: commands.Bot) -> Any`
Set up the SummarizerCog.
