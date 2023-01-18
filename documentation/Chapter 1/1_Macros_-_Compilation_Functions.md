Macros get copy & pasted in the compilation time of the program. They are little blocks with their own syntax, which can shorten our code. Macros in this language are directly inspired by Rust.

We can create a macro using the `macro` key-word & identifier, followed by a pattern match. These patterns use the special macro language that consist of designators, which usually go by `$identifier:type` which may have an optional `{}`. Then in the block, we can use `$identifier` to replace the value.

**DESIGNATORS' TYPES**
The `expr` macro type checks for expressions. Here is an example of using python-like logical operators, instead of default `&|!`.
```
macro py_logic {
    ($x:expr and $y:expr) => {
        x & y
    },
    ($x:expr or $y:expr) => {
        x | y
    },
    (not $x:expr) => {
        !x
    }
}

py_logic(true and false)
py_logic(true or  false)
py_logic(not true)
```

Similar to `expr`. The `ident`, `op` & `type` types, check for identifiers, operators & types.
```
macro func {
    ($i:ident ($x:ident : $t:type, $y:ident : $_:type) $o:op) => {
        fn $i($x: $t, $y: $t) => {
            $x $o $y
        }
    }
}

func(add (x: int, y: int) +)
add(1,1)
```

`rep` shows that a pattern might get repeated, it uses `{}` to annotate the repeated pattern & loop in the block. Here is one to replicate C++'s stream insertion operator.
```
open std::stream

macro cpp {
    ($s:expr $xs:rep{<< $x}) => {
        $xs {
            stream::write($s, $x)
        }
    }
}

stream::out << "Hello, world!" << '\n'
```
