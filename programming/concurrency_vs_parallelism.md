---
theme: https://raw.githubusercontent.com/dannylongeuay/tech-slides/main/themes/dark.json
---

# Concurrency vs Parallelism

## A brief comparison with Python and Golang

---

## What is concurrency

Execution of tasks are interwoven in a single thread

> Your house has dirty dishes and laundry
> You load the dishwasher and start it
> You load the washing machine and start it
> The washing machine finishes
> You load the dryer and start it
> The dishwasher finishes
> The dryer finishes

---

## What is Parallelism

Execution of tasks are done simultaneously in separate processes

> Your house has dirty dishes and laundry
> You do the dishes
> Your significant other does the laundry

---

## Pros of Concurrency

- Threads have a lower overhead cost than processes
- Shared memory, sharing data between tasks is simple

---

## Cons of Concurrency

- Divided attention (interrupted)
- Shared memory, larger blast radius
- Non-deterministic

---

## Pros of Parallelism

- Dedicated attention (independence)
- Separate memory, smaller blast radius
- Deterministic

---

## Cons of Parallelism

- Processes have a higher overhead cost than threads (minimized by pooling)
- Separate memory, sharing data between tasks is complex

---

## Concurrency and Parallelism

```
Concurrency               Concurrency + parallelism
(Single-Core CPU)         (Multi-Core CPU)
 __                        __ __
|t1|                      |t1|t2|
|  |                      |  |__|
|__|__                    |  |__
   |t2|                   |__|t2|
 __|__|                    __|__|
|t1|                      |t1|
|__|__                    |  |__
   |t2|                   |  |t2|
   |__|                   |__|__|
```

---

## General Guidance

- Long-running and CPU intensive operations benefit from parallelism

  - Mathematical computations
  - Machine learning

- I/O intensive operations benefit from concurrency
  - Network API calls
  - File system operations

---

## Python Example (Concurrency)

```python
import asyncio

async def do_laundry():
    print('Load dirty laundry into washing machine')
    await asyncio.sleep(2)
    print('Washing machine cycle finishes')
    print('Load wet laundry into dryer')
    await asyncio.sleep(4)
    print('Dryer cycle finishes')

async def do_dishes():
    print('Load dirty dishes into dishwasher')
    await asyncio.sleep(4)
    print('Dishwasher cycle finishes')

async def main():
    task1 = asyncio.create_task(do_dishes())
    task2 = asyncio.create_task(do_laundry())

    await task1
    await task2

asyncio.run(main())
```

---

## Python Example (Concurrency)

```python
import asyncio

async def do_laundry():
    print('Load dirty laundry into washing machine')
    await asyncio.sleep(2)
    print('Washing machine cycle finishes')
    print('Load wet laundry into dryer')
    await asyncio.sleep(4)
    print('Dryer cycle finishes')

async def do_dishes():
    print('Load dirty dishes into dishwasher')
    await asyncio.sleep(4)
    print('Dishwasher cycle finishes')

async def main():
    task1 = asyncio.create_task(do_dishes())
    task2 = asyncio.create_task(do_laundry())

    await task1
    await task2

asyncio.run(main())
```

Load dirty dishes into dishwasher

---

## Python Example (Concurrency)

```python
import asyncio

async def do_laundry():
    print('Load dirty laundry into washing machine')
    await asyncio.sleep(2)
    print('Washing machine cycle finishes')
    print('Load wet laundry into dryer')
    await asyncio.sleep(4)
    print('Dryer cycle finishes')

async def do_dishes():
    print('Load dirty dishes into dishwasher')
    await asyncio.sleep(4)
    print('Dishwasher cycle finishes')

async def main():
    task1 = asyncio.create_task(do_dishes())
    task2 = asyncio.create_task(do_laundry())

    await task1
    await task2

asyncio.run(main())
```

Load dirty dishes into dishwasher

Load dirty laundry into washing machine

---

## Python Example (Concurrency)

```python
import asyncio

async def do_laundry():
    print('Load dirty laundry into washing machine')
    await asyncio.sleep(2)
    print('Washing machine cycle finishes')
    print('Load wet laundry into dryer')
    await asyncio.sleep(4)
    print('Dryer cycle finishes')

async def do_dishes():
    print('Load dirty dishes into dishwasher')
    await asyncio.sleep(4)
    print('Dishwasher cycle finishes')

async def main():
    task1 = asyncio.create_task(do_dishes())
    task2 = asyncio.create_task(do_laundry())

    await task1
    await task2

asyncio.run(main())
```

