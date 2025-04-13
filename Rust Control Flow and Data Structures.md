---
tags:
  - rust
---
- **Substep 1: Control Flow (if, else, loops)**
    - Control flow allows you to dictate the order in which your code executes.
    - `if` and `else` statements let you conditionally execute blocks of code.
    - `for` and `while` loops enable you to repeat code blocks.

```Rust
fn main() {
    let number = 7;

    if number < 5 {
        println!("condition was true");
    } else {
        println!("condition was false");
    }

    for i in 1..5 {
        println!("The number is: {}", i);
    }
}
```

```Rust
fn main() {
    let age = 20; // You can change this age to test your code

    if age >= 18 {
        println!("You are eligible to vote");
    } else {
        println!("You are not eligible to vote");
    }
}
```


- **Substep 2: Data Structures (Vectors, Strings, Hash Maps)**
    - Data structures are ways to organize and store data.
    - Vectors (`Vec`) are like resizable arrays.
    - Strings (`String`) are used for text.s
    - Hash maps (`HashMap`) store key-value pairs.

```Rust
use std::collections::HashMap;

fn main() {
    // Vectors
    let mut numbers: Vec<i32> = vec![1, 2, 3];
    numbers.push(4);
    println!("Numbers: {:?}", numbers);

    // Strings
    let greeting: String = String::from("Hello, Rust!");
    println!("Greeting: {}", greeting);

    // Hash Maps
    let mut scores: HashMap<String, i32> = HashMap::new();
    scores.insert(String::from("Blue"), 10);
    scores.insert(String::from("Yellow"), 50);
    println!("Scores: {:?}", scores);
}
```

- `Vec<i32>` creates a vector of integers.
- `String::from()` creates a string.
- `HashMap<String, i32>` creates a hash map with string keys and integer values.

```Rust
use std::collections::HashMap;

fn main() {
    let mut fruits: Vec<String> = vec![
        String::from("apple"),
        String::from("banana"),
        String::from("cherry"),
    ];
    fruits.push(String::from("orange"));

    let mut fruit_colors: HashMap<String, String> = HashMap::new();
    fruit_colors.insert(String::from("apple"), String::from("red"));
    fruit_colors.insert(String::from("banana"), String::from("yellow"));
    fruit_colors.insert(String::from("cherry"), String::from("red"));
    fruit_colors.insert(String::from("orange"), String::from("orange"));

    println!("Fruits: {:?}", fruits);
    println!("Fruit Colors: {:?}", fruit_colors);
}
```