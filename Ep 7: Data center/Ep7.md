# Data center networks

We used to design data centers like we designed home/office networks, but their purpose is different so the design should be different.

## What is a Data Center?

A data center is a building or a group of buildings that contains servers and other equipment that is used to process, store, and distribute large amounts of data. Data centers are the backbone of the internet and are used by companies to store and process data.

Any website, app, or service that you use is hosted on a server in a data center. Data centers are also used by companies to store and process data that is not publicly available.

You can setup your own data center at on premise if you are a small/medium company, but if you are a big company you will need to rent a space in a data center or cloud provider.

As a network engineer, you'll usually work with on prem or renting "racks" in a data center. More that often however it will be a hybrid of all three.

## Data Center Design

Rent a bunch of racks

each rack has a bunch of servers

- one or more switches (redundancy) also referred to as ToR (Top of Rack) switches

the servers are connected to the switches

our TOR switches (access layer switches) are connected to our distribution layer switches

our distribution layer switches are connected to our core layer switches

core layer
distribution layer
access layer

However there is a problem with this design.

Here we only car about traffic to/from the internet (North bound/South bound traffic). We don't care about traffic between servers (East bound/West bound traffic).

But in a data center we care about both.

## East/West Traffic

With virtialization we can have multiple machine trying to talk to each other. Nowadays 80% of the traffic in datacenters is East/West traffic.

With the three layer design we have a problem. If we have a server in rack 1 trying to talk to a server in rack 2, the traffic will have to go through the core layer switches. This is not efficient.

## New Design

racks have switches called leaf switches

They are still the access layer switches, but they talk to spine switches instead of distribution layer switches. They are the backbone of the data center that support the bandwidth between racks.

Each leaf switch is connected to each spine switch. This is called a full mesh topology.

spine/leaf design (clos)

It's a cabling nightmare but it's the most efficient design.

Now when a server 1 wants to talk to a server 2, it will connect to any spine switch and then to the sever 2 (2 hopes)

No matter where the servers are located, they will always be 2 hopes away from each other.

With the three layer design, it was at least 3 hopes or more, it wasn't predictable.

Cisco Nexus 9000 series switches are designed for this design.

## L3

Connection between leaf and spine switches is actually a layer 3 (ip address) rather than layer 2 (mac address). Typically switches use layer 2 to communicate with each other.

This means that they are multi layer switches

this Avoids spanning tree (loop prevention), since we are using layer 3 we don't have to worry about loops as we can load balance traffic between connections.

This is the underlay of the data center.

Then there is the overlay which is the virtualization part.

## Questions

which of the following devices cannot be connected to leaf nodes in the cisco ACI architecture?
[] APICs
[] application servers
[] EPGs
[] spine switches
[x] leaf nodes <== leaf doesn't connect to leaf directly

ACI => network automation solution from Cisco
depends on the spine'/leaf design underlay

which of the following statments are true regarding physical connections in the cisco aci architecture? (2 options)

[] Spine nodes must be fully meshed
[x] ecach spine node must connect to every leaf node
[] an APIC must connect to at least one spine node
[] leaf nodes must be fully meshed
[x] each leaf node must connect to every spine node