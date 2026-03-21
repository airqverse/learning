# Graphs

## 📋 Definition
> A non-linear data structure consisting of a finite set of vertices (or nodes) and a set of edges that connect a pair of nodes. Graphs can be directed, undirected, weighted, or unweighted.

## ⚙️ Operations & Complexity
| Operation        | Adjacency List                            | Adjacency Matrix                             |
| ---------------- | ----------------------------------------- | -------------------------------------------- |
| Add Vertex       | [[04_Complexity/O(1) - Constant\|O(1)]]   | [[04_Complexity/O(n^2) - Quadratic\|O(V^2)]] |
| Add Edge         | [[04_Complexity/O(1) - Constant\|O(1)]]   | [[04_Complexity/O(1) - Constant\|O(1)]]      |
| Search (BFS/DFS) | [[04_Complexity/O(n) - Linear\|O(V + E)]] | [[04_Complexity/O(n^2) - Quadratic\|O(V^2)]] |

## 🐍 Python Implementation
```python
# Adjacency List Representation
graph = {
    'A': ['B', 'C'],
    'B': ['D'],
    'C': ['E'],
    'D': [],
    'E': []
}

# Simple DFS
def dfs(graph, node, visited=None):
    if visited is None:
        visited = set()
    if node not in visited:
        print(node, end=" ")
        visited.add(node)
        for neighbor in graph[node]:
            dfs(graph, neighbor, visited)

dfs(graph, 'A') # A B D C E
```

## 💡 Use Cases & Notes
- **Use when**: Modeling networks (social media, internet), pathfinding (GPS), or dependency resolution (package managers).
- **Storage**: Adjacency list is better for sparse graphs; Adjacency matrix is better for dense graphs.

---
[[00_Index/01_Data_Structures_MOC|Back to Data Structures Index]]