# File: `llm/tools/math.py`

## Overview
Math calculation tools for LLM integration.

This module provides LangChain-compatible tools for performing mathematical
calculations using the MathCalculatorCog.

## Classes

### `MathTools`
Container class for mathematical calculation tools.

This class holds the runtime context and provides factory methods
to create tool instances bound to that context.

Attributes:
    runtime: The orchestrator request containing bot, message, and logger.

- **Attributes**:
  - `runtime` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, runtime: 'OrchestratorRequest') -> Any`: Initializes MathTools with runtime context.
  - `get_tools(self) -> list`: Returns a list of LangChain tools bound to this runtime.
