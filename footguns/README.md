# Rust Footguns

## Cheap vs Expensive Clones
The .clone() method does not descriminate between cheap and expensive clones. 

Cloning a String, Vec, or Hashmap creates an secondary heap allocation.
Cloning an Rc<&str> however, only creates a new stack allocation and incremenets the refernce count.

When cloning in rust it can be difficult to ensure that the programmer knows when heap allocations are made.

The solution is to use either Dupe, or LightClone.
Both of which will issue a compiler error if attempting to .dupe() or .light_clone() on a type that will create additional heap allocations.

So go ahead an liberally dupe or light_clone. When you run into a type that causes compiler error the programmer has two options.
1. Refactor the type:
  - If the value is immutable, then Rc<T> is an easy win.
  - If the value is mutable, then ???? maybe &str? (But then doesn't that cause lifetime issues?)
3. Acknowledge the performance hit, call .clone, perhaps measure performance before and after, and document the decision.

## Aliasing in Match statements
When aliasing the enum name in order to save space in a match statement, do NOT use the wildcard (*) value.

