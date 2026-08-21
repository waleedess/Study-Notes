# CSS Syntax 

`SELECTOR {` => ex. body *-selected HTML tag-*
	`PROPERTY: VALUE` => ex. color: navy
`}`

# Simple Selectors

- Have 4 Types:
	1. Element (Lowest Specifity - Most Negligible)
	2. Class
	3. ID
	4. Inline   (Highest Specifity - Least Negligible)

### Element Selector 

- `<Tag> {` => ex. body *-selected HTML tag-*
	`PROPERTY: VALUE`
`}`

`<style>`
`h2 {` => Selects all H2, changes color for all 
`color:khaki;`
`}`
`h3{` => Selects all H3, changes color for all 
`color:hotpink`
`}`
`body {`
`background-color: aqua;`
`}`
`</style>`

- **Body HTML**
	`<body>`
	`<h2> Hi Ana Waleed </h2>`
	`<h2> Msh baaraf akhtar alwan </h2>`
	`<h2> Da bgd </h2>
	`<h3>Bas msh moshkela</h3>`
	`<h3>Msh lazem aady</h3>`
	`</body>`

- **Output**
  All H2 => khaki
  All H3 => hotpink

--- 

### Class Selector

- `.<class> {` => ex. body *-selected HTML class-*
	`PROPERTY: VALUE`
`}`

`<style>`
`h2 {` 
`color:khaki;`
`}`
`h3{` 
`color:hotpink`
`}`
`.niggas{`  => Selects all tags that have `class="niggas"`
`color:black`
`}`
`body {`
`background-color: aqua;`
`}`
`</style>`

- **Body HTML**
	`<body>`
	`<h2> Hi Ana Waleed </h2>`
	`<h2> Msh baaraf akhtar alwan </h2>`
	`<h2 class="niggas"> Da bgd </h2>
	`<h3 class="niggas">Bas msh moshkela</h3>`
	`<h3>Msh lazem aady</h3>`
	`</body>`

- **Output**
  All H2 => khaki, except the last
  All H3 => hotpink, except the first
  All with `class="niggas"` => black
  
--- 
### ID Selector

- `#<id> {` => ex. body *-selected HTML id-*
	`PROPERTY: VALUE` 
`}`

- ID is unique for tags
  
`<style>`
`h2 {` 
`color:khaki;`
`}`
`h3{` 
`color:hotpink`
`}`
`.niggas{`  
`color:black`
`}`
`#whiteboi1{` => Selects only the tag that have `id="whiteboi1"`
`color:whitesmoke`
`}`
`body {`
`background-color: aqua;`
`}`
`</style>`

- - **Body HTML**
	`<body>`
	`<h2 id="whiteboi1"> Hi Ana Waleed </h2>`
	`<h2> Msh baaraf akhtar alwan </h2>`
	`<h2 class="niggas"> Da bgd </h2>
	`<h3 class="niggas">Bas msh moshkela </h3>`
	`<h3> Msh lazem aady< /h3>`
	`</body>`

- **Output**
  All H2 => khaki, except the first and the last
  All H3 => hotpink, except the first
  All with `class="niggas"` => black
  Tag with `id="whiteboi1"` => whitesmoke
  
  ---
### Inline 

- In eah HTML tag as an attribute not under style tag
	`<h1 style="color:red"> <h1>`

---
# External CSS

- File.css

`<head>
`<link rel="stylesheet" href="Learning.css">`
`</head>`

---
# Complex Selectors

- Complex Selectors are :
	1. Universal Selector 
	2. Multiple & Compinator Selector
	3. Attribute Selectors

### Universal Selector

- `* {` 
	`PROPERTY: VALUE`
`}`

- Have less specifity, more neglected than all of Simple Selectors
---
### Multiple & Combinator Selectors

###### 1
- `x,y,z {` => Selects all of x,y and z
	`PROPERTY: VALUE` 
`}`

###### 2
- `x z {` => Each z that is inside *-i.e. Child of-* a x (**Even** if as a **Grand Child**) 
	`PROPERTY: VALUE`
`}`

###### 3
- `x > z {` => Each z inside *-i.e. Child of-* x (**Only** if as a **Direct Child**)
	`PROPERTY: VALUE` 
`}`

###### 4 
- ` x + y {` => Each y after *-i.e. Sibling of-* x (**Only** if as a **Direct**)
	`PROPERTY: VALUE`
`}`

###### 5 
- ` x ~ y {` => Each y after *-i.e. Sibling of-* x (**Even** if as a **Not Direct**)
	`PROPERTY: VALUE` 
`}`
---
### Attribute Selectors

###### 1
- ` [att] {` => Selects each HTML tag that includes that attribute
	`PROPERTY: VALUE`
`}`

###### 2
- ` [att = "VALUE"] {` => Selects each HTML tag that includes that attribute with the exact mentioned value
	`PROPERTY: VALUE` 
`}`

###### 3
- ` [att ^= "VALUESTART"] {` => Selects each HTML tag that includes that attribute with the value starting with the mentioned input
	`PROPERTY: VALUE`
`}`

###### 4
- ` [att $= "VALUEEND"] {` => Selects each HTML tag that includes that attribute with the value ending with the mentioned input
	`PROPERTY: VALUE` 
`}`

###### 5
- ` [att *= "VALUEInculded"] {` => Selects each HTML tag that includes that attribute with the value including with the mentioned input
	`PROPERTY: VALUE` 
`}`

###### 6
- ` [att |= input] {` => Selects each HTML tag that includes that attribute with the value is the **input first and alone or `input-xxxx`** 
	`PROPERTY: VALUE` 
`}`

###### 7
 - ` [att ~= input] {` => Selects each HTML tag that includes that attribute with the value includes that **input alone or spaced**
	`PROPERTY: VALUE` 
`}`

###### 8
- ` <tag>[att] {` => Selects the selected HTML tag that includes that attribute and **all the operators apply**
	`PROPERTY: VALUE`
`}`

###### 9 
- ` <tag> [att] {` => Selects the **childs** of the selected HTML tag that includes that attribute and **all the operators apply**
	`PROPERTY: VALUE`
`}`
---
