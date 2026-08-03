#### Inter-VLAN routing

- Has to have different networks under the switch
- Connection between switch and router, is a trunk and using subinterfaces on the router
	`int f0/0.<VLANID>`
	`encapsulation dot1q <ID>`
	`ip add`
- No need to routing as all vlans are networks connected directly and if only one router
- To stop VLANs from seeing each other again
	- Shutdown the whole router
	- Shutdown the whole divided interface f0/0

**Pros:**
1. Less Broadcast
2. Having the shutdown option