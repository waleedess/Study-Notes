# Text

- The website should contain only one h1
- `<font attributes=””>text</font>: size, color(name&hex) and face(font)`
- To get all spaces and break lines `<pre>h t m l</pre>`, but it is not preferable
- `<b> </b>` → bold
- `<i> </i>` → italic
- `<u> </u>`→ underline
- <br/>(no close), this only → break line
- <hr/> (no close), this only → horizontal separator
- `&nbsp` (nonbreakablespace) → space *breakable ely heya lama tool el satr yekhlas*
- &lt - &gt→ less/greater than
- `<center></center>` → center text
- `<div attributes=””></div>(Block element) →**accept alignment,** attributes: align`
- `<p></p>`(Block element) →**accept alignment,** attributes: align
- `<span></span>` (Inline element)→ in line text display, **do not accept alignment**

---

# Lists

Got 3 types:

#### unordered

`<ul></ul>` 
and members in between in list item `<li>`

- `<li attributes=””></li>` → attributes : type: circle …etc
    - Can have nested just like the ones im using in notion

---

#### ordered

`<or></or>` and members in between in list item `<li>`

- `<li attributes=””></li>` → attributes : type … a/A/i/I(roman) - start 2,3 same if roman not ii

---

#### definition

`<dl></dl>` Have title and definitions

<dt></dt> → definition title
<dd></dd> → definition, displayed under its title

---

# Linking

#### 1. To External File (URL)

`<a href=”https://xyz.com”> Click here </a>`

#### 2. To Internal File (Path)

Whether by:

- Absolute path **USING “”**
    - starting from drive going through each folder. even if both pages was in the same →  `href = “drive/folder/folder/file.html”`
- Relative path **NO USE OF “”**
    - If in same exact folder → `href = file.html`
    - If in a folder in the same folder → `href=folder/file.html`

Notes: 

1. `../` → to go to the mother folder`../../`is x2
2. `./` → means in the same folder and can be a mix of absolute *(using”)* and relative *(not full path)* by doing this `href=”./file.html”`

#### 3. To a section on the same page

`<a href=”#sectionname”> Click here </a>`
…<!--code-->…
`<a name=”sectionname”>...<!--code-->...</a>`

#### 4. To a section on Different page

Page 1

`<a href=”<Pathofpage2>/file.html#sectionname”> Click here </a>`

Page 2

`<a name=”sectionname”>...<!--code-->...</a`

#### 5. To email

`<a href=”mailto:email"> Click here to contact </a>`

- Can add some attributes by adding {`?`} then the attribute
`<a href=”mailto:email?subject=xyz"> Click here to contact </a>` 
attributes like subject : CC, BCC, Body
    - **BCC/CC**→ `<a href="mailto:test@email.com?bcc=secret@email.com>`
    - **BCC+CC** *using {&}* → `<a [href="mailto:test@email.com](mailto:href=%22mailto:test@email.com)?cc=copied@email.com**&**bcc=secret@email.com">`
    - {`&`} → Combines multiple fields together
    - `body..%20..body..%0A..body..` → `%20`=> Translates to space, `%0A` => Translates to line break. Both work whatever the attribute
    - `<a href="mailto:?subject=Spontaneous%20Message">` → Blank recipient (removes the assigned mail and let the user input it manually)
    - `<a [href="mailto:one@email.com](mailto:href=%22mailto:one@email.com)[,two@email.com](mailto:,two@email.com)">` →  {`,`} Sends to multiple primary recipients at once

---
# Images 

#### Adding
1. **Using URL**
   `<img src="URL" />`
   
2. **Relative Path**
	`<img src="/folder/file.ext" />`

#### Formatting 
`<img src="URL"`
`width="xxxpx"` -> ==Attribute==
`height="xxxpx"` -> ==Attribute==
`alt="text"` -> ==Attribute==
`/>`

#### Alignment
`<img src="URL" width="xxxpx" height="xxxpx" alt="text"`
`align="position"` -> ==Alignment==
`/>`

#### Mapping

1. **1 Link as whole Image**
`<a href="link">`
	`<img src="URL" width="xxx(px/%)" height="xxx(px/%)" alt="text" align="position" />`
`</a>`

2. **Mapping links to parts**

`<img` 
`src="URL" width="xxx(px/%)" height="xxx(px/%)" alt="text" align="position"` 
`usemap="mapname"` => ==Inside `<img/>`==
`/>`

