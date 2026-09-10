# File: `cogs/memory/services/event_summarization_service.py`

## Overview
EventSummarizationService: Process Discord message lists into meaningful events using LLM summarization.

## Classes

### `EventMetadata`
Structured metadata for an event.

- **Attributes**:
  - `start_message_id` (`int`): Class attribute.
  - `end_message_id` (`int`): Class attribute.
  - `channel_id` (`int`): Class attribute.
  - `guild_id` (`int`): Class attribute.
  - `user_ids` (`List[int]`): Class attribute.
  - `start_timestamp` (`float`): Class attribute.
  - `end_timestamp` (`float`): Class attribute.
  - `reaction_list` (`List[Dict[str, Any]]`): Class attribute.
  - `event_type` (`Optional[str]`): Class attribute.

### `Entity`
Represents an entity extracted from the conversation.

- **Attributes**:
  - `name` (`str`): Class attribute.
  - `type` (`str`): Class attribute.
  - `description` (`str`): Class attribute.

### `MemoryFragment`
Represents a single, distinct memory extracted from a conversation.

Attributes:
    query_key: A concise, objective, and human-readable summary of a specific
        event, decision, or piece of information from the conversation.
    query_keywords: A list of machine-optimized keywords for efficient
        database searching and retrieval.
    query_value: The detailed content of the memory, suitable for being
        returned as a search result.
    start_message_id: The ID of the first message in the conversation that
        is part of this memory.
    end_message_id: The ID of the last message in the conversation that is
        part of this memory.

- **Attributes**:
  - `query_key` (`str`): Class attribute.
  - `query_keywords` (`List[str]`): Class attribute.
  - `query_value` (`str`): Class attribute.
  - `start_message_id` (`int`): Class attribute.
  - `end_message_id` (`int`): Class attribute.
  - `entities` (`List[Entity]`): Class attribute.

### `MemoryFragmentList`
A list of MemoryFragment objects, representing all significant events extracted from a conversation.

Attributes:
    fragments: A list of memory fragments extracted from the conversation.

- **Attributes**:
  - `fragments` (`List[MemoryFragment]`): Class attribute.

### `EventSummary`
Structured output for an event summary.

- **Attributes**:
  - `query_key` (`str`): Class attribute.
  - `query_keywords` (`List[str]`): Class attribute.
  - `query_value` (`str`): Class attribute.
  - `entities` (`List[Dict[str, str]]`): Class attribute.
  - `metadata` (`EventMetadata`): Class attribute.

### `EventSummarizationService`
Service for processing Discord messages into meaningful event summaries using LLM.

This service groups related messages and uses LLM to extract key information
for improved memory retrieval and vectorization.

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `settings` (`Any`): Instance attribute.
  - `model_manager` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: discord.Client, settings: MemoryConfig) -> None`: Initialize the Event Summarization Service.
  - `_extract_structured_response(self, response: Any, expected_model: Type[T], context: str) -> Optional[T]`: Unified extractor for structured agent responses.
  - `summarize_events(self, messages: List[discord.Message], previous_summary: str) -> List[EventSummary]`: Process a list of messages and extract event summaries using LLM.
  - `_group_messages(self, messages: List[discord.Message]) -> List[List[discord.Message]]`: Group related messages into events.
  - `_process_message_group(self, messages: List[discord.Message], previous_summary: str) -> Optional[List[EventSummary]]`: Process a group of messages into an event summary using LLM.
  - `_prepare_message_data(self, messages: List[discord.Message]) -> List[Dict[str, Any]]`: Prepare message data for LLM processing.
  - `_get_llm_summary(self, message_data: List[Dict[str, Any]], previous_summary: str) -> Optional[MemoryFragmentList]`: Get event summary from LLM using the episodic memory extractor prompt with structured output.
  - `_create_llm_instance(self, model_name: str, force_json: bool) -> Any`: Create a LangChain model instance from a model name string.
  - `_get_system_prompt(self) -> str`: Get the system prompt from the episodic memory extractor template.
  - `_get_user_prompt_with_messages(self, message_data: List[Dict[str, Any]], previous_summary: str) -> str`: Get the user prompt with the prepared message data.
  - `_create_event_summary(self, messages: List[discord.Message], memory_fragment: MemoryFragment) -> Optional[EventSummary]`: Create an EventSummary from LLM response and message metadata.
  - `_generate_query_value(self, summary: str, query_key: str) -> str`: Generate query value for vector search.
  - `_create_event_metadata(self, messages: List[discord.Message], memory_fragment: MemoryFragment) -> EventMetadata`: Create event metadata from a group of messages using MemoryFragment info.
