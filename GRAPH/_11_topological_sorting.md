# Topological Sorting

- Topological sorting can only be performed for **Directed Acyclic Graphs (DAG).**
- There is always a topological sorted order possible for DAG.

- ### DAG (Directed Acyclic Graphs)
    - These graphs are directed and has no cycles.

- Topological sorting is the linear ordering of the vertices of the graph
    - The linear ordering must be such that **for every** directed edge u -> v , vertex u must come before the vertex v in the order

- There are a range of possible answers for the topological sorting.

- Topological sorting is used to solve the dependency related problems.
    - When one thing is dependent on the other and we need to find which thing is needed to be done before the other thing.

- The main logic to implement it using the DFS is for a given node first push all my neighbours then push me.
    - Then when we pop from the stack, we get the right order



