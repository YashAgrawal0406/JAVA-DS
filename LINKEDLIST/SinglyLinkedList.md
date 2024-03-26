# Topics
- [Topics](#Topics)
  - [Explanation](#Explanation) 
  - [Code](#Code)
    - [Node Structure](#Node-Structure)
    - [Linked List](#Linked-List)
    - [Main](#Main)
  - [Output](#Output)
 
## Explanation 
> A singly linked list is a fundamental data structure that consists of a sequence of nodes, where each node stores a value and a reference (or pointer) to the next node in the sequence. Unlike arrays, linked lists do not have a fixed size, and their elements are not stored in contiguous memory locations. Instead, each node in a linked list can be allocated dynamically from the memory heap.

Here's a brief explanation of singly linked lists:

- `Node:`
  - Each node in a singly linked list contains two fields:
  - Value/Data: Holds the data or value associated with the node.
  - Next pointer: Points to the next node in the sequence.
  - The last node in the list typically has a null reference as its next pointer, indicating the end of the list.

- `Head Pointer:`
  - The head pointer points to the first node in the linked list.
  - It serves as the entry point or starting point for accessing the elements of the list.

- Basic Operations:
  - `Insertion:`
    - Elements can be inserted at the beginning, middle, or end of the list.
    - To insert a new node, the next pointer of the preceding node is updated to point to the new node, and the next pointer of the new node is set to point to the following node.
  - `Deletion:`
    - Elements can be deleted from the list by updating the next pointer of the preceding node to skip the node to be deleted.
  - `Traversal:`
    - To traverse a singly linked list, you start from the head pointer and follow the next pointers until you reach the end of the list (i.e., a null reference).
  - `Search:`
    - Searching for a specific value involves traversing the list and comparing each node's value until the target value is found or the end of the list is reached.

![image](https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/7e93f52c-2046-42d6-8e81-90d7f418f62c)



## Code
### Node Struture
```Java
public class Node {
    String data;
    Node next;

    Node(String data) {
        this.data = data;
        this.next = null;
        size++;
    }
}
```
### Linked List
```Java
//Linked list code

class LL {
    public class Node {
        String data;
        Node next;

        Node(String data) {
            this.data = data;
            this.next = null;
            size++;
        }
    }

    Node head;
    private int size;
    LL() {
        size = 0;
    }

    public void addFirst(String data) {
        Node newNode = new Node(data);
        newNode.next = head;
        head = newNode;
    }

    public void addLast(String data) {
        Node newNode = new Node(data);

        if (head == null) {
            head = newNode;
            return;
        }

        Node lastNode = head;
        while (lastNode.next != null) {
            lastNode = lastNode.next;
        }
        lastNode.next = newNode;
    }

    public void addInMiddle(int index, String data) {
        if (index > size || index < 0) {
            System.out.println("Invalid Index value");
            return;
        }
        //size++;

        Node newNode = new Node(data);

        if (head == null || index == 0) {
            newNode.next = head;
            head = newNode;
            return;
        }
        Node currNode = head;
        for (int i = 1; i < size; i++) {
            if (i == index) {
                Node nextNode = currNode.next;
                currNode.next = newNode;
                newNode.next = nextNode;
                break;
            }
            currNode = currNode.next;
        }
    }

    public void printList() {
        Node currNode = head;

        while (currNode != null) {
            System.out.print(currNode.data + " -> ");
            currNode = currNode.next;
        }
        System.out.println("null");
    }

    public void removeFirst() {
        if (head == null) {
            System.out.println("Empty List, nothing to delete");
            return;
        }

        head = head.next;
        size--;
    }

    public void removeLast() {
        if (head == null) {
            System.out.println("Empty List, nothing to delete");
            return;
        }

        size--;
        if (head.next == null) {
            head = null;
            return;
        }

        Node currNode = head;
        Node lastNode = head.next;

        while (lastNode.next != null) {
            currNode = currNode.next;
            lastNode = lastNode.next;
        }

        currNode.next = null;
    }

    public void removemiddle(int index)
    {
        if(head == null)
        {
            System.out.println("list is empty");
            return;
        }

        if(head.next == null)
        {
            head = null;
            return;
        }

        Node currNode = head;
        for(int i = 1; i < size;i++)
        {
            if(index == i)
            {
                Node nextNode = currNode.next;
                currNode.next = nextNode.next;
                nextNode.next = null;
                break;
            }
            else
                currNode =currNode.next;
        }
    }

    //iterative approach
    public void reverse()
    {
        if(head == null || head.next == null)
            return;

        Node prevNode = head;
        Node currNode = head.next;
        while(currNode != null){
            Node nextNode = currNode.next;
            currNode.next = prevNode;

            prevNode = currNode;
            currNode = nextNode;
        }

        head.next = null;
        head = currNode;
    }

    //Recusrive approach
    public Node recusriveReverse(Node head)
    {
        if(head == null || head.next == null) {
            return head;
        }

        Node newHead = recusriveReverse(head.next);
        head.next.next = head;
        head.next = null;

        return newHead;
    }
    public int getSize() {
        return size;
    }
}
```
### Main
```Java
public class Main {
    public static void main(String args[]) {

        LL list =new LL();
        list.addLast("1");
        list.addLast("2");
        list.addLast("3");
        list.addLast("4");
        System.out.println("Initial List");
        list.printList();

        System.out.println("Reverse");
        list.head = list.recusriveReverse(list.head);
        list.printList();

        System.out.println("Add in middle at index 2 value 10");
        list.addInMiddle(2,"10");
        list.printList();

        System.out.println("Remove from the start");
        list.removeFirst();
        list.printList();

        System.out.println("Remove from index 2");
        list.removemiddle(2);
        list.printList();
        //Important problems for LL
        //1. Problem 19 LeetCode  : Remove Nth node from end of the list
        //2. Problem 234 LeetCode : palindrome LinkedList
        //3. Problem 141 LeetCode : linkedList Cycle
        //Remove a cycle in LL
    }
}

```

## Output
```
Initial List
1 -> 2 -> 3 -> 4 -> null
Reverse
4 -> 3 -> 2 -> 1 -> null
Add in middle at index 2 value 10
4 -> 3 -> 10 -> 2 -> 1 -> null
Remove from the start
3 -> 10 -> 2 -> 1 -> null
Remove from index 2
3 -> 10 -> 1 -> null
```
