# 2 Colouring

2 colouring is the standard way to check whether a graph is bipartite.

## Core Idea

Assign each node one of two colours such that every edge connects nodes with different colours.

If you ever find an edge connecting two nodes with the same colour, the graph is not bipartite.

## Recognition Signals

- Graph can be split into two groups
- Adjacent nodes must be different
- Need to detect an odd cycle
- "Can we divide into two teams?"

## BFS Template

```python
from collections import deque

def is_bipartite(graph):
    colour = {}

    for start in graph:
        if start in colour:
            continue

        queue = deque([start])
        colour[start] = 0

        while queue:
            node = queue.popleft()

            for nei in graph[node]:
                if nei not in colour:
                    colour[nei] = 1 - colour[node]
                    queue.append(nei)
                elif colour[nei] == colour[node]:
                    return False

    return True
```

## DFS Template

```python
def is_bipartite(graph):
    colour = {}

    def dfs(node, c):
        if node in colour:
            return colour[node] == c

        colour[node] = c

        for nei in graph[node]:
            if not dfs(nei, 1 - c):
                return False

        return True

    for start in graph:
        if start not in colour and not dfs(start, 0):
            return False

    return True
```

## Why It Works

- Nodes connected by an edge must have opposite colours
- BFS and DFS both propagate this constraint through the component
- An odd cycle forces a contradiction, so 2 colouring fails exactly when the graph is not bipartite

## Important Detail

You must start a new BFS or DFS from every unvisited node because the graph may be disconnected.

## Complexity

- Time: `O(V + E)`
- Space: `O(V)`

## Common Pitfalls

- Only starting from one node in a disconnected graph
- Forgetting to store colours separately from visited state
- Assuming every graph is connected
- Using recursion on very deep graphs without considering stack depth

## Related Problems

- Is Graph Bipartite?
- Possible Bipartition
- Divide players into two groups with conflict edges
