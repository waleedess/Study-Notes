
# 1. What is Google Dorking
---
> => It is the practice of advancing Google search queries using specific operators to find specific information that is not surfaced by a normal search 

# 2. Operators 
---
- **`site:`** -> restricts results to a specific domain or subdomain
- **`inurl:`** -> searches for a keyword appearing in the URL
- **`intitle:`** -> searches for a keyword appearing in the page title
- **`intext:`** -> searches for a keyword appearing in the body text of the page
- **`filetype:`** -> searches for files of a specific extension (e.g. pdf, sql, log)
- **`ext:`** -> same function as `filetype:`, alternate syntax
- **`cache:`** -> shows Google's cached version of a page
- **`allinurl:`** -> like `inurl:`, but all listed keywords must appear in the URL
- **`allintitle:`** -> like `intitle:`, but all listed keywords must appear in the title
- **`allintext:`** -> like `intext:`, but all listed keywords must appear in the body text
- **`link:`** -> finds pages that link to a specific URL
- **`related:`** -> finds sites related to a given domain
- **`"..."`** (quotes) -> searches for an exact phrase match
- **`-`** (minus) -> excludes a term from the results
- **`*`** (wildcard) -> acts as a placeholder for unknown words in a phrase
- **`OR`** / **`|`** -> returns results matching either term
- **`AND`** -> returns results matching both terms (often implicit by default)
- **`numrange:`** -> searches for a specific range of numbers
- **`define:`** -> returns a definition of a term
- Wildcard `*`


# 3. What can i find or when to use?
---
#### 1. Subdomain Passive Recon

- `site:*.example.com`

> => Enumerate subdomains indexed by Google without touching the target directly. Usually the first step in mapping attack surface.


#### 2. Service/Technology Discovery (+ Error/Stack Trace Discovery)

- `inurl:app/kibana`
- `inurl:phpmyadmin`
- `intitle:jenkins`
- `intext:"Warning: mysql_connect()"`
- `intext:"stack trace"`

> => Identify what software/services are running and publicly reachable (dashboards, admin tools), then fingerprint the tech stack, file paths, and DB info via leaked error messages — useful for matching known CVEs to the version in use.

#### 3. Indexed Sensitive Files (+ Directory Listing + Document/Metadata Discovery)

- `ext:php` / `filetype:php`
- `ext:log` / `filetype:log`
- `ext:asp` / `filetype:asp`
- `ext:xml` / `filetype:xml`
- `ext:bak` / `filetype:bak`
- `ext:cfm` / `filetype:cfm`
- `ext:pl` / `filetype:pl`
- `ext:jsp` / `filetype:jsp`
- `ext:sql` / `filetype:sql`
- `intitle:"index of /" "parent directory"`
- `site:example.com filetype:pdf`
- `filetype:docx intext:"confidential"`
  
> => Hunt for accidentally indexed/exposed files — leaked credentials, API keys, DB dumps, backup files, config files, open directories, and internal documents (which can reveal usernames, org structure, email formats).

#### 4. Management Interface Discovery (+ Login/Portal Discovery)
   
- `inurl:admin`
- `inurl:login`
- `intitle:"index of /admin"`
- `inurl:login intitle:"VPN"`
- `inurl:/owa/` (Outlook Web Access)
  
> => Find weakly protected admin panels, login portals, and remote access entry points (VPNs, webmail, RDP gateways) — these become targets for credential attacks or known-vuln exploitation.
 