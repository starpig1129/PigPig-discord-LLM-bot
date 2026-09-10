# File: `cogs/music_lib/youtube.py`

## Overview
Core module for youtube.py.

## Classes

### `YouTubeManager`
Class representing YouTubeManager.

- **Attributes**:
  - `time_limit` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, time_limit: Any) -> Any`: Method __init__.
  - `_get_default_ffmpeg_config(self) -> dict`: Method _get_default_ffmpeg_config.
  - `_build_postprocessor_args(self) -> list`: Method _build_postprocessor_args.
  - `create(cls, time_limit: Any) -> Any`: Method create.
  - `search_videos(self, query: Any, max_results: Any) -> Any`: Method search_videos.
  - `download_playlist(self, url: str, folder: str, interaction: discord.Interaction) -> tuple[Optional[List[Dict[str, Any]]], Optional[str]]`: Download a YouTube playlist.
  - `download_audio(self, url: str, folder: str, interaction: discord.Interaction) -> tuple[Optional[Dict[str, Any]], Optional[str]]`: Download audio from YouTube.
  - `get_related_videos(self, video_id: str, title: str, author: str, interaction: discord.Interaction, limit: int, exclude_ids: Optional[Set[str]]) -> tuple[List[Dict[str, Any]], Optional[str]]`: Get related videos for a YouTube video.

## Functions

### `check_ffmpeg(ffmpeg_path: Any) -> Any`
Function check_ffmpeg.
