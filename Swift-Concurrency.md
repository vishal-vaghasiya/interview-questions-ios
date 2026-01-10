

# interview-questions-ios
iOS interview questions with quick revision notes for Swift, UIKit, SwiftUI, Objective-C, and OOPS.

## Swift Concurrency – Interview Questions with Definitions & Examples

Each topic includes a **short definition** and a **small example** for easy understanding and interview revision.

---

## What is Concurrency?
Concurrency is the ability to run multiple tasks independently without blocking the main thread.

---

## Synchronous vs Asynchronous

### Synchronous
Blocks execution until the task completes.

### Asynchronous
Runs tasks in the background without blocking execution.

---

## What is Multithreading?
Multithreading allows multiple threads to execute tasks concurrently.

---

## What is GCD?
Grand Central Dispatch is Apple’s framework for managing concurrent tasks efficiently.

```swift
DispatchQueue.global().async {
    print("Background Task")
}
```

---

## Main Thread vs Background Thread
- UI updates → Main thread
- Heavy tasks → Background thread

---

## What is DispatchQueue?
DispatchQueue manages execution of tasks.

```swift
DispatchQueue.main.async {
    print("UI Update")
}
```

---

## What is DispatchGroup?
DispatchGroup tracks multiple asynchronous tasks.

```swift
let group = DispatchGroup()

group.enter()
DispatchQueue.global().async {
    group.leave()
}

group.notify(queue: .main) {
    print("All done")
}
```

---

## What is DispatchSemaphore?
Controls access to limited resources.

```swift
let semaphore = DispatchSemaphore(value: 1)
```

---

## What is OperationQueue?
Higher-level abstraction over GCD.

```swift
let queue = OperationQueue()
queue.addOperation {
    print("Operation")
}
```

---

## What is async / await?
Modern Swift syntax for writing asynchronous code sequentially.

```swift
let data = try await fetchData()
```

---

## What is Task?
Task represents a unit of asynchronous work.

```swift
Task {
    await loadData()
}
```

---

## What is Task Priority?
Defines importance of a task.

```swift
Task(priority: .background) {}
```

---

## What is Structured Concurrency?
Ensures child tasks complete before parent exits.

---

## What is TaskGroup?
Runs multiple async tasks in parallel.

```swift
await withTaskGroup(of: Int.self) { group in
    group.addTask { 1 }
}
```

---

## What is Cancellation?
Stops an ongoing task when no longer needed.

```swift
Task {
    try Task.checkCancellation()
}
```

---

## What is Actor?
Actor protects mutable state from data races.

```swift
actor DataManager {
    var value = 0
}
```

---

## What is @MainActor?
Ensures code runs on main thread.

```swift
@MainActor
func updateUI() {}
```

---

## What is Sendable?
Marks types safe to pass across concurrency domains.

---

## What is Detached Task?
Runs independently of parent task.

```swift
Task.detached {
    print("Detached")
}
```

---

## What is Continuation?
Bridges callback-based APIs to async/await.

```swift
withCheckedContinuation { continuation in
    continuation.resume(returning: value)
}
```

---

## What is AsyncSequence?
Sequence that produces values asynchronously.

---

## What is Race Condition?
Occurs when multiple threads access shared data simultaneously.

---

## How to Avoid Race Conditions?
Use actors, locks, or serial queues.

---

## What is Deadlock?
Two threads waiting on each other forever.

---

## Interview One-Liners
- async/await → readable async code
- Actor → thread-safe data
- GCD → task scheduling
- MainActor → UI safety
- Task → async unit of work
