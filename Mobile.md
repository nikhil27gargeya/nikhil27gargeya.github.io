# Mobile

Topics: mobile application architecture, native development, cross-platform development, iOS development, Android development, Swift, Kotlin, SwiftUI, UIKit, Jetpack Compose, application lifecycle, view lifecycle, navigation, state management, MVVM, MVC, Coordinator pattern, dependency injection, networking, REST API integration, JSON encoding, JSON decoding, multithreading, asynchronous programming, Swift concurrency, Kotlin coroutines, reactive programming, Combine, memory management, caching, local data persistence, Core Data, Room, offline-first applications, performance optimization, push notifications, deep linking, authentication, mobile application security, localization, accessibility, unit testing, UI testing, App Store deployment, Play Store deployment


Bundle ID: unique identifier for app 
App ID: team ID + Bundle ID suffix 
Certificate: proves the developer/team identity 
Provisioning Profile: an Apple permission file that connects the App ID, certificate, developer team, allowed devices, and app capabilities so a signed app can run on real devices or be distributed 

MVVM-C:
View contains only the code to build the view. The ViewModel contains only business logic (it should be View and Navigator agnostic). Coordinator should only contain the code for creating the relevant view and navigation flow. ViewModel shouldn't contain any Coordinator. And ViewModel to coordinator communication should happen only via closure or delegate pattern. Also avoid passing concrete objects, use dependency inversion.

