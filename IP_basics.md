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

## Routing protocols 
- EXAMPLE 

R3 Routing  Table
| Subnet | Interface |  Next Hop |
|-------------- | -------------- | -------------- |
| 168.1.0.0 | G0/1 | N/A |

R2 Routing  Table
| Subnet | Interface |  Next Hop |
|-------------- | -------------- | -------------- |
| 168.1.0.0 | G0/0 | R3 |

R1 Routing  Table
| Subnet | Interface |  Next Hop |
|-------------- | -------------- | -------------- |
| 168.1.0.0 | S0/1/1 | R2 |

- DEF just send messages about new subnets or changes in Subnets, and see which route is most effecient via a routing metric
- Enterprise Routing Protocols
| Routing Protocol | Degree Used |
| --------------- | ----------- |
| OSPF  | High |
| EIGRP | High |
| IS-IS | Medium |
| RIP Version 2 | Low |
| Rip version 1 | None |
|IGRP | None |
- Routers learn about subnets/networks
- Routers create routs to forward packets
- Routers choose best routs amoung multiple options 
- Routers react when links fail



