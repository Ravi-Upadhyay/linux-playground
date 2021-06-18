# Linux Processes

> A process is simply an instance of one or more related tasks (threads) executing on your computer. It is not the same as a program or a command. A single command may actually start several processes simultaneously. Some processes are independent of each other and others are related. A failure of one process may or may not affect the others running on the system.

- Processes use many system resources, such as memory, CPU (central processing unit) cycles. 
- The operating system (especially the kernel) is responsible for allocating a proper share of these resources to each process and ensuring overall optimized system utilization.

## Index

- Process Types
- Process Scheduling and States
  - Process and Thread IDs
  - User and Group IDs
  - Priorities
- Useful Commands
  - Kill the process
  - Set the priorities

___

![Process_Types](https://github.com/Ravi-Upadhyay/linux-playground/blob/master/LFS101x_Introduction_to_Linux/Assets/Linux_Process_Types.png)

## Process Types

|Process Type          |	Description	                                                  |  Example               |
|:---------------------|:-------------------------------------------------------------------------|:-----------------------|
| Interactive Processes | Need to be started by a user, either at a command line or through a graphical interface such as an icon or a menu selection.|	bash, firefox, top |
| Batch Processes	| Automatic processes which are scheduled from and then disconnected from the terminal. These tasks are queued and work on a FIFO (First-In, First-Out) basis.	| updatedb, ldconfig |
| Daemons	        | Server processes that run continuously. Many are launched during system startup and then wait for a user or system request indicating that their service is required. | httpd, sshd, libvirtd |
| Threads	        | Lightweight processes. These are tasks that run under the umbrella of a main process, sharing memory and other resources, but are scheduled and run by the system on an individual basis. An individual thread can end without terminating the whole process and a process can create new threads at any time. Many non-trivial programs are multi-threaded. | firefox, gnome-terminal-server |
| Kernel Threads	| Kernel tasks that users neither start nor terminate and have little control over. These may perform actions like moving a thread from one CPU to another, or making sure input/output operations to disk are completed. | kthreadd, migration, ksoftirqd |

___

## Process Scheduling and States

- **Scheduler** constantly shifts processes on and off the CPU, sharing time according to relative priority.
- **Running-state** either currently executing instructions on a CPU, or is waiting to be granted a share of time (a time slice) so it can execute.
- **Sleep-state** when they are waiting for something to happen before they can resume, perhaps for the user to type something.
- **Zombie-state** less frequent, especially when a process is terminating. It is not really alive, but still shows up in the system's list of processes.

### Process and Thread IDs

|   ID Type	        | Description                                                                                          |
|:----------------------|:-----------------------------------------------------------------------------------------------------|
| Process ID (PID)	|Unique Process ID number |
| Parent Process ID (PPID) | Process (Parent) that started this process. If the parent dies, the PPID will refer to an adoptive parent; on recent kernels, this is kthreadd which has PPID=2. |
| Thread ID (TID)	| Thread ID number. This is the same as the PID for single-threaded processes. For a multi-threaded process, each thread shares the same PID, but has a unique TID. |


### User and Group IDs

|   ID Type	        | Description                                                                                          |
|:----------------------|:-----------------------------------------------------------------------------------------------------|
| Real User ID (RUID)	| The operating system identifies the user who starts the process |
| Effective User ID (EUID) | The user who determines the access rights for the users is identified by the Effective UID (EUID) |
| Real Group ID (RGID)	| Users can be categorized into various groups. Each group is identified by the Real Group ID (RGID) |
| Effective Group ID (EGID)	| The access rights of the group are determined by the Effective Group ID (EGID). |

Most of the time we ignore these details and just talk about the User ID (UID) and Group ID (GID).

### Priorities

- **Nice Value** or **Niceness** can be used to set the priority for a process. 
- The lower the nice value, the higher the priority.
- In Linux, a nice value of -20 represents the highest priority and +19 represents the lowest. 
- You can also assign a so-called **real-time priority** to time-sensitive tasks, such as controlling machines through a computer or collecting incoming data
- **Hard real-time** which is conceptually different, and has more to do with making sure a job gets completed within a very well-defined time window.

![Representation Of Process](https://github.com/Ravi-Upadhyay/linux-playground/blob/master/LFS101x_Introduction_to_Linux/Assets/Linux_Representation_Of_Process.png)

___

## Useful Commands

### Kill the process

```bash
# To list down the processes, i.e. also PID
ps

# Kill the processes
kill -SIGKILL <pid>
kill -9 <pid>

```

### Set the priorities

```bash
# List all the process, with details i.e. Nice Values
ps lf

# Changing the priority (remember priorities -20 to +19)
renice +5 <pid>



```
___


