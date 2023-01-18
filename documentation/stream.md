A buffer that supports I/O operations, it has a de-constructor that automatically closes the connection.
```
use struct stream {
    ...
}
```

Connections to the `stdout`, `stdin` & `stderr` streams.
```
use const out: &stream 
use const in : &stream
use const err: &stream
```

Creates a new `stream` connecting to the file with the name `f`. It returns the new `stream` on success, but will return an error if the file could not be found.
```
use fn open(f: string): result<stream>
```

Writes elements of `xs` to `stream` `s`. The `write` & `writeLine` functions will return an error if the connection is no longer valid.
The next write operation, will always append to the end of the last write operation. The first write operation starts at the end of the `stream` `s`.
Members of `xs` may only be values that support string templates.
```
use fn write     (s: &stream, xs: ...): result
use fn writeLine (s: &stream, xs: ...): result // adds a new-line
use fn answer    (xs: ...            )         // always writes to stdout
use fn answerLine(xs: ...            )         // adds a new-line
```

A word is a sequince of characters, which is seperated from other words by white-space. This reads `n` words from `stream` `s` & returns an array, containing the words. It will error in-case of in-valid connection or if `stream` `s` contains less words than `n`. Since `stdin` is always valid. `ask` will only error if there weren't enough words.
The next read operation will occur at the start of the first word that wasn't read by the last read operation. The first read operation always starts at the first character of `stream` `s`.
```
use fn read(s: &stream, n: size): result<array<string>> 
use fn ask (n: size            ): result<array<string>> // always reads from stdin
```

Reads a whole line from `stream` `s`. Returns the line as a `string` & errors in-case connection is no longer valid.
```
use fn readLine(s: &stream): result<string>
use fn askLine (          ): string         // always reads from stdin
```

Clear, empties the buffer of `stream` `s` & Flush, flushes `stream` `s`. If the connection is no longer valid, they will fail
```
use fn clear(s: &stream): result
use fn flush(s: &stream): result
```
