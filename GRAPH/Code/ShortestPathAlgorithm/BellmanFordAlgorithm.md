# Topics

- [Topics](#Topics)
  - [Theory](#Theory)
  - [Code](#Code)
  - [Explanation](#Explanation)
  - [Advantages and Disadvantages](#Advantages-and-Disadvantages)
  - [References](#References)


## Theory
Overview
> The Bellman-Ford algorithm is an example of Dynamic Programming. It starts with a starting vertex and calculates the distances of other vertices which can be reached by one edge. It then continues to find a path with two edges and so on. The Bellman-Ford algorithm follows the bottom-up approach.

What is Bellman-Ford Algorithm?
> The Bellman-Ford algorithm computes the shortest path from a source vertex to all others in a graph, accommodating both weighted and unweighted edges. While it's generally slower than Dijkstra’s method, Bellman-Ford excels in graphs with negative edge weights and detects negative cycles, a crucial feature. This capability prevents infinite loops where path costs decrease infinitely by traversing negative cycles. Utilizing dynamic programming, Bellman-Ford employs a bottom-up approach, iteratively refining distance estimates via the "Principle of Relaxation." Starting with immediate neighbors, it progressively evaluates longer paths, converging to the optimal solution. However, if negative weight cycles exist, they can distort path distances, necessitating caution during analysis. Thus, Bellman-Ford offers a robust, albeit slower, alternative for diverse graph scenarios.

Example of Bellman Ford Algorithm
- Suppose that we have a graph consisting of 5 vertices having edges between them as shown in the picture below. Now, we want to find shortest distance to each vertex vi 0<i<6 starting from the vertex 1.

<p align="center">
  <img src="https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/4b686874-c191-4915-a515-86cf636c546f" width="450" height="300"> 
</p>

- After performing bellman ford algorithm on the above graph the output array would look like - Shortest_Distance = [0, 3, 5, 2, 5]
- Where each index 'í' of array denotes the shortest distance of the ith vertex from 1st vertex, 1<=i<=5.

## Code
```Java
//Bellman Ford Algorithm

import java.util.*;

//Does not work for negative edge cycle
public class Main {
    public static class Edge {
        int src;
        int des;
        int weight;

        public Edge(int src, int des, int weight) {
            this.src = src;
            this.des = des;
            this.weight = weight;
        }
    }

    public static void printGraph(ArrayList<Edge> graph) {
        for (int i = 0; i < graph.size(); i++) {
            Edge e = graph.get(i);
            System.out.println(e.src + "->" + e.des);
        }
    }

    public static void createGraph(ArrayList<Edge> graph[]) {
        for (int i = 0; i < graph.length; i++) {
            graph[i] = new ArrayList<Edge>();
        }

        graph[0].add(new Edge(0, 1, 2));
        graph[0].add(new Edge(0, 2, 4));

        graph[1].add(new Edge(1, 2, -4));

        graph[2].add(new Edge(2, 3, 2));

        graph[3].add(new Edge(3, 4, 4));

        graph[4].add(new Edge(4, 1, -1));
        //make weight -10 for -1 to get negative weight cycle
        //graph[4].add(new Edge(4, 1, -10));
    }


    public static void bellmanFord(ArrayList<Edge> graph[],int src,int V)
    {
        //O(V*E)
        int[] dist = new int[V];
        for (int i = 0; i < V; i++) {
            if(i != src)
            {
                dist[i] = Integer.MAX_VALUE;
            }
        }

        //We traverse from 0 to V, V times
        for (int k = 0; k < V-1; k++) { // V-1 times traversal for each node // just like bubble sort
            for (int i = 0; i < V; i++) { // traversal of each node
                for (int j = 0; j < graph[i].size(); j++) { // for each edge from curr node
                    Edge e = graph[i].get(j);
                    int u = e.src;
                    int v = e.des;

                    if(dist[u] != Integer.MAX_VALUE && dist[u] + e.weight < dist[v])
                    {
                        dist[v] = dist[u] + e.weight;
                    }

                }
            }
        }

        for (int i = 0; i < V; i++) {
            for (int j = 0; j < graph[i].size(); j++) {
                Edge e = graph[i].get(j);
                int u = e.src;
                int v = e.des;

                if(dist[u] != Integer.MAX_VALUE && dist[u] + e.weight < dist[v])
                {
                    //if this is true then we have negative weight cycle
                    System.out.println("Negative Weight Cycle");
                }

            }
        }

        for (int i = 0; i < dist.length; i++) {
            System.out.print(dist[i] + " ");
        }
    }
    public static void main(String[] args) {
        int V = 5;
        ArrayList<Edge> graph[] = new ArrayList[V];
        createGraph(graph);
        /*
                     -1
                 1--------4
                /|        |
             2 / |        |
              /  |        |
             0   |-4      |4
              \  |        |
             4 \ |        |
                \|        |
                 2--------3
                      2
         */
        bellmanFord(graph,0,V);
    }
}
```

## Advantages and Disadvantages:
- Advantages
  - The Bellman-Ford Algorithm can handle negative edge weights.
  - It can be used to detect negative cycles in a graph.
  - It is simple to understand and easy to implement.
- Disadvantages
  - The algorithm has a time complexity of O(V*E), where V is the number of vertices and E is the number of edges in the graph. This makes it less efficient than other shortest path algorithms such as Dijkstra’s Algorithm, which has a time complexity of O(E log V) for a graph with non-negative edge weights.
  - The algorithm may not terminate if the graph contains a negative cycle. In this case, the algorithm will keep updating the estimates of the shortest path indefinitely.


## References
- https://www.baeldung.com/cs/bellman-ford
- https://cyberw1ng.medium.com/a-beginners-guide-to-the-bellman-ford-algorithm-2023-e51b1a6110bb
- https://www.scaler.com/topics/data-structures/bellman-ford-algorithm/

