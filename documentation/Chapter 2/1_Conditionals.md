The `case` statement, will take `bool` conditions & execute the first code-block or expression that corresponds to the first true condition. `_`(Wild-card operator) will be executed if all the conditions, where `false`.
```
case {
    1 == 1 => "of course it is!",
    1 != 2 => "this is also true, but 1 == 1 will be executed only, due to order",
    _ => "this will never get executed here, since all the above conditions are true"
}
```
The syntax is the `case` key-word, followed by `{}`, where each condition is mapped to it's expression or code-block by `=>`. Different conditions are separated by `,`.

The `case` statement, can also be used as an expression. It is important to always use the wild-card operator on expressions.
```
let message = case {
    1 == 1 => "of course it is!",
    1 != 2 => "this is also true, but 1 == 1 will be executed only, due to order",
    _ => "this will never get executed here, since all the above conditions are true"
}
```

For single conditions, there is a short-hand, where `case` is followed by a condition & a code-block.
```
case 1 == 2 {
    // this will never happen
}
```
