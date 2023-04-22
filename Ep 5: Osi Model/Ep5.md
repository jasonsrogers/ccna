# Osi model

What happens in layer 5 6 and 7 in the OSI model?

In Tcp/ip model Data (Layer 7) gets encapsulated in a segment (Layer 4) which gets encapsulated in a packet (Layer 3) which gets encapsulated in a frame (Layer 2) which gets encapsulated in a bit (Layer 1)

L2 trailer Data L4 Header L3 Header L2 Header

## what happens when you watch a youtube video?

L7 layer is the interface/portal for applications to communication over a network

Data (Layer 7): I want to want a youtube video

Layer 6 will make the data look nice, it will convert the data to the correct format and encrypt it
- data format = file types (jpg, mp4, pdf, xml, etc)
- encryption = can encrypt to avoid people seeing ssl, tls, etc

Layer 5 will manage the session between the client and the server (authentication, authorization, etc), l2tp, rtcp(calls), h245(video calls), socks(proxies) etc

Layer 4 how to I get the data to the server, we can use TCP(reliably) or UDP (real time, less reliable, faster)
- tcp: reliable, makes sure that everything is received, if not it will resend it before it continues. Tcp 3 way handshake (syn, syn/ack, ack) before it starts sending data. tcp stands for transmission control protocol.
- udp: less reliable, faster, real time. udp stands for user datagram protocol. it doesn't care if it's received or not, it just sends it and moves on. it doesn't have a 3 way handshake.

When using watchin youtube video, we use both tcp and udp

Wireshark is a tool that we can use to inspect the packets that are being sent and received. 173.194.191.167 is the ip address of youtube

Starts by sending a 3 way handshake (syn, syn/ack, ack) to the server to make sure that the server is ready to receive data, it stays with tcp while loading the page, buttons, tiles etc.
Then suddenly it switches to udp so that it can stream the video.
While streaming, it doesn't make sense to resend what has been missed. It's better to just keep streaming and move on. So it switches to udp.

Ports: 443 and 57095

if we didn't have ports, and we wanted to get from a server: 
- http(s)
- ftp 21
- ssh 22 
- rdp 3389
...

How would we know which one to use? We would use ports

Well known ports: 0-1023
Registered ports: 1024-49151
Dynamic ports: 49152-65535

from 57095 to 443 is the source port and destination port

this tells youtube that we want it to send back data on port 57095

57095 is an ephemeral port, it's a dynamic port

Quiz:
DNS Domain Name System: 53
DHCP Dynamic Host Configuration Protocol: 67/68
FTP File Transfer Protocol: 21
HTTP Hypertext Transfer Protocol: 80
SMTP Simple Mail Transfer Protocol: 25
SNMP Simple Network Management Protocol: 161
tftp Trivial File Transfer Protocol: 69 

~TCP~
HTTP
SMTP
FTP

~UDP~
TFTP
DHCP
SNMP


~TCP and UDP~
DNS

 which of the following ports is used by tftp?
UDP:69
