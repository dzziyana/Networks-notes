Given n data bits, generate k check bits such that the n+k bits are evenly divisible by a generator C

# The approach
based on mathematics of finite fields, in which “numbers” represent polynomials
	e.g., 10011010 is x7 + x4 + x3 + x1
### What this means
We work with binary values and operate using $mod2$ arithmetic

# Send Procedure
1. Extend the n data bits with k zeros
2. Divide by the generator value C
3. Keep remainder, ignore quotient
4. Adjust k check bits by remainder

# Receive Procedure
1. Divide and check for zero remainder

# Example
Data bits: 1101011111
C = 10011
![[Pasted image 20250725160728.png]]