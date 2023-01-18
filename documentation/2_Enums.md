Enums allow the creation of custom constants. These constants only equal them-selves. The type of the constant is the enums name & the constants can be accessed using `.`(Type access) operator on the name of the enum.
```
enum direction {
    up   ,
    left ,
    right,
    down
}

let x: direction = direction.up
```

You can also assign constants to enum constants, but they must be of the same type. In this example an `int`. In this case, the constants won't be their own type, rather the type that they are assigned to, which can be infered.
```
enum direction: int {
    up    = -1,
    left  = -1,
    right = 1 ,
    down  = 1
}

let x: int = direction.up
```
