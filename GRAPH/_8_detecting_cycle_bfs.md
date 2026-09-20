# Detecting cycle in the Graph using BFS

- We need to find the back edge
- It means for a given node, we have its neighbours
    - If the neighbour is visited but not the parent of the node, it indicates the presence of a cycle

- parent is a conceptual concept, it is the node from which we arrived at the current node.

```
    def cycle_bfs(self, start):
        visited = set()
        queue = deque()
        queue.append((start, -1))
        visited.add(start)
        while queue:
            u, parent = queue.popleft()
            for v in self.graph[u]:
                if v not in visited:
                    queue.append((v,u))
                    visited.add(v)
                elif v != parent:
                    return True
        return False

```
- Time complexity is O(V+E)

- we must have a loop so that we can visit all the components of the graph as the graph can be disconnected.

