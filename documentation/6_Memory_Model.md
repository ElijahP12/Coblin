**COPY VS VIEW**
By default, when variables get passed around, they get copied, meaning that a new value is created.
```
var x = 2
let y = x

x = 3
// y is still 2
```

But we can pass variables by viewing them, which point to the same value. We can view a variable, by using the view type operator(`&`).
```
var x = 2
let y: &int = x

x = 3
// y is now 3 as well
```

Un-like most programming languages, this does not differ for dynamic types.
```
var x = "Hello, world!"
let y = x

x = "Lorem, ipsum!"
// y is still Hello, world!
```

It is important that you can't create a `var` that views a `let`.

There is a short-cut for viewing, which will allow you to view implicitly. To do this add `&` before the name of the variable.
```
let x = 1
let &y = x
```

Function parameters always view by default, but they are immutable. When the view type operator is used on a parameter, it will allow mutability.

**DESTROY & FREE**
Destroying a variable is getting it out of scope & freeing a dynamic value is de-allocating it.

Destroying & freeing occur in reverse order.

At the end of a code-block, variables defined in it get destroyed.
```
let x = 1
// x gets destroyed here
```

In-case it is dynamic, it will also get freed.
```
let x = "Hello, world!"
// x gets destroyed here, "Hello, world!" gets freed here
```

Views only get destroyed, not freed.
```
let x = "Hello, world!"
let &y = x

// y gets destroyed here
// x gets destroyed here, "Hello, world!" gets freed here
```

For mutable dynamic variables, the values get freed after assignment.
```
var x = "Hello, world!"

x = "Lorem, ipsum!"
// "Hello, world!" gets freed here

// x gets destroyed here, "Lorem, ipsum!" gets freed here
```

Values returned, get freed at the end of the upper code-block, although variables get destroyed.
```
let x = {
  let y = "Hello, world!"
  y // y gets destroyed here
}

// x gets destroyed here, "Hello, world!" is freed here
```

Values returned, neither get copied nor viewed. It is a special case, where they get borrowed(Like Rust).
