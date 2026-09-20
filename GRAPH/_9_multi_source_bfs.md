# Multi-source Breadth First Search

- If the graph is fully connected, then we can use a single source and apply BFS traversal to traverse all of the nodes of the graph

- If there are some disconnected components in the graph, then we can take each unvisited node as the source and then apply the BFS traversal for it


### Multi-source BFS
- If we want to traverse the graph from more than one source simultaneously using BFS, we can put all the source nodes together in the queue of the BFS and then traverse the graph by applying the BFS