Load dirty dishes into dishwasher

Load dirty laundry into washing machine

Washing machine cycle finishes

---

## Python Example (Concurrency)

```python
import asyncio

async def do_laundry():
    print('Load dirty laundry into washing machine')
    await asyncio.sleep(2)
    print('Washing machine cycle finishes')
    print('Load wet laundry into dryer')
    await asyncio.sleep(4)
    print('Dryer cycle finishes')

async def do_dishes():
    print('Load dirty dishes into dishwasher')
    await asyncio.sleep(4)
    print('Dishwasher cycle finishes')

async def main():
    task1 = asyncio.create_task(do_dishes())
    task2 = asyncio.create_task(do_laundry())

    await task1
    await task2

asyncio.run(main())
```

Load dirty dishes into dishwasher

Load dirty laundry into washing machine

Washing machine cycle finishes

Load wet laundry into dryer

---

## Python Example (Concurrency)

```python
import asyncio

async def do_laundry():
    print('Load dirty laundry into washing machine')
    await asyncio.sleep(2)
    print('Washing machine cycle finishes')
    print('Load wet laundry into dryer')
    await asyncio.sleep(4)
    print('Dryer cycle finishes')

async def do_dishes():
    print('Load dirty dishes into dishwasher')
    await asyncio.sleep(4)
    print('Dishwasher cycle finishes')

async def main():
    task1 = asyncio.create_task(do_dishes())
    task2 = asyncio.create_task(do_laundry())

    await task1
    await task2

asyncio.run(main())
```

Load dirty dishes into dishwasher

Load dirty laundry into washing machine

Washing machine cycle finishes

Load wet laundry into dryer

Dishwasher cycle finishes

---

## Python Example (Concurrency)

```python
import asyncio

async def do_laundry():
    print('Load dirty laundry into washing machine')
    await asyncio.sleep(2)
    print('Washing machine cycle finishes')
    print('Load wet laundry into dryer')
    await asyncio.sleep(4)
    print('Dryer cycle finishes')

async def do_dishes():
    print('Load dirty dishes into dishwasher')
    await asyncio.sleep(4)
    print('Dishwasher cycle finishes')

async def main():
    task1 = asyncio.create_task(do_dishes())
    task2 = asyncio.create_task(do_laundry())

    await task1
    await task2

asyncio.run(main())
```

Load dirty dishes into dishwasher

Load dirty laundry into washing machine

Washing machine cycle finishes

Load wet laundry into dryer

Dishwasher cycle finishes

Dryer cycle finishes

---

## Python Example (Parallelism)

```python
from time import sleep
from multiprocessing import Process

def do_laundry():
    print('Load dirty laundry into washing machine')
    sleep(2)
    print('Washing machine cycle finishes')
    print('Load wet laundry into dryer')
    sleep(4)
    print('Dryer cycle finishes')

def do_dishes():
    print('Load dirty dishes into dishwasher')
    sleep(4)
    print('Dishwasher cycle finishes')

def main():
    task1 = Process(target=do_dishes)
    task2 = Process(target=do_laundry)

    task1.start()
    task2.start()

    task1.join()
    task2.join()

main()
```

---

## Python Example (Parallelism)

```python
from time import sleep
from multiprocessing import Process

def do_laundry():
    print('Load dirty laundry into washing machine')
    sleep(2)
    print('Washing machine cycle finishes')
    print('Load wet laundry into dryer')
    sleep(4)
    print('Dryer cycle finishes')

def do_dishes():
    print('Load dirty dishes into dishwasher')
    sleep(4)
    print('Dishwasher cycle finishes')

def main():
    task1 = Process(target=do_dishes)
    task2 = Process(target=do_laundry)

    task1.start()
    task2.start()

    task1.join()
    task2.join()

main()
```

Load dirty dishes into dishwasher

---

## Python Example (Parallelism)

```python
from time import sleep
from multiprocessing import Process

def do_laundry():
    print('Load dirty laundry into washing machine')
    sleep(2)
    print('Washing machine cycle finishes')
    print('Load wet laundry into dryer')
    sleep(4)
    print('Dryer cycle finishes')

def do_dishes():
    print('Load dirty dishes into dishwasher')
    sleep(4)
    print('Dishwasher cycle finishes')

def main():
    task1 = Process(target=do_dishes)
    task2 = Process(target=do_laundry)

    task1.start()
    task2.start()

    task1.join()
    task2.join()

main()
```

