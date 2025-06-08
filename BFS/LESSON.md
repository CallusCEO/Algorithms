### Breadth-First Search (BFS)

Breadth-First Search (BFS) is a widely used algorithm for traversing or searching tree or graph data structures. It begins at a starting node (often the "root" in trees) and explores all neighboring nodes at the current depth before moving deeper. This level-by-level exploration makes BFS ideal for finding the shortest path in unweighted graphs.

#### How BFS Works

1. **Initialization**: Use a queue (first-in, first-out structure) to store nodes. Enqueue the starting node and mark it as visited.
2. **Exploration**: While the queue isn’t empty, dequeue a node and process it (e.g., examine or output it).
3. **Enqueue Neighbors**: Add all unvisited neighbors of the current node to the queue and mark them as visited.
4. **Repeat**: Continue until the queue is empty or a target node is found.

#### Example in Python

Here’s BFS for a graph as an adjacency list:

```python
from collections import deque

def bfs(graph, start):
    visited = set()
    queue = deque([start])
    visited.add(start)
    while queue:
        node = queue.popleft()
        print(node, end=' ')
        for neighbor in graph[node]:
            if neighbor not in visited:
                queue.append(neighbor)
                visited.add(neighbor)

graph = {
    'A': ['B', 'C'],
    'B': ['D', 'E'],
    'C': ['F'],
    'D': [],
    'E': ['F'],
    'F': []
}
bfs(graph, 'A')  # Output: A B C D E F
```

#### Key Characteristics

-   **Queue**: Ensures nodes are processed in order of discovery.
-   **Visited Set**: Avoids cycles by tracking processed nodes.
-   **Time Complexity**: O(V + E), where V is the number of vertices and E is edges, as each is visited once.

#### Applications

-   Shortest path in unweighted graphs.
-   Level-order traversal in trees.
-   Network connectivity testing.

BFS is straightforward, efficient, and foundational for many graph problems.
