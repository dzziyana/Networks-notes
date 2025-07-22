# Isolation Domainsn (ISD)
## ISD Core (core ASes)
- The only connection for any device in the ISD to other ISDs
- contains the [[SCION#Trust Root Configuration|Trust Root Configuration]] (TRC)
### Trust Root Configuration
- contains the root cryptographic keys to verify ISD operations
## Path-Segment Construction Beacon (PCB)
It's a core concept used to establish **secure, efficient, and policy-compliant paths** between different parts of the network.
- gets periodically initiated by the Beacon Routers and forwarded by the Border Routers
- When a Border Router receives a PCB, it checks its authenticity, which is done by...
	- ==Verifying the cryptographic signatures associated with the path segments in the PCB.== Each signature is checked using the public key of the AS or router that signed that segment.
	- ==Checking== that the ==AS identifiers== in the PCB match known, valid and trusted ASes.
	- ==Checking timestamps== to ensure that the PCB is recent and has not expired.

If authentication is completed the down-stream path (path to non-core AS) is stored in the Path Server and the Beacon Server. 
The Beacon Server periodically initiates PCB to neighboring ASes through Border Routers.

Constructing a Path : When a device in a specific AS wants to connect to an IP it asks the Path Server for possible paths. If the path is known, i.e. the according PCB is stored in the Path Server it returns possible paths, from which the device can choose from and optimize arbitrary metrics. If that is not the case the Path Server requests the missing path segments by the Path Server in the Core ISD.