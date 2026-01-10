# interview-questions-ios
iOS interview questions with quick revision notes for Swift, UIKit, SwiftUI, Objective-C, and OOPS.

# UIKit Interview Questions – Definitions & Examples

Each topic includes a **short definition** and a **small example** for easy understanding and quick interview revision.

---

## What is UIKit?
UIKit is Apple’s framework used to build iOS user interfaces using an **imperative programming approach**.

```swift
let label = UILabel()
label.text = "Hello UIKit"
```

---

## What is MVC?
MVC stands for **Model–View–Controller**, Apple’s default architecture pattern.

- **Model** → Data & business logic  
- **View** → UI components  
- **Controller** → Connects Model and View  

---

## What is MVVM?
MVVM separates UI and business logic.

- **Model** → Data
- **ViewModel** → Business logic
- **View** → UI

---

## What is Core Data?
Core Data is an **object graph and persistence framework**, not a database.

- Manages object relationships
- Lazy loading
- Uses SQLite internally

---

## iOS App States
1. Non-running  
2. Inactive  
3. Active  
4. Background  
5. Suspended  

---

## UIViewController Lifecycle
Called when a view appears and disappears.

```swift
override func viewDidLoad() {}
override func viewWillAppear(_ animated: Bool) {}
override func viewDidAppear(_ animated: Bool) {}
override func viewWillDisappear(_ animated: Bool) {}
override func viewDidDisappear(_ animated: Bool) {}
```

---

## What is loadView()?
Creates the view hierarchy manually.

```swift
override func loadView() {
    self.view = UIView()
}
```

---

## What is viewDidLoad()?
Called once when the view is loaded into memory.

---

## What is viewWillAppear?
Called before the view appears on screen.

---

## What is viewDidAppear?
Called after the view appears on screen.

---

## What is viewWillDisappear?
Called before the view disappears.

---

## What is viewDidDisappear?
Called after the view disappears.

---

## What is Delegation?
A **one-to-one communication** pattern using protocols.

```swift
protocol ButtonDelegate {
    func didTapButton()
}
```

---

## What is KVO?
Key-Value Observing allows observing property changes.

```swift
observe(\.isFinished) { _, change in }
```

---

## What is NotificationCenter?
A **broadcast mechanism** for loose coupling.

```swift
NotificationCenter.default.post(
    name: Notification.Name("Event"),
    object: nil
)
```

---

## What is Target-Action?
Used to handle UI events.

```swift
button.addTarget(self, action: #selector(tapped), for: .touchUpInside)
```

---

## What is Responder Chain?
Chain that handles events like touches and actions.

---

## What is RunLoop?
Manages input events and timers on a thread.

---

## What is GCD?
Manages concurrent execution.

```swift
DispatchQueue.global().async {
    DispatchQueue.main.async {
        print("UI Update")
    }
}
```

---

## Main Thread vs Background Thread
- UI updates → Main thread
- Heavy work → Background thread

---

## What is OperationQueue?
Higher-level alternative to GCD.

```swift
let queue = OperationQueue()
queue.addOperation {
    print("Task")
}
```

---

## What is AutoreleasePool?
Releases temporary objects earlier to save memory.

```swift
autoreleasepool {
    // memory intensive code
}
```

---

## What is Memory Leak?
Memory not released properly.

**Common cause:** retain cycles

---

## What is Retain Cycle?
Objects holding strong references to each other.

---

## How to avoid Retain Cycle?
Use `weak` or `unowned`.

```swift
[weak self] in
```

---

## Retain vs Copy
- **retain** → same object
- **copy** → new object

---

## What is Code Signing?
Ensures app authenticity.

- Required for device
- Required for App Store

---

## What is TestFlight?
Apple’s beta testing platform.

- Up to **10,000 testers**

---

## In-App Purchases (IAP)
1. Consumable  
2. Non-Consumable  
3. Auto-Renewable Subscription  
4. Non-Renewing Subscription  

---

## Developer vs Enterprise Account

| Feature | Developer | Enterprise |
|------|-----------|-----------|
| Cost | $99/year | $299/year |
| App Store | Yes | No |
| Internal Distribution | Limited | Unlimited |

---

## What is App Thinning?
Optimizes app size per device.

---

## What is Bitcode?
Intermediate representation used by Apple for optimization.

---

## What is Universal Links?
Deep links that open apps instead of browser.

---

## What is Deep Linking?
Navigate users to specific app screens.

---

## What is SceneDelegate?
Manages app UI lifecycle (iOS 13+).

---

## What is AppDelegate?
Handles app-level events.

---

## What is Safe Area?
Ensures UI avoids system elements.

---

## What is Auto Layout?
Constraint-based layout system.

---

## What is Intrinsic Content Size?
Default size of UI elements.

---

## What is ReuseIdentifier?
Used to reuse table/collection view cells.

---

## UITableView vs UICollectionView
- UITableView → Linear layout
- UICollectionView → Custom layouts

---

## What is Diffable Data Source?
Modern API for managing UI data updates.

---

## What is Storyboard?
Visual UI builder.

---

## Storyboard vs XIB
- Storyboard → Multiple screens
- XIB → Single view

---

## What is Programmatic UI?
UI built using code instead of Interface Builder.

---

## What is Objective-C Interoperability?
Swift can interact with Objective-C using bridging headers.

---

## What is @objc?
Exposes Swift code to Objective-C runtime.

```swift
@objc func tapped() {}
```

---
