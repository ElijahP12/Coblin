Since `string` is an alias for `array<char>`, most functions at `array`, also work for `string`s.

Overloaded functions that can turn `string`/`char` `x` to upper & lower-case.
```
use fn upper(x: string): string
use fn upper(x: char  ): char

use fn lower(x: string): string
use fn lower(x: char  ): char
```

Splits `string` `x` using separator `sep` & returns an `array`, which does not contain the separators.
```
use fn split(x: string, sep: string): array<string>
```

Removes white-space from the right & left side of a `string`.
```
use fn trim     (x: string): string
use fn trimRight(x: string): string
use fn trimLeft (x: string): string
```

Returns all matches of regular expression `r` in `string` `s`.
```
use fn regex(s: string, r: string): array<string>
```
