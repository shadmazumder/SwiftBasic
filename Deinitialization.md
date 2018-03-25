Deinitialization is called just before releasing a class instance. `deinit` is the signature.

If some resource is been used by the class then it is the duty of that class to free those resources. Like opening a file to read or write on a file, the class need to close the file on `deinit`.

```swift
//: Playground - noun: a place where people can play

import Foundation

class SimpleClass{
    
    init?() {
        print("init called")
    }
    
    deinit {
        print("deinit called")
    }
}

var demo = SimpleClass()
demo = nil // prints: deinit called
```
