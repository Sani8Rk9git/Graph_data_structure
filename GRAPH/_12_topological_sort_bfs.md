# Topological sorting using bfs

- we first calculate the **indegree** of all the nodes of the graph.
    - indegree is the total number of incoming edges to a node
- This will help us to know the number of dependency for that node.
- Then we push the nodes with 0 indegree in the queue.
- Then run the bfs loop
    - pop from the queue
    - put into answer
    - visit neighbours and reduce their indegree
    - if indegree becomes 0, then push into the queue

```
    def topological_sort_bfs(self):
        indegree = [0]*self.vertices
        for u in self.graph:
            for v in self.graph[u]:
                indegree[v] += 1

        queue = deque()
        visited = set()
        for i in range(self.vertices):
            if indegree[i] == 0:
                queue.append(i)
                visited.add(i)

        ans = []

        while queue:
            u = queue.popleft()
            ans.append(u)
            for v in self.graph[u]:
                indegree[v] -= 1
                if indegree[v] == 0:
                    queue.append(v)
                    visited.add(v)

        for i in ans:
            print(i,end=" ")
```
