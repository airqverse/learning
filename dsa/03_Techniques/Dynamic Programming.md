# Dynamic Programming (Technique)

## 🔍 How to Spot It
- Keywords: "Maximum/Minimum profit", "Number of ways", "Shortest path in DAG", "Optimal substructure".
- Input patterns: Overlapping subproblems, Decision making at each step.

## 🛠️ The Pattern (Template)
### 1. Top-Down (Memoization)
```python
def fib_memo(n, memo={}):
    if n <= 1: return n
    if n not in memo:
        memo[n] = fib_memo(n-1, memo) + fib_memo(n-2, memo)
    return memo[n]
```

### 2. Bottom-Up (Tabulation)
```python
def fib_tab(n):
    if n <= 1: return n
    dp = [0] * (n + 1)
    dp[1] = 1
    for i in range(2, n + 1):
        dp[i] = dp[i-1] + dp[i-2]
    return dp[n]
```

## 📝 Key Considerations
- **Identify the State**: What variables uniquely define a subproblem?
- **Transition Equation**: How do you get from smaller subproblems to the current one?
- **Base Cases**: What are the simplest possible subproblems?
- **Optimization**: Can you reduce space complexity (e.g., from O(n) to O(1) by only keeping track of the last few states)?

---
[[00_Index/03_Techniques_MOC|Back to Techniques Index]]