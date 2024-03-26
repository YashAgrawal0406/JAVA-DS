# Topics
- [Topics](#Topics)
  - [Explanation](#Explanation)
  - What is Tree Data Structure?
  - Tree Data Structure Terminologies
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
