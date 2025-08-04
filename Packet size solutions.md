# Discovery
• Find the largest packet that fits on the network path and use it
• IP uses this approach today instead of fragmentation

> Host **tests** path with large packet (with “don’t fragment” flag set)
- Routers provide feedback if too large; they tell host what size would have fit
# Fragmentation
- Split up large packets in the network if they are too big to send
- Classic method (but dated) and slow for routers to fragment

## IPv4 fragmentation fields
![[Pasted image 20250731112747.png]]

## Procedure
### Routers split a packet that is too large:
- Typically break into large pieces
- Copy IP header to pieces
- Adjust length on pieces
- Set offset to indicate position
- Set MF (More Fragments) on all pieces except last

### Receiving hosts reassembles pieces:
- Identification field links pieces together, MF tells receiver when it has all pieces

### Example
![[Pasted image 20250731113019.png]]