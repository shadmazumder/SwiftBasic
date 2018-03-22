
We will discuss `try` `try?` and `try!` using Error handling. Here we will `throws` `PrintError` for invalid input.


# `try`
`try` need to be used inside a `do catch` statement.
```swift
//: Playground - noun: a place where people can play

import Foundation

enum PrintError: Error{
    
    case InvalidName
    case EmptyName
}

func printMyName(name: String?){
    
    do {
        
        try validate(name: name)
        print("Finally my name is: \(name!)")
    } catch PrintError.InvalidName {
        
        print("Got an Invalid Name")
    } catch PrintError.EmptyName {
        
        print("Got an Empty Name")
    }catch {}
}

func validate(name: String?) throws{
    
    guard let name = name else {
        
        throw PrintError.InvalidName
    }
    
    if name.isEmpty {
        
        throw PrintError.EmptyName
    }
}

printMyName(name: "") //Prints: Got an Empty Name 
printMyName(name: nil) //Prints: Got an Invalid Name
printMyName(name: "Some Name") //Prints: Finally my name is: Some Name
```

# `try?`
`try?` is like optional unwrapping. If the called method after the `try?` throws an error then it will just ignore the error and will continue for the next statement.

```swift
//: Playground - noun: a place where people can play

import Foundation

enum PrintError: Error{
    
    case InvalidName
    case EmptyName
}

func printMyName(name: String?){
    
    try? validate(name: name)
    
    print("Finally my name is: \(name)")
}

func validate(name: String?) throws{
    
    guard let name = name else {
        
        throw PrintError.InvalidName
    }
    
    if name.isEmpty {
        
        throw PrintError.EmptyName
    }
}

printMyName(name: "")
printMyName(name: nil)
printMyName(name: "Some Name")
```

# `try!`
`try!` will forefully unwrape the throwable method. Can potentially crash the app. If the throwable method throws an error then using the try! will crash the app.

```swift
//: Playground - noun: a place where people can play

import Foundation

enum PrintError: Error{
    
    case InvalidName
    case EmptyName
}

func printMyName(name: String?){
    
    try! validate(name: name)
    
    print("Finally my name is: \(name)")
}

func validate(name: String?) throws{
    
    guard let name = name else {
        
        throw PrintError.InvalidName
    }
    
    if name.isEmpty {
        
        throw PrintError.EmptyName
    }
}

printMyName(name: "Some Name")
printMyName(name: "") // will crash the app. error: Execution was interrupted, reason: EXC_BAD_INSTRUCTION 
printMyName(name: nil) // will also crash the app. error: Execution was interrupted, reason: EXC_BAD_INSTRUCTION 
```
