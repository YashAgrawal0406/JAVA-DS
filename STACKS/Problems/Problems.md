# Problems
- [Problems](#Problems)
    - [Push at bottom](#PushAtBottom)
    - [Reverse](#Reverse)
    - [Balanced Parathensis](#Balanced-Parathensis)
    - [Duplicate Parenthesis](#Duplicate-Parenthesis)
    - [Infix Prefix Postfix](#Infix-prefix-postfix)
    - [Infix to Prefix and Postfix Conversion](#Infix-to-Prefix-and-Postfix-Conversion)
        - [Infix to Prefix Conversion](#Infix-to-Prefix-Conversion)
        - [Infix to Postfix Conversion](#Infix-to-Postfix-Conversion)
    - [Prefix to Infix and Postfix Conversion](#Prefix-to-Infix-and-Postfix-Conversion)
        - [Prefix to Infix Conversion](#Prefix-to-Infix-Conversion)
        - [Prefix to Postfix Conversion](#Prefix-to-Postfix-Conversion) 
    - [Postfix to Infix and Prefix Conversion](#Postfix-to-Infix-and-Prefix-Conversion)
        - [Postfix to Infix Conversion](#Postfix-to-Infix-Conversion)
        - [Postfix to Prefix Conversion](#Postfix-to-Prefix-Conversion) 
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
- Infix Expressions   :  A + B 
    > if an expression has multiple operators with the same precedence, the evaluation of those operators occurs from left to right.

    <img src="https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/e6999f2e-a391-4563-b743-9621e28d5502" width="150" height="100">

- Prefix Expressions  :  + A B
    > We should consider that prefix expressions are evaluated from right to left. Thus, we apply each operator to its operands as it is encountered.

    <img src="https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/21688b77-d988-4ff7-8237-b338441afb27" width="150" height="100">

- Postfix Expressions :  A B +
    > we can evaluate postfix expressions from left to right, with each operator being applied to its operands as encountered.

    <img src="https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/2ae428e7-42ff-4ab0-b0c5-d6eaf60541fe" width="150" height="100">

## `Infix to Prefix and Postfix Conversion:`
### Infix to Prefix Conversion 
    - This function converts an infix expression to its equivalent prefix notation.
    - It processes the expression in reverse order to handle parentheses effectively.
    - Operands are appended directly to the result.
    - Operators are pushed onto a stack, and when encountering lower-precedence operators, they're popped and appended to the result until the stack is empty or an operator with lower precedence is encountered.
    - Finally, remaining operators on the stack are appended to the result.

### Infix to Postfix Conversion
    - This function converts an infix expression to its equivalent postfix notation.
    - It iterates through the infix expression from left to right.
    - Operands are directly appended to the result.
    - Operators are pushed onto a stack, and when encountering lower-precedence operators, they're popped and appended to the result until the stack is empty or an operator with lower precedence is encountered.
    - Parentheses are handled similarly to infix to prefix conversion.
    - Finally, remaining operators on the stack are appended to the result.

```Java
import java.util.Stack;

public class InfixToPrefixPostfix {
    // Function to determine operator precedence
    private static int precedence(char operator) {
        switch (operator) {
            case '+':
            case '-':
                return 1;
            case '*':
            case '/':
                return 2;
            case '^':
                return 3;
            default:
                return -1;
        }
    }

    // Function to convert infix expression to prefix expression
    public static String infixToPrefix(String infix) {
        StringBuilder prefix = new StringBuilder();
        Stack<Character> stack = new Stack<>();

        // Reverse the infix expression for easier processing
        for (char c : new StringBuilder(infix).reverse().toString().toCharArray()) {
            if (Character.isLetterOrDigit(c))
                prefix.append(c);
            else if (c == ')')
                stack.push(c);
            else if (c == '(') {
                while (!stack.isEmpty() && stack.peek() != ')')
                    prefix.append(stack.pop());
                stack.pop(); // Discard ')'
            } else {
                while (!stack.isEmpty() && precedence(c) < precedence(stack.peek()))
                    prefix.append(stack.pop());
                stack.push(c);
            }
        }

        // Pop remaining operators and append to prefix
        while (!stack.isEmpty())
            prefix.append(stack.pop());

        // Reverse the prefix expression to get the final result
        return prefix.reverse().toString();
    }

    // Function to convert infix expression to postfix expression
    public static String infixToPostfix(String infix) {
        StringBuilder postfix = new StringBuilder();
        Stack<Character> stack = new Stack<>();

        // Process each character in the infix expression
        for (char c : infix.toCharArray()) {
            if (Character.isLetterOrDigit(c))
                postfix.append(c);
            else if (c == '(')
                stack.push(c);
            else if (c == ')') {
                while (!stack.isEmpty() && stack.peek() != '(')
                    postfix.append(stack.pop());
                stack.pop(); // Discard '('
            } else {
                while (!stack.isEmpty() && precedence(c) <= precedence(stack.peek()))
                    postfix.append(stack.pop());
                stack.push(c);
            }
        }

        // Pop remaining operators and append to postfix
        while (!stack.isEmpty())
            postfix.append(stack.pop());

        return postfix.toString();
    }

    public static void main(String[] args) {
        String infix = "a+b*(c^d-e)^(f+g*h)-i";
        System.out.println("Infix: " + infix);
        System.out.println("Prefix: " + infixToPrefix(infix));
        System.out.println("Postfix: " + infixToPostfix(infix));
    }
}
```

## `Prefix to Infix and Postfix Conversion:`
### Prefix to Infix Conversion
    - This function converts a prefix expression to its equivalent infix notation.
    - It iterates through the prefix expression from right to left.
    - Operands are pushed onto a stack.
    - When encountering an operator, two operands are popped from the stack, combined with the operator inside parentheses, and pushed back onto the stack.
    - The result is the infix expression.

### Prefix to Postfix Conversion
    - This function converts a prefix expression to its equivalent postfix notation.
    - It follows a similar approach to prefix to infix conversion but constructs the postfix expression instead.

```Java
import java.util.Stack;

public class PrefixToInfixPostfix {
    // Function to convert prefix expression to infix expression
    public static String prefixToInfix(String prefix) {
        Stack<String> stack = new Stack<>();
        StringBuilder infix = new StringBuilder(prefix).reverse();

        // Process each character in the reversed prefix expression
        for (char c : infix.toString().toCharArray()) {
            if (Character.isLetterOrDigit(c))
                stack.push(Character.toString(c)); // Operand: push onto stack
            else {
                String operand1 = stack.pop(); // Pop operands
                String operand2 = stack.pop();
                String expression = "(" + operand1 + c + operand2 + ")"; // Create infix expression
                stack.push(expression); // Push infix expression onto stack
            }
        }

        return stack.pop(); // Infix expression is at the top of stack
    }

    // Function to convert prefix expression to postfix expression
    public static String prefixToPostfix(String prefix) {
        Stack<String> stack = new Stack<>();
        StringBuilder postfix = new StringBuilder();

        // Process each character in the reversed prefix expression
        for (char c : new StringBuilder(prefix).reverse().toString().toCharArray()) {
            if (Character.isLetterOrDigit(c))
                stack.push(Character.toString(c)); // Operand: push onto stack
            else {
                String operand1 = stack.pop(); // Pop operands
                String operand2 = stack.pop();
                stack.push(operand1 + operand2 + c); // Concatenate operands with operator and push onto stack
            }
        }

        // Pop remaining operands and append to postfix
        while (!stack.isEmpty())
            postfix.append(stack.pop());

        return postfix.toString(); // Reverse the postfix expression to get the final result
    }

    public static void main(String[] args) {
        String prefix = "-+a*b-cd";
        System.out.println("Prefix: " + prefix);
        System.out.println("Infix: " + prefixToInfix(prefix));
        System.out.println("Postfix: " + prefixToPostfix(prefix));
    }
}
```

## `Postfix to Infix and Prefix Conversion:`
### Postfix to Infix Conversion
    - This function converts a postfix expression to its equivalent infix notation.
    - It iterates through the postfix expression from left to right.
    - Operands are pushed onto a stack.
    - When encountering an operator, two operands are popped from the stack, combined with the operator inside parentheses, and pushed back onto the stack.
    - The result is the infix expression.

### Postfix to Prefix Conversion
    - This function converts a postfix expression to its equivalent prefix notation.
    - It follows a similar approach to postfix to infix conversion but constructs the prefix expression instead

```Java
import java.util.Stack;

public class PostfixToInfixPrefix {
    // Function to convert postfix expression to infix expression
    public static String postfixToInfix(String postfix) {
        Stack<String> stack = new Stack<>();

        // Process each character in the postfix expression
        for (char c : postfix.toCharArray()) {
            if (Character.isLetterOrDigit(c))
                stack.push(Character.toString(c)); // Operand: push onto stack
            else {
                String operand2 = stack.pop(); // Pop operands
                String operand1 = stack.pop();
                stack.push("(" + operand1 + c + operand2 + ")"); // Create infix expression and push onto stack
            }
        }

        return stack.pop(); // Infix expression is at the top of stack
    }

    // Function to convert postfix expression to prefix expression
    public static String postfixToPrefix(String postfix) {
        Stack<String> stack = new Stack<>();

        // Process each character in the postfix expression
        for (char c : postfix.toCharArray()) {
            if (Character.isLetterOrDigit(c))
                stack.push(Character.toString(c)); // Operand: push onto stack
            else {
                String operand2 = stack.pop(); // Pop operands
                String operand1 = stack.pop();
                stack.push(c + operand1 + operand2); // Concatenate operands with operator and push onto stack
            }
        }

        return stack.pop(); // Prefix expression is at the top of stack
    }

    public static void main(String[] args) {
        String postfix = "ab*cd-+";
        System.out.println("Postfix: " + postfix);
        System.out.println("Infix: " + postfixToInfix(postfix));
        System.out.println("Prefix: " + postfixToPrefix(postfix));
    }
}
```














## Links To Stack Problems
- [Medium](https://medium.com/techie-delight/stack-data-structure-practice-problems-and-interview-questions-9f08a35a7f19)
- [GeeksforGeeks](https://www.geeksforgeeks.org/top-50-problems-on-stack-data-structure-asked-in-interviews/)
