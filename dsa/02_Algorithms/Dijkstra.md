# Dijkstra's Algorithm

## 🎯 Goal
> Find the shortest paths from a single source node to all other nodes in a weighted graph with non-negative edge weights.

## 🧠 Logic & Steps
1. Initialize distances to all nodes as infinity, except the start node which is 0.
2. Maintain a set of unvisited nodes and a priority queue (min-heap) of nodes to explore.
3. While the priority queue is not empty:
    a. Extract the node with the minimum distance.
    b. For each neighbor of the current node:
        i. Calculate the distance to the neighbor through the current node.
        ii. If this new distance is shorter than the previously known distance, update the distance and add the neighbor to the priority queue.
4. Once all nodes have been visited or the queue is empty, the shortest distances are found.

## 🐍 Python Implementation
```python
import heapq

def dijkstra(graph, start):
    # graph is expected to be a dict of dicts: {node: {neighbor: weight}}
    distances = {node: float('infinity') for node in graph}
    distances[start] = 0
    priority_queue = [(0, start)]
    
    while priority_queue:
        current_distance, current_node = heapq.heappop(priority_queue)
        
        if current_distance > distances[current_node]:
            continue
            
        for neighbor, weight in graph[current_node].items():
            distance = current_distance + weight
            
            if distance < distances[neighbor]:
                distances[neighbor] = distance
                heapq.heappush(priority_queue, (distance, neighbor))
                
    return distances
```

## 📊 Performance
- **Time Complexity**: [[04_Complexity/O(n log n) - Linearithmic|O((V + E) log V)]]
- **Space Complexity**: [[04_Complexity/O(n) - Linear|O(V)]]

## 🔗 Related Data Structures
- [[01_Data_Structures/Graphs|Graphs]]
- [[01_Data_Structures/Heaps|Heaps]] (Priority Queue)

---
[[00_Index/02_Algorithms_MOC|Back to Algorithms Index]]