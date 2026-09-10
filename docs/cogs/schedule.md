# File: `cogs/schedule.py`

## Overview
Core module for schedule.py.

## Classes

### `ScheduleManager`
Class representing ScheduleManager.

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `schedule_dir` (`Any`): Instance attribute.
  - `lang_manager` (`Optional[LanguageManager]`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: Any) -> Any`: Method __init__.
  - `cog_load(self) -> Any`: 當 Cog 載入時初始化語言管理器
  - `_sanitize_schedule_data(self, data: Any, fallback_channel_id: int) -> Any`: Ensure schedule_data has required keys and types. Returns (data, repaired).
  - `upload_schedule_command(self, interaction: discord.Interaction, file: discord.Attachment) -> Any`: Method upload_schedule_command.
  - `_core_upload_schedule(self, user_id: int, channel_id: int, yaml_data: bytes) -> Any`: Method _core_upload_schedule.
  - `query_schedule_command(self, interaction: discord.Interaction, query_type: app_commands.Choice[str], time: str, day: app_commands.Choice[str], target_user: discord.Member) -> Any`: Method query_schedule_command.
  - `_core_query_schedule(self, interaction_or_ctx: Any, query_type: str, target_user_id: int, time: str, day: str) -> Any`: Method _core_query_schedule.
  - `format_full_schedule(self, schedule: Any, guild_id: Any) -> Any`: Method format_full_schedule.
  - `format_specific_time_schedule(self, schedule: Any, specific_time: Any, day: Any, guild_id: Any) -> Any`: Method format_specific_time_schedule.
  - `format_next_schedule(self, schedule: Any, now: Any, guild_id: Any) -> Any`: Method format_next_schedule.
  - `update_schedule_command(self, interaction: discord.Interaction, day: str, time: str, description: str) -> Any`: Method update_schedule_command.
  - `_core_update_schedule(self, user_id: int, day: str, time: str, description: str) -> Any`: Method _core_update_schedule.
  - `show_template_command(self, interaction: discord.Interaction) -> None`: Method show_template_command.

## Functions

### `setup(bot: Any) -> Any`
Function setup.
