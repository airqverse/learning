# Linear Search

## 🎯 Goal
> Find the position of a target value within a list by checking each element sequentially until a match is found or the end of the list is reached.

## 🧠 Logic & Steps
1. Start from the first element of the list.
2. Compare the current element with the target value.
3. If the current element matches the target, return its index.
4. If not, move to the next element.
5. Repeat steps 2-4 until the end of the list is reached.
6. If the end of the list is reached without finding a match, return -1.

## 🐍 Python Implementation
```python
def linear_search(arr, target):
    for i in range(len(arr)):
        if arr[i] == target:
            return i
    return -1
```

## 📊 Performance
- **Time Complexity**: [[04_Complexity/O(n) - Linear|O(n)]]
- **Space Complexity**: [[04_Complexity/O(1) - Constant|O(1)]]

## 🔗 Related Data Structures
- [[01_Data_Structures/Static Arrays|Static Arrays]]
- [[01_Data_Structures/Linked Lists|Linked Lists]]

---
[[00_Index/02_Algorithms_MOC|Back to Algorithms Index]]