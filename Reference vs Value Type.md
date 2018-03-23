When an instance is assigned, two type of scenarion can occur based on the type(Reference or Value) of that instance. The new instance can have the reference of the old instance or the new instance can have a brand new instance.

+ **Reference Type**:
On reference type the already initiated instance's memory address is shared. So mutating the new instance will also mutate the old instance. Also there is no new copy or instance of that object is created.

+ **Value Type**:
On value type a new instance will be created. The old and the new instance will have two different references. So changing any one will not have any effect on other. Every assigning will create new instance, thus holding more space on memory.

On Swift `class`, `closure`(`function` are also a type of `closure`) are reference type. On the other hand `enum` and `struct` are value type.

# What happens on Initializing, Assigning, Copying and Mutating
+ For **Initializing** always new instance is created. So both type have the same behaviour. 
+ **Assign** is basically a **Copy**. On ref type instance, `class`, will share the reference of the instance. On the other hand value type instance, `struct` `enum`, will create new instance but will have the same property of the old instance.
+ For **Mutating** the ref type instance will mutate the old instance, when the new instance is updated as the new one is referencing the old instance. But for value type only the new instance will be updated, not the old one.

```swift
//: Playground - noun: a place where people can play

import Foundation

class DemoClass{
    
    var name: String
    
    init(name: String) {
        
        self.name = name
    }
}

struct DemoStruct{
    
    var name: String
}

let fClass = DemoClass(name: "First")
let sClass = fClass
sClass.name = "Second"
print(fClass.name) // Prints: Second

let fStruct = DemoStruct(name: "First Struct")
var sStruct = fStruct
print(fStruct.name) // Prints: First Struct

sStruct.name = "Second Struct"
print(fStruct.name) // Prints: First Struct
//fStruct.name = "New Name" //Cannot assign to property: 'fStruct' is a 'let' constant
```
# When to use which one
As a general guideline, consider creating a structure when one or more of these conditions apply:

+ The structure’s primary purpose is to encapsulate a few relatively simple data values.
+ It is reasonable to expect that the encapsulated values will be copied rather than referenced when you assign or pass around an instance of that structure.
+ Any properties stored by the structure are themselves value types, which would also be expected to be copied rather than referenced.
+ The structure does not need to inherit properties or behavior from another existing type.

In all other cases, define a class, and create instances of that class to be managed and passed by reference. In practice, this means that most custom data constructs should be classes, not structures.

Excerpt From: Apple Inc. [The Swift Programming Language (Swift 4.0.3).](https://itunes.apple.com/in/book/the-swift-programming-language-swift-4-0-3/id881256329?mt=11)
