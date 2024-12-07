# A Template for Learning Rust

# Hello World Tutorial:

Watch this video for a quick tutorial on how to create a Rust project, write a basic Rust closure, and run it: [link](https://www.youtube.com/watch?v=gtXUPOZ7_mA)

# Entry Point

---

### What is an entry point in Rust?

- The entry point is where the execution of a Rust program starts.
- The entry point in a Rust program is the main function, defined with the keyword **fn main()**, in which 'fn' stands for for function, while 'main' is the name of the function.


---

### Example:

```Rust
fn main() {
  println!("Hello, world!");
}
```

# Data Types in Rust

- Every value in Rust is of a certain data type, which tells Rust what kind of data is being specified so it knows how to work with that data. We’ll look at two data type subsets: scalar and compound.
- Note: Rust is a statically typed language, which means that it must know the types of all the variables at compile time.

### Scalar Types:
A scalar type represents a single value. Rust has four primary scalar types:

- **Integer Types:**: 
  -  Represents integer, number without fractional component. 
  - Rust defaults integer types to **i32**. Some other Signed Integer Types are i8, i16, i64, i128, isize.
  - Unsigned Integer Types are u8, u16, u32, u64, u128, and usize.
  - Example:
    ```Rust
    fn main() {
      let age: i32 = 25;
    }
    ```
- **Floating-Point Types:** 
  - Represents number with decimal points. 
  - Rust's floating-point types are **f32** and **f64**, which are 32 bits and 64 bits in size. The default type is **f64**.
  - Example:
    ```Rust
    fn main() {
      let x = 2.0; // f64
      let y: f32 = 3.0; // f32
    }
- **The Boolean Type:**
  - Has two possible value: True and False.
  - Booleans are one byte in size.
  - The main way to use Boolean values is through conditionals, such as an **if** expression.
  - Keyword: bool
  - Example:
  ```Rust
  fn main() {
    let t = true;
    let f: bool = false; // with explicit type annotation.
  }
  ```
- **The Character Type:**
  - The language's most primitive alphabetic type.
  - Specified with single quotes.
  - Example:
  ```Rust
  fn main() {
    let c = 'z';
    let z: char = 'Z'; // with explicit type annotation
    let
  }

### Compound Types:
Compound types can group multiple values into one type. Rust has two primitive compound types: **tuples** and **arrays**.

- **The Tuple Type:**
  - A tuple is a general way of grouping together a number of values with variety of types into one compound type.
  - Tuples have a fixed length: once declared, they cannot be modified to grow or shrink in size.
  - Example:
  ```Rust
  fn main() {
    let tup: (i32, f64, u8) = (500, 6.4, 1);

    let (x, y, z) = tup;

    println!("The value of y is {y}");
  }
  ```
- **The Array Type:**
  - An array is another way to have a collection of multiple values.
  - Unlike a tuple, every element of an array must have the **same type**.
  - Unlike arrays in some other languages, **arrays in Rust have a fixed length**.
  - Example:
  ```Rust
  fn main() {
    let numbers = [1, 2, 3, 4, 5];
    let months = ["January", "February", "March", "April", "May", "June", "July",
              "August", "September", "October", "November", "December"];
    let january = months[0];
    let may = months[4];
    let december = months[11];
  }
  ```
  You can also write an array's type using square brackets with the type of each element, a semicolon, and then the number of elements in the array:
  ```Rust
  let numbers: [i32; 5] = [1, 2, 3, 4, 5];
  ```

### Numeric Operations:
Rust supports the basic mathematical operations for all number types: addition, subtraction, multiplication, division, and remainder. Integer division truncates toward zero to the nearest integer. Example:
```rust
fn main() {
  // addition
  let sum = 15 + 10;

  // subtraction
  let difference = 95.9 - 4.2;

  // multiplication
  let product = 4 * 3;

  // division
  let quotient = 52.3 / 32.2;
  let truncated = -5 / 3 // Result in -1

  // remainder (module)
  let remainder = 43 % 5;
}
```

# Standard Data Structures

## Arrays
- Use for storing a fixed number of elements of the same type. Already covered above.

## Vectors
- Use for a collection that needs dynamic resizing, since the number of elements in List can be extended.
```Rust
let mut numbers = vec![10, 20, 30];
numbers.push(40);
println!("{}", numbers[2]); // Output: 30
```

## HashMaps
- Use for key-value pairs. Example: mapping student names to their GPAs.
```Rust
use std::collections::HashMap;

let mut student_grades = HashMap::new();
student_grades.insert("Alice", 90);
student_grades.insert("Bob", 85);

println!("{}", student_grades["Alice"]); // Output: 90
```
# Custom Data Types

## Structs
- Use for grouping related data into a single type.
```Rust
struct Point {
  x: i32,
  y: i32,
}

let p = Point {x : 3, y : 5};
println!("X: {}, Y: {}", p.x, p.y); // Output: X: 3, Y: 5
```

## Enums
- Use for representing one of several possible types:
```Rust
enum Direction {
  North,
  South,
  East,
  West,
}
```

## Tuples
- Use for grouping a small number of elements (can be of different types). Already covered above.

# Control Structures

### if Expressions
- An **if** expression allows you to branch your code depending on conditions. 
- By using the **if** expression, you basically provide a condition and state, "if this condition is met, run this block of code."
- Optionally, you can also include an **else** expression to give the program an alternate block of code to execute when the condition evaluate to **false**.
- You can also provide an **else if** expression to give an extra **if** statement when the first **if** statement evaluate to **false**.
Example:
```Rust
fn main() {
  let number = 6;
  
  if number % 4 == 0 {
        println!("number is divisible by 4");
    } else if number % 3 == 0 {
        println!("number is divisible by 3");
    } else if number % 2 == 0 {
        println!("number is divisible by 2");
    } else {
        println!("number is not divisible by 4, 3, or 2");
    }
}
```
You can use if in a **let** statement:
```bash
fn main() {
  let condition = true;
  let number = if condition { 5 } else { 6 };

  println!("The value of number is: {number}");
}
```

### Loops:
- **Loops** are often useful to execute a block of code more than once.
- Rust has three kinds of loops: **loop**, **while**, and **for**.

#### Repetition with loop:
- The **loop** keyword tells Rust to execute a block of code over and over again forever or until you explicitly tell it to stop
- Example:
```Rust
fn main() {
  loop {
    println!("again!");
  }
}
```
Returning Values from Loop:
```Rust
fn main() {
  let mut counter = 0;

  let result = loop {
    counter += 1;

    if counter == 10 {
      break counter * 2;
    }
  };
    println!("The result is {result}");
}
```
The code above declares a mutable integer **counter** as zero. Then it declares a variable named **result** to hold the value returned from the loop. On every iteration of the loop, we add 1 to the **counter** variable, and then check whether **counter** is equal to 10. When it is, we use the **break** keyword with the value **counter * 2**. After the loop, we use a semicolon to end the statement that assigns the value to result. Finally, we print the value in result, which in this case is 20.

#### Conditional Loops with while:
- Provides a structure that runs the code loop while the condition is **true**.
- When the condition is **true**, the program calls **break**, stopping the loop.
- Example:
```Rust
fn main() {
  let mut number = 5;

  while number != 0 {
        println!("{number}!");
        number -= 1;
  }

  println!("Loop finished.");
}
```

#### Looping Through a Collection with for:
- A for loop is used to iterate through a collection and execute some code for each item in that collection.
- Example:
```Rust
fn main() {
  let a = [10, 20, 30, 40, 50];

  for element in a {
    println!("the value is: {element}");
  }
}
```

# Functions
- Functions are prevalent in Rust code. Throughout this tutorial, we have seen one of the most important functions in the language: **main**.
- Defined with the **fn** keyword
- Rust code uses *snake case* as the conventional style for function and variables names, in which all letters are lowercase and underscores separate words.
- Example:
```Rust
fn main() {
  println!("Hello, world!");

  another_function();
}

fn another_function() {
  println!("Another function.");
}
```
#### Parameters in Functions:
- You can define functions to have **parameters**, which are special variables that are part of a function's signature.
- You can provide **parameters** with concrete values.
- The words **parameters** and **arguments** have the same meaning and are used interchangeably.
- Example:
```Rust:
fn main() {
  another_function(5);
}

fn another_function(x: i32) {
  println!("The value of x is: {x}");
}
```

## Scoping in Rust:

### 1. Variable Scope
- Variables in Rust have a scope, which is the range in which a variable is valid. The scope begins when the variable is defined and ends when it goes out of scope.
- When a variable goes out of scope, Rust automatically calls the **drop** function to free the resources.
- Example:
```Rust
fn main() {
  {
    let x = 5; // x is valid from this point
    println!("x is {x}"); 
  } // x is out of scope here, and Rust deallocates memory
  println!("x is {x}"); // Error: x is not valid here.
}
```

### 2. Ownership and Borrowing
- Rust ensures memory safety by enforcing rules about **ownership, borrowing,** and **lifetimes.**
#### Ownership
- Ownership defines which variable owns a value (each value in Rust has an owner, and there can only be one owner at a time).
- When the owner goes out of scope, Rust frees the memory.
#### Borrowing
- We use **reference (&)**, which like a pointer in that it’s an address we can follow to access the data stored at that address; that data is owned by some other variable. Unlike a pointer, a reference is guaranteed to point to a valid value of a particular type for the life of that reference.
- We call the action of creating a reference *borrowing*.
- Borrowing lets you use a value without transferring ownership, either immutably (&) or mutably (&mut).
Example of borrowing:
```Rust
fn main() {
  let s1 = String::from("hello");

  let len = calculate_length(&s1);

  println!("The length of '{s1}' is {len}.");
}

fn calculate_length(s: &String) -> usize {
  s.len()
}
```

Example of ownership and borrowing:
```Rust
fn main() {
    let s = String::from("hello"); // s is the owner of the string
    print_ownership(s);
    println!("{s}"); // Error: s was moved

    let x = 10;
    print_borrowing(&x); // Borrow x immutably
    println!("x is still accessible: {x}");
}

fn print_ownership(s: String) {
    println!("{s}");
} // s is dropped here

fn print_borrowing(num: &i32) {
    println!("{num}");
}
```
## Special Properties: Closures (anonymous functions that capture their environment)
### What are Closures?
- Rust’s closures are anonymous functions you can save in a variable or pass as arguments to other functions.
- Unlike functions, closures can capture values from the scope in which they’re defined.
- Defined using '|' pipes, closures can accept parameters, have a body, and return values.
- Closure syntax is similar to function syntax except for the use of pipes and the amount of syntax that is optional:
```Rust
fn  add_one_v1   (x: u32) -> u32 { x + 1 }
let add_one_v2 = |x: u32| -> u32 { x + 1 };
let add_one_v3 = |x|             { x + 1 };
let add_one_v4 = |x|               x + 1  ;
```
The first line shows a function definition. The second line shows a fully annotated closure definition. The third line remove the type annotations from the closure definition. The fourth line removes the brackets, which are optional because the closure body has only one expression. These are all valid definitions that will produce the same behavior when they’re called.
- Example:
```Rust
fn main() {
  let add_one = |x: i32| x + 1;
  let result = add_one(5);
  println!("5 + 1 = {result}");
}
```
Closures in Rust automatically infer their parameter and return types. You can annotate types explicitly if needed:
```Rust
fn main() {
  let multiply = |a: i32, b: i32| -> i32 { a * b };
  println!("3 * 4 = {}", multiply(3, 4));
}
```
### Capturing Variables
- Closures can capture variables from their environment in three ways:
  - By Borrowing (capturing by reference) **(&T)**: For read-only access.
  - By Mutably Borrowing (capturing by mutable reference) **(&mut T)**: For modification.
  - By Taking Ownership (capturing by value) **(T)**: For transferring ownership.
Example:
```Rust
fn main() {
    let x = 10;

    // Borrow x immutably
    let add_to_x = |y| x + y;
    println!("10 + 5 = {}", add_to_x(5)); // Results in 15

    // Borrow x mutably
    let mut z = 5;
    let mut update_z = |y| z += y;
    update_z(3);
    println!("Updated z: {z}"); // Results in 8

    // Take ownership
    let s = String::from("hello");
    let consume_s = || println!("Captured string: {s}"); // Results in "Captured string: hello"
    consume_s();
    // println!("{s}"); // Error: s is moved
}
```
### Lifetimes
#### 1. Lifetimes
- Rust uses **lifetimes** to ensure references are valid as long as necessary, preventing dangling pointers/references (reference whose value has gone out of scope)
- A lifetime annotation specifies how long a reference is valid.
- Lifetime annotations have a slightly unusual syntax: the names of lifetime parameters must start with an apostrophe (') and are usually all lowercase and very short, like generic types. Most people use the name 'a for the first lifetime annotation. 
- We place lifetime parameter annotations after the & of a reference, using a space to separate the annotation from the reference’s type:
```Rust
&i32        // a reference
&'a i32     // a reference with an explicit lifetime
&'a mut i32 // a mutable reference with an explicit lifetime
```
#### Lifetime Annotations in Function Signatures
- To use lifetime annotations in function signatures, we need to declare the generic lifetime parameters inside angle brackets between the function name and the parameter list.
- We want the signature to express the following constraint: the returned reference will be valid as long as both the parameters are valid. This is the relationship between lifetimes of the parameters and the return value.
- Example:
```Rust
// The longest function definition specifying that all the references in the signature must have the same lifetime 'a
fn longest<'a>(x: &'a str, y: &'a str) -> &'a str {
  if x.len() > y.len() {
    x
  } else {
    y
  }
}
```
#### 2. Nested Scope
- Rust lets you create nested scopes, where lifetimes of variables are restricted to their respective scopes:
```Rust
fn main() {
  let outer = String::from("outer");
  {
    let inner = String::from("inner");
    println!("In inner scope: {inner}");
  }

  // inner is out of scope here
  println!("In outer scope: {outer}");
}
```
# Conclusion 
##### This document provides a foundational overview of Rust programming concepts, designed to help both new and intermediate developers understand key principles of the language. Starting from the entry point fn main(), it explores Rust's data types, control structures, functions, and advanced topics like ownership, borrowing, and scoping. 
##### Rust's strong emphasis on safety, performance, and concurrency makes it a powerful tool for building reliable and efficient software. Understanding fundamental concepts like ownership, lifetimes, and immutability is essential for writing Rust programs.
##### By mastering these basics and experimenting with the examples, you can confidently progress to more complex topics and leverage Rust’s capabilities to create high-performance applications. 
