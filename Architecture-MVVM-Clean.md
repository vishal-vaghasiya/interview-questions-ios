# interview-questions-ios
iOS interview questions with quick revision notes for Swift, UIKit, SwiftUI, Objective-C, and OOPS.

## iOS Architecture – MVC, MVVM & Clean Architecture (Interview Notes)

Each topic includes a **short definition** and a **small example** for easy understanding and interview revision.

---

## What is Architecture?
Architecture defines how code is structured and how responsibilities are separated in an application.

---

## Why Architecture is Important?
- Scalability
- Testability
- Maintainability
- Clear separation of concerns

---

## MVC (Model–View–Controller)

### What is MVC?
Apple’s default architecture pattern.

- Model → Data & business logic  
- View → UI  
- Controller → Handles user interaction  

### MVC Flow
View → Controller → Model → Controller → View

### MVC Example
```swift
class User {
    let name: String
    init(name: String) {
        self.name = name
    }
}

class UserViewController: UIViewController {
    var user: User?
}
```

### Problem with MVC
- Massive View Controllers
- Business logic mixed with UI

---

## MVVM (Model–View–ViewModel)

### What is MVVM?
Separates UI from business logic using ViewModel.

- Model → Data
- ViewModel → Business logic & formatting
- View → UI

### MVVM Flow
View ↔ ViewModel → Model

### MVVM Example
```swift
class UserViewModel: ObservableObject {
    @Published var displayName: String = ""
    
    func load(user: User) {
        displayName = user.name.uppercased()
    }
}
```

### Advantages of MVVM
- Better testability
- Cleaner UI code
- Works perfectly with SwiftUI

### Disadvantages of MVVM
- Extra layer
- Overkill for small apps

---

## Clean Architecture

### What is Clean Architecture?
Clean Architecture separates code into independent layers.

### Layers
1. Presentation (UI)
2. Domain (Business rules)
3. Data (API / DB)

### Dependency Rule
Inner layers should not depend on outer layers.

---

## Clean Architecture Flow
UI → Use Case → Repository → Data Source

---

## Clean Architecture Example

### Domain Layer
```swift
protocol GetUserUseCase {
    func execute() -> User
}
```

### Data Layer
```swift
class UserRepository {
    func fetchUser() -> User {
        User(name: "Vishal")
    }
}
```

### Presentation Layer
```swift
class UserViewModel {
    let repository = UserRepository()
    
    func loadUser() -> String {
        repository.fetchUser().name
    }
}
```

---

## MVC vs MVVM vs Clean

| Feature | MVC | MVVM | Clean |
|------|-----|------|------|
| Complexity | Low | Medium | High |
| Testability | Low | High | Very High |
| Scalability | Low | Medium | High |
| SwiftUI Friendly | ❌ | ✅ | ✅ |

---

## SOLID & Architecture
Clean Architecture follows SOLID principles.

---

## When to Use Which?
- Small app → MVC
- Medium app → MVVM
- Large app → Clean Architecture

---

## Common Interview Questions
- Why MVC causes Massive View Controller?
- Why MVVM is better for SwiftUI?
- How Clean Architecture improves testability?
- Difference between Repository & UseCase?

---

## Interview One-Liners
- MVC → Apple default
- MVVM → UI & logic separation
- Clean → Scalable & testable
- ViewModel → Business logic holder
- UseCase → Single responsibility
