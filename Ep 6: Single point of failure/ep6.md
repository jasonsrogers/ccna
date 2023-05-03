# Avoid single point of failure

Router

Switch (1)
    WAP
    Computer
    phone 
    // as the number of devices increase, we need more ports
    switch (connected to first one) (2  )
        Computer
        phone 
        NAS
        // as the number of devices increase, we need more ports
        switch (connected to first one) (3)
            Computer
            phone 
            NAS
             // as the number of devices increase, we need more ports
            switch (connected to first one) (4)
                Computer
                phone 
                NAS

This all works fine, but what happens if any switch or cables fail? All the devices connected to it will lose connection to the network.

if cable between (2) and (3) fails, all devices connected to (3) and (4) will lose connection to the network

this is a SPOF (Single Point Of Failure)

## How to avoid SPOF

make sure that there are no SPOF, doh!

### don't chain switches

Don't do: 

Router - switch (1) - switch (2) - switch (3)

Do:

Switch (1) - Router - switch (2)
                |
                switch (3)

Better but can be improved

this is good to get your computers talking to the internet but not to each other or other network devices

Instead of connecting the switches to the router, connect them to a multi-layer switch (L3 switch)

it's a switch that can deal with ip addresses as well as mac addresses

Router - multi-layer switch - switch (1) (2) (3) (4)

this is a two tier architecture

tier 1: switch (1) (2) (3) (4): access layer, giving access to devices
tier 2: multi-layer switch: distribution layer, distributing the network

because of the multi-layer switch, handles all the traffic, it's beefier, it's more expensive, more component etc 

distribution layer also referred to as aggregation layer provides filtering, inter-vlan routing, security, policy-based connectivity, and access to the rest of the network

distribution layer is between the access layer and the core layer

Better but can be improved

### removing spof from the 2 tier architecture

2 multi-layer switches
2 links between them
each connected to router
each connected to every switch
+
extra router for redundancy connected to both multi-layer switches

perfect but expensive lol 

## 3 tier architecture

when we start to scale up and add more locations/sites, we end up with multiple 2 ties architectures

which we could connect all multi-layer switches together redundantly, but that would be a mess

### Tier 3: Core layer

a multi-layer (ideally 2) switches sit above the distribution layer

the core layer typically provides the fastest switching path in the network, as the network backbone, the core layer is primarily associated with low latency and high reliability

in the 2 tier architecture, the core layer is in the distribution layer. it is referred to as collapsed core layer

Only 1 building/site has the core layer. the other buildings/sites have 2 tier architecture and their distribution layer is connected to the core layer






