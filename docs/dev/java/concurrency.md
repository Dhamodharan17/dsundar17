# Java - Concurrency

## Thread Creation

```java
// 1. Extend Thread
class MyThread extends Thread {
    public void run() { /* work */ }
}

// 2. Implement Runnable (preferred)
Runnable task = () -> { /* work */ };
new Thread(task).start();

// 3. ExecutorService (best practice)
ExecutorService executor = Executors.newFixedThreadPool(4);
executor.submit(() -> { /* work */ });
executor.shutdown();
```

## Thread Pool Types

| Type | Use When |
|---|---|
| `newFixedThreadPool(n)` | Known number of concurrent tasks |
| `newCachedThreadPool()` | Many short-lived tasks |
| `newSingleThreadExecutor()` | Tasks must run sequentially |
| `newScheduledThreadPool(n)` | Delayed / periodic tasks |

## Synchronization

```java
// synchronized block (preferred — lock on specific object)
synchronized (lockObject) {
    // critical section
}

// ReentrantLock (more control)
Lock lock = new ReentrantLock();
lock.lock();
try {
    // critical section
} finally {
    lock.unlock(); // ALWAYS in finally
}
```

## Concurrent Collections

| Instead of | Use | Why |
|---|---|---|
| HashMap | ConcurrentHashMap | Segment-level locking |
| ArrayList | CopyOnWriteArrayList | Safe iteration |
| TreeMap | ConcurrentSkipListMap | Sorted + concurrent |
| LinkedList (queue) | ConcurrentLinkedQueue | Lock-free queue |
| — | BlockingQueue | Producer-consumer |

## volatile vs synchronized vs Atomic

| Feature | volatile | synchronized | Atomic |
|---|---|---|---|
| Visibility | Yes | Yes | Yes |
| Atomicity | No | Yes | Yes |
| Blocking | No | Yes | No (CAS) |
| Use | Flags, status | Critical section | Counters |

## CompletableFuture

```java
CompletableFuture.supplyAsync(() -> fetchData())
    .thenApply(data -> process(data))
    .thenAccept(result -> save(result))
    .exceptionally(ex -> { log(ex); return null; });

// Combine two futures
CompletableFuture.allOf(future1, future2).join();
```

## My Notes
<!-- Add your own observations, mistakes, and learnings below -->
