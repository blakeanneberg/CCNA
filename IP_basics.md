# Notes from Cisco Subnetting. 

# IP Addressing 
| Network   | Host | Dotted Decimal Notation DDN | 
|--------------- | --------------- | --------| 
| 0001010 | 00000000 00000000 00000111 | 10.0.0.7 |

## IP address for each LAN interface
- For different interfaces, need different IP addresses.


## IP addresses as Source/Destination
- IP Packet has a Source IP and a Destination IP

## Subnet Identifer
- Address + Mask = Subnet ID

## IP address
- RFC 791
- Identify an interface connected to TCP/IP network
- Destination and source of IP packets
- A Key used by Routers for Routing Table Lookups
- Value that when combined with a mask identifies a subnet

## IP routing 
- Routing table 
| Subnet    | Interface | Next Hop |
|---------| -------- | ---------- |
| 168.1.0.0 | Serial0/1/1 | 2.2.22. |

