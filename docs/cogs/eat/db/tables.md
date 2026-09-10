# File: `cogs/eat/db/tables.py`

## Overview
Core module for tables.py.

## Classes

### `UserPref`
Class representing UserPref.

### `SearchRecord`
Class representing SearchRecord.

- **Attributes**:
  - `discord_id` (`Any`): Instance attribute.
  - `keyword` (`Any`): Instance attribute.
  - `title` (`Any`): Instance attribute.
  - `tag` (`Any`): Instance attribute.
  - `address` (`Any`): Instance attribute.
  - `map_rate` (`Any`): Instance attribute.
  - `self_rate` (`Any`): Instance attribute.
  - `date` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, discord_id: str, title: str, keyword: str, tag: str, address: str, map_rate: str, self_rate: float) -> Any`: Method __init__.

### `Keywords`
Class representing Keywords.

- **Attributes**:
  - `keyword` (`Any`): Instance attribute.
  - `add_date` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, keyword: String) -> Any`: Method __init__.
