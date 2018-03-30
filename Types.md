Swift has two type:

+ # Named Types: 
Type with name when defined. Name types are `class`, `struct` and `enum`. As Data types, basic or primitive type on other language, are `struct` based on swift so they are also named type.
```swift
let sampleClass: Class
let someInt = 10
```

+ # Compound Types:
Types without a name. Compound types are `fun` and `tuple`. Can contain Name types and/or compound types.
```swift
let sampleTupple: (Int, (String, Bool)) // The (Int, (String, Bool)) itself is a compound type
func someFunc(param: Int, anotherParam: Int)-Bool {}
```

