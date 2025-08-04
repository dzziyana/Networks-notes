## Problem
- Multiple commodities α with their own source `S_α` and sink `T_α`
- Flows must not mix
## Variables
- `f_α`: total flow for commodity `α`
- `f_α,uv`: flow for `α` on edge `u → v`
## Objective
- maximize `Σ f_α`
## Constraints
1. **Capacity:** `Σ_α f_α,uv ≤ c_uv`
2. **Flow from source:** `f_α = F_α(S_α)`
3. **Conservation:** `F_α(v) = 0` for all v ≠ S_α, T_α

> [!Hot] 
> Best known solution is LP
