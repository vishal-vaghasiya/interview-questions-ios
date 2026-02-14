# Swift Interview Questions

---

# Section 1 – OOPS Concepts

---

## 1. What is a Class?

### Answer:
A class is a blueprint used to create objects.  
It defines properties (variables) and methods (functions).  
Class is a reference type, which means it is stored in heap memory.

### Example:
```swift
class Person {
    var name: String
    
    init(name: String) {
        self.name = name
    }
    
    func greet() {
        print("Hello, my name is \(name)")
    }
}
```

### Easy Remember:
Class = Blueprint to create objects.

---

## 2. What is an Object?

### Answer:
An object is an instance of a class.  
It contains real values and can use the class methods.

### Example:
```swift
let person1 = Person(name: "Vishal")
person1.greet()
```

### Easy Remember:
Object = Real thing created from class.

---

## 3. What is Abstraction?

### Answer:
Abstraction means hiding complex implementation details  
and showing only essential features to the user.

We use protocols and access control for abstraction.

### Example:
```swift
protocol Vehicle {
    func start()
}

class Car: Vehicle {
    func start() {
        print("Car Started")
    }
}
```

### Easy Remember:
Abstraction = Hide details, show only needed functionality.

---

## 4. What is Encapsulation?

### Answer:
Encapsulation means hiding data and controlling access to it.  
We use private, public, internal keywords.

### Example:
```swift
class BankAccount {
    private var balance: Double = 0
    
    func deposit(amount: Double) {
        balance += amount
    }
    
    func getBalance() -> Double {
        return balance
    }
}
```

### Easy Remember:
Encapsulation = Protect data using access control.

---

## 5. What is Inheritance?

### Answer:
Inheritance allows one class to inherit properties and methods  
from another class using the ':' symbol.

### Example:
```swift
class Animal {
    func eat() {
        print("Eating")
    }
}

class Dog: Animal {
    func bark() {
        print("Barking")
    }
}
```

### Easy Remember:
Inheritance = Child class gets features from parent class.

---

## 6. What is Polymorphism?

### Answer:
Polymorphism means "many forms".  
Same method name behaves differently in different classes.

### Example:
```swift
class Shape {
    func draw() {
        print("Drawing Shape")
    }
}

class Circle: Shape {
    override func draw() {
        print("Drawing Circle")
    }
}
```

### Easy Remember:
Polymorphism = Same method, different behavior.

---

## 7. What is Method Overloading?

### Answer:
Method overloading means multiple methods with the same name  
but different parameters in the same class.

### Example:
```swift
class MathOperations {
    func add(a: Int, b: Int) -> Int {
        return a + b
    }
    
    func add(a: Double, b: Double) -> Double {
        return a + b
    }
}
```

### Easy Remember:
Overloading = Same method name, different parameters.

---

## 8. What is Method Overriding?

### Answer:
Method overriding means changing the parent class method  
implementation in the child class using 'override' keyword.

### Example:
```swift
class Bird {
    func sound() {
        print("Bird sound")
    }
}

class Parrot: Bird {
    override func sound() {
        print("Parrot speaking")
    }
}
```

### Easy Remember:
Overriding = Child class changes parent method.

---

## 9. What is a Protocol?

### Answer:
A protocol defines a blueprint of methods and properties  
that a class, struct, or enum must implement.

Protocols support abstraction and loose coupling.

### Example:
```swift
protocol Flyable {
    func fly()
}

class Airplane: Flyable {
    func fly() {
        print("Flying in sky")
    }
}
```

### Easy Remember:
Protocol = Rules that classes must follow.

---

## 10. Why is Swift called a Protocol-Oriented Programming language?

### Answer:
Swift focuses more on protocols than inheritance.  
Protocols allow multiple types to share behavior  
without using class inheritance.

It makes code more flexible and reusable.

### Example:
```swift
protocol Walkable {
    func walk()
}

extension Walkable {
    func walk() {
        print("Walking")
    }
}

struct Human: Walkable { }
```

