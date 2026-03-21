# Dynamic Arrays

## 📋 Definition
> An array that can grow or shrink in size automatically as elements are added or removed. It manages its capacity by allocating a new, larger underlying static array and copying elements when the current capacity is reached.

## ⚙️ Operations & Complexity
| Operation | Time Complexity | Space Complexity |
| --------- | --------------- | ---------------- |
| Access    | [[04_Complexity/O(1) - Constant\|O(1)]] | [[04_Complexity/O(1) - Constant\|O(1)]] |
| Search    | [[04_Complexity/O(n) - Linear\|O(n)]] | [[04_Complexity/O(1) - Constant\|O(1)]] |
| Insertion (at end) | [[04_Complexity/O(1) - Constant\|O(1)]] (Amortized) | [[04_Complexity/O(n) - Linear\|O(n)]] |
| Deletion (at end) | [[04_Complexity/O(1) - Constant\|O(1)]] | [[04_Complexity/O(1) - Constant\|O(1)]] |
| Insertion (middle) | [[04_Complexity/O(n) - Linear\|O(n)]] | [[04_Complexity/O(1) - Constant\|O(1)]] |
| Deletion (middle) | [[04_Complexity/O(n) - Linear\|O(n)]] | [[04_Complexity/O(1) - Constant\|O(1)]] |

*Note: Insertion at the end is [[04_Complexity/Amortized Analysis|Amortized O(1)]] because resizing happens infrequently.*

## 🐍 Python Implementation
```python
# In Python, the built-in 'list' is a dynamic array.

# Initialization
dynamic_arr = []

# Adding elements - O(1) amortized
dynamic_arr.append(10)
dynamic_arr.append(20)
dynamic_arr.append(30)

# Access - O(1)
first_element = dynamic_arr[0]

# Insertion at a specific index - O(n)
dynamic_arr.insert(1, 15)

# Removing from the end - O(1)
last_element = dynamic_arr.pop()

# Removing from a specific index - O(n)
dynamic_arr.pop(0)

# Size of the array
length = len(dynamic_arr)
```

## 💡 Use Cases & Notes
- **Use when**: You don't know the final size of the collection in advance and need fast random access.
- **Don't use when**: You need frequent insertions/deletions at the beginning or middle, as these require shifting all subsequent elements.
- **Implementation Detail**: Most dynamic arrays double in size when they reach capacity (growth factor of 2).

---
[[00_Index/01_Data_Structures_MOC|Back to Data Structures Index]]
