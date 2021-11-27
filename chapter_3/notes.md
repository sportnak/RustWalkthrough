# Common Programming Concepts

## Reserved Keywords

Rust has some keywords that are reserved even though they have no use yet. Interesting.

## Variables and Mutability

By default variables are immutable

- Compiler time checks of immutability reduces bugs and improves the debugging process

Constants are always immutable and the type must be annotated.

- convention is to use all uppercase with underscores
- valid for entire time program runs within the scope they were declared in

Shadowing variables allows you to use the same variable name as in an upper scope.

- Requires use of the `let` keyword
- the value is reset when the scope is exited
- allows you to change the type
- keeps the variable immutable after the fact vs. using `mut`

## Data Types

Rust is statically typed. Types can be inferred, but some methods return multiple possible types, so you must annotate the type.

Four scalar types: integers, floating-point numbers, booleans, and characters.

You can cause an integer overflow - but Rust will catch it and create a panic at runtime when compiling in debug mode. However, in release mode, Rust will instead wrap the value around back to the minimum

Default floats are 64 bit because they are roughly the same speed as f32.

### Compound Types

Compound types allow you to group multiple values into one type. You can do this through tuples and arrays.

Tuples:

- fixed length
- each position can have a unique type
- extract values through destructuring or through `.{index}`
- accessing values by index out of range fails to compile
- empty tuple `()` is the default return type of functions

Arrays:

- fixed length
- all elements must have same type
- allocates data to the stack rather than the heap
- not as flexible as the `vector` type
- annotated as `[{type}; length]` or `[{value}; length]`
- runtime indexing is checked

## Functions

- snake_case is the conventional style for functions and variable names

Functions are started with `fn` . Rust doesn't care about the order in which functions are defined.

Rust functions optionally end in an expression.
Statements:

- instructions that perform an action and do not return a value.

Expressions:

- evaluate to a resulting value.
- Do not include ending semicolons

## Iterations

You can do a `loop`, `for` or `while` statements. You can name loops so that when they are nested you can control them with `continue` and `break` statements.

### Loops

`loop`s can return values with the `break` statements.

### For Loops

You can use an `in` operator to iterate the elements of an array. You can also do `(x..y)` to create a range.
