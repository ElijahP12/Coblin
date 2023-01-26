The main syntax is a follows
```
fn name(parameter: type): type => expression
```
Multiple parameters are allowed by separating them by `,`. The expression at the right of `=>` gets returned by the function & the `:` after the `()` specifies the return type of the function.

Since functions return something, the return type can be implicitly typed, but the parameters are the only exception in the language, where their type must be explicitly typed.
```
fn name(parameter: type) => expression
```

The usage of code blocks is allowed for functions' return.
```
fn add(x: int, y: int) => {
  let sum = x + y
  sum
}
```

In order to call a function, `name(arguments)` is used, where if the function has multiple parameters, the arguments get separated by `,`.

**DEFAULT PARAMETERS**
You can provide a parameter a default value, using `=`, in-case an argument isn't required.
```
fn add(x: int, y: int = 1) => x + y
```
The user can still use `add(1, 2)`, but if they don't provide the last one, `1` gets used as `y`.

You can also provide a default value, based on other parameters.
```
fn add(x: int, y: int = x + 1) => x + y
```

**VARIABLE AMOUNT ARGUMENTS**
Using `...` it is possible to take variable amount of parameters & turn them to an `array`. An `array` can turn to arguments using `~` operator.
```
open std::array
fn add(x: ...) => array::sum(x)

add(~[1, 2, 3])
```

**HIGHER ORDER FUNCTIONS**
Functions are generic values & the type of a function is `fn<type, type>`, where the last type is the return type & all the others are the types of parameters. For example the type of the `add` function is `fn<int, int, int>`.

With functions being used as values, the concept of an anonymous function is also valid(Lambdas). These are functions that don't have names. The syntax of an anonymous function is the same function syntax, without the name & `fn` key-word. `()` are not needed for single parameters(Like Java-Script).
```
let add = (x: int, y: int) => x + y
```
All operators are valid lambdas. When a lambda is constructed as a function argument, the type can be inferred.

You can create a function with the same name for multiple types(Over-loading).

The execution of a function can be stopped, using the `exit` statement. If a function does not return anything, it has the return type of `unit`.

**FUNCTION CHANING**
The `|>`(Inverse apply operator) turns `f(1,1)` to `1 |> f(1)`, allowing ease of read when applying functions to a value.
