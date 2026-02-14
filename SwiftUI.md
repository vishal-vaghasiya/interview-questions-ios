# SwiftUI Interview Questions

---

# Section 1 – SwiftUI Basics

---

## 1. What is SwiftUI?

### Answer:
SwiftUI is a modern UI framework by Apple  
used to build user interfaces declaratively.

It works across:
- iOS
- iPadOS
- macOS
- watchOS
- tvOS

### Easy Remember:
SwiftUI = Declarative UI framework by Apple.

---

## 2. What is Declarative UI?

### Answer:
Declarative UI means you describe  
what the UI should look like,  
and SwiftUI handles how to update it.

### Example:
```swift
Text("Hello World")
```

### Easy Remember:
Declarative = Describe UI, system updates it.

---

## 3. What is @State?

### Answer:
@State is a property wrapper  
used to store local mutable state in a View.

When value changes, UI automatically updates.

### Example:
```swift
@State private var count = 0
```

### Easy Remember:
@State = Local view state.

---

## 4. What is @Binding?

### Answer:
@Binding is used to pass a reference  
of a state variable to another view.

It allows child view to modify parent data.

### Example:
```swift
@Binding var count: Int
```

### Easy Remember:
@Binding = Two-way data connection.

---

## 5. What is @StateObject?

### Answer:
@StateObject is used to create  
and own a reference-type object in a view.

Used when view creates the ViewModel.

### Easy Remember:
@StateObject = View owns object.

---

## 6. What is @ObservedObject?

### Answer:
@ObservedObject is used to observe  
an external object created elsewhere.

View does not own the object.

### Easy Remember:
@ObservedObject = View observes object.

---

## 7. What is @EnvironmentObject?

### Answer:
@EnvironmentObject shares data  
across multiple views globally.

It avoids passing data manually through hierarchy.

### Easy Remember:
@EnvironmentObject = Shared global object.

---

## 8. What is @Published?

### Answer:
@Published is used inside ObservableObject  
to notify SwiftUI when value changes.

### Example:
```swift
class ViewModel: ObservableObject {
    @Published var name = ""
}
```

### Easy Remember:
@Published = Notify UI when value changes.

---

## 9. What is @ViewBuilder?

### Answer:
@ViewBuilder allows returning  
multiple views from a function  
without explicitly wrapping them.

### Easy Remember:
@ViewBuilder = Build multiple views.

---

## 10. What is Data Binding in SwiftUI?

### Answer:
Data binding automatically updates UI  
when underlying data changes.

SwiftUI provides:
- @State
- @Binding
- @ObservedObject
- @EnvironmentObject

### Easy Remember:
Data Binding = UI auto updates.

---

# Section 2 – SwiftUI Lifecycle

---

## 11. What is SwiftUI App Lifecycle?

### Answer:
SwiftUI uses the `@main` App protocol  
instead of AppDelegate by default.

### Example:
```swift
@main
struct MyApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}
```

### Easy Remember:
SwiftUI Lifecycle = App protocol based.

---

## 12. What is .onAppear()?

### Answer:
.onAppear() runs code  
when view appears on screen.

### Example:
```swift
.onAppear {
    print("View appeared")
}
```

### Easy Remember:
onAppear = When view shows.

---

## 13. What is .onDisappear()?

### Answer:
.onDisappear() runs code  
when view disappears.

### Easy Remember:
onDisappear = When view hides.

---

## 14. What is Task in SwiftUI?

### Answer:
Task is used to perform  
asynchronous work inside a View.

### Example:
```swift
.task {
    await fetchData()
}
```

### Easy Remember:
.task = Run async work in view.

---

# Section 3 – Layout & Navigation

---

## 15. What is VStack, HStack, and ZStack?

### Answer:
- VStack → Vertical layout
- HStack → Horizontal layout
- ZStack → Overlapping layout

### Easy Remember:
V = Vertical  
H = Horizontal  
Z = Overlap

---

## 16. What is NavigationStack?

### Answer:
NavigationStack is used  
for navigation between views.

### Example:
```swift
NavigationStack {
    NavigationLink("Next", destination: DetailView())
}
```

### Easy Remember:
NavigationStack = Push navigation.

---

## 17. What is GeometryReader?

### Answer:
GeometryReader provides  
size and position information of a view.

Used for responsive layouts.

### Easy Remember:
GeometryReader = Access layout size.

---

## 18. What is LazyVStack / LazyHStack?

### Answer:
Lazy stacks load views  
only when needed.

Improves performance for large lists.

### Easy Remember:
Lazy = Load when needed.

---

## 19. What is List in SwiftUI?

### Answer:
List displays scrollable data.

Similar to UITableView in UIKit.

### Easy Remember:
List = SwiftUI table view.

---

# Section 4 – Advanced SwiftUI

---

## 20. What is some View?

### Answer:
`some View` is an opaque return type.

It hides the exact type  
but still conforms to View.

### Easy Remember:
some View = Hide real view type.

---

## 21. What is View Modifier?

### Answer:
View Modifier changes appearance  
or behavior of a view.

