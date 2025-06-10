# Objective C:

Root class provides base functionality
a vast majority of classes inherit from NSObject

When UIButton doesn't offer the customization required, it makes sense to create a new class inheriting from UIButton to take the base functionality and then expand on it

UIButton itself inherits from UIControl, which inherits from UIView, which inherits from UIResponder

An object should be designed to hide details of its internal implementation (abstraction)
All you need to know about a UIButton is that you can change certain attributes like the title and color

When defining your own class, you determine what atttributes will be publicly accessible, and how other objects communicate with the instances of the class.

In Objective-C, the interface and implementation are decoupled, and the interface is public

Objective-C objects use an asterisk to indicate they are C pointers and a ; at the end

- (void)someMethodWithParam:(Param)value;

Syntax for a class:
#import "Car.h"

@implementation Car
@interface Car : NSObject
- (void)drive {
  NSLog(@"engine starting');
}
@end

In Objective-C, classes are also object, with opaque type called Class

Factory Method: used as an alternative to object allocation, objective c's constructor methods
