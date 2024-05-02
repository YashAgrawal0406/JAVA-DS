# Topics
- [Topics](#Topics)
  - [Explanation](#Explanation) 
  - [Code](#Code)
  - [Output](#Output)
  - [Inbuild Dequeue Collection Framework](#Inbuild-Dequeue-Collection-Framework)

## Explanation 
> A Double-ended Queue, or Deque, is a different type of queue where enqueue (insertion) and dequeue (deletion) operations are performed at both ends, i.e., the rear-end (tail) and the front-end (head). The Deque data structure supports clockwise and anticlockwise rotations in O(1) time, which can be useful in certain applications.

> The Deque can further be divided into two special queues, i.e., Input-restricted Deque and Output-Restricted Deque.

> The time complexity of a double-ended queue is O(1) for insertion and deletion.

![image](https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/9c96b9a9-e0b1-4631-bc0d-8629e8162722)

## Code
```Java
class ArrayDeque {
    private int[] deque;
    private int front;
    private int rear;
    private int size;
    private int capacity;

    // Constructor to initialize the deque with a given capacity
    public ArrayDeque(int capacity) {
        this.capacity = capacity;
        deque = new int[capacity];
        front = 0;
        rear = capacity - 1;
        size = 0;
    }

    // Function to insert an element at the front of the deque
    public void insertFront(int val) {
        if (isFull()) {
            System.out.println("Deque is full. Cannot insert at front.");
            return;
        }
        front = (front - 1 + capacity) % capacity;
        deque[front] = val;
        size++;
    }

    // Function to insert an element at the rear of the deque
    public void insertRear(int val) {
        if (isFull()) {
            System.out.println("Deque is full. Cannot insert at rear.");
            return;
        }
        rear = (rear + 1) % capacity;
        deque[rear] = val;
        size++;
    }

    // Function to delete an element from the front of the deque
    public void deleteFront() {
        if (isEmpty()) {
            System.out.println("Deque is empty. Cannot delete from front.");
            return;
        }
        front = (front + 1) % capacity;
        size--;
    }

    // Function to delete an element from the rear of the deque
    public void deleteRear() {
        if (isEmpty()) {
            System.out.println("Deque is empty. Cannot delete from rear.");
            return;
        }
        rear = (rear - 1 + capacity) % capacity;
        size--;
    }

    // Function to get the front element of the deque
    public int getFront() {
        if (isEmpty()) {
            System.out.println("Deque is empty. No front element.");
            return -1;
        }
        return deque[front];
    }

    // Function to get the rear element of the deque
    public int getRear() {
        if (isEmpty()) {
            System.out.println("Deque is empty. No rear element.");
            return -1;
        }
        return deque[rear];
    }

    // Function to check if the deque is empty
    public boolean isEmpty() {
        return size == 0;
    }

    // Function to check if the deque is full
    public boolean isFull() {
        return size == capacity;
    }

    // Function to print the elements of the deque
    public void printDeque() {
        if (isEmpty()) {
            System.out.println("Deque is empty.");
            return;
        }
        int index = front;
        for (int i = 0; i < size; i++) {
            System.out.print(deque[index] + " ");
            index = (index + 1) % capacity;
        }
        System.out.println();
    }
}

public class Main {
    public static void main(String[] args) {
        ArrayDeque deque = new ArrayDeque(5);
        deque.insertRear(1);
        deque.insertFront(2);
        deque.insertRear(3);
        deque.insertFront(4);
        deque.printDeque(); // Output: 4 2 1 3
        deque.deleteFront();
        deque.deleteRear();
        deque.printDeque(); // Output: 2 1
    }
}
```

## Output
```
4 2 1 3 
2 1
```


## Inbuild Dequeue Collection Framework
```Java
package DequeueCollectionFramework;

import java.util.ArrayDeque;

public class Main {
    public static void main(String[] args) {
        ArrayDeque<Integer> deque = new ArrayDeque<>();

        deque.addFirst(10);
        deque.addLast(100);
        deque.addLast(80);
        deque.addFirst(20);
        deque.addFirst(30);

        deque.removeFirst();
        deque.removeLast();

        System.out.println(deque);
    }

}
```
