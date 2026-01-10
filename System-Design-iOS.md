# interview-questions-ios
iOS interview questions with quick revision notes for Swift, UIKit, SwiftUI, Objective-C, and OOPS.

## iOS System Design – Interview Notes (Senior Level)

This file covers **system design concepts** commonly asked in **senior / lead iOS interviews**, with an iOS‑specific mindset.

---

## What is System Design?
System design is the process of defining **architecture, components, data flow, and scalability** of an application.

---

## Why System Design Matters in iOS?
- Scalable apps
- High performance
- Better user experience
- Easy maintenance
- Future-proof architecture

---

## High-Level iOS App Architecture

Typical layers:
1. UI Layer (UIKit / SwiftUI)
2. Presentation (ViewModel / Controller)
3. Domain (Business logic)
4. Data (API, Database, Cache)
5. Services (Networking, Analytics)

---

## Data Flow in iOS App
User Action → UI → ViewModel / Controller → UseCase → Repository → API / DB → UI

---

## Designing a Large-Scale iOS App

Key considerations:
- Offline support
- Pagination
- Caching
- Background tasks
- Error handling
- Analytics & logging

---

## Networking Layer Design

### Goals
- Reusable
- Testable
- Decoupled

### Example Structure
```swift
protocol NetworkService {
    func request<T: Decodable>(_ endpoint: Endpoint) async throws -> T
}
```

---

## API Layer Best Practices
- Use REST / GraphQL
- Proper HTTP status handling
- Retry on failure
- Timeout handling
- Pagination support

---

## Caching Strategy
Types of cache:
- Memory (NSCache)
- Disk (FileManager)
- Database (Core Data / SQLite)

When to use:
- Reduce API calls
- Improve app speed
- Offline access

---

## Offline-First App Design
Key ideas:
- Local DB as source of truth
- Sync with server when online
- Handle conflicts

---

## Database Design (iOS)
Options:
- Core Data
- SQLite
- Realm

Best practices:
- Background context
- Batch updates
- Avoid main-thread blocking

---

## Background Tasks
Use cases:
- File upload/download
- Sync
- Location updates

Tools:
- BGTaskScheduler
- URLSession background tasks

---

## Pagination Design
Techniques:
- Offset-based pagination
- Cursor-based pagination

Avoid:
- Loading all data at once

---

## Image Loading System Design
Key components:
- Downloader
- Cache (memory + disk)
- Prefetching
- Cancellation

---

## Performance Optimization
- Lazy loading
- Image compression
- Avoid heavy work on main thread
- Efficient diffing (SwiftUI)

---

## Memory Management in Large Apps
- Avoid retain cycles
- Use weak references
- Monitor memory warnings
- Release caches

---

## Modularization
Split app into modules:
- Core
- UI
- Networking
- Features

Benefits:
- Faster builds
- Team scalability
- Reusability

---

## Dependency Injection in System Design
- Constructor injection
- Protocol-oriented design

Benefits:
- Testability
- Loose coupling

---

## Feature Flag System
Allows enabling/disabling features remotely.

Use cases:
- A/B testing
- Gradual rollout

---

## Analytics & Logging
Track:
- User actions
- Crashes
- Performance

Tools:
- Firebase
- Custom logging systems

---

## Security Considerations
- Secure API calls
- Keychain for sensitive data
- Certificate pinning
- Data encryption

---

## Handling App Updates
- DB migration
- Feature compatibility
- Backward support

---

## Designing for Scalability
- Clean Architecture
- MVVM
- Modular codebase
- Async/await

---

## Common iOS System Design Interview Questions
- Design Instagram feed
- Design offline notes app
- Design chat application
- Design image-heavy app
- Design video streaming app

---

## How to Answer System Design Questions
1. Clarify requirements
2. Define architecture
3. Explain data flow
4. Discuss edge cases
5. Talk about scalability & performance

---

## Interview One-Liners
- System design → scalable thinking
- Offline-first → local DB first
- Cache → performance booster
- Modularization → faster teams
- Dependency Injection → testability
