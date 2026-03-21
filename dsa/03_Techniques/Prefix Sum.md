# Prefix Sum (Technique)

## 🔍 How to Spot It
- Keywords: "Range sum queries", "Subarray sum equals K", "Multiple queries on static array".
- Input patterns: Arrays.

## 🛠️ The Pattern (Template)
```python
# 1. Precomputing the Prefix Sum Array
def get_prefix_sums(arr):
    n = len(arr)
    prefix_sums = [0] * (n + 1)
    for i in range(n):
        prefix_sums[i + 1] = prefix_sums[i] + arr[i]
    return prefix_sums

# 2. Querying a range [L, R] (inclusive)
# sum(arr[L...R]) = prefix_sums[R + 1] - prefix_sums[L]
def query_range(prefix_sums, L, R):
    return prefix_sums[R + 1] - prefix_sums[L]
```

## 📝 Key Considerations
- **Index Offsets**: Using a prefix array of size `n + 1` often simplifies boundary logic (handling `L=0`).
- **Space-Time Tradeoff**: O(n) precomputation time and space, but O(1) query time.
- **Hash Maps**: Often combined with a Hash Map to find subarrays with a specific sum in [[04_Complexity/O(n) - Linear|O(n)]] time.

---
[[00_Index/03_Techniques_MOC|Back to Techniques Index]]