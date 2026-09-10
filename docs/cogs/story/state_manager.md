# File: `cogs/story/state_manager.py`

## Overview
Core module for state_manager.py.

## Classes

### `StoryStateManager`
Manages story state updates based on structured GM Action Plans.

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: Any) -> Any`: Method __init__.
  - `update_state_from_gm_plan(self, instance: StoryInstance, gm_plan: GMActionPlan) -> StoryInstance`: Updates the story state based on a structured GMActionPlan.
  - `initialize_default_state(self, instance: StoryInstance) -> StoryInstance`: Initialize default state for a new story instance.
