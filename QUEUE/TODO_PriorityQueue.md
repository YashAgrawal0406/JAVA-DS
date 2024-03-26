# Topics
- [Topics](#Topics)
  - [Explanation](#Explanation) 
  - [Code](#Code)
  - [Output](#Output)


## Explanation

> A priority queue also exhibits similar characteristics to a simple queue where each element is assigned a particular priority value, where elements in the queue are assigned based on priority.

- There are two types of priority queues:
  - Ascending Order: In this priority queue, the elements are arranged in ascending Order of their priority, i.e., the element with the smallest priority comes at the start, and the element with the greatest priority comes at the end.
  - Descending Order: In this priority queue, the elements are arranged in descending Order of their priority, i.e., the element with the greatest priority is at the start, and the element with the smallest priority is present at the end of the queue.
  - For insertion and deletion, the priority queue has a time complexity of O(logn). More information can be found at Priority Queue in Data Structure.
 
## Code
> Inbuild priority queue. See the notes of graph for implemantion of priority queue with classes
```Java
import java.util.PriorityQueue;

public class Main {

    public static void main(String[] args)
    {
        PriorityQueue<Integer> pq = new PriorityQueue<>((a,b)-> a - b);//ascending
        pq.add(100);
        pq.add(90);
        pq.add(80);
        pq.add(70);
        pq.add(60);
        pq.add(180);
        pq.add(10);

        System.out.println("Ascending");
        System.out.println(pq.toString());
        while (!pq.isEmpty())
        {
            System.out.print(pq.poll() + " ");
        }
        System.out.println();

        PriorityQueue<Integer> pq2 = new PriorityQueue<>((a,b)-> b - a);//descending
        pq2.add(100);
        pq2.add(90);
        pq2.add(80);
        pq2.add(70);
        pq2.add(60);
        pq2.add(180);
        pq2.add(10);

        System.out.println("Descending");
        System.out.println(pq2.toString());
        while (!pq2.isEmpty())
        {
            System.out.print(pq2.poll() + " ");
        }
    }
}
```

## Output

```
Ascending
[10, 70, 60, 100, 80, 180, 90]
10 60 70 80 90 100 180 
Descending
[180, 90, 100, 70, 60, 80, 10]
180 100 90 80 70 60 10 
```
