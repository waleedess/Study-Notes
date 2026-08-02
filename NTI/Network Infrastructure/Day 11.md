- HDLC the one responsible for routers to see each other. But, routing protocols like OSPF only shares ip route tables

- Switches work fine without initial configuration but routers need it 

- To remote to a switch i need to assign it an IP even though it works with MAC address and has no interfaces IP
	=> The IP is given to the whole switch to get recognized not to use it in its function
		`int vlan 1`
		`ip add <IP> <subnetmask>`

- Layer 2 Devices, that operate and understand MAC
	1. NIC
	2. ~~Bridge~~ => Legacy -*used with hubs*-
	3. Switch

- Switch packet forwarding Methods
	1. **Store-and-forward**:
		- Waits for bits to form a frame then read the MAC and decide
	2. **Cut-through**
		- Sends each bit

- Switching is can be
	1. Symmetric:
		- Only liks switches with ports assigned the same bandwidth
	2. Asymmetric
		- Free connection but operates as the least bandwidth

- Hierarchical Network Design
	1. **ACCESS**: with end devices
	2. **DISTRIBUTION**: with ACCESS switches
		- Each ACCESS connects with 2 DIST.
	3. **CORE**: with DISTRIBUTION switches
		- Each DIST. connects with 2 CORE
	=> ==DIST., CORE is better to be L3 switches==

- duplex auto -> send and recive
- half duplex -> only either way
- speed auto -> adjusts to wire
	- if not auto and assigned 10 or 100 -> the other connection should match, if not, no connection

- `ip default gateway <router's IP>` rather than setting the default gateway at each device that is already connected to the switch

- Each VLAN should have an IP to enable each VLAN-connected device to connect remotely with the switch

- Having two switches with VLANs 1 and 10
  -> Devices within VLAN 1 can communicate with each other across the switch but VLAN 10 cannot
  -> As the ports between the switches will be assigned to VLAN 1 as default, if i changed it to VLAN 10, only 10's will communicate
  
- Trunking mode `switchport mode trunk` => Passes the packet of all VLANs as `switchport access` mode allows it to pass packets and be assigned to a single VLAN
	- Should be atleast at one side and the other will compensate, the better to configure it both sides
	- Trunk links: the source switch adds the trunk number to the frame so when the destination knows which VLAN to pass it to
	- Trunking Protocols:
		1. **ISL**:
			- Encapsulated
			- Independent
			- Of Cisco
		2. 802.**1Q**
			- Tagged
			- Dependent
			- Open Source
	- Native VLAN `switchport mode trunk native <vlan id>` -*VLAN 1 by default*- and the native VLAN packet's is untagged
		- This helps much with unmanagment switch that has no VLANs
	- `switchport trunk allowed vlan id1,id2,id3 ` -> to make a list of only allowed VLANs over trunk
  