A socket is a **software abstraction** by which an application process exchanges network
messages with the *(transport layer in the)* operating system. 
Sockets enable applications to establish communication sessions, send and receive data, and manage network connections.

- TCP socket (SOCK_DGRAM) →  Connection-oriented, reliable 
	- TCP sockets operate using the Virtual Circuit Model, which provides a reliable, connection-oriented communication channel between two endpoints. They establish a virtual circuit through a handshake process before data exchange begins, ensuring reliable and ordered delivery of data. The sockets are used in applications requiring guaranteed delivery, in-order delivery of data, and congestion control. Examples include web browsing (HTTP), file transfer (FTP), and email (SMTP).

- UDP socket (SOCK_STREAM) → Connectionless, unreliable, faster.
	- UDP sockets operate using the Datagram Model, as discussed in the Network Layer. This model is connectionless, meaning each datagram is independently routed and delivered to its destination without establishing a persistent connection. They provide a lightweight, low-latency communication method suitable for applications where occasional packet loss is acceptable, such as real-time audio/video streaming and DNS (Domain Name System) queries.

> [!question] Problem
> Which app (socket) gets which packets

> [!check] Solution
> Port as transport layer identifier (16 bits)

## Ports: Identifying Applications on a Host
> Ports are numerical identifiers (16-bit unsigned integers) associated with each socket on a host. They help in multiplexing multiple network connections on a single host, distinguishing between different applications or services running concurrently.

- Multiple applications can run on the same IP address using different **port numbers**.
- **Transport layer headers** contain **source and destination port numbers** to identify which socket the packet belongs to.
- Well-known ports (0-1023) are reserved for common services (e.g., HTTP - 80, HTTPS - 443).
- Clients are assigned **ephemeral ports** (1024-65535) dynamically.
#### **4. Multiplexing & Demultiplexing**
- **Multiplexing**: The transport layer **encapsulates** data with IP and port information before sending it.
- **Demultiplexing**: The OS extracts **destination port number** from received packets and delivers them to the correct socket.
# Connection Mappings
OS stores mapping between sockets and ports
> [!tip] Storage method
> Port: in packets
> Socket: in OS
### For UDP (SOCK_DGRAM)
OS stores...
``(local port, local IP address) ⟷ socket``
### For TCP (SOCK_STREAM)
OS stores...
``(local port, local IP address, remote port, remote IP) ⟷ socket``
### Reason:
![[Pasted image 20250326134633.png]]
... whereas ==in UDP there is a connection ID== (app layer multiplexing needed)

![[Pasted image 20250804135223.png]]