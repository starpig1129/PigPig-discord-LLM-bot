# File: `cogs/memory/services/message_tracker.py`

## Overview
Core module for message_tracker.py.

## Classes

### `MessageTracker`
Tracks new messages in channels for the memory system.

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `storage` (`Any`): Instance attribute.
  - `settings` (`Any`): Instance attribute.
  - `_pending_message_count` (`Any`): Instance attribute.
  - `_processing_tasks` (`Any`): Instance attribute.
  - `_processing_semaphore` (`Any`): Instance attribute.
  - `_active_summarization_task` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: 'Bot', storage: 'StorageInterface', settings: MemoryConfig) -> Any`: Initializes the MessageTracker.
  - `track_message(self, message: discord.Message) -> Any`: Tracks a message, adding it to the pending list if it's not from a bot
  - `_schedule_processing(self, channel: Union[discord.TextChannel, discord.VoiceChannel, discord.StageChannel, discord.Thread]) -> Any`: Schedules channel memory processing with a debounce delay.
  - `interrupt_all(self) -> Any`: Interrupts all pending and active memory processing tasks.
  - `_process_channel_memory(self, channel: Union[discord.TextChannel, discord.VoiceChannel, discord.StageChannel, discord.Thread]) -> Any`: Processes memory for a channel when threshold is reached.
  - `reset_pending_count(self) -> Any`: Resets the pending message count to zero.

## Functions

### `discord_id_to_unix_timestamp(message_id: int) -> float`
Convert Discord message ID to Unix timestamp in milliseconds.

Args:
    message_id (int): The Discord message ID

Returns:
    float: The Unix timestamp in milliseconds when the message was created
