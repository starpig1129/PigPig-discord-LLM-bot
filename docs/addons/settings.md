# File: `addons/settings.py`

## Overview
Core module for settings.py.

## Classes

### `BaseConfig`
Configuration object mapped from config/base.yaml

- **Attributes**:
  - `path` (`Any`): Instance attribute.
  - `prefix` (`str`): Instance attribute.
  - `activity` (`list`): Instance attribute.
  - `ipc_server` (`dict`): Instance attribute.
  - `version` (`str`): Instance attribute.
  - `dashboard` (`dict`): Instance attribute.
  - `logging` (`dict`): Instance attribute.

- **Methods**:
  - `__init__(self, path: str) -> None`: Method __init__.

### `LLMConfig`
Configuration object mapped from config/llm.yaml

- **Attributes**:
  - `path` (`Any`): Instance attribute.
  - `data` (`dict`): Instance attribute.
  - `model_priorities` (`list`): Instance attribute.
  - `google_search_agent` (`str`): Instance attribute.
  - `vllm_url` (`Optional[str]`): Instance attribute.
  - `ollama_url` (`Optional[str]`): Instance attribute.
  - `llm_call_timeout` (`float`): Instance attribute.
  - `reasoning_optimization_prompt` (`str`): Instance attribute.

- **Methods**:
  - `__init__(self, path: str) -> None`: Method __init__.

### `UpdateConfig`
Configuration object mapped from config/update.yaml

- **Attributes**:
  - `path` (`Any`): Instance attribute.
  - `auto_update` (`dict`): Instance attribute.
  - `security` (`dict`): Instance attribute.
  - `notification` (`dict`): Instance attribute.
  - `restart` (`dict`): Instance attribute.
  - `github` (`dict`): Instance attribute.

- **Methods**:
  - `__init__(self, path: str) -> None`: Method __init__.

### `MusicConfig`
Configuration object mapped from config/music.yaml

- **Attributes**:
  - `path` (`Any`): Instance attribute.
  - `music_temp_base` (`dict`): Instance attribute.
  - `ffmpeg` (`dict`): Instance attribute.
  - `youtube_cookies_path` (`str`): Instance attribute.

- **Methods**:
  - `__init__(self, path: str) -> None`: Method __init__.

### `PromptConfig`
Configuration object mapped from config/prompt/*.yaml

- **Attributes**:
  - `path` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, path: str) -> None`: Method __init__.

### `MemoryConfig`
Memory subsystem configuration object mapped from config/memory.yaml

- **Attributes**:
  - `path` (`Any`): Instance attribute.
  - `enabled` (`bool`): Instance attribute.
  - `procedural_cache_ttl` (`float`): Instance attribute.
  - `knowledge_cache_ttl` (`float`): Instance attribute.
  - `episodic_cache_ttl` (`float`): Instance attribute.
  - `knowledge_max_cache_size` (`int`): Instance attribute.
  - `episodic_max_cache_size` (`int`): Instance attribute.
  - `procedural_data_path` (`str`): Instance attribute.
  - `episodic_data_path` (`str`): Instance attribute.
  - `vector_store_type` (`str`): Instance attribute.
  - `qdrant_url` (`str`): Instance attribute.
  - `qdrant_api_key` (`Optional[str]`): Instance attribute.
  - `qdrant_collection_name` (`str`): Instance attribute.
  - `embedding_provider` (`str`): Instance attribute.
  - `embedding_model_name` (`str`): Instance attribute.
  - `embedding_dim` (`int`): Instance attribute.
  - `vector_search_k` (`int`): Instance attribute.
  - `keyword_search_k` (`int`): Instance attribute.
  - `vllm_url` (`Optional[str]`): Instance attribute.
  - `ollama_url` (`Optional[str]`): Instance attribute.
  - `provider_options` (`dict`): Instance attribute.
  - `short_term_limit` (`int`): Instance attribute.
  - `episodic_top_k` (`int`): Instance attribute.
  - `episodic_max_chars` (`int`): Instance attribute.
  - `message_threshold` (`int`): Instance attribute.
  - `time_threshold` (`int`): Instance attribute.
  - `processing_concurrency` (`int`): Instance attribute.
  - `processing_delay` (`float`): Instance attribute.

- **Methods**:
  - `__init__(self, path: str) -> None`: Method __init__.

### `_AttachmentImageConfig`
Class representing _AttachmentImageConfig.

- **Attributes**:
  - `enabled` (`bool`): Instance attribute.
  - `max_dimension` (`int`): Instance attribute.

- **Methods**:
  - `__init__(self, data: dict) -> None`: Method __init__.

### `_AttachmentPdfConfig`
Class representing _AttachmentPdfConfig.

- **Attributes**:
  - `enabled` (`bool`): Instance attribute.
  - `max_pages` (`int`): Instance attribute.
  - `dpi_full` (`int`): Instance attribute.
  - `dpi_medium` (`int`): Instance attribute.
  - `dpi_compressed` (`int`): Instance attribute.
  - `threshold_full` (`int`): Instance attribute.
  - `threshold_medium` (`int`): Instance attribute.
  - `notify_truncated` (`bool`): Instance attribute.

- **Methods**:
  - `__init__(self, data: dict) -> None`: Method __init__.

### `_AttachmentVideoConfig`
Class representing _AttachmentVideoConfig.

- **Attributes**:
  - `enabled` (`bool`): Instance attribute.
  - `max_frames` (`int`): Instance attribute.
  - `min_interval_sec` (`float`): Instance attribute.

- **Methods**:
  - `__init__(self, data: dict) -> None`: Method __init__.

### `_AttachmentEmbedsConfig`
Class representing _AttachmentEmbedsConfig.

- **Attributes**:
  - `enabled` (`bool`): Instance attribute.
  - `include_images` (`bool`): Instance attribute.

- **Methods**:
  - `__init__(self, data: dict) -> None`: Method __init__.

### `AttachmentConfig`
Configuration for attachment and embed processing (base_configs/attachments.yaml).

- **Attributes**:
  - `path` (`Any`): Instance attribute.
  - `enabled` (`bool`): Instance attribute.
  - `max_download_bytes` (`int`): Instance attribute.
  - `image` (`Any`): Instance attribute.
  - `pdf` (`Any`): Instance attribute.
  - `video` (`Any`): Instance attribute.
  - `embeds` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, path: str) -> None`: Method __init__.

## Functions

### `_load_yaml_file(path: str) -> dict`
Safely load a YAML file; report errors via func.report_error and return an empty dict on failure.

### `_get_config_root() -> str`
Read CONFIG_ROOT environment variable.

If CONFIG_ROOT is not set, report the issue via func.report_error and
fall back to 'config' to allow startup to continue.
