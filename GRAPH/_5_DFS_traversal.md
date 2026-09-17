# Depth First Traversal on Graphs

- The approach of DFS traversal is:
> Keep going to the first unvisited neighbours
- we go deep in the branch and when there remains no unvisited nodes, we backtrack to the previous nodes
- DFS can be implemented using recursion or a stack
- Time complexity is O(V+E)
    - vertices + edges

- When our graph is disconnected, we need to choose multiple source points and then traverse the graph using these source points

```
#undirected unweighted graph
#adjacency list
class Graph:
    def __init__(self, vertices):
        self.vertices = vertices
        self.graph = {}

    def add_edge(self, u, v):
        if u not in self.graph:
            self.graph[u] = []
        if v not in self.graph:
            self.graph[v] = []
        self.graph[u].append(v)
        self.graph[v].append(u)

    def print_graph(self):
        for vertex in self.graph:
            print(vertex,":",self.graph[vertex])

    def bfs(self, start):
        visited = set()
        queue = deque()
        queue.append(start)
        visited.add(start)
        while queue:
            u = queue.popleft()
            print(u, end=" ")
            for v in self.graph[u]:
                if v not in visited:
                    queue.append(v)
                    visited.add(v)
        print()

    def __dfs_helper(self,u,visited):
        print(u, end=" ")
        visited.add(u)

        for v in self.graph[u]:
            if v not in visited:
                self.__dfs_helper(v,visited)

    def dfs(self,start):
        visited = set()
        self.__dfs_helper(start,visited)

```