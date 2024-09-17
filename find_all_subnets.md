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
- IF the next subnet ID has a 256, STOP!
- Previous subnet is th elast subnet (and alos the broadcast subnet). 

### Examples
1. 172.16.0.0 mask 255.255.255.0

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
 ENDED ON LESSON 17, 17.3 VIDEO
