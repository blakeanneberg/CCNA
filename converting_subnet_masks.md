# 32-Bit binary number
- Only computers use
- Example 1: /24 subnet mask: 11111111 11111111 11111111 00000000
- Example 2; /20 subnet mask: 11111111 11111111 11110000 00000000
- Binary 1s on the left and continious
- Binary 0s on the right and continious 

# Dotted decimal number DDN
- Looks like a IP
- Conversion of binary to DDN 
- Binary Mask | 11111111 | 11111111 | 11110000 | 00000000 |
- DDN Mask | 255 | 255 | 240 | 0 |
- Values found in DDN Mask Octet (Decimal, Binary)
   | Decimal Value | Binary | Number of Binary 1s | /Prefix |
   | ----------| --------|--------|-------|
   | 0 | 00000000 | 0 | / | 
   | 128 | 10000000 | 1 | / | 
   | 192 | 11000000 | 2 | / |
   | 224 | 11100000 | 3 | / |
   | 240 | 11110000 | 4 | / |
   | 248 | 11111000 | 5 | / |
   | 252 | 11111100 | 6 | / |
   | 254 | 11111110 | 7 | / | 
   | 255 | 11111111 | 8 | / | 

# Prefix Length /P
- P is the number of binary 1s in the mask, also called CIDR Mask

# DDN to Prefix
1. Set up problem on paper
- write the DDN mask with wide columns
- Leaver three rows of space for: Binary Mask, Addition, Prefix Mask
2. For each octet, convert decimal value to 8 bit binary
- Use memory or notes
3. Count the Number of Binary 1s in the mask
- Count the binary 1s in each octet: write the values
- Add the per-octet counts
4. Write the prefix mask as a / followed by the total from step 3

# Prefix to DDN
1. Set up problem on paper
- Write the prefix mask /P on the top
- Create four columns (one per octet), each wide enough for 8 bits
- Leave space for two rows: Binary Mask, DDN Mask
2. Create the binary mask
- Write P Binary 1s, starting on the left working to the right
- write only 8 bits per octet 
- complete the 32bit binary mask with 0s
3. create the DDN mask 
- Use memory or notes of nine mask octet values

# Identifies number of bits that
## Identify subnet number (Prefix Bits)
## Identify a host in the subnet (Host Bits) 

# Useful for calculating facts about subnets

# Subnet Mask formats

## Terms that mean the same thing 
- Subnet mask, network mask, mask
- Address mask, bit mask, net mask 
- Mask, CIDR mask, slash masks
- Prefix mask, prefix length, prefix notation 
