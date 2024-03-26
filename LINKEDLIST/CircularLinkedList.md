# Topics
- [Topics](#Topics)
  - [Explanation](#Explanation) 
  - [Code](#Code)
    - [Node Structure](#Node-Structure)
    - [Linked List](#Linked-List)
    - [Main](#Main)
  - [Output](#Output)
  - [References](#References)
 
## Explanation 
> A circular linked list is a variation of the linked list data structure where the last node of the list points back to the first node, forming a circle or loop. In other words, the next pointer of the last node points to the first node of the list. This circular structure allows traversal of the list from any node to any other node.
Here's a brief explanation of circular linked lists:
- `Node:`
  - Each node in a circular linked list contains two fields:
    - `Data:` Holds the value or data associated with the node.
    - `Next pointer:` Points to the next node in the list.
  - The last node's next pointer points back to the first node, forming the circular structure.
- Basic Operations:
  - `Insertion:`
    - Elements can be inserted at the beginning, middle, or end of the circular linked list.
    - To insert a new node, the next pointer of the new node is set to point to the next node of the insertion point, and the next pointer of the preceding node is updated to point to the new node.
  - `Deletion:`
    - Elements can be deleted from the list by updating the next pointer of the preceding node to skip the node to be deleted.
  - `Traversal:`
    - Circular linked lists support traversal in both forward and backward directions. Traversal typically starts from the head or any other node and continues until reaching the starting node again.
  - `Search:`
    - Searching for a specific value involves traversing the circular linked list and comparing each node's value until the target value is found or until traversing the entire list once.
- `Advantages:`
  - Circular structure: The circular linked list structure allows for efficient traversal and looping through the elements of the list.
  - No null references: Since the last node's next pointer points back to the first node, there are no null references in the list, simplifying certain operations.
  - Dynamic size: Circular linked lists can grow or shrink dynamically as nodes are added or removed.
- `Applications:`
  - Circular queues: Circular linked lists are often used to implement circular queues, where elements are added and removed in a circular manner.
  - Round-robin scheduling: Circular linked lists are used in round-robin scheduling algorithms, where tasks are scheduled in a circular order.
  - Circular buffers: Circular linked lists are used in implementing circular buffers, which are used for data storage and buffering in computer science and embedded systems.
 
![image](https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/6138d155-a589-4672-b6c9-bb2b95cf0ab8)

## Code
### Node Structure
```Java
class Node {
    int data;
    Node next;

    public Node(int data) {
        this.data = data;
        this.next = null;
    }
}
```
### Circular Linked Linked
```Java
class Node {
    int data;
    Node next;

    public Node(int data) {
        this.data = data;
        this.next = null;
    }
}

public class CircularLinkedList {
    private Node head;
    private Node tail;

    public CircularLinkedList() {
        this.head = null;
        this.tail = null;
    }

    // Insert a new node at the beginning of the circular linked list
    public void insertAtBeginning(int data) {
        Node newNode = new Node(data);
        if (isEmpty()) {
            head = newNode;
            tail = newNode;
            tail.next = head; // Point tail's next to head to form the circular structure
        } else {
            newNode.next = head;
            head = newNode;
            tail.next = head; // Update tail's next to point to the new head
        }
    }

    // Insert a new node at the end of the circular linked list
    public void insertAtEnd(int data) {
        Node newNode = new Node(data);
        if (isEmpty()) {
            head = newNode;
            tail = newNode;
            tail.next = head; // Point tail's next to head to form the circular structure
        } else {
            tail.next = newNode;
            tail = newNode;
            tail.next = head; // Update tail's next to point back to head
        }
    }

    // Delete the first occurrence of a node with the given data from the circular linked list
    public void delete(int data) {
        if (isEmpty()) {
            System.out.println("Circular linked list is empty. Cannot delete.");
            return;
        }
        Node current = head;
        Node prev = null;
        do {
            if (current.data == data) {
                if (current == head) {
                    head = head.next;
                    tail.next = head; // Update tail's next to point to the new head
                    if (head == null) {
                        tail = null; // If the list becomes empty after deletion
                    }
                } else if (current == tail) {
                    tail = prev;
                    tail.next = head; // Update tail's next to point back to head
                } else {
                    prev.next = current.next;
                }
                return;
            }
            prev = current;
            current = current.next;
        } while (current != head); // Traverse until we reach the head again
        System.out.println("Node with data " + data + " not found in the circular linked list. Cannot delete.");
    }

    // Print the elements of the circular linked list
    public void display() {
        if (isEmpty()) {
            System.out.println("Circular linked list is empty.");
            return;
        }
        Node current = head;
        do {
            System.out.print(current.data + " ");
            current = current.next;
        } while (current != head); // Traverse until we reach the head again
        System.out.println();
    }

    // Check if the circular linked list is empty
    public boolean isEmpty() {
        return head == null;
    }

    public static void main(String[] args) {
        CircularLinkedList cll = new CircularLinkedList();
        cll.insertAtEnd(1);
        cll.insertAtEnd(2);
        cll.insertAtEnd(3);
        cll.insertAtBeginning(0);
        cll.display(); // Output: 0 1 2 3
        cll.delete(1);
        cll.display(); // Output: 0 2 3
    }
}

```

## Output
```
0 1 2 3 
0 2 3 
```












