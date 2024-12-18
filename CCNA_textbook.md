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
- `enable passsword` into enable mode
- `login` tells IOS to enable use of simple shared password
- `enable secret` password-value: configures the enable password as a global config 
- `show running-config` shows configuration in the switch
- local usernames: `username blake secret youdda`

### Config Checklist for shared passwords for console, telnet and enable password
1. Configure enable pssword with `enable secret` password value command
2. Configure console password
- Use `line con 0` command to enter console configuration mode
- Use the `password` password-value subcommand to set the value of the console password
- USe the `login` subcommand to enable console password security using a simple password
3. Configure the Telnet (vty) password:
- Use `line vty 0 15` command to entre vty conf mode for all 16 vty lines (0 - 15)
- Use `password` password-value subcommand to set the value of the vty password
- Use `login` subcommand to enable console password security using a simple password
- Use `transport input all` subcommand to enable Telnet as an input protocolfor the vty lines

### Config local username login for mutiple people. 
1. use `username name secret` password global config command to add one or more username password pairs on local switch
2. Config console use local configure  username and pass pairs
- `line con 0` command to enter console config mode
- `login local` subcommand to enable console to prompt for both usernames and passwords
- use `no password` to remove any existing simple shared password, just for good housekeeping of config file
3. config telnet vty to use locally configured username password pairs. 
- use    `line vty 0 15` to enter vty conf mode for all 16 vty lines 0 - 15
- use `login local` to enable switch to prompt for both username and pw for all inbound telnet users, checked vs list of local users/passwords
- use `no password` to remove any existing simple shared password, just for good housekeeping of config file
- use `transport input all` subcommand to enable telnet as an input protocol foro vty lines- use `no password` to remove any existing simple shared password, just for good housekeeping of config file

## saving users and passwords with external server called authentication, authorization and accounting AAA server
- so you dont have to manually update this on each server

## SSH config process
- Make sure you doing `transport input ssh` to only have ssh, more secure. 
- `show ip ssh` lists status information about ssh server itself
- `show ssh` lists info about each ssh client connected to the switch. 
-Steps on configuing SSH: 
1. `configure terminal` 
2. `hostname sw1`
3. `ip domain name example.com`
4. ` crypto key generate rsa` witch will ask how many bits in modulus and you can write 1024
5. `ip ssh version 2`
6. `line vty 0 15`
7. `login local`
8. `transport input all` 
9. `exit`
10. `username blake secret yoda`
11. `username blake2 secret yoda2`
12. `^z`

## Config web gui
- `no ip http server` global command to disable http port 80 
- `ip http secure-server` global command to enable https port 443 uses tls
- ` ip http authentication` local to define authentication method ot use locally defined usernames 
- `username name priority 15 password` pass-value global command to define one or more usernames with privilge level 15
- `VLAN interface` acts like the switchs own NIC caled switch virtual interface starts in `VLAN 1` for ip configuration, for switch send and recive frames on any of VLAN 1 ports.
- `default gateway` switch communicating outside the local subnet. VS config IP address and mask on one VLAN interface allows the switch to send and receive IP packets with other hosts in a subnet that exists on that VLAN

## config IPv4 on a switch
- swtich configures ipv4 address and mask on VLAN interface
1. `interface vlan 1` command in global config mode to enter interface VLAN 1 config mode
2. `ip address ip-address mask` to assign an ip address and mask 
3. `no shutdown`in config mode to enable the VLAN 1 interface if its not already enabled, this administratively enables and interface on a switch
4. `ip default-gateway ip-address` command in global config mode to config default gateway
5. add `ip name-server ip-address1 ip-address2` command in global cong mode to config the switch to use DNS to resolve names into maitching ip address. 

## config switch to learn its IP address with DHCP
1. enter VLAN 1 config mode by using `interface vlan 1`, enable interface using `no shutdown` if neccessary
2. Assign IP address and mask using `ip address DHCP`

### verify ipv4 on a switch
- `show running-config` shows current config 
- `show interfaces vlan x` which shows detailed status of the vlan interface
- `show dhcp lease` command to see (temp) leased ip addresses
- `show ip default-gateway` 

