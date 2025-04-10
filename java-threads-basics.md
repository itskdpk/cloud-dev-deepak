# Java Threads and ExecutorService - Beginner Notes 🧵⚙️

### What are Threads?

A thread is the smallest unit of execution in a program. It helps you run multiple parts of code at the same time. Think of it like different hands working on the same task.

---

### Why Not Just Use `new Thread()`?

- Creating threads manually is **resource-heavy**
- Managing lifecycle (start, end, restart) is complex
- Not scalable for real-world apps

---

### Java's Solution: `ExecutorService`

The `ExecutorService` helps us manage a **pool of threads**. It lets us reuse threads instead of creating new ones every time.

Example:
```java
ExecutorService service = Executors.newFixedThreadPool(5);
service.submit(() -> System.out.println("Task running"));
service.shutdown();
```
### What if we're expecting a return  from the thread?
In Java, there a concept call "Future" which allow you to hold data from thread without stoping the execution, you can simply call the Future when you need to use the return Object.

Example:
```java
Future<Integer> result = service.submit(() -> return 10 + 20);
System.out.println(result.get()); // prints 30
```

Key Notes:
- Thread creation is expensive, so ExecutorService is better
- Future helps keep code async while waiting for results
- Even with few CPU cores, systems use context switching to run many thread
