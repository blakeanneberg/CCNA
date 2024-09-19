# Subnet ID patterns 

1. If using 1 mask to subnet 1 network:
- # of subnets is predictable 2^s
- Subnet IDs are predictable
- Predictable Size: 2^H (H is based on the subnet mask)
2. Concept only valid when not using Variable Length Subnet Mask
- VLSM: means >1 Mask in 1 network

# Using classful addressing logic to identify the number of subnets
- Classless Addressing is Prefix + Host = 32
- Classful addressing is Network (A 8, B 16, C 24) + Subnet + Host = 32.
- # of subnets 2^s and # of hosts 2^h-2

# Classful rules to analyze any mask
- | Network | Subnet | Host |
1. # Network bits (N) always exist at beginning, with # based on class
   - Class A: 8
   - Class B: 16
   - Class C: 24
2. # Host Bits (H) always exist at the end, with # based on # of binary 0s
3. # Subnet bits (S) may or may not exist!
   - S has a value so that N + S + H = 32 (the # bits in a mask) 
   - If S = 0, the mask is the default mask for the class
   - If S > 0, the mask is NOT the defualt mask. 

# Finding all subnets: Exactly 256 subnets
## The Zero Subnet
- Every Subnetted Network has one zero Subnet!
- Formal: all binary 0s in the subnet part of the subnet ID
- Useful facts: Numerically lowest subnet ID, Subnet ID = classful ID
-  IPv4 Address Classes
| Class | First Octet values | Purpose | # of networks | Hosts per network (2^H -2) |
|-------|--------------------|---------|-----------|--------|
| A     | 1-126 First octet of 0 or 127 reeserved for specal uses | Unicast (large networks|  126 (~2^7) | 16777214 |
| B     | 128-191 Unicast (medium sized networks) | 16,384(2^14) 65,534 | 
| c     | 192-223 Unicast (small  networks) | 2,097,152(2^21) | 254 |
| D     | 224-239 Multicast    | | |
| E     | 240-255 Reserved (formerly experimental | | |

## Making list of subnets
1. Start with zero subnet (which equals the network ID) 
2. Create the next subnet ID, based on previous subnet ID
- Network part: What class of network is it (A,B or C)? Copy down.
   - Class A: 8
   - Class B: 16
   - Class C: 24
- Host part: Find the part that only has 0s, so H = 8. Copy Down 
- Subnet part: Subtrack 256 minus Subnet mask number to get the magic number, then add that new number individually to get Subnet count numbers. 
- Network ID is the Zero Subnet.
3. Stop with the broadcast subnet is the last number before 256.
- IF the next subnet ID has a 256, 


## Finding ALL subnets
1. Set up the problem
- Write the mask first, followed by Network ID
- Leave space for more Subnet IDs below
2. Identify and Proess Network (Only) octets
- Apply Class A, B or C, rules to determin 1, 2, or 3 Network Octets
- A: 1-126 
- B: 128-191
- C: 192-223
- D: 224-239
- E: 240-255

- Copy Network ID to ALL subnet IDs for all network octets
3. Identify and process host (only) octets
- Octets with DDN mask octet = 0 are host only octets
- Copy network ID to subnet IDs for all host octets
- (Also... Host octet values of subnet IDs will be 0)
4. Process the cotets w/ subnet bits
- Details to be determined

### >1 subnet octets
| Network Octet   | all subnet octet | partial subnet octet | host octet      | 
| copy down       |                 |                       |     copy down
| Copy NetworkID  | 0..255, by 1s   | Add magic, up to 256  | copy down the 0 | 

## Two subnet octets, class A 
1. create the first block of subnet IDs 
- first subnet ID: same number as network ID
- Create first block by changing rightmost subnet octet:
-- calcuclate magic number for that octet
-- find multiples of the magic number from 0 though 255
2. because two subnet octets exist
- create 256 blocks like the first block
- one block for each value 0..255 in the subnet octet on the left
### 2 subnet octets
| Network Octet   | all subnet octet | partial subnet octet | host octet      | 
| copy down       |                 |                       |     copy down
| Copy NetworkID  | =0 for a block, =1 for a block though 255 | multiples for magic number | copy down the 0 | 

## Two subnet octets, class B 
1. create the first block of subnet IDs 
- first subnet ID: same number as network ID
- Create first block by changing rightmost subnet octet:
-- calcuclate magic number for that octet
-- find multiples of the magic number from 0 though 255
2. because two subnet octets exist
- create 256 blocks like the first block
- one block for each value 0..255 in the subnet octet on the left
### 2 subnet octets, class B 
| Network Octet   | Network Ocetet  | all subnet octet | partial host octet    | 
| copy down       | copy down       |                    |                       |
| Copy NetworkID  | Copy NetworkID   |  =0 for a block, =1 for a block though 255 |  multiples for magic number |


## Find the number of host addresses
1. Write the mask in prefix format /p convert as needed
2. Find H: The number of host bits
- H = 32 - P
3. Find the size of the subnet
- 2^H: the size including reserved numbers
- 2^H - 2: the size including reserved numbers, usable addresses in subnet.

## Find the number of subnets
1. Write two key input facts:
- Mask in prefix format /P convert as needed
- The network class A, B or C
2. Find number of network, subnet and host bits
- H = 32 - P
- N = 8, 16, or 24 based on Class A, B and C respectivly 
- S = P - N, or S = 32 - N - H
   - Class A: 8
   - Class B: 16
   - Class C: 24
3. Find the number of subnets
- 2^S: the number of subnets



### Example

- /19
1. /P = /19
2. H = 32 - 19 = 13
3. 2^13 = 8192 and 2^13 - 2 = 8190

- /25
1. /P = /25
2. H = 32 - 25 = 7
3. 2^7 = 128 and 2^7 - 2 = 126



###
Network: 172.28.0.0
Mask: 255.255.255.252
172.28.0.4
172.28.0.8
172.28.255.248
172.28.255.252

### 

Network: 10.0.0.0
Mask: 255.255.255.240

10.0.0.0
10.0.0.16
10.0.0.32
10.255.255.224
10.255.255.240

### Examples
1. Network: 10.0.0.0 Mask: 255.255.240.0 
- 10.0.0.0
- 10.0.0.1
- 10.0.16.0
- 10.0.32.0
....
- 10.255.192.0
- 10.255.208.0
- 10.255.224.0
- 10.255.240.0

### List all subnets
1. Network 172.21.0.0 Mask 255.255.255.0
- 1st subnet: 172.21.0.0
- 2nd subnet: 172.21.1.0
- 3rd subnet: 172.21.2.0
- 4th from end of list: 172.21.252.0
- 3rd from end of list: 172.21.253.0
- 2nd from end of list: 172.21.254.0
- Last Broadcast subnet: 172.21.255.0

2. Network 172.22.0.0 Mask 255.255.0.0 o
- 1st subnet: 172.22.0.0
- 2nd subnet: 172.22.1.0
- 3rd subnet: 172.22.2.0
- 4th from end of list: 172.22.252.0
- 3rd from end of list: 172.22.253.0
- 2nd from end of list: 172.22.254.0
- Last Broadcast subnet: 172.22.255.0

3. Network 172.23.0.0 Mask 255.255.255.0 o
- 1st subnet: 172.23.0.0
- 2nd subnet: 172.23.1.0
- 3rd subnet: 172.23.2.0
- 4th from end of list: 172.23.252.0
- 3rd from end of list: 172.23.253.0
- 2nd from end of list: 172.23.254.0
- Last Broadcast subnet: 172.23.255.0

4. Network 172.24.0.0 Mask 255.255.255.0 o
- 1st subnet: 172.24.0.0
- 2nd subnet: 172.24.1.0
- 3rd subnet: 172.24.2.0
- 4th from end of list: 172.24.252.0
- 3rd from end of list: 172.24.253.0
- 2nd from end of list: 172.24.254.0
- Last Broadcast subnet: 172.24.255.0

5. Network 16.0.0.0 Mask 255.255.0.0
- 1st subnet: 16.0.0.0
- 2nd subnet: 16.1.0.0 
- 3rd subnet: 16.2.0.0  
- 4th from end of list: 16.252.0.0 
- 3rd from end of list: 16.253.0.0 
- 2nd from end of list: 16.254.0.0 
- Last Broadcast subnet: 16.255.0.0 

6. 
Ended lesson 20 video 10.1 


