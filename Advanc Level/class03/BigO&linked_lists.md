# Big O Notation :

- Big O: The worst case analysis of algorithm efficiency,  is used to describe the efficiency of an algorithm or function. This efficiency is evaluated based on 2 factors:
- Running Time: The amount of time required for an algorithm to complete.
- Memory Space: The amount of memory resources required for an algorithm to complete.
- Input Size: Represented by the variable n, the total size of values used as parameters in an algorithm.
- Big Omega: The best case analysis of algorithm efficiency.
- Big Theta: The typical or random case used for analysis of algorithm efficiency.


# Linked Lists :

- A Linked List is a sequence of Nodes that are connected/linked to each other. The most defining feature of a Linked List is that each Node references the next Node in the link.

There are two types of Linked List - Singly and Doubly:


 - A Singly linked list means that there is only one reference, and the reference points to the Next node in a linked list
- A Doubly linked list means that there is a reference to both the Next and Previous node.


![single Linked List](./LinkedList1.png)
single linked list

### Terminology :

- Node - Nodes are the individual items/links that live in a linked list. Each node contains the data for each link.
- Next - Each node contains a property called Next. This property contains the reference to the next node.
- Head - The Head is a reference of type Node to the first node in a linked list.
- Current - The Current is a reference of type Node to the node that is currently being looked at. When traversing, you create a new Current variable at the Head to guarantee you are starting from the beginning of the linked list.

 ### Linear and non-linear data structures:

-  linear data structures, which means that there is a sequence and an order to how they are constructed and traversed

- In non-linear data structures, items don’t have to be arranged in order, which means that we could traverse the data structure non-sequentially

![](linear%26nonlinear%20datastructures.jpeg)

### Arrays and Linked lists :

The fundamental difference between arrays and linked lists is that arrays are static data structures, while linked lists are dynamic data structures. A static data structure needs all of its resources to be allocated when the structure is created; this means that even if the structure was to grow or shrink in size and elements were to be added or removed, it still always needs a given size and amount of memory.

On the other hand, a dynamic data structure can shrink and grow in memory. It doesn’t need a set amount of memory to be allocated in order to exist, and its size and shape can change, and the amount of memory it needs can change as well.

![](https://miro.medium.com/max/1400/1*G43FVT5xJ1n1QDKVNZUxXQ.jpeg)

>A node only knows about what data it contains, and who its neighbor is.

![](https://miro.medium.com/max/1400/1*cUehR5S18XSoVLaPNfNzlA.jpeg)

If you ever find yourself having to do something that requires a lot of traversal, iteration, or quick index-level access, a linked list could be your worst enemy. In those situations, an array might be a better solution, since you can find things quickly (a single chunk of allocated memory), and you can use an index to quickly retrieve a random element in the middle or end of the list without having to take the time to traverse through the whole entire thing.

### Growing a linked list :
<br>

![](https://miro.medium.com/max/1400/1*Jy5tjwrMdtpGl2ceq4f94A.jpeg)


## References :

[Big O : Analysis of Algorithm Efficiency](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-05/resources/big_oh.html)

[Linked Lists](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-05/resources/singly_linked_list.html)

[What’s a Linked List, Anyway pt1](https://medium.com/basecs/whats-a-linked-list-anyway-part-1-d8b7e6508b9d)

[What’s a Linked List, Anyway pt2](https://medium.com/basecs/whats-a-linked-list-anyway-part-2-131d96f71996)


## [Back To Home Page](../../README.md)