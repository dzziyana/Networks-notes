Allow multiple routing paths from node to destination be used at once
- Topology has them for redundancy
- Using them can improve performance and reliability

With ECMP, source/sink “tree” is a directed acyclic graph (DAG)
Find the source “tree” for E
- Procedure is Dijkstra, simply remember set of next hops
- Compile forwarding table similarly, may have set of next hops

Always send packets from a given flow on the same path
- Map flow identifier to single next hop
- No jitter within flow, but less balanced

How to identify flows?
• Hash 5-tuple (Src IP, Dst IP, Src Port, Dst Port, Protocol)
• Protocol is TCP or UDP
• Use IPv6 Flow ID