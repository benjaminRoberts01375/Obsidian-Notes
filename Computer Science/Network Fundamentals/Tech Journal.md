# Open Sourced Interconnected (OSI) Model
- Data starts from device 1, goes down, then up to device 2

| Layer | Name (Device 1) | Description                                   | Name (Device 2) | Layer |
| ----- | --------------- | -------------------------------------------- | --------------- | ----- |
| 7     | Application     | Basic protocols: HTTP(S), FTP)               | Application     | 7     |
| 6     | Presentation    | Translating binary into data: ASCII, Unicode | Presentation    | 6     |
| 5     | Session         | Activity connections (1 per request)         | Session         | 5     |
| 4     | Transport       | Ports and data integrety: UDP, TCP           | Transport       | 4     |
| 3     | Network         | Routers and logical stuff: IPs               | Network         | 3     |
| 2     | Datalink        | Physical stuff: MAC addresses, NICs, ARP     | Datalink        | 2     |
| 1     | Physical        | Wires, traces, hubs                          | Physical        | 1     |

# Fundamental Command Line Commands

#### `ipconfig` and `ipconfig /all`
- Displays information about a Windows PC's network interfaces and connections

#### `nslookup`
- Find IP address that a URL links to

#### `ping <address>`
- Checks to see if `Device A` can connect to `Device B`

#### `tracert <URL|IP>`
- Checks connectiont to each router along route to `Device B`

# IP Basics
## IP Structure and Uses
#### IPv4
- In the format of xxx.xxx.xxx.xxx
- A 32-bit address comprised of 4 8-bit numbers visually separated by periods.
	- First 8-bit number is the **network number**
	- Everything after is the **host number/address**
- Quickly running out of public IPs
- **Class A**
	- Governments, extremely large networks
	- Range of IPs: `0.0.0.0` to `127.255.255.255`
	- Maximum number of addresses = $2^{24}$ = 16,777,214
- **Class B**
	- Mid-sized networks, companies, universities…
	- Range of IPs: `128.0.0.0` to `191.255.255.255`
	- Maximum number of addresses = $2^{16}$ = 65,534
- **Class C**
	- Small networks
	- Range of IPs: `192.0.0.0` to `223.255.255.255`
	- Maximum number of addresses = $2^{8}$ = 254
- **Class D**
	- Multi-cast groups
	- Range of IPs: `224.0.0.0` to `239.255.255.255`
	- Maximum number of addresses isn’t applicable

#### IPv6
- (Typically a) physical IP format
- In the format of xx:xx:xx:xx:xx
	- 6 groups of up to 2 octets
		- Usually only 6 groups of 1 octet
	- Numbers from 0 to 256 or 65535
	- Separated by colons, not periods

#### Media Access Control (MAC) Address
- Physical/Hardware address
- Octets
	- First 3 octets specify manufacturer
	- Second 3 octets are for active device
	- MAC Addresses do get reused
