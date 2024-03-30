# Topics
- [Topics](#Topics)
  - Bridge in Graph
  - Articulation Point in Graph
  - [Explanation](#Explanation)
  - [Code](#Code)
  - [References](#References)
 

## Bridge in Graphs
> uses DFS algorithm
> Bridge is an edge whose deletion increases the graphs number of connected componenets

> A bridge is an edge from vertex U to vertex V such that removing the edge increases the number of connected components in the graph.

> To find bridges in a graph we can use the same approach used to find articulation points. But, since we are removing an edge instead of a vertex to find whether an edge is a bridge or not we use the condition, low[child_node] > discovery_time[current_node]
