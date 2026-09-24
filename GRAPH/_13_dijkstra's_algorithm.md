# Dijkstra's Algorithm

- It is used to find the shortest path from the source vertex to all the vertices of the weighted graph.

- Dijkstra's algorithm is a greedy algorithm 
    - we choose local optimal solutions that eventually lead to the global optimal value

- This algorithm work only for the positive weighted graph.

- The most important step of the Dijkstra's algorithm is **Edge Relaxation.**
    - Edge relaxation means comparing the direct and the indirect path of a node.
    - we first store direct/current path from the source to all the nodes
    - now we do edge relaxation
    - when we take a distance from the a node u to node v
    - distance[u] = distance from source to node u
    - distance[v] = distance from source to node v
    - ```if(dist[v] > dist[u]+wt(u,v))```
        - then we update the dist[v]
    
- we ask a question at each step "Is it cheaper to go to v from u"
- We use BFS to perform dijkstra's algorithm
    - we use a priority queue
    - arranges the elements according to the priority
    - Max heap and min heap is used by default to implement the priority queue
    - Highest priority element will be first (element with large value)

```
class WeightedDirected(Graph):
    def __init__(self, vertices):
        super().__init__(vertices)
        self.weights = []

    def add_edge_weight(self, u, v, weight):
        if u not in self.graph:
            self.graph[u] = []
        if v not in self.graph:
            self.graph[v] = []

        self.graph[u].append((v,weight))
        self.weights.append(weight)

    def print_graph(self):
        for u in self.graph:
            print(u,":",self.graph[u])

    def dijkstra(self,source):
        max_weight = max(self.weights)
        distance = []
        queue = PriorityQueue()
        for i in range(self.vertices):
            if i == source:
                distance.append(0)
            else:
                distance.append(max_weight+100)

        queue.insert(0,source)
        while queue:
            u = queue.delete()[1]
            for v in self.graph[u]:
                if distance[v[0]] > distance[u] + v[1]:
                    distance[v[0]] = distance[u] + v[1]
                    queue.insert(distance[v[0]],v[0])
        print(end="  ")
        for idx,dist in enumerate(distance):
            print(idx,end=" ")
        print()
        print(source,end=" ")
        for dist in distance:
            print(dist,end=" ")

```

- Time complexity is O(V+E)*log(V)
    - log(V) is the operation time of the priority queue

```
class PriorityQueue:
    def __init__(self):
        self.queue = []

    def insert(self, priority, item):
        self.queue.append((priority,item))

    def delete(self):
        min = 0
        for i in range(len(self.queue)):
            if self.queue[i][0] < self.queue[min][0]:
                min = i
        item = self.queue[min]
        del self.queue[min]
        return item

    def show_queue(self):
        for i in self.queue:
            print(i)

    def __len__(self):
        return len(self.queue)

```

