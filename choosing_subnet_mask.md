# Logic for choosing a mask based on requirements
1. Find N: Class determins # of 1s to begin: 8, 16, or 24
2. Choose S: Need additional 1s in mask to create enough subnets
- 2^S greater or equal to x? 
3. Choose H: Ensure enough 0s in mask to create enough hosts
- 2^h - 2 greater or equal to y?
4. /P = N + S = 24

- Example 1: requirements, Need exactly 1 mask, Class B Network 172.16.0.0
1. Prepare for 200 Subnets and 150 Hosts per subnet
| Mask   | N   | S | H | 2^S | 2^H - 2 |
| /24    | 16  | 8 | 8 | 256 | 254 | 

2. Prepare for 100 Subnets and 50 Hosts per subnet
| Mask   | N   | S   | H | 2^S   | 2^H - 2 |
| /23    | 16  | 7   | 9 | 128   | 510 | 
| /24    | 16  | 8   | 8 | 256   | 254 | 
| /25    | 16  | 9   | 7 | 512   | 126 | 
| /26    | 16  | 10  | 6 | 1024  | 62  | 
- 3 spare bits between subnet and host, could be mix between them.
3. Lead to no masks, 500 subnets and 300 hosts per subnet
4. 9 subnet and 9 host bits, not enough host bits with only 7 left.



ended on lession 22 videio 22.2

# Choosing mask based on requirements for one mask for all subnets
1. Determin Class A, B or C network to be subnetted
2. Required number of subnets
3. Required number of hosts/subnets

1. Find N: Exact number of network bits
2. Calculate S min: minimunm number of subnet bits
3. Calculate H min: minimum number of host bits
4. Based on total = N + S min + H min
   1. Total > 32:  No mask meets the need!
   2. Total = 32: One mask meets the need! 
      - P = N + S min
   3. Total < 32: Multiple masks meet the need
      - Maximize # hosts/subnets: P = N + S min
      - Maximize # subnets: P = 32 - H min
| Power  | Decimal   |

| 2^2    | 4 |
| 2^3    | 8 |
| 2^4    | 16  |
| 2^5    | 32  |
| 2^6    | 64  |
| 2^7    | 128 |
| 2^8    | 256 |
| 2^9    | 512 |
| 2^10    | 1000 |

- Example 1 
   - Network: 172.32.0.0 , # subnets required = 300 , # hosts required = 100
   1. N = 16 (class B)
   2. S min = 9 
   3. H min = 7
- Example 2
   - Network: 192.168.1.0 , # subnets required = 8 , # number of hosts required 2
   1. N = 24 (class C)
   2. S min = 3 
   3. H min = 2 
   4. Total = 24 + 3 + 2 = 29
      - Shortest mask: P = N + S min = /27
      - Longest mask: P = 32 - H min = /30
      - Allowed masks: /27 - /30 
- Example 3
   - Network: 192.168.2.0 , # subnets required = 8 , # number of hosts required 18 
   1. N = 24 (class C)
   2. S min = 3 
   3. H min = 5 
   4. Total = 24 + 3 + 5 = 32
      - Shortest mask: P = N + S min = /27
      - Longest mask: P = 32 - H min = /27
      - Allowed masks: /27 to /27
- Example 4
   - Network: 192.168.3.0 , # subnets required = 16 , # number of hosts required 16 
   1. N = 24 (class C)
   2. S min = 4
   3. H min = 5
   4. Total = 24 + 4 + 5 = 33 
      - Allowed masks: no masks as 33 is bigger than 32 
- Example 5
   - Network: 172.21.0.0 , # subnets required = 123 , # number of hosts required 98 
   1. N = 16 (class B)
   2. S min = 7
   3. H min = 7
   4. Total = 16 + 7 + 7 = 30 
      - Shortest mask: P = N + S min = /23
      - Longest mask: P = 32 - H min = /25
      - Allowed masks: /23 to /25
- Example 6
   - Network: 172.22.0.0 , # subnets required = 100 , # number of hosts required 300 
   1. N = 16 (class B)
   2. S min = 7
   3. H min = 9
   4. Total = 16 + 7 + 9 = 32 
      - Shortest mask: P = N + S min = /23
      - Longest mask: P = 32 - H min = /23
      - Allowed masks: /23 
- Example 7
   - Network: 192.168.23.0 , # subnets required = 75 , # number of hosts required 2 
   1. N = 24 (class C)
   2. S min = 7 
   3. H min = 2 
   4. Total = 24 + 7 + 2 = 33 which is illeglal mask

- Example 8
   - Network: 172.24.0.0 , # subnets required = 1000 , # number of hosts required 2 
   1. N = 16 (class b)
   2. S min = 10 
   3. H min = 2 
   4. Total = 16 + 10 + 2 = 27
      - Shortest mask: P = N + S min = /26
      - Longest mask: P = 32 - H min = /30
      - Allowed masks: /26 to /30  
- Example 9 
   - Network: 192.168.25.0 , # subnets required = 25 , # number of hosts required5  
   1. N = 24 (class C)
   2. S min = 5 
   3. H min = 3 
   4. Total = 24 + 5 + 3 = 32 
      - Shortest mask: P = N + S min = /29
      - Longest mask: P = 32 - H min = /29
      - Allowed masks: /29 











