# High-Level-Rust-Cheatsheet
How to write Rust for Grug Brained Developers

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

# Links / Inspiration
https://hamy.xyz/blog/2026-01_high-level-rust

https://grugbrain.dev/

