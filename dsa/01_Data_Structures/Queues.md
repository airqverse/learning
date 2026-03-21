# Queues

## 📋 Definition
> A linear data structure that follows the **First-In, First-Out (FIFO)** principle. The first element added to the queue is the first one to be removed.

## ⚙️ Operations & Complexity
| Operation | Time Complexity | Space Complexity |
| --------- | --------------- | ---------------- |
| Enqueue   | [[04_Complexity/O(1) - Constant\|O(1)]] | [[04_Complexity/O(1) - Constant\|O(1)]] |
| Dequeue   | [[04_Complexity/O(1) - Constant\|O(1)]] | [[04_Complexity/O(1) - Constant\|O(1)]] |
| Front/Peek| [[04_Complexity/O(1) - Constant\|O(1)]] | [[04_Complexity/O(1) - Constant\|O(1)]] |
| Search    | [[04_Complexity/O(n) - Linear\|O(n)]] | [[04_Complexity/O(1) - Constant\|O(1)]] |

## 🐍 Python Implementation
```python
from collections import deque

# Initialization
queue = deque()

# Enqueue (Add to back)
queue.append(10)
queue.append(20)

# Dequeue (Remove from front)
first = queue.popleft() # 10

# Peek
front = queue[0] if queue else None
```

## 💡 Use Cases & Notes
- **Use when**: Scheduling tasks, handling requests in a web server, or Breadth-First Search (BFS).
- **Note**: Avoid using `list.pop(0)` in Python as it is $O(n)$. Always prefer `collections.deque`.

---
[[00_Index/01_Data_Structures_MOC|Back to Data Structures Index]]