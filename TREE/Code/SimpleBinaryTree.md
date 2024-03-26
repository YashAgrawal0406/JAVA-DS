# Topics
- [Topics](#Topics)
  - [Explanation](#Explanation)
    - [Complexity](#Complexity)     
  - [Code](#Code)
    - [Node Structure](#Node-Structure)
    - [Simple Binary Tree](#Simple-Binary-Tree)
    - [Main](#Main)
  - [Output](#Output)
  - [References](#References)
 

## Explanation
> A binary tree is a tree-type non-linear data structure with a maximum of two children for each parent. Every node in a binary tree has a left and right reference along with the data element. The node at the top of the hierarchy of a tree is called the root node.

> A binary tree is the specialized version of the General tree. A binary tree is a tree in which each node can have at most two nodes.

### Complexity
- Time complexity :- O(n)
- Space complexity :- O(n)


## Code
### Node Structure
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

### Simple Binary Tree
```Java
static class BinaryTree {
      static int idx = -1;

      public static Node buildTree(int[] nodes) {
          idx++;
          if (nodes[idx] == -1) {
              return null;
          }

          Node newNode = new Node(nodes[idx]);
          newNode.left = buildTree(nodes);
          newNode.right = buildTree(nodes);

          return newNode;
      }
  }

  public static void preorder(Node root) {
      if (root == null) {
          return;
      }
      System.out.print(root.data + " ");
      preorder(root.left);
      preorder(root.right);
  }

  public static void inorder(Node root) {
      if (root == null) {
          return;
      }
      inorder(root.left);
      System.out.print(root.data + " ");
      inorder(root.right);
  }

  public static void postorder(Node root) {
      if (root == null) {
          return;
      }
      postorder(root.left);
      postorder(root.right);
      System.out.print(root.data + " ");

  }

  public static void levelOrder(Node root) {
      if (root == null)
          return;

      Queue<Node> q = new LinkedList<>();
      q.add(root);
      q.add(null);

      while (!q.isEmpty()) {
          Node currNode = q.remove();
          if (currNode == null) {
              System.out.println();
              if (q.isEmpty())
                  break;
              else
                  q.add(null);
          } else {
              System.out.print(currNode.data + " ");
              if (currNode.left != null) {
                  q.add(currNode.left);
              }
              if (currNode.right != null) {
                  q.add(currNode.right);
              }
          }
      }

  }

  public static int countofNodes(Node root) {
      if (root == null)
          return 0;
      int leftnodes = countofNodes(root.left);
      int rightnodes = countofNodes(root.right);

      return leftnodes + rightnodes + 1;
  }

  public static int sumOfNodes(Node root) {
      if (root == null)
          return 0;

      int leftSum = sumOfNodes(root.left);
      int rightSum = sumOfNodes(root.right);

      return leftSum + rightSum + root.data;
  }

  public static int height(Node root) {
      if (root == null)
          return 0;

      int leftHeight = height(root.left);
      int rightHeight = height(root.right);

      int myHeight = Math.max(leftHeight, rightHeight) + 1;
      return myHeight;
  }

  //the time complexity here is O(n^2)
  public static int diameter(Node root) {
      if(root == null)
          return 0;

      int diam1 = diameter(root.left);
      int diam2 = diameter(root.right);
      int diam3 = height(root.left) + height(root.right) + 1;

      return Math.max(diam3,Math.max(diam1,diam2));
  }


  //the time complexity is O(n)
  public static class TreeInfo{
      int ht;
      int diam;

      TreeInfo(int ht,int diam)
      {
          this.ht = ht;
          this.diam = diam;
      }
  }

  public static TreeInfo diameter2(Node root){
      if(root == null)
      {
          return new TreeInfo(0,0);
      }

      TreeInfo left = diameter2(root.left);
      TreeInfo right = diameter2(root.right);

      int myHeight = Math.max(left.ht,right.ht) + 1;
      int diam1 = left.diam;
      int diam2 = right.diam;
      int diam3 = left.ht + right.ht + 1;

      int myDiam = Math.max(diam3,Math.max(diam1,diam2));
      TreeInfo myInfo = new TreeInfo(myHeight,myDiam);
      return myInfo;
  }

  public static boolean isIdentical(Node root,Node subRoot)
  {
      if(root == null && subRoot == null)
      {
          return true;
      }

      if(root == null || subRoot == null)
      {
          return false;
      }

      if(root.data == subRoot.data)
      {
          return isIdentical(root.left,subRoot.left) && isIdentical(root.right,subRoot.right);
      }
      return false;
  }

  public static boolean isSubtree(Node root,Node subRoot){
      if(subRoot == null)
      {
          return true;
      }

      if(root == null)
      {
          return false;
      }

      if(root.data == subRoot.data)
      {
          if(isIdentical(root,subRoot))
          {
              return true;
          }
      }
      return isSubtree(root.left,subRoot) || isSubtree(root.right,subRoot);
  }
}
```

### Main
```Java
public static void main(String[] args) {
    int nodes[] = {1, 2, 4, -1, -1, 5, -1, -1, 3, -1, 6, -1, -1};
        /*
                      1
                  /       \
                 2          3
               /   \      /    \
             4      5    -1     6
         */

    BinaryTree tree = new BinaryTree();
    Node root = tree.buildTree(nodes);

    System.out.println("\nPreorder Traversal");
    preorder(root);

    System.out.println("\n\nInorder Traversal");
    inorder(root);

    System.out.println("\n\nPostOrder Traversal");
    postorder(root);

    System.out.println("\n\nlevel Order Traversal");
    levelOrder(root);

    //count of the nodes in a tree
    System.out.println("\nCount of the nodes in tree is : ");
    System.out.println(countofNodes(root));

    System.out.println("\nSum of the nodes is : ");
    System.out.println(sumOfNodes(root));

    System.out.println("\nHeight of the tree is : ");
    System.out.println(height(root));

    System.out.println("\ndiameter of the tree is : ");
    System.out.println(diameter(root));

    System.out.println("\ndiameter of the tree in linear time is : ");
    TreeInfo myInfo = diameter2(root);
    System.out.println(myInfo.diam);

    System.out.println("\nSubtree of another tree");
    //https://leetcode.com/problems/subtree-of-another-tree/
    //Question : 572
    int subnodes[] = {2,4,-1,-1,5,-1,-1};
    BinaryTree tree1 = new BinaryTree();
    BinaryTree.idx = -1;
    Node subRoot = tree1.buildTree(subnodes);
    System.out.println(isSubtree(root,subRoot));

    //Homework
    //Sum of nodes at kth level
}
```

## Output
```
Preorder Traversal
1 2 4 5 3 6 

Inorder Traversal
4 2 5 1 3 6 

PostOrder Traversal
4 5 2 6 3 1 

level Order Traversal
1 
2 3 
4 5 6 

Count of the nodes in tree is : 
6

Sum of the nodes is : 
21

Height of the tree is : 
3

diameter of the tree is : 
5

diameter of the tree in linear time is : 
5

Subtree of another tree
true

```

