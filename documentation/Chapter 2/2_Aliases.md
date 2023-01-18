Generics types can get quite long. The language allows the use of `alias` key-word for these situations.
```
alias union<byte, short, int, long, size, huge, float, double, triple> number

let x: number = 1
```

This can also be used for identifiers.
```
const pi = 3.14
alias pi pie
```
