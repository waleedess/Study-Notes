- HDLC the one responsible for routers to see each other. But, routing protocols like OSPF only shares ip route tables

- Switches work fine without initial configuration but routers need it 

- To remote to a switch i need to assign it an IP even though it works with MAC address and has no interfaces IP
	=> The IP is given to the whole switch to get recognized not to use it in its function
		`int vlan 1`
		`ip add <IP> <subnetmask>`