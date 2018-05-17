# Concurrency Tutorial

https://docs.oracle.com/javase/tutorial/essential/concurrency/index.html

- High level concurrency API's supported in Java since v5
- Library found at java.util.concurrent

# Processes and Threads

Two units of execution:
- processes
- threads

Java mostly uses threads.

Most PC's have lots of active threads and processes, even if they only have 1 processing core (only 1 thread can execute at a time). 

To share this core with other processes and threads requires the operating systems feature called *time slicing*.

However, most PCs now have multiple processors / processors with multiple execution cores.

## Process

Self contained execution environment.

Each process has it's own memory space, and other private runtime resources.

A single application can be composed of multiple processes, communicating with each other.

For processes to communicate with each other, the use IPC (interprocess communication).

Some examples of IPCs are *pipes*, and *sockets*.

Generally, the JVM runs as a single process.

The *ProcessBuilder* object can be used to create additional processes.

## Thread

Threads are considered lightweight processes.

Creating a thread takes less resources than creating a process.

Every process has at least one thread.

Threads share a processe's open files and memory, which can make communication harder.

System threads do memory management and signal handling alongside your applications *main thread*. The main thread can create new threads.

# Thread Objects

Threads are instantiated using the class *Thread*.

Creating a concurrent application using threads can be done in two ways:
- Instantiate Thread each time the system needs to do an asynchronous task
    
    - This allows for direct control of thread creation and management

- Pass the applications tasks to an executor.

    - This abstracts thread management from the rest of the applcation

## Defining and starting a Thread

Provide code to run in the thread.

```java
public class HelloRunnable implements Runnable {

    public void run() {
        System.out.println("Hello from a thread!");
    }

    public static void main(String args[]) {
        (new Thread(new HelloRunnable())).start();
    }

}
```