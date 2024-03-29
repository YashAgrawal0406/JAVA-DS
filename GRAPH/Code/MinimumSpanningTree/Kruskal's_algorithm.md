
# Topics
- [Topics](#Topics)
  - [Theory](#Theory)
  - [Code](#Code)
  - [References](#References)
 

## Theory
> - Suppose that there are some villages in a town, you being the Mayor of the town want to visit all the villages but you have very little time for it.
> - So you will be interested in visiting the villages in such a way that the total distance covered by you during the visit is minimum possible. Isn't it.?
> - If you try to formulate the above problem in terms of graph theory, by considering villages as the vertices, roads connecting them as the edges, and the distance of each road as the weight of the corresponding edge.
Kurskal's algorithm will help you in this case because it is used to find the minimum spanning tree (MST) of any given connected, weighted, undirected graph. Before discussing any further details of Kruskal's algorithm > - let's see what is meant by a Minimum spanning tree of a graph.
> - A spanning tree is a subgraph of a connected, undirected graph such that it is a tree and it includes all the vertices. So a minimum spanning tree would correspond to a spanning tree with the minimum weight. Where the weight of a spanning tree is the sum of the weight of the edges present in it.

For Example:

> The below-given image shows a graph G with 6 vertices and 9 edges

<p align="center">
  <img src="https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/755bb3aa-5d7d-42b4-8536-72c00143b752" width="450" height="300"> 
</p>

> This graph can have multiple spanning tree some of which are shown below with their respective weights.

<p align="center">
  <img src="https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/17eb128b-e1a0-4b83-8f60-9883c3407ada" width="450" height="300"> 
</p>

> But they can not be considered as minimum spanning trees as there exists at least one spanning tree with an even smaller sum of edge weights. The MST of the graph is -

<p align="center">
  <img src="https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/6f38c726-d3cf-4de3-8390-009861c98482" width="450" height="300"> 
</p>

> The MST of the given graph has a weight of 17, which means that we can't form any other spanning tree of graph G whose weight is less than 17.


## Code 

```Java
import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;

// Class to represent an edge in the graph
class Edge {
    int src, dest, weight;

    Edge(int src, int dest, int weight) {
        this.src = src;
        this.dest = dest;
        this.weight = weight;
    }
}

public class KruskalAlgorithm {
    // Function to find the MST of the graph using Kruskal's algorithm
    public static ArrayList<Edge> kruskalMST(ArrayList<Edge> graph, int V) {
        // Sort the edges in non-decreasing order of their weights
        Collections.sort(graph, Comparator.comparingInt(a -> a.weight));

        // Initialize an empty arraylist to store the edges of the MST
        ArrayList<Edge> mst = new ArrayList<>();

        // Create a disjoint-set data structure
        DisjointSet ds = new DisjointSet(V);

        // Iterate through the sorted edges
        for (Edge edge : graph) {
            int srcParent = ds.find(edge.src);
            int destParent = ds.find(edge.dest);

            // If adding the edge does not create a cycle, add it to the MST
            if (srcParent != destParent) {
                mst.add(edge);
                ds.union(srcParent, destParent);
            }
        }

        return mst;
    }

    public static void main(String[] args) {
        // Example graph represented by ArrayList of edges
        ArrayList<Edge> graph = new ArrayList<>();
        int V = 4; // Number of vertices

        // Adding edges to the graph (src, dest, weight)
        graph.add(new Edge(0, 1, 10));
        graph.add(new Edge(0, 2, 6));
        graph.add(new Edge(0, 3, 5));
        graph.add(new Edge(1, 3, 15));
        graph.add(new Edge(2, 3, 4));

        // Find the MST using Kruskal's algorithm
        ArrayList<Edge> mst = kruskalMST(graph, V);

        // Print the edges of the MST
        System.out.println("Edges of the Minimum Spanning Tree:");
        for (Edge edge : mst) {
            System.out.println(edge.src + " - " + edge.dest + " : " + edge.weight);
        }
    }
}

// Disjoint-set data structure for cycle detection
class DisjointSet {
    int[] parent;

    public DisjointSet(int n) {
        parent = new int[n];
        for (int i = 0; i < n; i++) {
            parent[i] = i;
        }
    }

    public int find(int x) {
        if (parent[x] != x) {
            parent[x] = find(parent[x]);
        }
        return parent[x];
    }

    public void union(int x, int y) {
        int xParent = find(x);
        int yParent = find(y);
        parent[xParent] = yParent;
    }
}

```

## References
- https://www.scaler.com/topics/data-structures/kruskal-algorithm/
- https://www.scaler.com/topics/prims-and-kruskal-algorithm/
- https://www.baeldung.com/java-spanning-trees-kruskal
- https://www.baeldung.com/cs/kruskals-vs-prims-algorithm
