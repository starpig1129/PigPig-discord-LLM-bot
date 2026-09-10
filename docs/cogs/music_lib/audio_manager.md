# File: `cogs/music_lib/audio_manager.py`

## Overview
Core module for audio_manager.py.

## Classes

### `AudioManager`
Class representing AudioManager.

- **Attributes**:
  - `_current_audio` (`Dict[int, Optional[FFmpegPCMAudio]]`): Instance attribute.

- **Methods**:
  - `__init__(self) -> Any`: Method __init__.
  - `create_audio_source(self, song: Dict[str, Any]) -> FFmpegPCMAudio`: Create an FFmpeg audio source based on song information.
  - `delete_file(self, guild_id: int, file_path: str) -> Any`: Non-blocking file deletion using asyncio.to_thread.
  - `cleanup_guild_files(self, guild_id: int, folder: str) -> Any`: Clean up all audio files for a guild.
