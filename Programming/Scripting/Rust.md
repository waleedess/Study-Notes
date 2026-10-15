# 3.1 Variables
---

###### Mutability
- Rust's variables are immutable by default meaning that they cannot be changed once assigned
- **`mut`** changes the value in the same variable. The type stays the same, and the variable must have been declared with `let mut VAR`
###### Shadowing
- Shadowing means declaring a new variable with the same name using `let` it creates a new binding, The old one is gone from that point on, so the type can change, Unlike `mut` 

###### Unused
- Rust treats an unused variable as a likely mistake so the compiler will give a warning and there is 2 fixes for this warnings:
	1. `let _VARNAME`: the underscore tells Rust you meant to leave it unused. This is the usual choice
	2. `#[allow(unused_variables)]`: silences the warning for the function or item it sits above. This is broader and can hide real bugs, so use it sparingly. It goes on the line above the item, and `#![allow(...)]` with an ==🔴exclamation mark applies it to the whole file== 