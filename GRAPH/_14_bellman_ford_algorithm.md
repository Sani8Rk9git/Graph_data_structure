# Bellman-Ford Algorithm

- It is used to calculate the shortest path from source to all the vertices for a weighted graph with negative weights.

- Bellman-Ford algorithm is Dynamic Programming based algorithm.

- we need to perform the edge relaxation for each edge in the graph.

- we run a loop from 0 to V-1
    - inside run a loop for each vertex of the graph
        - for each vertex we visit its edges

```
class Weighted:
    def __init__(self, vertices):
        self.vertices = vertices
        self.graph = {}

    def add_e(self, u, v, wt):
        if u not in self.graph:
            self.graph[u] = []
        if v not in self.graph:
            self.graph[v] = []

        self.graph[u].append((v,wt))

    def print_g(self):
        for u in self.graph:
            print(u,":",self.graph[u])

    def bell(self, source):
        distance = []
        for i in range(self.vertices):
            if i == source:
                distance.append(0)
            else:
                distance.append(float("inf"))

        for i in range(self.vertices-1):
            new_distance = distance.copy()
            for u in self.graph:
                for v in self.graph[u]:
                    if new_distance[v[0]] > distance[u] + v[1]:
                        new_distance[v[0]] = distance[u] + v[1]
            distance = new_distance

        for i in distance:
            print(i,end=" ")

```

- Between a source node to any node v, there are at most V-1 edges between it, where V is the total number of vertices.

- In the bellman-ford algorithm
    - in the 1 iteration, we consider paths that can be reached by 1 edge
    - in the 2 iteration, all paths that are 2 edges 
    - in the V-1 iteration, V-1 edge

- we are considering the longest path possible

- Bellman ford algorithm does not work for negative weight cycles
    - the total sum of the weights of the cycle is negative

- Time complexity is 
O(V*E)

- In the Bellman-Ford algorithm, the computer does not know the shape of the graph. It just loops through a random checklist of edges over and over again.

- Now since there is V-1 at most edges between two nodes of a graph so we loop V-1 times.

- Bellman-Ford instead thinks: "How many edges am I allowed to use?"

