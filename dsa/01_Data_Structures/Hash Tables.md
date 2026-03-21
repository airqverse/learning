# Hash Tables

## 📋 Definition
> A data structure that implements an associative array abstract data type, a structure that can map keys to values. A hash function is used to compute an index into an array of buckets or slots.

## ⚙️ Operations & Complexity
| Operation | Time Complexity (Avg)                   | Space Complexity                        |
| --------- | --------------------------------------- | --------------------------------------- |
| Search    | [[04_Complexity/O(1) - Constant\|O(1)]] | [[04_Complexity/O(n) - Linear\|O(n)]]    |
| Insertion | [[04_Complexity/O(1) - Constant\|O(1)]] | [[04_Complexity/O(n) - Linear\|O(n)]]    |
| Deletion  | [[04_Complexity/O(1) - Constant\|O(1)]] | [[04_Complexity/O(n) - Linear\|O(n)]]    |

## 🐍 Python Implementation
```python
# In Python, dictionaries are hash tables.

# Initialization
hash_map = {}

# Insertion
hash_map["key"] = "value"

# Search / Access
val = hash_map.get("key") # "value"

# Check existence
if "key" in hash_map:
    print("Exists")

# Deletion
del hash_map["key"]
```

## 💡 Use Cases & Notes
- **Use when**: You need extremely fast lookups, insertions, and deletions based on a unique key.
- **Don't use when**: You need to maintain order (though Python 3.7+ dicts maintain insertion order) or need to find elements by value (which is O(n)).

---
[[00_Index/01_Data_Structures_MOC|Back to Data Structures Index]]