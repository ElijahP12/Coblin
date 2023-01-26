Structures allow us to create a custom type that consist of multiple fields with different types. The type of a structure is it's name. To create a new value of the structure, use its name with `()`, called an object. You can access individual fields of a structure using the `.`(Type access) operator.
```
struct person {
    name  : string,
    age   : byte  ,
    gender: string
}

var x: person = person()

x.name   = "Teker"
x.age    = 7
x.gender = "cat"
```

Constructors are functions that get called when a structure gets created. They use the `init` keyword, followed by a code-block, un-like regular functions. The `this` key-word, refers to the current object. The arguments used by a constructor, get filled in the `()` after the type.
```
struct person {
    name  : string,
    age   : byte  ,
    gender: string

    init(name: string, age: byte, gender: string) {
        this.name   = name
        this.age    = age
        this.gender = gender
    }
}

let x = person("Teker", 7, "cat")
```

De-constructors are the opposite of constructors. They get activated in the same place, where a dynamic type would get freed. Creating one is just like a constructors, but using the `deinit` keyword instead & they can't take any arguments.
```
struct person {
    name  : string,
    age   : byte  ,
    gender: string

    init(name: string, age: byte, gender: string) {
        this.name   = name
        this.age    = age
        this.gender = gender
    }

    deinit {
        // ...
    }
}

let x = person("Teker", 7, "cat")

// x gets destructed here
```

A structure can also posses many other functions. Functions decalared in structures are called methods. Methods are treated like fields.
```
struct person {
    name  : string,
    age   : byte  ,
    gender: string

    init(name: string, age: byte, gender: string) {
        this.name   = name
        this.age    = age
        this.gender = gender
    }

    fn greet() => "Hello {this.name}!"
}

let x = person("Teker", 7, "cat")

let message = x.greet()
```

Structures can also inherit fields from each-other. The `that` key-word is used to access the struct that it inherits(Like `super` in other languages). The constructors of the inherited structure don't get activated, by default. Rather you have to fill them in current structure's constructor.
```
struct creature {
    name  : string,
    age   : byte  ,
    gender: string

    init(name: string, age: byte, gender: string) {
        this.name   = name
        this.age    = age
        this.gender = gender
    }
}

struct person(creature) {
    init(name: string, age: byte, gender: string) {
        that.init(name, age, gender)
    }

    fn greet() => "Hello {this.name}!"
}

let x = person("Teker", 7, "cat")

let message = x.greet()
```

It is to make a structure that is an iterator. This done by the `iterate` custom function that uses the `yield` key-word to return the result of each iteration.
```
struct ourArray {
    value: array<int>

    init(value: array<int>) {
        this.value = value
    }

    iterate {
        for i : this.value {
            yield i
        }
    }
}

let x = ourArray([1, 2, 3])

for i : x {

}
```

To support the structure for formatting in string templates, the `template` custom function is used, along with the `format` key-word that will return the string used for formatting. Note that `format` can be used multiple times & the result will be concatinated.
```
struct ourArray {
    value: array<int>

    init(value: array<int>) {
        this.value = value
    }

    iterate {
        for i : this.value {
            yield i
        }
    }

    template {
        format '['

        for i : this.value[:-1] {
            format "{i}, "
        }

        let last = this.value[-1]
        format "{last}]"
    }
}

let x = ourArray([1, 2, 3])

let y = "{x}"
```
