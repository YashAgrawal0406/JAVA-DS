# Topics
- [Topics](#Topics)
  - [Explanation](#Explanation) 
  - [Code](#Code)
    - [Node Structure](#Node-Structure)
    - [Linked List](#Linked-List)
    - [Main](#Main)
  - [Output](#Output)
 
## Explanation 
> A doubly linked list is a linear data structure similar to a singly linked list, but with the added capability of bidirectional traversal. In a doubly linked list, each node contains two pointers: one pointing to the previous node and one pointing to the next node in the sequence. This allows traversal of the list both forwards and backwards.

Here's a brief explanation of doubly linked lists:
- `Node:`
  - Each node in a doubly linked list contains three fields:
    - `Value:` Holds the data or value associated with the node.
    - `Next pointer:` Points to the next node in the sequence.
    - `Previous pointer:` Points to the previous node in the sequence.
  - The first node (head) typically has a null reference as its previous pointer, indicating the start of the list.
  - The last node (tail) typically has a null reference as its next pointer, indicating the end of the list.
- `Head and Tail Pointers:`
  - The head pointer points to the first node in the linked list.
  - The tail pointer points to the last node in the linked list.
  - Having both head and tail pointers facilitates efficient insertion and deletion operations at both ends of the list.
- Basic Operations:
  - `Insertion:`
    - Elements can be inserted at the beginning, middle, or end of the list.
    - To insert a new node, the next pointer of the preceding node and the previous pointer of the following node are updated to maintain the bidirectional linkage.
  - `Deletion:`
    - Elements can be deleted from the list by updating the next and previous pointers of the adjacent nodes to skip the node to be deleted.
  - `Traversal:`
    - Doubly linked lists support bidirectional traversal, allowing efficient traversal both forwards and backwards.
  - `Search:`
    - Searching for a specific value involves traversing the list in either direction and comparing each node's value until the target value is found or the end of the list is reached.
- `Advantages:`
  - Bidirectional traversal: Doubly linked lists allow traversal of the list in both forward and backward directions, making operations like reverse traversal and deletion of the last element efficient.
  - Efficient insertion and deletion at both ends: Insertion and deletion operations at both the beginning and end of the list can be performed in constant time.
  - Flexibility: Doubly linked lists provide flexibility in managing data structures and implementing algorithms that require bidirectional access.
- `Disadvantages`:
  - Increased memory overhead: Each node in a doubly linked list requires additional memory to store both next and previous pointers, which increases memory overhead compared to singly linked lists.
  - More complex implementation: Maintaining bidirectional linkage adds complexity to the implementation and requires careful handling of edge cases.


![image](https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/46a06a28-c6ef-4da1-a78f-6c98fdcbaba0)

