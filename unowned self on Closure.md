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

[unowned self on closure](<script src="https://gist.github.com/shadmazumder/975badc4d6b01b17b69727c81066c0ba.js"></script>)
