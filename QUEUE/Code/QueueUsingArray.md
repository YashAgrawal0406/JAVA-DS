# Topics
- [Topics](#Topics)
  - [Code](#Code)
    - [Queue Using Array](#Queue-Using-Array) 
    - [Main](#Main) 
  - [Output](#Output)

> This is the code for Queue data structure using `Array`

## Code
### Queue using array
```Java
public static class Queue{
  static int[] arr;
  static int size;
  static int rear = -1;

  Queue(int n)
  {
      arr = new int[n];
      this.size = n;
  }

  public static boolean isEmpty()
  {
      return rear == -1;
  }

  public static void add(int data){
      if(rear == size -1)
      {
          System.out.println("Queue is full");
          return;
      }

      rear++;
      arr[rear] = data;

  }

  public static int remove()
  {
      if(isEmpty()) {
          System.out.println("Queue is empty");
          return -1;
      }

      int front = arr[0];
      for(int i =0;i < rear;i++)
      {
          arr[i] = arr[i +1];
      }
      rear--;
      return front;
  }

  public static int peek() {
      if(isEmpty()) {
          System.out.println("Queue is empty");
          return -1;
      }

      return arr[0];
  }
}
```

### Main
```Java
Queue q = new Queue(10);

q.add(1);
q.add(2);
q.add(3);
q.add(4);
q.add(5);
q.add(6);
q.add(7);
q.add(8);
q.add(9);
q.add(10);
q.add(11);

while(!q.isEmpty())
{
    System.out.println(q.peek());
    q.remove();
}
Queue.remove();
```

## Output
```
Queue is full
1
2
3
4
5
6
7
8
9
10
Queue is empty
```
