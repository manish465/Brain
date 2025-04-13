---
tags:
  - rust
---
- **Substep 1: Basic Syntax and Structure**
    
    - Every Rust program starts with a `main` function.
    - Rust uses curly braces `{}` to define blocks of code.
    - `println!` is used for printing output to the console.
    - Variables are declared using the `let` keyword.
    - Rust is statically typed, meaning the compiler must know the type of every variable at compile time.

```Rust
fn main() {
    println!("Hello, World!");
    let x = 5;
    println!("The value of x is: {}", x);
}
```

```Rust
fn main() {
    let a = 10;
    let b = 20;
    let sum = a + b; // Your code here
    println!("The sum of a and b is: {}", sum);
}
```