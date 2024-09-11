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
- + NAT: clients can communicate to internet
3. Classless Interdomain Routing (CIDR) block
- Public address block
- Sizes are any 2^H, so less waste
- Normally relies on also using Private Network and NAT






