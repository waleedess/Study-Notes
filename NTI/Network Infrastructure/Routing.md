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
# Dynamic

#### Routing vs Routed Protocols

| Criteria     | Routing                                                                                                                                                                                      | Routed                                                   |
| ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------- |
| **Usage**    | Used between routers                                                                                                                                                                         | Assigned to an interface                                 |
| **Function** | Maintain and share ip routing tables                                                                                                                                                         | Determines method of felivery after determining the path |
| **Notes**    | Classified into:<br><br>1. IGPs: Interior Gateway Protocols<br>2.EGPs: Exterior Gateway Protocols<br><br>==And into:==<br><br>1. Classful Routing Protocols<br>2. Classles Routing protocols |                                                          |
###### IGPs
- Used with networks that follow a specific lone autonomous system
	- Each ISP is assigned an autonomous system by IANA that keeps its passwords recognized

- ==Shares Public and Private IPs==

- Examples
	1. RIP
	2. EIGRP
	3. OSPF

###### EGPs
- Used to connect networks with different autonomous systems
	- Link ISPs/Large companies with each other

- ==Shares Only Public==

- Examples
	1. BGP


###### Classful 
- Do not include the subnet mask with route advertisement
- 