Inserts element `x` to `array` `xs` by mutating. It will insert `x` to the last index of `xs`, by default. Returns an error if index `i` doesn't exist.
```
use fn append<T>(xs: &array<T>, x: T, i: size = length(x)): result
```

Removes an element by index `i` in `array` `xs`, by mutating. Returns an error if index `i` doesn't exist.
```
use fn remove<T>(xs: &array<T>, i: size): result
```

Finds the first index that matches element `x`, using linear search. It returns `none` in-case of `array` `xs` didn't contain element `x`. Similarly `contains` checks if element `x` exists in `array` `xs`.
```
use fn search  <T>(xs: array<T>, x: T): option<size>
use fn contains<T>(xs: array<T>, x: T): bool
```

Gives the length of array `xs`.
```
use fn length<T>(xs: array<T>): size
```

Sorts `array` `xs`, by using quick sort.
```
use fn sort<T>(xs: &array<T>)
```

Reverses the elements of `array` `xs`.
```
use fn reverse<T>(xs: &array<T>)
```

Removes duplicates from `array` `xs`.
```
use fn dedup<T>(xs: &array<T>)
```

The famous `map`, `filter` & `reduce`. These are all immutable, meaning that they will return a new `array`, instead of modifying the old one. `map` applies function `f` to all elements of `xs`. `filter` will only allow elements that pass `function` `f` as `true`, stay. `reduce` starts by the first & second element of `xs` & applies `f` to them. The next iteration will apply function `f` to the result of the last iteration & current element.
```
use fn map   <T, B>(xs:  array<T>, f: fn<T,       B>): array<T>
use fn filter<T   >(xs:  array<T>, f: fn<T, bool   >): array<T>
use fn reduce<T   >(xs:  array<T>, f: fn<T, T   , T>): array<T>
```

`all` checks if all elements of `array` `xs` pass a function, while `any` will return `true` even if a single element passes.
```
use fn all<T>(xs: array<T>, f: fn<T, bool>): bool
use fn any<T>(xs: array<T>, f: fn<T, bool>): bool
```

Creates a new `array`, given starting range `x`, ending range `y` & separater `s` that specifies how the next element must advance. This is an overloaded function, that works for all numeric data types.
```
use fn range(x: int , y: int , sep: int  = 1): array<int >
...
use fn range(x: size, y: size, sep: size = 1): array<size>
```

Takes `array` `xs` & `array` `xz` & returns a new `array` containing two element long `array`s containing the elements of `xs` & `xz` that have a matching index. `enumerate` zips `array` `xs` by index of each element.
```
use fn zip<T>(xs: array<T>, xz: array<T>): array<tuple<T, T>>
use fn enumerate(xs: array<T>): array<tuple<size, T>>
```

Flattens `matrix` `xs` to an `array`.
```
use fn flatten<T>(xs: matrix<T>): array<T>
```

Safe version of indexing that returns an `option` when the index is not found.
```
use fn index<T>(xs: array<T>, i: size): option<T>
```
