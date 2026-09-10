# File: `cogs/eat/providers/googlemap_crawler.py`

## Overview
Core module for googlemap_crawler.py.

## Classes

### `GoogleMapCrawler`
Class representing GoogleMapCrawler.

- **Attributes**:
  - `_lock` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self) -> Any`: Method __init__.
  - `search_list(self, keyword: str, lang: str) -> list[dict]`: 快速爬取搜尋結果列表。
  - `fetch_detail(self, url: str, lang: str) -> dict`: 導航至特定餐廳頁面，抓取詳盡資訊（地址、評分、照片等）。
  - `async_search_list(self, keyword: str, lang: str) -> list[dict]`: Method async_search_list.
  - `async_fetch_detail(self, url: str, lang: str) -> dict`: Method async_fetch_detail.
  - `close(self) -> Any`: Method close.
