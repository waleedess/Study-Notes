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
====

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

-  `<input list="browsers" placeholder="Start typing...">`
   `<datalist>` => Enables an autocomplete or suggestion feature: as the user types into the input field, a drop-down list of matching options appears
   `<option value="Chrome">` 
   `</datalist>`
   ![[Pasted image 20261010043216.png]]
====
   
### Image Tags
---

- `<img src="" usemap="#MAPNAME" alt="">`
  `<map name="MAPNAME">` => is the container. Its `name` attribute gives it an identifier that the `img` tag connects to
  `<area shape="" coords="" href="" alt="">`
  `</area>` => defines one clickable region inside the map
  `</map>`

- `<canvas> </canvas>` => Used to draw graphics via JavaScript

- `<figure>` => Groups images, chart, code samples or diagram
  `<img src="">`
  `<figcaption> TEXT <figcaption>` => gives that content a caption
  `</figure>`

- `<picture>` => is a container that lets you offer several versions of the same image and lets the browser pick the best one for the current screen. It doesn’t display anything by itself
  `source media="(min-width: XXXpx) srcset="LargeImage.jpg"` => elements list the alternatives, each with a condition such as a screen width
  `source media="(min-width: XXXpx) srcset="MediumImage.jpg"`
  `<img src="SmallImage.jpg"` => Acts as the fallback
  `</picture>`

- `<svg width="120" height="120" xmlns="http://www.w3.org/2000/svg">` => is a container for vector graphics: shapes drawn with code instead of a bitmap image. Its contents are described with coordinates, so the graphic stays sharp at any size and can be styled with CSS or animated with JavaScript
  `<circle cx="60" cy="60" r="50" fill="tomato" />`
  `<rect />`
  `<line />`
  `</svg>`
====
  
### Audio & Video Tags
---

- `<audio controls src="">` => Control attribute shows the play and audio controlling buttons
  `<source src="song.mp3" type="audio/mpeg">` 
  `<source src="song.ogg" type="audio/ogg">` => lets you offer the same media in several file formats
  `TEXT` => Like alt
  `</audio>`
  
- `<video controls poster="">`
  `<source src="clip.mp4" type="video/mp4">`
  `<track kind="subtitles" src="subs-en.vtt" srclang="en" label="English" default>` => adds text to a video or audio element, most often subtitles or captions
  `TEXT`
  `</video>`
====

### Link Tags
---

- `<a href="" target="_blank">` `TEXT` `</a>` => `target="_blank"` opens the links in a new tab

- `<link rel="stylesheet or icon" href="">` => Connects the document to an external resource under `<head>` tag and does not display anything and the `rel` att. says what the linked file is

- `<nav>` => marks a section of the page that holds the main navigation links, like a menu.
  `<ul>`
  `<li><a href="index.html">Home</a></li>`
  `<li><a href="about.html">About</a></li>`
  `</ul>`
  `</nav>`
====

### List Tags 
---
![[Pasted image 20261018234409.png]]====

### Table Tags
---
![[Pasted image 20261018234606.png]]
====

### Style & Semantic Tags
---
![[Pasted image 20261019023626.png]]

- `<div> </div>` => groups content into a block-level section, usually for layout. it starts on a ==new line and takes up the full width available==

- `<span> </span>` => groups a small part of a line of text, so you can style just those words. Inline element, so it sits within the current line of text and ==only takes up as much width as its content==

- `<header> </header>` => holds introductory content for a page or section such as title or logo

- `<hgroup> </hgroup>` => groups heading e.g. `<h1>` with its subtitle e.g. `<p>`

- `<footer> </footer>` => groups closing content for a page or section such as contact or copyright details

- `<section> </section>` => groups related content, usually under its own heading

- `<search> </search>` => wraps search forms or features

![[Pasted image 20261019024534.png]]

- `<article> </article>` => holds self-contained piece of content that could stand on its own such as a blog post or news story

- `<aside> </aside>` => holds content related to the content but not essential to it such as sidebar or related links

- `<details>` => ==Creates a box that user can open or close for extra info==
  `<summary> </summary>` => gives visible heading
  `</details>` 

- `<dialog> </dialog>` => defines a dialog box or popup window and it is hidden until opened with JavaScript using `showmodal()` or `show()`

- `<data value="MACHINE"> HUMAN </data>` => links human-readable value to a machine-readable one