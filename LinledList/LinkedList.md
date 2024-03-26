# Topics
- [Topics](#Topics)
  - [Explanation](#Explanation) 
  - [Code](#Code)
    - [Node Structure](#Node-Structure)
    - [Linked List](#Linked-List)
    - [Main](#Main)
  - [Output](#Output)
 



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