Load dirty dishes into dishwasher

Load dirty laundry into washing machine

---

## Python Example (Parallelism)

```python
from time import sleep
from multiprocessing import Process

def do_laundry():
    print('Load dirty laundry into washing machine')
    sleep(2)
    print('Washing machine cycle finishes')
    print('Load wet laundry into dryer')
    sleep(4)
    print('Dryer cycle finishes')

def do_dishes():
    print('Load dirty dishes into dishwasher')
    sleep(4)
    print('Dishwasher cycle finishes')

def main():
    task1 = Process(target=do_dishes)
    task2 = Process(target=do_laundry)

    task1.start()
    task2.start()

    task1.join()
    task2.join()

main()
```

Load dirty dishes into dishwasher

Load dirty laundry into washing machine

Washing machine cycle finishes

---

## Python Example (Parallelism)

```python
from time import sleep
from multiprocessing import Process

def do_laundry():
    print('Load dirty laundry into washing machine')
    sleep(2)
    print('Washing machine cycle finishes')
    print('Load wet laundry into dryer')
    sleep(4)
    print('Dryer cycle finishes')

def do_dishes():
    print('Load dirty dishes into dishwasher')
    sleep(4)
    print('Dishwasher cycle finishes')

def main():
    task1 = Process(target=do_dishes)
    task2 = Process(target=do_laundry)

    task1.start()
    task2.start()

    task1.join()
    task2.join()

main()
```

Load dirty dishes into dishwasher

Load dirty laundry into washing machine

Washing machine cycle finishes

Load wet laundry into dryer

---

## Python Example (Parallelism)

```python
from time import sleep
from multiprocessing import Process

def do_laundry():
    print('Load dirty laundry into washing machine')
    sleep(2)
    print('Washing machine cycle finishes')
    print('Load wet laundry into dryer')
    sleep(4)
    print('Dryer cycle finishes')

def do_dishes():
    print('Load dirty dishes into dishwasher')
    sleep(4)
    print('Dishwasher cycle finishes')

def main():
    task1 = Process(target=do_dishes)
    task2 = Process(target=do_laundry)

    task1.start()
    task2.start()

    task1.join()
    task2.join()

main()
```

Load dirty dishes into dishwasher

Load dirty laundry into washing machine

Washing machine cycle finishes

Load wet laundry into dryer

Dishwasher cycle finishes

---

## Python Example (Parallelism)

```python
from time import sleep
from multiprocessing import Process

def do_laundry():
    print('Load dirty laundry into washing machine')
    sleep(2)
    print('Washing machine cycle finishes')
    print('Load wet laundry into dryer')
    sleep(4)
    print('Dryer cycle finishes')

def do_dishes():
    print('Load dirty dishes into dishwasher')
    sleep(4)
    print('Dishwasher cycle finishes')

def main():
    task1 = Process(target=do_dishes)
    task2 = Process(target=do_laundry)

    task1.start()
    task2.start()

    task1.join()
    task2.join()

main()
```

Load dirty dishes into dishwasher

Load dirty laundry into washing machine

Washing machine cycle finishes

Load wet laundry into dryer

Dishwasher cycle finishes

Dryer cycle finishes

---

## Golang Example (Concurrency)

```go
package main

import (
  "fmt"
  "time"
)

func do_laundry() <-chan int {
  laundry := make(chan int)
  go func() {
    defer close(laundry)
    fmt.Println("Load dirty laundry into washing machine")
    time.Sleep(time.Second * 2)
    fmt.Println("Washing machine cycle finishes")
    fmt.Println("Load wet laundry into dryer")
    time.Sleep(time.Second * 4)
    fmt.Println("Dryer cycle finishes")
  }()
  return laundry
}

func do_dishes() <-chan int {
  dishes := make(chan int)
  go func() {
    defer close(dishes)
    fmt.Println("Load dirty dishes into dishwasher")
    time.Sleep(time.Second * 4)
    fmt.Println("Dishwasher cycle finishes")
  }()
  return dishes
}

func main() {
  dishesChan := do_dishes()
  laundryChan := do_laundry()
  <-dishesChan
  <-laundryChan
}
```

---

## Golang Example (Concurrency)

