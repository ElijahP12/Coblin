Generics can only be used on functions, enums & structures. These allow the usage of any type, while being statically typed. `<>` are used after the identifier & the identifiers defined on it(Can be multiple), will be used as types that will be used later determined by the user.
```
struct wrapper<T> {
    value: T

    init(value: T) {
        this.value = value
    }
}

let x: wrapper<int> = wrapper<int>(1)
```

The type can be infered, either the variable type, getting infered by the value or the value type, getting infered by the variable.
```
let x = wrapper<int>(1)

let y: wrapper<int> = wrapper(0)
```
