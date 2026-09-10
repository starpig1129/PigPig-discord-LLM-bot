# File: `cogs/stats_cog.py`

## Overview
StatsCog: real-time user statistics tracking and historical log migration.

Listens for on_message events to update per-user stats in the user_stats
table, and runs a low-priority background task on cog load to ingest
historical NDJSON log files.

## Classes

### `StatsCog`
Real-time user stats tracking and historical log migration.

Attributes:
    bot: The Discord bot instance.
    stats_storage: StatsStorage instance for DB operations.

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `stats_storage` (`Optional[StatsStorage]`): Instance attribute.
  - `_migration_task` (`Optional[asyncio.Task]`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: commands.Bot) -> None`: Initialize StatsCog.
  - `cog_load(self) -> None`: Start background log migration task when cog loads.
  - `cog_unload(self) -> None`: Cancel background migration task on cog unload.
  - `on_message(self, message: Any) -> None`: Update user stats for every incoming message.
  - `_migrate_logs_background(self) -> None`: Ingest historical NDJSON log files into user_stats and stats.db.
  - `_migrate_guild_logs(self, guild_id: str, guild_dir: Path) -> None`: Migrate log files for a single guild.

## Functions

### `setup(bot: commands.Bot) -> None`
Register StatsCog with the bot.
