# Duties
## **frequency representation** 
digital <-> analog conversion, handling noise and attenuation

## baseband modulation 
Non-Return to Zero (NRZ), Manchester Coding, Non-Return to Zero with Inversion (NRZI), 4B/5B

## passband modulation 
amplitude shift keying, frequency shift keying, phase shift keying.

The physical layers provides an abstraction and model of the real-world implementation of the transfers. We use this abstraction to express desired properties. We have defined
# Rate  $[\frac{bits}{second}]$
# Delay  $[seconds]$
## Transmission delay
$$\frac{M[bits]}{R[\frac{bits}{second}]}$$
## Propagation delay
$$D = \frac{L_{link}}{\frac{2}{3}c}$$

# Total latency

$$L = M/R + D$$

# Bandwidth-delay product
The **(BDP)** represents the **maximum amount of data (in bits)** that can be "in flight" (i.e., on the wire) in the network at any given time.
$$BD[bits] = R \cdot D$$