```go
package main

import (
  "fmt"
  "time"
)

func do_laundry() <-chan int {
  laundry := make(chan int)
  go func() {
    defer close(laundry)
    fmt.Println("Load dirty laundry into washing machine")
    time.Sleep(time.Second * 2)
    fmt.Println("Washing machine cycle finishes")
    fmt.Println("Load wet laundry into dryer")
    time.Sleep(time.Second * 4)
    fmt.Println("Dryer cycle finishes")
  }()
  return laundry
}

func do_dishes() <-chan int {
  dishes := make(chan int)
  go func() {
    defer close(dishes)
    fmt.Println("Load dirty dishes into dishwasher")
    time.Sleep(time.Second * 4)
    fmt.Println("Dishwasher cycle finishes")
  }()
  return dishes
}

func main() {
  dishesChan := do_dishes()
  laundryChan := do_laundry()
  <-dishesChan
  <-laundryChan
}
```

Load dirty dishes into dishwasher

---

## Golang Example (Concurrency)

```go
package main

import (
  "fmt"
  "time"
)

func do_laundry() <-chan int {
  laundry := make(chan int)
  go func() {
    defer close(laundry)
    fmt.Println("Load dirty laundry into washing machine")
    time.Sleep(time.Second * 2)
    fmt.Println("Washing machine cycle finishes")
    fmt.Println("Load wet laundry into dryer")
    time.Sleep(time.Second * 4)
    fmt.Println("Dryer cycle finishes")
  }()
  return laundry
}

func do_dishes() <-chan int {
  dishes := make(chan int)
  go func() {
    defer close(dishes)
    fmt.Println("Load dirty dishes into dishwasher")
    time.Sleep(time.Second * 4)
    fmt.Println("Dishwasher cycle finishes")
  }()
  return dishes
}

func main() {
  dishesChan := do_dishes()
  laundryChan := do_laundry()
  <-dishesChan
  <-laundryChan
}
```

Load dirty dishes into dishwasher

Load dirty laundry into washing machine

---

## Golang Example (Concurrency)

```go
package main

import (
  "fmt"
  "time"
)

func do_laundry() <-chan int {
  laundry := make(chan int)
  go func() {
    defer close(laundry)
    fmt.Println("Load dirty laundry into washing machine")
    time.Sleep(time.Second * 2)
    fmt.Println("Washing machine cycle finishes")
    fmt.Println("Load wet laundry into dryer")
    time.Sleep(time.Second * 4)
    fmt.Println("Dryer cycle finishes")
  }()
  return laundry
}

func do_dishes() <-chan int {
  dishes := make(chan int)
  go func() {
    defer close(dishes)
    fmt.Println("Load dirty dishes into dishwasher")
    time.Sleep(time.Second * 4)
    fmt.Println("Dishwasher cycle finishes")
  }()
  return dishes
}

func main() {
  dishesChan := do_dishes()
  laundryChan := do_laundry()
  <-dishesChan
  <-laundryChan
}
```

Load dirty dishes into dishwasher

Load dirty laundry into washing machine

Washing machine cycle finishes

---

## Golang Example (Concurrency)

```go
package main

import (
  "fmt"
  "time"
)

func do_laundry() <-chan int {
  laundry := make(chan int)
  go func() {
    defer close(laundry)
    fmt.Println("Load dirty laundry into washing machine")
    time.Sleep(time.Second * 2)
    fmt.Println("Washing machine cycle finishes")
    fmt.Println("Load wet laundry into dryer")
    time.Sleep(time.Second * 4)
    fmt.Println("Dryer cycle finishes")
  }()
  return laundry
}

func do_dishes() <-chan int {
  dishes := make(chan int)
  go func() {
    defer close(dishes)
    fmt.Println("Load dirty dishes into dishwasher")
    time.Sleep(time.Second * 4)
    fmt.Println("Dishwasher cycle finishes")
  }()
  return dishes
}

func main() {
  dishesChan := do_dishes()
  laundryChan := do_laundry()
  <-dishesChan
  <-laundryChan
}
```

Load dirty dishes into dishwasher

Load dirty laundry into washing machine

Washing machine cycle finishes

Load wet laundry into dryer

---

## Golang Example (Concurrency)

