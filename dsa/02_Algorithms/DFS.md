# DFS (Depth-First Search)

## 🎯 Goal
> Explore or search through a tree or graph by starting at the root (or an arbitrary node) and exploring as far as possible along each branch before backtracking.

## 🧠 Logic & Steps
1. Start at the root or chosen node.
2. Mark the current node as visited.
3. For each unvisited neighbor:
    a. Recursively call DFS on that neighbor.
4. Backtrack when no more unvisited neighbors exist.

## 🐍 Python Implementation
```python
def dfs(graph, node, visited=None):
    if visited is None:
        visited = set()
    
    visited.add(node)
    result = [node]
    
    for neighbor in graph[node]:
        if neighbor not in visited:
            result.extend(dfs(graph, neighbor, visited))
            
    return result
```

## 📊 Performance
- **Time Complexity**: [[04_Complexity/O(n) - Linear|O(V + E)]] (Where V is vertices and E is edges)
- **Space Complexity**: [[04_Complexity/O(n) - Linear|O(V)]] (Recursive stack depth)

## 🔗 Related Data Structures
- [[01_Data_Structures/Graphs|Graphs]]
- [[01_Data_Structures/Stacks|Stacks]] (Implicitly via recursion or explicitly)
- [[01_Data_Structures/Trees|Trees]]

---
[[00_Index/02_Algorithms_MOC|Back to Algorithms Index]]