- Formatted with [[#IPv6]]
- Layer 2 on the [[#Open Sourced Interconnected (OSI) Model]]

#### Ports
- Physical I/O connection built into networking hardware
	- Ex. Ethernet port on a [[#Switch]], [[#Hub]], or [[#Router]]

#### Internet Assigned Number Authority (IANA)
- Organization responsible for distributing IPv4 and IPv6 address to networks and ISPs

# Hardware
## Basic Devices and Bits
#### Switch
- Connects several clients together
- Only sends data to relevant recipients
- Creates a Switching Table that matches MAC addresses to ports
- **Layer 2 Switch / Multiport Bridge**
	- A switch that provides a direct data connection for network devices
- **Managed Switch**
	- Allows admins to monitor, configure, and manage a network

#### Hub
- Connects all traffic going through it, regardless of send/receive 

#### Router
- For each port, a LAN network is created.
- Inspects IP addresses

#### Bridge
- A device that sends [[#Media Access Control (MAC) Address]] info to forward data and connect LANs
- **Transparent Bridge**
	- A bridge connecting two LANs running the same protocol
- **Translation Bridge**
	- A bridge connecting two LANs running the different protocols
- **Bridge Table**
	- A list of MAC addresses and ports

#### Link Light
- Activity lights on a switch or a hub
- **Link Integrity Test**
	- A test to ensure communication between Ethernet devices
- **Link Pulses**
	- Signals sent specifically to light up Link Lights to indicate the connection’s still setup

# Routers
## Subnets
#### Subnetting
- Breaking down networks into smaller internal networks

#### Subnet Mask
- Determines how much of a PC's IP address is shared with the network's
- Typically in [[#IPv4]] formatting or in [[#CIDR Notation]]
	- Ex. 255.255.255.0
		- Represents `11111111.11111111.11111111.00000000` in binary digits
		- 1's indicate borrowed from the default gateway
		- 0's indicate new IP address

#### CIDR Notation
- Shorthand for writing subnet masks
- Place a slash at the end of an IP address with the number of borrowed bits
- Ex. `192.168.0.1/24`
	- Subnet mask for this would be `255.255.255.0`

#### CIDR Table
| **CIDR Notation** | **Mask**        | **Bits for Host** | **Usable IPs (Subtract 2)** | **New Subnet Increment** |
| ----------------- | --------------- | ----------------- | --------------------------- | ------------------------ |
| **/0**            | 0.0.0.0         | 4294967296        | 4294967294                  | 256.0.0.0                |
| **/1**            | 128.0.0.0       | 2147483648        | 2147483646                  | 128.0.0.0                |
| **/2**            | 192.0.0.0       | 1073741824        | 1073741822                  | 64.0.0.0                 |
| **/3**            | 224.0.0.0       | 536870912         | 536870910                   | 32.0.0.0                 |
| **/4**            | 240.0.0.0       | 268435456         | 268435454                   | 16.0.0.0                 |
| **/5**            | 248.0.0.0       | 134217728         | 134217726                   | 8.0.0.0                  |
| **/6**            | 252.0.0.0       | 67108864          | 67108862                    | 4.0.0.0                  |
| **/7**            | 254.0.0.0       | 33554432          | 33554430                    | 2.0.0.0                  |
| **/8**            | 255.0.0.0       | 16777216          | 16777214                    | 1.0.0.0                  |
| **/9**            | 255.128.0.0     | 8388608           | 8388606                     | 128.0.0                  |
| **/10**           | 255.192.0.0     | 4194304           | 4194302                     | 64.0.0                   |
| **/11**           | 255.224.0.0     | 2097152           | 2097150                     | 32.0.0                   |
| **/12**           | 255.240.0.0     | 1048576           | 1048574                     | 16.0.0                   |
| **/13**           | 255.248.0.0     | 524288            | 524286                      | 8.0.0                    |
| **/14**           | 255.252.0.0     | 262144            | 262142                      | 4.0.0                    |
| **/15**           | 255.254.0.0     | 131072            | 131070                      | 2.0.0                    |
| **/16**           | 255.255.0.0     | 65536             | 65534                       | 1.0.0                    |
| **/17**           | 255.255.128.0   | 32768             | 32766                       | 128.0                    |
| **/18**           | 255.255.192.0   | 16384             | 16382                       | 64.0                     |
| **/19**           | 255.255.224.0   | 8192              | 8190                        | 32.0                     |
| **/20**           | 255.255.240.0   | 4096              | 4094                        | 16.0                     |
| **/21**           | 255.255.248.0   | 2048              | 2046                        | 8.0                      |
| **/22**           | 255.255.252.0   | 1024              | 1022                        | 4.0                      |
| **/23**           | 255.255.254.0   | 512               | 510                         | 2.0                      |
| **/24**           | 255.255.255.0   | 256               | 254                         | 1.0                      |
| **/25**           | 255.255.255.128 | 128               | 126                         | 0.128                    |
| **/26**           | 255.255.255.192 | 64                | 62                          | 0.64                     |
| **/27**           | 255.255.255.224 | 32                | 30                          | 0.32                     |
| **/28**           | 255.255.255.240 | 16                | 14                          | 0.16                     |
| **/29**           | 255.255.255.248 | 8                 | 6                           | 0.8                      |
| **/30**           | 255.255.255.252 | 4                 | 2                           | 0.4                      |
| **/31**           | 255.255.255.254 | 2                 | 0                           | 0.2                      |
| **/32**           | 255.255.255.255 | 1                 | 0                           | 0.0                      |

## Sending Messages
#### Default Gateway
- IP address for a router's [[#Ports]]
- Unique address for each port
- Set on every PC connected to router

####  Protocol
- Set of rules established for users to exchange information.

#### Carrier Sense Multiple Access with Collision Detection (CSMA/CD)
- Any computer on a network can listen out for traffic, and any computer can access the network.
- Collision detection is needed since two systems could access the same system at the same time, causing potential dataloss.

#### Frame
- A data format that provides info for transmission
- Preamble
	- Alternating pattern of 0’s and 1’s for synchronization
- Start frame delimiter
	- A binary 8-bit sequence of 10101011 that indicates the start of the frame
- Destination MAC address
- Source MAC address
- Data length in bytes
- Data
- Padding
- Frame check sequences

#### Network Number
- Typically the first IP address
- xxx.xxx.x.0

#### Network ID
- The part of an IP address a [[#Subnet Mask]]
- Ex. With a [[#Subnet Mask]] of 255.255.255.0, **192.168.3**.117

#### Host ID
- The part of an IP address a subnet does **not** mask
- Ex. With a subnet of 255.255.255.0, 192.168.3.**117**

#### Broadcast ID
- Typically the last IP address
- Ex. xxx.xxx.x.255

#### Dynamic Assignments
- A process where [[#Media Access Control (MAC) Address]]es are dynamically assigned to ports

#### Static Assignments
- A process where [[#Media Access Control (MAC) Address]]es are manually assigned to ports

#### Secure Address
- A device that disables itself when an unknown [[#Media Access Control (MAC) Address]] connects to the network

## Networks at Scale
#### Star Network
- A token is passed from device to a hub to another device, allowing each device to “have its turn” communicating. Additionally, each system opens up ports use dedicated “communication lanes”. These make networks deterministic.
- ![[Star Network.png|500]]

#### Bus Network
- All systems are connected to a single cable (usually ethernet work coaxial). Each system can see all communications. 
- ![[Bus Network.png|500]]

#### Mesh Topology (P2P)
- Each device is directly connected to each other.
- ![[Mesh Network.jpg|500]]

#### WAN/MAN/LAN/PAN 
- ![[WAN:LAN.jpg|500]]
- These are fairly arbitrary names, since a big enough LAN is basically a MAN or even a WAN

# Switches
## Protocols
#### Address Resolution Protocol (ARP)
- Protocol to resolve IP address to a hardware address (MAC address)
	- For final leg of sending data to/from a PC
- Sent by PC to switch
- Layer 2 but interacts with layer 3 [[#Open Sourced Interconnected (OSI) Model]]
- Spoofing: If a PC spoofs its [[#Media Access Control (MAC) Address]], and it connects first, that PC can steal traffic
- Literally sends “`Who has 192.168.1.1? Tell 192.168.1.6`”
- Literally receives “`192.168.1.1 is at 00:1e:a6:56:14:c0`”
- **ARP Cache/Table**
	- Temporary storage of [[#Media Access Control (MAC) Address]]
- **Broadcast**
	- A transmission sent to all devices connected to the network

## Routing
![[Link State Protocol.jpg|700]]

#### Static Route
- A list of IPs to where data can be forwarded, and was manually entered into the  computer/router’s routing table
- Most common route is the default gateway
- `netstat -r`
- `ip route <destination> <subnet mask> <next hop>`
	- Destination: Where we want to end up
	- Subnet mask for destination
	- Next hop: first network to connect to on the way
- Router A example
	- `ip route 10.10.10.0 255.255.255.0 10.10.200.2`
	- ![[Routing Example.jpg|500]]

#### Dynamic Route
- Can account for changes in the network
- Covers:
	- **Path Determination**: protocol to determine routes
	- **Metric**: Ranking best to worst routes
		- **Hop count**
		- **Reliability**
		- **Bandwidth**
	- **Cost**
	- **Delay**
	- **Load**
	- **Convergence Time**: Time to determine a clear view of a network
	- **Load Balancing**: A procedure that allows for multiple paths to help clear congestion of data.

#### Interior Gateway Protocols (IGP)
- Running networks inside an organization’s network
- Carries info about internal infrastructure prefixes
- Widely used protocols:
	- [[#Routing Information Protocol (RIP) v2]]
	- [[#Open Shortest Path First (OSPF)]]
	- ISIS

#### Exterior Gateway Protocols (EGP)
- Bouncing between routers connected directly to an ISP
- Convey routing info between organizations
- Widely used protocol: Border Gateway Protocol (BGP)
- Clearly defines edges of a network

#### Link State Protocols
- [[#Interior Gateway Protocols (IGP)]]
- Neighbor routers exchange _link state advertisements_ to update neighbors
	- Used if there’s some loss of hardware in the network and low convergence time
- Process
	1. Finds neighbors/adjacent routers
	2. Build routing table via link state advertisements
	3. Sends “Hello” packets
	4. Sends updates when routing changes
- Requires higher processing power

#### Distance Vector Protocol
- Periodically sends entire routing table to adjacent router to better determine layout of network
- Routers assign distance-vector number to each route
	- Directly connected has value of 0

#### Routing Information Protocol (RIP) v2
![[Distance Vector Packet.jpg|700]]
- Dynamic routing protocol
- An [[#Interior Gateway Protocols (IGP)]]
- Maximum of 15 hops to prevent loops
- Updates every 30-60 seconds
- Only real difference with v2 of RIP is speed of network traversal
- When configuring, only add networks directly attached to router being configured
- To enable:
	1. `router rip`
	2. `version 2`
	3. `network <ip address>`

#### Open Shortest Path First (OSPF)
- [[#Link State Protocols]] dynamic routing protocol
- Open standard
- Rapid convergence via Link State Advertisements
- All routers agree on best routes
- Recalculates immediately after device loss
	- Regularly sends “hello” packets to verify network
- **Variable Length Subnet Masks (VLSM)** 

#### Dynamic Host Configuration Protocol (DHCP)
- Automatically create and assign IPs
- Use several pieces of information to generate IP addresses
	- IP Address
	- Subnet Mask
	- Default Gateway/Default Router
	- DNS Server Address
- Server
	- Run on a DHCP server
	- Typically built into a home router

#### DORA
- **D**iscover: Client connecting to server
- **O**ffer: DHCP server offering IP
- **R**equest: Client ensuring correct IP address
- **A**cknowledgement: DHCP assurance that we all good
- Afterwards, repeat the request and acknowledgment to renew lease
	- Provided IP has a lease that gets revoked after a period of time
		- Minutes - Public wifi
		- Hours - Hotels
		- Days to a month - Labs, permanently connected systems
		- ![[Link State Protocol.jpg|600]]
## VLANs
#### VLAN Management
1. On switch, open config > VLAN Database, create VLAN number and name
2.  Setup PCs like normal. Use a desired network address (still using subnetting)
3. On switch where PC is connected, add desired VLAN
4. To connect several switches together, use cross over cable
5. On connected ports (both switches), set port to “Trunk” (from “Access”) and select desired VLANs to be shared

# Wireless
## WiFi
#### WiFi
- **802.11b (Wifi 1)**
	- 1999
	- 2.4GHz
	- 11mbps
	- Up to 100-150 feet indoors
- **802.11a (Wifi 2)**
	- 1999
	- 5GHz
	- 54mbps
	- Up to 75 feet indoors
- **802.11g (WiFi 3)**
	- 2003
	- 2.4GHz
	- 54mbps
	- Up to 150 feet indoors
- **802.11n (WiFi 4)**
	- 2009
	- 2.4/5GHz
	- 200+mpbs
	- Up to 255 feet indoors
- **802.11ac (Wifi 5)**
	- 2013
	- 5GHz
	- 867 Mbps
- **802.11ax (WiFi 6)**
	- 2020/2021
	- 1.2-1.3gbps
- **802.11ay (WiFi 6e)**
	- 2022
- **802.11be (WiFi 7)**
	- 2024
#### Direct Sequence Spread Spectrum (DSSS)
- Larger chunks of data
- Ex. [[#Wifi]] 802.11b

#### Frequency Hopping Spread Spectrum (FHSS)
- Bouncing between different frequencies

#### Orthogonal Frequency Multiplexing Division Multiplexing
- Larger chunks of data
- Across multiple frequencies

#### Wireless Management Protocol Types
- **Authentication**
	- Verify they are who they claim
- **Association**
	- Allocate resources to device
- **Data Delivery**
	- Ensure data gets to destination
- **Privacy**
- **Encryption**

#### Access Points (APs)
- **Transceiver**
	- Transmitter
	- Receiver
- Converts a wired connection to a wireless connection

#### Service Set Identifier (SSID)
- Name of the wireless network
- Used to identify which network traffic is meant for
- Similar to VLANs for wired networks


# Lab Summaries
## Lab 1-1: Network Connectivity Testing

#### Brief
- Using nslookup and ipconfig to learn basics of a connected network.

#### Useful details
- `ipconfig` to determine network details about the computer being used.

#### Problems
1. On Friday night, I went home with the intention of doing the assignment Saturday morning. I set my alarm to wake me up two hours before the deadline. I woke up, and tried running the first command, and it did not yield the expected output. This is when I realized that I learned the command for Windows, and macOS used different syntax.
2. I would have used a different computer, but every computer we have only Macs at my parents’s house.
3. I reached out to my significant other, who is the only person also home who has a Windows PC, but she was still asleep.
4. I tried downloading a VM, but because of the slow internet, I had no chance of downloading a Windows ISO in time.
5. Then I had an asthma attack because I’m allergic to cats and dogs, and my parents have both. It’s not usually a problem because I “get used to” them while I’m home, but it was particularly problematic because I had forgotten my inhaler at Champlain (2.5 hours away).
6. Once all the previous problems had finished, it was past the assignment deadline(s).
7. I eventually remembered that Champlain has access to VMware Horizon, which took some digging to find. Once I was signed in, it was smooth sailing through the rest of the assignment.
8. Finally, when writing the Tech Journal, I realized I wrote the entire thing in my personal email instead of my Champlain Email.

## Lab 2-1: Intro to Packet Tracer and Deploying/Pinging Devices
#### Brief
- Configure packet tracer to use 6 PCs and 2 switches, then have PC 0 ping PC 1.

#### Useful Details
- The devices being setup really do simulate the systems, thus things like starting/rebooting does actually take time.
- There is a difference between Terminal and Command Prompt. What that is, I do not know, but there is something.

#### Problems
- Signing in was a hassle. I had created my Cisco account, but it fought me until I tried signing in with Champlain’s single sign-on. While unfortunate, it was hurdled.
- I accidentally went to Terminal instead of Command Prompt. Fortunately I realized when I couldn’t immediately type.

#### Extra
1.  How do you deploy workstations and switches in Packet Tracer?
	1.  Use the top shelf’s “End Points” tab and drag a PC, or Network Devices then drag a switch.
	2.  Click on the device, and add any “hardware” desired.
	3.  Use the lightning bolt to add copper straight-through for device-to-switch, and copper cross-over for inter-switch.
2.  How do connect these devices with cables?
	1.  Go to the lightning bolt, and drag the desired cable. See part 1C.
	2.  How do you access the command-line terminal on a Packet Tracer PC?
	3.  Click on the PC > Desktop > Command Prompt

## Lab 2-2: Observing LAN Activity
#### Brief
- Use Wireshark to analyze packets both incoming and outgoing.

#### Useful Details
- When searching for MAC addresses, expand the packet in the lower section, and it’ll be under Ethernet II.
- Adding icmp to the top bar is a helpful way of isolating packets from the ping command.
- Keep wireshark searching for as little time as possible.

#### Problems
- I ran `ip route show` in the Linux VM made in class, and there were multiple IPs listed, but none explicitly said gateway, so I took to the internet and found that “default via” was the IP address I was looking for.
- Not completely sure where to find the source and destination MAC addresses in Wireshark. Some clicking around later and I found Ethernet II with “src” and “dst” tags. Expanding that yielded their full names and addresses.

#### Extras
- What is a MAC address and what are its components?
	- A MAC address is an address given to a NIC by its manufacturer. The first half is the manufacturer identifier, while the second half is the unique identifier. MAC addresses are 6 byte hex digits.
- How to get a MAC address.
	- On Windows, the easiest way is by using `ipconfig /all`. Other operating systems vary.
- What is Wireshark and how to use it. 
	- Wireshark is used for analyzing packets. There are many different uses, but simple press the blue fin in the upper left corner to start tracking packets. Click on a packet for its details in the lower sections.
- How to find a protocol in Wireshark.
	- Use the protocol tab in the upper section.

## Lab 3-1: ARP Observation
#### Brief
- Using `ip traceroute show` to get the IP address of the gateway, ping it, analyze the traffic with wireshark to see ARP requests.

#### Useful details
- Filtering in Wireshark proved to be extremely useful when trying to get packets using the ARP protocol. After that, using the columns to sort by source or destination helps with further sorting. However this isn’t always great for a screenshot.

#### Problems
- Clearing the arp cache with both of the provided commands did not work. With `arp -d`, the terminal replied with `arp: need host name` and with “netsh interface ip delete arpcahce” it replied with “netsh: command not found”.
		-To fix this, I ran just `arp`, which yielded the IP `192.168.3.250`. I tried `arp -d 192.168.3.250` which said `Operation not permitted`. I elevated to `sudo`, and it successfully removed the IP.

#### Deliverables
**Capture and Analyze an ARP Request**
1. Open you VM
2. Clear the arp cache command `arp -d` if `arp -d` does not work try: `netsh interface ip delete arpcache`
3. Make note of your default gateway (we did this in previous labs)
4. Open Wireshark and start a capture.
5. Clear the arp cache command `arp -d`
6. Open a terminal and ping the default gateway (we've done this before too!)
7. Stop Capture
8. Analyze Capture for ARP packets:
	1. **Deliverable 1**: Find the ARP broadcast that your computer used to find the gateway's MAC address. Provide a screenshot that shows the source and destination MAC address of this broadcast.
	2. **Deliverable 2**: Find the ARP reply from the gateway back to your computer. Provide a screenshot that shows the ARP reply packet indicating the MAC address for your gateway.
	3. **Deliverable 3**: What is the message sent in the ARP Request?  What is the message sent in the ARP Reply?
		- **Deliverables 1-3:** 
		  ![[Lab 3-1 1-3.png|700]]
1. Ping another student system on your LAN (We've done this).
	4. **Deliverable 4:**  Figure out how to create a display filter for ARP traffic only and provide a screenshot showing any ARP traffic related to your neighbor's system.
		- **Deliverable 4:** 
		  ![[Lab 3-1 4.png|700]]
	1. **Deliverable 5:**
		- ![[Lab 3-1 5.png|500]]
2. Stop your current capture and start a new one, dump the arp cache
3. Repeat the capture and ping- but this time ping Google's Public DNS server - `8.8.8.8`
	6. **Deliverable 6**.  This is important.  What do you see in the ARP request and reply? Can you discern the MAC address for the google DNS server or not?  Can you explain what happened?
		- In the ARP requests, only the router was being found with ip `192.168.3.250`.
		- The source and destination MAC addresses were found, but again, were only really for the router. `Source (local IP): 00:0c:29:92:94:7c, Dst (router): ec:13:db:c8:8e:81`
		- I did have a terminal pinging `8.8.8.8` but these are the only ARP results I received. Observing ICMP results however, the MAC Addresses are completely hidden for both the source and destination. This is likely because `8.8.8.8` is a proxy server merely acting as a single unit, when there are actually several servers working together. 

## Lab 3-2: Exploring Broadcast Domains
#### Brief
- Using Wireshark on multiple systems to observe the differences in reported MAC addresses.

#### Useful Details
- Filtering continues to be a particularly helpful method of finding necessary packets.
- Sanity checking with another computer is a great way to ensure what you’re looking at is what you’re supposed to be looking for.
- Ping commands are the same across all platforms: Linux, macOS, and Windows.

#### Problems 
- Wireshark cannot be installed on the lab computers, so for the last deliverable I had to use my personal computer.

#### Deliverables
1. Analyze Traffic to a Remote Network (different LAN)
	1. Open a Command Prompt (windows) or Terminal (Linux) 
	2. Open wireshark and start a capture
	3. Back in the Command Prompt/Terminal- ping the Google Public DNS server (8.8.8.8)
	4. Stop Capture
		1. **Deliverable  1**: Analyze the ICMP Response from Google. What is the source MAC address? What is the destination MAC address? (Hint: Data Link Layer Header). Does the source MAC address look familiar from prior labs? Do you think it is the Google Server's MAC address?
		   ![[Lab 3-2 1.png|500]]
			- **Deliverable 1-1:** The source MAC address is `ec:13:db:c8:8e:81`
			- **Deliverable 1-2:** The destination MAC address is `00:0c:29:92:94:7c`
			- **Deliverable 1-3:** The mac addresses look very familiar, particularly where it says “JuniperN”. This is likely not Google’s server.
2. Examine both sides of a ping
	1. Find a partner in class and get their IP address.
	2. From your workstation, ping your partner's IP and make sure you get a response
	3. On your workstation, start a Wireshark capture, ping your partner's IP, and stop the capture
	4. On your workstation, analyze the capture
	    ![[Lab 3-2 3.png|500]]
		2. **Deliverable 2**: What are the source and destination MACs in the ping reply
		- **Deliverable 2-1:** The source MAC address is `48:21:0b:33:5e:44`.
		- **Deliverable 2-2:** The destination MAC address is `00:0c:29:92:94:7c`.
	5. What is your partner's MAC address? 
		3. **Deliverable 3:** Does the MAC address match the address from you traffic capture? If not - what do you think happened?
		- **Deliverable 3:** Yes, the IP addresses do match. The source (`48:21:0b:33:5e:44`) matches the physical address listed by windows in the “Ethernet adapter Ethernet” section.
		  ![[Lab 3-2 3.png|500]]
3. Capture both side of the ping request
	1. Start a Wireshark capture on both PCs and let it run
	2. From a command prompt on your workstation, ping your partner's IP address
	3. Stop the captures on both Workstations
	4. Find and compare the ICMP traffic on both devices
		4. **Deliverable 4-1:** On your workstation, what is the source and destination MACs from the pings?
		- **Deliverable 4-1:** (Done with a different station than in the previous question). The source MAC address is `ec:13:db:c8:8e:81`. The MAC address destination is `00:0c:29:92:94:7c`.
		4. **Deliverable 4-2:** On your partner's workstation, what is the source and destination MACs from the pings?
		- **Deliverable 4-2:** The source MAC address is `a4:83:e7:69:44:82`. The destination MAC address is `0c:59:9c:f7:de:30`.
		5.  **Deliverable 5**:  Why do you think they are different?
		- **Deliverable 5:** All MAC addresses could be different from each other is potentially because `00:0c:29:92:94:7c` is actually the default gateway being reported. Meanwhile, with the VM and Windows being used in deliverable 3 the two “computers” are talking directly to each other, instead of through a router.

## Lab 4-1: Observing ARP in Packet Tracer
#### Brief
- An introduction to Packet Tracer, building a network and seeing how they appear on a switch.

#### Useful Details
- Ensure the network is readable by physically separating the devices more.
- Having the network labels be shown on the logical map is great for glancing (options>preferences>always show port labels in logical workspace.
- Use show mac-address-table to see connected devices and their Mac Addresses

#### Problems
- At first one PC wasn’t showing up when running mac-address-table. I ran it again, then all the PCs didn’t appear.
	- I pinged all the PCs from PC0 again, checked again, and they all appeared in the switch.

#### Deliverables
1. Start Packet Tracer and sign in with your Cisco Academy Credentials
2. Use the Devices Section in the lower left to build a simple network diagram using 4 generic computers and a switch
	1. Select the Device Category, locate the device you want, and click-drag into the workspace
	2. Do not connect the computers to the switch yet. (will embed graphic)
3. Hold the mouse over each computer to see the configuration. Gather information about the devices and answer the following questions
	1. SUBMIT: (1 Point): What is the MAC address of PC0? Is there an IP address? Hold the mouse over the switch to see the configuration. Are there IP addresses assigned?
		1. **Deliverable 1-1:** 00d0:582a:57ed
		2. **Deliverable 1-2:** The IP address is not set
		3. **Deliverable 1-3:** No IP addresses are set
4. Click on PC0 - Desktop Tab
	1. Open the Command Prompt 
	2. Type `arp –a` to see the arp table and review to see if there are any entries
5. Assign IP addresses to the computers (use 4 addresses on the same network : `10.10.10.X`) What does it mean for PCs to be "on the same network"?
	1. For PCs to be on the same network, they’ll have the same set of IPs so that all the computers can find each other.
	2. Select the computer, then Config tab, then FastEthernet0 ( Fa0)
	3. Configure the IP addresses as follows.  Use a netmask of 255.255.255.0

| PC  | IP Address   |
| --- | ------------ |
| 0   | 10.10.10.100 |
| 1   | 10.10.10.101 |
| 2   | 10.10.10.102 |
| 3   | 10.10.10.103 |

6. Review the ARP table entries of the PC's again
7. Examine the address table of the switch.  
	1.  Click on the switch and the select CLI.   This is the Command Line Interface.   You need to get to the root CLI prompt which looks like **Switch#**
		1.  If the prompt looks like:  **Switch>,**  then type `enable` to enter admin mode
		2.  If the prompt looks like  **Switch (config)#**  type `exit` to get back to the basic mode for admin
	2.  Then type `show mac-address-table`
8.  Review the table format for Mac Address and Port

9.  Use Ethernet cables to connect  the computers to the switch.

10.  The "Lightening Bolt" in lower left will allow you to add connections between devices
11.  Use the straight black cable (ethernet straight-through) to connect PC0 to Fa0/10 on the switch, PC1 to Fa0/11...

12.  On PC0, open the Desktop and select Command Prompt.
13.  From the command prompt on PC0, ping PC3 using it’s IP address.
14.  SUBMIT (2 Points) Screenshot showing successful ping between PC0 and PC3

## Lab 4-2: Simple Routing Lab
#### Brief
- Using Cisco Packet Tracer to easily see the role of a switch in a network, and how to configure computers to work with it.

#### Useful Details
- Simulation mode allows you to see protocols moving from system to system.
	- Use the panel on the right to “edit filters”
- USE COMMAND PROMPT. NOT TERMINAL.

#### Problems
- I had accidentally closed the window showing the OSI model, and couldn’t figure out how to get it back. Clicking on the switch wouldn’t summon the window back.
	- To fix this, the window’s likely open in the background. Clicking the switch once brings up the window, clicking it again brings up the switch configuration.

#### Deliverables
1. Part 1 - Configuring the Network
	1. Start by downloading and opening the Packet Tracer file for this lab: [lab41-starter.pkt](https://champlain.instructure.com/courses/1921220/files/238671667?wrap=1)
	2. The network should look something like this:
	   ![[Lab 4-2 dia 1.PNG]]

	3. Assign the following IP addresses and subnet masks to the PCs (you should have instructions for doing this in your Tech Journal): **Deliverable 1:** What is a subnet mask?
		- PC0
			- IP address: `192.168.1.10`
			- Subnet Mask: `255.255.255.0`
		- PC1
			- IP address: `192.168.2.20`
			- Subnet Mask: `255.255.255.0`
		- PC2
			- IP address: `192.168.3.30`
			- Subnet Mask: `255.255.255.0`
	4. Assign the following IP addresses and subnet masks to the PCs (you should have instructions for doing this in your Tech Journal): **What is a subnet mask?**
	5. Since we'll be pinging across different networks, we'll need to define the **gateway** addresses for our PCs. To set the gateway for a PC, choose the Config tab, and then choose 'Settings' in the left-hand menu. You can enter the gateway IP in the 'Gateway' field (make sure the 'Static' button above it is selected). **Define default gateway?**
	    ![[Lab 4-2 dia 2.PNG]]
		1.  **Deliverable 1:** A default gateway is “the door person”, which lets traffic in and out of the network.
	6.  Enter the following gateway IPs for each PC:
		- PC0: 192.168.1.1
		- PC1: 192.168.2.1
		- PC3: 192.168.3.1

	7. Now, we'll need to set the interface that each PC is connected to on the multilayer switch to match the gateway IP we just defined, since this switch also has layer 3 routing capabilities and will serve as the gateway for all three machines. Click on the multilayer switch, choose the Config tab in the window that appears, and then pick the FastEthernet interface that you want to configure (in the example below, we're selecting FastEthernet0/1).
	   ![[Lab 4-2 dia 4.PNG|500]]

8. Enter the following IPs on these interfaces:
	- FastEthernet0/1: 192.168.1.1
	- FastEthernet0/2: 192.168.2.1
	- FastEthernet0/3: 192.168.3.1
	- All subnet masks will be 255.255.255.0

	- Note that because each port is a distinct interface, they all have to be given their own address.

9. Once all of the interfaces are configured, try pinging PC1 and PC2 from PC0. If configured correctly, the pings should succeed!

	- Note that sometimes the first ping request between two machines will time out - this is just a relic of Packet Tracer, and subsequent pings should succeed.

2. **Deliverable 2:** SUBMIT screenshots of a successful ping between PC0 and PC1 (2 points) and a successful ping between PC0 and PC2 (2 points) 
	- **Deliverable 2:**
	  ![[Lab 4-2 2.png|400]]

2. Part 2: Packet Tracer Simulation Mode
	1. Click on the Simulation button in the bottom-right corner of the Packet Tracer window.
	   ![[Lab 4-2 dia 4.PNG|500]]
	2. A Simulation panel will appear on the right side of the window. Since Packet Tracer will simulate many protocols by default, click the 'Show All/None' button at the bottom of this window, and then click the 'Edit Filters' button. Check the ICMP box in the IPv4 tab of the window that pops up. 
	   ![[Lab 4-2 dia 5.PNG|500]]
	3. Now, ping PC1 from PC0. The initial ping packet should appear in the simulation window. Click the '►|' button a few times until the packet reaches PC1 - you should see the following packets in the simulation window:![[Lab 4-2 dia 6.PNG]]

	4. If you click on the packet at the Multilayer Switch, you'll receive a summary of the OSI information the packet contains as it both arrives at and leaves the switch. In particular, at layer 2 you'll see something like 'AAAA.AAAA.AAAA >> BBBB.BBBB.BBBB' - this indicates that the packet is being sent from the MAC address AAAA.AAAA.AAAA to the MAC address BBBB.BBBB.BBBB. If you click on the Inbound and Outbound detail tabs, you can see how this information is specifically formatted within each packet.

	3. **Deliverable 3:** SUBMIT answers to the following questions:
		- What is the Source and Destination MAC address of the packet as it arrives at the switch? (1 point) SCREEN CAPTURE 
			- **Deliverable 3-1:**
			   ![[Lab 4-2 3-1.png]]
		- What is the Source and Destination MAC address of the packet as it leaves the switch? (1 point) SCREEN CAPTURE
			- **Deliverable 3-2:**
			   ![[Lab 4-2 3-2.png]]
		- Why does the Destination MAC of the packet arriving at the switch match the Source MAC of the packet leaving the switch? (3 point)
			- **Deliverable 3-3:** This is likely because instead of checking at the PC level, we’re checking at the switch, so it’s the same device being used during the in and out operations.
 
## Lab 4-3: Simple 2-Network Packet Tracer Lab
#### Brief 
- A more hands off lab where 2 switches, a router, a server, and a laptop were setup for pinging.

#### Useful Details
- Save the NVRam when resetting a router.

#### Problems
- The router wasn’t connecting to either the Foster or Skiff switches.
	- After about an hour of clicking, and recreating the network, I learned the port needs to manually be enabled on the router.

#### Deliverables
1. Connect laptop/server to switches and switches to router (FastEthernet ports on Router) and pay attention to the interfaces you use.
2. Network address for Foster is `192.168.3.0/24` and Network address for Skiff is 192.168.1.0/24
3. On CNCS Router
	- Assign the IP `192.168.3.1` and subnet mask `255.255.255.0` to the Interface connected to the Foster Network
	- Assign the IP `192.168.1.1` and subnet mask `255.255.255.0` to the Interface connected to the Skiff Network
4. Configure IP's subnet mask and Default Gateway on the Laptop and Server
	- On the Laptop assign `192.168.3.20`, mask `255.255.255.0` and `192.168.3.1` as the Gateway
	- On the Server assign `192.168.1.40` Mask `255.255.255.0` and `192.168.1.1` as the Gateway
5. Ping server from laptop
	1. **Deliverable 1:** screenshot of successful ping (2 Points)
	- **Deliverable 1:**
	  ![[Lab 4-3 1.png|500]]
Traffic Analysis in Packet Tracer
1. Go into "Simulation Mode" in Packet Tracer (stopwatch on lower right)
2. From Laptop - open up "Web Browser" on Laptop Desktop
3. Enter the IP address of server and hit "go"
4. Use Capture/Forward to send to packets hop-by-hop
5. Continue until you see HTTP Packets in the Simulation Panel
6. Review Packet Details of a HTTP Packet in the Simulation Panel
	2. **Deliverable 2:** Screenshot of Details (Inbound or Outbound PDU) of a HTTP packet that includes the Source/Destination MAC, Source/Destination IP Address (2 Points)
		- **Deliverable 2:** 
		  ![[Lab 4-3 2.png]] 
Practice Saving Router config
1. Go back to Real-Time mode (clock)
2. From Router: Config Tab: Save NVRAM
3. From Router: Got to "Physical Tab" and use power button to turn off router. 
4. Power back on by clicking the button again
5. Use Fast Forward button to get links back
6. Check router to make sure Interface IP's are still there
	1. **Deliverable 3:** Screenshot of CNCS Router showing IP address on an Interface (2 Points)
		- **Deliverable 3:** 
		  ![[Lab 4-3 3.png|500]]

## Lab 5-1: Routing Lab
#### Brief
- Observing packets via a sniffer.

#### Useful Details
- An IP Address set in the router’s port will be the IP for the default gateway, and is a used IP on that network.
- Different devices may be “happy” with different cables.

#### Problems
- I wasn’t sure what ports I should add to the empty router.
	- I did some trial and error, and found that I needed to use PT-ROUTER-NM-1CFE.
- Couldn’t get the router to connect to anything for a bit.
	- After a small amount of head scratching, I forgot that the router’s ports need to be turned on.
- In several locations instead of writing “192” I wrote “129”
- I couldn’t get the sniffer to connect to the switch via a copper straight through cable
	- I abandoned the cable and opted for a copper cross-over cable, and that worked immediately.

1. Part 1 - Building the Network
	1. **Deliverable 1**: Build the below network in Packet Tracer. Screen Capture of networks (1 points). You will need to assign IPs to laptops and router interface. As well as assign default gateways. Device numbers may not match devices you have.
	   ![[Lab 5-1 dia 1.PNG]]
	2. Configure the IPs on the router interfaces. You will need 3 different network/IPs  **Deliverable 2:** Screen capture of router IP settings.  5 points
	   ![[Lab 5-1 2.png|500]]
	3. Set the appropriate IP's to your workstation's. Workstations IP should be in same network as default gateway.  You should have instructions for doing this in your Tech Journal!
	4. **Deliverable 3:** Once all of the interfaces are configured, try pinging from *HELLO!* laptop to Ping Me laptop. Deliverable 3: Screen capture of HELLO! pinging Ping Me. 1 points
		- **Deliverable 3:** 
		  ![[Lab 5-1 3.png|500]]
2.  Part 2: Packet Capture Observation
	1.  Using the sniffer inspect packets going from _HELLO!_ to _Ping Me_ and back.  Ping both ways
		- How to install a sniffer:
		- [https://www.youtube.com/watch?v=gsCSKQAVT2MWireshark](https://www.youtube.com/watch?v=gsCSKQAVT2M) 
		-  [(Links to an external site.)](https://www.youtube.com/watch?v=gsCSKQAVT2M)
		- Install sniffer between switch and router. Try pinging from _HELLO!_ laptop to _Ping Me_ laptop and observe packet info. **Deliverable 4:** SCREEN CAPTURE of sniffer GUI info. 2 points
			- **Deliverable 4:**
			  ![[Lab 5-1 4.png|500]]
		1. **Deliverable 5:**  Replace switch with a hub and repeat above steps. Deliverable 5: What was different about the sniffer information when it was connected to a hub? 3 points
			- **Deliverable 5:** The output was significantly limited to a single ARP and four ICMP packets.![[Lab 5-1 5.png]]


## Lab 7-1: VLSM
#### Brief
- Subnetting a network to create 5 networks accross 2 routers

#### Useful Details
1. Consulting the [[#CIDR Table]] in the Tech Journal is very useful.

#### Problems
1. Had to recreate the table of IPs a couple times because of a misunderstanding of counting IP addresses.

#### Deliverables
![[Lab 7-1 dia 1.png|700]]
**Deliverable 1:** Background
- PPC uses the private class B space of 172.16.0.0/16.  Currently all hosts are on the same network which is causing hate and discontent due to network performance impacts (hence, the sacking of Henry).  Here is some information which may help you in designing your subnet scheme.
	- Mumbai Divisions
		- Manufacturing will need 612 hosts
		- Engineering will need 31 hosts
	- North American Divisions
		- Sales is the largest division with a host requirement of 1200
		- HR needs 10 hosts  
		- Accounting will need space for 24 hosts -- (note gateways are part of this number too)

| Divisions | Number of Hosts | CIDR | Increment | Network Address | First Usable Host Address | Last Usable Host Address | Broadcast Address |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| Sales | 2046 | /21 | x.x.8.0 | 172.16.0.0 | 17.16.0.1 | 172.16.7.254 | 172.16.7.255 |
| Manufacturing | 1022 | /22 | x.x.4.0 | 172.16.8.0 | 172.16.8.1 | 172.16.11.254 | 172.16.11.255 |
| Engineering | 62 | /26 | x.x.x.64 | 172.16.12.0 | 172.16.12.1 | 172.16.12.62 | 172.16.12.63 |
| Accounting | 30 | /27 | x.x.x.32 | 172.16.12.64 | 172.16.12.65 | 172.16.12.94 | 172.16.12.95 |
| HR | 14 | /28 | x.x.x.16 | 172.16.12.96 | 172.16.12.97 | 172.16.12.110 | 172.16.12.111 |
| Router Network | 2 | /30 | x.x.x.4 | 172.16.12.112 | 172.16.12.113 | 172.16.12.114 | 172.16.12.115 |

## Lab 6-2 Classful Subnetting
#### Brief
- Connecting 3 routers together with serial cables to allow for inter-network communication.

#### Useful Details
1. Always remember to use unique IPs when assigning IPs to router networks.
2. The serial connections requre the same clock rate (64k is what was used here).
3. Labels are your friend .

#### Problems
- A couple computers had their default gateways off by one which was causing a lot of issues when going between routers.
	- Testing PDU packets within the network can help to diagnose the issue.

#### Deliverables
1. **Deliverable 1:** Show the successful transmission of a PDU from Joyce1 to Skiff1 and SkiffLast to JoyceLast.  Make sure to Capture the PDU List showing these successes in a screenshot that captures your entire PT window to include the PDU list (make sure to label your diagram with your name).
2. **Deliverable 2:** Show the successful transmission of a PDU from Foster1 to Skiff1 and Foster Last to SkiffLast in a screenshot that captures your entire PT window to include the PDU list (make sure to label your diagram with your name).
- **Deliverable 1 & 2:**
  ![[Lab 6-2 1-2.png|500]]

## Lab 10-1: RIP Lab
#### Brief
- Using RIP to connect multiple router networks together so that computers can 

#### Useful details
- Always remember to use unique IPs when assigning IPs to the router networks.
- The serial connections require the same clock rate (64,000 is what was used here).
- Labels are your friend

#### Problems
- None!

#### Provided Notes
- Cisco routers don't enable RIPv2 by default. To use RIPv2, you must use the ver 2 command in RIP Router Configuration Mode.
- RIP uses hop count as it’s metric.

#### Deliverables
1. Using the same starter [Packet Tracer File](https://champlain.instructure.com/courses/1921220/files/238671709/download?wrap=1 "Packet Tracer - Static Route.pkt") from the "Static Route" lab, we will now configure the network using RIP.  This means that the routers will learn about neighboring routers and network through RIP Broadcasts
	1. Configuring RIP involves 
	    - Enabling it on the router
	    - and, declaring which of the directly connected networks should be advertised
	2.  Here is the configuration for R2 in our example:
	    - From "config" mode type: `router rip`. This will now put you in "router config mode"
	    - Then specify the version with
		- `version 2`
	    - And then specify the networks directly connected to Router 2
		- `network 192.168.30.0`
		- `network 10.10.20.0`
	3. Thats it!
	4.  Repeat Step 2 for R1 and R3
		- Make sure to update the network statements to specify the correct networks for those routers!
	5.  If it is working, all PC's should now be able to ping one another
	6.  Go to R2, exit "config" mode, and type "show ip route".  You should see all of the the networks in the table. **Deliverable 1: Screenshot** 
	   ![[Lab 10-1 2.png|500]]
	8.  Repeat Step 4 for R1 and R3.   **Deliverables 2 & 3: Screenshot** 
	   ![[Lab 10-1 1.png|500]]![[Lab 10-1 3.png|500]]

2. Inspect RIP Activity
	1.  In Packet Tracer - switch to "Simulation Mode" (Stopwatch icon in Lower Left)
	2.  Under Event List Filters - Visible Event - Click Show All/None
	3.  Then click Edit Filters - and Select RIP
		1.  Click the "Capture/Forward" button in the lower center of the screen repeatedly. You should see RIP packets traversing the network.
	4.  In the upper right Event List - find a packet for RIPv2 from R1 to R2
	5.  Click the colored "info" box to display the packet details.
	6.  Click the Inbound PDU Details tab
	7.  Scroll down to RIP v2 section
	    -   **Deliverable 4: Screenshot**
	    - ![[Lab 10-1 4-6.png|600]]
		    -   **Deliverable 5:** Describe what is included in the packet details for the RIP v2 protocol section
			    - **Deliverable 5:** The packet holds information about what version of RIP, where it needs to go next, and the cost of the connection.
	1.  Repeat 5-8 for a RIP packet from R3 to R1
	2. **Deliverable 6 & 8**
	   ![[Lab 10-1 4-6.png|600]]![[Lab 10-1 4-6.png|600]]
	3. **Deliverable 7 & 9:** The RIP packets seems to all be identical, though the next hope and metric fields likely have different information.

## Lab 11-1: VLANs in Packet Tracer
#### Brief
- Creating VLANs on network switches to allow for separated networks over switches instead of routers.

#### Useful details
1. Set each port on the switch to use the desired VLAN
2. TRUNC a port that is used to be inter-switch, and select all desired VLANs

#### Problems
1. None!

#### Deliverables
1. Configure Switchports for VLANs
	1. On 1st Floor Switch, Go to Config/VLAN Database and add the VLANs the switch will support:
		1. VLAN Number: 10 Name: ENG
		2. VLAN Number: 20 Name: MKT
		3. VLAN Number: 30 Name: ACT
	2. Then, configure which ports are in which VLAN from Config tab by changing the VLAN number for the Access Port configuration per interface
		1. FastEthernet 0/1 can be VLAN 10 (ENG)
		2. FastEthernet 0/2 can be VLAN 20 (MKT)
		3. FastEthernet 0/3 can be VLAN 30 (ACT)
	3. Then, configure the Trunk port that will be used to connect the switch to the 2nd Floor Switch
		1. GigabitEthernet 0/1 change to Trunk and add VLANs 10, 20, and 30 (leaving the other default VLANs checked is fine)
	4. Repeat 1-3 on 2nd Floor and 3rd Floor switches
		- Note: On 2nd Floor switch, you will need to configure both GigabitEthernet 0/1 and Gigabit/Ethernet 0/2 as Trunk ports (step 3) as it connects to two switches
2. Connect Devices
	1. Assign Appropriate IP configurations to the PC's
		1. ENG network is 192.168.10.0/24 and the default gateway will be 192.168.10.1
		2. MKT network is 192.168.20.0/24 and the default gateway will be 192.168.20.1
		3. ACT network is 192.168.30.0/24 and the default gateway will be 192.168.30.1
		- Remember, every PC needs a unique address
	2. Connect PC's to the switch on their floor.
		- Make sure to connect the PC to the Port on the switch that is in their VLAN!
	3. Connect switches to each other using Crossover Cables  and the configured Trunk ports
		- If everything is connected and addressed correctly, all PC's on the same VLAN should be able to ping each other. But, PC's on different VLANs (even on the same switch) should not be able to ping.
		- At this point, All PC's on the same VLAN should ping one another - BUT PC's on different VLANs should not be able to ping one another
**Deliverable 1:**
![[Lab 11-1 1.png|500]]
**Router on a stick:** simply a router that has only one connection to a network (usually directly to a switch) and handles routing via VLANs.


## Lab 12-2: Building a WLAN in Packet Tracer![[12-2 WLAN.pkt]]
#### Brief
- Setting up a **secure** wireless router and 3 laptops to connect to it for internet access.

#### Problems
- Nothing of note

#### Notes
1. Part 1: Following Part 1
	1. Setup Internet Connection type with a static LAN IP from the table
	2. Setup the Network Setup type with the LAN IP from the table
	3. Set the Network Mode to `Wireless-N Only`, and set the SSID to `CoolSSID`
	4. Disabled the broadcasting of the SSID
		1. Don't forget to save your settings
	5. Set the security to WPA2-Personal and configured a password
2. Part 2: Following Part 2
	1. Created a new Wireless Profile called `Wireless Profile` in Laptop1 > Desktop > PC Wireless
	2. After going through the setup, I accidentally clicked on "Connect" for the Default profile. I swapped over to the "Wireless Access" profile, and the Link Information was good after a small bit of time.
	3. Took a tiny screenshot for **Deliverable 1**
	4. Setup laptops 2 and 3 the same way as Laptop 1
3. Part 3: Following Part 3
	1. Connected the router with FA0/1 to the wireless router
	2. Connected the router with FA0/0 to the web server
	3. While the directions didn't say to, I setup the rest of the IPs
	4. I found an interesting issue of the router not being able to ping the wireless router, but the wireless router being able to ping the router. It doesn't seem to keep the laptops from pinging the webserver, though.

#### Deliverables:

| **Device**          | **Interface** | **IP Address**    | **Subnet Mask**   | **Default Gateway** |
| --------------- | --------- | ------------- | ------------- | --------------- |
| Router          | FA0/0     | 192.168.30.1  | 255.255.255.0 | N/A             |
| Router          | FA0/1     | 192.168.1.1   | 255.255.255.0 | N/A             |
| Laptop 1        | NIC       | DHCP          | 255.255.255.0 | 192.168.0.100   |
| Laptop 2        | NIC       | DHCP          | 255.255.255.0 | 192.168.0.100   |
| Laptop 3        | NIC       | DHCP          | 255.255.255.0 | 192.168.0.100   |
| Wireless Router | Internet  | 192.168.1.100 | 255.255.255.0 | 192.168.1.1     |
| Wireless Router | LAN       | 192.168.0.100 | 255.255.255.0 | 192.168.0.1     |
| Web Server      | FE0       | 192.168.30.15 | 255.255.255.0 | 192.168.30.1    |

1.  Configure a Wireless Router  
	1. Step 1: Configure the Internet connection type on the WR.  
		1. Click WR > GUI tab.  
		2. Set the Internet Connection type to Static IP.  
		3. Configure the Internet IP address according to the Addressing Table.  
	2. Step 2: Configure the network setup.  
		1. Scroll down to Network Setup. For the Router IP option, set the IP address to the Wireless Router’s LAN address and the subnet mask  
		2. Enable the DHCP server.  
		3. Scroll to the bottom of the page and click Save Settings.  
	3. Step 3: Configure wireless access and security.  
		1. At the top of the window, click Wireless. Set the Network Mode to Wireless-N Only and change the SSID to whatever you want to call your network.  
		2. Disable SSID Broadcast and click Save Settings.  
		3. Click the Wireless Security option.  
		4. Change the Security Mode from Disabled to WPA2 Personal.  
		5. Configure a passphrase.  
		6. Scroll to the bottom of the page and click Save Settings.
2. Part 2: Configure a Wireless Client
	1. Step 1: Configure Laptop1  for wireless connectivity. Because SSID broadcast is disabled, you must manually configure Laptop1 with the correct SSID and passphrase to establish a connection with the router.
		1. Click Laptop1 > Desktop > PC Wireless.
		2. Click the Profiles tab.
		3. Click New.
		4. Name the new profile Wireless Access. 
		5. On the next screen, click Advanced Setup. Leave on Infrastructure Mode.
			1. Then manually enter the SSID of your network on Wireless Network Name. Click Next. 
			2. Choose Obtain network settings automatically (DHCP) as the network settings, and then click Next. 
			3. On Wireless Security, choose WPA2-Personal as the method of encryption and click Next.
		7. Enter the passphrase and click Next. 
		8. Click Save and then click Connect to Network.
	2. Step 2: Verify Laptop1 wireless connectivity and IP addressing configuration.
		1. The Signal Strength and Link Quality indicators should show that you have a strong signal.
		2. Click More Information to see details of the connection including IP addressing information.  
		3. **SCREENSHOT #1** 
		- **Deliverable 1:** Sorry it's so small, the window was tiny.
		  ![[Lab 12-2 1.jpg]]
		4. Close the PC Wireless configuration window.  
	3. Step 3: Configure Laptops 2 and 3 to connect to Wireless
4. Part 3: Connect to Wired Router and Web Server
	1. Step 1: Configure the Wired Router with the correct IP addresses per the Table.
		1. Connect the Wired Router to the Wireless Router using a crossover cable and correct ports.
		2. Connect the Wired Router to the Web Server using a crossover cable and the correct ports.  
	2. Step 2: Access Web server from the Laptops  
		1. Using the Web Browser on the laptops – connect to the Web Server  
		2. Show Laptop 2 & 3 connecting to Web Server.  
		3. **SCREENSHOT #2**  
		4. **Deliverable 2:**
		    ![[Lab 12-2 2-3.jpg|500]]

## Lab 14-1: Network Troubleshooting
#### Challenge 1 (about 5 minutes)
![[NET-150-Lab 14-1 Troubleshooting Challenge 1.pkt]]
1. Attempt to ping router from laptops (good)
2. Attempt to ping laptops from router (good)
3. Attempt to have laptops ping each other (failed)
4. Check laptop default gateways
	1. Found Skiff laptop default gateway to be empty
	2. Have laptops ping each other
		1. After several pings, the laptops were able to successfully ping each other.
		2. ![[Lab 14 1.jpg|500]]

#### Challenge 2 (about 2 minutes)
![[NET-150-Lab 14-1 Troubleshooting Challenge 2.pkt]]
1. Attempt to ping router from Foster laptop (known good)
2. Attempt to ping router from Skiff laptop (known bad)
3. Check difference between Foster and Skiff switches
	1. No difference found
4. Check difference between Foster and Skiff ports on router
	1. Skiff port had not been configured.
	2. Pull network details from Skiff laptop.
	3. ![[Lab 14 2.jpg|500]]

#### Challenge 3 (About 7 minutes)
![[NET-150-Lab 14-1 Troubleshooting Challenge 3.pkt]]
1. Attempt to have PCs 0-3 ping each other (good)
2. Attempt to have any PC ping router (all bad)
3. Investigate IP addresses
	1. Found cables from router were flipped
	2. ![[Lab 14 3.jpg|500]]

#### Challenge 4 (About 15 minutes)
![[NET-150-Lab 14-1 Troubleshooting Challenge 4.pkt]]
1. Attempt to have PC0 and PC1 ping each other (good)
2. Have PC1 ping router1 (good)
3. Have PC1 ping router2 (good)
4. Have PC1 ping router3 (bad)
5. Have PC2 ping router3 (good)
6. Have router2 ping router3 (good)
7. Have router1 ping router3 (good)
8. Check static routes on all routers
	1. Found router3 was missing a route to the 192.168.10.0 network
	2. ![[Lab 14 4.jpg|500]]

#### Challenge 5 (About 10 minutes)
![[NET-150-Lab 14-1 Troubleshooting Challenge 5.pkt]]
1. Found *technically* no problem since PC1 and PC2 can ping each other, though laptops are unable to at all
	1. Points to a subnetting problem
2. Check VLAN databases (good)
3. Check gigabit ports on switches are set to Trunk with correctly forwarded VLANs (good)
4. Check ports directly connected to laptop for correct VLAN (bad on second floor)
	1. Laptops can now ping each other
5. Ensure all devices can ping MultilayerSwitch0
6. Closed packet tracer and reopened
	1. Magically worked
	2. ![[Lab 14 5.jpg|500]]