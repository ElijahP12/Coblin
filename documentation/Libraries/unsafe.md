A `ptr`(pointer) is a memory address.
```
alias size ptr
```

An `arena` is used for memory allocation & keeping track of it. `alloc` allocates `n` bytes of memory & returns a `ptr` pointing to the allocated data. `realloc` re-allocates `ptr` `p` & returns were it was pointing to. After all the allocations are done, `dealloc` must be used to free memory (Inspired by Zig).
```
use struct arena {
    ...

    fn alloc  (n: size        ): ptr
    fn realloc(n: size, p: ptr): ptr

    fn dealloc()
}
```

Copies `n` bytes of data from `ptr` `src` to `ptr` `dest`.
```
use fn copy(dest: ptr, source: ptr, n: size)
```

Gets what `ptr` `p` is pointing to(De-refrences).
```
use fn peek<T>(p: size): T
```

Executes a single assembly line. Uses assembly key-words(Like `mov` & `add`). Has support for registers(Like `%eax`) & `%identifier` for variables. Uses Intel assembly where the destination is the first argument.
```
use macro asm
```
*example*
```
open std::unsafe

fn add(x: int, y: int) => {
    var result = 0
    unsafe::asm(mov %eax, %x)
    unsafe::asm(add %eax, %y)

    unsafe::asm(mov %result, %eax)
    result
}
```
