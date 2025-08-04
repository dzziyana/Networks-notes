In many communication systems, especially high-speed serial links, a **separate clock signal** is not transmitted alongside the data. Instead, the receiver must **recover the clock** from the incoming data stream to:
- Sample the data at the correct time (ideally at the center of each bit),
- Maintain synchronization with the transmitter,
- Prevent bit errors due to misaligned timing.
![[Pasted image 20250726131722.png]]

# 4B/5B
Map every 4 data bits into 5 code bits without long runs of zeros
• 0000 $\rightarrow$ 11110, 0001 $\rightarrow$  01001, 1110 $\rightarrow$  11100, … 1111 $\rightarrow$  11101
• Has at most 3 consecutive zeros
• Also invert signal level on a 1 to break up long runs of 1s (called NRZI)
