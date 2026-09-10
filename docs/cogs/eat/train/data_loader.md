# File: `cogs/eat/train/data_loader.py`

## Overview
Core module for data_loader.py.

## Classes

### `DataLoader`
Class representing DataLoader.

- **Attributes**:
  - `db` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, db: DB) -> None`: Method __init__.
  - `loadingData(self, discord_id: str) -> Any`: Method loadingData.
  - `procressData(self, data: Any) -> Any`: Method procressData.
  - `genVocabularyList(self, data: Any) -> Any`: Method genVocabularyList.
  - `transform(self, data: Any, voc_length: Any, batch_size: Any) -> Any`: Method transform.
