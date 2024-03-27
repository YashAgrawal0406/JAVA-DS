# Topics
- [Topics](#Topics)
  - [Summary](#Summary)
  - [What is Tree Data Structure?](#What-is-Tree-Data-Structure)
  - [Tree Data Structure Terminologies](#Tree-Data-Structure-Terminologies)
  - [Properties of Trees in Data Structure](#Properties-of-Trees-in-Data-Structure)
  - [Implementation of Tree in Data Structure](#Implementation-of-Tree-in-Data-Structure)
  - [Types of Trees](#Types-of-Trees)
  - [References](#references)
 
## Summary
> A tree data structure organizes data hierarchically, comprising nodes connected by edges. The root stands atop, branching out to child nodes, each potentially having its own sub-nodes, creating a recursive pattern. In contrast, linear structures like arrays, linked lists, stacks, and queues arrange elements sequentially. The choice between these structures hinges on several factors. Firstly, the nature of the data dictates the optimal structure; certain data types may align better with specific structures. Secondly, operational efficiency matters; for frequent search operations on a list, sorted arrays facilitate swift binary searches by halving the search space. Lastly, memory efficiency is crucial; selecting a structure that conserves memory aligns with resource constraints. Therefore, the selection process balances hierarchical needs, operational speed, and memory utilization.

## What is Tree Data Structure?

<p align="center">
<img src="https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/9b2ee88f-ee1a-4d6d-8c91-3bf572bf6909" width="350" height="350"> 
</p>

- Let's understand some key points of the Tree data structure.
  - A tree data structure is defined as a collection of objects or entities known as nodes that are linked together to represent a hierarchy.
  - It's a non linear data structure as it does not store data in a sequential manner, but stores in a hierarchical fashion.
  - In the Tree data structure, the first node is known as a root node i.e. from which the tree originates. Each node contains some data and also contains references to child nodes. A root node can never have a parent node.

## Tree Data Structure Terminologies
> Tree is a hierarchical data structure that is defined as a collection of nodes. In a tree nodes represent the values and are connected by edges. Following are the terminologies and properties of a tree:
<p align="center">
<img src="https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/d0a4f64d-c5b8-4eb5-87ba-cfdfc479eb47" width="800" height="500"> 
</p>


<table>
  <tr>
    <th><B><I>Terminology</I></B></th> 
    <th><B><I>Description</I></B></th> 
    <th><B><I>Diagram</I></B></th>  
  </tr>
  <tr>
    <td>Root</td> 
    <td>Root node is a node from which the entire tree originates. It does not have a parent</td> 
    <td>Node A</td>  
  </tr>
  <tr>
    <td>Parent Node</td>
    <td>An immediate predecessor of any node is its parent node.</td>
    <td>B is parent of E & F</td>
  </tr>
  <tr>
    <td>Child Node</td>
    <td>All immediate successors of a node are its children. The relationship between the parent and child is considered as the parent-child relationship.</td>
    <td>F & E are children of B</td>
  </tr>
  <tr>
    <td>Leaf</td>
    <td>Node which does not have any child is a leaf. Usually the boundary nodes of a tree or last nodes of the tree are the leaf or collectively called leaves of the tree.</td>
    <td>E, F, J, K, H, I are the leaf nodes.</td>
  </tr>  
  <tr>
    <td>Edge</td>
    <td>Edge is the connection represented by a line between one node to another.In a tree with n nodes, there will be ‘n-1’ edges in a tree.</td>
    <td>Connecting line between A&B OR A&C OR B&F OR any other nodes connecting each other.</td>
  </tr>  
  <tr>
    <td>Siblings</td>
    <td>Siblings in real life means people with the same parents, similarly in the case of trees, nodes with common parents are considered to be siblings.</td>
    <td>H&I are siblings</td>
  </tr>  
  <tr>
    <td>Path</td>
    <td>Path is a number of successive edges from source node to destination node.</td>
    <td>A ,C, G, K is path from node A to K</td>
  </tr>  
  <tr>
    <td>Height of Node</td>
    <td>Height of a node represents the number of edges on the longest path between that node and a leaf.</td>
    <td>A, C, G, K form a height. Height of A is no. of edges between A and K,, which is 3. Similarly the height of G is 1 as it has just one edge until the next leaf node.</td>
  </tr>  
  <tr>
    <td>Levels of node</td>
    <td>Level of a node represents the generation of a node. If the root node is at level 0, then its next child node is at level 1, its grandchild is at level 2, and so on</td>
    <td>Level of H, I & J is 3. Level of D, E, F & G is 2</td>
  </tr>  
  <tr>
    <td>Degree of Node</td>
    <td>Degree of a node implies the number of child nodes a node has.</td>
    <td>Degree of D is 2 and of C is 3</td>
  </tr>  
  <tr>
    <td>Visiting</td>
    <td>When you’ve iterated or traversed to a specific node programmatically, accessing value or checking value of the current node is called visiting.</td>
    <td></td>
  </tr>  
  <tr>
    <td>Internal Node</td>
    <td>A node that has at least one child is known as an internal node.</td>
    <td>All the nodes except E, F, J, K, H, I are internal.</td>
  </tr>  
  <tr>
    <td>Traversing</td>
    <td>Traversing is a process of visiting each node in a specific order in a tree data structure.</td>
    <td>There are three types of traversals: inorder, preorder, postorder traversal.</td>
  </tr>  
  <tr>
    <td>Ancestor node</td>
    <td>An ancestor or ancestors to a node are all the predecessor nodes from root until that node. I.e. any parent or grandparent and so on of a specific node are its ancestors.</td>
    <td>A, C & G are ancestor to K and J nodes</td>
  </tr> 
    <tr>
    <td>`Descendant`</td>
    <td>Immediate successor of a node is its descendent.	</td>
    <td>K is descendent of G</td>
  </tr> 
    <tr>
    <td>Sub tree</td>
    <td>Descendants of a node represent subtree. Tree being a recursive data structure can contain many subtrees inside of it.</td>
    <td>Nodes B, E, F represent one subtree</td>
  </tr> 
</table>


## Properties of Trees in Data Structure
<p align="center">
<img src="https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/73fd7d9f-b917-412c-91c1-3e470602b78f" width="800" height="500">
</p>

- `Recursive Data Structure:`
  - a recursive method is the one that calls itself. Similarly a recursive data structure is the one that contains itself. A tree can be viewed as a recursive data structure, as even though a tree has only one root node, each node acts as a root node to another sub-tree. For example:
  - Following is a tree that has ‘A’ as the root node. Similarly if we look at ‘C’ node, that is another tree in itself. And the tree no 3 i.e. that starts with ‘D’ node is also a tree in itself. 
  - And that is how a tree contains multiple trees in itself, and this proves that it's a recursive data structure as a recursive data structure contains itself.

> [!NOTE]
> Even the leaf nodes are a tree in itself i.e. they can be seen from a perspective as trees without any child nodes.

- `Number of edges:`
  - If there are ‘n’ nodes in a tree then there would be n−1 edges. Each edge is the line-arrow connecting two nodes.

- `Depth of node x:`
  - Depth of a specific node x is defined as the length from root till this x node. One edge contributes to one unit in the length. Hence depth of a node x can also be considered as the number of nodes from root node till this x node.
  - Or depth of a node x can also be considered as the level L at which this node is, and adding 1 to it i.e. depth=L+1. It is because the first level starts with 0.

- `Height of node x:`
  - Height of a node represents the number of edges on the longest path between that node and a leaf.

## Implementation of Tree in Data Structure

<p align="center">
<img src="https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/f1feb278-9115-4d06-8f95-7dec50d1cb9f" width="800" height="500">
</p>

The above representation depicts what a tree looks like on a memory. According to it, each node consists of three fields.
Left part of the node consists of the memory address of the left child, the right part of the node consists of the memory address of the right child and the center part holds the data for this node.

Relating to the above representation, each node can be programmatically defined as a class as follows:
```Java
Class Node {
  public int value;
  public Node left;
  public Node right; 
}
```
Here `left` will contain the reference to the Node that has value which is just smaller to the value in the current Node. Similarly `right` will contain reference to the Node that has value greater than the current Node.

What we’re discussing here is in reference to a binary tree as a binary tree has two children (utmost). That means, either a node has `0, 1 or max 2` children. A generic tree can have more than 2 children as well.

## Types of Trees
`General tree:` 
- In the general tree, each node has either 0 or n number of nodes. In this tree, there is no limitation to the number of nodes. It starts with a root node and the children of the parent node make another general sub tree. Hence eachnode is a root of another sub-tree i.e. there can be `n number of subtrees in a general tree. All the subtrees are unordered in a general tree.

`Binary Tree:` 
- In a binary tree, each node can have at most 2 children (i.e. either 0, 1, 2). There is no restriction as to what data will be in the left child or right child.

`Binary Search Tree:` 
- A binary search tree just like a binary tree can have at most 2 children. It can have n nodes and also each node can be defined as a data part that holds the data, left child and the right node.
Left child holds reference to the node that contains data which is immediately lesser than the data in the current node and similarly the right child contains the reference to the node that contains data which is just greater than the data in the current node.
- Every node in the left subtree must contain a value less than the value of the root node, and the value of each node in the right subtree must be bigger than the value of the root node. 

`AVL Tree:`
- It can be considered as a binary tree and also a type of binary search tree. It satisfies features of both binary tree and binary search tree.
- It's a self balancing tree i.e. balancing heights of left subtree and right subtree. This balancing is measured by something called balancing factor.
- A tree is considered as an AVL tree if it satisfies properties of both a binary search tree and the balancing factor. Difference between the height of the left subtree and the right subtree is considered as the height of the AVL tree.The value of the balancing factor must be 0, 1 or -1 for each node in an AVL tree.

`Red Black Tree:`
- It is also a variant of a binary search tree. It's also a self balancing tree just like an AVL tree, the only difference is in an AVL tree, we do not have an idea as to how much rotations would be required to balance the tree but in a red black tree a maximum of two rotations are required to balance the tree. It contains a bit that represents the red or black color of the node to ensure the balancing of the tree.
And there are and can be more types of tree data structure, but these are the common tree data structures that one must know about.


## References
- [Scaler DS](https://www.scaler.com/topics/data-structures/tree-data-structure/)
- [Scaler Binary Tree](https://www.scaler.com/topics/data-structures/binary-tree-in-data-structure/)
- [Scaler Types of Trees in Data Structures](https://www.scaler.com/topics/types-of-trees-in-data-structure/)





