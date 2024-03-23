# Topics
- [Topics](#Topics)
  - [Code](#Code)
    - [Stack Using Array](#Stack-Using-Array) 
    - [Main](#Main) 
  - [Output](#Output)

> This is the code for Stack structure using `Array`

## Code
### Stack Using Array
```Java
static class Stack{
  static int arr[];
  static int size;
  static int top = -1;

  Stack(int n)
  {
      arr = new int[n];
      size = n;
  }

  static boolean isEmpty()
  {
      return top == -1;
  }

  static boolean isFull()
  {
      return top == size -1;
  }

  static void push(int data)
  {
      if(isFull())
      {
          System.out.println("is full");
          return;
      }

      top++;
      arr[top] = data;
  }
  
  static int pop()
  {
      if(isEmpty()) {
          System.out.println("is Empty");
          return -1;
      }

      int data = arr[top];
      top--;

      return data;
  }
}
```

### Main
```Java
Stack s = new Stack(5);
s.push(10);
s.push(20);
s.push(30);
s.push(40);
s.push(50);
s.push(60); //Trying to put 6 element

int x = s.top; // return the top element index
System.out.println("Top value is : " + s.top);
for (int i = 0; i <= x; i++) {
    System.out.println(s.pop());
}
System.out.println(s.pop()); //To check if the stack is empty
```

## Output
```
Stack is full
Top value is : 4
50
40
30
20
10
Stack is Empty
-1
```
