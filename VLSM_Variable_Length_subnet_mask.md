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
