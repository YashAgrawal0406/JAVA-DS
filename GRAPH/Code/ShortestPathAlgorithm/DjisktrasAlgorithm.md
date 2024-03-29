# Topics

- [Topics](#Topics)
  - [Theory](#Code)
  - [Code](#Code)
  - [Explanation](#Explanation)


## Code
//Dijkstra's Algorithm

```Java
import java.util.*;

public class Main {
    public static class Edge {
        int src;
        int des;
        int weight;
        public Edge(int src, int des,int weight) {
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

        graph[0].add(new Edge(0, 1,2));
        graph[0].add(new Edge(0, 2,4));

        graph[1].add(new Edge(1, 3,7));
        graph[1].add(new Edge(1, 2,1));

        graph[2].add(new Edge(2, 4,3));

        graph[3].add(new Edge(3, 5,1));

        graph[4].add(new Edge(4, 3,2));
        graph[4].add(new Edge(4, 5,5));
    }

    public static class Pair implements Comparable<Pair> {
        int node;
        int dist;
        public Pair(int n,int d){
            this.node = n;
            this.dist =d;
        }

        @Override
        public int compareTo(Pair p2) {
            return this.dist - p2.dist; //ascending order sorting based on distance
            //if we do (p2.dist - this.dist) it will be descending order
        }
    }
    
    public static void dijkstra(ArrayList<Edge> graph[],int src,int V)
    {
        //O(E + E logV)
        //this code will give us shortest distance form src node to each
        //i.e 0 -> 0 = 0 , 0 -> 1 = 2 , 0 -> 2 = 3 , etc...
        PriorityQueue<Pair> pq = new PriorityQueue<>();
        int dist[] = new int[V];
        for (int i = 0; i < V; i++) {
            if(i!=src)//make all distances as infinity of int max except source node
            {
                dist[i] = Integer.MAX_VALUE;
            }
        }
        boolean vis[] = new boolean[V];

        pq.add(new Pair(0,0));

        while (!pq.isEmpty())
        {
            Pair curr = pq.remove(); // we will get shortest distance pair based on cost
            if(!vis[curr.node]){
                vis[curr.node] = true;

                for (int i = 0; i < graph[curr.node].size(); i++) {
                    Edge e = graph[curr.node].get(i);
                    int u = e.src;  //u --> v  //src to destination
                    int v = e.des;
                    if(dist[u] + e.weight < dist[v]) // destination weight is greater that the weight from the current
                    {                                //source + weight of the edge then change destination weight
                        dist[v] = dist[u] + e.weight;
                        pq.add(new Pair(v,dist[v])); //dist[v] this distance is the total of the distance from the source
                    }
                }
            }
        }

        for (int i = 0; i < V; i++) {
            System.out.print(dist[i] + " ");
        }
    }

    public static void main(String[] args) {
        int V = 6;
        ArrayList<Edge> graph[] = new ArrayList[V];
        createGraph(graph);
        /*
                      7
                 1--------3
                /|        |\
             2 / |        | \ 1
              /  |        |  \
             0   |1      2|   5
              \  |        |  /
             4 \ |        | / 5
                \|        |/
                 2--------4
                      3
         */

        //Dijkstra's Algorithm
        dijkstra(graph,0,V);
    }
}
```

## Explanation
```
- We first create a Pair class which has the source node, the neighbor node, and the weight. We have initialized its constructor.
- We have then implemented the Comparable interface and the weight will be compared.
- In the main function, we create a graph and then add the edges accordingly.
- We create a boolean array visited which tracks whether the vertex has been visited or not. We create a priority queue of the
- Add the source node in the priority queue. Then while the queue is not empty, now we keep removing one edge and add the adjacent edges if they have not been visited and mark them as visited.
- As we are using a priority queue, the edge with a lesser value will be popped. The adjacent edges are added and the steps are repeated till all nodes are covered.
```
