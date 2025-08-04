### Problem 
Should dual-stack hosts contact servers via IPv4 or IPv6?
### Solution
Try both but prefer IPv6

- Issue A (IPv4) and AAAA (IPv6) DNS queries simultaneously
- If AAAA record is received, start connection setup over IPv6 immediately
- If A record is received, wait 50 milliseconds for AAAA record
- If first connection attempt (e.g., via IPv6) is unsuccessful, try again with different address (e.g., via IPv4)