...define an order in which nodes get a chance to send
- or pass, if no traffic at present
- 
We just need some ordering …
- E.g., Token Ring
- E.g., node addresses

# Token Ring
![[Pasted image 20250725112520.png]]

> [!info]
> Fixed overhead with no collisions
> • More efficient under load
> Regular chance to send with no unlucky nodes
> • Predictable service, easily extended to guaranteed quality of service

## Complexity
• More things that can go wrong than random access protocols!
• E.g., what if the token is lost?
• Elect a leader who manages the token, what to do if leader crashes?
• Higher overhead at low load

# Turn-taking in practice
Regularly tried as an improvement offering better service
• E.g., quality of service

But random multiple access is hard to beat
• Simple, and usually good enough
• Scales from few to many nodes