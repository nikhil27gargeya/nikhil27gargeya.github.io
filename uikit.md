# UIKit

App: basic template for ann app containing a single view and a viewcontroller

DocumentApp: project intended to use the iOS document browser

Game: project configured to take advantage of SpriteKit,SceneKit, OpenGL, Metal

AR App: configured to use ARKit

Main storyboard file is the save file used by the Interface Builder tool holding the user interface design

Property List files: contains key/value pair information
Info.plist contains resource settings including language, executable name, and app identifier, and is the location where several properties are stored to configure the capabilities of the project (ie. user's current geographical location)

Center panel of the window shows a general summary of the settings for the app project

Signing section allows selecting an Apple identity, which ensures that the app is signed with a certificate when it is compiled.

https://medium.com/@bingkuo/a-beginners-guide-to-code-signing-in-ios-development-d3d5285f0960

Playground: interactive environment for Swift code

results panel have the results of each Swift expression 

execute playground button located in the bottom left-hand corner of the main panel, or click the play buttons to run code in stages on the margin of the editor


App Delegate:

Scene Delegate:

UIKit is used to build user interfaces and handle touch events and other things imperatively and giving control. 
UIView: object that manages content for a rectangular area and it is the fundamental superclass for all visual elements
let view = UIView()








Coordinators:
Without coordinators, navigation (controlling the flow of the app) is tightly coupled with UIViewControllers and is hard coded. Coordinators replace navigation flow with separate object.
View Controller A, instead of speaking to View Controller B and building it, speaks to its Coordinator, which pushes or pops the view. This decouples the navigation from the View Controller.
protocol Coordinator {
  var children: [Coordinator] { get set } //child coordinators
  var nav : UINavigationController { get set}
  func start() {}
}
class MainCoordinator : Coordinator { //implements the protocol
  func start() {
    let vc = ViewController()
    vc.coordinator = self
    nav.pushViewController(vc, animated = false)
  }
  func userTapped() {
    coordinator?.buy(widget)
  }
}
