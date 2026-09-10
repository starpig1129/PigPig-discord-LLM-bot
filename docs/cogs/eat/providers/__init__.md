# File: `cogs/eat/providers/__init__.py`

## Overview
餐廳搜尋 Provider 工廠

根據環境變數自動選擇最合適的 Provider：
- 有 FOURSQUARE_API_KEY → FoursquareProvider（免費 API，每月 1000 次）
- 否則 → GoogleMapCrawler fallback（Selenium 爬蟲，較慢但無費用限制）

## Classes

### `_SeleniumFallbackProvider`
將 GoogleMapCrawler 包裝為符合 Provider 介面的 fallback。

- **Attributes**:
  - `_crawler` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, crawler: Any) -> Any`: Method __init__.
  - `async_search_list(self, keyword: str, lang: str) -> list[dict]`: Method async_search_list.
  - `async_fetch_detail(self, url: str, lang: str) -> dict`: Method async_fetch_detail.
  - `search(self, keyword: str, lang: str) -> list[dict]`: Method search.
  - `close(self) -> Any`: Method close.

## Functions

### `get_restaurant_provider() -> Any`
返回最合適的餐廳搜尋 Provider 實例。
