# MVC vs MVVM


Model View Controller:
Model: Data Layer, does talk to other components
View: Displays and performs logic over UI. Receives data from controller.
Controller: Intermediary between the data and UI, receives data and passes it onto the UI

Issue: View Controller can get large in large functionality apps since it handles the UI and the logic. Additionally, controller is tightly coupled with the model and view whereas viewmodel cannot directly update the view but use data binding to reactively update the UI

User taps button -> controller handles input -> model updated -> controller manually updates view

Model View ViewModel:
Model: Data Layer
View: UI 
ViewModel (Model-ish): Abstraction of the view (stores simplified version of the model specifically for that view) that exposes certain properties which are data binded with the view. The view updates upon state changes. The key responsibility of the viewmodel is to encapsulate the interaction logic for a view, but not all logic should go in the ViewModel, some should go in the model or other files. The ViewModel unlike a controller does not know the concrete UI but is rather an abstraction of the view. 

User taps button -> viewmodel handles input, updates model, view model auto updates view

https://learn.microsoft.com/en-us/archive/blogs/johngossman/advantages-and-disadvantages-of-m-v-vm

Pros: Obvious purpose is to decouples the logic from the view and the ViewModel is easier to unit test. Can allow for reactive UI updates.
Cons: Overkill for simple UI, data binding is declarative and is harder to debug.

What is state:
data at a given moment 