### Easy Remember:
Swift prefers Protocol + Extension over heavy inheritance.

---

# Section 2 – Memory Management

---

## 11. What is ARC?

### Answer:
ARC (Automatic Reference Counting) automatically manages memory in Swift.  
It keeps track of how many strong references point to a class object.  
When reference count becomes 0, the object is removed from memory.

### Example:
```swift
class Person {
    var name: String
    init(name: String) {
        self.name = name
    }
}
```

### Easy Remember:
ARC = Automatically manage memory for class objects.

---

## 12. What is Strong Reference?

### Answer:
Strong reference increases the reference count of an object.  
By default, all references in Swift are strong.

Use strong when you want to keep the object alive.

### Example:
```swift
var person: Person? = Person(name: "Vishal")
```

### Easy Remember:
Strong = Keep object alive.

---

## 13. What is Weak Reference?

### Answer:
Weak reference does NOT increase reference count.  
It is always optional and automatically becomes nil  
when the object is removed from memory.

Used mostly in delegate patterns.

### Example:
```swift
class Car {
    weak var owner: Person?
}
```

### Easy Remember:
Weak = Does not keep object alive.

---

## 14. What is Unowned Reference?

### Answer:
Unowned reference does not increase reference count.  
It is non-optional and should be used when  
the object will never become nil during lifetime.

### Example:
```swift
class Engine {
    unowned var car: Car
    init(car: Car) {
        self.car = car
    }
}
```

### Easy Remember:
Unowned = No strong hold, but not optional.

---

## 15. What is Retain?

### Answer:
Retain means increasing the reference count of a class object.  
When a strong reference is created, retain count increases.

ARC handles retain automatically.

### Easy Remember:
Retain = Increase reference count.

---

## 16. What is Copy?

### Answer:
Copy creates a new instance with same value.  
Structs automatically create copies because they are value types.

### Example:
```swift
struct User {
    var name: String
}

var user1 = User(name: "Vishal")
var user2 = user1
user2.name = "Raj"
```

### Easy Remember:
Copy = New memory, separate value.

---

## 17. What is Retain Cycle?

### Answer:
Retain cycle happens when two class objects  
hold strong references to each other.  
Because of this, ARC cannot remove them from memory.

### Example:
```swift
class A {
    var b: B?
}

class B {
    var a: A?
}
```

### Easy Remember:
Retain Cycle = Strong reference loop.

---

## 18. How to Avoid Retain Cycle?

### Answer:
Use weak or unowned reference  
to break the strong reference cycle.

Mostly used in delegate and closure.

### Example:
```swift
class B {
    weak var a: A?
}
```

### Easy Remember:
Use weak/unowned to break cycle.

---

## 19. Memory Management in Swift?

### Answer:
Swift uses ARC for class types.  
Structs and enums are value types and stored on stack.  
Memory is automatically released when reference count becomes zero.

### Easy Remember:
Class → ARC  
Struct → Stack memory

---

## 20. How to Handle Memory in Structs?

### Answer:
Structs are value types.  
They create a copy when assigned to another variable.  
They do not use ARC.

### Example:
```swift
struct CarModel {
    var name: String
}
```

### Easy Remember:
Struct = Copy, no retain cycle.

---

# Section 3 – Swift Core Concepts

---

## 21. What are Value Types?

### Answer:
Value types store their own copy of data.  
When assigned to another variable, a new copy is created.

Struct, Enum and Tuple are value types.

### Example:
```swift
struct Car {
    var name: String
}

var car1 = Car(name: "BMW")
var car2 = car1
car2.name = "Audi"
```

### Easy Remember:
Value Type = Copy created.

---

## 22. What are Reference Types?

### Answer:
Reference types share the same memory location.  
When assigned to another variable, both point to same object.

Class is a reference type.

### Example:
```swift
class PersonRef {
    var name: String
    init(name: String) {
        self.name = name
    }
}
```

