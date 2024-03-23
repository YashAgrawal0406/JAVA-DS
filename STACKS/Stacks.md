# Topics
- [Topics](#Topics)
  - [Explanation](#Explanation)
    - [Operations](#Operations)  
    - [Complexity](#Complexity)
    - [Application](#Application)
  - [Code](#Code)
  - [References](#references)


## Explanation

> A stack in data structure, following the Last In First Out (LIFO) principle, is a crucial linear data structure for sequential task completion. Imagine entering a crowded elevator last and exiting first; this mirrors stack behavior.Stack in data structure are essential linear data structures that adhere to the Last-In-First-Out (LIFO) principle, meaning the most recently added element is the first one to be removed. This structure is akin to a stack of plates, where only the top plate is accessible for removal or addition of a new plate.

> Stacks follow `LIFO`, which is `Last In, First Out` mechanism. Inserting an element is known as `push`, and deleting an element is known as `pop`

### Operations
- `isEmpty()`: Checks if the stack is empty.
- `push(T data)`: Adds an element to the top of the stack.
- `pop()`: Removes and returns the top element from the stack.
- `peek()`: Returns the top element of the stack without removing it.
- `search(T data)`: Returns the position of element form the top element (index starts form 1). if not found returns -1

### Complexity
- `isEmpty()`: O(1)
- `push(T data)`: O(1)
- `pop()`: O(1)
- `peek()`: O(1)
- `search(T data)`: O(n)

### Application 
- `Balancing of symbols:` Stack is used for balancing a symbol. For example, we have the following program: 
As we know, each program has an opening and closing braces; when the opening braces come, we push the braces in a stack, and when the closing braces appear, we pop the opening braces from the stack. Therefore, the net value comes out to be zero. If any symbol is left in the stack, it means that some syntax occurs in a program.
- `String reversal:` Stack is also used for reversing a string. For example, we want to reverse a "javaTpoint" string, so we can achieve this with the help of a stack.
First, we push all the characters of the string in a stack until we reach the null character.
After pushing all the characters, we start taking out the character one by one until we reach the bottom of the stack.
- `UNDO/REDO:` It can also be used for performing UNDO/REDO operations. For example, we have an editor in which we write 'a', then 'b', and then 'c'; therefore, the text written in an editor is abc. So, there are three states, a, ab, and abc, which are stored in a stack. There would be two stacks in which one stack shows UNDO state, and the other shows REDO state.
If we want to perform UNDO operation, and want to achieve 'ab' state, then we implement pop operation.
- `Recursion:` The recursion means that the function is calling itself again. To maintain the previous states, the compiler creates a system stack in which all the previous records of the function are maintained.
- `DFS(Depth First Search):` This search is implemented on a Graph, and Graph uses the stack data structure.
- `Backtracking:` Suppose we have to create a path to solve a maze problem. If we are moving in a particular path, and we realize that we come on the wrong way. In order to come at the beginning of the path to create a new path, we have to use the stack data structure.
- `Expression conversion:` Stack can also be used for expression conversion. This is one of the most important applications of stack. The list of the expression conversion is given below:
    - Infix to prefix
    - Infix to postfix
    - Prefix to infix
    - Prefix to postfix
    - Postfix to infix
- `Memory management:` The stack manages the memory. The memory is assigned in the contiguous memory blocks. The memory is known as stack memory as all the variables are assigned in a function call stack memory. The memory size assigned to the program is known to the compiler. When the function is created, all its variables are assigned in the stack memory. When the function completed its execution, all the variables assigned in the stack are released.


## Code
> [!NOTE]
> Use Arraylist for creation of stack in interview

```Java
public static class Stack {
    static ArrayList<Integer> list = new ArrayList<>();
    
    public static boolean isEmpty() {
        return list.size() == 0;
    }

    public static void push(int data) {
        list.add(data);
    }

    public static int pop() {
        if (list.isEmpty())
            return -1;
        
        int top = list.get(list.size() - 1);
        list.remove(list.size() - 1);
        return top;
    }

    public static int peek() {
        if (list.isEmpty())
            return -1;

        return list.get(list.size() - 1);
    }
}
```






