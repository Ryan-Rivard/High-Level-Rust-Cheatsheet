# High-Level-Rust-Cheatsheet
How to write Rust for Grug Brained Developers

Writing rust on the intersection of the vendiagram of Correctness, Performance, and Ergonomics.

## Correctness
Both Rust's memory type safety, which us grug brains don't always understand the holy scriptures; but I think almost just as important is its Type Saftey. Algebraic Data Types allow for illegal states to be unrepresentable. And if a good practice is to fail fast, then type driven development is one of the fastest ways toward correct software.

## Ergonomics
As a C-like language with great support for either functional or proceedural paradigms, standard Rust is actually quite simple to read. Pure functions make refactoring simpler, and the absence of pure OOP is a net positive. However Rust does have deeper more unfamiliar aspects that can crop up when squeezing out every ounce of performance, or anything async tbh...

## Performance
No garbage collection means low memory footprint. Speed should be just as or damn near any other language can achieve, if you are willing to put in the work. But we are grug brained developers. We recognize that Facebook was written in PHP, and we are okay with tradeoffs of performance to keep our ergonomics.

# What to prefer and what to avoid
Be like Bruce Lee; absorb what is useful, disgard what is useless.

## Functional Paradigm
| Aspect | Recomendation | Reasoning |
| :---: | :---: | :---: |
| Immutability | 🟢 Prefer | Mutable data and shared state can be difficult to manage, Rust defaults to immutable but allows the explicit escape hatch for when it is needed |
| Pure Functions | 🟢 Prefer | Functions that have no side-effects and always produce the same output for a given input are easy to test and less prone to bugs. They have other benefits such as simpler parallelization and are easier to refactor if needed |
| First Class Functions | 🟢 asdf | asdf |
| Higher-Order Functions | ⚠️ Contingent | Good for simpler actions, but if your logic is complex prefer procedural as it will be easier to debug |
| Function Composition | 🟢 asdf | asdf |
| Recursion over loops | 🛑 Avoid | asdf |


---

Rust and its benefits have always felt out of reach for some (most) developers. Memory Management is often touted as the Elephant Graveyard, and that Garbage Collection is the Pride Lands from which we should not stray.

Rust's promise of Memory Safety without Memory Management has been so alluring but so foreign for myself and many others. Inspired by Hamy.xyz I have been exploring how to write Rust with the Pareto Princliple in mind. Gaining the majority of the benefits with a minimum amount of the drawbacks.

Rust's benefits being:
1. Type System
2. Fuctional Patterns
3. Performance (Speed / Size)
4. Street Cred

Rust's drawbacks being:
1. Fighting the Borrow Checker
2. Lifetimes
3. Abstraction Layers
4. Thigh-high socks

# How to write Grug-brained Rust
1. Type-first domain modeling
2. Prefer
    1. Immutable values + structures
    2. Pure functions
    3. Functional Core Imperative Shell
3. Domain Driven Design

When in trouble `.clone()` can help you escape (but beware of the dragons defined below)

# Type-first Domain Modeling
Before writing any functions or tests. We first should model out our domain, with the goal to make irrepresentable states illegal. Doing so will erase an entire category of bugs, reduce the amount of code required, and is the best for of documentation.


## Unit Types
```rust
// unsigned prevents negative numbers (but can force this to runtime error with indirection)
let positive: u8 = 10;
let zero: u8 = 0;
// Compilation error
let negative: u8 = -10;

// nonzero returns option on construction which enforces runtime check
let some_positive = NonZeroU8::new(10);
let none_zero = NonZeroU8::new(0);
// Compilation Error
let negative = NonZeroU8::new(-10);

let possible_input : Option<&str> = Some("user input");

enum UserRole {
    Guest,
    User,
    Admin,
}
```
Enums represent a singular 

# Links / Inspiration
https://hamy.xyz/blog/2026-01_high-level-rust

https://grugbrain.dev/

