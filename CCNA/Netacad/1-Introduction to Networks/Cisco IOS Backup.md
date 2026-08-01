1. Add a server, give it an IP and enable `TFTP` from services tab
2. Choose what to backup:
	1. Startup: 
		   `copy startup-config tftp`
		   fill in server's IP
		   choose file source name
		   -> verify as it will be found on the in the tftp tab in services and now lets get it back form the server 
		   `copy tftp statup-config`
		   fill in server's IP
		   choose file source and destination name
	2. Flash that contains the IOS in .bin:
		   `show flash` to view it 
		   `copy flash tftp`
		   fill in server's IP
		   choose file source name
		   -> verify as it will be found on the in the tftp tab in services and now lets get it back form the server 
		   `copy tftp flash`
		   fill in server's IP
		   choose file source and destination name
		   -> to change the booting IOS on flash
		   `boot system <flash/tft> <sourcefilename`