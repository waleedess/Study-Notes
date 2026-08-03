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

- Secure MAC:
	1. Static 
	2. Dynamic
	3. Stikcy

- Error Disable
	 => Restart the interface to reset![[Pasted image 20260803121514.png]]

- How to enable
`int f0/0`
`sw mode access` => Cannot be enabled on trunk 
`sw port-security`
`sw port-security maximum 1->132` => if too much => use sticky MACs taking the first x MACs after the boot as you need to give the whole below command for each MAC 
`sw port-security mac-address xcvbvcx`
`sw port-securityc violation <rest/prot/shut>`

- `show port-security` or `show port-security interface f0/0`
---
# Spannig Tree Protocol - STP

- Root Bridge is assigned to the least priorty numbered switch 
	- If priorities are equal, assigned to the least MAC
	- Root has all of its conected interfaces are active, not shuten down, not half and half(non-designated) => ==Designated port== 

- Other switches(bridges) choose the path between them according to bandwidth cost
	![[Pasted image 20260803131308.png]]
	- 100mbps, 2 hops => X
	- 100mbps, 1 hop => Chosen path even if the same bandwidth

`show spanning-tree`
-> Root ID
-> Bridge(the opened CLI) ID
-> Interfaces (Designated/non), Cost and etc.

- **Bridge Protocol Data Unit - BPDU**
	- Passes even through non-designated or closed paths
	- Determines the topology and it is the packet of STP

- **Port states**
	1. Disables: no cable or shutdown
	2. Blocked: LIsten to BPDU but do not transmit it and no data takes 20 sec
	3. Listening: Process BPDU forwards after 15s, no data
	4. Learning: Process BPDU forwards again after 15s, no data and drops recivied frames
	5. Forwarding: Data Transmission

- Ports connected to end devices as PC or server do not need STP so it is better to switch it off on that specific port using:
  `int f0/10`
  `spanning-tree portfast`=> Disable STP
- Rapid PVST => Fast STP mode
  
- **PVST+**
  
`f0/1`
`spanning-tree vlan 20 root primary`
`spanning-tree vlan 10 root secondary`
`f0/2
`spanning-tree vlan 10 root primary`
`spanning-tree vlan 20 root secondary`

Or 
`spanning-tree vlan 10 priorty xxxx`
`spanning-tree vlan 20 priorty yyyy`