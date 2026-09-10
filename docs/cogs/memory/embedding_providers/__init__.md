# File: `cogs/memory/embedding_providers/__init__.py`

## Overview
Core module for __init__.py.

## Functions

### `_import_all_providers() -> None`
Import all modules in this package so that registration decorators run.
Provider modules should call register_embedding_provider when defined.

### `list_providers() -> List[str]`
Return registered embedding provider names.

### `get_provider_factory(name: str) -> Optional[Callable]`
Return the factory callable for a given provider name, or None if not found.
