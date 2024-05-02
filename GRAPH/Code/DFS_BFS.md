# Topics
- [Topics](#Topics)
  - [Code](#Code)
    - [Node Sturcture](#Node-Sturcture) 
    - [Trie Data structre](#Trie-Data-structre)


## Code
Graph
```Java
  ArrayList<Edge> graph[] = new ArrayList[V];
        /*

                1----3
               /     | \
              0      |  5----6
               \     | /
                2----4
         */
```
### BFS
```Java
//Main Method
//Connected Graph BFS
System.out.println("\nBFS : ");
BFS(graph, V);
System.out.println();



public static void BFS(ArrayList<Edge> graph[], int V) {
    //The graph is connected graph
    Queue<Integer> q = new LinkedList<>();
    boolean vis[] = new boolean[V];

    q.add(0);//add first element to queue

    while (!q.isEmpty()) { //loop till all elments in queue are removed
        int curr = q.remove(); //remove front item from queue further processing

        if (vis[curr] == false) { //if visited is true go to next do nothing and go to next item in queue
            System.out.print(curr + " ");
            vis[curr] = true;

            for (int i = 0; i < graph[curr].size(); i++) { //add all edges of current node to queue
                Edge e = graph[curr].get(i);
                q.add(e.des);
            }
        }
    }
}

```


### Disconnected BFS
```Java
//Main Method
//Disconnected Graph BFS
/*
    0 --- 1 ----2
    3 ---- 4
*/
System.out.println("\nDisconnected BFS : ");
boolean vis[] = new boolean[V];
for (int i = 0; i < V; i++) {
    if(vis[i] == false)
    {
        BFSDisConnectedGraph(graph,V,vis,i);
    }
}



public static void BFSDisConnectedGraph(ArrayList<Edge> graph[], int V, boolean vis[], int start) {
    //The graph is disconnected graph
    //This code is same as normal BFS but while calling this we make sure to call each node and if its not visited
    // the we do the below activities on that
    System.out.println();
    Queue<Integer> q = new LinkedList<>();

    q.add(start);

    while (!q.isEmpty()) {
        int curr = q.remove();

        if (vis[curr] == false) {
            System.out.print(curr + " ");
            vis[curr] = true;

            for (int i = 0; i < graph[curr].size(); i++) {
                Edge e = graph[curr].get(i);
                q.add(e.des);
            }
        }
    }
}
```


### DFS
```Java
//Main Method
//connected graph DFS
System.out.println("\nDFS : ");
boolean vis1[] = new boolean[V];
DFS(graph,0,vis1);



public static void DFS(ArrayList<Edge> graph[], int curr, boolean vis[]) {
    System.out.print(curr + " ");
    vis[curr] = true;

    for (int i = 0; i < graph[curr].size(); i++) {
        Edge e = graph[curr].get(i);
        if (vis[e.des] == false) {
            DFS(graph, e.des, vis);
        }
    }
}
```

### Disconnected DFS
```Java
//Main Method
//Disconnected Graph DFS
/*
    0 --- 1 ----2
    3 ---- 4
*/
System.out.println("\nDisconnected DFS");
boolean vis2[] = new boolean[V];
for (int i = 0; i < V; i++) {
    if (vis2[i] == false) {
        DFSDisConnectedGraph(graph, i, vis2);
    }
}



public static void DFSDisConnectedGraph(ArrayList<Edge> graph[], int curr, boolean vis[]) {
    System.out.print(curr + " ");
    vis[curr] = true;

    for (int i = 0; i < graph[curr].size(); i++) {
        Edge e = graph[curr].get(i);
        if (vis[e.des] == false) {
            DFS(graph, e.des, vis);
        }
    }
}
```


### Print all the patch
> print all the paths in graph from src to target
```Java
//Main Method
//Find all the paths from src to target
int src = 0, tar = 5;
System.out.println("\nAll the patch from SRC to DES : ");
printAllPath(graph,new boolean[V],src,"0",tar);



public static void printAllPath(ArrayList<Edge> graph[], boolean vis[], int curr, String path, int tar) {
    if (curr == tar) {
        System.out.println(path);
        return;
    }

    for (int i = 0; i < graph[curr].size(); i++) {
        Edge e = graph[curr].get(i);
        if (!vis[e.des]) {
            vis[curr] = true;
            printAllPath(graph, vis, e.des, path + e.des , tar);
            vis[curr] = false;
        }
    }
}
```


## Complete Code
```Java
//This file contains
//1. BFS
//2. BFSDisConnected
//3. DFS
//4. DFSDisConnected
//5. Print all paths from Src to Des

import java.util.ArrayList;
import java.util.LinkedList;
import java.util.Queue;


//This code is for Directed unweighted graph
public class Main {
    public static class Edge {
        int src;
        int des;

        public Edge(int src, int des) {
            this.src = src;
            this.des = des;
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

        graph[0].add(new Edge(0, 1));
        graph[0].add(new Edge(0, 2));

        graph[1].add(new Edge(1, 0));
        graph[1].add(new Edge(1, 3));

        graph[2].add(new Edge(2, 0));
        graph[2].add(new Edge(2, 4));

        graph[3].add(new Edge(3, 1));
        graph[3].add(new Edge(3, 4));
        graph[3].add(new Edge(3, 5));

        graph[4].add(new Edge(4, 2));
        graph[4].add(new Edge(4, 3));
        graph[4].add(new Edge(4, 5));

        graph[5].add(new Edge(5, 3));
        graph[5].add(new Edge(5, 4));
        graph[5].add(new Edge(5, 6));

        graph[6].add(new Edge(6, 5));
    }

    //BFS = Queue
    public static void BFS(ArrayList<Edge> graph[], int V) {
        //The graph is connected graph
        Queue<Integer> q = new LinkedList<>();
        boolean vis[] = new boolean[V];

        q.add(0);//add first element to queue

        while (!q.isEmpty()) { //loop till all elments in queue are removed
            int curr = q.remove(); //remove front item from queue further processing

            if (vis[curr] == false) { //if visited is true go to next do nothing and go to next item in queue
                System.out.print(curr + " ");
                vis[curr] = true;

                for (int i = 0; i < graph[curr].size(); i++) { //add all edges of current node to queue
                    Edge e = graph[curr].get(i);
                    q.add(e.des);
                }
            }
        }
    }

    public static void BFSDisConnectedGraph(ArrayList<Edge> graph[], int V, boolean vis[], int start) {
        //The graph is disconnected graph
        //This code is same as normal BFS but while calling this we make sure to call each node and if its not visited
        // the we do the below activities on that
        System.out.println();
        Queue<Integer> q = new LinkedList<>();

        q.add(start);

        while (!q.isEmpty()) {
            int curr = q.remove();

            if (vis[curr] == false) {
                System.out.print(curr + " ");
                vis[curr] = true;

                for (int i = 0; i < graph[curr].size(); i++) {
                    Edge e = graph[curr].get(i);
                    q.add(e.des);
                }
            }
        }
    }

    public static void DFS(ArrayList<Edge> graph[], int curr, boolean vis[]) {
        System.out.print(curr + " ");
        vis[curr] = true;

        for (int i = 0; i < graph[curr].size(); i++) {
            Edge e = graph[curr].get(i);
            if (vis[e.des] == false) {
                DFS(graph, e.des, vis);
            }
        }

    }

    public static void DFSDisConnectedGraph(ArrayList<Edge> graph[], int curr, boolean vis[]) {
        System.out.print(curr + " ");
        vis[curr] = true;

        for (int i = 0; i < graph[curr].size(); i++) {
            Edge e = graph[curr].get(i);
            if (vis[e.des] == false) {
                DFS(graph, e.des, vis);
            }
        }

    }

    public static void printAllPath(ArrayList<Edge> graph[], boolean vis[], int curr, String path, int tar) {
        if (curr == tar) {
            System.out.println(path);
            return;
        }

        for (int i = 0; i < graph[curr].size(); i++) {
            Edge e = graph[curr].get(i);
            if (!vis[e.des]) {
                vis[curr] = true;
                printAllPath(graph, vis, e.des, path + e.des , tar);
                vis[curr] = false;
            }
        }

    }


    public static void main(String[] args) {
        int V = 7;
        ArrayList<Edge> graph[] = new ArrayList[V];
        /*

                1----3
               /     | \
              0      |  5----6
               \     | /
                2----4
         */

        createGraph(graph);


        //Connected Graph BFS
        System.out.println("\nBFS : ");
        BFS(graph, V);
        System.out.println();

        //Disconnected Graph BFS
        /*
            0 --- 1 ----2
            3 ---- 4
        */
        System.out.println("\nDisconnected BFS : ");
        boolean vis[] = new boolean[V];
        for (int i = 0; i < V; i++) {
            if(vis[i] == false)
            {
                BFSDisConnectedGraph(graph,V,vis,i);
            }
        }
        System.out.println();


        //connected graph DFS
        System.out.println("\nDFS : ");
        boolean vis1[] = new boolean[V];
        DFS(graph,0,vis1);
        System.out.println();


        //Disconnected Graph DFS
        /*
            0 --- 1 ----2
            3 ---- 4
        */
        System.out.println("\nDisconnected DFS");
        boolean vis2[] = new boolean[V];
        for (int i = 0; i < V; i++) {
            if (vis2[i] == false) {
                DFSDisConnectedGraph(graph, i, vis2);
            }
        }
        System.out.println();

        //Find all the paths from src to target
        int src = 0, tar = 5;
        System.out.println("\nAll the patch from SRC to DES : ");
        printAllPath(graph,new boolean[V],src,"0",tar);

    }
}
```
## Output
```
 /*

        1----3
       /     | \
      0      |  5----6
       \     | /
        2----4
 */
```
```
BFS : 
0 1 2 3 4 5 6 

Disconnected BFS : 
0 1 2 3 4 5 6 

DFS : 
0 1 3 4 2 5 6 

Disconnected DFS
0 1 3 4 2 5 6 

All the patch from SRC to DES : 
01345
0135
02435
0245
```
