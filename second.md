# SwiftUI vs. UIKit

**SwiftUI** is a UI framework that allows for building user interfaces using a simpler, more intuitive syntax. It is:  
1) Declarative (Declarative means that the programmer defines the desired state of the UI and Swift in this case will take care of the actions of the UI)
2) Compositional (Modular components)
3) State-driven (UI in sync with the state/data)

and designed to integrate across various Apple platforms.

**Good For:** Declarative UI, reusable components  
**Not Good For:** Full control over UI behavior, animations, older iOS versions (apps built in iOS 13 and before were built with UIKit, and apps today may be legacy apps with UIKit code. UIKit and SwiftUI can be used together, and data can be bridged using `UIViewRepresentable`).  

---

**UIKit** is the traditional imperative UI framework providing control over UI behavior/actions and has a vast collection of third-party APIs.

**Good For:** Custom UI elements, complex gestures  
**Not Good For:** Simplistic code with idiomatic capabilities, multi-platform development  

