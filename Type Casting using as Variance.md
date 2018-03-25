Type casting is to convert one type of object to another. Has two kinds; UpCast and DownCast. UpCast is to convert child into 
parent. On the other hand DownCast is to convert parent into child.

[Sample hierarchy](http://what-when-how.com/wp-content/uploads/2011/08/tmp125_thumb.jpg)

# `as`
`as` is used only on UpCast.
```swift
//: Playground - noun: a place where people can play

import UIKit

//: Up Cast
let label = UILabel(frame: CGRect(x: 0, y: 0, width: 100, height: 100))
let labelView = label as UIView
```

# `as?`
`as?` is used on DownCast by an inplecite way or a safe way. On successfull conversion it will return the child object; on
fail case will return `nil`. Basically a optional type cast.
```swift
//: Playground - noun: a place where people can play

import UIKit

//: Up Cast
let label = UILabel(frame: CGRect(x: 0, y: 0, width: 100, height: 100))
let labelView = label as UIView


//: Down cast
let childLabel = labelView as? UILabel // success
childLabel?.text // prints "Hello"

let childButton = labelView as? UIButton // fails
childButton?.tintColor // prints nil
```

# `as!`
`as!` is used for forced downcast. Will potentially crash the app when froce dowcast will return nil.
```swift
//: Playground - noun: a place where people can play

import UIKit

//: Up Cast
let label = UILabel(frame: CGRect(x: 0, y: 0, width: 100, height: 100))
label.text = "Hello"
let labelView = label as UIView


//: Down cast
let childLabel = labelView as! UILabel
childLabel.text

let childButton = labelView as! UIButton
childButton.tintColor //error: Execution was interrupted, reason: signal SIGABRT.
```

**`is`**
`is` is the *type check operator*.
```swift
//: Playground - noun: a place where people can play

import UIKit

let label = UILabel(frame: CGRect(x: 0, y: 0, width: 100, height: 100))
let valid = label is UIView // true
```
