# Topics
- [Topics](#Topics)
  - [Theory](#Theory)
  - [Explanation](#Explanation)
  - [Code](#Code)
  - [References](#References)
 

## Theory
**How Prim's algorithm works?**
- Prim's algorithm builds a minimum spanning tree (MST) by adding vertices from a starting vertex. It follows these steps:
  - Initialize MST: Begins with a single vertex from the graph.
  - Find Minimum Edge: Selects the least weight edge connecting the MST to another vertex.
  - Update Edges: Modifies the edge set to avoid cycles by including new edges from the MST and excluding any that form loops.
  - Complete MST: Continues until all vertices are incorporated, each time adding the smallest edge to expand the MST without forming cycles.
 

**Prim's Algorithm Implementation**
- Prims Algorithm belongs to the Greedy class of algorithms. This simply means that at every step, the algorithm will make a decision depending on what is the best choice at that point.
- In other words at each step, it solves the current problem in the best way and assumes the complete problem will be solved eventually in the best way.
- Let's take a look at the steps of the algorithm:
  - Start with a random vertex in the graph and mark it as visited
  - Iterate over all the visited vertices and pick the minimum weight edge that is not yet processed
  - Keep repeating step 2 until all the nodes are visited.

**Prim's Algorithm Example**
>Let’s see a step-by-step walkthrough of the algorithm:
Consider the below table with all source and destination vertices along with their weights. We want to find the minimum spanning tree for this graph.

![image](https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/3ba44473-2381-49f2-9135-8ab187ab62da)
![image](https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/acb5dfed-085b-4627-99e5-372d428619c4)

## Explanation:
- Figure-1: We pick a random vertex (A in our case). The smallest edge from A is AF having a weight of 3.
- Figure-2: Now A and F are the vertices in our answer set. The edges for these vertices which are not yet selected are (AB, AC, and FE). Of these FE has the smallest weight of 3.
- Figure-3: Now the answer set has A, F, and E. Among the edges connected to all these vertices, EC has the next minimum cost.
- Figure-4: Vertices A, F, E, and C are visited. The not selected edges for these vertices are CB, CA, AB, CD, ED. Of these, edge CB has the minimum cost.
- Figure-5: The next minimum cost edge is CD.
- Figure-6: We stop the algorithm as all the vertices are visited.

## Code
```Java
//Prims Algorithm
//we will use this to find Minimum Spanning Tree

import java.util.ArrayList;
import java.util.PriorityQueue;

//this is implemented for only undirected weighted graph
//all edges need to be connected
//Undirected , Weighted and Connected
public class PrimAlgorithm {
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

    public static void createGraph(ArrayList<Edge> graph[]) {
        for (int i = 0; i < graph.length; i++) {
            graph[i] = new ArrayList<Edge>();
        }

        graph[0].add(new Edge(0, 1, 10));
        graph[0].add(new Edge(0, 2, 15));
        graph[0].add(new Edge(0, 3, 30));

        graph[1].add(new Edge(1, 0, 10));
        graph[1].add(new Edge(1, 3, 40));

        graph[2].add(new Edge(2, 0, 15));
        graph[2].add(new Edge(2, 3, 50));

        graph[3].add(new Edge(3, 1, 40));
        graph[3].add(new Edge(3, 2, 50));


    }

    public static class Pair implements Comparable<Pair> {
        int node;
        int cost;

        public Pair(int n, int c) {
            this.node = n;
            this.cost = c;
        }

        @Override
        public int compareTo(Pair p2) {
            return this.cost - p2.cost; //ascending order sorting based on cost
        }
    }

    public static void primsAlgo(ArrayList<Edge> graph[], int V) {
        //O(E log E)
        //this will give us minimum spaning tree.
        // only node with list cost that are required to keep the graph connected
        PriorityQueue<Pair> pq = new PriorityQueue<>();  //(Node-int, cost-int) //non-mst set
        boolean vis[] = new boolean[V]; //mst set

        int finalCost = 0;
        pq.add(new Pair(0,0));

        while(!pq.isEmpty())
        {
            Pair curr = pq.remove();
            if(!vis[curr.node]){
                vis[curr.node] = true;
                finalCost = finalCost + curr.cost;

                for (int i = 0; i < graph[curr.node].size(); i++) {
                    Edge e = graph[curr.node].get(i);
                    if(!vis[e.des])
                    {
                        pq.add(new Pair(e.des,e.weight));
                    }
                }
            }
        }
        System.out.println("min cost of MST : " + finalCost);

    }

    public static void main(String[] args) {
        int V = 4;
        ArrayList<Edge> graph[] = new ArrayList[V];
        createGraph(graph);
        /*
                     15
                0--------2
                |\       |
                | \      |
                |  \30   |
             10 |   \    |50
                |    \   |
                |     \  |
                |      \ |
                1--------3
                     40
         */

        primsAlgo(graph,V);
    }
}
```

## References
- https://www.scaler.com/topics/data-structures/prims-algorithm/
- https://www.baeldung.com/java-prim-algorithm