```go
package main

import (
  "fmt"
  "time"
)

func do_laundry() <-chan int {
  laundry := make(chan int)
  go func() {
    defer close(laundry)
    fmt.Println("Load dirty laundry into washing machine")
    time.Sleep(time.Second * 2)
    fmt.Println("Washing machine cycle finishes")
    fmt.Println("Load wet laundry into dryer")
    time.Sleep(time.Second * 4)
    fmt.Println("Dryer cycle finishes")
  }()
  return laundry
}

func do_dishes() <-chan int {
  dishes := make(chan int)
  go func() {
    defer close(dishes)
    fmt.Println("Load dirty dishes into dishwasher")
    time.Sleep(time.Second * 4)
    fmt.Println("Dishwasher cycle finishes")
  }()
  return dishes
}

func main() {
  dishesChan := do_dishes()
  laundryChan := do_laundry()
  <-dishesChan
  <-laundryChan
}
```

Load dirty dishes into dishwasher

Load dirty laundry into washing machine

Washing machine cycle finishes

Load wet laundry into dryer

Dishwasher cycle finishes

---

## Golang Example (Concurrency)

```go
package main

import (
  "fmt"
  "time"
)

func do_laundry() <-chan int {
  laundry := make(chan int)
  go func() {
    defer close(laundry)
    fmt.Println("Load dirty laundry into washing machine")
    time.Sleep(time.Second * 2)
    fmt.Println("Washing machine cycle finishes")
    fmt.Println("Load wet laundry into dryer")
    time.Sleep(time.Second * 4)
    fmt.Println("Dryer cycle finishes")
  }()
  return laundry
}

func do_dishes() <-chan int {
  dishes := make(chan int)
  go func() {
    defer close(dishes)
    fmt.Println("Load dirty dishes into dishwasher")
    time.Sleep(time.Second * 4)
    fmt.Println("Dishwasher cycle finishes")
  }()
  return dishes
}

func main() {
  dishesChan := do_dishes()
  laundryChan := do_laundry()
  <-dishesChan
  <-laundryChan
}
```

Load dirty dishes into dishwasher

Load dirty laundry into washing machine

Washing machine cycle finishes

Load wet laundry into dryer

Dishwasher cycle finishes

Dryer cycle finishes

---

## Golang example (Parallelism)

```go
package main

import (
  "fmt"
  "sync"
  "time"
)

func do_laundry() {
  fmt.Println("Load dirty laundry into washing machine")
  time.Sleep(time.Second * 2)
  fmt.Println("Washing machine cycle finishes")
  fmt.Println("Load wet laundry into dryer")
  time.Sleep(time.Second * 4)
  fmt.Println("Dryer cycle finishes")
}

func do_dishes() {
  fmt.Println("Load dirty dishes into dishwasher")
  time.Sleep(time.Second * 4)
  fmt.Println("Dishwasher cycle finishes")
}

func main() {
  var wg sync.WaitGroup
  wg.Add(2)
  go func() {
    defer wg.Done()
    do_dishes()
  }()
  go func() {
    defer wg.Done()
    do_laundry()
  }()
  wg.Wait()
}
```

---

## Golang example (Parallelism)

```go
package main

import (
  "fmt"
  "sync"
  "time"
)

func do_laundry() {
  fmt.Println("Load dirty laundry into washing machine")
  time.Sleep(time.Second * 2)
  fmt.Println("Washing machine cycle finishes")
  fmt.Println("Load wet laundry into dryer")
  time.Sleep(time.Second * 4)
  fmt.Println("Dryer cycle finishes")
}

func do_dishes() {
  fmt.Println("Load dirty dishes into dishwasher")
  time.Sleep(time.Second * 4)
  fmt.Println("Dishwasher cycle finishes")
}

func main() {
  var wg sync.WaitGroup
  wg.Add(2)
  go func() {
    defer wg.Done()
    do_dishes()
  }()
  go func() {
    defer wg.Done()
    do_laundry()
  }()
  wg.Wait()
}
```

Load dirty dishes into dishwasher

---

## Golang example (Parallelism)

```go
package main

import (
  "fmt"
  "sync"
  "time"
)

func do_laundry() {
  fmt.Println("Load dirty laundry into washing machine")
  time.Sleep(time.Second * 2)
  fmt.Println("Washing machine cycle finishes")
  fmt.Println("Load wet laundry into dryer")
  time.Sleep(time.Second * 4)
  fmt.Println("Dryer cycle finishes")
}

func do_dishes() {
  fmt.Println("Load dirty dishes into dishwasher")
  time.Sleep(time.Second * 4)
  fmt.Println("Dishwasher cycle finishes")
}

func main() {
  var wg sync.WaitGroup
  wg.Add(2)
  go func() {
    defer wg.Done()
    do_dishes()
  }()
  go func() {
    defer wg.Done()
    do_laundry()
  }()
  wg.Wait()
}
```

