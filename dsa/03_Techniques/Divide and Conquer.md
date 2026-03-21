# Divide and Conquer (Technique)

## 🔍 How to Spot It
- Keywords: "Binary Search", "Merge", "Recursive structure".
- Input patterns: Problems that can be broken down into identical subproblems of smaller size.

## 🛠️ The Pattern (Template)
```python
def divide_and_conquer(problem):
    # 1. Base Case
    if is_simple(problem):
        return solve_directly(problem)
    
    # 2. Divide
    subproblems = split(problem)
    
    # 3. Conquer (Recursive calls)
    solutions = [divide_and_conquer(sub) for sub in subproblems]
    
    # 4. Combine
    return merge(solutions)
```

## 📝 Key Considerations
- **Recursion Depth**: Be aware of potential stack overflow for very deep recursions.
- **Merge Complexity**: The efficiency often depends on how quickly you can combine the results (e.g., [[02_Algorithms/Merge Sort|Merge Sort]] is O(n)).
- **Master Theorem**: Use the [[04_Complexity/Master Theorem|Master Theorem]] to calculate the time complexity of these algorithms.

---
[[00_Index/03_Techniques_MOC|Back to Techniques Index]]