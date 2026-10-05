- Cross-site scripting works by manipulating a vulnerable web site so that it returns malicious JavaScript to users
- If the user visits the URL constructed by the attacker, then the attacker's script executes in the user's browser, in the context of that user's session with the application. At that point, the script can carry out any action, and retrieve any data, to which the user has access
- Browser treats the code as trusted as it is did run inside the victim site's own origin so **xss defeats the Same Origin Policy - SOP**
- Severity will be as extreme as the permissions the user have
- Will be reflected directly as the input is injected to the HTML Document directly
- Tested at input fields, URL parameter and etc. by using either `alert()` or `print()` functions as a **POC** 

### Search for:

1. Input is not sanitized and special charachters like `<` are not prohibited
2. Input is displayed with no encoding