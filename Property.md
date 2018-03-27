Property associate values with specific Class, Structure, or Enumeration.

Property can be categorised as 
+ `instance property`, property of an instance of a type.
+ `type property`, property of a type itself. One copy for all the instances of that type. Need to have a default value for stored property as, type itself does not have a initializer.

Both `instance property` and `type property` have two types:
- `Stored property`, Only provided by `class` and `struct`. Can be variable(`var`) or constant(`let`) store property.
- `Computed property`, Provided by all `class`, `struct` and `enum`. Usually doesn't store value rather provide a `getter` and an optional `setter`, to set the other property or variable indirectly. Variable(`var`) computed property only. If a computed property does not provide a setter then it is called **Read only computed property**.

```swift
//: Playground - noun: a place where people can play

// instance property

import Foundation

struct SimpleStruct{
    
    var storedProperty = 2
    
    var computedProperty: Int{
        get{
            return storedProperty*2
        }
        
        set(newComputedProperty){
            storedProperty = newComputedProperty
        }
    }
}

var aStruct = SimpleStruct()

aStruct.storedProperty //prints out: 2
aStruct.computedProperty //prints out: 4

aStruct.computedProperty = 3

aStruct.storedProperty //prints out: 3
aStruct.computedProperty //prints out: 6
```

```swift
//: Playground - noun: a place where people can play

// type property

import Foundation

struct SimpleStruct{
    
    static var storedProperty = 2
    
    static var computedProperty: Int{
        get{
            return storedProperty*2
        }
        
        set(newComputedProperty){
            storedProperty = newComputedProperty
        }
    }
}

SimpleStruct.storedProperty //prints out: 2
SimpleStruct.computedProperty //prints out: 4

SimpleStruct.computedProperty = 3

SimpleStruct.storedProperty //prints out: 3
SimpleStruct.computedProperty //prints out: 6
```
By using the `class` keyword before computed property on a parent class type, the child class can override that computed type property.
```swift
//: Playground - noun: a place where people can play

import Foundation

class ParentClass{
    
    static var storeProperty = 2
    
    class var computedProperty: Int{
    
        return storeProperty*2
    }
}

class ChildClass: ParentClass{
    
    override class var computedProperty: Int{
        
        return storeProperty*3
    }
}

ParentClass.computedProperty //prints out: 4
ChildClass.computedProperty //prints out: 6
```

### Difference between `static` `class` and `final` property
Value type(`struct` and `enum`) can only use `static`. Reference type, aka `class`, can use `static`, `class` and `final` property. The following difference is for `class` type only:
+ `static` property can not be override by subclass type. However `class` property can be overridden by the subclass type.
+ `final` will be used only for the instance of a `class` type. `final` property can not be overridden by the instance of a subclass type.

### Property Observer, `willSet` `didSet`
Responses to the changes of value for a property, even for the same value. Not applicable for `Lazy Stored Property`. 

```swift
//: Playground - noun: a place where people can play

import Foundation

struct SimpleStruct{
    
    var storeProperty: Int {
        
        didSet{
            print("didSet \(oldValue)") //prints out: 2
        }
        
        willSet{
            print("willSet \(newValue)") //prints out: 4
        }
    }
}

var smplStruct = SimpleStruct(storeProperty: 2)
smplStruct.storeProperty = 4
```

### Lazy Stored Property
For Lazy stored property the initial value is not calculated untill the first use. `lazy` modifier is added as a prefix before a `var`.

Reason to use:
+ As the var's initialization is dependent on some other factor/s, that are not know at init time.
+ Expensive setup for the var, should not be preformed unless required.

Note:
“If a property marked with the lazy modifier is accessed by multiple threads simultaneously and the property has not yet been initialized, there is no guarantee that the property will be initialized only once.”

Excerpt From: Apple Inc. “The Swift Programming Language (Swift 4.0.3).” iBooks. 
