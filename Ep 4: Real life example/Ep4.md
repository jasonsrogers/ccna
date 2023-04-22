# OSI TCP/IP

How packet goes through a network and interacts with the layers;

 In Cicso packet tracer, adjust filters to only have http/https traffic so that we only see events linked to navigating to NetworkChuck.coffee

 In simulation we see that it prepqares 2 packets/messages, 

 one that he is getting ready and one for the switch

 message has 7 layers (event if it's tcp/ip)

 Layer 7: the http client sends a http request to the server (application layer)
Layer 6: blank (merged with application)
layer 5: blank (merged with application)
Layer 4: TCP (transport layer) (how we can transfer the data), other option would be UDP (user datagram protocol). TCP is more reliable, UDP is faster
We also have a port number, 80 is the default port for http 443 for https
Layer 3: IP (network layer) (how we can find the destination) source and destination IP address
Layer 2: MAC address (data link layer) (how we can find the destination) source and destination MAC address


Data + Layer 4 header = (segment) 

Data + layer 4 header + layer 3 header = (packet)

Data + layer 4 header + layer 3 header + layer 2 header = (frame)

Data + layer 4 header + layer 3 header + layer 2 header + layer 1 header = (bit)

As we move through the layers, we encapsulate the data, we add a header to the data etc

if we inspect the message as it goes through the switch, we can only see layer 2. all the information has beer encapsulated in the frame

the switch will look at the destination MAC address and forward the frame to the correct port

when it hits the router, the router will look at the destination IP address and forward the packet to the correct port

in the router we can see the packet, aka layer 3,2,1 information

the router will decapsulate the packet to see where it's supposed to go. it will encapsulate the packet again with the new destination MAC address and send it to the switch

the server is built with following the tcp/ip model, so it will decapsulate the frame in layer 2 (data link) to see that it's supposed to come to him, then the decapsulate the packet in layer 3 (network) to see that it's supposed to come to him, then decapsulate the segment in layer 4 (transport) to see that it's supposed to come to him, then decapsulate the data in layer 7 (application) and see what to do with it

Questions:

Which of the following functions are performed by the application layer of the OSI model?


 - determining wether adequate resources exist for communication
 

 - managing communication between applications 

- directing data to the correct program

Converting data to the correct data format is presentation layer (layer 6) only relevant to OSI, in tci/ip it's merged with application layer

which of the following relies on a three way handshake in order to provide connection oriented reliable data transfer between networked computers

TCP 


ARP: map a MAC address to an IP address (IP to MAC)
DNS: map a domain name to an IP address
RARP: map an IP address to a MAC address (MAC to IP)
UDP: unreliable data transfer but faster