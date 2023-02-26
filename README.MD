Implementing Reader Writer solution with only 1 semaphore for mutual exclusion of readers and writers leads to a scenario that 
starves the writer process.

To overcome this we come up with an analogy similar to that of a door/gate which needs to be passed by both the writers and readers.
It is locked by the writer whenever it enters the gate and is unlocked only after access to its critical section has been completed.

So whenever a writer enters this gate, it locks it so that no more processes can vie for access to the critical section. This ensures 
that when a writer is waiting for access to the shared resource due to existing readers, new readers which are coming are queued at 
the gate and are not allowed to read the file.

Once the writer has finished writing, it unlocks the gate once again and the scheduler can now choose either a writer or a reader 
waiting at the gate to enter the critical section.