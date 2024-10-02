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

# Choosing mask based on requirements
