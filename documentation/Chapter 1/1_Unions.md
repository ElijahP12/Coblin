Unions are different in other languages. A `union` specifies a type, that allows the usage of multiple type(Like python typing module unions). Unions are generic types.

A variable that can either be a `string` or `int`, can be the type of `union<string, int>`.
```
var x: union<string, int> = "Hello, world!"

x = 1
```

`union`s can be combined with other generic types.
```
let x: array<union<string, int>> = ["A", 2, "C"]
```
