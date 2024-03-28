# Topics
- [Topics](#Topics)
  - [Code](#Code)
    - [Node Sturcture](#Node-Sturcture) 
    - [Simple Graph Implementation](#Simple-Graph-Implementation)
   

## Code
### Node Structure
```Java
 public static class Edge{
    int src;
    int des;
    //if we want weighted graph we can use this code all commented data
    //int weight
    public Edge(int src, int des)
    {
        this.src = src;
        this.des = des;
        //this.weight = weight;
    }
}
```

### Simple Graph Implementation
```Java
//This code is for undirected unweighted graph

import java.util.ArrayList;

public class Main {
    public static class Edge{
        int src;
        int des;
        //if we want weighted graph we can use this code all commented data
        //int weight
        public Edge(int src, int des)
        {
            this.src = src;
            this.des = des;
            //this.weight = weight;
        }
    }

    public static void printGraph(ArrayList<Edge> graph)
    {
        //this will print all the edges for only one node
        for (int i = 0; i < graph.size(); i++) {
            Edge e = graph.get(i);
            System.out.println(e.src +"->"+e.des);
        }
        // output
        // 2->0
        // 2->1
        // 2->3

    }
    public static void createGraph(ArrayList<Edge> graph[])
    {
        for (int i = 0; i < graph.length; i++) {
            graph[i] = new ArrayList<>();
        }

	//add extra paramter edge for weight
        graph[0].add(new Edge(0,2));

        graph[1].add(new Edge(1,2));
        graph[1].add(new Edge(1,3));

        graph[2].add(new Edge(2,0));
        graph[2].add(new Edge(2,1));
        graph[2].add(new Edge(2,3));

        graph[3].add(new Edge(3,1));
        graph[3].add(new Edge(3,2));
    }
    public static void main(String[] args) {
        int V = 4;
        /*
                    0    3
                    |  / |
                    | /  |
                    2 ---1

         */

        ArrayList<Edge> graph[] = new ArrayList[4];
        createGraph(graph);

        //lets print neighbors of 2
        printGraph(graph[2]);
    }
}
```
