It is possible to create your own, using structures & ..., but they are some already hard-coded into the language.

**STATIC**
Static data types, only occupy a fixed amount of memory.

`char` - size: 8 bits
Used for storing single characters, wrapped by `''`.
By default it only stores ascii values, but using the buff(`^`) type operator, it can be used to store uni-code characters as well(`^char`).

There are some special characters, that can't be represented, hence a new syntax is permitted.
`'\n'` - new line
`'\''` - quotes
`'\"'` - double quotes
`'\\'` - normal back-slash

`byte`  - size: 8 bits
`short` - size: 16 bits
`int`   - size: 32 bits
`long`  - size: 64 bits
`size`  - size: depends on system(Like C's `size_t`)
These data types are used to store whole numbers. By default, those are signed integers, but that can be changed using the buff type operator(`^int`). `size`s are always un-singed.

`float`  - size: 64 bits
`double` - size: 128 bits
These data types, store real numbers.

`bool` - size: 1 bit
Stores values, either `true` or `false`.

`unit` - size: 0 bits
Can store nothing. Usage will later be provided.

`tuple`
A generic type that can be used to store a fixed amount of values, that main contain different types. Tuples are denoted by `()` & `,` can be used to seperate elements. If it only contains a single element `,` may be used at the end to specify that it's a tuple. For example the type of tuple `(1, true)` is `tuple<int, bool>`.

**DYNAMIC**
Dynamic types, allocate memory during the execution-time of the program.

`huge` - whole numbers
`triple` - real numbers
These types are used to store any integers or real, no matter how long.

`array`
This is a generic type that can be used to store a sequence of a type, ordered by an index.

The type it-self is denoted by `[]` & `,` can be used separate elements. For example the type of an array of ints, would be `array<int>`.

In order to access elements `name[index]` is used & indexes start at zero. `name[start:end]` can be used to take a slice of an array. Negative indexing is used to start at the end, rather than the begining.

`matrix`
This is an alias for an `array`, containing `array`s. For example `matrix<int>` is `array<array<int>>`.

`hash`
This is a generic type that is just like an array, but it uses keys instead of indexes. So a hash of `int` values, with `char` keys is `hash<char, int>`.

The type is denoted by `{}`(Not to be confused by code blocks) & the elements are separated by `,`. Also the keys & the values are separated by `:`. Accessing by a key is just like indexing an array(`name[key]`). 

`string`
This is just an alias for `array<char>` & is denoted by `""`. Both indexing & slicing are supported.

By default it can only store `char`s, but `^char`s can also be stored by using the buff type operator (`^string`).

Formatting for strings is supported for templates & there are also options to make custom types compatible with formatting. The main syntax is as it follows `"{value}"`(Like Python f-strings). In-order to use `{}` as characters, instead of formatting, `\{}` is permitted.

The value of a string template can be separated by a `:`, for special effects. A `"{1:x}"` will convert the number to hexadecimal.
`b`  - converts all numbers to binary.
`o`  - converts all numbers to octal.
`x`  - converts all numbers to hexa-decimal.
`>N` - shifts the value with tabs N times to the right.
`<N` - shifts the value with tabs N times to the left.
`?`  - pretty prints an array or a hash.

Multy-line strings are also allowed.

**SPECIAL TYPES**
`option`
A generic type that can be used to store a value that optionally might not exist. The value can either be `none` or `some(value)`.

`result`
A generic type that might be an error. The value is either `ok(value)` or `error(message)`, where the `message` is of type `string`. A result might not be generic, in this case the `ok` does not contain a value.
Errors caused by syntax, unknown identifiers & imports, types, operators & function argument count, do not create `result`s.

**TYPE CONVERSION**
By wrapping a type in `()`, at the left side of a value, it is possible to convert static types to each-other. Converting an `int` to a `double` would be `(double)1`.

When converting a `bool` into a numeric type & vise-versa, in-case it was `true` it turns to 1, other-wise 0. For converting a `char` to a numeric type & vise-versa, it turns into the corresponding ascii or uni-code value.

Converting a `char` to a `bool` & vise-versa is hereby not permitted. It is possible to convert larger data types, to smaller ones, which may cause data loss.

You can also convert types to `string` & from `string`, if string templating is enabled for that type. In case of converting from, it will reverse the order of templating.

Type conversion can be implicit.

**DYNAMICALLY TYPED**
The `type` type can be used, to tell the compiler to ignore type checking.
```
main {
  let x: type = 1
  x = "Hello, world!"
}
```
It can also be used on generics, so an `array<type>`, is still an array, but the elements can be anything.

**OPERATORS**
`+`
`-`
`*`
`/`
`\`
`%`
`^`
In order addition, subtraction, multiplication, division, whole division(No floats), remainder of division & exponent(Power).
`+` & `-` can also be used as prefixes on numbers that can be combined & work like mathematics.

`==`
`!=`
`>`
`<`
`>=`
`<=`
In order equality, inverse equality, bigger than, less than, bigger than or equal, less than or equal.

`&`
`|`
`!`
In order logical and, logical or & logical not.

`$`
Gets the memory address, which a value is stored in.
