# Finding IP Networking Basics
1. Determine the class
   - Class A: 1st octet 1 - 126
   - Class B: 1st octet 128 - 191
   - Class C: 1st octet 192 - 223
   - Class D: 1st octet 224 - 239
   - Class E: 1st octet 240 - 255
2. Record the number of network and host octets (classes A, B, C) 
   - Class A: 1 Network, 3 Host, /8
   - Class B: 2 Network, 2 Host, /16
   - Class C: 3 Network, 1 Host, /32
3. Record Default Mask
   - Class A: 255.0.0.0
   - Class B: 255.255.0.0
   - Class C: 255.255.255.0

- Examples
1. 10.1.2.3 , class A, 1 net, 3 hosts 255.0.0.0
2. 172.20.1.1. , class B 2 net 2 hosts, 255.255.0.0 
3. 200.3.4.5 , class C 3 network 1 host, 255.255.255.0
4. 227.3.4.5 , class D
5. 241.5.4.3 , class E 

# Calculating classful network facts
1. Set up problem on paper
2. For each column, if mask = 255
- Copy address octets to Network ID
- Copy address octets to Network Broadcast Address
3. For each column, if mask = 0
- Write 0s in the Network ID
- Write 255s in the Network Broadcast Addres
4. To find the range of addresses: 
- In the 4th Octet, Network ID: +1
- In the 4th Octet, Broadcast -1


## Examples
1. 10.1.2.3, 255.0.0.0
   - NetworkID: 10.0.0.0
   - 1st addr: 10.0.0.1
   - 2nd addr: 10.255.255.254
   - Network boradcast address:10.255.255.255
2. 172.20.1.1, 255.255.0.0
   - NetworkID: 172.20.0.0
   - 1st addr: 172.20.0.1
   - 2nd addr: 172.20.255.254
   - Network boradcast address: 172.20.255.255
3. 200.3.4.5, 255.255.255.0 
   - NetworkID: 200.3.4.0
   - 1st addr: 200.3.4.1
   - 2nd addr: 200.3.4.254
   - Network boradcast address: 200.3.4.255
4. 172.21.1.1 , 255.255.0.0
   - NetworkID: 172.21.0.0
   - 1st addr: 172.21.0.1
   - 2nd addr: 172.21.255.254
   - Network boradcast address: 172.21.255.255
5. 200.3.4.5, 255.255.255.0
   - NetworkID: 200.3.4.0
   - 1st addr: 200.3.4.1
   - 2nd addr: 200.3.4.254
   - Network boradcast address: 200.3.4.255
6. 9.99.199.9 , 255.0.0.0
   - NetworkID: 9.0.0.0
   - 1st addr:  9.0.0.1
   - 2nd addr: 9.255.255.254
   - Network boradcast address: 9.255.255.255
7. 10.155.18.97 , 255.0.0.0
   - NetID: 10.0.0.0
   - 1st addr: 10.0.0.1
   - 2nd addr: 10.255.255.254
   - Net broadcast 10.255.255.255
8. 172.21.134.243 , 255.255.0.0
   - Net ID: 172.21.0.0
   - 1st addr: 172.21.0.1
   - 2nd addr: 172.21.255.254
   - Net broadcast: 172.21.255.255
9. 192.168.56.87 , 255.255.255.0
   - Net ID: 192.168.56.0
   - 1st addr: 192.168.56.1
   - 2nd addr: 192.168.56.254
   - Net broadcast: 192.168.56.255
10. 192.168.219.176 , 255.255.255.0
   - Net ID: 192.168.219.0
   - 1st: 192.168.219.1
   - Last: 192.168.219.254
   - Net broadcast: 192.168.219.255
11. 172.22.18.35 , 255.255.0.0
   - Net ID: 172.22.0.0
   - 1st: 172.22.0.1
   - 2nd: 172.22.255.254
   - Net broadcast: 172.22.255.255
12. 55.66.77.88, 255.0.0.0 
   - Net ID: 55.0.0.0
   - 1st: 55.0.0.1
   - 2nd: 55.255.255.254
   - Net broadcast: 55.255.255.255
12. 172.24.1.223 , 255.255.0.0
   - Net ID: 172.24.0.0
   - 1st: 172.24.0.1
   - 2nd: 172.24.255.254
   - Net broadcast: 172.24.255.255
13. 172.26.223.42 , 255.255.0.0
   - Net ID: 172.26.0.0
   - 1st: 172.26.0.1
   - 2nd: 172.26.255.254
   - Net broadcast: 172.26.255.255
14. 182.168.119.95 , 255.255.0.0
   - Net ID: 182.168.0.0
   - 1st: 182.168.0.1
   - 2nd: 182.168.255.254
   - Net broadcast: 182.168.255.255
15. 192.168.200.1, 255.255.255.0
   - Net ID: 192.168.200.0
   - 1st: 192.168.200.1
   - 2nd: 192.168.200.254
   - Net broadcast: 192.168.200.255










