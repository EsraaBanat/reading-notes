# Stacks and Queues

## **Stacks**

**Stack:** is a data structure that consists of Nodes. Each Node references the next Node in the stack, but does not reference its previous.

### Common terminology for a stack is:

1. `Push` - Nodes or items that are put into the stack are pushed
2. `Pop` - Nodes or items that are removed from the stack are popped. When you attempt to pop an empty stack an exception will be raised.
3. `Top` - This is the top of the stack.
4. `Peek` - When you peek you will view the value of the top Node in the stack. When you attempt to peek an empty stack an exception will be raised.
5. `IsEmpty` - returns true when stack is empty otherwise returns false.

### Stacks follow these concepts:

**FILO**

**F**irst **I**n **L**ast **O**ut

This means that the first item added in the stack will be the last item popped out of the stack.

**LIFO**

**L**ast **I**n **F**irst **O**ut

This means that the last item added to the stack will be the first item popped out of the stack.

![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-10/resources/images/stack1.PNG)

**Push O(1)**

Pushing a Node onto a stack will always be an O(1) operation. This is because it takes the same amount of time no matter how many Nodes (n) you have in the stack.

When adding a Node, you push it into the stack by assigning it as the new top, with its next property equal to the original top.

**Pop O(1)**

Popping a Node off a stack is the action of removing a Node from the top. When conducting a pop, the top Node will be re-assigned to the Node that lives below and the top Node is returned to the user.

Typically, you would check isEmpty before conducting a pop. This will ensure that an exception is not raised. Alternately, you can wrap the call in a try/catch block.

**Peek O(1)**

When conducting a peek, you will only be inspecting the top Node of the stack.

Typically, you would check isEmpty before conducting a peek. This will ensure that an exception is not raised. Alternately, you can wrap the call in a try/catch block.

## **Queue**

Common terminology for a queue is:

1. `Enqueue` - Nodes or items that are added to the queue.
2. `Dequeue` - Nodes or items that are removed from the queue. If called when the queue is empty an exception will be raised.
3. `Front` - This is the front/first Node of the queue.
4. `Rear` - This is the rear/last Node of the queue.
5. `Peek` - When you peek you will view the value of the front Node in the queue. If called when the queue is empty an exception will be raised.
6. `IsEmpty` - returns true when queue is empty otherwise returns false.

Queue is FIFO and LILO

**Enqueue O(1)**

When you add an item to a queue, you use the enqueue action. This is done with an O(1) operation in time because it does not matter how many other items live in the queue (n); it takes the same amount of time to perform the operation.

**Dequeue O(1)**

When you remove an item from a queue, you use the dequeue action. This is done with an O(1) operation in time because it doesn’t matter how many other items are in the queue, you are always just removing the front Node of the queue.

Typically, you would check isEmpty before conducting a dequeue. This will ensure that an exception is not raised. Alternately, you can wrap the call in a try/catch block.

**Peek O(1)**

When conducting a peek, you will only be inspecting the front Node of the queue.

Typically, you want to check isEmpty before conducting a peek. This will ensure that an exception is not raised. Alternately, you can wrap the call in a try/catch block.

## References

## [Stacks and Queues](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-10/resources/stacks_and_queues.html)



## [Back To Home Page](../../README.md)
