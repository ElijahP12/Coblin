# Coblin - Code Goblin
Coblin is an open-source, compiled & multi-paradigm programming language developed by the Fire-Ship community(Known as Coblins).

# Hello, world!
```
open std::stream

main {
    stream::answerLine("Hello, world!")
}
```

# Simple & Fast Memory Model
Coblin uses the Copy & View memory model(Inspired by Rust). It automatically frees dynamic values without the need of a garbage collection in run-time.
* immutable & mutable
* static & dynamic
* copy & view
* destroy & free
```
// function with an immutable view, value returned, gets moved
fn inc(x: int) => ++x

// subroutine with a mutable view
fn change(x: &string) => {
    x = "Lorem, ipsum!"
    exit
}

main {
    let i = 1               // static  value
    var x = "Hello, world!" // dynamic value

    {
        let j = i           // gets coppied
        let y = x           // also gets coppied
    
        // j & y get destroyed, "Hello, world!" gets freed
    }

    let &y = x              // immutable view
    var &z = y              // mutable   view

    change(z)
    // "Hello, world!" gets freed
    // x & y also change to "Lorem, ipsum!"

    // ERROR - can't make a mutable view to an immutable value
    // var &j = i

    let t = inc(i)

    // i, x, y & z get destroyed, "Lorem ipsum" gets freed
}
```

# Multi-Paradigm
#### imperative
* Support for loops(`repeat`, `when`, `by`, `for`).
* Mutable variables & subroutines.
```
fn sum(xs: array<int>) => {
    var r = 0

    for i : xs {
        r += i
    }

    r
}
```
#### functional
* Higher-order functions & lambdas
* Pipe operator. `f(x, y)` = `x |> f(y)`
```
open std::array

fn sum(xs: array<int>) =>
    xs |> array::reduce((x, y) => x + y)
```

# Powerful Type System
* Type inference
* Constructors & deconstructors
* Iterators & string templates
* Inheritance
* Generics
* Over-loading & shadowing
* Unions

# Dynamically Typed
The standard library is statically typed, although dynamic typing is supported via the `type` type.
```
var x: type = 0

x = "Hello, world!"
```

# Macros & Meta-Programming
The powerful macros, allow changing the syntax of a language in a certain block of code(Inspired by Rust macros).
```
open std::stream

macro cpp {
    ($s:expr $xs:rep{<< $x}) => {
        $xs {
            stream::write($s, $x)
        }
    }
}

main {
    stream::out << "Hello, world!" << '\n'
}
```

# Low-Level Integration
* Pointers
* Memory allocation
* In-line assembly
```
open std::unsafe

fn add(x: int, y: int) => {
    var result = 0
    unsafe::asm(mov eax, x)
    unsafe::asm(add eax, y)

    unsafe::asm(mov $result, eax)
    result
}
```

# Packages
Modules are files designed for an intended purpose. They come together in a package. The standard library is the most important package, although additional ones can be installed via the package manager.
*data::info.cbln*
```
use const message = "Hello, world!"
```
*main.cbln*
```
open data::info

open std::stream

main {
    stream::answerLine(info::message)
}
```