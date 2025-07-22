[![udp Memes · ProgrammerHumor.io](https://i.programmerhumor.io/2025/06/5eec3a8f7b4e9f5c957670d08c1d907aeebdffd5368a159b1a5563b7c41a4852.jpeg)
UDP is a [[Transport Layer]] protocol. It is often used for applications where low latency and quick data transmission are more critical than guaranteed delivery and error recovery.

Within an IP network, UDP does not require prior communication to set up communication channels or data paths.

UDP is a connectionless protocol, meaning that messages are sent without negotiating a connection and that UDP does not keep track of what it has sent. UDP provides checksums for data integrity, and port numbers for addressing different functions at the source and destination of the datagram. It has no handshaking dialogues and thus exposes the user's program to any unreliability of the underlying network; ==there is no guarantee of delivery, ordering, or duplicate protection.== If error-correction facilities are needed at the network interface level, an application may instead use Transmission Control Protocol (TCP) or Stream Control Transmission Protocol (SCTP) which are designed for this purpose.

UDP is suitable for purposes where error checking and correction are either not necessary or are performed in the application; UDP avoids the overhead of such processing in the protocol stack. ***Time-sensitive applications often use UDP*** because dropping packets is preferable to waiting for packets delayed due to retransmission, which may not be an option in a real-time system.

It is a simple and lightweight protocol, lacking the built-in error checking and retransmission mechanisms found in other transport layer protocols like TCP . The only such properties it has are:
- Demultiplexing
- Checksums (optional)