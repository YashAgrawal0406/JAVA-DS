# Topics
- [Topics](#Topics)
  - [Explanation](#Explanation)
    - [Complexity](#Complexity)     
  - [Code](#Code)
    - [Node Structure](#Node-Structure)
    - [Binary Search Tree](#Binary-Search-Tree)
    - [Main](#Main)
  - [Output](#Output)
  - [References](#References)


## Explanation 
> A binary search tree shares similarities with a binary tree but has specific limitations.The value of the left child in a binary search tree is always smaller than that of the parent node, and the value of the right child is larger than that of the parent node in the binary search tree. This property makes the binary search tree optimal for search operations.

### Complexity
- Search (Find):
  - Best Case (Balanced Tree): O(log n)
  - Worst Case (Unbalanced Tree): O(n)
- Insertion:
  - Best Case (Balanced Tree): O(log n)
  - Worst Case (Unbalanced Tree): O(n)
- Deletion:
  - Best Case (Balanced Tree): O(log n)
  - Worst Case (Unbalanced Tree): O(n)
- Traversal (In-order, Pre-order, Post-order):
-   Time complexity for all traversal operations: O(n), as each node is visited once.
- Minimum/Maximum Finding:
  - Best Case (Balanced Tree): O(log n)
  - Worst Case (Unbalanced Tree): O(n)


## Code
### Node structure
```Java
static class Node {
    int data;
    Node left;
    Node right;

    Node(int data) {
        this.data = data;
        this.left = null;
        this.right = null;
    }
}
```


### Binary Search Tree
```Java
//This file contains operations related to binary search tree.
//Also some questions around BST

import java.util.ArrayList;

public class Main {

    static class Node {
        int data;
        Node left;
        Node right;

        Node(int data) {
            this.data = data;
            this.left = null;
            this.right = null;
        }
    }

    public static Node insert(Node root, int val) {
        if (root == null) {
            root = new Node(val);
            return root;
        }

        if (root.data > val) {
            //leftsubtree
            root.left = insert(root.left, val);
        } else {
            root.right = insert(root.right, val);
        }
        return root;
    }

    public static void printInorder(Node root) {
        if (root == null)
            return;

        printInorder(root.left);
        System.out.print(root.data + " ");
        printInorder(root.right);
    }

    public static boolean search(Node root, int key) {
        if (root == null) {
            return false;
        }

        if (root.data == key) {
            return true;
        }

        if (root.data > key) {
            return search(root.left, key);
        } else {
            return search(root.right, key);
        }
    }

    public static Node delete(Node root, int val) {
        if(root == null)
        {
            return root;
        }

        if (root.data > val) {
            root.left = delete(root.left, val);
        }
        else if (root.data < val) {
            root.right = delete(root.right, val);
        }
        else //root.data == val
        {
            //case 1
            //has no child
            if (root.left == null && root.right == null) {
                return null;
            }

            //case 2
            //has only one child
            {
                if (root.left == null) {
                    return root.right;
                } else if (root.right == null) {
                    return root.left;
                }
            }

            //case 3
            //has both the children
            // here we will find the inorder successor of the node that is to be deleted
            //i.e. left most node in right subtree of the item that is to be deleted
            //then we perform a delete operation on the successor that has been used
            Node IS = inorderSuccessor(root.right);
            root.data = IS.data;
            root.right = delete(root.right, IS.data);
        }
        return root;
    }

    public static Node inorderSuccessor(Node root) {
        if (root.left == null)
            return root;

        return inorderSuccessor(root.left);
    }


    public static void printInRange(Node root, int low, int high) {
        if (root == null)
            return;

        if (low <= root.data && root.data <= high){ //if root.data is in range
            printInRange(root.left, low, high);
            System.out.print(root.data + " ");
            printInRange(root.right, low, high);
        } else if (root.data >= high) { //if root.data is greater than the range highest value
            printInRange(root.left, low, high);
        } else { // anything else will call right subtree
            printInRange(root.right, low, high);
        }

    }

    public static void printPath(ArrayList<Integer> path)
    {
        for (int i = 0; i < path.size(); i++) {
            System.out.print(path.get(i) + "->");
        }
        System.out.println();
    }
    public static void printRoot2AllLeaf(Node root, ArrayList<Integer> path){
        if(root == null)
            return;

        path.add(root.data);
        if(root.left == null && root.right == null)
        {
            printPath(path);
        }

        else {
            printRoot2AllLeaf(root.left, path);
            printRoot2AllLeaf(root.right, path);
        }
        
        path.remove(path.size() - 1);
        return;
    }
}
```

### Main
```Java
public static void main(String[] args) {
    int[] values = {8, 5, 3, 1, 4, 6, 10, 11, 14};
    Node root = null;

    for (int i = 0; i < values.length; i++) {
        root = insert(root, values[i]);
    }

    //inorder print is always sorted print in BST
    System.out.println("\nInOrder Traversal");
    printInorder(root);
    System.out.println();

    //Search an element in BST
    System.out.println("\nSearch Element with value 10");
    if (search(root, 10)) {
        System.out.println("FOUND!! 😊"); //for smile use windows + colon
    } else {
        System.out.println("NOT FOUND !! 🥲");
    }

    //Delete an element in BST
    System.out.println("\nDelete an element in BST : ");
    root = delete(root,15);
    printInorder(root);

    //Print the element in the given range
    System.out.println("\n\nPrint in range 3 to 11");
    printInRange(root, 3, 11);

    //print all the paths from root to leaf nodes
    System.out.println("\n\nPrint all paths from Root to leaf");
    printRoot2AllLeaf(root,new ArrayList<Integer>());
}
```

## Output
```
InOrder Traversal
1 3 4 5 6 8 10 11 14 

Search Element with value 10
FOUND!! 😊

Delete an element in BST : 
1 3 4 5 6 8 10 11 14 

Print in range 3 to 11
3 4 5 6 8 10 11 

Print all paths from Root to leaf
8->5->3->1->
8->5->3->4->
8->5->6->
8->10->11->14->
```


## Refernces
- [Binary Search tree scaler](https://www.scaler.com/topics/data-structures/binary-search-tree/)

