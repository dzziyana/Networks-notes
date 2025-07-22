- layered over a bidirectional bytestream
- stateless
	- maintains no info about past client requests
## Pros and Cons of Statelessness
![[Pasted image 20250321121443.png]]
## Cookies - Tool to maintain state
• Client stores small state on behalf of the server X
• Client sends state **in all future requests** to X
• Can provide **authentication** as well as state
# Request Structure
![[Pasted image 20250321120812.png]]
## First Line 
![[Pasted image 20250321120655.png]]
## Header
![[Pasted image 20250321120856.png]]
# Response Structure
![[Pasted image 20250321121040.png]]

## First Line
![[Pasted image 20250321121024.png]]
## Header
![[Pasted image 20250321121341.png]]