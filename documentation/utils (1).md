`date` is used to store real-life dates. When getting initialized it will use today's date. Addition & subtraction between `date`s are possible using `add` & `sub`.
```
use struct date {
    milis   : ^short
    secs    : ^byte
    mins    : ^byte
    hours   : ^byte
    days    : ^short
    months  : ^byte
    years   : ^byte
    decades : ^byte
    centries: ^byte

    init()
    template

    fn add(x: data): date
    fn sub(x: data): date
}
```

Generates a random number based on seed `s`.
```
use fn rand(s: ^long): ^long
```

Command-line arguments.
```
use const arg: array<string>
```
