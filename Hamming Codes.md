The idea is that we send ***check bits*** $R$, which are a function of the data bits D, i.e. $R= f(D)$.
In this context we define the 
# Hamming Distance 
which is the minimum distance between any pair of strings. To determine the distance between two binary strings one can just count the digits where both differ.
![[Pasted image 20250722144741.png]]
# Check bits
- $b_i$ where $i$ is a power of 2.
## Syndrome
The syndrome of the code is a bit string $p_1p_2...p_n$ where $p_{i}$ is the parity (sum $mod2$) of all positions which have the $i$-th bit set in the binary representation of the position
> For a Hamming code of length 6:
> $$p_1​=b_1​+b_3​+b_5$$

>[!Tip]
> If nonzero, the value of the syndrome indicates the position of the bit flip
## Error Detection : 
When all code-words of a mapping have the minimum hamming distance $d + 1$, we can detect up to $d$ errors.
## Error Correction : 
For a code of Hamming distance $2d + 1$, up to d errors can always be corrected by mapping to
the closest code-word
# Example
A possible mapping could be 0 → 000 and 1 → 111. Notice that all other binary strings of length 3 have no meaning in this mapping and thus one can conclude that they are corrupted if they occur. We can detect an error as long as the hamming distance is greater than the amount of errors occurred. Assume one wants to send a 0, which gets

![[Pasted image 20250722145244.png]]
Notice that we can detect up to 2 errors. Having 3 bit flips would not be recognized in this mapping.

