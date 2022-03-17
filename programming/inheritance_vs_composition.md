---
theme: https://raw.githubusercontent.com/dannylongeuay/tech-slides/main/themes/dark.json
---

# Inheritance vs Composition

## A brief comparison with Python and Golang

---

## Why do software engineers use inheritance or composition?

- Modeling
- Separation of responsibilities
- Code reuse

---

## What is Inheritance?

- Mechanism to derive an object from another object

> The car is a vehicle

---

## When to use Inheritance?

- Group related concepts in a domain
- The child object uses the entire implementation of the parent object and changes are additive

> What a car is

---

## Pros of Inheritance

- Models the world how we humans understand it (generalized to specialized)
- Code reuse and augmentation in child objects

---

## Cons of Inheritance

- Deeply nested objects can complicate and confuse
- Tight coupling between parent/child objects
- Strict design requirements

---

## What is Composition?

- Combine related objects into more complex objects

> The car has a steering wheel

---

## When to use Composition?

- Build a whole from parts

> What a car does

---

## Pros of Composition

- Loose coupling between components
- Natural design process
- Composition is interchangeable with inheritance (for most languages)

---

## Cons of Composition

- Composition turning into decomposition
- Verbosity

---

## Python Examples (Inheritance)

```python
class Foo:
    x = "Buzz"


class Bar(Foo):
    y = "Bazz"


foo = Foo()
bar = Bar()

print("Do bar and foo have the same type?", type(bar) == type(foo))
```

---

## Python Examples Cont. (Inheritance)

```python
class Foo:
    x = "Buzz"


class Bar(Foo):
    y = "Bazz"


foo = Foo()
bar = Bar()

print("Is a bar an instance of a foo?", isinstance(bar, type(foo)))
print("Is a foo an instance of a bar?", isinstance(foo, type(bar)))
```

---

## Python Examples Cont. (Inheritance)

```python
class Foo:
    x = "Buzz"


class Bar(Foo):
    y = "Bazz"


foo = Foo()
bar = Bar()

print("Is a bar a subclass of foo?", issubclass(Bar, Foo))
print("Is a foo a subclass of bar?", issubclass(Foo, Bar))
```

---

## Python Examples Cont. (Inheritance)

```python
class Foo:
    x = "Buzz"


class Bar(Foo):
    y = "Bazz"


foo = Foo()
bar = Bar()

foos: list[Foo] = [foo, bar]

for fu in foos:
    print("Object of type", type(fu), "has an attribute x =", fu.x)
```

---

## Python Examples Cont. (Inheritance)

```python
class Foo:
    x = "Buzz"


class Bar(Foo):
    y = "Bazz"


foo = Foo()
bar = Bar()

bars: list[Bar] = [foo, bar]

for brr in bars:
    try:
        print("Object of type", type(brr), "has an attribute y =", brr.y)
    except AttributeError as err:
        print(err)
```

---

## Golang Examples (Composition)

```go
package main

import (
  "fmt"
  "reflect"
)

type Foo struct {
  x string
}

type Bar struct {
  Foo
  y string
}

func main() {
  foo := Foo{"Buzz"}
  bar := Bar{foo, "Bazz"}

  fmt.Println("Do bar and foo have the same type?", reflect.TypeOf(bar) == reflect.TypeOf(foo))
}
```

---

## Golang Examples Cont. (Composition)

```go
package main

import (
  "fmt"
  "reflect"
)

type Foo struct {
  x string
}

type Bar struct {
  Foo
  y string
}

func main() {
  foo := Foo{"Buzz"}
  bar := Bar{foo, "Bazz"}

  fmt.Println("Does a bar have a foo?", reflect.TypeOf(bar.Foo) == reflect.TypeOf(foo))
}
```

---

## Golang Examples Cont. (Composition)

```go
package main

import (
  "fmt"
  "reflect"
)

type Foo struct {
  x string
}

type Bar struct {
  Foo
  y string
}

func main() {
  foo := Foo{"Buzz"}
  bar := Bar{foo, "Bazz"}

  fmt.Println("Does a foo have a bar?", reflect.TypeOf(foo.Bar) == reflect.TypeOf(bar))
}
```

---

## Golang Examples Cont. (Composition)

```go
package main

import (
  "fmt"
  "reflect"
)

type Foo struct {
  x string
}

type Bar struct {
  Foo
  y string
}

func main() {
  foo := Foo{"Buzz"}
  bar := Bar{foo, "Bazz"}

  foobardoos := make([]interface{}, 3)
  foobardoos[0] = foo
  foobardoos[1] = bar
  foobardoos[2] = "doo"

  for _, v := range foobardoos {
    switch v.(type) {
    case Foo:
      fu := v.(Foo)
      fmt.Println("Struct of type", reflect.TypeOf(fu), "has attribute x =", fu.x)
    case Bar:
      brr := v.(Bar)
      fmt.Println("Struct of type", reflect.TypeOf(brr), "has attribute x =", brr.x)
      fmt.Println("Struct of type", reflect.TypeOf(brr), "has attribute y =", brr.y)
    default:
      fmt.Println(reflect.TypeOf(v), "is an unhandled type")
    }
  }
}
```

---

## Quote of the Day

> Favor composition over inheritance

---

## Q&A

```rust
fn main() {
  println!("Thanks for listening! Any questions?")
}
```
