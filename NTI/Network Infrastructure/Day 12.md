# Inter-VLAN routing

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
   
#### VLAN Trunking Protocol - VTP

- Configure on 1 'Domain' switch
  `vtp domain <name>`
	- To turn off => `no vtp` 
  
- Switches share a VTP domain, VTP advertises that change to all other switches in the domain over trunk links
	- Each advertisement carries a revision number — switches only accept updates with a higher revision number than what they already have

- VTP has a known weakness — a rogue switch with a higher revision number can join the domain and wipe out the VLAN database, causing a network-wide outage. This is why many networks either disable VTP or run it in transparent mode, and use VTP passwords

- VTP Modes: `vtp <mode>`
	1. **Server**
		- Create, modify and delete
		- Sends and forwards advertisment
		- Synchs VLAN config
		- Saves configs in NVRAM
	2. **Client**
		- Cannot create, change or delete
		- Forward advertisments
		- Synchs VLAN config
		- Does not save, loads with rach boot from the server
	3. **Transparent**
		- Creates, modifies and delete local VLANs
		- Forwards advertismets
		- Does not sync VLAN configs
		- Saves configs in NVRAM
			=> Do not take or give, only passes

- **Revision number**
	- It is the number of actions done in the VLAN
	- The higher it is on a switch the more overwrititng ability that this switch has
---
# Port Security

