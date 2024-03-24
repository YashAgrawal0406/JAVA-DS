# Problems
- [Problems](#Problems)
    - [Push at bottom](#PushAtBottom)
    - [Reverse](#Reverse)
    - [Balanced Parathensis](#Balanced-Parathensis)
    - [Duplicate Parenthesis](Duplicate-Parenthesis)
- [Links To Stack Problems](#Links-to-stack-problems)

## `PushAtBottom` 
Push a new item at the bottom of the stack

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
Reverse a given stack
> We will use pushatbottom code and enhance it to reverse the stack

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

## `Balanced Parathensis`
Given a string containing opening and closing braces, check if it represents a balanced expression or not.
```Java
import java.util.Stack;
 
class Main
{
    // Function to check if the given expression is balanced or not
    public static boolean isBalanced(String exp)
    {
        // base case: length of the expression must be even
        if (exp == null || exp.length() % 2 == 1) {
            return false;
        }
 
        // take an empty stack of characters
        Stack<Character> stack = new Stack<>();
 
        // traverse the input expression
        for (char c: exp.toCharArray())
        {
            // if the current character in the expression is an opening brace,
            // push it into the stack
            if (c == '(' || c == '{' || c == '[') {
                stack.push(c);
            }
 
            // if the current character in the expression is a closing brace
            if (c == ')' || c == '}' || c == ']')
            {
                // return false if a mismatch is found (i.e., if the stack is empty,
                // the expression cannot be balanced since the total number of opening
                // braces is less than the total number of closing braces)
                if (stack.empty()) {
                    return false;
                }
 
                // pop character from the stack
                Character top = stack.pop();
 
                // if the popped character is not an opening brace or does not pair
                // with the current character of the expression
                if ((top == '(' && c != ')') || (top == '{' && c != '}')
                        || (top == '[' && c != ']')) {
                    return false;
                }
            }
        }
 
        // the expression is balanced only when the stack is empty at this point
        return stack.empty();
    }
 
    public static void main(String[] args)
    {
        String exp = "{()}[{}]";
 
        if (isBalanced(exp)) {
            System.out.println("The expression is balanced");
        }
        else {
            System.out.println("The expression is not balanced");
        }
    }
}
```
<br>

## `Duplicate Parenthesis`
Given a balanced expression that can contain opening and closing parenthesis, check if it contains any duplicate parenthesis or not.

> `Examples` <br>
> Input:  ((x+y))+z <br>
> Output: true <br>
> Explanation: Duplicate () found in subexpression ((x+y)) <br>

> Input:  (x+y) <br>
> Output: false <br>
> Explanation: No duplicate () is found <br>
>
> Input:  ((x+y)+((z))) <br>
> Output: true <br>
> Explanation: Duplicate () found in subexpression ((z)) <br>

> `Explanation` <br>
> We can use a stack to solve this problem. The idea is to traverse the given expression and
> - If the current character in the expression is not a closing parenthesis ')', push the character into the stack.
> - If the current character in the expression is a closing parenthesis ')', check if the topmost element in the stack is an opening parenthesis or not. If it is an opening parenthesis, then the subexpression ending at the current character is of the form ((exp)); otherwise, continue popping characters from the stack till matching '(' is found for current ')'.

```Java
```
## Links To Stack Problems
> [Links To Stack Problems](https://medium.com/techie-delight/stack-data-structure-practice-problems-and-interview-questions-9f08a35a7f19)
