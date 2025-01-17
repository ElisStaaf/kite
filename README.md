Kite Programming Language
=========================

Kite is a pure and minimalistic programming language written in C.
It can be a lot, but if I'd *have* to classify it, it's a functional
programming language with imperative elements. This is a sample of what
code written in Kite might look like:

```coffeescript
let loop = fun(func, times, until)
    if times < until do @(func, times + 1, until)
    else func

let incr = fun(num)
    num + 1

let mainloop = fun(k, j, i)
    loop(incr(k), j, i)

loop(mainloop(1, 5, 25), 0, 10)
```

Simple program to print the number "100":

```coffeescript
# To print without newline:
write(tostring(100)
# or
import io
io.print(100)

# To print with a newline:
writeln(tostring(100))
# or
import io
io.println(100)
```

It also includes functions:

```coffeescript
let println = fun(v)
    writeln(tostring(v)

let sum = fun(x)
    if x < 2 do x
    else x + sum(x - 1)

println(sum(3))
```

This does the same thing as the last example:

```coffeescript
let println = fun(v)
    writeln(tostring(v))

println((fun(x) if x < 2 do x else x + @(x - 1))(3))
```

Oh, almost forgot about Modules:

```coffeescript
import io
io.print(10)
io.println(20)
io.print(30)
```

stdlib/io.kite:

```coffeescript
let export print = fun(val)
    write(tostring(val))
let export println = fun(val)
    writeln(tostring(val))
```

Another module; func:

```coffeescript
import func

let test = fun()
    writeln(tostring(100))

func.loop(test(), 0, 10)
```

stdlib/func.kite:

```coffeescript
let export loop = fun(func, times, until)
    if times < until do @(func, times + 1, until)
    else func
```

Another one; math:

```coffeescript
import math

writeln(tostring(math.facto(5)))
writeln(tostring(math.fib(10)))
```

stdlib/math.kite:

```coffeescript
let facto = fun(n)
    if n == 1 do n
    else n * @(n - 1)

let fib = fun(x)
	if x < 2 do 1
	else @(x - 1) + @(x - 2)
```

All modules should be located in ./lib/. This means that you
can create your own Kite project, and you can import other files
by putting all libraries in ./lib/.

Requirements
------------
* https://gcc.gnu.org/install
* https://www.gnu.org/software/make
* https://git-scm.com/downloads or https://github.com/cli/cli#installation

Installation
------------
To install, firstly clone the repo:

```sh
# git
git clone https://github.com/ElisStaaf/kite

# gh
gh repo clone ElisStaaf/kite
```

Then build an executable using make:

```sh
cd kite
sudo make
```