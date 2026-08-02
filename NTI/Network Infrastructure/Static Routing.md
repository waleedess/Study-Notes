- To show routes 
=> `show ip route`
		-> c  => Directly connected
		-> S => Static/manually routed

- We have to ==set routes -*of the whole networks i want to go to*- for all intermediate routers== not only one

- To set route 
=> `ip route <targetnetworkip> <targetnetworksubnetmask> (<sourceInterface> or <destinationrouterIP>)`

- Pros of Static Routing
	1. If a specific route is wanted
	2. VPN does not support dynamic routing