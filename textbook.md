#TCPIP

## Networking architecture or network blueprint of TCPIP 
- Define protocol via Requests for Comments RFC defines set of functions and specifics about implementation


### Application (data)
- Protocols
1. HTTPS, POP3, SMTP
- Create and encapsulate the application data with any required application layer headers

### Transport (TCP, data = segment)
- Protocols
1. TCP, UDP 
- adjacent-layer interaction how adjacent layers in networking model on same computer work together. 
- Same-layer interaction when a particular layer on one computer wants to communicate with the same layer on another computer, the two computers use headers to hold the information that they want to communicate. 
- Encapsulate the data supplied by the application layer inside a transport layer header

### Network/Internet protocol IP (IP, TCP, Data = Packet)
- Delivering data over the entire path from the original sending computer to final destination computer (National Postal services to addresses)
- Protocols
1. IP, ICMP 
- Addressing and routing: packets of data 
- Encapsulate the data supplied by the transport layer inside a network layer IP header

### Data Link (Data Link header, IP, TCP, Data link trailer = Frame) 
- Control use of physical  link (standards for roads, cars and traffic signals)
- Protocols
1. Ethernet, 802.11 (wifi) 
- Encapsulate the data supplied by the network layer inside a data link layer header and trailer

### Physical
- How to transmit bits over each link
- Transmit the bits.

## Ethernet LANS
- Ethernet connecting devices, with SOHO (small office or home network) with Router, switch and access point for wifi in one device. 

## Ethernet physical layers
- Unshielded twisted pair (UTP)
- Kinds of Ethernet 
   1. 10 Mbps, Ethernet, 10BASE-T, 802.3, copper, 100m
   2. 100 Mbps, Fast Ethernet, 100BASE-T, 802.3u, copper, 100m
   3. 1000 Mbps, Gigabit Ethernet, 1000BASE-LX, 802.Z, Fiber, 5000,
   4. 1000 Mbps, Gigabit Ethernet, 1000BASE-T, 802.3ab, copper, 100m
   5. 10 Gbps, 10 Gig Ethernet, 10Gbase-T, 802.3an, copper, 100m
- cabling pinouts for 10BASE-T 100BASE-T
   1. Crossover Cables: If the endpoints transmit on the same pair 
   2. Strait though cable: if the endpoints transmit on different pin pairs

|  Transmits pins 1, 2  |  Transmits pins 3, 6     |
|-----------------------|--------------------------|
|  PC NICs              |  Hubs                    |
| Routers               |  Switches                |
| WAPs (ethernet)       | none                     |

- Auto-MDIX automatic medium dependent interface crossover can redirect a strait through pinout to crossover and visa versa 
- UTP cabling pin outs for 1000BASE-T
   1. Requires 4 wire pairs

