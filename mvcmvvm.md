# MVC vs MVVM


Model View Controller:
Model: Data Layer, does talk to other components
View: Renders UI. Receives data from controller.
Controller: Intermediary between the data and UI, receives data and passes it onto the UI

Issue: View Controller can get large in large functionality apps. Additionally, controller is tightly coupled with the model and view whereas viewmodel cannot directly update the view but use data binding to reactively update the UI

Model View ViewModel:
Model: Data Layer
View: UI 
ViewModel (Model-ish): Abstraction of the view that exposes certain properties which are data binded with the model

https://learn.microsoft.com/en-us/archive/blogs/johngossman/advantages-and-disadvantages-of-m-v-vm

Pros: Obvious purpose is to decouples the logic from the view and the ViewModel is easier to unit test. Can allow for reactive UI updates.
Cons: Overkill for simple UI, data binding is declarative and is harder to debug.
