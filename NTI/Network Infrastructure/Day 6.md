- D class in CIDR (224.0.0.0->239.255.255.255) is assigned to Apps as they use multicast
- Least Metric is the Primary for Default gateway

### IPv6
- First 3 periods -> Global Routing Prefix
	- The very first 3 bits are fixed:
		1. 001 -> Privarte
		2. 200 -> Public
	- The very next 3 bits -> Regional Registery
	- The remaining of the first 8 bits (very next to the first 6) -> Defines ISP 
	- The whole 2nd period -> Site(central)/Customer ID
- 4th Period -> Subnet ID
- Last 4 periods -> Interface ID
	- Can be manually or dynamically configured using EUI-64
	- EUI-64 uses MAC address and converts it into 64-bits
	- Network and Network's Broadcast IPs can be assigned to Interfaces 

- Each device and each IP is assigned from the ISP and NAT will no longer be used
- FFxx: -> at the first hextet -> Multicast address
- Anycast is the new 'Beroadcast'
	- Broadcast: will keep sending for all even if it wants to target only one device but is unkown
	- Anycast: Stops once the destination is found