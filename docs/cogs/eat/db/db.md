# File: `cogs/eat/db/db.py`

## Overview
Core module for db.py.

## Classes

### `DB`
Class representing DB.

- **Attributes**:
  - `engine` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self) -> None`: Method __init__.
  - `getKeywords(self) -> list`: Method getKeywords.
  - `checkKeyword(self, keyword: String) -> Any`: Method checkKeyword.
  - `storeKeyword(self, keyword: str) -> None`: Method storeKeyword.
  - `storeSearchRecord(self, discord_id: str, title: str, keyword: str, map_rate: str, tag: str, map_address: str) -> int`: Method storeSearchRecord.
  - `getSearchRecoreds(self, discord_id: str) -> list`: Method getSearchRecoreds.
  - `updateRecordRate(self, id: int, new_rate: float) -> bool`: Method updateRecordRate.
  - `getRecentRecords(self, discord_id: str, days: int) -> list`: 取得最近 N 天內的搜尋記錄，用於避免重複推薦
  - `getLikedRecords(self, discord_id: str) -> list`: 取得 self_rate >= 1 的記錄（用戶喜歡的）
  - `getDislikedRecords(self, discord_id: str) -> list`: 取得 self_rate <= -1 的記錄（用戶不喜歡的）
