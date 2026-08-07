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

- To set Secondary route
=> `ip route <targetnetworkip> <targetnetworksubnetmask> (<sourceInterface> or <destinationrouterIP> 2` -> ==That 2 or 3 or whatever its rank is the key==

- Pros of Static Routing
	1. If a specific route is wanted
	2. VPN does not support dynamic routing
---
# Dynamic

#### Routing vs Routed Protocols

| Criteria     | Routing                                                                                                                                                                                                                                                    | Routed                                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------- |
| **Usage**    | Used between routers                                                                                                                                                                                                                                       | Assigned to an interface                                 |
| **Function** | Maintain and share ip routing tables                                                                                                                                                                                                                       | Determines method of felivery after determining the path |
| **Notes**    | Classified into:<br><br>1. IGPs: Interior Gateway Protocols<br>2.EGPs: Exterior Gateway Protocols<br><br>==And into:==<br><br>1. Classful Routing Protocols<br>2. Classles Routing protocols<br><br>==And into==<br><br>1. Distance vector<br>2. Linkstate |                                                          |


##### IGPs
- Used with networks that follow a specific lone autonomous system
	- Each ISP is assigned an autonomous system by IANA that keeps its passwords recognized

- ==Shares Public and Private IPs== from the routing table  

- Examples
	1. RIP
	2. EIGRP
	3. OSPF

##### EGPs
- Used to connect networks with different autonomous systems
	- Link ISPs/Large companies with each other

- ==Shares Only Public IPs== from the routing table  

- Examples
	1. BGP

##### Classful 
- Do not include the subnet mask with route advertisement
	- Sends only the IP and the subnet mask is concluded
	- Do not support VLSM subnetting

- Legacy and no longer used, examples:
	1. RIP v1
	2. IGRP  

##### Classless
- Sends the Subnet mask with the IP

- Examples:
	1. EIGRP
	2. RIP v2
	3. OSPF
	4. IS-IS

##### Distance Vector
- Exchange routing tables with neighbour, the neighbour exchange with its neighbour, and so on

- Examples
	1. RIP
	2. EIGRP - Advanced Distance Vector

##### Link State
- Routers choose a designated router router
	- Then if a router gets new network it shares it with onlt the DR
		- The DR multicasts with OSPF's 

- Faster than Distance Vector

- Examples 
	1. OSPF
   
   ****
# Dynamic Routing Protocols

### RIP 

- Has 2 versions: Legacy ~~v1~~ , v2
  
- Chooses path according to the least hop count
	- Max hop count is 15, the 16 is unreachable

- Sends the routing table to neighbours every 30sec

-  If the hop count metric is equal for paths, the RIP will load balance with maximum of 6 equal paths, default is 4 paths

- Keeps sending hello packets to neighbours
	- ==V2 multicasts news with IP: 224.0.0.10==


|     | **Pros**              | **Cons**                                                   |
| --- | --------------------- | ---------------------------------------------------------- |
|     | - Light<br>- Standard | - Max hop count is low<br>- Chooses path acc. to hop count |

###### Activation Steps:
1. `router rip`
2.  `v 2` -> after entering RIP config
3. `network <classfulnetworkip>` -> Attached networks to the router without subnetmasks
	 **Passive Interface**: to allow router receive but not send updates via specific interface
 4. `passive-interface <serial0>`
	**Split Horizon**: if a router gets new network from interface 1, it will not send it back out of it
   
   - Debug and verbose
=> `debug ip rip` -> On
=>`undebug all` -> Off
to see routing tabels shared every 30 sec

---
### Enhanced IGRP - EIGRP

- Chooses path according to Bandwidth and delay
	- Delay is hop count's time

- Uses DUAL - Diffused Update Algorithm
	- Sets primary path and secondary Feasable successor 
	- Not calculates when the first fails. Tha backup was calculated from the beginning
	![[Pasted image 20260807193448.png]]


- Have Load Balance with max of 6 and default of 4
	- But can -*with variance config*- ==balance unequal paths==

- Max hop count = 255, default is 100
  
- Hello packets are sent every 5sec => LAN
	- Every 60 sec => WAN
	- ==Multicasts news also at IP: 224.0.0.10==
  
###### Activation Steps: 
1. `router eigrp <autonomous number>` -> autonomous number shoul be the same
2. `network <classfulnetworkip>` -> Without subnetmask
	**Hello Packets** configured ==from the 2 interfaces ==connected, tries 3 times totalling 15 holdtime secs before asssuming that the conncection is down by default
3. `ip hello-interval <autonomous numeber> <secs>`
4. `ip hold-time eigrp <autonomous number> <secs>`

---


---

**Administrative** **Distance**
- ==If a router is set up to work with 2 different routing protocols, the one with lower administrative distance will win==
	- The second or ==higher== administrative distance will only work if the first is unavailable

- **Default Administrative Distances**:
	- Dircetly connected -> 0
	- Static route -> 1
	- EIGRP -> 90
	- ~~IGRP -> 100~~ => Legacy
	- OSPF -> 110
	- RIP -> 120
  
**Show**
- `show ip <protocol> neighbours`
- `show ip <protocol> topolgy`
- `show ip route <protocol>`
- `show ip protocols`
- `show ip <protocol> traffic`
  
**Routing not assigned networks**
- Networks that are not assigned to an interface will not be routed using routing protocols
- The fix is a virtual interface "loopback"
	`int loopback <interface number>`
	`ip add <networkgateway> <subnetmask>` -> .1 of the needed network to be added
	`no shut`

**Auto-summary**
`no auto-summary`
