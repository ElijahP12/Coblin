The main syntax of a variable is as it follows.
```
keyword name: type = expression
```

The language is smart enough to implicitly determine the type, based on the expression.
```
keyword name = expression
```

You can also assign a value, later of the declaration, but you can't use the value. You also must explicitly annotate the type.
```
keyword name: type
```

Variables defined using the `let` keyword are immutable. Meaning that after assignment, you can't change their value.
Variables defined with `const`, are compilation-time constants.
Variables defined with `var`, are your regular variables, that can be mutated at any time.

There are no global variables(Constants are exceptions).

You can re-create a new variable with the same name(Shadowing).
