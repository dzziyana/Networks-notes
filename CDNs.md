# Caching
## ... can be performed at different locations
![[caching locations.png]]
## HTTP cached object validation
- Server hints when an object expires (kind of TTL) as well as the last modified date of an object
- Client conditionally requests a resource using the “if-modified-since" header in the HTTP request
- Server compares this against “last modified” time of the resource and returns
	- “Not Modified” if the resource has not changed
	- “OK” with the latest version otherwise

# Global replication
## Why?
### Fault tolerance
- Service remains available (at least partially) even if some datacenter or network fails
### Load balancing
	- Distribute requests over multiple servers
		- (Could be solved with multiple servers in one location)
### Optimize latency
	- Requests are directed to “nearby” server
### Network inefficiency
	- No need to transmit data across the globe

## Directing clients to closest servers

###  using DNS
 Return different IP addresses based on
- **resolver**’s geo-localization
- server load (load balancing)
- Use short TTL of DNS records to prevent caching
### using BGP-anycast
 Always use same IP address (or small set of addresses)
- Addresses are advertised via BGP from multiple locations
- Closest location is found by BGP
- Same approach as open DNS resolvers (e.g., 9.9.9.9)
### Comparison
![[Pasted image 20250723124243.png]]