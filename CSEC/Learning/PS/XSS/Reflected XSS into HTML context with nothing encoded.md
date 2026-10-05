- Cross-site scripting works by manipulating a vulnerable web site so that it returns malicious JavaScript to users
- If the user visits the URL constructed by the attacker, then the attacker's script executes in the user's browser, in the context of that user's session with the application. At that point, the script can carry out any action, and retrieve any data, to which the user has access
- Browser treats the code as trusted as it is did run inside the victim site's own origin so **xss defeats the Same Origin Policy - SOP**
- Severity will be as extreme as the permissions the user have
- Will be reflected directly as the input is injected to the HTML Document directly
- Tested at input fields, URL parameter and etc. by using either `alert()` or `print()` functions as a **POC** 

### Impact 

- Perform any action within the application that the user can perform
-  View any information that the user is able to view.
- Modify any information that the user is able to modify.
- Initiate interactions with other application users, including malicious attacks like:
	1. Website Defacement
	2. Session Hijacking
	3. Malware Injection that might escape the browser and run on the OS natively
	4. Redirection to other malicious websites

### Search for:

1. Input is not sanitized and special charachters like `<` are not prohibited
2. Input is displayed with no encoding

--- 
 
-  The need for an external delivery mechanism for the attack means that the impact of reflected XSS is generally less severe than stored XSS, where a self-contained attack can be delivered within the vulnerable application itself
 - Reflected XSS arises when an application takes some input from an HTTP request and embeds that input into the immediate response in an unsafe way. With stored XSS, the application instead stores the input and embeds it into a later response in an unsafe way. 