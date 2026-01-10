# interview-questions-ios
iOS interview questions with quick revision notes for Swift, UIKit, SwiftUI, Objective-C, and OOPS.

## Memory Management – Interview Questions with Definitions & Examples

Each topic includes a **short definition** and a **small example** for quick interview revision.

---

## What is Memory Management?
Memory management is the process of allocating and deallocating memory efficiently to avoid leaks and crashes.

---

## What is ARC?
ARC (Automatic Reference Counting) automatically tracks and manages memory by counting strong references to objects.

---

## What is a Strong Reference?
A strong reference increases an object’s retain count and keeps it alive.

```swift
var obj = MyClass()
```

---

## What is a Weak Reference?
A weak reference does not increase retain count and becomes `nil` when the object is deallocated.

```swift
weak var delegate: MyDelegate?
```

---

## What is an Unowned Reference?
An unowned reference does not retain the object and assumes it always exists.

```swift
unowned let owner: Owner
```

---

## Strong vs Weak vs Unowned

| Type | Retains Object | Nil on Dealloc | Crash Risk |
|----|----|----|----|
| Strong | Yes | No | No |
| Weak | No | Yes | No |
| Unowned | No | No | Yes |

---

## What is a Retain Cycle?
A retain cycle occurs when objects strongly reference each other and never deallocate.

---

## Retain Cycle Example

```swift
class A {
    var b: B?
}

class B {
    var a: A?
}
```

---

## How to Avoid Retain Cycles?
Use `weak` or `unowned`.

```swift
class B {
    weak var a: A?
}
```

---

## Retain Cycle in Closures
Closures capture `self` strongly by default.

---

## Closure Retain Cycle Example

```swift
self.fetch {
    self.updateUI()
}
```

---

## How to Avoid Closure Retain Cycle?

```swift
self.fetch { [weak self] in
    self?.updateUI()
}
```

---

## What is Capture List?
Defines how values are captured inside closures.

```swift
{ [weak self] in }
```

---

## What is AutoreleasePool?
AutoreleasePool releases temporary objects early to reduce memory usage.

```swift
autoreleasepool {
    // memory intensive code
}
```

---

## What is Memory Leak?
Memory that is not released even when no longer needed.

---

## What is Dangling Pointer?
Reference pointing to deallocated memory (unsafe).

---

## What is Heap Memory?
Heap stores dynamically allocated objects.

---

## What is Stack Memory?
Stack stores function calls and local variables.

---

## Heap vs Stack

| Heap | Stack |
|----|----|
| Dynamic | Static |
| Reference types | Value types |
| Slower | Faster |

---

## What is Copy-on-Write (COW)?
Optimization where copying happens only when data is modified.

Used in `Array`, `Dictionary`, `Set`.

---

## How Swift Optimizes Struct Memory?
Using Copy-on-Write and stack allocation.

---

## What is Lazy Property?
Initialized only when accessed first time.

```swift
lazy var data = loadData()
```

---

## What is Deinit?
Called just before object deallocation.

```swift
deinit {
    print("Deallocated")
}
```

---

## What is Memory Warning?
System notification when memory is low.

---

## How to Handle Memory Warnings?
Release cached data and heavy objects.

---

## Tools to Detect Memory Issues
- Xcode Memory Graph
- Instruments (Leaks, Allocations)

---

## Common Memory Issues
- Retain cycles
- Strong delegate references
- Long-living singletons
- Large images in memory

---

## Interview One-Liners
- ARC → automatic memory handling
- Weak → avoids retain cycles
- Deinit → cleanup
- COW → efficient copying
- AutoreleasePool → temporary memory cleanup
