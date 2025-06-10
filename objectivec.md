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

- sign means instance method

+ sign means class methods

+ (id)string;

Working with Objects:
work in an objective-c are messaging being sent between objects

[someObject doSomething]; //uses the square brackets

someObject in this case is the receiver of the object, it will be sent the doSomething message

local variables like this are limited in scope to the method in which they are defined. Once the closing bracket is reached, the integer will no longer be accessible
- (void)myMethod {
  int someInteger = 42;
}

Obj-C objects are allocated differently, they have longer life cycles than the scope of a method call. They normally need to stay alive long than the original variable created to keep track of it.

NSString *myString = // a string from somewhere
Although the scope is limited to the scope of the method this is in, the actual string object may have a longer life

%@ is a format specifier used for printing and formatting objective-c objects

passing objects as a method paramater:
- (void)saySomething:(NSString *)greeting;
greeting pointer points to a string object that exists longer than its local variable that keeps track of it

self is a pointer meaning "object that's received this message" , the receiver

super calls a method implementation defined by a superclass further up the inheritance chain

Objects are created dynamically using alloc (class method from the NSObject root class)
id: keyword to signify "some kind of object", special that it doesn't use an asterisk

in nested calls, the innermost call is carried out first


Object Allocation example
NSNumber *magicNumber = [[NSNumber alloc] initWithInt:42];
Factory method:
NSNumber *magicNumber = [NSNumber numberWithInt:42];

Use new to create an objects if no arguments are needed for initialization

Using literals for concise object creation
NSString *string = @"Hello";

Objective-C is a dynamically typed language, meaning that you can assign any type of value to variable, and you can get around compile time errors, while at runtime there can be errors

Always good to initialize scalar variables otherwise their initial values will have garbage from the previous stack contents

compiler automatically sets uninitialized objects to nil

if variable is nil, its logical value is 0 (false), if it has an address, it's not 0

Encapsulation: an object encapsulates data through its properties
@property (readonly) NSString *fullName; //this cannot be set

NSString *firstName = somePerson.firstName;
somePerson.firstName = @"Johnny";
dot syntax is a convenient wrapper around accessor method calls

An init method should assign self to the result of calling superclass's intialization method

custom accessor methods:
in the case that a property is not backed by an instance variable
instead of having to update a property everytime it is changed, its easier to write a custom accessor method to build string on request:
- (NSString *)fullName {
  return [NSString stringWithFromat:@"%@ %A", self.firstName, self.lastName]
}

if the custom accessor method does use an instance variable, it must access the variable directly within the method

Properties are atomic, meaning that the synthesized accesors ensure that a value is fully retrieved/set even if they are called simultaneously from different threads

A strong reference is when one objects relies on another, effectively taking ownership of it. In Obj-c, an object is kept alive as long as it has at least one strong reference to it from another object.

A strong reference cycle results in a memory leak. To remedy this, one of the strong references should be substituted for a weak reference. A weak reference does not imply ownership and doesnot keep an object alive.

__weak variable doesn't not keep an object alive and it is set to nil when the object is deallocated to prevent a dangling pointer (when a pointer points to an object that has already been freed/deallocated)

caching a weak property in a strong variable ensures that it exists in memory while the strong variable (object) is still in scope




