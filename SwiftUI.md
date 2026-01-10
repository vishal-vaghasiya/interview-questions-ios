# interview-questions-ios
iOS interview questions with quick revision notes for Swift, UIKit, SwiftUI, Objective-C, and OOPS.

## SwiftUI – Interview Questions with Definitions & Examples

Each topic includes a **short definition** and a **small example** for quick interview revision.

---

## What is SwiftUI?
SwiftUI is Apple’s **declarative UI framework** for building user interfaces across Apple platforms.

---

## UIKit vs SwiftUI
- UIKit → Imperative
- SwiftUI → Declarative

---

## What is Declarative UI?
You describe **what** the UI should look like, not **how** to update it.

---

## What is body?
`body` defines the UI of a SwiftUI view.

```swift
var body: some View {
    Text("Hello SwiftUI")
}
```

---

## What is @State?
Stores local mutable state inside a view.

```swift
@State private var count = 0
```

---

## What is @Binding?
Creates a two-way connection to a parent view’s state.

```swift
@Binding var count: Int
```

---

## Difference between @State and @Binding
- @State → owns the data
- @Binding → borrows the data

---

## What is @ObservedObject?
Observes an `ObservableObject` created outside the view.

```swift
@ObservedObject var viewModel: MyViewModel
```

---

## What is @StateObject?
Creates and owns an `ObservableObject` inside the view.

```swift
@StateObject var viewModel = MyViewModel()
```

---

## What is @EnvironmentObject?
Shares an object across many views without passing it manually.

```swift
@EnvironmentObject var session: UserSession
```

---

## What is ObservableObject?
A protocol that allows views to observe data changes.

```swift
class MyViewModel: ObservableObject {
    @Published var name = ""
}
```

---

## What is @Published?
Automatically notifies views when value changes.

```swift
@Published var isLoading = false
```

---

## What is NavigationStack?
Used for navigation in SwiftUI (iOS 16+).

```swift
NavigationStack {
    NavigationLink("Next", destination: DetailView())
}
```

---

## What is NavigationPath?
Stores navigation state programmatically.

```swift
@State private var path = NavigationPath()
```

---

## What is ViewBuilder?
Allows returning multiple views from a closure.

```swift
@ViewBuilder
func makeView() -> some View {
    Text("A")
    Text("B")
}
```

---

## What is Data Binding?
Automatically keeps UI and data in sync.

---

## What is List?
Displays a scrollable list of data.

```swift
List(items) { item in
    Text(item.name)
}
```

---

## What is ForEach?
Iterates over a collection to create views.

```swift
ForEach(0..<5) { index in
    Text("\(index)")
}
```

---

## What is GeometryReader?
Reads size and position of parent view.

```swift
GeometryReader { geo in
    Text("\(geo.size.width)")
}
```

---

## What is onAppear?
Runs code when view appears.

```swift
.onAppear {
    loadData()
}
```

---

## What is onDisappear?
Runs code when view disappears.

```swift
.onDisappear {
    stopTask()
}
```

---

## What is Task in SwiftUI?
Runs async work tied to view lifecycle.

```swift
.task {
    await loadData()
}
```

---

## What is async/await in SwiftUI?
Used to perform asynchronous tasks cleanly.

---

## What is @MainActor?
Ensures code runs on the main thread.

```swift
@MainActor
func updateUI() {}
```

---

## What is actor?
Provides thread-safe data access.

```swift
actor DataStore {
    var value = 0
}
```

---

## What is Animation in SwiftUI?
Automatically animates state changes.

```swift
.withAnimation {
    count += 1
}
```

---

## What is Transition?
Defines how views appear and disappear.

```swift
.transition(.opacity)
```

---

## What is @AppStorage?
Stores data persistently using UserDefaults.

```swift
@AppStorage("isLogin") var isLogin = false
```

---

## What is @SceneStorage?
Stores data per scene session.

```swift
@SceneStorage("tab") var selectedTab = 0
```

---

## What is PreviewProvider?
Provides live preview in Xcode.

```swift
struct MyView_Previews: PreviewProvider {
    static var previews: some View {
        MyView()
    }
}
```

---

## SwiftUI Benefits
- Less code
- Automatic UI updates
- Live previews
- Built-in state management
- Cross-platform
- Easy animations

---

## Interview One-Liners
- SwiftUI → Declarative UI
- @State → local state
- @Binding → two-way data
- ObservableObject → shared state
- @Published → UI refresh
- Task → async work
- @MainActor → UI safety
