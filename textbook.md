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
- Transpmit the bits.

## Ethernet LANS
- ethernet connecting devices, with SOHO (small office or home network) with Router, switch and access point for wifi in one device. 


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
- UTP cabling pinouts for 1000BASE-T
   1. Requires 4 wire pairs

### Ports
1. Gigabit ethernet interface converter GBIC (larger than gigabit interfaces, larger than SFPs
2. Small form factor pluggable SFP: replacement for GBICs used on gigabit interfaces with smaller size  taking up less spaces
3. Small form factor pluggable plus SFP+: same size as SFP but used on 10 Gbps interfaces

### NIC transmitters
- Transmitters use pairs 1 and 2 
- Recievers use 3 and 6
- Lan switches do opposite

### LAN switches
- Transmitters use 3 and 6
- Recievers use 1 and 2

## Fiber 


