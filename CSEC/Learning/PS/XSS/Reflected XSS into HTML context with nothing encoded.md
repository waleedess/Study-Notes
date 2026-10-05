- Cross-site scripting works by manipulating a vulnerable web site so that it returns malicious JavaScript to users
- Browser treats the code as trusted as it is did run inside the victim site's own origin so **xss defeats the Same Origin Policy - SOP**
- Severity will be as extreme as the permissions the user have
- Will be reflected directly as the input is injected to the HTML Document directly
- Tested at input fields, URL parameter and etc. by using either `alert()` or `print()` functions as a **POC** 

### Search for:

1. Input is not sanitized and special charachters like `<` are not prohibited
2. Input is displayed with no encoding