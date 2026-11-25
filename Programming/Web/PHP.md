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

`$NAME = [`
    `KEY1  => VALUE1,`
    `KEYn => VALUEn,`
`];`
**OR**
`$NAME = array(`
    `KEY1  => VALUE1,`
    `KEYn => VALUEn,`
`);`


- Keys can be int or string only, while value can be of any type
- The key is optional. if not specified will be indexed by incrementing form 0 as usual
	- It is possible to specify keys for some elements and leave others
	- If negative integer key was used will be incremented as usual also
- Additionally the following key casts will occur:
	- Strings containing valid decimal [int](https://www.php.net/manual/en/language.types.integer.php)s, unless the number is preceded by a `+` sign, will be cast to the int type. E.g. the key `"8"` will actually be stored under `8`. On the other hand `"08"` will not be cast, as it isn't a valid decimal integer.
	- Floats are also cast to [int](https://www.php.net/manual/en/language.types.integer.php)s, which means that the fractional part will be truncated. E.g. the key `8.7` will actually be stored under `8`.
	- Bools are cast to ints, too, i.e. the key `true` will actually be stored under `1` and the key `false` under `0`.
	- Null will be cast to the empty string, i.e. the key `null` will actually be stored under `""`.
	- Arrays and objects _can not_ be used as keys. Doing so will result in a warning: `Illegal offset type`.