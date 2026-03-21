# Binary Search

## 🎯 Goal
> Find the position of a target value within a **sorted** array by repeatedly dividing the search interval in half.

## 🧠 Logic & Steps
1. Start with the entire array.
2. Compare the target value to the middle element.
3. If the target is the middle element, return its index.
4. If the target is less than the middle element, narrow the interval to the lower half.
5. If the target is greater, narrow it to the upper half.
6. Repeat until the target is found or the interval is empty.

## 🐍 Python Implementation
```python
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
            
    return -1
```

## 📊 Performance
- **Time Complexity**: [[04_Complexity/O(log n) - Logarithmic|O(log n)]]
- **Space Complexity**: [[04_Complexity/O(1) - Constant|O(1)]] (Iterative)

## 🔗 Related Data Structures
- [[01_Data_Structures/Static Arrays.md|Static Arrays]]

## 🔗 Related Techniques
- [[03_Techniques/Divide and Conquer|Divide and Conquer]]
- [[03_Techniques/Two Pointers|Two Pointers]]

---
[[00_Index/02_Algorithms_MOC|Back to Algorithms Index]]