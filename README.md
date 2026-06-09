[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/TeyGQAqr)

# Weekly Coding #3 — Metro City Help Center

## Overview

This project implements stack and queue data structures in pure Python (stdlib only) to simulate a Metro City Help Center support system.

## Files

- `src/challenges.py` — All implemented classes and functions.

## Data Structures

### `ActionStack`
A stack of recent help-center actions backed by a Python list. Follows **LIFO** (Last In, First Out) order.

### `RequestQueue`
A queue of waiting citizens backed by `collections.deque`. Follows **FIFO** (First In, First Out) order.

## Implemented Functions

### `ActionStack.push(action: str) -> None`
Adds an action to the top of the stack.

### `ActionStack.pop() -> str | None`
Removes and returns the top action. Returns `None` if empty.
- **Time complexity:** O(1) — `list.pop()` from the end is constant time.

### `ActionStack.peek() -> str | None`
Returns the top action without removing it. Returns `None` if empty.

### `ActionStack.is_empty() -> bool`
Returns `True` if the stack has no actions.

### `RequestQueue.enqueue(name: str) -> None`
Adds a citizen name to the back of the queue.

### `RequestQueue.dequeue() -> str | None`
Removes and returns the front citizen. Returns `None` if empty.
- **Time complexity:** O(1) — `deque.popleft()` is constant time.

### `RequestQueue.peek() -> str | None`
Returns the front citizen without removing it. Returns `None` if empty.

### `RequestQueue.is_empty() -> bool`
Returns `True` if the queue has no waiting citizens.

### `is_note_balanced(note: str) -> bool`
Returns `True` if all `()`, `[]`, and `{}` brackets in the note are correctly balanced.
- **Time complexity:** O(n) — visits each character once.

### `process_request_line(citizens: list[str]) -> list[str]`
Returns citizens in the order they are served (FIFO).
- **Time complexity:** O(n) — enqueues and dequeues each citizen once.

### `undo_recent_actions(actions: list[str], undo_count: int) -> list[str]` *(Stretch)*
Removes the most recent `undo_count` actions and returns the remaining list.

## Edge Cases Handled

- Empty action stack — `pop()` and `peek()` return `None`
- Empty request queue — `dequeue()` and `peek()` return `None`
- Empty string for `is_note_balanced` — returns `True`
- Note with no brackets — returns `True`
- Empty citizen list — returns `[]`

## Example Usage

```python
from src.challenges import (
    ActionStack,
    RequestQueue,
    is_note_balanced,
    process_request_line,
    undo_recent_actions,
)

# Stack
stack = ActionStack()
stack.push("open ticket")
stack.push("assign agent")
print(stack.pop())   # assign agent
print(stack.peek())  # open ticket

# Queue
queue = RequestQueue()
queue.enqueue("Alice")
queue.enqueue("Bob")
print(queue.dequeue())  # Alice

# Balanced brackets
print(is_note_balanced("(hello [world])"))  # True
print(is_note_balanced("(hello [world)"))   # False

# Process line
print(process_request_line(["Alice", "Bob", "Charlie"]))  # ['Alice', 'Bob', 'Charlie']

# Undo actions
print(undo_recent_actions(["a", "b", "c"], 2))  # ['a']
```

## Complexity Summary

| Function | Time | Why |
|---|---|---|
| `ActionStack.pop` | O(1) | `list.pop()` from the end is constant time |
| `RequestQueue.dequeue` | O(1) | `deque.popleft()` is constant time |
| `is_note_balanced` | O(n) | visits each character once |
| `process_request_line` | O(n) | enqueues and dequeues each citizen once |

## Requirements

- Python 3.10+
- No third-party libraries (stdlib only)

## Assistance & Sources

- AI used? Y
- What it helped with: Implementation guidance and complexity analysis
- Other sources: Python docs (collections.deque)