# `mutating`
On `value types` ie `struct` and `enum`, when `mutating` keyword is used before a method it is symbolically saying that this 
method will modify the structure of `struct` or `enum`.

By default, the properties of `value type` can not be changed from withing its instance. So `mutating` keyword tells the 
compiler that the following method will modify the properties of that `value type`. 

# Points to be noted:
+ all the changes made by the `mutating` method will be written on the `value type` after that particular method ends.
+ the `mutating` method can completely write down a new instance to the implecite `self`.
