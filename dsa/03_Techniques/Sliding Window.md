# Sliding Window (Technique)

## 🔍 How to Spot It
- Keywords: "Subarray", "Substring", "Longest/Shortest with condition K", "Max/Min sum of size K".
- Input patterns: Arrays, Strings.

## 🛠️ The Pattern (Template)
### 1. Fixed Window Size
```python
def fixed_sliding_window(arr, k):
    current_sum = sum(arr[:k])
    max_sum = current_sum
    
    for i in range(len(arr) - k):
        current_sum = current_sum - arr[i] + arr[i + k]
        max_sum = max(max_sum, current_sum)
    
    return max_sum
```

### 2. Variable Window Size (Dynamic)
```python
def variable_sliding_window(arr, target):
    left = 0
    current_sum = 0
    min_length = float('inf')
    
    for right in range(len(arr)):
        current_sum += arr[right]
        
        while current_sum >= target:
            min_length = min(min_length, right - left + 1)
            current_sum -= arr[left]
            left += 1
            
    return min_length if min_length != float('inf') else 0
```

## 📝 Key Considerations
- **Boundary Conditions**: Ensure the `right` pointer iterates through the whole array and the `left` pointer correctly shrinks the window.
- **Complexity**: Usually results in [[04_Complexity/O(n) - Linear|O(n)]] time complexity as each element is visited at most twice.

---
[[00_Index/03_Techniques_MOC|Back to Techniques Index]]