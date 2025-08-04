# Subnets
![[Pasted image 20250731150857.png]]

# Aggregation
![[Pasted image 20250731151118.png]]

## Two Points of aggregation
1. Optimize local routing table
• Construct routing table with fewer entries but same longest-matching-prefix results
• See “Compress forwarding table” in network-layer slides
• See “Optimal Routing Table Constructor” algorithm in supplementary material at the end of these lecture slides

2. Decide which prefixes to advertise
• Additional issue: router must make sure that nobody else can advertise a prefix that hides part of its address space