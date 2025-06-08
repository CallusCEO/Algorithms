### What is DFS?

Depth-First Search (DFS) is a fundamental algorithm used to traverse or search through tree or graph data structures. Unlike Breadth-First Search (BFS), which explores nodes level by level, DFS dives as deeply as possible down each branch before backtracking. This "deep-first" strategy makes it ideal for problems requiring exhaustive exploration of paths, such as finding a single solution in a maze or performing topological sorting.

---

### How DFS Works

Here’s the step-by-step process:

1. **Start at a Node**: Begin at a chosen root node and mark it as visited.
2. **Explore Deeply**: Use recursion or a stack to visit an unvisited neighbor of the current node, then repeat this process for that neighbor.
3. **Backtrack**: When a node has no unvisited neighbors, backtrack to the previous node and explore its other unvisited neighbors.
4. **Finish**: Continue until all reachable nodes are visited or a target is found.

---

### Example in Python

Here’s a simple implementation of DFS for a graph represented as an adjacency list:

```python
def dfs(graph, node, visited=None):
    if visited is None:
        visited = set()
    if node not in visited:
        print(node, end=' ')
        visited.add(node)
        for neighbor in graph[node]:
            dfs(graph, neighbor, visited)

# Example graph
graph = {
    'A': ['B', 'C'],
    'B': ['D', 'E'],
    'C': ['F'],
    'D': [],
    'E': ['F'],
    'F': []
}
dfs(graph, 'A')  # Output: A B D E F C
```

This code prints nodes in the order they’re visited, starting from 'A'.

---

### Key Characteristics

-   **Stack-Based**: DFS uses a stack—either explicitly or via the call stack in recursion—to track nodes.
-   **Visited Tracking**: A set prevents revisiting nodes, avoiding infinite loops in cyclic graphs.
-   **Time Complexity**: O(V + E), where V is the number of vertices and E is the number of edges, as each is processed once.

---

### Applications

DFS shines in various scenarios:

-   **Topological Sorting**: Ordering nodes in directed acyclic graphs (DAGs).
-   **Cycle Detection**: Identifying loops in graphs.
-   **Maze Solving**: Finding a path through puzzles with a single solution.
