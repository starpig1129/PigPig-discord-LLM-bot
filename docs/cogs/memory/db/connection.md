# File: `cogs/memory/db/connection.py`

## Overview
Database connection manager for the memory cog.

Handles SQLite connection lifecycle, thread-safe access, and error reporting.

## Classes

### `DatabaseConnection`
Manage SQLite connections per-thread and provide thread-safe access.

- **Attributes**:
  - `db_path` (`Any`): Instance attribute.
  - `bot` (`Any`): Instance attribute.
  - `_loop` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.
  - `_lock` (`Any`): Instance attribute.
  - `_connections` (`Dict[int, sqlite3.Connection]`): Instance attribute.

- **Methods**:
  - `__init__(self, db_path: Union[str, Path], bot: Optional['PigPig']) -> Any`: Initialize connection manager.
  - `_report_error_threadsafe(self, exc: Exception, ctx: str) -> None`: Report errors in a thread-safe manner to the async error reporter.
  - `get_connection(self) -> Any`: Context manager that yields a sqlite3.Connection bound to the current thread.
  - `close_connections(self) -> None`: Close all managed SQLite connections.