### Easy Remember:
Reference Type = Shared memory.

---

## 23. What is a Stored Property?

### Answer:
Stored property stores a value in memory.  
It is defined inside class or struct.

### Example:
```swift
struct User {
    var name: String
}
```

### Easy Remember:
Stored Property = Stores value.

---

## 24. What is a Computed Property?

### Answer:
Computed property does not store value.  
It calculates value every time it is accessed.

### Example:
```swift
struct Rectangle {
    var width: Double
    var height: Double
    
    var area: Double {
        return width * height
    }
}
```

### Easy Remember:
Computed = Calculated property.

---

## 25. What is Lazy Initialization?

### Answer:
Lazy property is initialized only when it is first used.  
Declared using `lazy` keyword.

### Example:
```swift
class DataManager {
    lazy var data: String = {
        return "Loaded Data"
    }()
}
```

### Easy Remember:
Lazy = Created when needed.

---

## 26. What is a Property Observer?

### Answer:
Property observer monitors value changes.  
We use `willSet` and `didSet`.

### Example:
```swift
var score: Int = 0 {
    didSet {
        print("New score: \(score)")
    }
}
```

### Easy Remember:
Observer = Watch value changes.

---

## 27. What is a Property Wrapper?

### Answer:
Property wrapper adds reusable logic to properties.  
Declared using `@propertyWrapper`.

### Example:
```swift
@propertyWrapper
struct Capitalized {
    private var value: String = ""
    
    var wrappedValue: String {
        get { value }
        set { value = newValue.capitalized }
    }
}

@Capitalized var name: String
```

### Easy Remember:
Wrapper = Add extra behavior to property.

---

## 28. What is Optional?

### Answer:
Optional means a variable can have a value or nil.  
Defined using `?`.

### Example:
```swift
var name: String?
```

### Easy Remember:
Optional = Value or nil.

---

## 29. What is Optional Binding?

### Answer:
Optional binding safely unwraps optional values  
using `if let` or `guard let`.

### Easy Remember:
Optional Binding = Safe unwrapping.

---

## 30. What is if let?

### Answer:
`if let` unwraps optional inside an if block.

### Example:
```swift
var name: String? = "Vishal"

if let safeName = name {
    print(safeName)
}
```

### Easy Remember:
if let = Safe unwrap in block.

---

## 31. What is guard let?

### Answer:
`guard let` unwraps optional and exits early  
if value is nil.

### Example:
```swift
func printName(name: String?) {
    guard let safeName = name else { return }
    print(safeName)
}
```

### Easy Remember:
guard let = Exit early if nil.

---

## 32. What is Tuple?

### Answer:
Tuple groups multiple values into one.  
It can store different data types.

### Example:
```swift
let person = ("Vishal", 28)
```

### Easy Remember:
Tuple = Multiple values in one.

---

## 33. What is defer?

### Answer:
`defer` executes code just before scope ends.  
Used for cleanup tasks.

### Example:
```swift
func test() {
    defer { print("End") }
    print("Start")
}
```

### Easy Remember:
defer = Run at end.

---

## 34. What is Inout Parameter?

### Answer:
`inout` allows a function to modify the original value.  
Use `&` when passing parameter.

### Example:
```swift
func increase(value: inout Int) {
    value += 1
}

var num = 5
increase(value: &num)
```

### Easy Remember:
inout = Modify original value.

---

## 35. What is Generics?

### Answer:
Generics allow writing flexible and reusable code  
that works with any data type.

### Example:
```swift
func swapValues<T>(_ a: inout T, _ b: inout T) {
    let temp = a
    a = b
    b = temp
}
```

### Easy Remember:
Generics = Reusable for any type.

---

## 36. What is Opaque Type?

### Answer:
Opaque type hides the exact return type  
using `some` keyword.

### Example:
```swift
func getView() -> some View {
    Text("Hello")
}
```

### Easy Remember:
Opaque = Hide real return type.

