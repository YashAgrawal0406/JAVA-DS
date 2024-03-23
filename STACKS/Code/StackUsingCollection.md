# Topics
- [Topics](#Topics)
  - [Code](#Code)
  - [Output](#Output)

> This is a code for Stack data struture implementation using the inbuild stack collection framework provided by Java
## Code
```Java
import java.util.Stack;

public class Main {
    public static void main(String[] args) {
        Stack<Integer> s = new Stack<Integer>();

        s.push(1);
        s.push(2);
        s.push(3);
        s.push(4);
        s.push(5);
        System.out.println("Size of stack is : " + s.size());
        System.out.println("Position of stack is : " + s.search(6));

        while (!s.isEmpty()) {
            System.out.println("Element at top of stack before pop is : " + s.peek());
            s.pop();
        }
    }
}
```

## Output
```
Size of stack is : 5
Position of stack is : -1
Pop top element : 5
Peek top element : 4
Element at top of stack before pop is : 4
Element at top of stack before pop is : 3
Element at top of stack before pop is : 2
Element at top of stack before pop is : 1
```
