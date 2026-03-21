# Merge Sort

## 🎯 Goal
> Sort a list by recursively dividing it into halves, sorting each half, and then merging the sorted halves back together.

## 🧠 Logic & Steps
1. **Divide**: If the list has more than one element, split it into two halves.
2. **Conquer**: Recursively apply merge sort to both halves.
3. **Combine**: Merge the two sorted halves into a single sorted list.
    a. Compare the smallest elements of each half.
    b. Take the smaller element and move it into the result list.
    c. Repeat until one half is empty, then append the remaining elements of the other half.

## 🐍 Python Implementation
```python
def merge_sort(arr):
    if len(arr) <= 1:
        return arr
    
    mid = len(arr) // 2
    left_half = merge_sort(arr[:mid])
    right_half = merge_sort(arr[mid:])
    
    return merge(left_half, right_half)

def merge(left, right):
    sorted_arr = []
    i = j = 0
    
    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            sorted_arr.append(left[i])
            i += 1
        else:
            sorted_arr.append(right[j])
            j += 1
            
    sorted_arr.extend(left[i:])
    sorted_arr.extend(right[j:])
    return sorted_arr
```

## 📊 Performance
- **Time Complexity**: [[04_Complexity/O(n log n) - Linearithmic|O(n log n)]]
- **Space Complexity**: [[04_Complexity/O(n) - Linear|O(n)]]

## 🔗 Related Data Structures
- [[01_Data_Structures/Static Arrays|Static Arrays]]

## 🔗 Related Techniques
- [[03_Techniques/Divide and Conquer|Divide and Conquer]]

---
[[00_Index/02_Algorithms_MOC|Back to Algorithms Index]]