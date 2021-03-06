# Data Structures Notes

**ADT** - abstract data type 

## Queues

A **queue** is a list or collection with the restriction that insertion can be performed at one end (rear) and deletion can be performed at other end (front)

#### Operations 
- enqueue(x) or push(x) - Insert

- dequeue(x) or pop(x) - Delete 

- front() or peek() - Look at what’s in front without deleting anything

- isempty() - Check whether queue is empty or not 

#### Time complexity
Constant time or O(1)


#### What are the use cases of queue data structure?
Queue is most often used in a scenario where there is a shared resource that’s supposed to serve some requests but the resource can handle only one request at a time. In such a scenario, it makes most sense to queue up the requests. The request that comes first, gets served first. Let’s say we have a printer shared in a network... any machine in the network can send a print request to this printer. Printer can serve only one request at a time. It can print only one document at a time. So if a request comes, and it’s busy, it can’t be like “I’m busy, request later” ... what happens is that the program that manages the printer puts the print request in a queue. As long as there is something in the queue, the printer keeps picking up a request from the front of the queue and serves it. 

The processor on your computer is also a shared resource. A lot of running programs or processors need time of the processor but the processor can only attend to only one process at a time. Processor has to execute all the instructions, and has to perform all the arithmetic and logical operations. So the processes are put in a queue. 

Queues can be used to simulate wait in a number of scenarios 

#### Resources
- https://www.youtube.com/watch?v=XuCbpw6Bj1U&list=PL2_aWCzGMAwI3W_JlcBbtYTwiQSsOTa6P&index=22
- https://www.youtube.com/watch?v=okr-XE8yTO8&list=PL2_aWCzGMAwI3W_JlcBbtYTwiQSsOTa6P&index=23 (haven't watched)


## Stacks

#### Stack ADT

When we talk about data structures as abstract data types, we talk only about features or operations available within the data structure, not implementation details. We define the data structure only as a mathematical or logical model

A **stack** is a list or collection with the restriction that an insertion or deletion can only be performed from one end, that we call the top of stack. Only the top of the stack is accessible. Stack is also called last in, first out collection. An element that is pushed or inserted last into a stack is popped or removed first.

Stack examples in the real world 
- stack of plates
- Pack of tennis balls 

#### Operations 
- push(x) - Insertion
- pop() - Deletion
- top() - Returns the element at the top of the stack
- isempty() - Returns true if stack is empty

#### Time complexity
constant time or O(1)


#### What are the real world applications of stack?

Stack data structure is used for the execution of function calls in a program. Stack is also used for recursion, which is a chain of function calls - it’s just that all the calls are to the same function. 

Another application of stack is that we can use it to implement an undo operation in an editor. 

Stack is used in a number of important algorithms. For example, a complainer verifies whether parentheses in a source code are valid or not using stack data structure. Corresponding to each opening curly brace, or each opening parentheses in a source code, there must be a closing parentheses at the appropriate position. And if the parentheses in a source code are not put properly, the compiler should throw an error and this check can be performed using a stack 

#### Resources
- https://www.youtube.com/watch?v=F1F2imiOJfk&list=PL2_aWCzGMAwI3W_JlcBbtYTwiQSsOTa6P&index=14


## Linked lists 
A **linked list** is a sequence of elements where each element links to the next element which links to the next element 
Every node has 2 parts: data and a pointer to the next node


#### Operations
- get_size() - We keep a variable in linked list that tracks the size of the list. get_size() returns that size variable 
- find(data) - Start at the root. Compare the value that we’re searching for to the data in the first node, then go to the next until we find the matching value and return that value. If the value is not in the list, return null or false.
- add(data) - If we want to add data, we create a new node, and change the next pointer so that it points to the root node, and then we’ll change the root node so that it points to our new node
- remove(data) - First we have to find the data to remove. We’ll start at the first node and make the comparison. If it’s not equal, we go to the next node. Once we’ve found the correct node, we can change the next pointer in the previous node to the next node of the node you’re trying to remove. The node you’re trying to delete is still there but it’s excluded from the linked list 

#### Advantages of linked lists 
- insertions and deletions are quick (constant time if appending an element to beginning of list, linear time if appending to end of list)

#### Disadvantages of linked lists
- slow to get to nth element (linear time)


#### Doubly linked list 
A **doubly linked** list is just like a singly linked list but in addition to each element having a link to the next element, each element also links to the previous element 

#### The node has three fields:
- prev
- data
- next

#### Operations
- insertion
- deletion
- traversal


#### What are the advantages or use cases of a doubly linked list?
- Forward and reverse lookup 
- Deletion is easier. In a singly liked list, to delete a node, you will need two pointers - one to the node to be deleted and one to the previous node. In a doubly linked list, we can delete a node using only one pointer - a pointer to the node to be deleted 

#### What are the disadvantages of a doubly linked list?
- Requires extra memory for the pointer to previous node
- Need to reset more pointers when inserting or deleting than in a singly linked list


#### Resources
- https://www.youtube.com/watch?v=Ast5sKQXxEU
- https://www.youtube.com/watch?v=njTh_OwMljA
- https://www.youtube.com/watch?v=JdQeNxWCguQ&list=PL2_aWCzGMAwI3W_JlcBbtYTwiQSsOTa6P
- https://www.youtube.com/watch?v=VOQNf1VxU3Q&list=PL2_aWCzGMAwI3W_JlcBbtYTwiQSsOTa6P
- https://www.youtube.com/watch?v=A5_XdiK4J8A&list=PL2_aWCzGMAwI3W_JlcBbtYTwiQSsOTa6P (haven't watched)
- https://www.youtube.com/watch?v=MuwxQ2IB8lQ&list=PL2_aWCzGMAwI3W_JlcBbtYTwiQSsOTa6P (haven't watched)


#### LS Lecture
https://www.youtube.com/watch?v=S49kli7DOw4&feature=youtu.be


