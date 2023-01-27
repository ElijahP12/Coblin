Coblin is a compiled, multi-paradigm language.

It consists of statements(They do something), expressions(They evaluate down to something), declarations(Giving name to something) & code-blocks(Allow usage of multiple statements, expressions & declarations).

Code-blocks are defined using `{}` & anything in-side those is part of the code-blocks scope. Semi-colons are used for ending expressions & ..., except code-blocks. The usage of semi-colons is not necessary(Like Go).

The entry point of a program is the main keyword, followed by a code-block. Here is Hello-World!
```
open std::stream

main {
  stream::answerLine("Hello, world!")
}
```

`camelCase` is used for everything in this language. `//` defines comments, ignored by the compiler. `/*` `*/` is also used for multi line comments.
