# Topics
- [Topics](#Topics)
  - [Code](#Code)
    - [Node Structure](#Node-Structure)
    - [Stack Using Lisked List](#Stack-Using-LinkedList) 
    - [Main](#Main) 
  - [Output](#Output)

> This is the code for Stack structure using `Linked List`

## Code
### Node Structure
```Java
static class Node{
    int data;
    Node next;
  
    public Node(int data)
    {
        this.data = data;
        this.next = null;
    }
}
```

### Stack Using Lisked List
```Java
 static class Stack{
    public static Node head;
    public static boolean isEmpty()
    {
        return head == null;
    }
    public static void push(int data)
    {
        Node newNode = new Node(data);
        if(isEmpty())
        {
            head = newNode;
            return;
        }
        newNode.next = head;
        head = newNode;

    }

    public static int pop()
    {
        if(isEmpty())
        {
            return -1;
        }
        int top = head.data;
        head = head.next;
        return top;
    }

    public static int peek()
    {
        if(isEmpty())
            return -1;

        return head.data;
    }
}
```
### Main
```Java
Stack s = new Stack();
s.push(1);
s.push(2);
s.push(3);
s.push(4);

while(!s.isEmpty())
{
    System.out.println("Element on top is : " + s.peek());
    s.pop();
}

```

## Output
```
Element on top is : 4
Element on top is : 3
Element on top is : 2
Element on top is : 1
```
