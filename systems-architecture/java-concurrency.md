# Java Concurrency

## What is concurrency?
* the ability to run several programs or parts of a program in parallel
* improves throughput and interactivity of the program
* leverage multi-cores key for managing high-volume application

## Process vs Threads

### Process

* runs independently
* isolated from other processes
* cannot access shared data in other processes
* resources (memory, CPU time) are allocated via the OS

### Thread

* lightweight process
* have their own call stack (memory cache)
* can access shared data of other threads in the same process
* copies shared data to local memory cache

### Java app

* runs in one process by default
* work with threads to achieve parallel processing or asynchronous behavior
* divide tasks into subtasks and execute in parallel

## Problems

### Two basic problems

<dl>
  <dt>visibility</dt>
  <dd>thread A reads shared data which is later changed by thread B and thread A is unaware of change</dd>

  <dt>access</dt>
  <dd>several threads access and change the same shared data simultaneously</dd>
</dl>

### Program failures

<dl>
  <dt>liveness failure</dt>
  <dd>program doesn’t react anymore due to deadlocks</dd>

  <dt>safety failure</dt>
  <dd>program creates incorrect data</dd>
</dl>

## Java

* supports threads
    - Thread class — represents a thread
    - java.util.concurrent package — utility classes useful for concurrency
- locks and synchronization
    - lock — protects code which can be executed by several threads simultaneously
    - lock is achieved using “synchronized” keyword
- synchronized keyword
    - only a single thread can execute a block of code at the same time
    - each thread entering a synchronized block sees the effects of all previous modifications that were guarded by the same lock
- synchronization necessary for mutually exclusive access to blocks and for reliable communication between threads
- use synchronized keyword
    - for definition of method; ensures only one thread can enter this method at the same time
    - to protect blocks of code within a method
      - block is guarded by a key, which is either a String or an object
      - key is called lock
- volatile keyword
    - guaranteed that any thread that reads volatile variable will see most recently written value

```java
public synchronized void critical() {
    // some thread critical stuff
    // here
}
  
public class CrawledSites {
    private List<String> crawledSites = new ArrayList<String>();
    private List<String> linkedSites = new ArrayList<String>();

    public void add(String site) {
      synchronized (this) {
        if (!crawledSites.contains(site)) {
          linkedSites.add(site);
        }
      }
    }
}
```

### Imutability and Defensive

- simplest way to avoid problems is to share only immutable data between threads
- practice defensive coding for values that might be changed (like a List)

```java
public List<String> getList() {
    return Collections.unmodifiableList(list);
}
```

### Threads in Java
- main way to create threads is to use java.lang.Thread
- Thread executes an object of type java.lang.Runnable
- Runnable is interface

    - defines run() method, which is called by Thread object and contains the work which should be done
    - can’t return a result to the caller
- Runnable is the task to perform and Thread is the worker who is doing this task
- disadvantages

    - creating a new thread causes some performance overhead
    - too many threads can lead to reduced performance because of context switching
    - cannot easily control the number of threads and may run out of memory because of too many threads
- java.util.concurrent package offers improved support for concurrency

### Thread Pools

- Thread pools manage a pool of worker threads
- Thread pool is a collection of tasks and running threads
- contains a work queue which holds tasks waiting to get executed
- Executor framework

    - provides implementation of java.util.concurrent.Executor interface — Executors.newFixedThreadPool(int num_threads)
    - tasks are Runnable or Callable
- Executor lifecycle

    - get ExecutorService from Executors.newFixedThreadPool
    - add task

        - add Runnable by calling execute(Runnable)
        - add Callable by calling executor.submit(Callable) (returns Future)
    - service will execute threads
    - call shutdown() on service to begin shutdown process
    - call awaitTermination() on service to allow all threads to complete

```java
public class Main {
    private static final int NTHREDS = 10;

    public static void main(String[] args) {
        ExecutorService executor = Executors.newFixedThreadPool(NTHREDS);
        for (int i = 0; i < 500; i++) {
            Runnable worker = new MyRunnable(10000000L + i);

            executor.execute(worker);
        }
        // This will make the executor accept no new threads
        // and finish all existing threads in the queue
        executor.shutdown();
        // Wait until all threads are finish
        executor.awaitTermination();
        System.out.println("Finished all threads");
    }
}
```

### Futures and Callables    

- Callable can also be run by Thread pool
- Callable allows return values after completion, whereas Runnable does not
- if callable submitted to Executor, framework returns a java.util.concurrent.Future
- Future can be used to retrieve the Callable result
- as of Java 8 can use CompletableFuture interface to provide a callback

    - code to be executed when a task completes
    - this is sort of like JavaScript promises

### Fork-Join

* fork-join framework allows you to distribute a certain task on several workers and wait for results

```java
public class Test {

    public static void main(String[] args) {
        Problem test = new Problem();
        // check the number of available processors
        int nThreads = Runtime.getRuntime().availableProcessors();
        System.out.println(nThreads);
        Solver mfj = new Solver(test.getList());
        ForkJoinExecutor pool = new ForkJoinPool(nThreads);
        pool.invoke(mfj);
        long result = mfj.getResult();
        System.out.println("Done. Result: " + result);
        long sum = 0;
        // check if the result was ok
        for (int i = 0; i < test.getList().length; i++) {
            sum += test.getList()[i];
        }
        System.out.println("Done. Result: " + sum);
    }
}
```