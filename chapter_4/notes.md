## Ownership

All program shave to manage the way they use a computer's memory while running. Instead of constant garbage collection or manual garbage collection, Rust manages memory through ownership with a set of rules the compiler checks at compile time (which prevents this from slowing down your program).

### Stack vs. Heap

Data stored on the stack is stored in a LIFO structure. You can push/pop data. The data must have a known, fixed size. Data stored to the heap includes requesting a certain amount of space and an allocator finds an empty spot that fits. Data is accessed on the heap with pointers.

Parameters passed into a function are pushed onto the stack - then when the function has completed they get popped off the stack. Mimimizing the amount of data on the heap and cleaning up unused data on the heap is addressed with ownership in Rust.

### Ownership Rules

There are three key rules to Rust Ownership:

1. Each value in Rust has a variable that’s called its owner.
1. There can only be one owner at a time.
1. When the owner goes out of scope, the value will be dropped.

Scope is one of the main ways to keep track of when ownership exists.

### Ownership Pt. 2

The `String` type exists to extend string literals and allow them to be extended. You can turn a string literal into a string by running `String::from({literal})`. Literal types cannot be mutated because of how they deal with memory. Complex data types are stored on the heap, whereas literals are able to be stored on the stack.

In Rust, memory is automatically returned once the variable that owns it goes out of scope.

Literal types actually copy data, whereas complex types copy references. Complex data types have three pars - a pointer, a size, and a capacity. When you assign a variable of a complex type to a new variable - you re-use the same reference. However, when deallocating data, there are two variables - which would result in two attempts to deallocate the complex type. This would result in a failure because the variable cannot be deallocated twice.

To deal with this - Rust considers copy-by-reference to be a `move`. So then the original passes out of scope and will not be deallocated when the enclosing scope ends. Rust will never automatically create a "deep" copy.

If you _do_ want a deep copy of a variable, Rust provides a method called `clone`. You don't need to call `clone` on literal types, but on custom types, you can implement a `Copy` trait to allow a variable to be copied. However, if you also have a `Drop` trait you will get a compile-time error.

### Functions

When dealing with complex data types - passing a variable into a function that would normally be passed by reference leads to the variable being out of scope after it's been passed. Effectively function calls with pass by reference prevent you from using the variable in the parent scope. This prevents accidentally modifying shared memory.

Returning values can also transfer ownership from an inner scope to an outer scope.

### References & Borrowing

Similar to C++, we can use an `&` to pass a reference of a value. This is the location in memory where the variable is stored. The opposite is the dereferencing operator `*`.

You cannot mutate references by default. However, you can pass in mutable references by passing `&mut var` instead of just `&var`. However, you can only have one mutable reference at a time. This is to prevent _data races_ which happen when two or more pointers access the same data at the same time and at least one of them is used to write data and nothing is used to synchronize them.

So you cannot have multiple mutable references and you cannot combine mutable and immutable references.

Rust can also guarantee that there will _never be any dangling references_. As a result, you cannot return a reference when the value will get dropped out of scope.

### Slices

Slices are another data type that does not have ownership. You can use them to reference contiguous sequences of elements in a collection. You can access a string slice through `&s[start_index..end_index]`.

You must use indices at valid UTF-8 character boundaries.

String literals are slices. You can also do slices of arrays of values.
