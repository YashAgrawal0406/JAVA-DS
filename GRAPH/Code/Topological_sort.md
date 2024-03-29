# Topics
- [Topics](#Topics)
  - [Theory](#Theory)
  - [Explanation](#Explanation)
  - [Code](#Code)
  - [References](#References)


## Theory
> Topological sorting arranges vertices in a Directed Acyclic Graph (DAG) linearly, ensuring for every edge u-v, u precedes v. Crucially, this sorting is exclusive to DAGs; cyclic graphs defy this ordering. Integral to graph theory, the Topological Sort Algorithm finds applications in project scheduling, dependency management, and compiling. This method's exploration unveils its mechanics and real-world relevance, offering insights through examples. Understanding its principles is pivotal for leveraging its benefits across diverse fields and scenarios
 
What is Topological Sort?
> Essentially, topological sort is an algorithm which sorts a directed graph by returning an array or a vector, or a list, that consists of nodes where each node appears before all the nodes it points to.

> Here, we'll simply refer to it as an array, you can use a vector or a list too.

> Say we had a graph,
> ` a --> b --> c  `

> then the topological sort algorithm would return - [a, b, c]. Why? Because, a points to b, which means that a must come before b in the sort. b points to c, which means that b must come before c in the sort.

Let's look at a relatively more complex example.

<p align="center">
  <img src="https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/be9cffc3-c0cb-4053-b719-771a51437057"> 
</p>

> - What do you think the topological sort for this directed graph look like? Well, let's see. Initially, our return array/vector, or the sorted array/vector (array containing nodes of the graph in sorted order) is empty [].
> - Can we add 4 to the start of the sorted result? No! The algorithm states that if there are any nodes pointing to the current node, then they must be added first. So, if we want to add 4 to the sorted result, we must check out the node(s) that point to 4.
> - We can see that there are 2 nodes that can be added to the sorted result - 2, 3. Hold on, there is a node that points to them as well! So it all starts from the node with the value 1! Before we can add 2 or 3, we must add 1 because both the nodes (2, 3) have another node pointing to them, which means that neither of 2 or 3 can be added to the sorted result before 1.
> - So, the first element that will be added to our sorted result (array/vector / list) will definitely be 1 as it has no other nodes pointing to it. Our sorted result now looks like this [1]
> - Which nodes do we add next? The node '1' points to two nodes - 2, 3. Which must be added first when it looks like any can be added?


Peculiarity of Topological Sort
> - That's the thing about topological sort. In most sorting algorithms, you must have seen that there is only one way that the elements can be sorted. There are no two ways, or there aren't any options available.
> - However, in topological sorting, a particular graph can be sorted in multiple ways. Just like how we observed in the above example that after adding 1 into the sorted array, we have an option of adding either 2 or 3.
> - But, what must be noted is that since neither 2 nor 3 have a different priority, both of these values must be inserted in the sorted array, before moving on to any other node. Both the elements 2 and 3 have the same > - priority.
> - So now, the topologically sorted result of our example graph can either look like [1, 2, 3] or [1, 3, 2]. For the time being, you can select any one of those. We'll go with [1, 3, 2].
> - Can you guess what the next element must be inserted into our sorted result? Is it 5? As you can see, even though moving forward from the node with value 2, we can move to the node with value 5, but 5 has another node that points to it, and that is 4. Hence, 4 must be added before we add 5.
> - The result now looks like this [1, 3, 2, 4]. Remember that it can also look like this [1, 2, 3, 4], but currently, it can not look any other way.
> - After we have added the 4 elements, we can see that there's only one element remaining, and that is 5 so that is our last addition to the sorted result. Voila, you have topologically sorted a directed graph!
> - Let's formally define topological sorting, now that we have understood how it works.
> - A topological sort or topological ordering of a directed graph is a linear ordering of its vertices such that for every directed edge uv from vertex u to vertex v (u --> v), u comes before v in the ordering.
> - We've understood topological sorting and how it works, but how do we code it up? Let's discuss the algorithm for this sort.
> - But before we move on to that, let's take some slightly complicated graphs and try to find the sorted result (it could be another data structure that you prefer) for the same.

<p align="center">
<img src="https://github.com/YashAgrawal0406/JAVA-DS/assets/93816952/3e441217-9847-4366-b12c-10d28a2e1d63">
</p>


