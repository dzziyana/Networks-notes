### Summary of Lecture 8: Network Layer

#### **Introduction to Network Layer**
- **Purpose**: The network layer builds on the link layer and provides services to the transport layer. It enables routers to send packets across multiple networks.
- **Key Challenges**:
  - **Scale**: Hierarchical addressing (prefixes) to manage global networks.
  - **Heterogeneity**: IP facilitates communication between diverse networks.
  - **Bandwidth Control**: Efficient routing and Quality of Service (QoS).
  - **Economics**: Ensures cost-effective network traffic management.

#### **Network Service Models**
1. **Datagram Model (Connectionless)**:
   - Packets contain full destination addresses; each router forwards independently.
   - Example: IP (Internet Protocol).
2. **Virtual Circuit Model (Connection-Oriented)**:
   - Three phases: connection setup, data transfer, teardown.
   - Packets use short labels for routing; requires per-connection state in routers.
   - Example: MPLS (Multi-Protocol Label Switching).

#### **IPv4 (Internet Protocol Version 4)**
- **Header Fields**: Includes version, header length, TTL (Time to Live), protocol, checksum, and source/destination addresses.
- **Fragmentation**: Splits large packets to fit smaller MTUs (Maximum Transmission Units), but modern networks prefer Path MTU Discovery to avoid fragmentation.
- **Addressing**:
  - **IPv4 Addresses**: 32-bit, written in dotted-quad notation (e.g., 192.168.1.1).
  - **Prefixes**: Hierarchical blocks (e.g., 192.168.1.0/24). The first and last addresses in a prefix are reserved (network and broadcast addresses).

#### **Forwarding and Routing**
- **Forwarding**: Local process where routers use forwarding tables to send packets to the next hop based on the longest matching prefix.
- **Routing**: Global process to determine paths (covered in later lectures).
- **Longest Matching Prefix Rule**: Ensures packets are forwarded to the most specific route available.

#### **Helper Protocols**
- **ARP (Address Resolution Protocol)**: Maps IP addresses to MAC addresses on the same network.
- **DHCP (Dynamic Host Configuration Protocol)**: Assigns IP addresses and network parameters (e.g., default gateway, DNS server) dynamically.
- **ICMP (Internet Control Message Protocol)**: Reports errors (e.g., unreachable hosts) and supports tools like `ping` and `traceroute`.

#### **NAT (Network Address Translation)**
- **Purpose**: Allows private networks (using RFC 1918 addresses) to share a single public IP.
- **How It Works**: Translates internal IP:port pairs to external ones, enabling multiple devices to access the internet.
- **Downsides**: Breaks end-to-end connectivity, complicates running servers, and requires port forwarding for incoming traffic.

#### **IPv6 (Internet Protocol Version 6)**
- **Motivation**: Address exhaustion in IPv4; IPv6 uses 128-bit addresses (e.g., `2001:db8::1`).
- **Key Improvements**:
  - Simplified header (fixed size, no fragmentation, no checksum).
  - Built-in support for autoconfiguration (SLAAC) and security.
  - No need for NAT due to vast address space.
- **Transition Mechanisms**: Dual-stack (IPv4 and IPv6 coexistence), tunneling, and translation.

#### **Key Takeaways**
- The network layer ensures scalable, efficient, and heterogeneous communication across networks.
- IPv4 relies on helper protocols (ARP, DHCP) and workarounds (NAT), while IPv6 offers a more streamlined solution.
- Forwarding uses longest prefix matching, while routing determines paths (covered separately).

This lecture sets the foundation for understanding how data is routed and forwarded in modern networks, with IPv6 poised to address the limitations of IPv4.