`open` can be used to import functions & ... from other files(modules). `::` can be used to access modules. Only things from the package level can be used, if they have a `use` before them.
*info*
```
use const message = "Hello, world!"
```
*main*
```
open std::stream
open info

main {
    stream::answerLine(info::message)
}
```

Using the package manager, it is possible to install packages. To use the contents of a package the package name must also be provided.
*Consider that info is defined in an installed package called doc*
```
open std::stream
open doc::info

main {
    stream::answerLine(info::message)
}
```

You can import everything from a module using `*` or only some stuff by using `()`.
```
open std::stream::*

main {
    answerLine("Hello, world!")
}
```
```
open std::stream::(answerLine)

main {
    answerLine("Hello, world!")
}
```

**STANDARD LIBRARY**
The `std` library is a package which is installed by default & cannot be removed. It provides many modules for a lot of common programming utilities.

It is built in a way that the language can work perfectly fine without it, but when building an application it is pretty much essential & some things can't be done without it.
