De-structuring is extracting data, from compound types. Compound types get de-structured by patterns. In a pattern the position of the data is the field & it contains a value.
```
let [first, last] = [1, 2]
// first is 1, last is 2
```
*function parameters may also support de-structing*

The value ignore operator(Wild-card operator`_`), can be used for ignoring the value of a field in a pattern.
```
let [_, last] = [1, 2]
// the first value is ignored, last is 2
```

There is also the field ignore operater(Range operator`...`) which can be used once in every pattern. This continuously ignores fields by position in a pattern.
```
let [first, ..., last] = [1, 2, 3, 4, 5, 6]
// first is 1, last is 6
```

Pattern matching, will execute the expression or code block which corresponds to the first pattern that a value can de-structure to.
```
match [1, 2, 3] {
    [] => "this array is empty",
    [..., last] => "the latest value is {last}"
}
```
The syntax is just like a `case` statement, but after `match` the value we want to match against is specified.

Just like the `case` statement, it can also be used as an expression. There needs to be at least one matching pattern for all possible values if it's an expression.
```
let last = match [1, 2, 3] {
    [] => none,
    [..., xs] => some(xs)
}
```