## other commands
1. history buffer
- `show history` an EXEC command 
- `terminal history size x` sets size of history buffer 
- `history size x` sets default number of history commands 
2. `no logging console` and `logging console` wan to temp not be bothered by sys log messages
3. `logging synchronous` tells IOS to synchronize the syslog message display with the messages requetsted using `show` commands
4. `exec-timeout` can change length of inativity timer and you can set it as 0 minutes and 0 seconds meaning never time out
5. `no ip domain-lookup` global config command which disables IOSs attempt to resolve the hostname into an ip address

# Configuring and verifyng switch interfaces

## Autonogotiation rules 
1. both endpoints send messages, out of band companred to any specific data transmission standards, using fast link pulses FLPs
2. the message declare all supported speed and duplex combinations
3. after hearing the link partner, each device choses fastst speed supported by both devices and the best duplex (full being better than half)

### When only one node uses autonegotioation
- if you disable auto negotitation on both ends of all ethernet links
- if you diable it, use predefined speed and duplex on links, `speed 1000` meaning 10000 mbps or 1 gbps, and `duplex full`. if both ends of link are set up with these same values, the link will work due to matching settings of 1000BASE-T with full duplex
- parallell detection is when speed (detects neighboring devices physical layer standard by analyzing the neighbors incoming frames, use that speed) and Duplex, makes a defualt choice based on speed, if speed is 10 or 100 mbps and full duplex if faster
- LAN Hub that is not new can result in half autonegotitation 
- `show interfaces status` can show operation of autonegotiation on a switch interface 
1. `a-full` full duplex with  the a- meaning the switch learned the value using autonogotiation
2. `a-1000` 1000 mbps with the a- meaning the switch learned the setting using autonegotiation
3. `auto` the interface will use autonegotitation when the link physically workss 

## Auto-MDIX

- automatic medium dependent interface crossover
- gives etherent interface the ability to sense when the attached cable uses the wrong cable pinout and to overcome the problem 
## Other commands
-  `description` allows you to write comments
- `no speed` can remove things like speed, duplex, description, shutdown. otherwise use the `default interface` with the interface-id global config command
- `show interfaces` and `show interfaces descrption` list a two code status named line status and protocol status. example for interface status for notconnect is a no cable, bad cable, wrong cable pinouts with MDIX disabled, speed mismatch or neighboring device is powered off, shutdown or error disabled.

## commkon layer 1 problems on working interfaces
- Runts: frames that did not meet minimum frame size requirements, collisions can cause it.
- Giants: frames that exceed frame size requirements
- Input errors: a total of many counters, inlcuding runts, giants, no buffer, crc, frame, overrun and ignored counts
- CRC: received frames that did not pass the FCS math, can be caused by collisions
- Frame: received frames that have illegal fromat, can be caused by collisions
- Packets output: total num of packets (frames) forwraeded out the interface
- Output errrors: total number of packets (frames) that the switch port tried to transmit but for some problem occured
- Collision: counter of all collission that occure when the interface is transmitting a frame
- Late Collisions: subset of all collisions that happen after 64th byyte of frame, often point to a duplex mismatch

# Ethernet Virtual Lans
- switches 
   1. receve ethernet frames
   2. make decisions on Mac addresses, interface in which frame arrives and interface out which the switch forwards the frame.
   3. Forward (switch) those ethernet frames
- Switches with VLANS
   1. impacts switching logic for each freame becease each VLAN acts as a subset  of the switch ports in an ethernet LAN. of the switch portocol
   2. each ethernet fram to be received in a identifible VLAN
   3. forwarded based on MAC table entries for that VLAN
   4. Forward out ports in that VLAN
- How VLANS work on a single switch
- How VLAN trunking to create VLAN that span across multiple switches
- How to forward traffic between VLANs using a router
- How to configure VLANs and VLAN trunks
- How to statically assign interfaces to a VLAN
- Issues that arrise when using VLAs and trunks 

