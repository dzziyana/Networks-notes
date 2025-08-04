# Max-Flow Problem as a Linear Program

![[Pasted image 20250802195446.png]]
## Problem
- Maximize flow from source `S` to target `T`.
## Variables
- `f_uv`: flow on edge u → v
- `f`: total flow from S to T
## Objective
- `maximize f`
## Constraints
1. **Capacity:** `0 ≤ f_uv ≤ c_uv`
2. **Flow from source:** `f = F(S)`
3. **Flow into sink:** `f = -F(T)`
4. **Conservation:** `F(v) = 0` for all v ≠ S, T
## Note
- Complexity: $~O(E^3)$, slower than specialized algorithms like Edmonds-Karp $(O(V^2E))$

# Adapting to [[LP - Multiple Commodity Flow Problem|MCF]]
![[Pasted image 20250802202610.png]]