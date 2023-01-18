The `repeat` loop, will execute a code-block, for-ever.
```
repeat {
    // the program will never be terminated
}
```
The `stop` & `cycle` statements, will configure the control flow of loops. `stop` exits out of the loop, while `cycle` goes through the next iteration.
```
var x = 0

repeat {
    case {
        x == 4 => cycle
        x == 8 => stop
    }

    x++
}
```

The `when` loop, will keep executing a code-block, till its condition is no longer met.
```
var x = 0

when x != 8 {
    x++
}
```
You can also supply a `when` loop, with a statement after `:` that will execute in every iteration.
```
var x = 0

when x != 8 : x++ {

}
```
The usage of another statement before condition that will initialize a variable for start-up of the loop is also permitted.
```
when x = 0 : x != 8 : x++ {

}
```

The `by` loop, will execute a code-block by a range.
```
by 10 {

}
```
The range can also conclude a starting range.
```
by 2 : 10 {

}
```
And it can also have an iteration range, which by default the range changes by one each iteration, but the iteration range will change one to the desired number.
```
by 2 : 10 : 2 {

}
```
We can also keep track of iteration of the range, by assigning a variable that stores the current number of the range.
```
by i : 2 : 10 : 2 {

}
```

Iterators generate values on the fly & they can only be iterated once.
The `for` loop, will iterate through an iterator. The `string`, `array` & `hash` data types have a built-in iterator(`string` turns into `char`). It is possible to create iterators for custom types, discussed later.
```
for i : "abc" {

}
```
```
for i : [1, 2, 3] {

}
```
```
for key, value : {'a': 1, 'b': 2, 'c': 3} {

}
```
We can track the index in a `for` loop as well.
```
for index : i : [1, 2, 3] {

}
```
