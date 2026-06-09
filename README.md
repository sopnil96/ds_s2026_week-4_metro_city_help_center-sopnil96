[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/TeyGQAqr)

# Week 3 Homework: The Royal Rail Ledger

## Overview

This project implements singly and doubly linked list operations in pure Python (stdlib only).

## Files

- `src/challenges.py` — All implemented functions and node/list class definitions.

## Data Structures

### `SLLNode` / `SinglyLinkedList`
A basic singly linked list where each node holds a value and a reference to the next node.

### `DLLNode` / `DoublyLinkedList`
A doubly linked list where each node holds a value and references to both the previous and next nodes. The list maintains both `head` and `tail` references.

## Implemented Functions

### `build_sll_from_list(values: list[int]) -> SinglyLinkedList`
Builds and returns a singly linked list from a Python list.

### `sll_to_list(sll: SinglyLinkedList) -> list[int]`
Converts a singly linked list back into a Python list.

### `find_first_repeat_sll(sll: SinglyLinkedList) -> int | None`
Traverses the singly linked list from left to right and returns the first value that appears more than once. Returns `None` if no duplicates exist.

- **Time complexity:** O(n)
- **Space complexity:** O(n)
- Uses a `set` to track seen values.

### `remove_all_from_dll(dll: DoublyLinkedList, target: int) -> None`
Removes all nodes from the doubly linked list whose value equals `target`. Correctly updates `head`, `tail`, and all `prev`/`next` pointers in-place.

### `is_train_palindrome(dll: DoublyLinkedList) -> bool` *(Stretch)*
Returns `True` if the doubly linked list reads the same forward and backward. Uses a two-pointer approach starting from `head` and `tail`, meeting in the middle.

- Handles even and odd length lists correctly.
- Returns `True` for an empty list.

## Example Usage

```python
from src.challenges import (
    build_sll_from_list,
    sll_to_list,
    find_first_repeat_sll,
    remove_all_from_dll,
    is_train_palindrome,
    DoublyLinkedList,
    DLLNode,
)

# Singly linked list
sll = build_sll_from_list([1, 2, 3, 2, 4])
print(sll_to_list(sll))           # [1, 2, 3, 2, 4]
print(find_first_repeat_sll(sll)) # 2

# Doubly linked list - remove all
dll = DoublyLinkedList()
dll.head = DLLNode(1)
dll.head.next = DLLNode(2, prev=dll.head)
dll.head.next.next = DLLNode(1, prev=dll.head.next)
dll.tail = dll.head.next.next
remove_all_from_dll(dll, 1)
# dll now contains only: [2]

# Palindrome check
dll2 = DoublyLinkedList()
dll2.head = DLLNode(1)
dll2.head.next = DLLNode(2, prev=dll2.head)
dll2.head.next.next = DLLNode(1, prev=dll2.head.next)
dll2.tail = dll2.head.next.next
print(is_train_palindrome(dll2))  # True
```

## Requirements

- Python 3.10+
- No third-party libraries (stdlib only)