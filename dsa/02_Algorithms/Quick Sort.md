# Quick Sort

## 🎯 Goal
> Sort a list by selecting a 'pivot' element and partitioning the other elements into two sub-arrays according to whether they are less than or greater than the pivot.

## 🧠 Logic & Steps
1. **Pick**: Choose an element as the pivot (e.g., the last element).
2. **Partition**: Rearrange the array so that elements less than the pivot are on the left, and elements greater than the pivot are on the right.
3. **Recurse**: Recursively apply the same logic to the left and right sub-arrays.
4. **Base Case**: If the array has 0 or 1 elements, it is already sorted.

## 🐍 Python Implementation
```python
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    
    return quick_sort(left) + middle + quick_sort(right)
```

## 📊 Performance
- **Time Complexity**: 
    - Average: [[04_Complexity/O(n log n) - Linearithmic|O(n log n)]]
    - Worst: [[04_Complexity/O(n^2) - Quadratic|O(n^2)]]
- **Space Complexity**: [[04_Complexity/O(log n) - Logarithmic|O(log n)]] (Recursive stack)

## 🔗 Related Data Structures
- [[01_Data_Structures/Static Arrays|Static Arrays]]

## 🔗 Related Techniques
- [[03_Techniques/Divide and Conquer|Divide and Conquer]]

---
[[00_Index/02_Algorithms_MOC|Back to Algorithms Index]]