# Backtracking (Technique)

## 🔍 How to Spot It
- Keywords: "All possible permutations/combinations", "Find all paths", "Solve puzzle (N-Queens, Sudoku)".
- Input patterns: Trees, Graphs, Sets.

## 🛠️ The Pattern (Template)
```python
def backtrack(candidate, options):
    if is_solution(candidate):
        output.append(list(candidate))
        return

    for next_option in options:
        if is_valid(next_option):
            # 1. Make a choice
            candidate.append(next_option)
            
            # 2. Explore
            backtrack(candidate, remaining_options)
            
            # 3. Undo the choice (Backtrack)
            candidate.pop()
```

## 📝 Key Considerations
- **Pruning**: Skip paths that cannot lead to a valid solution to improve performance.
- **State Management**: Ensure you correctly reset the state after returning from a recursive call.
- **Base Case**: Clearly define when a candidate is a complete and valid solution.

---
[[00_Index/03_Techniques_MOC|Back to Techniques Index]]