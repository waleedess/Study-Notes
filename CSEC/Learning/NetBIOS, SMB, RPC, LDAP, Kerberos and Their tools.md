

#### Intro

---
# Protocols' Foundations

#### NetBIOS: Network Basic Input/Output System

- Allows applications on separate computers to communicate and share resources within a LAN. 
- Designed fundemntally as Peer-to-Peer
- Operating Primarily at the **Session Layer of OSI** = **Application Layer of TCP/IP** -> NBT *NetBIOS over TCP/IP*
- Superseded by more **secure & scalable** protocols like DNS & SMB
  
###### Ports and Usages

| Port   | Name                       | Usage                                                                                          | Notes                                                                         |
| ------ | -------------------------- | ---------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| U: 137 | NBNS: NetBIOS Name Service | Name Registration & Resolution                                                                 | - Primitive version of DNS<br>- Names are broadcasted to ensure no duplicates |
| U: 138 | NetBIOS Datagram Service   | Connection-less and Fast Communication                                                         | - Broadcasting and Windows Network Neighborhood discovery features            |
| T: 139 | NetBIOS Session Service    | Manages Connection-oriented, Reliable Communication for data transfer between 2 specific hosts | - Used to carry Leagcy SMB -*before SMB had its own T: 445 port*-             |
- **All of its ports and usages are considered as high-risk legacy protocols**
  
---
#### SMB: Server Message Block

- Enabling applications on a computer to **Read/Write** to files, also request services from server programs in the network 
- Client-Server Communication

###### versions

| Version | Windows Version | Port              | OSI Layers                                                                                     | TCP Layers | Notes                                                           |
| ------- | --------------- | ----------------- | ---------------------------------------------------------------------------------------------- | ---------- | --------------------------------------------------------------- |
| SMBv1   |                 | T: 139 of NetBIOS | 7: SMB<br>->6: NetBIOS Session Service<br>>5: NetBIOS Session Service                          | 4          | - Responsible for the 2 massive attacks: Eternal Blue, WannaCry |
| SMBv2   | Visita          | T: 445            | 7->4<br>- Hands requests straight down to TCP Layer, **Completely Skipping** the middle layers | 4,3        |                                                                 |
| SMBv2.1 | 7               | T: 445            | 7->4<br>- Hands requests straight down to TCP Layer, **Completely Skipping** the middle layers | 4,3        |                                                                 |
| SMBv3   | 8               | T: 445            | 7->4<br>- Hands requests straight down to TCP Layer, **Completely Skipping** the middle layers | 4,3        |                                                                 |
| SMBv3.1 | 10              | T: 445            | 7->4<br>- Hands requests straight down to TCP Layer, **Completely Skipping** the middle layers | 4,3        |                                                                 |



---
#### RPC: Remote Procedure Call

- Allows programs to **execute** a subroutine or procedure on another computer over network as if it was a local function call
- Client-Server Inter-Process Communication
  
###### Ports and Usages

| Port               | Name                                  | OSI Layers                                          | TCP/IP Layers | Usage                                                                                                                                                                     |
| ------------------ | ------------------------------------- | --------------------------------------------------- | ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| T/U: 135           | RRC Endpoint Mapper                   | Layer 5: Session                                    | 4             | - Registers, tracks and looks up endpoints<br>- Handle initial handshake client -> server                                                                                 |
| T/U: 49152 – 65535 | Dynamic RPC Workers / Ephemeral Ports | Layer 4: Transport<br>(*Carrying Layer 7 payloads*) | 3             | - Actual data transmission and function execution                                                                                                                         |
| T: 445             | SMB                                   | Layer 7: Application                                | 4             | - Relies on SMB to handle application-layer authentication and transport encapsulation                                                                                    |
| T: 80/443          | GRPC - *RPC over HTTP/S*              | Layer 7: Application<br>Layer 6: Presentation       | 4             | - Payloads serialized using (JSON or Protocol Buffers) and sent natively inside HTTP/S application streams<br>- Serialization/NDR Network Data Representation are Layer 6 |
- **Due to RPC's dynamic nature it is difficult to firewall due to Dynamic worker ephemeral ports** -> To have some security force RPC to use tightly controlled, static range of ports and restrict the port 135 **TCP & UDP**

