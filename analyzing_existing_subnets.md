# Info needed
- Site: like router R1
- Subnet ID: 10.1.1.0
- First Address: 10.1.1.1
- Last Address: 10.1.1.254
- Subnet Broadcast address: 10.1.1.225

# Example Three Easy Masks
| Binary | Prefix | DDN |
| 11111111 00000000 00000000 00000000 | /8 | 255.0.0.0 |
| 11111111 11111111 00000000 00000000 | /16 | 255.255.0.0 |
| 11111111 11111111 11111111 00000000 | /24 | 255.255.255.0 |

Process: Calculating Subnet 
1. Write problem on paper: Mask above, Address below, column aligned. Leave space for Subnet ID, Subnet boradcast address, two more values
2. For each column, if Mask = 255
- Copy Address octets to Subnet ID
- Copy addresses octets to Subnet broadcast address
3. For each column, if Mask = 0
- Write 0s in the subnet ID
- Write 255s in subnet Broadcast Address
4. To find the range of addressess
- In 4th octet, Subnet ID: +1
 dd
- In 4th Octet, Broadcast: -1

example: 
1. __.__.__.__ MASK
2. __.__.__.__ Subnet ID
3. __.__.__.__ First Address
4. __.__.__.__ Last Address
5. __.__.__.__ Broadcast 



