# Router

Router allows to connect multiple networks together

Networks are defined by their IP address and subnet mask

network A 10.1.1.0 -> 10.1.1.255
network B 23.227.38.0 => 23.227.38.255

when we ping from computer A to computer B,

ARP (address resolution protocol) is a protocol that allows to resolve an IP address to a MAC address

This allows to resolve a MAC address to an IP address

A sends out a broadcast frame (level 2) to all devices on the network by asking for mac address FFFF.FFFF.FFFF
This signal is called a broadcast and tells all devices on the network to listen

the switch will then forward the frame to all devices on the network. devices that are not the destination will ignore the frame. the device that has this ip address will respond with its mac address

When we try to ping a machine on a different network, it will not query 23.227.38.65, instead it will query 10.1.1.1

Machine A is configured with a default gateway of 10.1.1.1
So it's not trying to find 23.227.38.65, it's asking the default gateway to find it

Gateway is Router

network A 10.1.1.0 -> 10.1.1.255 is his network, but if tries to reach something not in his network for to the default gateway

Routers are layer 3 devices they can handle ip addresses

the router knows where  23.227.38.xxx is. it will then broadcast a frame to all devices on the network asking if they have the ip address through the switch

machine b will respond with its mac address and the router will then send the frame to machine a

then a and b can communicate

A sends a message with the target ip address in layer 3 and the mac address in layer 2 of the router

switch will forward the frame to the router due to the mac address

router will forward the frame to machine b due to the ip address

first time it will broadcast to all devices on the network, then it will cache the mac address

Sneak peek when we enter a url, how does it find the ip address?

