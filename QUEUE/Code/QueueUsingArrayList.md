# Topics
- [Topics](#Topics)
  - [Code](#Code)
    - [Queue Using ArrayList](#Queue-Using-ArrayList) 
    - [Main](#Main) 
  - [Output](#Output)

> This is the code for Queue data structure using `ArrayList`

## Code
### Queue Using ArrayList
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
        if(queue.isEmpty()) {
            System.out.println("Queue is Empty");
            return -1;
        }

        int front = queue.get(0);
        queue.remove(0);
        return front;
    }
}
```

### Main
```
 Queue q = new Queue();
q.add(10);
q.add(20);
q.add(30);
q.add(40);

while(!q.isEmpty()) {
    System.out.println(q.remove());
}
q.remove();
```

## Output
```
10
20
30
40
Queue is Empty
```
