---
tags:
  - rust
---
**Substep 1: Concurrency (Threads)**
- Concurrency allows multiple tasks to run seemingly simultaneously.
- Threads are a common way to achieve concurrency.
- Rust's ownership and borrowing system helps prevent data races.

```Rust
use std::thread;

fn main() {
    let handle = thread::spawn(|| {
        for i in 1..10 {
            println!("hi number {} from the spawned thread!", i);
            thread::sleep(std::time::Duration::from_millis(1));
        }
    });

    for i in 1..5 {
        println!("hi number {} from the main thread!", i);
        thread::sleep(std::time::Duration::from_millis(1));
    }

    handle.join().unwrap();
}
```

In this example:
- `thread::spawn` creates a new thread.
- `handle.join().unwrap()` waits for the spawned thread to finish.
- Rust's ownership system ensures safe concurrent access to data.
- The `||` syntax in `thread::spawn(|| { ... })` represents a closure in Rust.

Concurrency is essential for building high-performance applications that can take advantage of multiple CPU cores.