Load dirty dishes into dishwasher

Load dirty laundry into washing machine

---

## Golang example (Parallelism)

```go
package main

import (
  "fmt"
  "sync"
  "time"
)

func do_laundry() {
  fmt.Println("Load dirty laundry into washing machine")
  time.Sleep(time.Second * 2)
  fmt.Println("Washing machine cycle finishes")
  fmt.Println("Load wet laundry into dryer")
  time.Sleep(time.Second * 4)
  fmt.Println("Dryer cycle finishes")
}

func do_dishes() {
  fmt.Println("Load dirty dishes into dishwasher")
  time.Sleep(time.Second * 4)
  fmt.Println("Dishwasher cycle finishes")
}

func main() {
  var wg sync.WaitGroup
  wg.Add(2)
  go func() {
    defer wg.Done()
    do_dishes()
  }()
  go func() {
    defer wg.Done()
    do_laundry()
  }()
  wg.Wait()
}
```

Load dirty dishes into dishwasher

Load dirty laundry into washing machine

Washing machine cycle finishes

---

## Golang example (Parallelism)

```go
package main

import (
  "fmt"
  "sync"
  "time"
)

func do_laundry() {
  fmt.Println("Load dirty laundry into washing machine")
  time.Sleep(time.Second * 2)
  fmt.Println("Washing machine cycle finishes")
  fmt.Println("Load wet laundry into dryer")
  time.Sleep(time.Second * 4)
  fmt.Println("Dryer cycle finishes")
}

func do_dishes() {
  fmt.Println("Load dirty dishes into dishwasher")
  time.Sleep(time.Second * 4)
  fmt.Println("Dishwasher cycle finishes")
}

func main() {
  var wg sync.WaitGroup
  wg.Add(2)
  go func() {
    defer wg.Done()
    do_dishes()
  }()
  go func() {
    defer wg.Done()
    do_laundry()
  }()
  wg.Wait()
}
```

Load dirty dishes into dishwasher

Load dirty laundry into washing machine

Washing machine cycle finishes

Load wet laundry into dryer

---

## Golang example (Parallelism)

```go
package main

import (
  "fmt"
  "sync"
  "time"
)

func do_laundry() {
  fmt.Println("Load dirty laundry into washing machine")
  time.Sleep(time.Second * 2)
  fmt.Println("Washing machine cycle finishes")
  fmt.Println("Load wet laundry into dryer")
  time.Sleep(time.Second * 4)
  fmt.Println("Dryer cycle finishes")
}

func do_dishes() {
  fmt.Println("Load dirty dishes into dishwasher")
  time.Sleep(time.Second * 4)
  fmt.Println("Dishwasher cycle finishes")
}

func main() {
  var wg sync.WaitGroup
  wg.Add(2)
  go func() {
    defer wg.Done()
    do_dishes()
  }()
  go func() {
    defer wg.Done()
    do_laundry()
  }()
  wg.Wait()
}
```

Load dirty dishes into dishwasher

Load dirty laundry into washing machine

Washing machine cycle finishes

Load wet laundry into dryer

Dishwasher cycle finishes

---

## Golang example (Parallelism)

```go
package main

import (
  "fmt"
  "sync"
  "time"
)

func do_laundry() {
  fmt.Println("Load dirty laundry into washing machine")
  time.Sleep(time.Second * 2)
  fmt.Println("Washing machine cycle finishes")
  fmt.Println("Load wet laundry into dryer")
  time.Sleep(time.Second * 4)
  fmt.Println("Dryer cycle finishes")
}

func do_dishes() {
  fmt.Println("Load dirty dishes into dishwasher")
  time.Sleep(time.Second * 4)
  fmt.Println("Dishwasher cycle finishes")
}

func main() {
  var wg sync.WaitGroup
  wg.Add(2)
  go func() {
    defer wg.Done()
    do_dishes()
  }()
  go func() {
    defer wg.Done()
    do_laundry()
  }()
  wg.Wait()
}
```

Load dirty dishes into dishwasher

Load dirty laundry into washing machine

Washing machine cycle finishes

Load wet laundry into dryer

Dishwasher cycle finishes

Dryer cycle finishes

---

## Quote of the Day

> Concurrency is about dealing with a lot of tasks at once.
> Parallelism is about doing a lot of tasks at once.

---

## Q&A

```rust
fn main() {
  println!("Thanks for listening! Any questions?")
}
```
