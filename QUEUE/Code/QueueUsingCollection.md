# Topics
- [Topics](#Topics)
  - [Code](#Code)
    - [Queue Using Collection](#Queue-Using-Collection) 
  - [Output](#Output)

> This is the code for Queue data structure using `Collection Frameworks`
 
  ## Code
  ### Queue Using Collection
  ```Java
Queue<Integer> q = new LinkedList<Integer>();
q.add(1);
q.add(2);
q.add(3);
System.out.println("Using Linked Declaration" + q);
while(!q.isEmpty())
{
    System.out.println(q.remove());
}

Queue<Integer> q1 = new ArrayDeque<>();
q1.add(1);
q1.add(2);
q1.add(3);

System.out.println("Using ArrayDequeue Declaration : " + q1);
while(!q1.isEmpty())
{
    System.out.println(q1.remove());
}
```

## Output
```
Using Linked Declaration[1, 2, 3]
1
2
3
Using ArrayDequeue Declaration : [1, 2, 3]
1
2
3
```
