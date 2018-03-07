Property associate values with specific Class, Structure, or Enumeration.

Property can be categorised as 
+ `instance property` as follows
    - Stored property
    - Computed property
+ `type property`

## Stored Property:
Only provided by `class` and `struct`. Can be variable(`var`) or constant(`let`) store property.
```swift
struct SimpleStruct{
    let constStoredProperty: Int
    var variableStoredProperty: Int
}
```

## Computed Property:
Provided by all `class`, `struct` and `enum`. Usually doesn't store value rather provide a `getter` and an optional `setter`,
to set the other property or variable indirectly.
Variable(`var`) computed property only.
```swift
struct SimpleStruct{
    var computedProperty: Int{
        get{
            return someProperty*2
        }
        
        set(newComputedProperty){
            someProperty = newComputedProperty
        }
    }
}
```
