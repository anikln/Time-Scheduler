# Time Scheduler System that uses system calls, programmed in C language

<p align="justify">I developed this program for my semester's assignment in the course of "Operating Systems", that i attended during my college studies. The course was taught by the Assistant Professor Dr Eli Katsiri during the winter academic semester of year 2016-2017. The project contains two txt files. The first one is "DemoScheduler.txt", that schedules for execution 50 random processes using the Non-Interactice-Process-Administrator (NIPA) and afterwards the Shortest Job First Scheduler policy.</p>

## Definitions about the assignment

### Non-Interactice-Process-Administrator (NIPA)

The Non-Interactice-Process-Administrator has the following features:

1. It runs in a repeating loop (until all 50 processes are completed):
    a. It sleeps for a random time interval from 1 to 10 second.
    b. It creates a random number of process descriptors, from 1 to 10, in order.
    c. For each process:
        I. Creates an unique identifier (id), a duration of execution (duration) and a priority (priority). The duration of execution must be between the closed interval 5-30 sec while the priority must be between the closed interval 1-5. Lower value corresponds to higher priority, so the highest priority is the value 1.
        II. Stores the above information about each process in a struct data type with the name procDesc.
        III. Stores the struct in list (buffer) > 50 spots with FIFO order.
2. When it terminates it returns the buffer.
 
### Shortest Job First Scheduler (SJFScheduler) 

The Shortest Job First Scheduler (SJFScheduler) has the following features:

1. It keeps (after it makes the necessary initializations):
    a. A linked list, inputProcessList that is sorted by ascending execution time.
    b. A list named terminatedProcessList, for the process descriptors that are completed.
2. It takes as input the buffer and it copies it to inputProcessList putting in the head the process with the smallest duration of execution.
3. As long as there are process descriptors in inputProcessList:
    a. For each process descriptor, beginning from the head, it creates a testProcess process with parameters (id, duration, priority) and it executes it.
    b. It waits until the current process is executed and copies the process descriptor in the terminatedProcessList.
    c. In case that occurs an error during the execution of the process the scheduler returns and prints an error message with the number of the error code that is returned from the execution of the process.
4. Otherwise, when the scheduler terminates, it returns the terminatedProcessList. 

### Process (testProcess) 

For each process descriptor included in the struct procDesc the scheduler must create a testProcess process that prints in the screen  the following message:

"Hello World. Process (id), duration (duration), priority (priority)."

where the values in the parenthesis are respectively the unique identifier, the duration of execution and the priority that are included in the struct procDesc.

Then the execution of the process will be delayed inside a repeated loop:

```
r = (int) (double)rand() / ((double) RAND_MAX);
for (i=1;i<r*10000000;i++);
```

where the r variable is and integer, rand() is the random number generator and RAND_MAX is a constant equal to 32767.

The creation of a testProcess process that corresponds to the process descriptor, isdone throught the system calls fork() and execve().

## Results after the program is executed

<img src="/images/1.png"><img src="/images/2.png"><img src="/images/3.png"><img src="/images/4.png">
## Authors

* **Kleinaki Athina Styliani** -  [AniKln](https://github.com/anikln)

