# File: `cogs/memory/services/vectorization_service.py`

## Overview
Core module for vectorization_service.py.

## Classes

### `VectorizationService`
Service responsible for converting EventSummary objects into MemoryFragment objects,
uploading them to the vector store.

Dependencies are injected to keep this service testable and decoupled:
  - bot: used only for contextual logging if needed
  - storage: implements StorageInterface
  - vector_manager: object that exposes .store.add_memories(...)
  - settings: MemoryConfig

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `storage` (`Any`): Instance attribute.
  - `vector_manager` (`Any`): Instance attribute.
  - `settings` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: Any, storage: StorageInterface, vector_manager: Any, settings: MemoryConfig) -> None`: Method __init__.
  - `process_event_summaries(self, event_summaries: List[EventSummary]) -> None`: Process a list of EventSummary objects and store them in the vector database.
  - `_convert_event_summaries_to_fragments(self, event_summaries: List[EventSummary]) -> List[MemoryFragment]`: Convert EventSummary objects to MemoryFragment objects.
