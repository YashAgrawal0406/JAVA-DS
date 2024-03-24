# Problems
- [Problems](#Problems)
    - [Push at bottom](#PushAtBottom)
    - [Reverse](#Reverse)
    - [Balanced Parathensis](#Balanced-Parathensis)
    - [Duplicate Parenthesis](#Duplicate-Parenthesis)
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
import java.util.Stack;
 
class Main
{
    // Function to find duplicate parenthesis in an expression
    public static boolean hasDuplicateParenthesis(String exp)
    {
        if (exp == null || exp.length() <= 3) {
            return false;
        }
 
        // take an empty stack of characters
        Stack<Character> stack = new Stack<>();
 
        // traverse the input expression
        for (char c: exp.toCharArray())
        {
            // if the current char in the expression is not a closing parenthesis
            if (c != ')') {
                stack.push(c);
            }
            // if the current char in the expression is a closing parenthesis
            else {
                // if the stack's top element is an opening parenthesis,
                // the subexpression of the form ((exp)) is found
                if (stack.peek() == '(') {
                    return true;
                }
 
                // pop till '(' is found for current ')'
                while (stack.peek() != '(') {
                    stack.pop();
                }
 
                // pop '('
                stack.pop();
            }
        }
 
        // if we reach here, then the expression does not have any
        // duplicate parenthesis
        return false;
    }
 
    public static void main(String[] args)
    {
        String exp = "((x+y))";        // assumes valid expression
 
        if (hasDuplicateParenthesis(exp)) {
            System.out.println("The expression has duplicate parenthesis.");
        }
        else {
            System.out.println("The expression does not have duplicate parenthesis");
        }
    }
}
```
<br>

## `Infix Prefix Postfix`
Infix Expressions   :  A + B 
> if an expression has multiple operators with the same precedence, the evaluation of those operators occurs from left to right.

<img src="https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/e6999f2e-a391-4563-b743-9621e28d5502" width="150" height="100">

Prefix Expressions  :  + A B
> We should consider that prefix expressions are evaluated from right to left. Thus, we apply each operator to its operands as it is encountered.

<img src="https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/21688b77-d988-4ff7-8237-b338441afb27" width="150" height="100">

Postfix Expressions :  A B +
> we can evaluate postfix expressions from left to right, with each operator being applied to its operands as encountered.

<img src="https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/2ae428e7-42ff-4ab0-b0c5-d6eaf60541fe" width="150" height="100">





















## Links To Stack Problems
- [Medium](https://medium.com/techie-delight/stack-data-structure-practice-problems-and-interview-questions-9f08a35a7f19)
- [GeeksforGeeks](https://www.geeksforgeeks.org/top-50-problems-on-stack-data-structure-asked-in-interviews/)
