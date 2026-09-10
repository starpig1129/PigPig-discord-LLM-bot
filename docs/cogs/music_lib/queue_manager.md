# File: `cogs/music_lib/queue_manager.py`

## Overview
Core module for queue_manager.py.

## Classes

### `PlayMode`
Class representing PlayMode.

### `QueueManager`
Class representing QueueManager.

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `guild_queues` (`Dict[int, asyncio.Queue]`): Instance attribute.
  - `guild_settings` (`Dict[int, Dict[str, Any]]`): Instance attribute.
  - `guild_playlists` (`Dict[int, List[Dict[str, Any]]]`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: Any) -> Any`: Method __init__.
  - `get_guild_settings(self, guild_id: int) -> Dict[str, Any]`: Get server playback settings.
  - `get_guild_queue_and_folder(self, guild_id: int) -> Tuple[asyncio.Queue, str]`: Ensure the server has a unique folder and playlist.
  - `get_queue(self, guild_id: int) -> asyncio.Queue`: Get the queue for the guild.
  - `clear_guild_data(self, guild_id: int) -> Any`: Clear the playlist for the specified server.
  - `get_next_playlist_songs(self, guild_id: int, count: int, youtube_manager: Any, folder: Optional[str], interaction: Any) -> List[Dict[str, Any]]`: Get the next song from the playlist.
  - `has_playlist_songs(self, guild_id: int) -> bool`: Check if there are more songs in the playlist.
  - `toggle_shuffle(self, guild_id: int) -> bool`: Toggle shuffle playback state.
  - `set_play_mode(self, guild_id: int, mode: PlayMode) -> Any`: Set the playback mode.
  - `get_play_mode(self, guild_id: int) -> PlayMode`: Get the playback mode.
  - `is_shuffle_enabled(self, guild_id: int) -> bool`: Check if shuffle playback is enabled.
  - `copy_queue(self, guild_id: int, shuffle: bool) -> Tuple[List[Dict[str, Any]], asyncio.Queue]`: Copy queue contents without consuming the original queue.
  - `get_queue_snapshot(self, guild_id: int) -> List[Dict[str, Any]]`: Get a snapshot of the current playback queue.
  - `is_queue_empty(self, guild_id: int) -> bool`: Check if the queue is empty.
  - `clear_queue(self, guild_id: int) -> Any`: Clear the playback queue for the specified server.
  - `add_to_queue(self, guild_id: int, item: Dict[str, Any], force: bool) -> bool`: Add an item to the queue and apply different priority logic based on the adder (user or bot).
  - `add_to_front_of_queue(self, guild_id: int, item: Dict[str, Any]) -> bool`: Add item to the front of the queue and handle overflow. Returns True on success, False on failure.
  - `get_next_item(self, guild_id: int) -> Optional[Dict[str, Any]]`: Get the next item from the queue.
  - `enforce_autoplay_limit(self, guild_id: int, limit: int) -> Any`: Ensure the number of autoplayed songs in the queue does not exceed the specified limit.
