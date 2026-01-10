

# iOS Interview Cheat Sheet (One Page)

Last‑minute quick revision for **iOS interviews**.  
Covers **Swift, UIKit, SwiftUI, Objective‑C, Concurrency, Memory, Architecture, and System Design**.

---

## Swift – Core
- **struct** → Value type (Copy‑on‑Write)
- **class** → Reference type
- **enum** → Type‑safe states
- **Optional** → Value or `nil`
- **guard let** → Early exit
- **defer** → Executes before function exits
- **Protocol** → Contract
- **Extension** → Add behavior

---

## ARC & Memory
- **Strong** → Keeps object alive
- **Weak** → Auto `nil`, avoids retain cycle
- **Unowned** → No retain, crash if nil
- **Retain Cycle** → Strong ↔ Strong
- **Fix** → `[weak self]`
- **Heap** → Classes
- **Stack** → Structs, locals
- **Tools** → Memory Graph, Instruments

---

## UIKit
- **Architecture** → MVC (default)
- **Delegation** → One‑to‑one
- **KVO** → Observe property
- **NotificationCenter** → Broadcast
- **GCD** → Thread handling
- **UI updates** → Main thread only

### ViewController Lifecycle
```
viewDidLoad
viewWillAppear
viewDidAppear
viewWillDisappear
viewDidDisappear
```

---

## SwiftUI – Basics
- **Declarative UI**
- **@State** → Local value
- **@Binding** → Two‑way data
- **@StateObject** → Own ViewModel
- **@ObservedObject** → External ViewModel
- **@EnvironmentObject** → App‑wide state
- **Navigation** → NavigationStack
- **Task** → Async work

---

## SwiftUI – Advanced
- Views are **value types**
- `body` is **recomputed often**
- **View identity** → type + position + `.id()`
- **PreferenceKey** → Child → Parent data
- **MatchedGeometryEffect** → Hero animations
- **Avoid AnyView** → Performance hit
- **LazyVStack / LazyGrid** → Large lists
- **@MainActor** → UI safety

---

## Concurrency
- **Sync** → Blocks thread
- **Async** → Non‑blocking
- **GCD** → DispatchQueue
- **async/await** → Modern concurrency
- **Task** → Async unit
- **Actor** → Thread‑safe state
- **Race condition** → Shared data
- **Deadlock** → Threads waiting forever

---

## Objective‑C
- Runtime‑based language
- **@interface / @implementation**
- **id** → Generic object
- **SEL** → Method identifier
- **Category** → Add methods
- **Extension** → Private members
- **KVC / KVO**
- Messaging `nil` is safe
- Bridging Header → Swift ↔ Obj‑C

---

## Architecture
- **MVC** → Simple, Massive VC issue
- **MVVM** → UI & logic separation
- **Clean Architecture**
  - Presentation
  - Domain
  - Data
- **Repository + UseCase**
- **SOLID** principles

---

## System Design (iOS)
- Offline‑first design
- Cache → Memory + Disk
- Pagination → Cursor preferred
- Image loading → Cache + cancel
- Background tasks → BGTaskScheduler
- Modularization → Faster builds
- Dependency Injection → Testability
- Security → Keychain, pinning

---

## In‑App Purchases
1. Consumable  
2. Non‑Consumable  
3. Auto‑Renewable Subscription  
4. Non‑Renewing Subscription  

---

## TestFlight
- Up to **10,000 external testers**

---

## Interview One‑Liners
- SwiftUI → State drives UI
- ARC → Automatic memory
- Actor → Race‑safe
- MVVM → Testable UI
- Cache → Performance boost
- Offline‑first → Better UX

---

## Final Tips
- Explain **trade‑offs**
- Mention **performance & memory**
- Draw **architecture flow**
- Use **real project examples**

⭐ Best used for **last 10‑minute revision before interview**.
