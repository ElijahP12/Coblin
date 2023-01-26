Most things here are self-explanatory.

```
use alias union<byte, short, int, long, huge, float, double, triple> number
```

```
const pi: double = 3.141592653589793
const e : double = 2.718281828459045
```

```
use fn abs(x: number, y: number): number
use fn max(x: number, y: number): number
use fn min(x: number, y: number): number
use fn GCD(x: number, y: number): number
use fn LCM(x: number, y: number): number
```

```
use fn fact    (x: number): number
use fn fib     (x: number): number
use fn is_prime(x: number): number
```

Gives the `n`th root of `x`.
```
use fn root(x: number, n: number): number
```

Sine, cosine & tangant, which inverse & hyperbolic can be configure, by default `false`.
```
use fn sin(x: number, a: bool = false, h: bool = false)
use fn cos(x: number, a: bool = false, h: bool = false)
use fn tan(x: number, a: bool = false, h: bool = false)
```

Finds the `n` logarithm of `x`.
```
use fn log(x: number, n: number): number
```

Safe versions of division & modulo that return a `result`, for cases like division by zero.
```
use fn div(x: number, y: number): result<number>
use fn mod(x: number, y: number): result<number>
```
