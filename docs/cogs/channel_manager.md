# File: `cogs/channel_manager.py`

## Overview
Core module for channel_manager.py.

## Classes

### `ChannelManager`
Cog for managing server-wide and channel-specific response modes and permissions.

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `data_dir` (`Any`): Instance attribute.
  - `lang_manager` (`Optional[LanguageManager]`): Instance attribute.
  - `tokens` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: Any) -> Any`: Method __init__.
  - `cog_load(self) -> Any`: Initialize LanguageManager when the cog is loaded.
  - `load_config(self, guild_id: str) -> Dict[str, Any]`: Load configuration for a specific guild.
  - `_get_default_config(self) -> Dict[str, Any]`: Provide a default configuration template.
  - `save_config(self, guild_id: str, config: Dict[str, Any]) -> Any`: Save configuration for a specific guild.
  - `check_admin_permissions(self, interaction: discord.Interaction, defer: bool) -> bool`: Check if the user has administrator permissions or is the bot owner.
  - `set_server_mode(self, interaction: discord.Interaction, mode: app_commands.Choice[str]) -> Any`: Set the global response mode for the entire server.
  - `set_channel_mode(self, interaction: discord.Interaction, channel: Union[discord.TextChannel, discord.VoiceChannel, discord.StageChannel, discord.Thread], mode: app_commands.Choice[str]) -> Any`: Configure a specific mode override for a single channel.
  - `add_channel_command(self, interaction: discord.Interaction, channel: Union[discord.TextChannel, discord.VoiceChannel, discord.StageChannel, discord.Thread], list_type: app_commands.Choice[str]) -> Any`: Add a channel to the server's whitelist or blacklist.
  - `remove_channel_command(self, interaction: discord.Interaction, channel: Union[discord.TextChannel, discord.VoiceChannel, discord.StageChannel, discord.Thread], list_type: app_commands.Choice[str]) -> Any`: Remove a channel from the server's whitelist or blacklist.
  - `auto_response_command(self, interaction: discord.Interaction, channel: Union[discord.TextChannel, discord.VoiceChannel, discord.StageChannel, discord.Thread], enabled: bool) -> Any`: Enable or disable automatic bot responses in a specific channel.
  - `is_allowed_channel(self, channel: Union[discord.TextChannel, discord.VoiceChannel, discord.StageChannel, discord.Thread], guild_id: str) -> Tuple[bool, bool, Optional[str]]`: Determine if the bot is allowed to respond in a channel and get its effective mode.

## Functions

### `setup(bot: Any) -> Any`
Set up the ChannelManager cog.
