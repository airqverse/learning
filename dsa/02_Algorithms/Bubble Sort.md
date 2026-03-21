# Bubble Sort

## 🎯 Goal
> Sort a list by repeatedly stepping through it, comparing adjacent elements and swapping them if they are in the wrong order.

## 🧠 Logic & Steps
1. Start at the beginning of the list.
2. Compare the current element with the next element.
3. If the current element is greater than the next element, swap them.
4. Move to the next pair and repeat until the end of the list (this completes one pass, and the largest element "bubbles" to its correct position).
5. Repeat the entire process for the remaining unsorted portion of the list until no more swaps are needed.

## 🐍 Python Implementation
```python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        swapped = False
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
                swapped = True
        if not swapped:
            break
    return arr
```

## 📊 Performance
- **Time Complexity**: [[04_Complexity/O(n^2) - Quadratic|O(n^2)]]
- **Space Complexity**: [[04_Complexity/O(1) - Constant|O(1)]]

## 🔗 Related Data Structures
- [[01_Data_Structures/Static Arrays|Static Arrays]]

---
[[00_Index/02_Algorithms_MOC|Back to Algorithms Index]]