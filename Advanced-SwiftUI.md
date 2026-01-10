# interview-questions-ios
iOS interview questions with quick revision notes for Swift, UIKit, SwiftUI, Objective-C, and OOPS.

## Advanced SwiftUI – Interview Questions (Senior Level)

This file contains **advanced SwiftUI topics** asked in **senior / lead iOS interviews**.  
Basic SwiftUI concepts remain in **SwiftUI.md**.

---

## SwiftUI Rendering System
SwiftUI uses a **diffing engine** to compare view states and update only the changed UI parts.

Key point:
- Views are value types
- `body` is recomputed frequently

---

## View Identity
SwiftUI identifies views using:
- View type
- Position in hierarchy
- Explicit `.id()`

```swift
Text(item.name)
    .id(item.id)
```

Wrong identity causes:
- Unexpected animations
- State reset

---

## View Lifecycle in SwiftUI
SwiftUI views are **recreated often**.

Use:
- `onAppear`
- `onDisappear`
- `.task {}`

Avoid heavy logic in `init`.

---

## State Update Cycle
1. State changes  
2. View invalidated  
3. `body` recomputed  
4. UI updates  

---

## @State vs @StateObject vs @ObservedObject
- `@State` → local simple values
- `@StateObject` → owns reference type (created once)
- `@ObservedObject` → observes external object

Interview tip:
> Wrong choice causes view model re-creation.

---

## @Environment vs @EnvironmentObject
- `@Environment` → system values (colorScheme, locale)
- `@EnvironmentObject` → shared app-level objects

```swift
@Environment(\.colorScheme) var scheme
```

---

## PreferenceKey
Used to pass values **from child → parent**.

```swift
struct HeightKey: PreferenceKey {
    static var defaultValue: CGFloat = 0
    static func reduce(value: inout CGFloat, nextValue: () -> CGFloat) {
        value = nextValue()
    }
}
```

Use cases:
- Custom layouts
- Scroll offset tracking

---

## MatchedGeometryEffect
Creates smooth animations between two views.

```swift
.matchedGeometryEffect(id: "image", in: namespace)
```

Used for:
- Hero animations
- Shared element transitions

---

## Custom ViewModifier
Encapsulates reusable UI logic.

```swift
struct CardModifier: ViewModifier {
    func body(content: Content) -> some View {
        content
            .padding()
            .background(.white)
            .cornerRadius(10)
    }
}
```

---

## Custom Property Wrapper
Encapsulates reusable state logic.

```swift
@propertyWrapper
struct Clamped {
    private var value: Int
    var wrappedValue: Int {
        get { value }
        set { value = min(max(0, newValue), 100) }
    }
}
```

---

## AnyView
Type-erased view.

⚠️ Avoid when possible:
- Performance cost
- Loses type information

---

## ViewBuilder Performance
Large conditional `ViewBuilder` blocks can hurt performance.

Best practice:
- Extract subviews
- Reduce branching inside `body`

---

## Lazy Containers
Efficient rendering for large data sets.

- `LazyVStack`
- `LazyHStack`
- `LazyVGrid`

---

## GeometryReader Pitfalls
- Takes maximum available space
- Can break layouts

Use only when needed.

---

## EquatableView
Prevents unnecessary re-rendering.

```swift
EquatableView(content: MyView())
```

---

## @ViewThatFits
Chooses first view that fits available space.

```swift
ViewThatFits {
    Text("Large Layout")
    Text("Compact Layout")
}
```

---

## TimelineView
Used for time-based updates (clock, live widgets).

---

## Canvas
Low-level drawing API for custom rendering.

---

## SwiftUI + Combine
SwiftUI reacts automatically to Combine publishers.

Use cases:
- Network streams
- Live data updates

---

## AsyncImage
Loads images asynchronously.

```swift
AsyncImage(url: url)
```

---

## Accessibility in SwiftUI
Make UI accessible using modifiers.

```swift
.accessibilityLabel("Profile Image")
```

---

## Testing SwiftUI
- Unit test ViewModels
- Snapshot testing
- ViewInspector (third-party)

---

## Common Performance Issues
- Heavy computation inside `body`
- Large view hierarchies
- Wrong state ownership
- Excessive AnyView usage

---

## Common Interview Questions
- How does SwiftUI decide when to re-render?
- Difference between `@StateObject` and `@ObservedObject`?
- When should PreferenceKey be used?
- How do you optimize SwiftUI performance?
- Why is `AnyView` discouraged?

---

## Interview One-Liners
- SwiftUI views → value types
- `body` → recomputed frequently
- State drives UI
- Extract views for performance
- PreferenceKey → child-to-parent data flow
