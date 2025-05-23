# Swift

Swift was introduced in 2014 as a modern language for writing apps. It replaces Objective-C as the primary programming language for iOS and macOS. Swift is designed to be safe (prevents human errors), fast, and expressive.
Swift types are not automatically cast to other types unless it is manually instructed. Type inference means that the compiler can deduce the type of an expression.

let keyword is used for constants
var keyword is used for variables

comments can be used through // or /* */

Built in types:
Int: represents whole numbers
Double: representing a decimal number
Bool: true or false
String: text

Type annotation
let cityName : String = "San Francisco" //Swift would infer this type but we use annotation to be explicit 
let amountOwed : Decimal = 0 //case where it is useful
3 cases to use Type annotation:
1. Create a constant or variable without assigning a value
2. When you create a constant that can be inferred as two or more different types (ie. "J" is character or string?)
3. When you create attributes to a type definition (ie. struct/class where you don't want a default value in many cases)



   

Localization:
Adapting app to support different languages
Techniques: 
1. including strings files so that Text() (because the first argument to Text is the LocalizedStringKey type) and interpolated strings (embedded strings in expressions) are automatically formatted. issue is manually have to keep strings in sync with code. 
2. Setting .locale in NumberFormatter/DateFormatter/CurrencyFormatter
3. String Catalogs (automatic extraction by xcode)


Foundation:
Base functionality for Swift files that includes Number Formatter and Date Formatter (works with numbers and dates respectively and the textual representation) and Sorting/Filtering functionality 

```
private static func formatCurrency(amount: Decimal, currencyCode: String) -> String {
     let formatter = NumberFormatter()
     formatter.numberStyle = .currency
     formatter.currencyCode = currencyCode
     formatter.locale = Locale.current
     formatter.minimumFractionDigits = 2
    formatter.maximumFractionDigits = 2
     return formatter.string(from: NSDecimalNumber(decimal: amount)) ?? "\(amount)"
}
```

Value Type vs Reference Type:

Copy on Write (deferring copy for performance reasons, useful when we need a value type just for reading):
When we pass a value type instance to an object, a new copy will not be created until modification is needed, if a change is required only then will a need to copy. Arrays and dictionaries in Swift has copy on write functionality included already. With structs though, 

Structs vs Classes
Structs:
Value types like Strings and Ints and Doubles and Bools and structs and enums, create independent copies when assigned (pass by value). Use structs when you don't control identity (ie. instance's identity is owned by a remote server, objects you want to be independent).

Classes:
Reference types, like classes, share the same instance and when assigned and are passed by reference. Use classes when you do control identity (ie. network connections, bluetooth central manager which needs to be shared across the app, shopping cart object, authentication session). Two different class instances sharing the same values will not be the same using the (===) operator.
```
import UIKit

var value: Int? = nil

struct Person {
    let name: String
    let attributes: Attributes
}
 
 
class Attributes {
    var age: Int
    var height: Int
    var weight: Int
    
    init(age: Int, height: Int, weight: Int) {
        self.age = age
        self.height = height
        self.weight = weight
    }
}
 
 //p1 is a person value type with inner reference type
let p1 = Person(name: "Person 1", attributes: Attributes(age: 24, height: 180, weight: 80))
print(p1.attributes.age) //print 24
let p2 = p1 //p2 is an independent copy of p1, but the reference type (attributes) is shared among the two objects
p2.attributes.age = 30 //reassigns the age of the object to 30
print(p1.attributes.age) //print 30
```

Closures:
functions that can be passed around in your code
