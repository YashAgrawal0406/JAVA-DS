# Topics
- [Topics](#Topics)
  - [Explanation](#Explanation) 
  - [Code](#Code)
  - [Output](#Output)
 
## Explanation
> A Circular Queue, also known as a Ring Buffer, is a type of linear data structure that adheres to the FIFO (First In, First Out) principle. Unlike a traditional queue, the last position in a Circular Queue is linked back to the first position, forming a circular arrangement.

- Key points about Circular Queue:

  - It operates on the FIFO principle, where the rear is connected to the end, creating a circular structure.
  - Commonly referred to as a ring buffer due to its circular nature.
  - Insertion and deletion operations in a Circular Queue have a constant time complexity of O(1), making it efficient for managing data.
  - Circular Queues find application in various domains such as memory management, traffic systems, and CPU scheduling due to their efficient operation and ability to manage data in a cyclical manner.

![image](https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/1f982707-763a-44a2-bc7a-9aa3590d1dab)


## Code
```Java
//Circular Queue using array
public class Main {

    public static class Queue {
        static int[] arr;
        static int size;
        static int rear = -1;
        static int front = -1;

        Queue(int n) {
            arr = new int[n];
            this.size = n;
        }

        public static boolean isEmpty() {
            return rear == -1 && front == -1;
        }

        public static boolean isFull() {
            return (rear + 1) % size == front;
        }

        public static void add(int data) {
            if (isFull()) {
                System.out.println("Queue is full");
                return;
            }
            if (front == -1) {
                front++;
            }
            rear = (rear + 1) % size;
            arr[rear] = data;
        }

        public static int remove() {
            if (isEmpty()) {
                System.out.println("Queue is empty");
                return -1;
            }

            int result = arr[front];
            if (rear == front) {
                rear = front = -1;
            } else {
                front = (front + 1) % size;
            }
            return result;
        }

        public static int peek() {
            if (isEmpty()) {
                System.out.println("Queue is empty");
                return -1;
            }
            return arr[front];
        }
    }

    public static void main(String[] args) {
        Queue q = new Queue(5);
        q.add(1);
        q.add(2);
        q.add(3);
        q.add(4);
        q.add(5);
        System.out.println("Item removed : " + q.remove());  //remove 1
        q.add(6);
        System.out.println("Item removed : " + q.remove()); //remove 2
        q.add(7);
        q.add(8); // After removing 1 & 2 and adding 6 & 7 // Queue is full
        System.out.println("Item removed : " + q.remove()); //remove 3 
        q.add(8);
        while (!q.isEmpty()) {
            System.out.println(q.peek());
            q.remove();
        }
        q.remove();
    }
}
```

## Output
```
Item removed : 1
Item removed : 2
Queue is full
Item removed : 3
4
5
6
7
8
Queue is empty

```
