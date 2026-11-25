# Basic Info
---
- PHP can be injected in the html file leading to changing its extension to `.php`

# Variables
---
- Variables do not have a type, values have: string, int, float, boolean, null, array, object, resource
- `isset(VAR)` method used to check if the variable is defined or not in an bool output 
	- `null` definied => false
	- `undefined`, `unset()` => null

##### Declaration

`$NAME = VALUE;`

##### Call

`$NAME`

- to get them with their type => 
  
# Constants
---
- Immutable cannot be changes 
- `defined(VAR)` method is used to check if a constant is defined or not in a bool output

###### Declaration

`define('NAME', VALUE)` => Without `$`

###### Call

`NAME` => Without `$`

### Arrays

`NAME(
    `KEY1  => VALUE1,
    `KEYn => VALUEn,
`)`
