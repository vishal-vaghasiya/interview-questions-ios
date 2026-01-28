# OOPS Concepts – Questions & Answers (Swift)
iOS interview questions with quick revision notes for Swift, UIKit, SwiftUI, Objective-C, and OOPS.

## OOPS Concepts – Interview Questions with Definitions & Examples (Swift)

Each question includes a **short definition** and a **small example** for quick interview revision.

---

## 1. What is OOPS?
**OOPS (Object-Oriented Programming System)** is a programming paradigm based on objects that contain **data (properties)** and **behavior (methods)**.

Benefits:
- Reusability
- Scalability
- Maintainability

---

## 2. What is a Class?
A **class** is a blueprint used to create objects.

```swift
class Car {
    var brand: String = "BMW"
    func drive() {
        print("Driving")
    }
}
```

---

## 3. What is an Object?
An **object** is an instance of a class.

```swift
let car = Car()
car.drive()
```

---

## 4. What is Encapsulation?
Encapsulation hides internal data and exposes only required functionality.

```swift
class BankAccount {
    private var balance = 0

    func deposit(_ amount: Int) {
        balance += amount
    }

    func getBalance() -> Int {
        balance
    }
}
```

---

## 5. What is Inheritance?
Inheritance allows a child class to reuse parent class properties and methods.

```swift
class Vehicle {
    func move() {}
}

class Bike: Vehicle {
    func ride() {}
}
```

---

## 6. What is Polymorphism?
Polymorphism allows the same method to have different implementations.

```swift
class Animal {
    func sound() { print("Sound") }
}

class Dog: Animal {
    override func sound() { print("Bark") }
}
```

---

## 7. What is Abstraction?
Abstraction hides implementation details and shows only essential features.

```swift
protocol Payment {
    func pay()
}
```

---

## 8. What is a Protocol?
A protocol is basically a blueprint of rules.

It defines what methods, properties, or requirements a class, struct, or enum must have, but not how they work.

```swift
protocol Flyable {
    func fly()
}
```

---

## 9. What is Method Overloading?
Same method name with different parameters.

```swift
func add(a: Int, b: Int) {}
func add(a: Double, b: Double) {}
```

---

## 10. What is Method Overriding?
Child class provides its own implementation of a parent method.

```swift
override func sound() {}
```

---

## 11. What are Value Types?
Value types create a copy on assignment.

Examples: `struct`, `enum`

```swift
struct User {
    var name: String
}
```

---

## 12. What are Reference Types?
Reference types share the same memory reference.

Example: `class`

---

## 13. What is ARC?
**Automatic Reference Counting** automatically manages memory by releasing unused objects.

---

## 14. What is a Strong Reference?
Keeps an object alive by increasing retain count.

---

## 15. What is a Weak Reference?
Does not increase retain count and is set to `nil` when object deallocates.

```swift
weak var delegate: SomeDelegate?
```

---

## 16. What is an Unowned Reference?
Does not retain the object and assumes it always exists.

```swift
unowned let owner: Owner
```

---

## 17. What is a Retain Cycle?
Two objects hold strong references to each other and never deallocate.

---

## 18. How to Avoid Retain Cycles?
Use `weak` or `unowned` references.

```swift
{ [weak self] in }
```

---

## 19. What is a Singleton?
A singleton allows only one shared instance in the app.

```swift
class AppManager {
    static let shared = AppManager()
    private init() {}
}
```

---

## 20. What is Copy-on-Write (COW)?
Optimization where copying happens only when data is modified.

Used in: `Array`, `Dictionary`, `Set`

---

## 21. What is Lazy Initialization?
Object is created only when accessed.

```swift
lazy var data = loadData()
```

---

## 22. What is Dependency Injection?
Providing dependencies from outside instead of creating them internally.

```swift
class Service {
    init(api: API) {}
}
```

---

## 23. What is SOLID?
Design principles for scalable and maintainable code.

- **S** Single Responsibility
- **O** Open / Closed
- **L** Liskov Substitution
- **I** Interface Segregation
- **D** Dependency Inversion

---

## Interview One-Liners
- Class → Blueprint
- Object → Instance
- Encapsulation → Data protection
- Inheritance → Code reuse
- Polymorphism → Multiple behaviors
- Abstraction → Hide details
