# Two Pointers (Technique)

## 🔍 How to Spot It
- Keywords: "Sorted array", "Pair with target sum", "Reverse", "Palindrome".
- Input patterns: Linear data structures (arrays, strings, linked lists).

## 🛠️ The Pattern (Template)
### 1. Opposite Ends (e.g., Sorted Sum)
```python
def two_pointers_opposite(arr, target):
    left = 0
    right = len(arr) - 1
    
    while left < right:
        current_sum = arr[left] + arr[right]
        if current_sum == target:
            return [left, right]
        elif current_sum < target:
            left += 1
        else:
            right -= 1
    return []
```

### 2. Slow & Fast (e.g., Cycle Detection)
```python
def slow_fast_pointers(head):
    slow = head
    fast = head
    
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            return True # Cycle detected
    return False
```

## 📝 Key Considerations
- **Sorting**: Often requires the input to be sorted to work effectively (for opposite ends).
- **Termination**: Be careful with `while left < right` vs `while left <= right`.
- **Space Efficiency**: Usually achieves [[04_Complexity/O(1) - Constant|O(1)]] space complexity.

---
[[00_Index/03_Techniques_MOC|Back to Techniques Index]]