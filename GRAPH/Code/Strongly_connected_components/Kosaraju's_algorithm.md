
# Topics
- [Topics](#Topics)
  - [Theory](#Theory)
  - [Explanation](#Explanation)
  - [Code](#Code)
  - [References](#References)

 ## Theory
> - Find all strongly connected components in O(V+E) time using Kosaraju’s algorithm.

> - Strongly connected Component(SCC) - In a directed graph a strongly connected component is a component of the graph in which there is a path between every pair of vertices.

Example
> Example of strongly connected component in a graph :

<p align="center">
  <img src="https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/6fab8f82-befe-45b6-9cb0-30a1f0ffbb85"> 
</p>

Example Explanation
- In the above Example diagram the directed graph contains three strongly connected component.
  - the vertex group of (7,5,6) in which there is a path between every pair of vertices.
  - 4 - single vertex
  - The vertex group of (1,2,3) in which there is a path between every pair of vertices.
- In the above example we can see that a single vertex is also considered as a strongly connected component. As kosaraju Algorithm finds the minimum number of strongly connected component in directed graph so the answer to the above example will be 3.


## Code
```Java
import java.util.ArrayList;
import java.util.Stack;

//this is basically topological graph with some additional steps
//another name is strongly connected graph
//this is done on directed graph
public class Main {
    static class Edge {
        int src;
        int dest;
        public Edge(int s, int d) {
            this.src = s;
            this.dest = d;
        }
    }
    static void createGraph(ArrayList<Edge> graph[]) {
        for(int i=0; i<graph.length; i++) {
            graph[i] = new ArrayList<>();
        }
        graph[0].add(new Edge(0, 2));
        graph[0].add(new Edge(0, 3));

        graph[1].add(new Edge(1, 0));

        graph[2].add(new Edge(2, 1));

        graph[3].add(new Edge(3, 4));
    }


    //modified DFS
    public static void topologySortUtil(ArrayList<Edge> graph[], int curr, boolean vis[], Stack<Integer> stack){
        vis[curr] = true;

        for (int i = 0; i < graph[curr].size(); i++) {
            Edge e = graph[curr].get(i);
            if(!vis[e.dest])
            {
                topologySortUtil(graph,e.dest,vis,stack);
            }
        }
        stack.push(curr);
    }

    public static void dfs(ArrayList<Edge> graph[],int curr,boolean vis[]){
        vis[curr] = true;
        System.out.print(curr + " ");

        for (int i = 0; i < graph[curr].size(); i++) {
            Edge e = graph[curr].get(i);
            if(!vis[e.dest]){
                dfs(graph, e.dest, vis);
            }
        }
    }
    public static void kosarajuAlgo(ArrayList<Edge> graph[],int V)
    {
        //step1 //push in stack using DFS
        boolean vis[] = new boolean[V];
        Stack<Integer> stack = new Stack<>();

        for (int i = 0; i < V; i++) {
            if(!vis[i])
            {
                topologySortUtil(graph,i,vis,stack );
            }
        }

        //Step 2 //Transpose of graph
        //Basically reverse each edge if its 0 to 2 make it 2 to 0 (0->2)turns to (2->0)
        ArrayList<Edge> tranpose[] = new ArrayList[V];
        for (int i = 0; i < graph.length; i++) {
            vis[i] = false;
            tranpose[i] = new ArrayList<Edge>();
        }

        for (int i = 0; i < V; i++) {
            for (int j = 0; j < graph[i].size(); j++) {
                Edge e = graph[i].get(j); //e.src ->e.dest
                tranpose[e.dest].add(new Edge(e.dest, e.src));

            }
        }

        while(!stack.isEmpty())
        {
            int curr = stack.pop();
            if(!vis[curr])
            {
                dfs(tranpose,curr,vis);
            }
            System.out.println();

        }
    }
    public static void main(String args[]) {
/*
        0 ------- 3
       /|         |
      / |         |
     1  |         4
      \ |
       \|
        2
*/
        int V = 5;
        ArrayList<Edge> graph[] = new ArrayList[V];
        createGraph(graph);

        kosarajuAlgo(graph,V);
    }

}
```

## References
- https://www.baeldung.com/cs/kosaraju-algorithm-scc
- https://www.scaler.com/topics/kosaraju-algorithm/
