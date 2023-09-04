# Table of Contents



---
If $G$ is in CNF, then every non-empty string $w\in L(G)$ can be derived in at most $2|w|-1$ steps

**Problem:** Given a CNF $G$ and a string $w$, decide if $G$ generates $w$

Use a *divide and conquer* algorithm
1. **Base:** If the problem can't be broken up, solve it directly
2. **Divide:** Otherwise break up the problem into several sub-problems
3. **Recur:** Recursively solve each sub-problem
4. **Conquer:** Combine the solutions of the sub-problems into the overall solution

Define a function `parse(var, i, j)` that decides if $G$ can derive $w[i:j]$ starting with the nonterminal `var`
```
Parse(var, i, j):
1. Base parse(var, i, i+1): check if var->w[i] is a rule
2. Divide w[i:j] into w[i:k] and w[k:j] for i < k < j
3. Recursively check, for every rule var->AB if parse(A,i,k) and parse(B,k,j)
4. Conquer: if yes for any k and rule, we know var derives w[i,j]
```