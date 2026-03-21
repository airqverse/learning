# Arrays

## 📋 Definition
> A collection of elements stored in contiguous memory locations, where each element is identified by at least one array index or key.

## ⚙️ Operations & Complexity
| Operation | Time Complexity                          | Space Complexity                        |
| --------- | ---------------------------------------- | --------------------------------------- |
| Access    | [[04_Complexity/O(1) - Constant \|O(1)]] | [[04_Complexity/O(1) - Constant\|O(1)]] |
| Search    | [[04_Complexity/O(n) - Linear\|O(n)]]    | [[04_Complexity/O(1) - Constant\|O(1)]] |
| Insertion | [[04_Complexity/O(n) - Linear\|O(n)]]    | [[04_Complexity/O(1) - Constant\|O(1)]] |
| Deletion  | [[04_Complexity/O(n) - Linear\|O(n)]]    | [[04_Complexity/O(1) - Constant\|O(1)]] |

## 🐍 Python Implementation
```python
# In Python, lists are dynamic arrays.
# Initialization
arr = [10, 20, 30, 40, 50]

# Access - O(1)
print(arr[2]) # 30

# Search - O(n)
if 30 in arr:
    print("Found")

# Insertion (at end) - O(1) amortized
arr.append(60)

# Insertion (at specific index) - O(n)
arr.insert(1, 15)

# Deletion - O(n)
arr.pop(2) # Removes element at index 2
```

## 💡 Use Cases & Notes
- **Use when**: You need fast access to elements via index and know the approximate size of the data.
- **Don't use when**: You need frequent insertions/deletions at the beginning or middle of the collection.

---
[[00_Index/01_Data_Structures_MOC|Back to Data Structures Index]]