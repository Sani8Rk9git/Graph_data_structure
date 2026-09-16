# Traversal on Graphs

Travelling to each node of the graph can be done in the following ways:

1. ## Breadth First Search(BFS)
    - The fundamental rule of BFS is 
    > when we are at a node, then first travel to all the immediate neighbours of that node before moving to any other node.
    - There is no fixed point to start traversal in graph, so we can choose any node.
    - We need to keep tract of the vertices that have been visited so that we can avoid cycles in the graph.
    - There is no heirarchy in the graph so tracking the visited vertices is required.

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

```

- The worst case time complexity of the bfs algorithm is O(V+E)
    - vertices + edges
- when we push the element in the queue, then we need to mark the nodes as visited


    