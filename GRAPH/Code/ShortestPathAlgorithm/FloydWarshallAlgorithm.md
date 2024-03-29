# Topics
- [Topics](#Topics)
  - [Theory](#Theory)
  - [Code](#Code)
  - [Explanation](#Explanation)
  - [Advantages and Disadvantages](#Advantages-and-Disadvantages)
  - [References](#References)


## Theory
> - If you’re looking for an algorithm for scenarios like finding the shortest distance between every pair of stations in a subway, then all hail the mighty polynomial-time Floyd-Warshall algorithm!
> - In other words, the Floyd-Warshall algorithm is an ideal choice for finding the length of the shortest path across every pair of nodes in a graph data structure.
> - Albeit, the graph shouldn’t contain any negative weight cycles. 🤞🏻
> - You see, the Floyd-Warshall algorithm does support negative weight edges in a directed graph so long the weighted sum of such edges forming a cycle isn’t negative.
> - And that’s what I mean by a negative weight cycle!
> - Think about it, if there exists such a negative cycle, we can always just keep traversing this cycle over and over while making the length of the path smaller and smaller. Keep doing it, and the length eventually approaches negative infinity which is absurd!
> - Refer below gif for example 
>   - https://www.scaler.com/topics/media/floyd-warshall.gif
> - Also if we observe, the algorithm can’t support negative weight edges in an undirected graph at all. Such an edge forms a negative cycle in and of itself since we can traverse back and forth along that edge infinitely as it’s an undirected graph.
> - Well, you might argue why bother learning another algorithm when we can solve the same stuff by extending the Bellman-Ford or Dijkstra’s shortest path algorithm on every node in the graph.
> - Technically you can, but we don't use Dijkstra/Bellman-ford...
Because of time complexity! ⏰
Will discuss more on that later…
Now that we have a fair share of understanding as to what is and why we need the Floyd-Warshall algorithm, let’s peek behind the curtains and see how it works!


## Code
```Java
import java.util.ArrayList;
import java.util.Arrays;

public class FloydWarshall {
    // Function to find the shortest distances between all pairs of vertices
    public static void floydWarshall(ArrayList<ArrayList<Integer>> graph) {
        int V = graph.size(); // Number of vertices

        // Create a 2D array to store the shortest distances
        int[][] dist = new int[V][V];

        // Initialize the dist array with the weights of the edges
        for (int i = 0; i < V; i++) {
            for (int j = 0; j < V; j++) {
                if (i == j) {
                    dist[i][j] = 0;
                } else if (graph.get(i).get(j) != 0) {
                    dist[i][j] = graph.get(i).get(j);
                } else {
                    dist[i][j] = Integer.MAX_VALUE;
                }
            }
        }

        // Compute shortest distances
        for (int k = 0; k < V; k++) {
            for (int i = 0; i < V; i++) {
                for (int j = 0; j < V; j++) {
                    // If vertex k is on the shortest path from i to j, update the distance
                    if (dist[i][k] != Integer.MAX_VALUE && dist[k][j] != Integer.MAX_VALUE &&
                        dist[i][k] + dist[k][j] < dist[i][j]) {
                        dist[i][j] = dist[i][k] + dist[k][j];
                    }
                }
            }
        }

        // Print the shortest distances
        printSolution(dist);
    }

    // Function to print the shortest distances
    public static void printSolution(int[][] dist) {
        int V = dist.length;
        System.out.println("Shortest distances between all pairs of vertices:");
        for (int i = 0; i < V; ++i) {
            for (int j = 0; j < V; ++j) {
                if (dist[i][j] == Integer.MAX_VALUE) {
                    System.out.print("INF ");
                } else {
                    System.out.print(dist[i][j] + " ");
                }
            }
            System.out.println();
        }
    }

    public static void main(String[] args) {
        // Example graph represented by adjacency list
        ArrayList<ArrayList<Integer>> graph = new ArrayList<>();
        graph.add(new ArrayList<>(Arrays.asList(0, 5, 0, 10)));
        graph.add(new ArrayList<>(Arrays.asList(0, 0, 3, 0)));
        graph.add(new ArrayList<>(Arrays.asList(0, 0, 0, 1)));
        graph.add(new ArrayList<>(Arrays.asList(0, 0, 0, 0)));

        floydWarshall(graph);
    }
}
```


## References
- https://www.scaler.com/topics/data-structures/floyd-warshall-algorithm/
- https://www.geeksforgeeks.org/floyd-warshall-algorithm-dp-16/
- https://www.baeldung.com/cs/dijkstra-vs-floyd-warshall
- https://www.baeldung.com/cs/floyd-warshall-shortest-path#:~:text=The%20Floyd%2DWarshall%20algorithm%20is,in%20a%20weighted%20directed%20graph.
