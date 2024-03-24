# Topics
- [Topics](#Topics)
  - [Explanation](#Explanation)
    - [Operations](#Operations)  
    - [Complexity](#Complexity)
    - [Application](#Application)
  - [Code](#Code)
    - [SimpleQueue](#SimpleQueue)
    - [Main](#Main)   
  - [References](#references)

## Explanation

> A Queue is an abstract linear data structure serving as a collection of elements that are inserted (enqueue operation) and removed (dequeue operation) according to the First in First Out (FIFO) approach.

> Insertion happens at the rear end of the queue whereas deletion happens at the front end of the queue. The front of the queue is returned using the peek operation.

### Operations
- `Enqueue` : The Enqueue operation is used to add an element to the front of the queue.
- `Dequeue` : The Dequeue operation is used to remove an element from the rear of the queue.
- `Peek` : The Peek operation is used to return the front most element of the queue.
- `isFull` : The isFull operation is used to check if the queue is full or not.
- `isEmpty` : The isEmpty operation is used to check if the queue is empty or not.

### Complexity
- `Enqueue` : O(1)
- `Dequeue` : O(1)
- `Peek` : O(1)
- `isFull` : O(1)
- `isEmpty` : O(1)

### Application
- Job Scheduling
- Multiprogramming
- Operation on data structures
- Buffer Space

## Code
> [!NOTE]
> Use Arraylist for creation of Queue in interview

### SimpleQueue
```Java
public static class Queue{
    static ArrayList<Integer> queue = new ArrayList<>();

    public static boolean isEmpty()
    {
        return (queue.size() == 0);
    }

    public static void add(int data)
    {
        queue.add(data);
    }

    public static int remove()
    {
        if(queue.isEmpty())
            return -1;

        int front = queue.get(0);
        queue.remove(0);
        return front;
    }
}
```

Main
```Java
public static void main(String[] args) {
    Queue q = new Queue();
    q.add(10);
    q.add(20);
    q.add(30);
    q.add(40);

    while(!q.isEmpty()) {
        System.out.println(q.remove());
    }
}
```

## References
- https://www.scaler.com/topics/data-structures/queue-in-data-structure/
- https://www.scaler.com/topics/types-of-queue-in-data-structure/

