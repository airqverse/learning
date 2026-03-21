# Greedy (Technique)

## 🔍 How to Spot It
- Keywords: "Maximum/Minimum", "Locally optimal choice", "Intervals", "Scheduling".
- Input patterns: Decisions that don't depend on future choices.

## 🛠️ The Pattern (Template)
```python
def greedy_approach(items):
    # 1. Sort items based on a specific criteria (e.g., end time, value/weight)
    items.sort(key=lambda x: x.end_time)
    
    selected_items = []
    current_end_time = -float('inf')
    
    for item in items:
        # 2. Make the locally optimal choice
        if item.start_time >= current_end_time:
            selected_items.append(item)
            current_end_time = item.end_time
            
    return selected_items
```

## 📝 Key Considerations
- **Proof of Correctness**: Greedy algorithms are tricky; ensure the local optimum always leads to a global optimum.
- **Sorting**: Almost always involves sorting the input as a first step.
- **Counter-examples**: Try to find cases where a greedy choice fails before committing to this approach (often dynamic programming is the alternative).

---
[[00_Index/03_Techniques_MOC|Back to Techniques Index]]