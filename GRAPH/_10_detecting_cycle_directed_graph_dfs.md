# Detecting cycle in Directed Graph using DFS

- In DFS, we use recursion to visit the nodes by going to a depth and then backtrack to visit other branch.
- Cycle occurs in the directed graph if a node is already visited and it occurs in the recursive path 

```
class DirectedGraph(Graph):
    def __init__(self, vertices):
        super().__init__(vertices)

    def add_edge(self, u, v):
        if u not in self.graph:
            self.graph[u] = []
        
        self.graph[u].append(v)

    def print_graph(self):
        for vertex in self.graph:
            print(vertex,":",self.graph[vertex])

    
    def __cycle_dfs_helper(self,u,visited,rec_path):
        visited.add(u)
        rec_path.append(u)
        for v in self.graph[u]:
            if v not in visited:
                if self.__cycle_dfs_helper(v,visited,rec_path):
                    return True
            elif v in rec_path:
                return True
                
        rec_path.pop()
        return False
    
    
    def cycle_dfs(self):
        visited = set()
        rec_path = []
        for u in self.graph:
            if u not in visited:
                if self.__cycle_dfs_helper(u,visited,rec_path):
                    return True

        return False

```
