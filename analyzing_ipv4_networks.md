# IPv4 networks vs IP Subnets

# IPv4 Subnet
- Predictable set of consecutive numbers
1. Subnet ID: lowest number in the subnet
2. Address range: numbers between 
3. Subnet broadcast address: highest number in the subnet
- Set of predictable sizes that are powers of 2
1. Theoretical size: 2^H (H is based on the subnet mask) 
2. Useable size: 2^H - 2
3. Two reserved numbers: (subnet ID, Subnet broadcast address)
- A Subset of an IP network

# IPv4 Address Classes
| Class | First Octet values | Purpose | # of networks | Hosts per network (2^H -2) |
|-------|--------------------|---------|-----------|--------|
| A     | 1-126 First octet of 0 or 127 reeserved for specal uses | Unicast (large networks|  126 (~2^7) | 16777214 |
| B     | 128-191 Unicast (medium sized networks) | 16,384(2^14) 65,534 | 
| c     | 192-223 Unicast (small  networks) | 2,097,152(2^21) | 254 |
| D     | 224-239 Multicast    | | |
| E     | 240-255 Reserved (formerly experimental | | |

## Class A 
- 1-126 octet are same in first octet, but then differ in the last three octet
- Network ID is same first octet
- Network Broadcast address is same first octet 

## Class B
- 128-191 octet have first two octets be the same, and last two will differ
- Network ID has same first two octets 
- Network Broadcast address has same first two octets

## Class c
- 192-223 octet have first three octets be the same, last octet will differ
- Network ID has same first three octets
- Network Broadcast address has same first three octets

## Default Mask
- A Mask that does not subnet a classful network
- One Default mask for each class
- Not the same as a subnet mask, which does subnet a classful network, and is any mask other than a default mask for that class
| Class | Default Masks |
|-------|---------------|
| A     | 255.0.0.0     |
| B     | 255.255.0.0   |
| C     | 255.255.255.0 |

# IPv4 Network
- Predictable set of consecutive numbers
1. Network ID: Lowest number in the network
2. Address Range: Numbers in between
3. Network broadcast address: Highest number in the network
- A set with three specific predictable sizes
1. Theoretical sizes: 2^8, 2^16 or 2^24
2. Usable sizes: 2^8 - 2, or 2^16 - 2, or 2^24 - 2
3. Two reserved numbers: Network ID, Network broadcast address
- Usable as: 
1. Use as one set  of addresses (like subnets)
2. Subdivide into smaller subsets to create subnets

# Using a network in a topology
- VLAN
- Serial Link
- Ethernet WAN

# Options for enterprise IPv4 Addresses

1. Public network
- Private
- NAT
- CIDR

2. Private networks
- Within orgs
   1. + NAT: clients can communicate to internet
   2. Private network 10 is the reserved 
   3. A router with NAT will change a internal packet's source IP like 10.1.1.1 to another IP for outside the enterprise netowrk and on the wider world wide web IP like 200.1.1.1 
- Class of Private networks
| Class of Networks  | Private IP networks         | Number of networks |
|--------------------|-----------------------------|--------------------|
| A                  | 10.0.0.0                    | 1                  |
| B                  | 172.16.0.0-171.31.0.0       | 16                 |
| C                  | 192.168.0.0-192.168.255.0   | 256                | 

3. Classless Interdomain Routing (CIDR) block
- Public address block
- Sizes are any 2^H, so less waste
- Normally relies on also using Private Network and NAT
- Assign public addresses using any mask
- Allocates only the smallest block to meet need, saving addresses 
- example IP 192.0.2.0/29 means you get IP addresses from 192.0.2.0 to 192.0.2.7






