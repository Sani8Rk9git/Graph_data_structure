# DFS traversal on disconnected graph

- If the graph given to us is disconnected, we can have several connected components in it.
- To apply DFS traversal on it, we need to pick multiple source points

```
    def dfs_dis(self):
        visited = set()
        count = 0
        for u in self.graph:
            if u not in visited:
                count +=1
                self.__dfs_helper(u,visited)
        print()
        print(count)

```
