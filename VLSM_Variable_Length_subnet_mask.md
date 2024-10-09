# Variable Legnth Subnet Masks
- Using >1 mask (like /24 and /16) in subnet of one classful network (A, B or C)
   1. Example: 172.16.32.0 /22 and 172.16.8.0 /30 and 172.16.64.0 / 25 where 172.16 subnets of class be where /30 and /25 and /22 are different VLSM subnets.
- If VLSM is not used, you can predict number of subnets. But if VLSM is used you cannot predict number of subnets.
- Use VLSM to conserve your IP address space
- No VLSM is simplier to operate though.
   1. Example: Need 625 subnets
   | Subnet Type | # subnet needed | # hosts/subnets needed | Mask | Available hosts per subnet |
   |-------------|----------------|-------------------------|--------|-------------------------|
   | core LAN     | 25              | 200                   | /24    | 254    |
   | Branch LAN   | 400             | 10                    | /24    | 254    |
   | WAN          | 200             | 2                     | /24    | 254    |
   So you would need 625 subnets with /24. 
   3 class B networks required! 
   2. Example: Need 625 subnets
   | Subnet Type | # subnet needed | # hosts/subnets needed | Mask | Available hosts per subnet |
   |-------------|----------------|-------------------------|--------|-------------------------|
   | core LAN     | 25              | 200                   | /24    | 254    |
   | Branch LAN   | 400             | 10                    | /28    | 14     |
   | WAN          | 200             | 2                     | /30    | 2      |
   So you would need 625 subnets with /24. 
   3 class B networks required! 
- Usually see a /30 for WAN link and a couple different sizes for LAN implementations
- Conserve IP addresses, due to being department.
- VLSM: > 1 mask used within a network
   1. Cannot answer: how many subnets in the network?
   2. Cannot answer: how many hosts in in every subnet?
   3. CAN answer: how many hosts in a specific subnet? 
- Finding overlapping subnets in a desgin, can have overlap, even when the subnet IDs are not the same number. 
   1. Find the range of addresses in each subnet by:
      - Finding the subnet ID
      - Finding the subnet broadcast address
   2. List the subnets in order by subnet ID, low to high
   3. inspect the ranges for overlaps
   EXAMPLE: 
      - Mask: 172.21.0.201 /25 or 255.255.255.128
      - Subnet ID: 127.21.0.0
      - Broadcast: 127.21.0.255 
   EXAMPLE:
      - Mask: 172.21.1.1 /23 or 255.255.254.0
      - Subnet ID: 127.21.0.0 
      -Broadcast: 172.21.1.255
   EXAMPLE: 
      - Mask: 172.22.101.1 /21 or 255.255.248.0
      - Subnet ID: 172.22.96.0
      - Broadcast: 172.22.103.255
   EXAMPLE: 
      - Mask: 172.22.107.9 /21 or 255.255.254.0 
      - Subnet ID: 172.22.106.0
      - Broadcast: 172.22.107.255 

   EXAMPLE: 
      - Mask: 172.22.113.5 /20 or 255.255.240.0
      - Subnet ID: 172.22.112.0
      - Broadcast: 172.22.127.255 




- Adding a new subnet to a VLSM design
   1. Calculat range of current exhisting subnets and then think about possible subnets to be created with the mask and then compaire the two. 
   2. What mask will the new subnet use?
   3. what are all subnets of the network when using that mask? 
   4. which of the new subnets do not overlap with the old?
   5. Choice: use any of the subnets that do not overlap?

- Finding the correct IP route, and finding the matching logic
   1. If only one route matches, simple, use that route
   2. if  >1 route matches: use most specific route (router will use longer prefix like /30 vs /20 route, ie >> /P mask)
   3. Does not use "first line matched" per `show ip route` output
   4. Address may match >1 routing table entry
      - mistakes (incorrect address or mask configuration) 
      - legitimate (route summarization)

- Adding new VLSM subnet Process
   1. List candidate subnet
      - Mask: pick a mask (figure out the mask, then 256 - mask, increment by the remainder)
      - Subnets: Calculate all possible subnet IDs of the network using that mask
      - Address RAnges: also list the subnet braodast of each subnet 
   2. List existing subnets: 
      - Subnets: create a list of subnet IDs in numeric order
      - Address Ranges: also list the subnet broadcast address of each subnet
   3. Compare candidates to the existing subnet 



# Review: number of host addresses in a subnet 
- # hosts/subnet = 2^H - 2
- were looking for he number of zeros in the binary mask (ie the host part at the end of the mask)
- example: LAN: /28 
1.  /P = /28
2. H = 32 - 28 = 4
3. 2^4 = 16
4. 2^4 - 2 = 14 addresses per subnet 
- example: WAN: /30
1. /P = /30
2. H = 32 - 30 = 2
3. 2^2 = 4
   2^2 - 2 = 2   
- example: LAN: /24
1. /P = /24
2. H = 32 - 24 = 8
3. 2^8 = 256
   2^8 - 2 = 254



