---
tags:
  - rust
---
- **Substep 1: Error Handling (Result and Option)**
    - Rust emphasizes robust error handling.
    - The `Result` enum represents either success (`Ok`) or failure (`Err`).
    - The `Option` enum represents either a value (`Some`) or no value (`None`).

```Rust
fn divide(x: f64, y: f64) -> Result<f64, String> {
    if y == 0.0 {
        return Err(String::from("Cannot divide by zero"));
    }
    Ok(x / y)
}

fn main() {
    match divide(10.0, 2.0) {
        Ok(result) => println!("Result: {}", result),
        Err(error) => println!("Error: {}", error),
    }

    match divide(5.0, 0.0) {
        Ok(result) => println!("Result: {}", result),
        Err(error) => println!("Error: {}", error),
    }
}
```

In this example:

- The `divide` function returns a `Result`.
- The `match` expression handles both `Ok` and `Err` cases.
- Rust's error handling helps prevent unexpected program crashes.

- **Substep 2: Modules (Organizing Code)**
    - Modules help organize code into logical units.
    - They promote code reusability and maintainability.
    - `mod` keyword is used to define modules.
    - `pub` keyword is used to make items public.
    - Modules help manage namespaces and prevent naming conflicts.

```Rust
mod math {
    pub fn add(x: i32, y: i32) -> i32 {
        x + y
    }

    pub fn subtract(x: i32, y: i32) -> i32 {
        x - y
    }
}

fn main() {
    println!("Add: {}", math::add(5, 3));
    println!("Subtract: {}", math::subtract(10, 4));
}
```

In this example:
- `mod math` defines a module named `math`.
- `pub fn add` and `pub fn subtract` define public functions within the module.
- `math::add` and `math::subtract` are used to call the functions.