---

# Section 4 – Functional Programming

---

## 37. What is Closure?

### Answer:
Closure is a self-contained block of code  
that can be passed and used in your code.

Closures can capture and store references  
to variables from surrounding context.

### Example:
```swift
let greet = { (name: String) in
    print("Hello \(name)")
}

greet("Vishal")
```

### Easy Remember:
Closure = Function without name.

---

## 38. What is map?

### Answer:
`map` transforms each element in a collection  
and returns a new array.

### Example:
```swift
let numbers = [1, 2, 3]
let doubled = numbers.map { $0 * 2 }
```

### Easy Remember:
map = Transform each value.

---

## 39. What is compactMap?

### Answer:
`compactMap` removes nil values  
and unwraps optionals.

### Example:
```swift
let values = ["1", "2", "abc"]
let numbers = values.compactMap { Int($0) }
```

### Easy Remember:
compactMap = Remove nil + unwrap.

---

## 40. What is flatMap?

### Answer:
`flatMap` flattens nested collections  
into a single array.

### Example:
```swift
let array = [[1, 2], [3, 4]]
let flat = array.flatMap { $0 }
```

### Easy Remember:
flatMap = Flatten nested array.

---

## 41. What is filter?

### Answer:
`filter` returns elements  
that match a condition.

### Example:
```swift
let numbers = [1, 2, 3, 4]
let even = numbers.filter { $0 % 2 == 0 }
```

### Easy Remember:
filter = Keep matching values.

---

## 42. What is reduce?

### Answer:
`reduce` combines all values  
into a single result.

### Example:
```swift
let numbers = [1, 2, 3, 4]
let sum = numbers.reduce(0) { $0 + $1 }
```

### Easy Remember:
reduce = Combine into one value.

---

# Section 5 – Concurrency

---

## 43. What is Concurrency?

### Answer:
Concurrency means performing multiple tasks  
at the same time or overlapping time.

It helps improve app performance and responsiveness.

### Easy Remember:
Concurrency = Multiple tasks together.

---

## 44. What is Synchronous vs Asynchronous?

### Answer:

**Synchronous:**  
Tasks execute one after another.  
Next task waits until previous task finishes.

**Asynchronous:**  
Task runs in background.  
Program does not wait and continues execution.

### Example:
```swift
DispatchQueue.global().async {
    print("Background task")
}
```

### Easy Remember:
Sync = Wait  
Async = Don’t wait

---

## 45. What is GCD?

### Answer:
GCD (Grand Central Dispatch) is a low-level API  
used to manage concurrent tasks.

It uses DispatchQueue to run tasks  
on main or background threads.

### Example:
```swift
DispatchQueue.main.async {
    print("Update UI")
}
```

### Easy Remember:
GCD = Manage threads easily.

---

## 46. What is async/await?

### Answer:
`async/await` is modern Swift concurrency.  
It makes asynchronous code look like synchronous code.

It improves readability and avoids callback hell.

### Example:
```swift
func fetchData() async {
    print("Fetching data...")
}
```

### Easy Remember:
async/await = Clean async code.

---

## 47. What is Actor?

### Answer:
Actor is a reference type  
that protects its data from data races.

Only one task can access actor’s data at a time.

### Example:
```swift
actor Counter {
    var value = 0
    
    func increment() {
        value += 1
    }
}
```

### Easy Remember:
Actor = Safe shared data.

---

## 48. What is @MainActor?

### Answer:
`@MainActor` ensures code runs  
on the main thread.

Used when updating UI.

### Example:
```swift
@MainActor
class ViewModel {
    func updateUI() {
        print("UI Updated")
    }
}
```

### Easy Remember:
@MainActor = Run on main thread.

---

## 49. Explain Swift Concurrency.

### Answer:
Swift Concurrency includes:
- async/await
- Task
- Actor
- Structured concurrency

It provides safe and modern way  
to write asynchronous code.

