# Heaps

## 📋 Definition
> A specialized tree-based data structure that satisfies the heap property: in a **Min-Heap**, for any given node $C$, if $P$ is a parent node of $C$, then the key of $P$ is less than or equal to the key of $C$.

## ⚙️ Operations & Complexity
| Operation | Time Complexity | Space Complexity |
| --------- | --------------- | ---------------- |
| Insert    | [[04_Complexity/O(log n) - Logarithmic\|O(log n)]] | [[04_Complexity/O(1) - Constant\|O(1)]] |
| Delete (Extract Min/Max) | [[04_Complexity/O(log n) - Logarithmic\|O(log n)]] | [[04_Complexity/O(1) - Constant\|O(1)]] |
| Peek (Min/Max) | [[04_Complexity/O(1) - Constant\|O(1)]] | [[04_Complexity/O(1) - Constant\|O(1)]] |
| Heapify   | [[04_Complexity/O(n) - Linear\|O(n)]] | [[04_Complexity/O(1) - Constant\|O(1)]] |

## 🐍 Python Implementation
```python
import heapq

# Python's heapq implements a Min-Heap
heap = []

# Insert (push)
heapq.heappush(heap, 10)
heapq.heappush(heap, 5)
heapq.heappush(heap, 15)

# Peek
min_val = heap[0] # 5

# Delete (pop the smallest)
smallest = heapq.heappop(heap) # 5

# Transform list to heap in-place
nums = [3, 1, 4, 1, 5]
heapq.heapify(nums)
```

## 💡 Use Cases & Notes
- **Use when**: Implementing priority queues, finding the k-th smallest/largest element, or in algorithms like Dijkstra's.
- **Max-Heap in Python**: Multiply values by -1 before pushing, then multiply by -1 after popping.

---
[[00_Index/01_Data_Structures_MOC|Back to Data Structures Index]]