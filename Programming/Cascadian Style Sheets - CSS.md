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
	`PROPERTY: VALUE` => ex. color: navy
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

# Class Selector

- .class {` => ex. body *-selected HTML class-*
	`PROPERTY: VALUE` => ex. color: navy
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

- - **Body HTML**
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
# ID Selector

- `#id {` => ex. body *-selected HTML id-*
	`PROPERTY: VALUE` => ex. color: navy
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