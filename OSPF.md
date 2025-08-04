Link-state routing protocol widely used for intra-domain routing
- OSPF splits the AS into different areas
	- Improves scalability: flooding only within each area
	- Like splitting the whole Internet into ASes
	- Areas are identified by 32-bit numbers, formatted as IP addresses (a.b.c.d)
	- Each area independently runs the link-state routing algorithm
- Routers keep a link-state database for the areas they are connected to
- An area’s topology is invisible from the outside
	- Only aggregated information is communicated
- All areas are connected exclusively **via a special backbone area**
	- Backbone area must be contiguous
	- ID of backbone area: 0.0.0.0
![[Pasted image 20250731165423.png]]

# Different types of routers
## Internal routers
- Belong to a single area (not the backbone area)
- Only run the LS routing algorithm with routers belonging to their respective area
## Backbone routers
- Routers with a connection to the backbone area
## Area border routers
- Special case of backbone routers
- Belong to the backbone area and at least one other area
- Run the LS routing algorithm for all connected areas
- Condense topological information of their areas and distribute it to the backbone
## AS boundary routers
- Routers connected to other ASes
 - Can be either internal or backbone routers
- Advertise external routing information throughout the AS