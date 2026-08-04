# Ether Channel 

Is having multiple cables between 2 switches having these cables bundled to ==enhance bandwidth== and stop looping also stopping STP
- Switches use this bundle as one connection and one interface
- If one wire disconnects the bandwidth is lowered but no total disconnection and no spear (one falls the other starts), they are all working from the beginning

`int range f0/x - y`
`channel-group <1:6> <mode>`
- Modes:
	1. **Protocol:** LACP
		1. Active
		2. Passive (Default)
			- Passive - Passive => X, No EtherChannel
			- Active - Active => OK
			- Active - Passive => OK
	2. **Protocol:** PAGP: Cisco's
		1. Auto
		2. Desirable
			- Desirable - Desirable => OK
			- Desirable - Auto => OK
			- Auto - Auto => X, No EtherChannel
	3. **Manual**

# PVST

`spanning-tree mode pvst`

# Rapid-PVST

`spanning-tree mode rapid-pvst`

# Redundancy

Works on L3 switch
- L3 Switch act as a LAN router, no WAN
- Router routes Both

