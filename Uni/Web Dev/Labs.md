# HTML

### Formatting Tags
--- 
- `<abbr title="Xyz"> X </abbr>` => Defines an abbreviation or an acronym (e.g., "HTML", "CSS", "NASA"). Using the `title` attribute provides the full expansion when hovering over the element
  
- `<address> </address>` => Supplies contact details for the author or owner of a document or article. Browsers typically render the text inside `<address>` in italics and add a line break before and after
  
- `<bdi> </bdi>` => Isolates a span of text that might be formatted in a different direction (e.g., right-to-left languages like Arabic or Hebrew) from surrounding text formatted left-to-right (or vice versa)
  
- `<bdo> </bdo>` => Renders text backwards
  
- `<blockquote> </blockquote>` => Defines a section or block of text quoted from another source. Browsers typically display blockquotes indented from both margins
  
- `<cite> </cite>` or `<dfn> </dfn>`=> Defines the title/definition, Browsers typically render the content inside `<cite>` in italics
  
- ==`<code> </code>`== or `<kbd> </kbd>` or `<pre> </pre>` or `<samp> </samp>` => Snippet of computer code or programming syntax. Browsers typically render code using a fixed-width (monospace) font
  
- `<del> </del>` or `<s> </s>`=> Represents text with ~~strikethrough~~
  
- `<ins> </ins>` & `<u> </u>` => Represents text with Underline
  
- `<mark> </mark>` => Represents text highlighted
  
- (`<b> </b>` or `<strong> </strong>`), `<i> </i>` & `<q> </q>` => Bold, Italic & quoted texts
  
- ==`<p>Storage capacity used: <meter value="0.75" min="0" max="1">75%</meter></p>`== => Defines a scalar measurement within a known range, functioning as a gauge. It is often used to show disk usage, relevance scores, or static values ![[Pasted image 20261010035257.png]]
  
- `<progress value="60" max="100">60%</progress>` ![[Pasted image 20261010035637.png]]
  
- `<small> </small>` => Represents smaller text
  
- `<sub> </sub>` => Defines subscripted text. Subscripts appear half a character below the normal baseline and are usually displayed in a smaller font (Chemistry)
  
- `<sup> </sup>` => Defines superscripted text. Superscripts appear half a character above the normal baseline and are usually displayed in a smaller font (Power/Exponential)
  
- `<template> </template >` => Defines a container for content that should be hidden when the page loads. The HTML inside a template is ignored by the browser initially, but it can be cloned and inserted into the document later using JavaScript
  
- `<time> </time>` => Defines a specific time or datetime. The optional `datetime` attribute provides a machine-readable format for search engines and browsers
  
- `<var> </var>` => Defines a variable, typically used in mathematical expressions, programming contexts, or scientific formulas. Browsers usually render this in an italic font style
  
- `<wbr> </wbr>` => Defines a possible line-break. It tells the browser where it is safe to break a long word if it needs to wrap onto the next line


### Forms and Input Tags
---
![[Pasted image 20261010041828.png]]![[Pasted image 20261010041837.png]]
- `<textarea rows="x" cols="y" placeholder="default text here"> </textarea>` => Defines a multiline input control (text area), Unlike a standard single-line `<input type="text">`

-  `<select>` => Defines a drop-down list
	`<optgroup label="">` => Defines a group of related options within, label attribute is a must to specify the title of the group
	`<option value="xxx"> XXX </option>` => Defines an option in a drop-down list
	`</optgroup>`
	`</select>`
	![[Pasted image 20261010042435.png]]

- ``