# Topics
- [Topics](#Topics)
  - [Code](#Code)
    - [Stack Using Arraylist](#Stack-Using-Arraylist) 
    - [Main](#Main) 
  - [Output](#Output)

> This is the code for Stack structure using `ArrayList`

## Code
### Stack Using ArrayList
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
### Main
```Java
Stack s = new Stack();
s.push(1);
s.push(2);
s.push(3);
s.push(4);

while (!s.isEmpty()) {
    System.out.println("Item at top is : " + s.peek());
    s.pop();
}
```

## Output
```
Item at top is : 4
Item at top is : 3
Item at top is : 2
Item at top is : 1
```
