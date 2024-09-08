# Subnet
## Topological
- Addresses in the same VLAN
    1. Should be in same subnnet VLAN in layer 2 and subnet is layer 3
    2. Addresses on the same WAN link intefaces on the same WAN `link should be in the same subnet 
    3. Addresses on one subnet shoud not be seperated by a router

## Subnet facts
- Subnet ID: lowest number in the subnet
- Address Range: nunbers in between
- Subnet Broadcast Address: highest number in the subnet
- Subnet size and starting blue based on 2^h
    1. Two reserved numbers (Subnet ID and Subnet Braodcast Addrewss) 
    2. Useable Size is 2^h - 2
- To Subnet
    1. subdivide a larger set of IPv4 addresses into multiple smaller sets
    2. Begin each subnets range of numbers no at an arbitrary number, but at a predicitable number, an integer multiple of 2^H
- Mast
    1. 2^H is really meaning H is a mask
    | Mask 1s | Mask 0s |
    | --------| --------|
    |Prefix (P) | Host(H) |
    | 32 bits            |

