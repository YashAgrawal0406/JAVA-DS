# Topics
- [Topics](#Topics)
  - [What is Graph in Data Structure?](What-is-Graph-in-Data-Structure)
    - [Non-linear Data Structure](#Non-linear-Data-Structure)
  - [Graph Terminology](#Graph-Terminology)
    - [Nodes](#Nodes)
    - [Edges](#Edges)
    - [Path](#Path)
    - [Closed Path](#Closed-Path)
    - [Degree of a Node](#Degree-of-a-Node)
   
- [Syllabus](#Syllabus)
  
# Syllabus
  - Introduction to Graphs:
    - Definition of a graph.
    - Basic terminology:
      - Vertices (nodes) and edges.
      - Directed and undirected graphs.
      - Weighted and unweighted graphs.
      - Simple and non-simple graphs.
    - Types of graphs:
      - Complete graph, cycle, path, tree, bipartite graph, etc.
    - Applications of graphs in real-world scenarios.
   
  - Graph Representations:  
    - Adjacency matrix representation.
    - Adjacency list representation.
    - Edge list representation.
    - Comparison of different representations in terms of space and time complexity.

  - Graph Traversals:
    - Depth-first search (DFS):
      - Recursive implementation.
      - Iterative implementation using a stack.
    - Breadth-first search (BFS):
      - Iterative implementation using a queue.
    - Comparison of DFS and BFS.
    - Applications of graph traversal algorithms.
  
  - Graph Algorithms:
    - Shortest path algorithms:
      - Dijkstra's algorithm.
      - Bellman-Ford algorithm.
      - Floyd-Warshall algorithm.
    - Minimum spanning tree (MST):
      - Prim's algorithm.
      - Kruskal's algorithm.
    - Topological sorting.
    - Strongly connected components (SCC):
      - Kosaraju's algorithm.
      - Tarjan's algorithm.

  - Advanced Graph Algorithms:
    - Graph coloring:
      - Greedy coloring algorithm.
    - Maximum flow and minimum cut:
      - Ford-Fulkerson algorithm.
      - Edmonds-Karp algorithm.
    - Travelling Salesman Problem (TSP):
      - Brute-force approach.
      - Dynamic programming approach.
      - Approximation algorithms.
   
  - Graph Theory Concepts:
    - Eulerian and Hamiltonian graphs.
    - Planar graphs and graph coloring theorems.
    - Graph isomorphism.
    - Connectivity and cut vertices/edges.
    - Graph diameter and radius.


## What is Graph in Data Structure?
A Graph in Data Structure is a non-linear data structure that consists of nodes and edges which connects them.

A Graph in Data Structure is a collection of nodes that consists of data and are connected to other nodes of the graph.
<p align="center">
  <img src="https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/e84f96b2-02f2-4239-9f2c-2f08a6b6c6cb" width="400" height="300"> 
</p>

### Non-linear Data Structure:
> In a non-linear data structure, elements are not arranged linearly or sequentially. Because the non-linear data structure does not involve a single level, an user cannot traverse all of its elements at once.
<p align="center">
  <img src="https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/6b753af5-f1d6-4147-abb3-ab30a6bc61c9" width="500" height="350"> 
</p>


## Graph Terminology
### Nodes
- Nodes create complete network in any graph. They are one of the building blocks of a Graph in Data Structure. They connect the edges and create the main network of a graph. They are also called vertices. A node can represent anything such as any location, port, houses, buildings, landmarks, etc.
- They basically are anything that you can represent to be connected to other similar things, and you can establish a relation between the them.
<p align="center">
  <img src="https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/bb2f179a-a53e-498a-a581-12483c943093" width="450" height="300"> 
</p>


## Edges
- Edges basically connects the nodes in a Graph in Data Structure. They represent the relationships between various nodes in a graph. Edges are also called the path in a graph.
- A graph data structure (V,E) consists of:
  - A collection of vertices (V) or nodes.
  - A collection of edges (E) or path
<p align="center">
  <img src="https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/977fe030-171b-433d-abbe-d704b83d156d" width="450" height="300"> 
</p>

## Path
- A path in a graph is a finite or infinite set of edges which joins a set of vertices. It can connect to 2 or more nodes. Also, if the path connects all the nodes of a graph in Data Structure, then it is a connected graph, otherwise it is called a disconnected graph.
- There may or may not be path to each and every node of graph. In case, there is no path to any node, then that node becomes an isolated node.
- In the below graph, the path from 'a' to 'e' is = {a,b,c,d,e}

<p align="center">
  <img src="https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/e7f05de9-b3f0-4d90-92b5-01a497771b75" width="450" height="300"> 
</p>

## Closed Path:
- A path is called as closed path if the initial node is same as terminal(end) node. A path will be closed path if : V0 = Vn, where V0  is the starting node if the graph and Vn is the last node. So, the starting and the terminal nodes are same in a closed graph.
- The above graph have a closed path, where the initial node = {e} is same as the final node = {e}. So, the path becomes = {e,d,f,g,e}.
<p align="center">
  <img src="https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/1f4b5610-5e05-42f6-9316-11ec79a595b2" width="450" height="300"> 
</p>

## Degree of a Node
- Degree of a node is the number of edges connecting the node in the graph. A simple example would be, suppose in facebook, if you have 100 friends then the node that represents you has a degree of 100.
- There are 2 degress `in degree` and `out degree`
- Indegree is number of edges coming to the vertex/Node
- Outdegree is number of edges going out from the vertex/Node

<p align="center">
  <img src="https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/99cc5d9a-2485-45b4-b2d1-3ed3df290a53" width="450" height="300"> 
</p>

```
Output:
Vertex    In    Out
0          1    2
1          2    1
2          2    3
3          2    2
4          2    2
5          2    2
6          2    1
```













