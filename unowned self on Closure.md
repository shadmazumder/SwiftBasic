# `[unowned self]` on Closure

The problem starts with strong ref cycle. Consider the following example:

```swift
import UIKit

class Office{
    
    let stuffNumber: Int
    
    lazy var totalLunchPackage: () -> Int = {
        
        return self.stuffNumber
    }
    
    init(totalNumberOfStuff stuffNumber:Int) {
        
        self.stuffNumber = stuffNumber
    }
    
    deinit {
        
        print("Office deinitialized")
    }
}

var officeX: Office?

officeX = Office(totalNumberOfStuff: 10)

if let officeX = officeX {
    
    print(officeX.totalLunchPackage)
}

officeX = nil
```

The `deinit` was not called, `Office deinitialized` didn't print. Lets find out why. 

The `totalLunchPackage` holds a `closure` and on that `closure` we are keeping an instance of `Office`, when we are assiging `totalLunchPackage` as `self.stuffNumber`. Here `self` is the instance of `Office` class.

Point to be noted: Both `class` and `closure` are reference typed. So assigning the `closure` to a property is basically assiging a reference.

As a result we have a strong reference cycle. Two strong references are keeping each other alive. 

```
If you assign a closure to a property of a class instance, and the closure captures that instance by referring to the instance or its members, you will create a strong reference cycle between the closure and the instance.”

Excerpt From: Apple Inc. “The Swift Programming Language (Swift 4.0.3).” iBooks. 
```

### Solution: Capture List