### Easy Remember:
Swift Concurrency = Modern async system.

---



## 50. What is Task in Swift Concurrency?

### Answer:
`Task` creates a new asynchronous unit of work.

It is used to start async operations from synchronous code.

### Example:
```swift
Task {
    await fetchData()
}
```

### Easy Remember:
Task = Start async work.

---

## 51. What is async let?

### Answer:
`async let` allows running multiple async tasks in parallel.

### Example:
```swift
async let first = fetchData()
async let second = fetchData()

let result = await (first, second)
```

### Easy Remember:
async let = Parallel async tasks.

---

## 52. What is TaskGroup?

### Answer:
TaskGroup allows creating and managing
multiple child tasks dynamically.

Used in structured concurrency.

### Example:
```swift
await withTaskGroup(of: Int.self) { group in
    group.addTask { return 1 }
}
```

### Easy Remember:
TaskGroup = Manage multiple async tasks.

---

## 53. What is Continuation?

### Answer:
Continuation is used to convert
callback-based code into async/await.

### Example:
```swift
func fetch() async -> String {
    await withCheckedContinuation { continuation in
        continuation.resume(returning: "Done")
    }
}
```

### Easy Remember:
Continuation = Callback to async.

---

## 54. What is AsyncSequence?

### Answer:
AsyncSequence represents
a stream of asynchronous values.

### Example:
```swift
for await value in asyncSequence {
    print(value)
}
```

### Easy Remember:
AsyncSequence = Async data stream.

---

# Section 6 – Architecture

---

## 55. What is MVC?

### Answer:
MVC stands for Model-View-Controller.

- Model → Manages data
- View → Displays UI
- Controller → Handles logic and user interaction

It is the default architecture used in UIKit.

### Example:
```swift
class User {
    var name: String
    init(name: String) {
        self.name = name
    }
}
```

### Easy Remember:
MVC = Separate Data, UI, and Logic.

---

## 56. What is MVVM?

### Answer:
MVVM stands for Model-View-ViewModel.

- Model → Data
- View → UI
- ViewModel → Business logic

View communicates with ViewModel instead of directly with Model.

Mostly used in SwiftUI.

### Example:
```swift
class UserViewModel {
    var name: String = "Vishal"
}
```

### Easy Remember:
MVVM = View talks to ViewModel.

---

## 57. What is MVP?

### Answer:
MVP stands for Model-View-Presenter.

- Model → Data
- View → UI
- Presenter → Handles logic and updates View

View and Presenter communicate using protocols.

### Easy Remember:
MVP = Presenter controls View logic.

---

## 58. What is VIPER?

### Answer:
VIPER stands for:

- V → View
- I → Interactor
- P → Presenter
- E → Entity
- R → Router

It separates responsibilities strictly  
and is used in large-scale projects.

### Easy Remember:
VIPER = Highly structured & modular architecture.

---

## 59. What is Decorator Design Pattern?

### Answer:
Decorator pattern adds new behavior  
to an existing object without modifying its original code.

It wraps the original object.

### Example:
```swift
protocol Coffee {
    func cost() -> Double
}

class SimpleCoffee: Coffee {
    func cost() -> Double {
        return 5
    }
}

class MilkDecorator: Coffee {
    var coffee: Coffee
    
    init(coffee: Coffee) {
        self.coffee = coffee
    }
    
    func cost() -> Double {
        return coffee.cost() + 2
    }
}
```

### Easy Remember:
Decorator = Add functionality without changing original class.

---

## 60. What is Singleton?

### Answer:
Singleton ensures only one instance  
of a class exists throughout the app.

Used for shared managers like NetworkManager.

### Example:
```swift
class NetworkManager {
    static let shared = NetworkManager()
    
    private init() { }
}
```

### Easy Remember:
Singleton = Only one shared instance.

---
# Section 7 – UIKit & App Lifecycle

---

## 61. Explain the iOS Application Lifecycle.

