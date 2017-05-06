# Project 2

The goal of this project is to understand the idea of threads, by <br />
implementing a basic user-level thread library for Linux. The library will  <br />
provide a complete interface for applications to create and run  <br />
independent threads concurrently.<br />

Some Requirements are:<br />

Create new threads<br />
Schedule the execution of threads in a round-robin fashion  <br />
Provide a synchronization mechanism for threads to join other threads  <br />
Be preemptive, that is to provide an interrupt-based scheduler  <br />

## Phase: 1 | Queue Implementation

For this project we were able to completely implement the queue including  <br />
functions such as queue_iterator(), queue_create() and queue_destroy(). <br />
We used a structure for queue and structure for node in our queue implementation. Our queue has two main pointers one for the head of the linked list and the other for the tail of the linked list. All the enqueueing of the data is done from the tail of the linked list while all the dequeueing of the data is done from the head of the linked list. Besides this every node in our queue implementation has a pointer to point it to next node. 

How we implementaed different functions:
queue_create() : To create the queue, we simply allocate enough memeory to it. 
queue_destroy() : To destroy the queue, we check if it has elements in it, and if it does we free up that memeory. 
queue_enqueue() : To enqueue, we reroute the tail pointer of the queue and set the pointer of the new node to NULL
queue_dequeue() : To dequeue, we reroute the head using a temporary pointer to the next node of the head and assign the queue element data to the data passed as argument. 
queue_delete() : To delete, we parse through the queue for the appropriate data, and free up that memeory by reassigning the respective pointers.
queue_iterate() : To iterate, we applied the function passed in the paramenter, to all the elements in the queue. 
queue_length() : To find the length of the queue, we walk through the queue, counting elements and returned the total.

#### Testing of queue
In order to test our queue implemntation, we wrote of test file. In this file we used assert() function to check if our queue is returning the correct return value to its function call. One of the way we checked our queue is by using different number of queue_enqueue() followed by the same number of queue_dequeue(). This way we ended up with the empty queue. Also, We tried subjecting the queue to invalid elements in order to make sure it does not lose objects or crash.


## Phase: 2 | Thread Control Block (TCB) Implementation 

uthread_create() <br />
uthread_yield() <br />
uthread_start() <br />
uthread_block() <br />
uthread_unblock() <br />
uthread_exit() <br />


## Phase: 3 | uthread_join() Implementation 

uthread_join()

## Phase: 4 | Preemption

### Authors

* **Harshil Shah** 
* **Aashay Wadnagara** 

