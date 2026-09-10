# File: `cogs/memory/db/version_storage.py`

## Overview
Per-guild version tracking storage.

Stores which bot version each guild has already seen, so the
version-announcement feature fires exactly once per version per guild.

## Classes

### `GuildVersionStorage`
SQLite-backed store for per-guild seen-version tracking.

Uses an isolated SQLite connection so it works regardless of whether
the memory sub-system is enabled.

- **Attributes**:
  - `db_path` (`Any`): Instance attribute.
  - `_conn` (`Optional[sqlite3.Connection]`): Instance attribute.

- **Methods**:
  - `__init__(self, db_path: Union[str, Path]) -> None`: Initialize and ensure the required table exists.
  - `_open_connection(self) -> sqlite3.Connection`: Open (or reuse) the SQLite connection.
  - `_ensure_table(self) -> None`: Create the guild_version_seen table if it does not exist.
  - `set_seen_version(self, guild_id: str, version: str) -> None`: Record that guild_id has seen the given bot version.
