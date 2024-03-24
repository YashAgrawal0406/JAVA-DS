# Problems
- [Problems](#Problems)
    - [Push at bottom](#PushAtBottom)
    - [Reverse](#Reverse)
- [Links To Stack Problems](#Links-to-stack-problem)

## `PushAtBottom` 
1. Push a new item at the bottom of the stack

```Java
//Push to the bottom of the stack
import java.util.Stack;

public class Main {
    public static void pushAtBottom(int data, Stack<Integer> s){
        if(s.empty()) {
            s.push(data);
            return;
        }

        int top = s.pop();
        pushAtBottom(data,s);
        s.push(top);
    }
    public static void main(String[] args) {
        Stack<Integer> s = new Stack<Integer>();
        s.push(1);
        s.push(2);
        s.push(3);
        s.push(4);
        pushAtBottom(5,s);

        while (!s.isEmpty()) {
            System.out.println(s.peek());
            s.pop();
        }
    }
}
```
<br>

## `Reverse`
2. Reverse a given stack
> we will use push at bottom code and enhance it to reverse the stack

```Java
//Reverse a stack
import java.util.Stack;

public class Main {
    public static void pushAtBottom(int data, Stack<Integer> s){
        if(s.empty()) {
            s.push(data);
            return;
        }

        int top = s.pop();
        pushAtBottom(data,s);
        s.push(top);
    }

    public static void reverse(Stack<Integer> s)
    {
        if(s.isEmpty())
            return;
        int top = s.pop();
        reverse(s);
        pushAtBottom(top,s);
    }
    public static void main(String[] args) {
        Stack<Integer> s = new Stack<Integer>();

        s.push(1);
        s.push(2);
        s.push(3);
        s.push(4);

        reverse(s);

        while (!s.isEmpty()) {
            System.out.println(s.peek());
            s.pop();
        }
    }
}
```
<br>




## Links To Stack Problems
> [Links To Stack Problems](https://medium.com/techie-delight/stack-data-structure-practice-problems-and-interview-questions-9f08a35a7f19)
