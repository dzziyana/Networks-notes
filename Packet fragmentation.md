Since different paths have different MTU sizes, a packet might have to be fragmented into multiple subparts to adhere to the limits. This is mostly done by the router. IPv4 does implement fragmentation, **whereas IPv6 only will send an ”Packet Too Big” error-message if the MTU is exceeded.** 
To make fragmentation possible, headers with different fields are used. Only at the final destination host the fragmented packets are reassembled.

# Identification Field
This field uniquely identifies each datagram. If one packet gets fragmented, all the subpart will share the same identification field.
# Offset Field 
This field indicates the position of the current fragment within the original datagram.
# Control Bits
These bits include flags such as the ”More Fragments” (MF) flag and the ”Don’t Fragment” (DF) flag. The MF flag indicates whether more fragments of the original datagram are to follow,

while the (DF) flag instructs routers not to fragment the datagram if it exceeds the MTU of the outgoing interface.


> [!NOTE] 
> Related to / simplification of the page [[Packet size solutions]]
