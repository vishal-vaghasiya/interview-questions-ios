# Swift Interview Questions

---

# Section 1 – OOPS Concepts

---

## 1. What is a Class?

### Answer:
A class is a blueprint used to create objects.  
It defines properties (variables) and methods (functions).  
Class is a reference type and is stored in heap memory.

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
Structs and enums are value types and are typically stored on the stack.  
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

let rect = Rectangle(width: 5, height: 4)
print("Area:", rect.area)
```

Output:
```swift
Area: 20.0
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
print("Before:", num)

increase(value: &num)

print("After:", num)
```

Output:
```swift
Before: 5
After: 6
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

var first = 10
var second = 20

print("Before Swap:", first, second)

swapValues(&first, &second)

print("After Swap:", first, second)
```

Output:
```swift
Before Swap: 10 20
After Swap: 20 10
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
protocol Shape {
    func draw()
}

struct Circle: Shape {
    func draw() {
        print("Drawing Circle")
    }
}

func getShape() -> some Shape {
    return Circle()
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

# Easy Remember:
Singleton = Only one shared instance.

---

## 61. What is Coordinator Pattern?

### Answer:
Coordinator Pattern is an architectural pattern  
used to manage navigation logic outside of ViewControllers.

Instead of handling navigation inside ViewController,  
a separate Coordinator object controls screen flow.

It improves:
- Separation of concerns
- Testability
- Reusability
- Cleaner ViewControllers

### Example:
```swift
protocol Coordinator {
    func start()
}

class AppCoordinator: Coordinator {
    
    var navigationController: UINavigationController
    
    init(navigationController: UINavigationController) {
        self.navigationController = navigationController
    }
    
    func start() {
        let viewController = UIViewController()
        navigationController.pushViewController(viewController, animated: true)
    }
}
```

### Easy Remember:
Coordinator = Handles navigation outside ViewController.

---
# Section 7 – UIKit & App Lifecycle

---

## 62. Explain the iOS Application Lifecycle.

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

## 63. What are iOS App States?

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

## 64. What is UIViewController Lifecycle?

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

## 65. What is Delegate?

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

## 66. What is Delegation?

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

## 67. What is KVO?

### Answer:
KVO (Key-Value Observing)  
allows observing changes to a property.

When the value changes,  
observers are automatically notified.

It is mainly used with Objective-C compatible properties.

### Easy Remember:
KVO = Observe property changes automatically.

---

## 68. What is NotificationCenter?

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

## 69. What is CoreData?

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

## 70. What is SwiftData?

### Answer:
SwiftData is a modern data persistence framework introduced by Apple in iOS 17.

It is built on top of CoreData but designed specifically for Swift and SwiftUI.

SwiftData removes boilerplate code and makes data storage simpler and more developer-friendly.

### Example:
```swift
@Model
class User {
    var name: String
    var age: Int
    
    init(name: String, age: Int) {
        self.name = name
        self.age = age
    }
}
```

### Easy Remember:
SwiftData = Modern Swift-friendly CoreData.

---

## 71. Difference Between CoreData vs SwiftData

### Answer:

| Feature | CoreData | SwiftData |
|----------|------------|------------|
| Introduced | 2005 | 2023 (iOS 17) |
| Data Model | .xcdatamodeld file | @Model class |
| Boilerplate | More | Less |
| SwiftUI Integration | Manual setup | Automatic |
| Language Style | Objective-C style | Pure Swift |

### Easy Remember:
CoreData = Traditional  
SwiftData = Modern & Simple

---
---

# Section 8 – App Distribution & Accounts

---

## 72. What is Code Signing?

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

## 73. What is an Apple Developer Account?

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

## 74. What is an Enterprise Account?

### Answer:
Enterprise Account is used by companies  
to distribute internal apps to employees  
without publishing on App Store.

Cost: $299 per year.

Apps are distributed privately.

### Easy Remember:
Enterprise = Internal company apps only.

---

## 75. What is TestFlight?

### Answer:
TestFlight is Apple’s official tool  
for beta testing iOS apps.

Developers can invite testers  
before releasing app to App Store.

### Easy Remember:
TestFlight = Beta testing platform.

---

## 76. How many testers are allowed in TestFlight?

### Answer:
TestFlight allows:

- 100 internal testers  
- Up to 10,000 external testers  

Each build is valid for 90 days.

### Easy Remember:
100 internal + 10,000 external testers.

---

## 77. How many types of In-App Purchases (IAP) are there?

### Answer:
There are 4 types of IAP:

1. Consumable  
2. Non-Consumable  
3. Auto-Renewable Subscription  
4. Non-Renewing Subscription  

### Easy Remember:
Consumable, Non-Consumable, Subscriptions (Auto + Non-auto).

---

## 78. How to Upload an App to the App Store?

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

## 79. What is cherry-pick in Git?

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

# Section 10 – Security & Storage

---

## 80. What are SOLID Principles?

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

## 81. What is the difference between try, try?, and try!?

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

## 82. What is Combine?

### Answer:
Combine is a framework by Apple  
used for reactive programming.

It allows handling asynchronous events  
using publishers and subscribers.

Used heavily in SwiftUI and MVVM.

### Easy Remember:
Combine = Reactive programming framework.

---

### Example:

```swift
import Combine

class ViewModel {
    var cancellables = Set<AnyCancellable>()
    @Published var name: String = ""
    
    init() {
        $name
            .sink { newValue in
                print("Name updated to:", newValue)
            }
            .store(in: &cancellables)
    }
}

let vm = ViewModel()
vm.name = "Vishal"
```

Output:
```swift
Name updated to: Vishal
```

### Explanation:
- `@Published` creates a publisher.
- `$name` observes changes.
- `sink` receives updated values.
- `AnyCancellable` stores the subscription.

---

---

## 83. What is Data Binding?

### Answer:
Data Binding connects UI with data source  
so when data changes, UI updates automatically.

Used in:
- MVVM pattern

### Easy Remember:
Data Binding = Auto UI update when data changes.

---

## 84. Explain Stack vs Heap Memory.

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

## 85. Mention the main features of Swift.

### Answer:
Main features of Swift:

- Safe and secure (type safety)
- Automatic memory management (ARC)
- Optionals to avoid null crashes
- Powerful generics
- Protocol-Oriented Programming
- Fast performance
- Modern concurrency (async/await)

### Easy Remember:
Swift = Safe + Fast + Modern.

---

## 86. What is an Extension?

### Answer:
Extension allows adding new functionality  
to an existing class, struct, enum, or protocol  
without modifying the original source code.

Used to:
- Add methods
- Add computed properties
- Conform to protocols

### Example:
```swift
extension String {
    func greet() -> String {
        return "Hello \(self)"
    }
}
```

### Easy Remember:
Extension = Add new features without changing original code.

---


## 87. What is Enum?

### Answer:
Enum (Enumeration) is a type  
that defines a group of related values.

Enums in Swift are powerful and can:
- Have associated values
- Have methods
- Conform to protocols

### Example:
```swift
enum Direction {
    case north
    case south
    case east
    case west
}
```

### Easy Remember:
Enum = Group of related cases.

---

### 🔐 Security Topics

## 88. What is Keychain and why is it used?

### Answer:
Keychain is a secure storage system provided by iOS  
to store sensitive information in encrypted form.

It is mainly used to store:
- Passwords
- Access Tokens
- Refresh Tokens
- API Keys
- Encryption Keys
- Biometric-protected credentials

Keychain data is encrypted and managed by the iOS security system.

Unlike UserDefaults, Keychain is secure  
and should always be used for confidential data.

---

## Steps to Store Data in Keychain:

1. Convert value into `Data`
2. Create a query dictionary
3. Specify keychain class (kSecClassGenericPassword)
4. Add attributes (account, service)
5. Call `SecItemAdd`
6. Handle status result

---

### Example – Save Data to Keychain:

```swift
import Security

func saveToKeychain(key: String, value: String) {
    
    let data = value.data(using: .utf8)!
    
    // Remove existing item (if any)
    let deleteQuery: [String: Any] = [
        kSecClass as String: kSecClassGenericPassword,
        kSecAttrAccount as String: key
    ]
    SecItemDelete(deleteQuery as CFDictionary)
    
    // Add new item
    let query: [String: Any] = [
        kSecClass as String: kSecClassGenericPassword,
        kSecAttrAccount as String: key,
        kSecValueData as String: data
    ]
    
    let status = SecItemAdd(query as CFDictionary, nil)
    
    if status == errSecSuccess {
        print("Saved successfully")
    } else {
        print("Error saving:", status)
    }
}
```

---

### Example – Read Data from Keychain:

```swift
func readFromKeychain(key: String) -> String? {
    
    let query: [String: Any] = [
        kSecClass as String: kSecClassGenericPassword,
        kSecAttrAccount as String: key,
        kSecReturnData as String: true,
        kSecMatchLimit as String: kSecMatchLimitOne
    ]
    
    var dataTypeRef: AnyObject?
    let status = SecItemCopyMatching(query as CFDictionary, &dataTypeRef)
    
    if status == errSecSuccess,
       let data = dataTypeRef as? Data,
       let value = String(data: data, encoding: .utf8) {
        return value
    }
    
    return nil
}
```

---

### Easy Remember:
Keychain = Encrypted storage for passwords & tokens.

---


## 89. Keychain vs UserDefaults (Interview Comparison)

### Answer:

| Feature | Keychain | UserDefaults |
|----------|------------|--------------|
| Security | Encrypted | Not encrypted |
| Used For | Passwords, Tokens, API Keys | App settings, Preferences |
| Data Type | Small sensitive data | Small non-sensitive data |
| Survives Reinstall | Yes (by default) | No |
| Access Control | Can use Face ID / Touch ID | No biometric protection |

### When to Use Keychain:
- Login tokens
- Passwords
- Secure credentials
- Encryption keys

### When to Use UserDefaults:
- Theme preference
- Login flag (isLoggedIn)
- App settings
- Simple small values

### Example (UserDefaults):
```swift
UserDefaults.standard.set(true, forKey: "isLoggedIn")
```

---

## 90. Can I store user password in iOS?

### Answer:
Yes, but only in **Keychain**.

User password is sensitive data  
and should NEVER be stored in:

- UserDefaults
- Plist
- CoreData
- Local files

The correct and secure place to store user password  
is the iOS **Keychain**, because:

- It is encrypted
- Managed by iOS security system
- Can be protected with Face ID / Touch ID
- More secure than normal storage

### Important Best Practice:
In real-world apps, we usually:
- Do NOT store raw password
- Store authentication token instead

Password should only be stored  
if absolutely required.

### Example:
```swift
// Save password securely in Keychain
saveToKeychain(key: "userPassword", value: "123456")
```

### Easy Remember:
Password → Always Keychain  
Never UserDefaults.

---

## 91. What type of data is stored in Info.plist?

### Answer:
Info.plist (Information Property List) stores  
app configuration and metadata required by iOS.

It is NOT used to store sensitive data.

Info.plist contains:

- App name
- Bundle identifier
- Version number
- Build number
- Required device capabilities
- Privacy permission descriptions (Camera, Location, etc.)
- App Transport Security settings
- URL Schemes
- Background modes

### Important:
Info.plist is readable and included inside the app bundle.  
Do NOT store:

- Passwords
- API secrets
- Tokens
- Sensitive credentials


### Example (Privacy Permission in Info.plist):

```xml
<key>NSCameraUsageDescription</key>
<string>This app needs camera access to scan plants.</string>
```

---

## 92. How to Secure API Keys in iOS?

### Answer:
API keys should NEVER be hardcoded directly inside the app  
because the app bundle can be reverse engineered.

Not secure places:
- Hardcoded strings
- Info.plist
- UserDefaults
- Public GitHub repositories

### Best Practices:
- Store sensitive keys on server
- Call APIs through backend
- Use short-lived tokens instead of static API keys
- Use .xcconfig for environment separation (not for strong security)

### Example (Wrong Way):
```swift
let apiKey = "MY_SECRET_KEY"
```

### Better Approach:
- Keep API key on server
- App calls backend
- Backend communicates with third-party service

### Easy Remember:
Never trust client-side storage for secret API keys.

---

## 93. What happens to Keychain data after app uninstall?

### Answer:
By default, Keychain data survives app uninstall.

This means:
- If user deletes app
- Reinstalls app
- Keychain data may still exist

This is useful for:
- Auto-login
- Persistent credentials

To remove Keychain data manually:
```swift
SecItemDelete(query as CFDictionary)
```

### Easy Remember:
Keychain survives uninstall (by default).

---

## 94. How to Protect Sensitive Data in iOS?

### Answer:
To protect sensitive data:

- Use HTTPS (never HTTP)
- Use Keychain for tokens and passwords
- Avoid logging sensitive information
- Avoid storing secrets in app bundle
- Use SSL Pinning (advanced)
- Use server-side validation

### Example (Avoid Logging Tokens):
```swift
print("User logged in") // Correct
// Avoid printing tokens in console
```

### Easy Remember:
Protect data at:
- Storage
- Network
- Logging
- Server

---

## 95. What is Data Protection in iOS?

### Answer:
Data Protection encrypts files stored on device  
based on the device lock state.

iOS provides file protection levels such as:

- NSFileProtectionComplete
- NSFileProtectionCompleteUntilFirstUserAuthentication
- NSFileProtectionNone

These control when files are accessible.

### Example:
```swift
try FileManager.default.setAttributes(
    [.protectionKey: FileProtectionType.complete],
    ofItemAtPath: filePath
)
```

### Easy Remember:
Data Protection = File encryption based on device lock state.

---
### 💾 Storage Topics

## 96. What is Persistent Storage in iOS and what are its types?

### Answer:
Persistent storage refers to saving data in a way  
that it remains available even after:

- The app is closed
- The device is restarted

It is used to store user data permanently.

---

### Common Persistent Storage Options in iOS:

1. **UserDefaults**
   - Used for small non-sensitive data
   - Example: Login flag, theme preference

2. **Keychain**
   - Used for secure sensitive data
   - Example: Passwords, access tokens

3. **CoreData**
   - Used for structured and relational data
   - Example: Notes app, task manager

4. **FileManager**
   - Used for storing files (images, PDFs, JSON)
   - Example: Downloaded documents

5. **SQLite**
   - Lightweight local database
   - Used in large structured data apps

---

### Example 1 – UserDefaults

```swift
UserDefaults.standard.set("Vishal", forKey: "username")
let name = UserDefaults.standard.string(forKey: "username")
```

---

# Section 11 – Advanced Swift & Networking

---

### 🚀 Advanced Swift & Concurrency

## 97. What is the difference between Struct and Class?

### Answer:

| Feature | Struct | Class |
|----------|--------|--------|
| Type | Value Type | Reference Type |
| Memory | Stack (typically) | Heap |
| Inheritance | Not supported | Supported |
| ARC | Not used | Used |
| Mutability | Safer by default | More flexible |

### Easy Remember:
Struct = Value  
Class = Reference

---

## 98. What is Access Control in Swift?

### Answer:
Access control defines how code is accessed from different parts of the app.

Levels:
- open
- public
- internal (default)
- fileprivate
- private

### Example:
```swift
private var name: String
```

### Easy Remember:
Access Control = Control visibility.

---

## 99. What is Error Handling in Swift?

### Answer:
Swift uses `do-try-catch` for error handling.

Steps:
- Define error type
- Throw error
- Catch error

### Example:
```swift
enum LoginError: Error {
    case invalidCredentials
}

func login() throws {
    throw LoginError.invalidCredentials
}

do {
    try login()
} catch {
    print(error)
}
```

### Easy Remember:
Error Handling = do-try-catch.

---

## 100. What is Dependency Injection?

### Answer:
Dependency Injection means providing dependencies from outside  
instead of creating them inside the class.

It improves testability and flexibility.

### Example:
```swift
class NetworkService { }

class UserViewModel {
    let service: NetworkService
    
    init(service: NetworkService) {
        self.service = service
    }
}
```

### Easy Remember:
Inject dependency from outside.

---

## 101. What is Copy-on-Write (COW)?

### Answer:
Copy-on-Write means data is copied  
only when it is modified.

Used in:
- Array
- Dictionary
- String

### Example:
```swift
var arr1 = [1,2,3]
var arr2 = arr1
arr2.append(4)
```

### Easy Remember:
COW = Copy only when changed.

---

## 102. What is Equatable and Hashable?

### Answer:
Equatable allows comparing two instances.  
Hashable allows using objects in Set or Dictionary.

### Example:
```swift
struct User: Equatable {
    var id: Int
}
```

### Easy Remember:
Equatable = Compare  
Hashable = Store in Set/Dictionary

---

### 🌐 Networking Topics

## 103. What is URLSession?

### Answer:
URLSession is used to perform network requests.

### Example:
```swift
URLSession.shared.dataTask(with: URL(string: "https://example.com")!) { data, response, error in
    print("Response received")
}.resume()
```

### Easy Remember:
URLSession = Networking API.

---

## 104. What is Autoreleasepool?

### Answer:
Autoreleasepool releases temporary objects  
at the end of a scope.

Used in loops or memory-heavy operations.

### Example:
```swift
for _ in 0..<1000 {
    autoreleasepool {
        print("Inside pool")
    }
}
```

### Easy Remember:
Autoreleasepool = Release temp memory early.

---

## 105. What is Codable?

### Answer:
Codable is a protocol used  
to encode and decode JSON data.

It combines:
- Encodable
- Decodable

### Example:
```swift
struct User: Codable {
    var name: String
}
```

### Easy Remember:
Codable = Convert model ↔ JSON.

---

## 106. What is DispatchGroup?

### Answer:
DispatchGroup allows grouping multiple tasks  
and notifying when all tasks complete.

### Example:
```swift
let group = DispatchGroup()

group.enter()
DispatchQueue.global().async {
    print("Task 1")
    group.leave()
}

group.notify(queue: .main) {
    print("All tasks completed")
}
```

### Easy Remember:
DispatchGroup = Wait for multiple tasks.

---

## 107. Difference between OperationQueue and GCD?

### Answer:

| GCD | OperationQueue |
|-----|----------------|
| Lightweight | Higher-level API |
| Uses DispatchQueue | Uses Operation objects |
| Less control | More control (cancel, dependencies) |
| Simple tasks | Complex task management |

### Easy Remember:
GCD = Simple concurrency  
OperationQueue = Advanced control

---
