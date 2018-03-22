When a method or a type is generic then that corresponding method and type can be workable for a wide range of data-types(ie Int, String, Double etc).


To make a method or a type(ie `class`, `struct`, `enum`) generict the syntax is `<T>`; where `T` is a placeholder, usually means type. Add `<T>` after type(ie `class`, `struct`, `enum`) name or a method name to make the type or method generic. We can write anything in place of T, but it is a popular convention.


# Generic on method
```swift
func genericPrint<T>(elements:[T]){
    
    for element in elements {
        
        print(element)
    }
}

let names = ["First", "Second", "FullName"]
let ages = [10, 20, 100]

genericPrint(elements: names)
genericPrint(elements: ages)
```

# Generic on type

```swift
//: Playground - noun: a place where people can play

import Foundation

struct Stack<T>{
    
    var elemets: [T] = []
    
    mutating func push(element: T){
        
        elemets.insert(element, at: 0)
    }
    
    mutating func pop() -> T? {
        
        return elemets.isEmpty ? nil : elemets.remove(at: 0)
    }
}

var intStack = Stack<Int>()
var stringStack = Stack<String>()

for i in 1...3 {
    
    intStack.push(element: i)
    stringStack.push(element: String(i))
}

print(intStack)
print(stringStack)

for i in 1...3 {
    
    print(intStack.pop())
}

for i in 1...4 {
    
    print(stringStack.pop())
}
```
Implementation of generic on `class` and `enum` will be similar.

[More about mutating keyword on value type](https://github.com/shadmazumder/SwiftBasic/blob/master/mutating.md)

# Type constraint on generic
We can constraint the generic type by a specific type or protocol.
```swift
//: Playground - noun: a place where people can play

import Foundation

class Bug{}
class BedBug: Bug {}

func onlyBugs<T: Bug>(elements: T){}

onlyBugs(elements: Bug())
onlyBugs(elements: BedBug())
```
