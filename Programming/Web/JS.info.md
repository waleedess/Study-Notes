# 1st Chapter

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
- **As a rule**, only the simplest scripts are put into HTML. More complex ones reside in separate files 
	- The benefit of a separate file is that the browser will download it and store it in its cache
	- Other pages that reference the same script will take it from the cache instead of downloading it, so the file is actually downloaded only once
	- That reduces traffic and makes pages faster

- If `src` is set, the script content is ignored
	- `<script src="/path/to/script.js"`
	  `alert(x); // the content is ignored, because src is set`
	  `</script>
	- The example above can be split into two scripts to work