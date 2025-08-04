## Objective
- Minimize path length from `S` to `T`
## Variables
- `x_uv ∈ [0, 1]`: Indicates if edge u→v is part of path
## LP Formulation
- minimize `Σ x_uv · w_uv`
## Constraints
1. **Conservation:** `X(v) = 0` for all v ≠ S, T
2. **Start at S:** `X(S) = 1`
3. **End at T:** `X(T) = -1`
## Note
- Even without integer constraints, solution is often integral