### Ports
1. Gigabit Ethernet interface converter GBIC (larger than gigabit interfaces, larger than SFPs
2. Small form factor pluggable SFP: replacement for GBICs used on gigabit interfaces with smaller size  taking up less spaces
3. Small form factor pluggable plus SFP+: same size as SFP but used on 10 Gbps interfaces

### NIC transmitters
- Transmitters use pairs 1 and 2 
- Receivers use 3 and 6
- Lan switches do opposite

### LAN switches
- Transmitters use 3 and 6
- Receivers use 1 and 2

### Ethernet Protocols
#### Use data link standards with the Ethernet frame
|  Header      | Header |  Header         |  Header      |  Header   |                          | Traieler  |
|--------------|--------|-----------------|--------------|-----------|--------------------------|-----------|
|  Preamble 7  | SFD 1  |  Destination 6  |  Sources  6  |  Type 2   |  Data and Pad 46 - 1500  |  FCS 4    |

- Preamble 7 bytes, synchronization
- Start frame delimiter 1 byte: Signifies that the next byte begins the destination MAC field
- Destination MAC address 7 bytes: Identifies the intended recipient of this frame
- Source Mac address 6 bytes: identities the sender of the frame
- Type 2 bytes: Defines the type of protocol listed inside the frame, IPv4 or IPv6
- Data and PAD 46 0 1500 bytes: Holds data from a higher layer, typically an L3PDU (IPv4 or IPv6). Sender adds padding to meet the minimum length requirement for this field 46 bytes
- Frame check sequence FCS 4 bytes: provides a method for receiving NIC to determine whether frame experienced any transmission errors

#### Ethernet Addresses
- MAC Addresses are 6 byte 48 bit long 
- Unicast: MAC address represents a single NIC or Ethernet port
- Broadcast: 
- Multicast:
- Source and Destination MAC addresses are added

#### Group Addresses
- Broadcast Address: Frames sent to this address should be delivered to all devices on Ethernet lan, FFFF.FFFF.FFFF
- Multicast addresses: Frames sent to a multicast Ethernet address will be copied and forwarded to a subset of the deices on the LAN that volunteers to receive frames sent to a specific multicast address

#### Ethernet type field or EtherType
- help the network process on routers and hosts, identifies the type of network layer (layer 3) packet that sits inside the Ethernet frame.
- IPv4 is type = 0800
- IPv6 is type = 86DD

#### Frame Check Sequence FCS 
- Math formula and errors marks receiver to discard the frame 

#### Sending data Full duplex  for switches and hubs
1. PC1 builds and sends original Ethernet frame, using own MAC address as source address and PC2s MAC address as destination address
2. Switch SW1 receives and forwards Ethernet frame out of its G0/1 interface to SW2
3. Switch SW2 receives and forwards the Ethernet frame out of its F0/2 interface 
4. PC2 receives the frame, recognizes the destination MAC address as its own and processes the frame.
- Full Duplex: device does not have to wait before sending, it can send and receive at the same time


#### Half duplex and Ethernet shared media 
- Device must wait to send if it is currently receiving a frame, it cant send and receive at same time. 
- Carrier sense multiple access with collusion detection CSMA/CD algorithm avoids collision by unfortunate timing 
- Any switch connected to a old hub needs to have Half duplex enabled on the port. 



## Fiber Cabling 
- Fiber optics use fiberglass
- Core: where the laser shines
- Cladding: light reflects off the cladding back into the core

### Multi mode fiber
- Cable allows for multiple angles (modes) of LED light waves to enter the core
- Less expensive, 10 Gb Ethernet over fiber allow for distances up to 400

### Single mode fiber
- Small diameter core, 1/5th the diameter for multi mode cables for laser to shine though
- Distances of tens of KMs but slightly more expensive SFP/SFP+ hardware

# WANs and IP routing  
- Physical Layer 1
- Datalink layer 2
- Leased line WANS
- Ethernet WANS

## Leased Line WANs 
- service is a physical layer services, delivers bits in both directions at predetermined speed using full duplex
- it acts as if you have a full duplex crossover Ethernet link between two routers
- Leased line uses two pairs of wires, one for each direction of sending data, allows ful duplex operations 
- Telcos put equipment in buildings called central offices COs 
- term is fact that the telco leases the use of the leased line to a customer but the customer does not permanently own the line
- Data link protocols of High Level Data Link Control HDLC and Point to Point Protocol, 
1. HDLC fram can only go to one destination device (router on other end) so destination is implied in address field.
|  HDLC and PPP Fields frame form   |  Ethernet Equivalent     |  Description    |
|-----------------------------------|--------------------------|-----------------|
|  Flag                             |  Preamble SFD            | pattern to show a new frame is arriving  |
|  Address                          |  Destination Address      |  Identities destination device, not interesting for leased PPP topos |
|  Control                          |  N/A                     |  No longer used between routers |
|  Type                             |  Type                    |  Identifies type of layer 3 packet encapsulated inside data portion of the frame  |
|  FCS                              |  FCS                     |  Identifies field used by the error detection process |

### Routers using WAN Data Link
1. TCP/IP network layer focuses on forwarding IP Packets from the sending host to the destination host
2. Routers de-encapsulating and re-encapsulating IP packets
- 802.3 Header, IP Packet, 802.3 Trailer ---> HDLC Header, IP Packet, HDLC Trailer ---> 802.3 Header, IP Packet, 802.3 Trailer 

## Ethernet as a WAN technology 
- Fiber Ethernet link to connect a CPE Router to a service providers WAN
1. customer connects to an Ethernet link using a router interface. 
2. fiber Ethernet link leaves the customer building and connects to some nearby Service provider location called a point of presence POP, service provider uses a Ethernet switch. Inside the SP network SP users any tech it wants to create specific Ethernet WAN serves

- Ethernet WAN
1. WANs by their very nature give IP routers a way to forward IP packets from a LAN at one site over the WAN to another LAN at another site
- 802.3 Header, IP Packet, 802.3 Trailer ---> H802.3 Header (Source = Router 1 G0/1 MAC, Destination = Router 2 G0/0 MAC) , IP Packet, 802.3 Trailer ---> 802.3 Header, IP Packet, 802.3 Trailer 
2. Ethernet Line Service E-Line: the kind of point to point Ethernet WAN services

## IP Routing  
- Internet Protocol IP focuses on job of routing data
- In Network layer TCP/IP two options exist for the main protocol around which all other network layer functions resolve:
1. IP version 4 IPv4
2. IP version 6 IPv6

### Network Layer routing (forwarding) logic
- Send Packet to default router: Host choose where to send IP packets, often to a nearby router, router makes choices of where to send IP packet next
- Default router is also referred to as the default gateway 
- Routing data across the network: 
1. All routers use same general process to route packet: IP Routing Table
2. Table lists IP address groupings, called IP networks and IP subnets
3. When router receives a packet, it compares the packets destination IP address to the entries in the routing able and makes a match. Matching entry also lists directions that tell the router where to forward the packet next
- Delivering data to the end destination 

### How network Layer routing uses LANs and WANs
- Network Link layer thinks about the bigger view of the goal like "send this packet to the specified next router or host"
- Data link layer thinks about the specifics like "Encapsulate the packet in a data link frame and transmit it" 
1. Network Layer logic in a host or router must hand off packet to data link layer protocol
2. Which asks the physical layer to actually send the data.
3. Data link layer adds the appropriate header and trailer to the packet, creating a frame before sending frames over each physical network
- Major steps in a routers internal network layer routing for each packet beginning with frame arriving in routers interface
1. Use data link frame check sequence (FCS) field to ensure the frame had no errors, if errors occurred, discard the frame
- Major steps in a routers internal network layer routing for each packet beginning with frame arriving in routers interface
1. USe data link frame check sequence (FCS) field to ensure the frame had no errors, if errors occurred, discard the frame- Major steps in a routers internal network layer routing for each packet beginning with frame arriving in routers interface
1. Use data link frame check sequence (FCS) field to ensure the frame had no errors, if errors occurred, discard the frame
2. Assuming the frame was not discarded in step 1, discard old data link header and trailer, leaving IP packet 
3. Compare IP packets destination IP address to routing table, find the route that best matches destination address. Rout identifies the outgoing interface of the router and possibly the next hop router IP address
4. Encapsulate the IP packet inside a new data link header and trailer, appropriate for the outgoing interface and forward the frame
- How a router determines which data link address to use is the IP Address Resolution Protocol ARP. ARP dynamically learns the data link address of an IP Host connected to a LAN. Because routers build new data link headers and trailers, and because new headers contain data link addresses, PC/Routers must have way to decide what data link addresses to use

### Rules for groups of IP addresses (Networks and subnets) 
- Subnetting 
1. Two IP addresses, not separated from each other by a router, must be in the same group (subnet)
2. Two IP addresses, separated from each other by at least one router, must be in different groups (subnets)
- IPv4 Header of 4 bytes, for a total of 20 bytes, header lists 32 bit source IP address, 32 bit destination IP address
|  Version  |  Length   |  DS Field |  Packet Length              |
|  Identification                   |  Flags |  Fragment offset   |
|  Time to Live   |  Protocol |     |  Header Checksum            |
|  Source IP Address                                              |
|  Destination IP Address                                         |

### How IP routing protocols help IP routing
- Hosts need to know the IP address of their default router so that hosts can send packets to remote destinations
- Routers need to know routes so they forward packets to each and every reachable IP network and IP subnet 
- Routing protocols for learning routs
1. Each router, independent of routing protocol, adds a route to its routing table for each subnet directly connected to the router
2. Each routers routing protocol tells its neighbors about the routes in its routing table, including directly connected routes and routes learned from other routers
3. Each routers routing protocol listens to messages from neighboring routers and learns routes with net hop router of that route typically being the neighbor from which the rout was learned

## DNS
- hostname: human readable 
- DNS: ip addresses used by the hostname
- Routers treat DNS messages just like any other IP packet, routing them based on destination IP addresses
- DNS defines protocol of working with other DNS servers 

## Address Resolution Protocol ARP
- how a router knows what MAC address to use for destination 
- Method by which any host or router on LAN can dynamically learn the MAC address of another IP host or router on the same LAN
- ARP request: which is a message that makes the simple request "if this is your IP address, please reply with your MAC address"
- ARP reply: which lists both original IP address and matching MAC address
- ARP cache or ARP table: keeps information on MAC and IP addressees 
- See ARP cache by using `arp -a` command

## Ping
- uses Internet Control Message Protocol ICMP, sending a ICMP echo request to another IP  
- uses layers 1, 2, 3 of OSI model
- Only tests basic IP connectivity 

# Implementing Ethernet LANs

## Accessing Cisco Catalyst Switch CLI
- UTP 10/100/1000 meaning unshielded twisted pair 10BASE-T (10 Mbps), 100BASE-T (1000 Mbps), or 1000BASE-T (1 Gbps) no matter the current speed used on the interface
- Interface IDs to identify specific ports
|  Speeds Supported  | Common Name  | Example Switch Interface ID | Valid Abbreviations | 
|---                 |---           |---                          |---                 |
|  10 Mbps           |Ethernet      |ethernet0/0                  |E0/0,Et0/0, Eth0/0  |
|  10/100 Mbps       |10/100        |FastEthernet 0/1             |F0/1, Fa0/1         |
|  10/100/1000 Mbps  |10/100/1000   |GigabitEthernet 1/0/1        |G1/0/1, Gi1/0/1     |
|1G/2.5G/10G         |Multigig      |TenGigabit 1/0/2             |T1/0/2, Te1/0/2     |

## Console: physical port specifically to allow access to CLI
- Old DB-9 nine pins
- UTP rollover cable with RJ-45 connectors on each end. Rollover pinout uses eight wires, rolling the wire at pin 1 to pin 8, pin 2 to pin 7 , pin 3 to pin 6 and so on
- USB connector also needs software driver for PC Os so it knows the device on the other end of the USB is the console of a Cisco device. 
1. Terminal emulator software treats all data as text for user to read.
2. Emulator must be configured to use PCs serial port to match the settings on the switches console port settings, default settings: 9600 Bits/Second, No hardware flow control, 8-bit ASCII, No parity bits, 1 stop bit. 

- Telnet
1. telnet is terminal application and telnet server (the switch). Telnet client, device that sits in front of the user, accepts keyboard input and sends those commands to the telnet server. telnet server accepts text, interprets text as a command and replies back. 
2. Telnet sends all data as clear text data

- Secure Shell SSH
1. SSH encrypts

## User> and Enable# (Privileged) Modes
- USERNAME>`user EXEC mode` also called user mode allows
1. look around but not break anything
2. Exec mode part of the name refers to the fact that in this mode, when you enter a command, the switch executes the command and then displays messages that describe the commands results. 
- USERNAME# `privileged mode` also known as enable mode. 
1. allows more powerful commands
2. moves user from user mode to enable mode 
- `reload` command tells switch to reinitialize or reboot Cisco IOS, only from privileged mode. 
- EXEC: commands that can be used in either user (EXEC) mode or enable (EXEC) mode are called EXEC commands
- `!` are comments
- `show running-config` lists current configuration in the switch
- `enable secret love` config commands defines the password that all users must use to reach enable mode. 
- `login` switch performs simple password check
- `password faith` command defines the password the console user must type when prompted
- `?` provides help for all commands available in the mode
- `debug` issues messages over time as events continue to occur. 

## Configuration Submodes and contexts
- Commands entered in configuration mode update the active conf file, changes to the config occur immediately each time you press the enter key at the end of a command. 
- `interface` 
1. enter interface configuration mode by entering `interface FastEthernet 0/1` configuration command. 
- `configure terminal` EXEC command allows movement from enable mode to global config mode
- `hostname Fred` configures switches name
- `line console 0` movement from global configuration mode to console line configuration mode 
- Common Switch Configuration Modes
|  Prompt   | Name of mode | Context setting commands to reach this mode   |
|---        |---           |---                                            |
|  hostname(config)#   | Global | None - First mode after configure terminal |
|  hostname(config-line)#  | Lane   | line console 0  |
|  hostname(config-if)# | Interface | interface type number |
|  hostname(config-vlan)#  | VLAN   | vlan number  |

## Saving/Storing Switch Configuration files
- RAM: sometimes called DRAM dynamic random access memory used by switch for working storage, the running (active) config file is stored here
- Flash memory: either a chip inside the switch or a removable memory card, stores its Cisco IOS at boot by default, can be used to store any other files, including backup copies of config files
- ROM: Read only memory stores a bootstrap or boothelper program that is loaded when the switch powers on. Bootstrap program then finds the full Cisco IOS image and manages the process of loading Cisco IOS into RAM, at which Cisco IOS takes over operation of the switch
- NVRAM: Nonvolatile RAM stores initial startup configuration file that is used when the switch is first powered on and when the switch is reloaded. 
- `startup-config` stores initial config used anytime the switch reloads Cisco ios in NVRAM
- `running-config` stores currently used config commands. This file changes dynamically when someone enters commands in config mode in RAM, to save you have to copy the running-config file into NVRAM and overwrite the old startup-config file. 
- `copy running-config startup-config` back ups the running config to the startup config file, overwriting the current startup config file with what is currently in the running config file. 
- erase the startup-config file: `write erase` --> `erase startup-config` --> `erase nvram` and then clear out running-config file, simply erase startup-config file and then `reload` the switch and the running config will be empty at the end of the process

STOPPED ON PAGE 111 

# Ethernet LAN switching 

## Switching logic
- either forward the frame out some other ports or ignore the frame
1. Main job: Deciding when to foward a frame or when to filter (not forward the frame), based on the destination MAC address. Table lists MAC addresses and outgoing interfaces relative to that one switch. 
2. Overhead functions: Preparing to forward future frames by learning the source MAC addresses of each frome received by the switch
3. Overhead function: Coooperating with all switches to prevent endless looping of frames by using Spanning Tree Protocol STP
- Example: 
1. Frame came in F0/1
2. Destined for 0200.2222.2222. 
3. Forward Out F0/2 
4. Filter (Do not send) on F0/3, F0/4
- Frames called Known Unicast frames (known unicasts) because the destination address is a unicast address and the destination is known. 

## Learning MAC addresses
- Learn MAC addresses and interfaces to put into its address table
- Listen to incoming frames and examining source MAC address in the frame, and lists interface from which frame arrived. 
- Unknown unicast frame: if there is no matching entry in the table, switches forward the frame out all interfaces (except theincomeing interface), called flooding. 
- Flood unknown unicast frames: if switches dont know where to send it, send it weverywhere
- Flood LAN broadcast frames: frames destined to the ethernet braodcast address of FFF.FFF.FFF, helps deliver a copy of the frame to all devices in the lan

## Avoiding Loops using spanning tree protocol
- Spanning tree protocol STP prevents loops and flooded frames indefenently, STP blocks some ports from forwarding frames so that only one active path exists between any pair of LAN segments
- To avoid Layer 2 loops, all switches need to use STP
- STP causes each interface on a switch to settle into either a blocking state or a forwarding state
1. Blocking: interface cannot forward or receive data frames. IF correct subset of the interfaces is blocked, only a single currently active logical path exists between each pair of lans. 
2. Forwarding: interface can send and receive data frames. 
### LAN Switching logic summary
1. Switches forward frames based on the destination MAC address
- IF destinatinon MAC address is broadcast, multicast or unknown destination univcast (a unicast not listed in the MAC table), the switch floods the frame
- IF the destination MAC address is a known unicast address ( a unicast address found in the MAC table): IF the outgoing interface listed in the MAC address table is different from the interface in which the frame was received, the switch forwards the frame out the outgoing interface. IF the outgoing interface is the same oas the interface in which the frame was receved, the switch filters the frame, meaning that the switch ignores the frame and does not forward it.
2. Switches learn MAC address table entries based on the source MAC address
- For each received frame, note the source MAC address and incoming interface ID
- If not yet in the MAC address table, add an entry listing the MAC address and incoming interface. 
3. Switches use STP to prevent loops by causing some interfaces to block, meaning that they do not send or receive frames. 


## Verifying and Analyzing Ethernet Switching 

- `show mac address-table` to see a switches MAC address table and shows overhead static MAC addresses that we can ignore
- `show mac address-table dynamic` shows all dynamically leanred MAC addresses only. Type column is how the switch learned the MAC address. You can also stattically predefine MAC table entries with port security.
- VLANs virtual LANs: LAN switches forward ethernet frames inside a VLAN. If a frame enters via a port in VLAN 1, then the switch will forward or flood that frame out other ports in VLAN 1 only, and not out any ports that hapen to be assigned to another VLAN 

## Switch Interfaces
- `show interfaces status` shows ports, status, VLAN, Duplex, Speed and type
- `show interfaces f0/1 status` lists status in a single link
- `show interfaces f0/1` displays a detailed set of messages about the interface
- `show interfaces` can have arguments: 
1. with `counters` lists stats about incoming and outgoing frames on the intrerfaces, number of unicast, multicast and broadcast frames (both in and out) and total byte count for those frames

## Finding entries in MAC address Table 
- `show mac address-table` with arguments:
1. `dynamic address 0200.1111.1111` and if address exists, the output lists the address 
- `show mac address-table dynamic interface` for a particual port with arguments:
1. `fastEthernet 0/1` 
- `show mac address-table dynamic vlan` for one vlan with for MAC address table entries with arguments:
1. `1` to show VLAN 1

## Managing the MAC address table for Aging and Clearing
- MAC addresses do not remain in the table indefinitely due to age (timer set to 300 seconds), due to table filling, and using a command
1. `show mac address-table aging-time` shows the global aging time 
- MAC address table uses contnet addressable memory CAM, a physical memory that has great table lookup capibiliites 
- `clear mac address-table dynamic` removes the dynamic entries from MAC address table in enable mode 
1. clear by vlan: `clear mac adddress-table dynamic vlan` + `vland number`
2. clear by interface: `clear mac adddress-table dynamic interface` + `interface-ID`
3. clear by MAC address: `clear mac adddress-table dynamic address` + `mac-address`. 



# Configuring Basic Switch Management
1. Data Plane
- process of forwarding frames received by the switch
2. Control Plane
- Processes that control and change the switcs data plane
- configuration to enable or disable an interface
- control the speed used by each interface
- dynamic processes of Spanning Tree to block some ports to prevent loops
3. Management Plane
- Device Management features
- Telnet / SSH used to connect to the CLI

## Securing user mode and privileged mode with simple passoword
- one password for console users and a different password for telnet users 
- Telnet password,`vty` password. 


Stopped on page 135

