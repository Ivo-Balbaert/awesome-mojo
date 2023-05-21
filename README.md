# Awesome Mojo🔥

![Mojo](img/mojo.png)

Mojo 🔥 — a new programming language for all developers, AI/ML scientists and software engineers.

A curated list of awesome Mojo🔥 code, problem-solving, solution, and in future libraries, frameworks, software and
resources.

Let's accumulate here very new technology knowledge and best practices.

* [Awesome Mojo🔥](https://github.com/ego/awesome-mojo)
* [Mojo 🔥Driven Community](https://mojo-lang.dev)
* [Official Mojo docs](https://docs.modular.com/mojo/)

Mojo is a programming language that combines the user-friendliness of Python with the performance capabilities of C++
and Rust. Additionally, Mojo enables users to harness the vast ecosystem of Python libraries.

In a brief

* Mojo allows you to leverage the entire Python ecosystem.
* Mojo is designed to become a superset of Python.
* Make Mojo compatible with existing Python programs.
* Mojo as a member of the Python family.
* Applied for AI systems and AI field.
* Scalable programming for heterogeneous systems.
* Building unify the world’s ML/AI infrastructure.
* Innovations in compiler internals.
* Support for current and emerging hardware accelerators.
* Systems programming features.
* Leverage the existing MLIR compiler ecosystem.

# Hello Mojo🔥

Mojo is a new programming language that bridges the gap between research and production by combining the best of Python
syntax with systems programming and metaprogramming.

`hello.mojo` or `hello.🔥` the file extension can be an emoji!

You can read more about why Modular doing this [Why Mojo🔥](https://docs.modular.com/mojo/why-mojo.html)

> What we wanted was an innovative and scalable programming model that could target accelerators and other heterogeneous
> systems that are pervasive in the AI field.
> ...
> Applied AI systems need to address all these issues, and we decided there was no reason it couldn’t be done with just
> one language. Thus, Mojo was born.

But Python has done its job very well =)

> We didn’t see any need to innovate in language syntax or community.
> So we chose to embrace the Python ecosystem because it is so widely used, it is loved by the AI ecosystem, and because
> we believe it is a really nice language.

Who knows these programming languages will be very happy, because Mojo benefits from tremendous lessons learned from
other languages Rust, Swift, Julia, Zig, Nim, etc.

* Rust starts the C revolution and now [Rust in the Linux kernel](https://docs.kernel.org/rust/index.html).
* [Swift](https://www.swift.org) makes [Apple beautiful](https://developer.apple.com/swift/) from a technical
  perspective.
* [Julia](https://julialang.org) high performance.
* [Nim](https://nim-lang.org) systems programming language.
* [Zig](https://ziglang.org) general-purpose programming language. We are like and following it =)

![Mojo](img/speed.png)

# Contributing

* Your contributions are always welcome!
* If you have any **question**, do not hesitate to contact me.
* If you would like to participate in the initiative [Mojo 🔥Driven Community](https://mojo-lang.dev), please contact me.

# Programming manual

## Comments

## Symbol visibility

## Variables

## let and var declarations

### Mutable variables

## Mojo types

### Primitive types

### Int vs int

### Int, Float, SIMD

### Bool

### Strings

### Runes

### Numbers

### Arrays

### Maps

### struct types

### Pointer

## Value lifecycle

### @value decorator

## Overloaded functions and methods

## Special methods

### __init__

### __del__

### __moveinit__

### __copyinit__

### __iadd__

### raises

## Argument passing control and memory ownership

### self

### Immutable arguments (borrowed)

### Mutable arguments (inout)

### Transfer arguments (owned and ^)

## Functions

### def definitions

### fn definitions

### Comparing def and fn argument passing

## Parameterization: compile-time metaprogramming

### Defining parameterized types and functions

### Powerful compile-time programming (@parameter)

### alias: named parameter expressions

## Value Lifecycle

### Non-movable and non-copyable types

### Unique “move-only” types

## Asynchronous Programming

## Common with Python

## Different with Python

## List of keywords

## List of builtin function

### strdup

# Mojo notebooks

# Mojo library

## Builtin (Builtin)

## Standard library (Stdlib)

## Python interop (Python)

### Python integration

### Mojo types in Python

# Awesome Mojo🔥 code

## Binary Search Algorithm

In computer science, [binary search algorithm](https://en.wikipedia.org/wiki/Binary_search_algorithm), also known as
half-interval search, logarithmic search, or binary chop, is a search algorithm that finds the position of a target
value within a sorted array.

Let's do some code with Python, Mojo🔥, Swift, V, Julia, Nim, Zig.

Note:
For **Python** and **Mojo** versions,
I leave some optimization and make the code similar for measurement and comparison.

* [Python Binary Search](algorithm/binary_search_Python.py)

```python
from typing import List
import timeit

SIZE = 1000000
MAX_ITERS = 100
COLLECTION = tuple(i for i in range(SIZE))  # Make it aka at compile-time.


def python_binary_search(element: int, array: List[int]) -> int:
    start = 0
    stop = len(array) - 1
    while start <= stop:
        index = (start + stop) // 2
        pivot = array[index]
        if pivot == element:
            return index
        elif pivot > element:
            stop = index - 1
        elif pivot < element:
            start = index + 1
    return -1


def test_python_binary_search():
    _ = python_binary_search(SIZE - 1, COLLECTION)


print(
    "Average execution time of func in sec",
    timeit.timeit(lambda: test_python_binary_search(), number=MAX_ITERS),
)
```

* [Mojo🔥 Binary Search](algorithm/BinarySearch_Mojo.mojo)

```python
"""Implements basic binary search."""

from Benchmark import Benchmark
from Vector import DynamicVector


alias SIZE = 1000000
alias NUM_WARMUP = 0
alias MAX_ITERS = 100


fn mojo_binary_search(element: Int, array: DynamicVector[Int]) -> Int:
    var start = 0
    var stop = len(array) - 1
    while start <= stop:
        let index = (start + stop) // 2
        let pivot = array[index]
        if pivot == element:
            return index
        elif pivot > element:
            stop = index - 1
        elif pivot < element:
            start = index + 1
    return -1


@parameter  # statement runs at compile-time.
fn get_collection() -> DynamicVector[Int]:
    var v = DynamicVector[Int](SIZE)
    for i in range(SIZE):
        v.push_back(i)
    return v


fn test_mojo_binary_search() -> F64:
    fn test_closure():
        _ = mojo_binary_search(SIZE - 1, get_collection())
    return F64(Benchmark(NUM_WARMUP, MAX_ITERS).run[test_closure]()) / 1e9


print(
    "Average execution time of func in sec ",
    test_mojo_binary_search(),
)
```

* [Swift Binary Search](algorithm/binarySearch_Swift.swift)

```swift
func binarySearch(items: [Int], elem: Int) -> Int {
    var low = 0
    var high = items.count - 1
    var mid = 0
    while low <= high {
        mid = Int((high + low) / 2)
        if items[mid] < elem {
            low = mid + 1
        } else if items[mid] > elem {
            high = mid - 1
        } else {
            return mid
        }
    }
    return -1
}

let items = [1, 2, 3, 4, 0].sorted()
let res = binarySearch(items: items, elem: 4)
print(res)
```

* [Julia Binary Search](algorithm/binarysearch_Julia.jl)

```julia
function binarysearch(lst::Vector{T}, val::T) where T
    low = 1
    high = length(lst)
    while low ≤ high
        mid = (low + high) ÷ 2
        if lst[mid] > val
            high = mid - 1
        elseif lst[mid] < val
            low = mid + 1
        else
            return mid
        end
    end
    return 0
end
```

* [Nim Binary Search](algorithm/binarySearch_Nim.nim)

```nim
proc binarySearch[T](a: openArray[T], key: T): int =
  var b = len(a)
  while result < b:
    var mid = (result + b) div 2
    if a[mid] < key: result = mid + 1
    else: b = mid
  if result >= len(a) or a[result] != key: result = -1


let res = @[2,3,4,5,6,7,8,9,10,12,14,16,18,20,22,25,27,30]
echo binarySearch(res, 10)
```

* [Zig Binary Search](algorithm/BinarySearch_Zig.zig)

```zig
const std = @import("std");

fn binarySearch(comptime T: type, arr: []const T, target: T) ?usize {
    var lo: usize = 0;
    var hi: usize = arr.len - 1;

    while (lo <= hi) {
        var mid: usize = (lo + hi) / 2;

        if (arr[mid] == target) {
            return mid;
        } else if (arr[mid] < target) {
            lo = mid + 1;
        } else {
            hi = mid - 1;
        }
    }

    return null;
}
```

* [V Binary Search](algorithm/binary_search_V.v)

```v
fn binary_search(a []int, value int) int {
	mut low := 0
	mut high := a.len - 1
	for low <= high {
		mid := (low + high) / 2
		if a[mid] > value {
			high = mid - 1
		} else if a[mid] < value {
			low = mid + 1
		} else {
			return mid
		}
	}
	return -1
}

fn main() {
	search_list := [1, 2, 3, 5, 6, 7, 8, 9, 10]
	println(binary_search(search_list, 9))
}
```

* [Bonus V Breadth First Search Path](algorithm/bfs_V.v)
    * [BFS at vlang examples](https://github.com/vlang/v/blob/master/examples/graphs/bfs.v)
    * [BFS original PR](https://github.com/ego/v/blob/e13474757bee0afa00e8c4dd013b14e2f4fbc428/examples/bfs.v)

```v
fn breadth_first_search_path(graph map[string][]string, vertex string, target string) []string {
	mut path := []string{}
	mut visited := []string{init: vertex}
	mut queue := [][][]string{}
	queue << [[vertex], path]
	for queue.len > 0 {
		mut idx := queue.len - 1
		node := queue[idx][0][0]
		path = queue[idx][1]
		queue.delete(idx)
		if node == target {
			path << node
			return path
		}
		for child in graph[node] {
			mut tmp := path.clone()
			if child !in visited {
				visited << child
				tmp << node
				queue << [[child], tmp]
			}
		}
	}
	return path
}

fn main() {
	graph := map{
		'A': ['B', 'C']
		'B': ['A', 'D', 'E']
		'C': ['A', 'F']
		'D': ['B']
		'E': ['B', 'F']
		'F': ['C', 'E']
	}
	println('Graph: $graph')
	path := breadth_first_search_path(graph, 'A', 'F')
	println('The shortest path from node A to node F is: $path')
	assert path == ['A', 'C', 'F']
}
```

# The Zen of Mojo🔥

# Additional materials

* [The Golden Age of Compiler Design in an Era of HW/SW Co-design by Dr. Chris Lattner](https://youtu.be/4HgShra-KnY)
* [LLVM in 100 Seconds](https://youtu.be/BT2Cv-Tjq7Q)
* [Mojo Dojo](https://mojodojo.dev/mojo_team_answers.html)
* [Mojo Cheatsheet](https://github.com/czheo/mojo-cheatsheet/tree/main)
* [Counting chars with SIMD in Mojo](https://mzaks.medium.com/counting-chars-with-simd-in-mojo-140ee730bd4d)
