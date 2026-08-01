- Requires: 
	- Hostname
	- Router username and secret: `username a7a privilege 15 secret a7teen` 
		- Privilege 0->15(admin & default)
	- Domain name: `ip domain name a7a.com` *-malosh ay lazma bs lazem akhro .com-*
	- Encryption: `crypto key generate rsa` and choose the bits 512 and multiples.
		- The higher the bits, the higher security but it counts from the bandwidth
	- Line password: 
	  `line vty 0 15` -> number of session 0=1 up to 15=16 
	  `pass a7a`
	  `transport input ssh`
	  `login`
	   