---
#### LDAP: Lightweight Directory Access Protocol

- Used for querying and managing distributed directory information services over an IP network
- Organizes data such as user credentials, groups, accounts, organizational units into a tree-like structure called **Directory Information Tree - DIT** 
- LDAP servers are the engine for centralized identity and access management (IAM) as it utilizes **read-heavy** architecture that allows client applications to rapidly search, authenticate and authorize users across enterprise networks
- Operates at the Application layer of both OSI & TCP/IP

###### Ports and Usages

| Port     | Name                           | OSI Layers                                                     | TCP/IP Layers | Usage                                                                                                                                                  | Notes                                                                                                               |
| -------- | ------------------------------ | -------------------------------------------------------------- | ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------- |
| T/U: 389 | Standard LDAP                  | Layer 7: Application                                           | 4             | - Standard directory queries, modifications, and authentication requests.                                                                              | - **Cleartext** *(unencrypted)* by default<br>- Frequently upgraded to an encrypted TLS session using **StartTLS**. |
| T: 636   | LDAPS<br>*(LDAP over SSL/TLS)* | Layer 7: Application<br>Layer 6: Presentation *for encryption* | 4             | - It serves the exact same purpose as port 389 (searching, binding, altering directory objects), but it mandates encryption from the very first packet |                                                                                                                     |
| T: 3268  | Global Catalog LDAP            | Layer 7: Application                                           | 4             | - Used to query the Global Catalog with Active Directory                                                                                               |                                                                                                                     |
| T: 3269  | Global Catalog LDAPS           | Layer 7: Application<br>Layer 6: Presentation *for encryption* | 4             | - Used to query the Global Catalog with Active Directory                                                                                               |                                                                                                                     |


---
#### Kerberos Protocol

- Kerberos is a ticket-based authentication protocol designed to establish secure identity verification over an unsecure, packet-sniffed network fabric
- Relies on a centralized network service called the **Key Distribution Center (KDC)** to issue time-stamped, cryptographically sealed tokens known as Tickets. These tickets are embedded into the payloads of network packets, allowing distributed client-server applications to achieve mutual authentication ==without exposing passwords to interception, replay attacks, or man-in-the-middle exploits==

###### Ports & Usages


| Port   | Name                        | Usages                                                         | Note                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| ------ | --------------------------- | -------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| U: 88  | Key Distribution Center     | Gateway for all Kerberos and KDC traffic                       | - Default choice as Kerberos is mainly stateless, fast and has low network overhead                                                                                                                                                                                                                                                                                                                                                                                 |
| T: 88  | Key Distribution Center     | Gateway for all Kerberos and KDC traffic                       | - Fallback / Large payload choice<br><br>-> If a user belongs to a large number of security groups, their authorization data (PAC - Privilege Attribute Certificate) grows significantly. If the Kerberos response packet exceeds the standard Maximum Transmission Unit (MTU) size—typically **1465 bytes** for Kerberos—the protocol automatically switches (**falls back**) from UDP to TCP port 88 to ensure reliable, fragmented delivery without packet loss. |
| U: 53  | DNS SRV records             | Discover _where_ the KDC servers actually live on the network. | - Before a client can send a packet to port 88, it uses DNS SRV records (`_kerberos._udp.domain.com`) to discover<br>                                                                                                                                                                                                                                                                                                                                               |
| T: 123 | NTP - Network Time Protocol | Prevent replay attacks                                         | - Kerberos tickets are cryptographically bound to timestamp, If the local machine clock and the KDC clock differ by more than **5 minutes** (the default skew), Kerberos packets are completely rejected by the network.                                                                                                                                                                                                                                            |

**DNS SRV Records**

- It doesn't just tell a computer _where_ a server is *-by mapping host name to IP-* it tells the computer ==which specific service== it runs and ==which port== it is listening on.
- An SRV record uses a highly structured format so that protocols (like Kerberos or LDAP) can read them programmatically. A typical record looks like this:
	  `_service._proto.name. TTL class type priority weight port target.` 
  -> `_kerberos._udp.cyberus.local. 3600 IN SRV 0 100 88 dc01.cyberus.local.`
---
###### Comparison 

---
# Enumeration Tools

#### nbtscan

---
#### smbclient & smbmap

---
#### enum4linux/-ng

---
######  Usage Guide
