[[Distance Vector Routing|Distance vector]] protocol with hop count as metric

- Infinity is 16 hops; limits network size
- Includes [[Count to Infinity#Split Horizon|split horizon]], [[Count to Infinity#Poison Reverse|poison reverse]] 

Routers send vectors every 30 secs
- Runs on top of [[UDP]]
- Timeout in 180 secs to detect failures