`<map name="mapname">`
`<area shape="circ/rec/poly" coords="x,y,radius" href="link1">`
`<area shape="circ/rec/poly" coords="x,y,radius" href="link2">`
`<area shape="circ/rec/poly" coords="x,y,x,y,..." href="link3">`
`</map>`

---
# iFrame

**Other Websites or manual**
`<iframe `
`width="(px/%)" height="(px/%)" scrolling="yes/no"` => ==Attributes==
`src="Path/URL"`
`/>`

**Third-party**
like YT and other -> use embedding

---
# Tables

![[Pasted image 20260815025721.png]]

- **Main** **Structure**
`<table width="xxxpx" border="xxxpx">`
	`<caption>txt</caption>`
	`<thead>`
		`<tr>`
			`<th colspan="2" > </th>`
			`<th  rowspan="2" > </th>`
			- both makes headers, th -> Bold and centered but td is not
		`</tr>` 
	`</thead>`
	`<tbody>`
		`<tr>`
			`<th width="50%" ></th>`
			`<td height="100px"></td>`
		`</tr>`
	`</tbody>`
	`<tfoot>`
		`<tr>`
			`<th></th>`
			`<th></th>`
		`</tr>`
	`</tfoot>`
`</table>`

- **Attributes**
	- Text:
		- Font
		  `<td> <font color="xyz" >text</font> <th>`
	- Cell:
		- Background
		  `<body bgcolor="zyx">`
		  `<tr bgcolor="zyx">`
		  `<table bgcolor="zyx">`
		- Alignment
			- Vertical: `<td valign="Top/middle/Bottom">`
			- Horizontal: `<td align="Right/Centre/Left">`
		- Padding & Spacing
			- Padding: `<table cellbadding="xxpx">`
			  -> Space between cell border and text
			- Spacing `<table cellspaceing="yypx">`
			  -> Space between Cells
			- Both can be used only affecting the whole tabel i.e. in the `<table>`
  
---
# Forms 
![[Pasted image 20260817214522.png]]
- All of the blue highlighted uses input tag

# Form Tag  

`<form>`
`method="POST/GET"` -> GET is the defauly
`action=""` -> When to go after submission
`<input>1`
`<input>2`
`<input>3`
`<textarea> </textarea>`
`</form>`

### Input Tag

`<input` 
`type="One of the blue highlighted"
`id=""` => As it inputs data that will be retrived, ID is unique
`name""` => Just like ID but may be repeated
	- Same name groups things, all radio for example is clickable. but when 2 have the same i.e. have group only one will be clickable
`value=""` =>  The input Variable that will be retrived. Intially written before user input
*`src=""` => with Image Button
`/>`

### TextArea 

`<textarea
`cols="xxx"`
`rows="yyy"` => When text is longer -> Scroll appears
`id=""`
`name=""`
`>
`</textarea>`

# Dropdown list/Select Tag

`<select
`size="x"` => Default = 1
`multiple` => Can select multi-values using ctrl from keyboard
`>`
	`<option>` option1`</option>1`
	`<option>` option2 `</option>2`
`</select>`

---
# Body Attributes

`<body>`
`bgcolor=""`
`background="image from file"`
`link=""` => idle, el tabe3y
`alink=""` => Active, lama el cursor yegy aleha bs no click
`vlink=""`=> visited, lama y-click
`<script> </script>` => JS code or JS file path
`</body>`

---

# Head and Doctype

### Doctype

- Info for browser, can be neglected now, but it was essential at legacy.
- `<!Doctype html>` => HTML5

### Head tag

`<head>`
	`<title></title>` => The only visible 
	`<base href="relativepath"/>` => Folder containing all added sources like imgs in the website
	`<meta`
		`name="Author"`
		`description=""`
	`/>`
	`<meta`
		`name="Author"`
		`content="Authorcontent"`
	`/>` => Meta can be multiple
	`<script> </script>` => JS code or JS file path
	`<style>` `<style>` => ==CSS code only==
	`<link`
		`rel="icon"`
		`href="path"`
	`>` => Link can be multiple
	`<link`
		`rel="stylesheet"`
		`href="path"`
	`>` => To add CSS file 
`/head`

---

# Notes

1. The `color` attribute can be used in `<link>`, `<font>`, and `<hr>` tags, but ***not*** in `<p>`, `<div>`, `<span>`, or `<body>` tags.