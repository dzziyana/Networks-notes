# Randomized
> Nodes randomize their resource access attempts
- good for low load
# Contention free
> Nodes order their resource access attempts
- good for high load or guaranteed quality of service
# MACA (Mult. Access with collision avoidance)
- MACA uses a short handshake instead of [[CSMA#CSMA (Carrier Sense Multiple Access)|CSMA]] (Karn, 1990)
- [[WiFi]] uses a refinement of MACA (later)
- helps with the problem of [[Hidden Terminal|hidden terminals]]
## Protocol rules:
1. A sender node transmits a RTS (Request-To-Send, with frame length)
2. The receiver replies with a CTS (Clear-To-Send, with frame length)
3. Sender transmits the frame while nodes hearing the CTS stay silent
• Collisions on the RTS/CTS are still possible, but less likely