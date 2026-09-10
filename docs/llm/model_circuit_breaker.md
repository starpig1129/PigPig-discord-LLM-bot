# File: `llm/model_circuit_breaker.py`

## Overview
ModelCircuitBreaker: Tracks model failures and temporarily skips known-failing models.

This module implements a circuit breaker pattern to prevent repeated API calls
to models that are known to fail (due to quota exhaustion, non-existent models,
rate limits, etc.). Failed models are temporarily marked as 'open' (unavailable)
and will be skipped until a cooldown period expires.

Typical usage:
    from llm.model_circuit_breaker import get_model_circuit_breaker

    cb = get_model_circuit_breaker()

    # Check before calling
    if cb.is_available(model_name):
        try:
            result = await call_model(model_name)
        except Exception as e:
            cb.record_failure(model_name, e)

## Classes

### `ErrorCategory`
Categorizes errors for different cooldown strategies.

### `FailureRecord`
Record of a model failure.

- **Attributes**:
  - `model_name` (`str`): Class attribute.
  - `category` (`ErrorCategory`): Class attribute.
  - `failure_time` (`float`): Class attribute.
  - `cooldown_until` (`float`): Class attribute.
  - `error_message` (`str`): Class attribute.
  - `consecutive_failures` (`int`): Class attribute.

### `ModelCircuitBreaker`
Thread-safe circuit breaker for LLM model calls.

Tracks model failures and temporarily disables calls to models that are
known to be failing. This prevents wasting API quota and reduces latency
by avoiding doomed retry attempts.

Attributes:
    _failures: Dict mapping model names to their failure records.
    _lock: Threading lock for thread-safe operations.

- **Attributes**:
  - `_failures` (`Dict[str, FailureRecord]`): Instance attribute.
  - `_lock` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self) -> None`: Initialize the circuit breaker with empty failure tracking.
  - `categorize_error(self, error: Exception) -> ErrorCategory`: Classify an exception into an error category.
  - `is_available(self, model_name: str) -> bool`: Check if a model is currently available (not in cooldown).
  - `record_failure(self, model_name: str, error: Exception, category: Optional[ErrorCategory]) -> ErrorCategory`: Record a model failure and start the cooldown period.
  - `reset(self, model_name: Optional[str]) -> None`: Reset circuit breaker state.

## Functions

### `get_model_circuit_breaker() -> ModelCircuitBreaker`
Get the global ModelCircuitBreaker singleton instance.

Returns:
    The singleton ModelCircuitBreaker instance.
