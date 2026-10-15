# 3.1 Variables
---

###### Mutability
- Rust's variables are immutable by default meaning that they cannot be changed once assigned
- **`mut`** changes the value in the same variable. The type stays the same, and the variable must have been declared with `let mut VAR`
###### Shadowing
- Shadowing means declaring a new variable with the same name using `let` it creates a new binding, The old one is gone from that point on, so the type can change, Unlike `mut` 