### Answer:
The iOS Application Lifecycle describes  
the different states an app goes through  
from launch to termination.

It is managed by `UIApplicationDelegate`.

Main phases:
- App Launch
- Foreground
- Background
- Termination

### Easy Remember:
App Lifecycle = App state changes from launch to close.

---

## 62. What are iOS App States?

### Answer:

There are 5 app states:

1. **Not Running**
   → App is not launched or was terminated.

2. **Inactive**
   → App is in foreground but not receiving events  
   (e.g., phone call interruption).

3. **Active**
   → App is running in foreground and receiving events.

4. **Background**
   → App runs in background executing code.

5. **Suspended**
   → App is in memory but not executing code.

### Easy Remember:
NR → I → A → B → S

(Not Running → Inactive → Active → Background → Suspended)

---

## 63. What is UIViewController Lifecycle?

### Answer:
UIViewController lifecycle methods are called  
during view loading and appearance.

Main methods:

1. `viewDidLoad()`  
   → Called once when view is loaded into memory.

2. `viewWillAppear()`  
   → Called before view appears.

3. `viewDidAppear()`  
   → Called after view appears.

4. `viewWillDisappear()`  
   → Called before view disappears.

5. `viewDidDisappear()`  
   → Called after view disappears.

### Example:
```swift
override func viewDidLoad() {
    super.viewDidLoad()
    print("View Loaded")
}
```

### Easy Remember:
Load → Will Appear → Did Appear → Will Disappear → Did Disappear

---

## 64. What is Delegate?

### Answer:
Delegate is a design pattern  
used to pass data or events  
from one object to another.

It uses protocols for communication  
and helps achieve loose coupling between objects.

### Example:
```swift
protocol DataDelegate: AnyObject {
    func didReceiveData(_ data: String)
}
```

### Easy Remember:
Delegate = One object informs another.

---

## 65. What is Delegation?

### Answer:
Delegation is the process  
where one object assigns responsibility  
to another object using a protocol.

It is widely used in UIKit components like:

- UITableViewDelegate  
- UICollectionViewDelegate  
- UITextFieldDelegate  

### Easy Remember:
Delegation = Assign task using protocol.

---

## 66. What is KVO?

### Answer:
KVO (Key-Value Observing)  
allows observing changes to a property.

When the value changes,  
observers are automatically notified.

It is mainly used with Objective-C compatible properties.

### Easy Remember:
KVO = Observe property changes automatically.

---

## 67. What is NotificationCenter?

### Answer:
NotificationCenter is used  
to broadcast information  
to multiple observers.

It follows the publish-subscribe pattern.

Multiple objects can listen to the same notification.

### Example:
```swift
NotificationCenter.default.post(
    name: Notification.Name("DataUpdated"),
    object: nil
)
```

### Easy Remember:
NotificationCenter = Broadcast message to many listeners.

---

## 68. What is CoreData?

### Answer:
CoreData is a framework  
used to store and manage local data  
in iOS applications.

It is not just a database —  
it is an object graph and persistence framework.

Features:
- Data persistence
- Relationships
- Fetching and filtering
- Memory management

### Easy Remember:
CoreData = Local storage + object management system.

---

# Section 8 – App Distribution & Accounts

---

## 69. What is Code Signing?

### Answer:
Code Signing ensures that the app is created by a trusted developer  
and has not been modified.

It uses:
- Certificate
- Provisioning Profile
- Apple Developer Account

Without code signing, app cannot run on real device.

### Easy Remember:
Code Signing = Verify developer + secure app.

---

## 70. What is an Apple Developer Account?

### Answer:
Apple Developer Account allows developers  
to build, test and publish apps on App Store.

Cost: $99 per year.

Used for:
- App Store distribution
- TestFlight testing
- Push Notifications
- In-App Purchases

### Easy Remember:
Developer Account = Publish apps on App Store.

---

## 71. What is an Enterprise Account?

### Answer:
Enterprise Account is used by companies  
to distribute internal apps to employees  
without publishing on App Store.

