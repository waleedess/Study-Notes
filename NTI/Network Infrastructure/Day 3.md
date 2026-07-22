#### Network Interface Card - NIC
- Digital = Analog Translation
- Uses RJ45/Antennas
- Contain the MAC address
- Access Methods:
	1. **Token Ring (Legacy)**: Only 1 device sends 
	2. **Ethernet**: Any device can attempt to send at any time (no token needed)
		- But if two transmit at once, a **collision** occurs and both back off and retry. Collisions are handled via CSMA/CD on shared media, or avoided entirely on modern switched networks
	![[Screenshot From 2026-07-22 04-26-54.png|225]]
- NIC Speeds
	1. Ethernet -> 10 Mbps
	2. Fast Ethernet -> 100 Mbps
	3. Gigabit Ethernet -> 1000 Mbps / 1 Gbps
	4. 10 Gigabit Ethernet → 10,000 Mbps / 10 Gbps
	5. Beyond that: 40G, 100G, and even 400G Ethernet exist today, mainly used in data centers and backbone infrastructure rather than typical desktop connections
	- **Note That** NIC speed do not determine network speed as network speed is tied to other speed like
		1. NIC speed
		2. Switch