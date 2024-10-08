# Info needed
- Site: like router R1
- Subnet ID: 10.1.1.0
- First Address: 10.1.1.1
- Last Address: 10.1.1.254
- Subnet Broadcast address: 10.1.1.225

-Example Three Easy Masks
| Binary | Prefix | DDN |
| 11111111 00000000 00000000 00000000 | /8 | 255.0.0.0 |
| 11111111 11111111 00000000 00000000 | /16 | 255.255.0.0 |
| 11111111 11111111 11111111 00000000 | /24 | 255.255.255.0 |

# Process: Calculating Subnets 
1. Write problem on paper: Mask above, Address below, column aligned. Leave space for Subnet ID, Subnet boradcast address, two more values
2. For each column, if Mask = 255 in first three octects
- Copy Address octets to Subnet ID
- Copy addresses octets to Subnet broadcast address
3. For each column, if Mask = 0
- Write 0s in the subnet ID
- Write 255s in subnet Broadcast Address
4. If Mask is neither 0 nor 255:
- Calculate Magic number = 256 - Mask_Value
- Subnet ID: Use nearest magic MULTIPLE (not greater than) to match the addresses value 
- Broadcast: use next magic multiple, minus 1
5. To find the range of addressess
- In 4th octet, Subnet ID and add 1
- In 4th Octet, Broadcast and subtract 1

- Template: 
1. __.__.__.__ MASK
2. __.__.__.__ Subnet ID
3. __.__.__.__ First Address
4. __.__.__.__ Last Address
5. __.__.__.__ Broadcast 

- Template: 
|---|---|---|---|---|
| . | . | . |  | Mask |
| . | . | . |  | Address |
| . | . | . |  | first Address |
| . | . | . |  | Last Address |
| . | . | . |  | Subnet ID |
| . | . | . |  | Broadcast |

- Example: 
|---|---|---|---|---|
| 255. | 255. | 255. | 0 | Mask |
| 172. | 16. | 55. | 56 | Address |
| 172. | 16. | 55. | 0 | Subnet ID |
| 172. | 16. | 55. | 1 | First Address |
| 172. | 16. | 55. | 254 | Last Address |
| 172. | 16. | 55. | 255 | Broadcast |

- Example 10.200.100.200, 255.255.0.0
|---|---|---|---|---|
| 255. | 255. | 0. | 0 | Mask |
| 10. | 200. | 100. | 200 | Address |
| 10. | 200. | 0. | 1 | first Address |
| 10. | 200. | 255. | 254 | Last Address |
| 10. | 200. | 0. | 0 | Subnet ID |
| 10. | 200. | 255. | 255 | Broadcast |


- Example: 172.24.15.15, 255.255.255.0 : 
|---|---|---|---|---|
| 255. | 255. | 255. | 0 | Mask |
| 172. | 24. | 15. | 15 | Address |
| 172. | 24. | 15. | 0 | Subnet ID |
| 172. | 24. | 15. | 1 | first Address |
| 172. | 24. | 15. | 254 | Last Address |
| 172. | 24. | 15. | 255 | Broadcast |

- Example: 
Add: 128.1.101.200
Mask: 255.255.255.0
Subnet ID: 128.1.101.0 
First Usable: 128.1.101.1 
Last Usable: 128.1.101.254 
Subnet Broadcast Address: 128.1.101.255

- Example: 
Add: 9.19.29.39 
Mask: 255.255.255.0
Subnet ID: 9.19.29.0 
First Usable: 9.19.29.1 
Last Usable: 9.19.29.254 
Subnet Broadcast Address: 9.19.29.255

- Example: 
Add: 10.101.151.1 
Mask: 255.255.255.0 
Subnet ID: 10.101.151.0
First Usable: 10.101.151.1
Last Usable: 10.101.151.254
Subnet Broadcast Address: 10.101.151.255

