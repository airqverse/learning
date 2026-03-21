# Stacks

## 📋 Definition
> A linear data structure that follows the **Last-In, First-Out (LIFO)** principle. The last element added to the stack is the first one to be removed.

## ⚙️ Operations & Complexity
| Operation | Time Complexity | Space Complexity |
| --------- | --------------- | ---------------- |
| Push      | [[04_Complexity/O(1) - Constant\|O(1)]] | [[04_Complexity/O(1) - Constant\|O(1)]] |
| Pop       | [[04_Complexity/O(1) - Constant\|O(1)]] | [[04_Complexity/O(1) - Constant\|O(1)]] |
| Peek/Top  | [[04_Complexity/O(1) - Constant\|O(1)]] | [[04_Complexity/O(1) - Constant\|O(1)]] |
| Search    | [[04_Complexity/O(n) - Linear\|O(n)]] | [[04_Complexity/O(1) - Constant\|O(1)]] |

## 🐍 Python Implementation
```python
# Using a list (standard approach)
stack = []

# Push
stack.append('a')
stack.append('b')

# Pop
item = stack.pop() # 'b'

# Peek
top = stack[-1] if stack else None

# Using collections.deque (more efficient for large data)
from collections import deque
stack = deque()
stack.append('a')
stack.pop()
```

## 💡 Use Cases & Notes
- **Use when**: Managing function calls (Call Stack), reversing data, or implementing "undo" mechanisms.
- **Key Algorithms**: Depth-First Search (DFS), Expression Parsing.

---
[[00_Index/01_Data_Structures_MOC|Back to Data Structures Index]]