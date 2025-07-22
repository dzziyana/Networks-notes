# Address Resolution Protocol
is used to map a local IP address to the link layer addresses

>[!Question] Problem
> A node needs Link layer addresses to send a frame over the local link...
> How does it get the destination link address from a destination IP address?

![[Pasted image 20250327181635.png]]

ARP resolves destination hardware addresses by a two-step procedure.

1. REQUEST : After checking that the wanted MAC address is not present in the ARP cache, the sender broadcasts an ARP request onto the local network segment $\rightarrow$ ***flooding***

2. REPLY : Upon receiving the ARP request, the target device (the host with the specified IP address) responds with an ARP reply.

If a device wants to send something on another network, ARP won’t work. The packet gets encapsulated by the IP Address and is sent to the default gateway. Via the network layer the packet gets sent to the local router of the wanted device. Here ARP can be used by the local router to determine the MAC address if necessary.