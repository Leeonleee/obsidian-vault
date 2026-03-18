# Trees and Graph Traversal

DFS explores depth-first. BFS explores level-by-level. Pick based on the information the problem needs.

## Recognition Signals

- Tree traversal
- Connected components
- Shortest path in an unweighted graph
- Level-order processing

## DFS Recursive Template

```python
def dfs(node):
    if not node:
        return

    # preorder work
    dfs(node.left)
    # inorder work
    dfs(node.right)
    # postorder work
```

## Graph DFS Template

```python
visited = set()

def dfs(node):
    if node in visited:
        return
    visited.add(node)

    for nei in graph[node]:
        dfs(nei)
```

## BFS Template

```python
from collections import deque

queue = deque([start])
visited = {start}

while queue:
    node = queue.popleft()

    for nei in graph[node]:
        if nei not in visited:
            visited.add(nei)
            queue.append(nei)
```

## Heuristics

- Use DFS for path existence, subtree properties, backtracking-style traversal
- Use BFS for minimum number of edges or level-order answers
- On trees, pass state down or return state up depending on the question

## Pitfalls

- Forgetting `visited` on graphs
- Using recursion too deep on large inputs
- Confusing tree problems with graph problems that can revisit nodes

## Related Problems

- Maximum Depth of Binary Tree
- Binary Tree Level Order Traversal
- Number of Islands
- Clone Graph
- Course Schedule
