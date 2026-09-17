# Detecting cycle in Graph

- Cycle in graph is a closed path that start and end at the same node.
- The cycle contains no repeating edge or vertex.

## Detecting cycle in Undirected Graph using DFS

- We start from a node and we traverse to its neighbours using DFS
- When we reach a node that can be reached from two of its visited neighbours, one which is its parent and the other which is not its parent, then there exist a cycle
- The direct edge between the node and one of its visited neighbours that is not its parent is called **back edge**.
- so we keep track of the parent 
```
for neighbour(v):
    if unvisited:
        then visit
    else:
        if parent:
            ok
        else:
            cycle detected
```

```
    def __cycle_helper_dfs(self,u,parent,visited):
        visited.add(u)
        for v in self.graph[u]:
            if v not in visited:
                if self.__cycle_helper_dfs(v,u,visited):
                    return True
            elif v != parent:
                return True

        return False

    def is_cycle_dfs(self):
        visited = set()
        for u in self.graph:
            if u not in visited:
                if self.__cycle_helper_dfs(u,-1,visited):
                    return True
        return False

```
         
- Time complexity is O(V+E)
