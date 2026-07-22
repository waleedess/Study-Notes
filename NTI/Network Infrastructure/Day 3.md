#### Network Interface Card - NIC
- Digital = Analog Translation
- Uses RJ45/Antennas
- Contain the MAC address
- Network Access Methods:
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
	- **Note that** overall network speed isn't determined by any single component alone. but, it's determined by the **slowest** link in the path, which could be the NIC, the switch port, the cable, or another device along the way.
		1. NIC speed
		2. Switch's Port speed
		3. Cable speed and Category
- NIC Types
	1. **Normal NIC**
		- NIC is only used for network communication _after_ the OS has already loaded
	2. **(Super) Remote Boot NIC**
		- This is commonly used with **PXE (Preboot Execution Environment)** for diskless workstations, imaging labs, or thin-client setups

---
### Network Devices

###### Repeater / Extender 
- Network device used to regenerate a signal - *analog or digital -* that was distorted by transmission loss due to attenuation or distance whether connected wired or wireless
- Does **Not** perform intelligent routing
- Largely replaced by switches in modern wired LANs, but still commonly used in wireless networks and long-distance links
- Can be replaced by old DSL routers by closing DHCP and using WDS (Wireless Distribution System) service open on **both** intermediate (old) and Destination (main) router

###### Hub 
- Concentrate connections as the take a group of hosts and allow the network to see them as a single unit as all physical ports are connected to the same wire inside the device
  *Done passively without any other effect on data transmission*
- Can regenerate signals
- Slow due to Broadcasting
- Not all devices receive the broadcasted message if the Mac was not a broadcast (**FF:FF:FF:FF:FF:FF** (12 F's))
  any other mac address -> only that mac address' device receive it and other devices **drop the packet**

###### Bridge 
- Converts network transmission data formats as well as perform basic data transmission management
- Provides connections between LANs
- Perform a check on data to determine it should cross the bridge or not

###### Router
- Have all capabilities of devices as they can
	1. Regenerate signals
	2. Concentrate multiple connections
	3. Convert data transmission formats
	4. Manage data transfers
	5. Connect to WANs