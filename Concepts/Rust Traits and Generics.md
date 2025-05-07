---
tags:
  - rust
---
- **Substep 1: Traits (Defining Shared Behavior)**
    
    - Traits are like interfaces in other languages.
    - They define a set of methods that a type must implement.
    - Traits enable code reuse and polymorphism.

```Rust
trait Shape {
    fn area(&self) -> f64;
}

struct Circle {
    radius: f64,
}

impl Shape for Circle {
    fn area(&self) -> f64 {
        std::f64::consts::PI * self.radius * self.radius
    }
}

struct Rectangle {
    width: f64,
    height: f64,
}

impl Shape for Rectangle {
    fn area(&self) -> f64 {
        self.width * self.height
    }
}

fn main() {
    let circle = Circle { radius: 5.0 };
    let rectangle = Rectangle {
        width: 4.0,
        height: 6.0,
    };

    println!("Circle area: {}", circle.area());
    println!("Rectangle area: {}", rectangle.area());
}
```

In this example:
- `trait Shape` defines a trait with an `area` method.
- `impl Shape for Circle` and `impl Shape for Rectangle` implement the trait for the `Circle` and `Rectangle` structs.
- Traits allow us to write generic code that works with different types.

Traits are a powerful feature in Rust that promotes code reusability and flexibility.

- **Substep 2: Generics (Writing Reusable Code)**
    
    - Generics allow you to write code that works with multiple types.
    - They prevent code duplication and increase flexibility.
    - Generics are defined using angle brackets `<T>`.

```Rust
fn largest<T: PartialOrd + Copy>(list: &[T]) -> T {
    let mut largest = list[0];

    for &item in list.iter() {
        if item > largest {
            largest = item;
        }
    }

    largest
}

fn main() {
    let numbers = vec![34, 50, 25, 100, 65];
    let result = largest(&numbers);
    println!("The largest number is: {}", result);

    let chars = vec!['y', 'm', 'a', 'q'];
    let result = largest(&chars);
    println!("The largest char is: {}", result);
}
```

In this example:
- `fn largest<T: PartialOrd + Copy>(list: &[T]) -> T` defines a generic function that finds the largest element in a list.
- `T: PartialOrd + Copy` specifies that the type `T` must implement the `PartialOrd` and `Copy` traits.
- Generics allow us to use the same function for different types.

Generics are a powerful tool for writing flexible and reusable code in Rust.

```Rust
trait Summary {
    fn summarize(&self) -> String;
}

struct NewsArticle {}

struct Tweet {}

impl Summary for NewsArticle {
    fn summarize(&self) -> String {
        return String::from("NewsArticle");
    }
}

impl Summary for Tweet {
    fn summarize(&self) -> String {
        return String::from("Tweet");
    }
}

fn notify<T: Summary>(item: &T) {
    println!("Notifying: {}", item.summarize());
}

fn main() {
    let article = NewsArticle {};
    let tweet = Tweet {};
    notify(&article);
    notify(&tweet);
    let article_summary = article.summarize();
    let tweet_summary = tweet.summarize();
    println!("Article Summary: {}", article_summary);
    println!("Tweet Summary: {}", tweet_summary);
}
```

**Key improvements:**
- Added `&self` to the `summarize` method signature.
- Modified the `notify` function to take a parameter of type `T: Summary`.
- Corrected the call to `item.summarize()` in the `notify` function.