# Static

- To show routes 
=> `show ip route`
		-> c  => Directly connected
		-> S => Static/manually routed

- We have to ==set routes -*of the whole networks i want to go to*- for all intermediate routers== not only one

- To set route 
=> `ip route <targetnetworkip> <targetnetworksubnetmask> (<sourceInterface> or <destinationrouterIP>)`

- To set any unkown exit ot default gateway route
=> `ip route 0.0.0.0 0.0.0.0 (<sourceInterface> or <destinationrouterIP>)`
then `ip classless`

- Pros of Static Routing
	1. If a specific route is wanted
	2. VPN does not support dynamic routing
---
#### Routing vs Routed Protocols

| Routing                           | Routed                                                                           |
| --------------------------------- | -------------------------------------------------------------------------------- |
| Used between routers              | Assigned to an interface                                                         |
| Maintain and share routing tables | Determines method of felivery after determining the path by the routing protocol |
|                                   |                                                                                  |


---
# Dynamic