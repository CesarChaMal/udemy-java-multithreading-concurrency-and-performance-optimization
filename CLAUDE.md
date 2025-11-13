# CLAUDE.md - AI Assistant Guide

## Repository Overview

This repository contains source code for the Udemy course: **"Java Multithreading, Concurrency & Performance Optimization"** by Michael Pogrebinsky from Top Developer Academy.

- **Course URL**: https://www.udemy.com/course/java-multithreading-concurrency-performance-optimization
- **Author**: Michael Pogrebinsky - Top Developer Academy (https://topdeveloperacademy.com)
- **Copyright**: 2019-2023
- **Total Examples**: 19 numbered, self-contained projects
- **Total Code**: ~1,788 lines of Java
- **Primary IDE**: IntelliJ IDEA

## Repository Structure

The repository follows a **progressive learning path** with numbered examples:

```
udemy-java-multithreading-concurrency-and-performance-optimization/
├── .git/
├── .gitignore
├── README.md
├── out/                          # Compiled output directory
├── 01_threads-creation-part1/    # Basic thread creation
├── 02_thread-creation-part2-example/
├── 03_thread-termination-example/
├── 04_joining-threads-example/
├── 05_optimizing-for-latency-example/
├── 06_optimizing-for-throughput-example/
├── 07_introduction-to-critical-sections-example/
├── 08_critical-sections-and-synchronization-example/
├── 09_application-metrics-example/
├── 10_data-races-example/
├── 11_deadlocks-example/
├── 12_reentrantlock-example/    # Maven project with JavaFX
├── 13_read-write-lock-example/
├── 14_wait-notify-example/
├── 15_atomic-integer-example/
├── 16_atomic-reference-example/
├── 17_io-bound-application/     # Java 21 examples
├── 18_intro-to-virtual-threads/ # Java 21 - Virtual threads
└── 19_high-performance-io-virtual-threads/ # Java 21
```

### Example Directory Structure

**Standard Java Projects (Examples 01-11, 13-16):**
```
##_example-name/
├── src/
│   ├── Main.java           # Main entry point
│   └── [Other Java files]
├── resources/              # Optional: images, text files
├── README.md              # Example-specific readme
└── *.iml                  # IntelliJ IDEA module file
```

**Maven Project (Example 12 only):**
```
12_reentrantlock-example/
├── pom.xml                # Maven configuration
├── src/
│   └── main/java/Main.java
└── README.md
```

## Build System & Java Versions

### Build Systems
- **18 Projects**: Plain Java (no build tool required)
- **1 Project**: Maven (`12_reentrantlock-example`)

### Java Versions Required
- **Examples 01-16**: Java 11 (or higher)
- **Example 12**: Java 8+ (Maven pom.xml targets Java 1.8)
- **Examples 17-19**: Java 21 (required for virtual threads)

### Environment
Current environment has **OpenJDK 21.0.8** installed, which is compatible with all examples.

## How to Build and Run

### For Standard Java Projects (01-11, 13-16, 17-19)

**Compile:**
```bash
cd ##_example-name
javac src/*.java -d out/
```

**Run:**
```bash
java -cp out Main
# Or for examples with specific main classes:
java -cp out Main1
java -cp out Main2
```

**Quick compile and run:**
```bash
cd ##_example-name/src
java Main.java  # Java 11+ allows running without explicit compilation
```

### For Maven Project (12_reentrantlock-example)

**Build:**
```bash
cd 12_reentrantlock-example
mvn clean compile
```

**Run:**
```bash
mvn exec:java
```

**Package:**
```bash
mvn package
```

### For Examples with Resources

**Example 05** (image processing):
- Requires: `resources/many-flowers.jpg`
- Creates output: `out/many-flowers.jpg`

**Example 06** (HTTP server):
- Uses: `resources/war_and_peace.txt`
- Performance testing: `resources/performance_test_plan.jmx` (JMeter)
- Test data: `resources/search_words.csv`
- Server runs on `http://localhost:8000`

**Example 14** (matrix operations):
- Generates matrices files in project directory
- Creates results files with matrix multiplication outputs

## Course Content & Concepts

### Module 1: Thread Fundamentals (Examples 01-04)

**01 - Thread Creation Part 1** (`01_threads-creation-part1/`)
- Creating threads with `Runnable` interface
- Thread naming: `thread.setName()`
- Thread priorities: `setPriority()`
- Exception handling: `setUncaughtExceptionHandler()`
- Files: `Main1.java`, `Main2.java`

**02 - Thread Creation Part 2** (`02_thread-creation-part2-example/`)
- Extending `Thread` class
- Abstract base classes for threads
- Practical example: Vault password hacker simulation
- Multiple competing threads
- File: `Main.java`

**03 - Thread Termination** (`03_thread-termination-example/`)
- Interrupting threads: `thread.interrupt()`
- Handling `InterruptedException`
- Daemon threads: `setDaemon(true)`
- Graceful shutdown patterns
- BigInteger long-running computations
- Files: `Main1.java`, `Main2.java`, `Main3.java`

**04 - Joining Threads** (`04_joining-threads-example/`)
- Thread coordination: `thread.join()`
- Join with timeout: `join(milliseconds)`
- Parallel factorial calculations
- Collecting results from multiple threads
- File: `Main.java`

### Module 2: Performance Optimization (Examples 05-06)

**05 - Optimizing for Latency** (`05_optimizing-for-latency-example/`)
- Image processing parallelization
- Dividing work among threads
- `BufferedImage` manipulation
- Performance measurement and comparison
- Single-threaded vs multi-threaded benchmarking
- File: `Main.java`

**06 - Optimizing for Throughput** (`06_optimizing-for-throughput-example/`)
- HTTP server with thread pools
- `HttpServer` from `com.sun.net.httpserver`
- `ExecutorService` with `newFixedThreadPool()`
- Word counting in large texts
- JMeter performance testing
- File: `ThroughputHttpServer.java`

### Module 3: Synchronization & Thread Safety (Examples 07-10)

**07 - Introduction to Critical Sections** (`07_introduction-to-critical-sections-example/`)
- Race conditions demonstration (problem)
- Shared resource access without synchronization
- `InventoryCounter` pattern
- File: `Main.java`

**08 - Critical Sections and Synchronization** (`08_critical-sections-and-synchronization-example/`)
- Fixing race conditions (solution)
- `synchronized` blocks
- Lock objects
- Atomic operations through synchronization
- File: `Main.java`

**09 - Application Metrics** (`09_application-metrics-example/`)
- `volatile` keyword for visibility
- `synchronized` methods
- Live metrics calculation
- Producer-consumer pattern
- Real-world application: request processing metrics
- File: `Main.java`

**10 - Data Races** (`10_data-races-example/`)
- Understanding data races
- Memory visibility issues
- Non-atomic operations
- Difference between race conditions and data races
- File: `Main.java`

### Module 4: Advanced Locking (Examples 11-13)

**11 - Deadlocks** (`11_deadlocks-example/`)
- Deadlock demonstration
- Nested locks causing circular wait
- Train intersection simulation
- Understanding deadlock conditions
- File: `Main.java`

**12 - ReentrantLock** (`12_reentrantlock-example/`) ⭐ **Maven + JavaFX**
- `ReentrantLock` instead of `synchronized`
- `tryLock()` for non-blocking acquisition
- Lock fairness
- JavaFX GUI application
- Cryptocurrency price tracker (simulated)
- Dependencies: JavaFX 11.0.2 (controls, fxml)
- File: `Main.java`

**13 - Read-Write Lock** (`13_read-write-lock-example/`)
- `ReentrantReadWriteLock`
- Separating read and write locks
- Performance advantages for read-heavy workloads
- TreeMap-based inventory database
- File: `Main.java`

### Module 5: Inter-Thread Communication (Example 14)

**14 - Wait-Notify** (`14_wait-notify-example/`)
- `wait()` and `notify()` / `notifyAll()`
- Producer-consumer pattern
- `ThreadSafeQueue` implementation
- Matrix multiplication with multiple producers
- File I/O with threading
- Files: `MainApplication.java`, `MatricesGenerator.java`

### Module 6: Lock-Free Programming (Examples 15-16)

**15 - Atomic Integer** (`15_atomic-integer-example/`)
- `AtomicInteger` class
- Lock-free increment/decrement
- `incrementAndGet()`, `decrementAndGet()`
- Lock-free thread safety
- File: `Main.java`

**16 - Atomic Reference** (`16_atomic-reference-example/`)
- `AtomicReference<T>`
- Compare-and-swap (CAS): `compareAndSet()`
- Lock-free stack implementation
- `LockSupport.parkNanos()` for backoff
- Performance comparison with synchronized
- File: `Main.java`

### Module 7: Virtual Threads (Examples 17-19) 🆕 **Java 21**

**17 - IO-Bound Application** (`17_io-bound-application/`)
- Traditional threading for I/O operations
- `Executors.newCachedThreadPool()`
- `Executors.newFixedThreadPool()`
- Simulated blocking I/O
- Performance baseline for virtual threads comparison
- Files: `IoBoundApplication.java`, `IoBoundApplicationV2.java`

**18 - Introduction to Virtual Threads** (`18_intro-to-virtual-threads/`)
- Virtual threads basics (Java 21 Project Loom)
- `Thread.ofVirtual()` API
- Virtual thread creation patterns
- Blocking operations with virtual threads
- Files: `VirtualThreadsDemo.java`, `VirtualThreadsWithBlockingCalls.java`

**19 - High-Performance IO with Virtual Threads** (`19_high-performance-io-virtual-threads/`)
- `Executors.newVirtualThreadPerTaskExecutor()`
- Massive scalability: 10,000+ concurrent tasks
- Performance comparison with platform threads
- Modern I/O patterns
- Files: `IoBoundApplication.java`, `IoBoundApplicationV2.java`

## Key Java APIs & Concepts

### Threading Primitives
- `Thread` class: creation, start, join, interrupt
- `Runnable` interface
- Thread priorities and daemon threads
- `UncaughtExceptionHandler`

### Synchronization
- `synchronized` keyword (methods and blocks)
- `volatile` keyword (memory visibility)
- `wait()`, `notify()`, `notifyAll()`
- Intrinsic locks (monitor locks)

### java.util.concurrent.locks
- `ReentrantLock` - explicit locks with try-lock capability
- `ReentrantReadWriteLock` - separate read/write locks
- `Lock` interface

### java.util.concurrent.atomic
- `AtomicInteger` - lock-free integer operations
- `AtomicReference<T>` - lock-free reference operations
- Compare-and-swap (CAS) operations

### java.util.concurrent (Executors)
- `ExecutorService` - thread pool management
- `Executors.newFixedThreadPool(n)` - fixed-size pools
- `Executors.newCachedThreadPool()` - dynamic pools
- `Executors.newVirtualThreadPerTaskExecutor()` - virtual thread pools (Java 21)

### Advanced Topics
- `LockSupport` - low-level thread parking
- Virtual threads (Project Loom, Java 21)
- Performance measurement techniques
- JMeter for load testing

## Coding Conventions

### Copyright Header
All Java files include:
```java
/*
 * Copyright (c) 2019-2023. Michael Pogrebinsky - Top Developer Academy
 * https://topdeveloperacademy.com
 * All rights reserved
 */
```

### Code Style
- **Package Structure**: Most examples use default package (no package declaration)
- **Class Naming**: PascalCase (e.g., `InventoryCounter`, `Main`)
- **Inner Classes**: Frequent use of static inner classes for organization
- **Main Method**: Standard `public static void main(String[] args)`
- **Comments**: Educational comments explaining concepts
- **Javadoc**: Some files include Javadoc with course references

### Common Patterns
- **Thread Classes**: Often extend `Thread` or implement `Runnable`
- **Shared State**: Encapsulated in dedicated classes (e.g., `InventoryCounter`)
- **Resource Management**: Try-with-resources for `ExecutorService`
- **Error Handling**: `InterruptedException` properly caught and handled

### Example Structure
Each example follows this pattern:
1. **Demonstrate a problem** (e.g., race condition)
2. **Show the solution** (e.g., synchronization)
3. **Measure performance** where applicable
4. **Use simple, relatable scenarios** (vault, inventory, trains)

## Development Workflow

### For AI Assistants

When working with this repository:

1. **Understand the Context**
   - This is educational code from a course
   - Examples are self-contained and independent
   - Code intentionally demonstrates both problems and solutions
   - Some examples show "bad" code to illustrate issues (e.g., race conditions in Example 07)

2. **Making Changes**
   - **Preserve copyright headers** in all files
   - **Maintain educational clarity** - don't over-engineer
   - **Keep examples self-contained** - avoid cross-dependencies
   - **Test thoroughly** - threading bugs are subtle
   - **Document threading concepts** in comments

3. **Adding New Examples**
   - Follow the numbering convention: `##_descriptive-name-example/`
   - Create `src/` directory with Java files
   - Add `README.md` explaining the concept
   - Include copyright header in all Java files
   - Use IntelliJ IDEA project structure (.iml files)

4. **Testing Threading Code**
   - Run examples multiple times (threading bugs are non-deterministic)
   - Test with different numbers of threads
   - Verify synchronization correctness
   - Check for deadlocks (program hangs)
   - Look for race conditions (inconsistent results)

5. **Common Issues to Check**
   - **Race conditions**: Unsynchronized shared state access
   - **Deadlocks**: Circular lock dependencies
   - **Data races**: Non-volatile, non-synchronized variable access
   - **Thread leaks**: Threads not properly terminated
   - **Resource leaks**: ExecutorService not shut down

### Git Workflow

**Current Branch**: `claude/claude-md-mhy27qwbovcvvxya-01J2YKjuZLhzMrUSoNb4hGQa`

**Commit Guidelines**:
- Use clear, descriptive commit messages
- Mention example numbers when relevant (e.g., "Fix race condition in Example 07")
- Group related changes together
- Test before committing

**Push Command**:
```bash
git push -u origin claude/claude-md-mhy27qwbovcvvxya-01J2YKjuZLhzMrUSoNb4hGQa
```

## Dependencies

### Standard JDK (All Examples)
- `java.lang.*` - Core threading APIs
- `java.util.*` - Collections, Random, Scanner
- `java.util.concurrent.*` - Locks, Executors, Atomics
- `java.io.*` - File I/O
- `java.math.BigInteger` - Large number computations
- `javax.imageio.ImageIO` - Image processing
- `java.awt.image.BufferedImage` - Image manipulation
- `com.sun.net.httpserver.*` - HTTP server (Example 06)

### External Dependencies
**Example 12 ONLY** (`12_reentrantlock-example/pom.xml`):
```xml
<dependency>
    <groupId>org.openjfx</groupId>
    <artifactId>javafx-controls</artifactId>
    <version>11.0.2</version>
</dependency>
<dependency>
    <groupId>org.openjfx</groupId>
    <artifactId>javafx-fxml</artifactId>
    <version>11.0.2</version>
</dependency>
```

### Testing Tools
- **JMeter**: Example 06 includes `performance_test_plan.jmx`
- Performance testing done via `System.currentTimeMillis()`

## Common Threading Pitfalls (Demonstrated in Course)

1. **Race Conditions** (Example 07)
   - Multiple threads accessing shared state without synchronization
   - Results in inconsistent or incorrect values

2. **Data Races** (Example 10)
   - Non-volatile, non-synchronized variable access
   - Memory visibility issues between threads

3. **Deadlocks** (Example 11)
   - Circular wait on locks
   - Threads blocked indefinitely

4. **Improper Thread Termination** (Example 03)
   - Not handling `InterruptedException`
   - Non-daemon threads preventing JVM shutdown

5. **Performance Issues**
   - Over-synchronization reducing parallelism
   - Not using appropriate thread pool sizes
   - Using platform threads for massive I/O (solved by virtual threads)

## Quick Reference Commands

### Compile All Examples (excluding Maven)
```bash
for dir in */; do
    if [ -d "$dir/src" ] && [ ! -f "$dir/pom.xml" ]; then
        echo "Compiling $dir"
        javac "$dir/src/"*.java -d "$dir/out/" 2>/dev/null || true
    fi
done
```

### Run Specific Example
```bash
# Standard examples
cd 01_threads-creation-part1/src && java Main1.java

# Maven example
cd 12_reentrantlock-example && mvn exec:java
```

### Find All Main Classes
```bash
grep -r "public static void main" --include="*.java" . | cut -d: -f1
```

### Check Java Version Requirements
```bash
grep -r "source>" --include="pom.xml" .
grep -r "JDK_" --include="*.iml" . | grep -v ".idea"
```

## Resources

- **Course**: https://www.udemy.com/course/java-multithreading-concurrency-performance-optimization
- **Instructor**: Michael Pogrebinsky - Top Developer Academy
- **Website**: https://topdeveloperacademy.com
- **Java Docs**: https://docs.oracle.com/en/java/javase/21/docs/api/java.base/java/lang/Thread.html
- **Virtual Threads**: https://openjdk.org/jeps/444

## Notes for AI Assistants

### When Analyzing Code
- **Don't flag intentional bugs**: Examples 07, 10, 11 demonstrate problems before solutions
- **Respect educational purpose**: Simple code is better than clever code
- **Check example numbers**: Solutions often follow problems (07→08, 17→18→19)

### When Suggesting Improvements
- **Maintain simplicity**: This is teaching code
- **Preserve demonstration value**: Don't "fix" intentional problems
- **Keep examples independent**: Avoid shared utilities across examples
- **Consider the learning path**: Early examples use simpler patterns

### When Writing New Code
- **Match the style**: Follow existing conventions
- **Add copyright**: Include proper headers
- **Document thoroughly**: Explain threading concepts
- **Test extensively**: Run multiple times to catch threading bugs

### Common User Requests
- "Run example X" → Compile and execute specific example
- "Fix race condition" → Check if it's intentional (Example 07)
- "Add new example" → Follow numbering and structure conventions
- "Explain deadlock" → Reference Example 11
- "Virtual threads" → Examples 18-19, requires Java 21

---

**Last Updated**: 2025-11-13 (Generated)
**Repository State**: Clean working directory on branch `claude/claude-md-mhy27qwbovcvvxya-01J2YKjuZLhzMrUSoNb4hGQa`
