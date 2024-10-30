#TCPIP

## Networking architecture or network blueprint of TCPIP 
- Define protocol via Requests for Comments RFC defines set of functions and specifics about implementation


### Application (data)
- Protocols
1. HTTPS, POP3, SMTP
- Create and encapsulate the application data with any required application layer headers

### Transport (TCP, data = segment)
- Protocols
1. TCP, UDP 
- adjacent-layer interaction how adjacent layers in networking model on same computer work together. 
- Same-layer interaction when a particular layer on one computer wants to communicate with the same layer on another computer, the two computers use headers to hold the information that they want to communicate. 
- Encapsulate the data supplied by the application layer inside a transport layer header

### Network/Internet protocol IP (IP, TCP, Data = Packet)
- Delivering data over the entire path from the original sending computer to final destination computer (National Postal services to addresses)
- Protocols
1. IP, ICMP 
- Addressing and routing: packets of data 
- Encapsulate the data supplied by the transport layer inside a newtwrk layer IP header

### Data Link (Data Link header, IP, TCP, Data link trailer = Frame) 
- Control use of physical  link (standards for roads, cars and traffic signals)
- Protocols
1. Ethernet, 802.11 (wifi) 
- Encapsulate the data supplied by the network layer inside a data link layer header and trailer

### Physical
- How to transmit bits over each link
- Transpmit the bits.

## Ethernet LANS