## Virtual LAN concepts 
- LAN: includes all devices in the same broadcast domain. So when any device sends a broadcast frame, all other devices get a copy of the frame. Lan and broadcast domain are basically the same. 
- Creating VLANS helps limit the number of hosts that receive a single broadcast frame reduces the number of hosts that waste effort processing undeeded broadcasts, and reduces secruity risks because fewer hosts see frames sent by any one host. Also helps solve problems more quickly, because failure domain for any problems is the same set of devices as thse in the same broadcast domain, and reduces workload for spanning treee protocol by limiting a VLAN to a singlec access switch. 

## Multiswitch VLANS using trunking 
### how to
- simply configure each port to tell it the VLAN number to which the port belongs to
- multiple switches you have to consider additional concepts about how to forward traffic between switches via VLAN trunking on links between switches
- VLAN trunking
   1. causes the switches to use a process called VLAN tagging
   2. sending switch adds another header to the frame before sending it over the trunk
   3. extra trunking header includes VLAN identifier (VLAN ID) field so that sending switch can associate frame with particular VLAN ID and receiving switch can then know in what VLAN each frame belongs
- tunking allows switches to forward frames from multiple vlans over a sing physical connection by adding a small header to the ethernet frame

## Inter Switch Link ISL and IEEE 802.1Q 
- Trunking protocols
- 802.1Q tags each frame with VLAN ID, with a extra 4 byte header into the origional frames etherent header, making it a 12 bit VLAN ID field supporting up a max of 212 VLANS but in practice supporting 4094 vlans
- VLAN IDs are seperated into 2 ranges, normal (1 to 1005) and extended (1006 to 4094).
- Extened range vlans are configured with VLAN Trunking Protocol VTP

## Forwarding data between VLANS
- LAN switches that forward data based on Layer 2 logic receive ethernet frames (layer 2 concept) look at destination Etherent MAC address (layer 2 address) and forward ethernet frame out some other interface. Layer 2 switches will not forward data between VLANs 

## Routing patcks between VLANs with a router
- devices in a VLAN need to be on the same subnet, devices in differnet VLANs need to be in different subnets 
- to forward packets between VLANs, network must use devices that acts as a router, (whether thats a switch that can perform some functions like a router)
- Devices that can perform Layer 3 routing functions called multilayer switch or Layer 3 Switch

## Creating VLANs and assigning access VLANS to an interface 
- switch must be configured to believe that VLAN exists in order to forward frames in a particular VLAN
- must have non-trucking interfaces called access interfaces or static access interfaces assigned to the VLAN and or trunks that support the VLAN
1. configure a new VLAN in config mode use `vlan vlan-d` command in global configuration mode to create the VLAN and to move the user into VLAN config mode
2. optional, use the `name name` command in VLAN config mode to list a name ofr the VLAN. If not configured, the VLAN name is VLANZZZZ, where ZZZZ is the 4 digit decimal VLAN ID
3. for each access interface, use `interface type number`command in global config mode to move into interface config mode for each desiered interface
4. Use `switchport access vlan id-number` in command interface congif mode to specify the VLAN num associated with that interface
5. optional, use `switchport mode access` command in interface conig mode to make this port always operate in access mode (to not trunk). 


## VLAN Trunking Protocol
- turn off by using `VTP transparent mode` or `vtp mode tranparent` global command or `vtp mode off` 

## VLAN trunking configuration 
- `switchport mode trunk` and then create VLAN trunk that supported all VLANs known oto each switch
### trunking administrative mode options with `switchport mode` command
- `access` always ac as an access nontrunk port
- `trunk` always act as a trunk port
- `dynamic desirable` initiates negotiatin messages and respods to negotiation messages to dynamically chose whether to start using trunking
- `dynamic auto` passively waits to reciecve trunk negotiation messsages at which point the swithc will respond and negotiate whether to use trunking
- `show interfaces gigabit 0/1 switchport` to show if the initial (default) state is trunking or not
- `show interfaces trunk` command lists information about all interfaces that currently operationally trunk, lists interfaces that curerently use VLAN trunking 
- `switchport mode dynamic desirable` asks switch to both negotiate as well as to begin the negotiation process rather than waiting on the other device
- `show interfaces gi0/1 switchport` will show output of intercaes like admin mode, operational mode and stuff
- `show vlan id 2` shows info on the VLAN
### expected trunking operational mode based on configured administrative modes 
|  administrative mode  |  access   |     dynamic auto   |  Trunk | Dynamic desirable  |
|  -------------------- |---------- |------------------  |------- |------------------  |
|  access               |  access   |  access            |dont use|  access            |
|  dynamic auto         |  access   |  access            |trunk   |  trunk             |
|  trunk                |  dont use!|  trunk             |trunk   |  trunk             |
|  dynamic desirable    |  access   |  trunk             |trunk   |  trunk             |
- recommendes disabling trunk negotiation on most ports for better security, esp with ports without `switchport mode access`, like ports with statically configured to trunk with `switchport mode trunk` DTP still operates. disable DTP negotiations altogether using `switchport nonenegotiate` 

