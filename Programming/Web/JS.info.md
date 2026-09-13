# 1st Chapter

### Basic Info

- Different engines have different “codenames”. For example:
	- [V8](https://en.wikipedia.org/wiki/V8_\(JavaScript_engine\)) – in Chrome, Opera and Edge.
	- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) – in Firefox.
	- …There are other codenames like “Chakra” for IE, “JavaScriptCore”, “Nitro” and “SquirrelFish” for Safari, etc.

- JavaScript’s capabilities greatly depend on the environment it’s running in. For instance, [Node.js](https://wikipedia.org/wiki/Node.js) supports functions that allow JavaScript to read/write arbitrary files, perform network requests, etc.
- In-browser JavaScript can do everything related to webpage manipulation, interaction with the user, and the webserver.
	- Add new HTML to the page, change the existing content, modify styles.
	- React to user actions, run on mouse clicks, pointer movements, key presses.
	- Send requests over the network to remote servers, download and upload files (so-called [AJAX](https://en.wikipedia.org/wiki/Ajax_\(programming\)) and [COMET](https://en.wikipedia.org/wiki/Comet_\(programming\)) technologies).
	- Get and set cookies, ask questions to the visitor, show messages.
	- Remember the data on the client-side (“local storage”).
- Examples of such In-browser JavaScript restrictions include:
	- JavaScript on a webpage may not read/write arbitrary files on the hard disk, copy them or execute programs. It has no direct access to OS functions.
	    Modern browsers allow it to work with files, but the access is limited and only provided if the user does certain actions, like “dropping” a file into a browser window or selecting it via an `<input>` tag.
	    
	    There are ways to interact with the camera/microphone and other devices, but they require a user’s explicit permission. So a JavaScript-enabled page may not sneakily enable a web-camera, observe the surroundings and send the information to the [NSA](https://en.wikipedia.org/wiki/National_Security_Agency).
	- Different tabs/windows generally do not know about each other. Sometimes they do, for example when one window uses JavaScript to open the other one. But even in this case, JavaScript from one page may not access the other page if they come from different sites (from a different domain, protocol or port).
	    This is called the “Same Origin Policy”. To work around that, _both pages_ must agree for data exchange and must contain special JavaScript code that handles it. We’ll cover that in the tutorial.
	    This limitation is, again, for the user’s safety. A page from `http://anysite.com` which a user has opened must not be able to access another browser tab with the URL `http://gmail.com`, for example, and steal information from there.
	- JavaScript can easily communicate over the net to the server where the current page came from. But its ability to receive data from other sites/domains is severely limited. Though possible, it requires explicit agreement (expressed in HTTP headers) from the remote side. Once again, that’s a safety limitation.
- Such limitations do not exist if JavaScript is used outside of the browser, for example on a server. Modern browsers also allow plugins/extensions which may ask for extended permissions.

- The `<script>` tag contains JavaScript code which is automatically executed when the browser processes the tag.
	- The `type` attribute: `<script type=…>`
		The old HTML standard, HTML4, required a script to have a `type`. Usually it was `type="text/javascript"`. It’s not required anymore. Also, the modern HTML standard totally changed the meaning of this attribute. Now, it can be used for JavaScript modules. But that’s an advanced topic, we’ll talk about modules in another part of the tutorial.
	- The `language` attribute: `<script language=…>`
		This attribute was meant to show the language of the script. This attribute no longer makes sense because JavaScript is the default language. There is no need to use it.
- External scripts
	- `<script src="/path/to/script.js"></script >` 
	  Here, `/path/to/script.js` is an absolute path to the script from the site root. One can also provide a relative path from the current page. For instance, `src="script.js"`, just like `src="./script.js"`, would mean a file `"script.js"` in the current folder
	- We can give a full URL as well and can attach several scripts, use multiple tags
	  `<script src="https://cdnjs.cloudflare.com/ajax/libs/lodash.js/4.17.11/lodash.js"></script>`
	  `<script src="/path/to/script.js"></script>` 
	- **Syntax**-**Wise**: If `src` is set, the script content is ignored
		`<script src="/path/to/script.js"`
		`alert(x); // the content is ignored, because src is set`
		`</script>
		- The example above can be split into two scripts to work
- **As a rule**, only the simplest scripts are put into HTML. More complex ones reside in separate files 
	- The benefit of a separate file is that the browser will download it and store it in its cache
	- Other pages that reference the same script will take it from the cache instead of downloading it, so the file is actually downloaded only once
	- That reduces traffic and makes pages faster

- **Syntax-Wise**: 
	-  Semicolons Can be omitted in most cases
	  - Newline implies a semicolon in most cases
	  - There are cases when a newline does not mean a semicolon. For example:
	    1. `alert(3 +`
		    `1`
		    `+ 2);`
			- The code outputs `6` because JavaScript does not insert semicolons here. It is intuitively obvious that if the line ends with a plus `"+"`, then it is an “incomplete expression”, so a semicolon there would be incorrect. And in this case, that works as intended
		2. `alert("Hello")`
		    `[1,2].foreach(alert);`
		    - If we run this code, only the first `Hello` shows (and there’s an error, you may need to open the console to see it). There are no numbers any more.
		    - That’s because JavaScript does not assume a semicolon before square brackets `[...]`. So, the code in the last example is treated as a single statement.
  - Having 2 statements in the same line wothout a semicolon; both won't run

- **Syntax-Wise**: 
	- One-line comments start with `//` 
	- Multiline comments start with `/*` and closed with `*/`
	- Statments do not run inside comments
	- Nested comments are not supported 

-  To keep the old code working, most such modifications are off by default. You need to explicitly enable them with a special directive: `"use strict";` or `'use strict';`
	- When it is located at the top of a script, the whole script works the “modern” way.
	- Can be put at the **beginning** of a function. Doing that enables strict mode in that function only. But usually people use it for the whole script.
	- There is no directive like `"no use strict"` that reverts the engine to old behavior. Once we enter strict mode, there’s no going back
	- It works in most browsers, namely Firefox and Chrome. If it doesn’t, e.g. in an old browser, there’s an ugly, but reliable way to ensure `use strict`. Put it inside this kind of wrapper:
	  `(function(){'use strict';// ...your code here... })()`
	- Modern JavaScript supports “classes” and “modules” – advanced language structures, that enable `use strict` automatically. So we don’t need to add the `"use strict"` directive, if we use them.
  
### Variables

- A [variable](https://en.wikipedia.org/wiki/Variable_\(computer_science\)) is a “named storage” for data. We can use variables to store goodies, visitors, and other data.
- Is Uniquely named and **case matters**
- To create a variable in JavaScript, use the `let/var VARNAME;` keyword.
- Can put some data into it by using the assignment operator `VARNAME=VARVALUE;`
- Can combine the variable declaration and assignment into a single line
- Can access it using the variable name
- Can also declare multiple variables in one line by either ways
	1. `let VAR1 , VAR2 , VAR3;`
	2. `let VAR1,` 
	    `VAR2,`  
	    `VAR3;`
	3. `let VAR1;` 
	    `let VAR2;`  
	    `let VAR3;`
- Can also change it as many times as we want using `VARNAME=VARVALUE;`
- Can also declare two variables and copy data from one into the other using `VAR1=VAR2;`
- Declaring twice triggers an error
- There are two limitations on variable names in JavaScript
	1. The name must contain only letters, digits, or the symbols `$` and `_`. **no hyphens**
	2. The first character must not be a digit.
	- Non-Latin letters are allowed, but not recommended
	- There is list of reserved words -ones used by the language itself- that cannot be used as `let, class, return, function, etc.`
- **Without using `use strict`** we can assign a value without using `let` /  `var` with only `VARNAME = VARVALUE` as declaration and assignment 
	- `'use strict;'` `VARNAME = VARVALUE` => variable is not definied 

### Constants

- To declare a constant use `const` instead of `let` or `var`
- Constants cannot be reassigned, and an attempt to do so will cause an error
- There is a widespread practice to use constants as aliases for difficult-to-remember values that are known before execution. like colors selected in hex
- Some constants are known before execution and some are calculated during runtime. Both as constants, once assigned; they will never change

### Data types

- There are 8 data types in JS which are:
	1. `number` 
		- has a safe interval: {9007199254740991, -9007199254740991} *+/- 2^53 -1*
		-  But can store more outside the safe range leading to precision errors
	2. `bigint` 
		-  can store any large number but ad `xxxn` after the number
	3. `string`
		-   can be using `` '' "" 
		- The first (hidden) backtricks allow to embed variables and expressions into a string wrapping them in `${}` 
		- `alert(``Hello,_${name}!)``; // Hello, John!`
	4. `boolean` 
		- Yes / No situations
	5. `null`
		- Referencing to non-existing 
	6. `undefined`
		- Differenet from null as it inicates no assignation *i.e. no declaration*
	7. `object`
		- Used to store collections of data and more complex entities
	8. `symbol`
		- Used to create unique identifiers for objects
- We can put any type in a variable. For example, a variable can at one moment be a string and then store a number
- There are many operations for numbers, e.g. multiplication `*`, division `/`, addition `+`, subtraction `-`, and so on
- There are so-called “special numeric values” which also belong to this data type: `Infinity`, `-Infinity` and `NaN` 
	 - `NaN`represents a computational error. It is a result of an incorrect or an undefined mathematical operation *(number / letter)*
	 - `NaN` is sticky. Any further mathematical operation on `NaN` returns `NaN`, it propagates to the whole result (there’s only one exception to that: `NaN ** 0` is `1`
- **Syntax-Wise**: Doing maths is “safe” in JavaScript. We can do anything, The script will never stop with a fatal error (“die”). At worst, we’ll get `NaN` as the result
- There is no a character only data type like `char` in C++, **only a string** that may consist of zero characters (be empty), one character or many of them
- `typeof xxxx` / `type of (xxxx)` operator is used to tell whats the type of that entry
  
### Alert

- Mini window AKA modal
- Visitor cannot interact with the rest of the page until dealing with the modal *i.e. pressing OK*
- Converts any value to a string to show it

### Prompt

`result = prompt( TITLE, default/xxx/'leftempty' )`
- Modal window that takes 2 inputs (one from code, the other from user)
	1. Title: Text shown to the visitor
	2. Default: **Opptional -But good to use-** second parameter, the intial value for the input field
- Prompt can be exited by user without inputting by pressing ESC and the result will be `null`

### Confirm

`result = confirm ("question")`
- Modal window that have 2 choices as a result or answer for the asked question
	1. OK => True
	2. Cancel / pressing ESC => False

## For all Interactions Alert, Prompt & Confirm  

- There are 2 limitations 
	1. The exact location of the modal window is determined by the browser, usually the center
	2. The exact look of the modal window is determined by the browser
   
### Conversions 

| String Conversion          | Numeric Conversion                                                      | Boolean Conversion                            |
| -------------------------- | ----------------------------------------------------------------------- | --------------------------------------------- |
| `newvalue = string(value)` | `newvalue = number(value)`                                              | `newvalue = boolean(value)`                   |
| True of bool => "True"     | True of bool => 1                                                       |                                               |
| null => "null"             | null => 0                                                               | null => False                                 |
| undefined => "undefined"   | undefined => `NaN`                                                      | undefined => False                            |
| `NaN` => "NaN"             |                                                                         | `NaN` => False                                |
|                            | empty string => 0                                                       | empty string => False                         |
|                            | numstring => numstring without whitespaces (tabs, newline,spaces, etc.) | numstring => True if zero / False if non zero |
|                            | nonempty string => NaN                                                  | nonempty string / => True                     |
- `Boolean("0"/"false"/" ")` → `True` (non-empty string)

### Operators & Maths

- Operators are classified into:
	1. unary -> Needs single operand (term/argument)
		- `- OPERAND` -> `-` **resverses** the sign of a number 
		- `+ OPERAND` -> `+` has no effect on numbers, **but converts non numbers -> numbers** *i.e. `+true => 1`*
		- `--OPERAND/ OPERAND--` -> In/decerements **only variable** operand by 1
	2. Binary -> Needs 2 operands 
		- `OPERAND - OPERAND` -> Minus
- Maths Operators supported:
	1. Addition `+`
		- Can concate/merge strings
		  `let s = "my" + " " + "string"; // my string`
		- If any of the operands is a string, then the other one is converted to a string too
			-  `let s = 2 + 2 + "1"; // 41`
				- leftmost `+` has both operands as numbers `2+2=4`
				- rightmost `+` has `4` as number operand and `"1"` as string operand => both are converted to strings => `"41"`
			- `let s = "1" + 2 + 2 ; // 122` 
				- leftmost `+` has `2` as number operand and `"1"` as string operand => both are converted to strings => `"12"`
				- rightmost `+` has `2` as number operand and `"12"` as string operand => both are converted to strings => `"122"`
		- **OTHER OPERATORS CANNOT CONCATEANTE OR DEAL WITH STRINGS AND CONVERTS THEM TO NUMBERS if possible**
	2. subtraction `-`
	3. Multiplication `*`
	4. Division `/`
	5. Remainder `%`
	6. Exponentiation
		- `BASEOPERAND ** POWEROPERAND`
		- Can use non-integers as well
- Operator precedence ![[Pasted image 20260913084457.png]]
	- If equal precedence => Leftmost first
	- `++/--` are considered unary plus/negation so they have top precedence
- Bitwise Operators