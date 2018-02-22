*`In-Out Parameters` is used* on a `functuion` for the following case:
- modifying the value of a parameter.
- persistant change of value for a parameter, after the corresponding function call has ended.

*Can't * 
+ be used on a `constant` or `literal value`. 
+ can't have `default value`. 
+ `variadic parameters` can't be marked as `In-Out Parameters`

*To use* the `In-Out Parameters`, a variable must be prefixed with an ampersand(`&`) at the time of calling the corresponding function.
