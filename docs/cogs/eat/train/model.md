# File: `cogs/eat/train/model.py`

## Overview
Core module for model.py.

## Classes

### `Net`
Class representing Net.

- **Attributes**:
  - `embedding_dim` (`Any`): Instance attribute.
  - `hidden_dim` (`Any`): Instance attribute.
  - `embeddings` (`Any`): Instance attribute.
  - `lstm` (`Any`): Instance attribute.
  - `hidden2out` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, n_vocab: Any, embedding_dim: Any, hidden_dim: Any, dropout: Any) -> Any`: Method __init__.
  - `forward(self, seq_in: Any) -> Any`: Method forward.
