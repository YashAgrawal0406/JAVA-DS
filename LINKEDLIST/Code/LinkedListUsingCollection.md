# Topics
- [Topics](#Topics)
  - [Code](#Code)
    - [Linked Using Collection](#LinkedList-Using-Collection) 
  - [Output](#Output)

> This is the code for Linked List data structure using `Collection Frameworks`
 
## Code
### Linked Using Collection
```Java
import java.util.LinkedList;

public class Main {
    public static void main(String[] args) {
        LinkedList<String> list = new LinkedList<>();

        list.addFirst("a");
        list.addFirst("is");

        System.out.println(list);

        list.addFirst("This");

        System.out.println(list);

        list.addLast("list");
        System.out.println(list);

        //adds it to the last by default
        list.add("end");
        System.out.println(list);

        list.add(3,"Linked");
        System.out.println(list);

        System.out.println("Size : " + list.size());
        System.out.println(list);

    }
}
```

## Output
```
[is, a]
[This, is, a]
[This, is, a, list]
[This, is, a, list, end]
[This, is, a, Linked, list, end]
Size : 6
[This, is, a, Linked, list, end]

```
