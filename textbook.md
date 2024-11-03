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
- Encapsulate the data supplied by the transport layer inside a newtwrk layer IP header

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

## Etherent physical layers
- Unshielded twisted pair (UTP)
- Kinds of ethernet 
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

- Auto-MDIX automatic medium dependent interface crossover can redirect a strait through pintout to crossover and vicse versa 
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
- Multicast addresses: Frames sent to a multicast Ethernet address will be copied and forwarded to a subset fo the deices on the LAN that volunteers to receive frames sent to a specific multicast address

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
- it acts as if you have a full duplex crossover ethernet link beweeen two routers
- Leased line uses two pairs of wires, one for each direction of sending data, allows ful duplex operations 
- Telcos put equipment in buildings called central offices COs 
- term is fact that the telco leases the use of the leased line to a customer but the customer does not permanently own the line




STOPPED ON PAGE 66
