# interview-questions-ios
iOS interview questions with quick revision notes for Swift, UIKit, SwiftUI, Objective-C, and OOPS.

## Objective-C – Interview Questions with Definitions & Examples

Each topic includes a **short definition** and a **small Objective-C example** for quick interview revision.

---

## What is Objective-C?
Objective-C is a **superset of C** and an **object-oriented language** used primarily for iOS and macOS development before Swift.

---

## Why Objective-C?
- Dynamic runtime
- Message passing
- Legacy iOS codebases
- Runtime features not available in Swift

---

## Objective-C vs Swift
- Objective-C → Dynamic, runtime-based
- Swift → Static, compile-time safety

---

## What is @interface?
Declares a class and its properties/methods.

```objc
@interface Car : NSObject
@property(nonatomic, strong) NSString *name;
@end
```

---

## What is @implementation?
Defines the actual implementation of a class.

```objc
@implementation Car
@end
```

---

## What is @property?
Declares getters and setters automatically.

```objc
@property(nonatomic, strong) NSString *title;
```

---

## Property Attributes
- strong
- weak
- assign
- copy
- nonatomic / atomic

---

## strong vs weak
- strong → retains object
- weak → avoids retain cycles

---

## copy vs strong
Use `copy` for `NSString`, `NSArray`, `NSDictionary`.

```objc
@property(nonatomic, copy) NSString *name;
```

---

## What is NSObject?
Root class of most Objective-C classes.

---

## What is nil?
Represents absence of object.  
Calling method on `nil` is safe.

---

## What is Message Passing?
Methods are called by sending messages.

```objc
[obj doSomething];
```

---

## What is SEL?
Selector represents method name.

```objc
SEL selector = @selector(doSomething);
```

---

## What is IMP?
Function pointer to method implementation.

---

## What is id?
Generic object type.

```objc
id obj = @"Hello";
```

---

## What is Category?
Adds methods to existing class.

```objc
@interface NSString (Utils)
- (BOOL)isEmpty;
@end
```

---

## What is Extension?
Adds private methods/properties.

```objc
@interface MyClass ()
@property(nonatomic, strong) NSString *secret;
@end
```

---

## What is Protocol?
Defines method contracts.

```objc
@protocol Payment
- (void)pay;
@end
```

---

## Optional vs Required Protocol Methods

```objc
@optional
- (void)optionalMethod;
```

---

## What is Delegation?
One-to-one communication pattern.

---

## What is KVC?
Key-Value Coding allows accessing properties using strings.

```objc
[obj valueForKey:@"name"];
```

---

## What is KVO?
Observe property changes.

```objc
addObserver:forKeyPath:
```

---

## What is ARC in Objective-C?
Automatic Reference Counting manages memory automatically.

---

## retain / release / autorelease
Manual memory management (pre-ARC).

---

## What is AutoreleasePool?
Releases temporary objects later.

```objc
@autoreleasepool {
    // code
}
```

---

## What is Dealloc?
Called before object deallocation.

```objc
- (void)dealloc {
    NSLog(@"Deallocated");
}
```

---

## What is Bridging Header?
Allows Swift to use Objective-C code.

---

## What is @objc?
Exposes Swift code to Objective-C runtime.

---

## What is Dynamic Dispatch?
Method resolution at runtime.

---

## What is Runtime?
Objective-C runtime allows:
- Method swizzling
- Dynamic method resolution
- Introspection

---

## Interview One-Liners
- Objective-C → Runtime-based language
- id → Generic object
- SEL → Method identifier
- Category → Add methods
- ARC → Automatic memory management
- nil → Safe messaging
