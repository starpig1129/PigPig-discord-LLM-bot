# File: `cogs/memory/db/knowledge_storage.py`

## Overview
KnowledgeStorage: handles guild and channel level knowledge storage.

This module provides persistence for shared interaction knowledge, including
inside jokes, relationships, and special events.

## Classes

### `KnowledgeStorage`
Handles knowledge table storage operations.

- **Attributes**:
  - `db` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, db: DatabaseConnection) -> None`: Initialize with a DatabaseConnection instance.
  - `update_knowledge(self, target_type: str, target_id: str, content: str) -> bool`: Update or insert knowledge for a specific scope.
  - `delete_knowledge(self, target_type: str, target_id: str) -> bool`: Delete knowledge for a specific scope.
