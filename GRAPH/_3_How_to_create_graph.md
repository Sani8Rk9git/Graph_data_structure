# How to create Graph

The Graph can be represented as:

1. ### Adjacency List
    - For any graph, we need to store the information of its edges and vertices.
    - Adjacency list is one of the way to store that information
    - Store the neighbours for all the vertices
    - Two vertices are neighbours if they are directly connected to each other by an edge
    
Code for the adjacency list
```
#undirected unweighted graph
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

```
