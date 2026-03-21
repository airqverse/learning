# BFS (Breadth-First Search)

## 🎯 Goal
> Explore or search through a tree or graph by visiting all neighbor nodes at the present depth level before moving on to nodes at the next depth level.

## 🧠 Logic & Steps
1. Create a queue and enqueue the starting node.
2. Mark the starting node as visited.
3. While the queue is not empty:
    a. Dequeue a node from the front.
    b. Visit all unvisited neighbors of the dequeued node.
    c. Mark each neighbor as visited and enqueue them.
4. Repeat until the queue is empty or the target is found.

## 🐍 Python Implementation
```python
from collections import deque

def bfs(graph, start_node):
    visited = {start_node}
    queue = deque([start_node])
    
    result = []
    while queue:
        node = queue.popleft()
        result.append(node)
        
        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)
    return result
```

## 📊 Performance
- **Time Complexity**: [[04_Complexity/O(n) - Linear|O(V + E)]] (Where V is vertices and E is edges)
- **Space Complexity**: [[04_Complexity/O(n) - Linear|O(V)]]

## 🔗 Related Data Structures
- [[01_Data_Structures/Graphs|Graphs]]
- [[01_Data_Structures/Queues|Queues]]
- [[01_Data_Structures/Trees|Trees]]

---
[[00_Index/02_Algorithms_MOC|Back to Algorithms Index]]