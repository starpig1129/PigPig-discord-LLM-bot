# File: `cogs/story/database.py`

## Overview
Core module for database.py.

## Classes

### `CharacterDB`
Handles all database operations for characters, independent of story worlds.

- **Attributes**:
  - `db_path` (`Any`): Instance attribute.
  - `_initialized` (`Any`): Instance attribute.
  - `_lock` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self) -> Any`: Method __init__.
  - `_get_connection(self) -> sqlite3.Connection`: Establishes and returns a database connection.
  - `initialize(self) -> Any`: Initializes the character database, creates the table, and handles migrations.
  - `save_character(self, character: StoryCharacter) -> Any`: Saves or updates a character.
  - `_row_to_character(self, row: sqlite3.Row) -> StoryCharacter`: Converts a database row to a StoryCharacter object.
  - `get_characters_by_ids(self, character_ids: List[str]) -> List[StoryCharacter]`: Retrieves multiple characters by their IDs.
  - `delete_character(self, character_id: str) -> Any`: Deletes a character by ID.

### `StoryDB`
Handles all database operations for the story module (worlds and instances).

- **Attributes**:
  - `db_path` (`Any`): Instance attribute.
  - `guild_id` (`Any`): Instance attribute.
  - `_initialized` (`Any`): Instance attribute.
  - `_lock` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, guild_id: int) -> Any`: Method __init__.
  - `_get_connection(self) -> sqlite3.Connection`: Establishes and returns a database connection.
  - `initialize(self) -> Any`: Initializes the database and creates tables if they don't exist.
  - `save_world(self, world: StoryWorld) -> Any`: Saves or updates a story world using a SELECT then INSERT/UPDATE strategy.
  - `get_world(self, world_name: str) -> Optional[StoryWorld]`: Retrieves a story world by name.
  - `get_all_worlds(self) -> List[StoryWorld]`: Retrieves all story worlds for this guild.
  - `save_story_instance(self, instance: StoryInstance) -> Any`: Saves or updates a story instance.
  - `save_player_relationship(self, relationship: PlayerRelationship) -> Any`: Saves or updates a player-NPC relationship.
