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
We used a structure for queue and structure for node in our queue  <br />
implementation. Our queue has two main pointers one for the head of the  <br /> 
linked list and the other for the tail of the linked list. All the  <br /> 
enqueueing of the data is done from the tail of the linked list while all  <br />
the dequeueing of the data is done from the head of the linked list.  <br />
Besides this every node in our queue implementation has a pointer to point <br /> 
it to next node.   <br />
 <br />

How we implementaed different functions: <br />
queue_create() : To create the queue, we simply allocate enough memeory to it. <br /> 
queue_destroy() : To destroy the queue, we check if it has elements in it, and <br /> 
if it does we free up that memeory. <br /> 
queue_enqueue() : To enqueue, we reroute the tail pointer of the queue and set <br /> 
the pointer of the new node to NULL. <br /> 
queue_dequeue() : To dequeue, we reroute the head using a temporary pointer to <br /> 
the next node of the head and assign the queue element data to the data <br /> 
passed as argument. <br /> 
queue_delete() : To delete, we parse through the queue for the appropriate data, <br />  
and free up that memeory by reassigning the respective pointers. <br /> 
queue_iterate() : To iterate, we applied the function passed in the paramenter, <br /> 
to all the elements in the queue. <br /> 
queue_length() : To find the length of the queue, we walk through the queue, <br /> 
counting elements and returned the total. <br /> 

#### Testing of queue
In order to test our queue implemntation, we wrote of test file. In this file we <br /> 
used assert() function to check if our queue is returning the correct return <br />
value to its function call. One of the way we checked our queue is by using <br />
different number of queue_enqueue() followed by the same number of <br />
queue_dequeue(). This way we ended up with the empty queue. Also, We tried <br />
subjecting the queue to invalid elements in order to make sure it does <br />
not lose objects or crash. <br /> 


## Phase: 2 | Thread Control Block (TCB) Implementation 

List of the functions that we implemented during this phase are: <br />
uthread_create() <br />
uthread_yield() <br />
uthread_start() <br />
uthread_block() <br />
uthread_unblock() <br />
uthread_exit() <br />
<br />
So we as a group, we started on working at different functions at the <br />
same time. We started from implementing the uthread_start() function and <br />
uthread_yield() function of uthread library. We created four global queues <br />
for running, ready, blocked and zombie for different stated of the thread <br />
life cycle. Eventhough, there was only one thread running at a time, we still <br />
made a queue for the running state because it made our implemetation easier. <br />
<br />
For the implementation of uthread_start() function, we weren't sure <br />
about how to handle the contexts and the stack and how do to the various <br />
functions in the context.h files work. However, we googled inorder to see <br />
different examples where they use this similar functions. We also have <br />
private data structure to hold data memebers like TID, State, Stack <br />
Pointer, Context, Thread state using the data-type such as uthread_t <br />
and uthread_func_t. We also implemented global running thread to keep <br />
track of what is being run. <br />
<br />
For the uthread_create() function, we checked if ready has any elements.<br /> 
If not then we called uthread_init() function which initializes the <br />
queues and the main thread. If there are elements in the ready queue, <br />
then the we just create a new thread and enqueue it in the ready queue <br />
by setting it state to the ready. <br />
<br />
In the exit function, we created a temporary thread to store the TCB <br />
values from the running thread. Then we set the current state of that <br />
thread to zombie and enqueue it into zombie queue.<br />
<br />
In the uthread_yield() function, we gave the chance to the threads <br />
that are in the ready queue to be executed by dequeueing the thread <br />
from the running queue and enqueueing it back into the ready queue. <br />
After dequeue thread from the ready and enqueuing it into the running <br />
queue and setting it current state to running.<br />
<br />

## Phase: 3 | uthread_join() Implementation 

uthread_join()

## Phase: 4 | Preemption

We could not reached to this phase of the project :(

### Authors

* **Harshil Shah** 
* **Aashay Wadnagara** 

### References

- https://gist.github.com/mycodeschool/7510222 (our queue structure was heavily based on this)
- http://stackoverflow.com/questions/1152246/mutual-exclusion-using-testandset-instruction (provided example on dealing with critical section)
- https://github.com/twcamper/c-programming/blob/master/lib/bounded-queue.c (another source for examples of queue functions)
- https://raw.githubusercontent.com/hpatel3006/Pro2-1 (For syntax support in C )
 