### Example:
```swift
Text("Hello")
    .font(.title)
    .foregroundColor(.blue)
```

### Easy Remember:
Modifier = Change view style.

---

## 22. What is Combine in SwiftUI?

### Answer:
SwiftUI works closely with Combine  
to handle reactive data updates.

ObservableObject and @Published  
are based on Combine.

### Easy Remember:
Combine = Reactive engine for SwiftUI.

---

## 23. What is @AppStorage?

### Answer:
@AppStorage stores small values  
in UserDefaults.

### Example:
```swift
@AppStorage("username") var username = ""
```

### Easy Remember:
@AppStorage = UserDefaults wrapper.

---

## 24. What are the benefits of SwiftUI?

### Answer:
- Less code
- Declarative syntax
- Automatic UI updates
- Cross-platform support
- Live preview

### Easy Remember:
SwiftUI = Fast + Modern + Declarative.

---

## 25. Difference between UIKit and SwiftUI?

### Answer:

UIKit:
- Imperative
- Uses ViewControllers
- More mature

SwiftUI:
- Declarative
- State-driven
- Modern and simpler

### Easy Remember:
UIKit = Imperative  
SwiftUI = Declarative

---

# Section 5 – Real-World & Tricky Interview Questions

---

## 26. Why does my SwiftUI View reload multiple times?

### Answer:
SwiftUI Views are value types (structs).  
They are recreated whenever state changes.

This is normal behavior.

Problem occurs when:
- Heavy logic is inside `body`
- API calls are triggered inside `body`

### Easy Remember:
View reload is normal. Avoid heavy work inside `body`.

---

## 27. What is the difference between @StateObject and @ObservedObject in real projects?

### Answer:
Use @StateObject when:
- View creates the ViewModel
- View owns the object

Use @ObservedObject when:
- Object is created outside
- View only observes it

Wrong usage may cause object reinitialization.

### Easy Remember:
Create → @StateObject  
Observe → @ObservedObject

---

## 28. Why is my ViewModel getting recreated unexpectedly?

### Answer:
Because you used @ObservedObject instead of @StateObject.

@ObservedObject does not preserve instance across view reloads.

### Easy Remember:
Wrong wrapper = New instance created.

---

## 29. How do you prevent infinite view updates in SwiftUI?

### Answer:
Avoid:
- Updating @State inside `body`
- Mutating state inside computed properties

Use:
- .onAppear
- .task
- ViewModel logic

### Easy Remember:
Never change state inside `body`.

---

## 30. How does SwiftUI decide when to re-render a view?

### Answer:
SwiftUI re-renders a view when:
- @State changes
- @Published changes
- @Binding changes
- Environment value changes

It compares new view with previous one using diffing.

### Easy Remember:
State change = UI refresh.

---

## 31. What is View Identity in SwiftUI?

### Answer:
View identity determines  
whether SwiftUI treats a view as new or existing.

Using `.id()` changes identity.

Incorrect identity may cause animation or state issues.

### Easy Remember:
Identity controls view lifecycle.

---

## 32. Why is ForEach crashing sometimes?

### Answer:
Because items are not uniquely identifiable.

Each item must conform to:
- Identifiable
OR
- Have unique id

### Example:
```swift
ForEach(items, id: \.id) { item in
    Text(item.name)
}
```

### Easy Remember:
ForEach needs unique identity.

---

## 33. What causes performance issues in large SwiftUI lists?

### Answer:
Common reasons:
- Using VStack instead of LazyVStack
- Heavy calculations in body
- No stable IDs
- Large images without resizing

### Easy Remember:
Use Lazy + Optimize body logic.

---

## 34. How do you debug SwiftUI layout issues?

### Answer:
Use:
- .border(Color.red)
- GeometryReader
- Xcode View Debugger
- Print frame sizes

### Easy Remember:
Add border to debug layout.

---

## 35. When should you use UIKit inside SwiftUI?

### Answer:
Use UIKit when:
- SwiftUI lacks specific feature
- Need advanced camera, PDF, WebView customization
- Working with legacy code

Use UIViewRepresentable / UIViewControllerRepresentable.

### Easy Remember:
SwiftUI for modern UI  
UIKit for advanced control.

---

## 36. What is Concurrency in SwiftUI?

### Answer:
Concurrency in SwiftUI refers to performing asynchronous tasks  
without blocking the main UI thread.

SwiftUI uses Swift Concurrency features like:
- async/await
- Task
- @MainActor

It ensures smooth UI updates while background work is running.

### Example:
```swift
.task {
    await fetchData()
}
```

### Easy Remember:
SwiftUI Concurrency = Run background work without freezing UI.

---

## 37. What is Environment Property?

### Answer:
Environment Property allows a SwiftUI view  
to access shared system or app-level values  
without passing them manually through the view hierarchy.

It uses the `@Environment` property wrapper.

### Example:
```swift
@Environment(\.colorScheme) var colorScheme
```

Common environment values:
- colorScheme
- dismiss
- locale
- scenePhase

### Easy Remember:
@Environment = Access shared system values in SwiftUI.

---
