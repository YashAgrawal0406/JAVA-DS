# Topics
- [Topics](#Topics)
  - [Bridge in Graph](#Bridge-in-Graph)
    - [Code](#CodeBridge) 
  - [Articulation Point in Graph](#Articulation-Point-in-Graph)
    - [Code](#CodeArticulation) 
  - [References](#References)
 

## Bridge in Graphs
> Uses DFS algorithm. 
> Bridge is an edge whose deletion increases the graphs number of connected componenets

> A bridge is an edge from vertex U to vertex V such that removing the edge increases the number of connected components in the graph.

> To find bridges in a graph we can use the same approach used to find articulation points. But, since we are removing an edge instead of a vertex to find whether an edge is a bridge or not we use the condition, low[child_node] > discovery_time[current_node]

### CodeBridge
```Java
import java.util.ArrayList;

public class BridgeInGraph {

    static class Edge{
        int src;
        int des;

        public Edge(int s , int d){
            this.src = s;
            this.des = d;
        }
    }


    public static void createGraph(ArrayList<Edge> graph[]) {
        for (int i = 0; i < graph.length; i++) {
            graph[i] =  new ArrayList<Edge>();
        }

        graph[0].add(new Edge(0,1));
        graph[0].add(new Edge(0,2));
        graph[0].add(new Edge(0,3));

        graph[1].add(new Edge(1,0));
        graph[1].add(new Edge(1,2));

        graph[2].add(new Edge(2,0));
        graph[2].add(new Edge(2,1));

        graph[3].add(new Edge(3,0));
        graph[3].add(new Edge(3,4));
        //graph[3].add(new Edge(3,5));

        graph[4].add(new Edge(4,3));
        //graph[4].add(new Edge(4,5));

        //graph[5].add(new Edge(5,3));
        //graph[5].add(new Edge(5,4)); // Remove Node 5 from the graph to get 2 bridges
    }

    public static void dfs(ArrayList<Edge> graph[], int curr, boolean vis[],int dt[],int low[], int time, int par){

        vis[curr] = true;
        dt[curr] = low[curr] = ++time;

        for (int i = 0; i < graph[curr].size(); i++) {
            Edge e = graph[curr].get(i);
            if(e.des == par) {
                continue;
            } else if (!vis[e.des]) {
                dfs(graph,e.des,vis,dt,low,time,curr); // curr can be replaced with e.src
                low[curr] = Math.min(low[curr],low[e.des]);
                if(dt[curr] < low[e.des]){
                    System.out.println("Bridge is  : " + curr + "-----" + e.des);
                }
            } else{
               low[curr] = Math.min(low[curr],dt[e.des]);
            }
        }
    }

    public static void getBridge(ArrayList<Edge> graph[],int V)
    {
        int dt[] = new int[V];
        int low[] = new int[V];
        int time = 0;
        boolean vis[] = new boolean[V];

        for (int i = 0; i < V; i++) {
            if(!vis[i]){
                dfs(graph,i,vis,dt,low,time,-1);
            }
        }
    }

    public static void main(String args[]){
        /*
              1 --- 0 ----- 3 --- 4
              |   /          \   |
              |  /            \  |
              | /              \ |
               2                5
         */

        int V = 6;
        ArrayList<Edge> graph[] = new ArrayList[V];
        createGraph(graph);

        getBridge(graph,V);

    }
}

```


## Articulation point
> Articulation Points in a network represent single points of failure. That is if we remove a vertex that is an articulation point in the network the number of connected components in that network increases. A connected component is defined as a sub-graph or a sub-network in which one node can be reached from every other node by traversing edges. The knowledge of articulation points in a network becomes crucial when building reliable networks without single points of failure. Tarjan’s Algorithm is used to find articulation points in a network efficiently.

> An articulation point is a vertex that when removed (along with it's edges) creates more components in the graph.
### CodeArticulation
```Java
import java.util.ArrayList;

public class ArticulationPoint {
    static class Edge{
        int src;
        int des;

        public Edge(int s , int d){
            this.src = s;
            this.des = d;
        }
    }


    public static void createGraph(ArrayList<Edge> graph[]) {
        for (int i = 0; i < graph.length; i++) {
            graph[i] =  new ArrayList<Edge>();
        }

        graph[0].add(new Edge(0,1));
        graph[0].add(new Edge(0,2));
        graph[0].add(new Edge(0,3));

        graph[1].add(new Edge(1,0));
        graph[1].add(new Edge(1,2));

        graph[2].add(new Edge(2,0));
        graph[2].add(new Edge(2,1));

        graph[3].add(new Edge(3,0));
        graph[3].add(new Edge(3,4));

        graph[4].add(new Edge(4,3));
    }

    public static void dfs(ArrayList<Edge> graph[], int curr, boolean vis[], int dt[], int low[], int time, int par, boolean ap[]){

        vis[curr] = true;
        dt[curr] = low[curr] = ++time;
        int children = 0;

        for (int i = 0; i < graph[curr].size(); i++) {
            Edge e = graph[curr].get(i);
            int neigh = e.des;

            if(neigh == par) {
                continue;
            } else if (vis[neigh]) {
                low[curr] = Math.min(low[curr],dt[neigh]);
            } else{
                dfs(graph,neigh,vis,dt,low,time,curr,ap);
                low[curr] = Math.min(low[curr],low[neigh]);
                if(dt[curr] <= low[neigh] && par != -1)
                {
                    ap[curr] = true;
                }
                children++;
            }
        }

        if(par == -1 && children > 1)
        {
            ap[curr] = true;
        }
    }

    public static void getAP(ArrayList<Edge> graph[], int V)
    {
        int dt[] = new int[V];
        int low[] = new int[V];
        int time = 0;
        boolean vis[] = new boolean[V];
        boolean ap[] = new boolean[V];

        for (int i = 0; i < V; i++) {
            if(!vis[i]){
                dfs(graph,i,vis,dt,low,time,-1,ap);
            }
        }
        for (int i = 0; i < V; i++) {
            if(ap[i])
            {
                System.out.println("AP : " + i);
            }
        }
    }

    public static void main(String args[]){
        /*
              1 --- 0 ----- 3
              |   /         |
              |  /          |
              | /           |
               2            4
         */

        int V = 6;
        ArrayList<Edge> graph[] = new ArrayList[V];
        createGraph(graph);

        getAP(graph,V);

    }
}

```

## References
- https://www.scaler.com/topics/data-structures/articulation-points-and-bridges/
- https://www.baeldung.com/cs/scc-tarjans-algorithm
- https://www.scaler.com/topics/data-structures/strongly-connected-components/