Cost: $299 per year.

Apps are distributed privately.

### Easy Remember:
Enterprise = Internal company apps only.

---

## 72. What is TestFlight?

### Answer:
TestFlight is Apple’s official tool  
for beta testing iOS apps.

Developers can invite testers  
before releasing app to App Store.

### Easy Remember:
TestFlight = Beta testing platform.

---

## 73. How many testers are allowed in TestFlight?

### Answer:
TestFlight allows:

- 100 internal testers  
- Up to 10,000 external testers  

Each build is valid for 90 days.

### Easy Remember:
100 internal + 10,000 external testers.

---

## 74. How many types of In-App Purchases (IAP) are there?

### Answer:
There are 4 types of IAP:

1. Consumable  
2. Non-Consumable  
3. Auto-Renewable Subscription  
4. Non-Renewing Subscription  

### Easy Remember:
Consumable, Non-Consumable, Subscriptions (Auto + Non-auto).

---

## 75. How to Upload an App to the App Store?

### Answer:
Steps to upload app:

1. Create App ID & Certificates
2. Archive app in Xcode
3. Validate build
4. Upload to App Store Connect
5. Add metadata (screenshots, description)
6. Submit for review

After approval, app becomes live on App Store.

### Easy Remember:
Archive → Upload → Submit → Review → Live

---

# Section 9 – Git

---

## 76. What is cherry-pick in Git?

### Answer:
`git cherry-pick` is a Git command  
used to apply a specific commit  
from one branch into another branch.

It copies only the selected commit  
instead of merging the entire branch.

### Example:
```bash
git cherry-pick <commit-hash>
```

---

# Section 10 – Advanced Swift Concepts

---

## 77. What are SOLID Principles?

### Answer:
SOLID is a set of 5 design principles:

S – Single Responsibility Principle  
O – Open/Closed Principle  
L – Liskov Substitution Principle  
I – Interface Segregation Principle  
D – Dependency Inversion Principle  

These principles help write clean and maintainable code.

### Easy Remember:
SOLID = Rules for clean architecture.

---

## 78. What is the difference between try, try?, and try!?

### Answer:

- `try` → Used with do-catch to handle errors.
- `try?` → Returns optional. If error occurs, returns nil.
- `try!` → Force try. Crashes if error occurs.

### Example:
```swift
do {
    try someFunction()
} catch {
    print(error)
}

let result = try? someFunction()
let force = try! someFunction()
```

### Easy Remember:
try = handle  
try? = optional  
try! = crash if fails

---

## 79. What is Combine?

### Answer:
Combine is a framework by Apple  
used for reactive programming.

It allows handling asynchronous events  
using publishers and subscribers.

Used heavily in SwiftUI and MVVM.

### Easy Remember:
Combine = Reactive programming framework.

---

## 80. What is Data Binding?

### Answer:
Data Binding connects UI with data source  
so when data changes, UI updates automatically.

Used in:
- MVVM pattern

### Easy Remember:
Data Binding = Auto UI update when data changes.

---

## 81. Explain Stack vs Heap Memory.

### Answer:

Stack:
- Stores value types
- Faster
- Automatically managed

Heap:
- Stores reference types
- Managed by ARC
- Slower than stack

### Easy Remember:
Struct → Stack  
Class → Heap

---

## 82. What is async let?

### Answer:
`async let` allows running multiple asynchronous tasks in parallel.

### Example:
```swift
async let first = fetchData()
async let second = fetchData()

let result = await (first, second)
```

### Easy Remember:
async let = Run async tasks in parallel.

---

## 83. What is TaskGroup?

### Answer:
TaskGroup allows creating and managing  
multiple child tasks dynamically.

Used for structured concurrency.

### Example:
```swift
await withTaskGroup(of: Int.self) { group in
    group.addTask { return 1 }
}
```

### Easy Remember:
TaskGroup = Manage multiple async tasks.

---


