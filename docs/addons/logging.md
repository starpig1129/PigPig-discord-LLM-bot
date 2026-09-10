# File: `addons/logging.py`

## Overview
Core module for logging.py.

## Classes

### `LogRecord`
Structured log record following plan.md schema.

- **Attributes**:
  - `timestamp` (`str`): Class attribute.
  - `level` (`str`): Class attribute.
  - `source` (`str`): Class attribute.
  - `server_id` (`str`): Class attribute.
  - `channel_or_file` (`str`): Class attribute.
  - `user_id` (`str`): Class attribute.
  - `action` (`str`): Class attribute.
  - `message` (`str`): Class attribute.
  - `trace_id` (`Optional[str]`): Class attribute.
  - `extra` (`Dict[str, Any]`): Class attribute.

- **Methods**:
  - `to_json_line(self) -> str`: Serialize record to a single NDJSON line.

### `BackgroundWriter`
Background single-thread writer that batches NDJSON records and writes per-level files.

- **Attributes**:
  - `batch_size` (`int`): Instance attribute.
  - `flush_interval` (`float`): Instance attribute.
  - `queue_maxsize` (`int`): Instance attribute.
  - `_queue` (`'Queue[Dict[str, Any]]'`): Instance attribute.
  - `_thread` (`Any`): Instance attribute.
  - `_stop_event` (`Any`): Instance attribute.
  - `_metrics` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self) -> Any`: Method __init__.
  - `enqueue(self, server_id: str, level: str, json_line: str, timestamp_iso: str) -> None`: Attempt to enqueue a log event non-blocking. On full queue, drop and report.
  - `_report_error_async(self, exc: Exception, context: str) -> None`: Report errors through func.report_error if available, fallback to printing.
  - `stop(self, timeout: float) -> None`: Signal worker to stop and flush remaining items.
  - `_worker(self) -> None`: Worker loop: collect batches and perform grouped writes per server/date/level.

### `LoggerAdapter`
Logger-like object exposing bind(...) and level methods (info/warning/error/debug).

This provides a minimal structlog-like API for bindable context while delegating
actual output to BackgroundWriter and loguru console renderer.

- **Attributes**:
  - `server_id` (`Any`): Instance attribute.
  - `source` (`Any`): Instance attribute.
  - `channel` (`Any`): Instance attribute.
  - `bound_context` (`Dict[str, Any]`): Instance attribute.
  - `_writer` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, server_id: str, source: str, channel: Optional[str], bound: Optional[Dict[str, Any]]) -> Any`: Method __init__.
  - `isEnabledFor(self, level: int) -> bool`: Check if the given numeric level is enabled based on current CONFIG.
  - `bind(self, **context: Any) -> 'LoggerAdapter'`: Return a new LoggerAdapter with merged context, similar to structlog.bind.
  - `_emit(self, level: str, message: str, exception: Optional[BaseException], **event_fields: Any) -> None`: Compose structured record, enqueue NDJSON line, and render to console as single-line text.
  - `_format_console_line(self, record: LogRecord) -> str`: Create enhanced console representation with simplified timestamp and optional emoji.
  - `_colorize_line(self, record: LogRecord, line: str) -> str`: Apply ANSI color codes to different parts of the log line for better readability.
  - `info(self, message: Optional[str], *args: Any, exception: Optional[BaseException], **event_fields: Any) -> None`: Emit an INFO event.
  - `warning(self, message: Optional[str], *args: Any, exception: Optional[BaseException], **event_fields: Any) -> None`: Emit a WARNING event.
  - `error(self, message: Optional[str], *args: Any, exception: Optional[BaseException], **event_fields: Any) -> None`: Emit an ERROR event.
  - `debug(self, message: Optional[str], *args: Any, exception: Optional[BaseException], **event_fields: Any) -> None`: Emit a DEBUG event.
  - `exception(self, message: Optional[str], *args: Any, **event_fields: Any) -> None`: Log an ERROR-level event with the current exception traceback.

### `InterceptHandler`
Logging.Handler that redirects stdlib logging records into our structured logger.

It routes messages to get_logger(server_id='Bot', source=record.name) while avoiding
recursion from this module or loguru internals.

- **Methods**:
  - `emit(self, record: logging.LogRecord) -> None`: Method emit.

## Functions

### `_check_color_support() -> bool`
Enhanced check for terminal color support including Windows.

### `load_config_from_settings() -> None`
Load logging configuration from addons.settings.base_config and merge with defaults.

This function should be called by addons.settings after it successfully
constructs BaseConfig from CONFIG_ROOT so user configuration is applied.

### `init_loguru_console() -> None`
Initialize or reconfigure the loguru console sink based on current CONFIG.

Call this after load_config_from_settings() so the console format and color
options come from the user's configuration.

### `get_logger(server_id: Any, source: str, channel: Optional[str]) -> LoggerAdapter`
Factory returning a bindable logger-like object for a given server_id.

server_id: string or int representing server/guild id
source: "server" | "system" | "external"
channel: optional channel or file name for context

### `configure_std_logging() -> None`
Configure the standard library logging to route through InterceptHandler and apply third-party levels.

This function:
- Removes existing handlers from the root logger.
- Adds InterceptHandler to capture stdlib logging and funnel it into our structured logger.
- Attempts to remove non-root handlers to avoid duplicate/unstructured outputs.
- Applies per-logger level overrides from settings.base_config.logging['third_party_levels'] if present.
