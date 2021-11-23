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
