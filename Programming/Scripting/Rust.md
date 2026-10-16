# 3.1 Variables
---
### Mutability
- Rust's variables are immutable by default meaning that they cannot be changed once assigned
- **`mut`** changes the value in the same variable. The type stays the same, and the variable must have been declared with `let mut VAR`
### Shadowing
- Shadowing means declaring a new variable with the same name using `let` it creates a new binding, The old one is gone from that point on, so the type can change, Unlike `mut` 

### Unused Variables
- Rust treats an unused variable as a likely mistake so the compiler will give a warning and there is 2 fixes for this warnings:
	1. `let _VARNAME`: the underscore tells Rust you meant to leave it unused. This is the usual choice
	2. `#[allow(unused_variables)]`: silences the warning for the function or item it sits above. This is broader and can hide real bugs, so use it sparingly. It goes on the line above the item, and `#![allow(...)]` with an ==🔴exclamation mark applies it to the whole file== 
====

# 4.1 Numbers
---
### Integers `:i/u`

- **`i`: Signed integer** can represent both positive and negative integers
- **`u`: Unsigned integer** represents positives only

| Length                                           | Signed              | Unsigned |
| ------------------------------------------------ | ------------------- | -------- |
| 8-bit                                            | `i8`                | `u8`     |
| 16-bit                                           | `i16`               | `u16`    |
| 32-bit                                           | `i32` - **Default** | `u32`    |
| 64-bit                                           | `i64`               | `u64`    |
| 128-bit                                          | `i128`              | `u128`   |
| arch - architecture dependent (32-bit or 64-bit) | `isize`             | `usize`  |

### Floating Point `:f`

| Length | Float               |
| ------ | ------------------- |
| 32-bit | `f32`               |
| 64-bit | `f64` - **Default** |

### Converting Numeric Types

 `as`: explicit type conversion 
> 	`as` converts a value to another type. Rust doesn’t do this implicitly, so you write it yourself. If the value doesn’t fit the new type, it wraps or truncates

- Possibilities:
	1. **Widening**: `let small = 38_u8 as u16;` => ==🟢Safe==
	2. **Narrowing**: `let big = 300_u16 as u8;` => ==🔴wraps around==, gives 44
	3. **Bool->Integer**: `let flag = true as i32;` => 1
	4. **Char->Integer**: `let letter = 'A' as u32;` => 65
	5. **Float->Integer**: `let pi_int = 3.9_f64 as i32;` => ==🔴truncates== to 3

###### Ranges
 
- `a..b`: Includes `a` but excludes `b` (equates `Range{ start: a, end: b }`)
- `a..=b`: Includes both `a` and `b` (equates `RangeInclusive::new(a, b)`)

###### Bitwise Operators

1. `&` AND
2. `|` OR
3. `^` XOR (exclusive OR), Alike => 0, Diff => 1
4. `!` NOT (flips every bit)
5. `value << amount` left Bit-shift
6. `value >> amount` right Bit-shift
====

# 4.2 Char, Bool & Unit
---
### Characters `:char`

- Double quotes => ==🔴String==, Single quotes => ==🟢Char==
- Always in size of 32-bits
- Holds one Unicode scalar value, so it can represent letters from any language, symbols, and emoji

### Boolean `:Bool`

- Always in size of 8-bits
- Default => `False`
- Can be compared using 2 methods:
	1. **Bitwise Operators**: `&&`/`&`, `||`/`|`, `!` or `^`
	2. **Mathematical Operators**: `<`/`>`
		- `True > False` => True
		- `True > True` / `False > False` / `False > True` => False

### Unit `: ()`

- An ==empty tuple== Symbolizes "No data" and sizes 0-bytes
  
- Has 1 value *`bool` has 2, `u8` has 256*
	- The “never” type `!` has 0 values, because it can never produce a value at all. A function that always panics or loops forever has this return type

- Example: `let v: () = ();`

- **Rust uses it in a few places**: 
	1. **Functions with no return value.** A function without `->` returns `()` implicitly.
	2. **Statements ending in `;`.** `5;` evaluates to `()`, not `5`.
	3. **Results where only success or failure matters**, such as `Result<(), String>`. `Ok(())` means success with no data, and `Err(message)` carries the error.
====

# 4.3 Statements & Expressions

### Statements

- Performs an action & does not produce a useful value
- End with `;`
- Examples:
	1. `let` bindings
	2. Function calls whose result are not used

### Expressions 
- Produce a value 
- Do not end with `;` directly
	- `let z = { 10 * 2 };` (block) => is still an expression even with the `;`
  
### Contrast

###### First
`fn plus_one(n: i32) -> i32 {
    `n + 1        // expression: no semicolon, value is returned`
`}`

`fn plus_one_broken(n: i32) -> i32 {`
    `n + 1;       // statement: value is discarded, function returns ()`
`}                // error: expected i32, found ()`

- Semicolon is the key difference as it discarded the value
###### Second

`let n = 7;`
`let kind = if n % 2 == 0 { "even" } else { "odd" };  // "odd"`

- If's result is used => ==**If** is an Expression== 
====

# 4.4 Functions `fn`

- Block of reusable code 
- Declared with `fn name(param: Type, param2: Type) -> ReturnType { // body }`
- Can take arguments/parameters, return type and returns results
	1. **Arguments**:
		- Must have explicit types 
		- Mention `mut` when using mutability
	2. **Return Type**:
		- If `-> RT` is omitted, function returns `()`
		- Use `-> !` if the function is never-returning
	3. **Return**:
		- The lase expression without `;` is returned
		- `return VALUE;` returns it early, useful in loops/conditions
- **`const fn`** can be evaluated at compile time