## implementing interfaces connected to phones, data and voice LAN concepts
- private branch exchange PBX  is connected to a IP phone with a port that also connects the PC
- Data VLAN: same idea and config as access VLAN on a access port but defined as the VLAN on that link for forwarding traffic for the device connected to the phone onthe desk, like the users PC
- Voice VLAN: VLAN defined on the link for forwarding the phones traffic. Traffic in this VLAN is typically tagged with a 802.1Q header. 
### data and voice VLAN config and verification 
- configuring a switch port to support IP phones with their planned voice and data VLAN IDs is easy.
- making sence of `show` command is hard, as voice frames flow with the 802.1Q header 
1. use `vlan vlan-id` command in global config mode to create the data and voice VLANs if they do not already exist on the switch
2. configure the data VLAN like an access vlan as usual. A: use `interface type number` command in global config mode to move interface config mode. B: use `switchport access vlan id-number` command in interface config mode to define data VLAN. C: use `switchport mode access` command in interace config mode to make the port always operate in access mode (not trunk mode) 
3. use `switchport voice vlan id-number` command in interface conf mode to set the voice VLAN ID
- check the status of the data VLAN (access VLAN) and Voice VLAN by using `show interfaces switchport  for details about the access ports. 
### key takeaways for IP telephony ports on switches
- configure ports like normal access port to begin: config it as a static access port and assign it an access VLAN
- add one more command to define the voice VLAN (`switchport voice vlan vlan-id`) 
- look for mention of voice LVNA ID, butno other facs in the output of the `show interfaces type number switch` command
- look for both the voice and data (access)  VLAN IDs in the outut of the `show interfaces type number` trunk command.
- do not expect to see the port listed in the list of operational trunks as listed by the `show interfaces trunk` command

## troubleshooting VLANs and VLAN trunks
### steps
1. confim correct access VLANs have been assigned
2. confirm all vlans are both defined and active
3. check allowed VLAN lists on both ends of each trunk to ensure all VLANs are intended to be used are included
4. check for incorrect trunk config settings that result in one switch operating as a trunk, with neighboring switch not operating as a trunk
5. check native VLAN settings on both ends of the trunk to ensure the settings match

### 1. confim correct access VLANs have been assigned
- commands that can find access ports and vlans

|  exec command         | description                                                              |
|--------------------   |------------------------------------------------------------  |
| `show vlan brief` or `show vlan` | lists each VLAN and all interfaces assigned to that VLAN but not operational trunks   |
|  `show vlan id number` | lists both acess and trunk ports in the vlan    |
|  `show interfaces status` | on ports operating as access ports, it lists the access VLAN and on ports operating as trunk ports, it lists word trunk|
| `show interfaces type number` or `number switchport` | identifies interfaces access VLAN and voice VLAN, plus the configured and operational mode (access or trunk) |
| `show mac address-table` | lists MAC table entries, including associated VLAN     |
- if the interface is assigned to the wrong VLAN, use the `switchport access vlan vlan-id` interface subcommand to assign the correct VLAN ID

### enabling and disabling vlans on a switch
- disable (`shutdown`)
- enable (`no shutdown`) 
- `no` or `shutdown vlan number` 
### trunking issues
- easily avoided by checking confugraion and by checking trunks operational state (mode) on both sides of the trunk by `show interfaces trunk` and `show interfaces switchport` 
### how to identify which LVANS a particual trunk port currently supports
1. `show interfaces interaface-id trunk` command lists info  only about operational trunks. this means the VLAN has not been removed from allowed VLAN list on the trunk as configured with `switchport trunk allowed vlan` interface subcommand, and the VLAN exists and is active on the local switch as seen in `show vlan` command and that the VLAN has not been VTP pruned from the trunk bc the swithc has dissabled VTP as seen in `sho spanning-tree vlan vlan-id` command. 
2. `switchport trunk allowed vlan` method to administraivly limit VLANs whose traffic uses a trunk 
3. `show interfaces trunk` command creates three separate lists of vlans. 

|  list position  | heading         |  reasons                                                                                |
|-----------------|-----------------|-----------------------------------------------------------------------------------------|
|  first          |  vlans allowed  | vlans 1-4094 minsu those removed by `switchport trunk allowed` command                  |
|  second         |  vlans allowd and active |  first list minus VLANs not defined to local switch, minus those VLANS in shutdown mode |
|  third          |  vlans in spanning tree  |  second list, minus vlans in an STP blocking state for that interface, minus vlans VTP pruned from the trunk | 
- it is possible to set native VLAN ID to different VLans on either end of the trunk using `switchport trunk native vlan vlan-id` command


stopped at chapter 9 page 222

# Spanning Tree Protocol 
- STP allows ethernet LANs to have redundant links in a LAN while overcoming the known problems when adding those extra links, allows redundancy for when links fail.
- RSTP rapid spanning tree protocol is used in more modern networks
- STP and RSTP strike a balance allowing switches to block ports so that these ports do not forward frames with, but STP/RSTP does not block too many ports and frames have a short life and do not loop around the network indefinitely. 
- ports are checked with as a noraml state for frames in a STP/RSTP `forwarding state` and a blocking `blocking state` which blocks all traffic 
## Needing STP 
- if no STV/RSTP some ethernet frames would loop around the network for a long time 
- just one looping frame causes a braodcast storm when frames loop around a LAN indefinitely 
### classes of problems caused by not using STP in redundant LANS
1. broadcast storms: forwarding of a frame repeatedly on the same links, consuming significant parts of the links capacities
2. MAC table instabiliites: continual updating of a switchs MAC address table with incorrect entries, in reaction to looping frames, resuliting in frames being sent to wrong locations
3. multiple frame transmission: a side effect of looping frames in which multiple copies of one frame are delivered to the intended host, confusing the host
### what STP does
- STP/RSTP prevents loops by placing each switch port in either a forwardig state or a blocking state
- interfaces in a forwarding state act as normal, forwarding and receving frames
- interfaces in a blocking state do not process any frames except STP/RSTP messages
- interfaces that block do not forward user frames, do not learn MAC addresses of received frames and do not process received user frames
- "STP convergence" is process in which switches collectively realize that something has changed in the LAN topologoy and determine whether they need to change which ports block and which ports forward. 
- term bridge and switch is synonymous 
- spanning tree algorithm chosses interface that should be in forwardng statys, any other interafce not chose in in a blocking state. 
### reasons for forwarding or blocking 
|  characterization of port   |  STP state   |  Description             |
|-----------------------------|--------------|--------------------------|
|  all root switches ports      |  forwarding   |   root switch is always designated switch on all connected segments   |
|  each nonroot switcs root port|   forwarding  |  lowest root cost, port though which switch has least cost to reach root switch   |
|  each LANS designated port     | forwarding   |  switch forwarding the hello on the segment, lowest root cost, is designated switch for that segment|
|  all other working ports    |  blocking    |  port is not used for forwardin user frames, nor are any frames received on these interfaces considered for forwarding |

### STP bridge ID and Hello BPDU
- Bridge ID (BID) based on a MAC address in each switch
- Bridge Protocol Data Units BPDU which switches use to exhancge info with each other switch
- Hello BPDU lists many details in these BPDU messgages, includes the unique BID so swtiches can tell which switch sent wich hello BPDU
- fields in the STP Hello BPDU

|  field          |  description                       |
|-----------------|------------------------------------|
|  root bridge ID | bridge ID of the switch that the send of the Hello currently beleives to be root switch |
|  senders bridge ID |  bridge ID of the switch sending this hello BPDU    |
|  senders root cost |  STP/RSTP cost between this switch and current root |
|  timer values on the root switch  |  includes the hello timer, MaxAge timer and forward delay timer |

### elevcting the root switch
- root switch is with the liwest numeric value for the BIDs
- if there is a tie, the lowset switch MAC wins 

### choosing each switchs root port 
- second part of STP/RSTP process is for each non root switch chooses itone and only root port RP
- a switchs RP is its interface thorough whicvh it has the least STP/RSTP cost to reach the root switch least root cost
- default port costs based on operating speed of the link, not the max speed

|  ethernet speed | IEEE costs old  | IEEE Costs new  |
|-----------------|-----------------|-----------------|
| 10 mbps         |  100            |  2,000,000      |
|  100 Mbps       |  19             |  200,000        |
|  1 Gbps         |  4              |  20,000         |
|  10 Gbps        |  2              |  2000           |
|  100 Gbps       |  NA             |  200            |
|  1 Tbps         |  NA             |  20             |

### STP activity when the network remains stable
1. root creates and sends out hello BPDU with root cost of 0, out all its working interfaces and those in a forwarding state
2. nonroot swtiches receive hello on their root ports, after changing the hello to list their own BID as the senders BID and listening that switchs root cost, the switch forwards the Hello out all designated ports
3. Steps 1 and 2 repeat every hello time until something changes 

### STP Timers that manage STP convergence 
- when a switch fails to receive a hello on its root port, it knwos there is a problem. if a switch fails to receve hellos or recieves a hello that lists a different detail, something had failed.  so the switch reacts and starts process of changing the spanning tree topology. 

|  Timer |  Default value  |  Description                            |
|---     |---              |---                                      |
|  hello |  2 seconds      |  time between Helllos created by root   |
|  MaxAge|  10 times Hello |  how long any switch should wait, after ceasing to hear hellows, before trying to change STP topology  |
|  Forward delay  |  15 seconds  |  when interface changes from blocking to forwarding. Port stays in interim listening state, then interim learning state for num of secnds defined by forward delay timer |

### STP changing interface states 
- Roles relate how STP analyzes Lan topology on weather to send or receve frames
- forwarding state is faster transition than a blocking state
- when a port that formerly blocked needs to transiition to forwarding, the switch puts port though two intermediate interfce states which help prevent temporarly loops
1. Listening: state where the switch does not forward frames, switch removes old MAC addresses that no frames are received from
2. Learning: do not forward frames, but switch begins to learn MAC addresses of frames recienved on the interface.
- STP = from blocking --> listening --> learning --> forwarding state


## Rapid Spanning Tree Protocol RSTP
- react quickly: Each switch independently generates its own Hellos and RSTP allows for queries between neighbors rather than waiting on timers to expire as a means to avoid waiiting to learn info. 

### Similarities with STP and RSTP 
- wSTP and STP elect the root switch using same rules and tiebreakers
- RSTP and STP switches select root ports with same rules
- RSTP and STP elect designated ports on each LAN segment with same rules and tiebreakers
- RSTP and STP place each port in either forwarding or blocking state, although RSTP calls the blocking state the discarding state 

### RSTP avoids waiting for a timer to expire
- RSTP allows for switch to replace root port without waiting to reach a forwarding state
- RSTP adds a mechanism to replace designated port witout any waiting to reach a forwarding state 
- RSTP lowers waiting times for case in which RSTP must wait for a timer `

### Port rols in RSTP
- Root port: nonroots switchses best path to the root
- Alternate port: port that will be used to replace the root port when the root port fails
- Designated port: switch port designed to forward onto a collision domain
- Backup port: port that will be used to replace a desinganted port when a designated port fails
- Disabled port: port in a nonworking interface state that is anything other than connected up/up 

STOPPED ON PAGE 241