- Example: 
Add: 11.21.31.41 
Mask: 255.255.0.0 
Subnet ID: 11.21.0.0 
First Usable: 11.21.0.1
Last Usable: 11.21.255.254 
Subnet Broadcast Address: 11.21.255.255

## Finding subnet facts difficult masks
- Example: 
Add: 10.1.7.3 
Mask: 255.255.254.0 
Subnet ID: 10.1.6.0 
First Usable:10.1.6.1 
Last Usable:10.1.7.254 
Subnet Broadcast Address: 10.1.7.255

- Example: 
Add: 172.16.55.56 
Mask: 255.255.240.0 
Subnet ID: 172.16.48.0
First Usable: 172.16.48.1
Last Usable: 172.16.255.254
Subnet Broadcast Address: 172.16.63.255

- Example
ADD: 10.200.100.100
MASK: 255.255.255.192
SubnetID: 10.200.100.64
First: 10.200.100.65
Last: 10.200.100.126
Broadcast ADD:  10.200.100.127

- Example
ADD: 10.200.100.200 
MASK: 255.252.0.0  
SubnetID: 10.200.0.0
First: 10.200.0.1
Last: 10.203.255.254
Broadcast ADD: 10.203.255.255

- Example
MASK: 255.254.0.0
ADD: 10.1.7.3
SubnetID: 10.0.0.0 
First: 10.0.0.1 
Last: 10.1.255.254 
Broadcast ADD: 10.1.255.255 

- Example
MASK: 255.248.0.0 
ADD: 10.104.15.19 
SubnetID: 10.104.0.0 
First: 10.104.0.1 
Last: 10.111.255.254 
Broadcast ADD: 10.111.255.255 

- Example 16
MASK: 255.240.0.0 
ADD: 10.157.18.1 
SubnetID: 10.160.0.0 
First: 10.144.0.1 
Last:10.159.255.254
Broadcast ADD: 10.159.255.255

- Example: 32 663 
MASK: 255.224.0.0
ADD: 10.39.224.119
SubnetID: 10.32.0.0
First: 10.32.0.1 
Last: 10.64.255.254
Broadcast ADD: 10.64.255.255 


- Example: 32
MASK: 255.255.224.0
ADD:  172.25.177.143
SubnetID: 172.25.160.0
First: 172.25.160.1
Last: 172.25.191.254
Broadcast ADD: 172.25.191.255

- Example: 16 
MASK: 255.255.240.0
ADD: 172.19.32.1
SubnetID: 172.19.32.0
First: 172.19.32.1
Last:  172.19.32.254
Broadcast ADD: 172.19.32.255

- Example: 8
MASK: 255.255.248.0
ADD: 172.21.95.114
SubnetID: 172.21.88.0
First: 172.21.88.1
Last:  172.21.95.224
Broadcast ADD: 172.21.95.255

- Example: 
MASK:  255.255.192.0
ADD: 172.28.234.210
SubnetID: 172.28.192.0
First: 172.28.192.1 
Last: 172.28.256.254
Broadcast ADD: 172.28.256.255


- Example: 
MASK: 255.255.255.128
ADD: 192.168.45.201
SubnetID: 192.168.45.128
First: 129.168.45.129
Last:  129.168.45.254
Broadcast ADD: 192.168.45.255

- Example: 
MASK: 255.255.255.224
ADD: 192.168.114.18
SubnetID: 192.168.114.0
First: 192.168.114.1
Last: 192.168.114.30
Broadcast ADD: 192.168.114.31

- Example: 
MASK: 255.255.255.248
ADD: 192.168.201.45
SubnetID: 192.168.201.40
First: 192.168.201.41
Last: 192.168.201.46
Broadcast ADD: 192.168.201.47

- Example: 
MASK:  255.255.255.252
ADD: 192.168.14.17
SubnetID: 192.168.14.16
First: 192.168.14.17
Last: 192.168.14.19
Broadcast ADD: 192.168.14.20










